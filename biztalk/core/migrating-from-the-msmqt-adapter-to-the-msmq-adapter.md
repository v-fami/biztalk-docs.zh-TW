---
title: "從 MSMQT 配接器移轉至 MSMQ 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, MSMQT adapters
- scaling, MSMQT adapters
- reliability, MSMQT adapters
- MSMQT adapters, transactional consistency
- migrating, MSMQT adapters
- MSMQT adapters, ordered delivery
- MSMQT adapters, migrating to MSMQ adapters
- MSMQT adapters, scaling
- MSMQT adapters, reliability
- MSMQ adapters, migrating MSMQT adapters
- high availability, MSMQT adapters
- MSMQT adapters, performance
- MSMQT adapters, availability
ms.assetid: 97126f70-0be5-4a2f-bcba-173fd932b6de
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b1fce448788a8c6c5721403dbb7e4e58609a31a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="migrating-from-the-msmqt-adapter-to-the-msmq-adapter"></a>從 MSMQT 配接器移轉至 MSMQ 配接器
本主題討論的內容是將解決方案從 BizTalk 訊息佇列 (MSMQT) 配接器移轉至訊息佇列 (MSMQ) 配接器以前，考量有關端對端排序的傳遞、交易一致性、高可用性和擴充性的要點。 排序的傳遞、交易一致性、高可用性和擴充性等主題的用途定義如下：  
  
-   **排序的傳遞。** 保證訊息會以接收它們時相同的排序從 BizTalk Server 傳送出去。  
  
-   **交易一致性。** 保證已處理的訊息不會因為硬體、軟體或網路失敗而遺失或重複。  
  
-   **高可用性。** 保證用來處理訊息的服務永遠都可用於處理。  
  
-   **延展性。** 增加現有訊息處理容量的能力。  
  
## <a name="end-to-end-ordered-delivery"></a>端對端排序的傳遞  
 MSMQT 配接器可以確保訊息端對端排序的傳遞。 這表示若 MSMQ 應用程式傳送訊息 1、2 和 3 至繫結至 MSMQT 配接器的接收位置，接著在 BizTalk Server 中就會以相同的順序，將這些訊息遞送至協調流程或傳送埠：1、2、3。 一個使用這項功能可能包含股市交易，必須提交並執行已接收的順序相同。  
  
 使用 MSMQT 的端對端排序的傳遞需要許多元件一起運作。 下列連續事件說明如何使用 MSMQT 配接器來完成此過程：  
  
1.  遠端電腦上的 MSMQ API 依序接到訊息 1、2 和 3 後，會以相同的順序再將訊息推入交易式本機佇列中：1、2、3。  
  
2.  遠端電腦上的 MSMQ 用戶端會擷取該佇列中的訊息，再將訊息依下列順序傳送至 MSMQ 佇列：1、2、3。  
  
3.  MSMQ 配接器會依 1、2、3 的順序接收訊息，再將訊息依相同的順序傳送至 BizTalk MessageAgent 元件：1、2、3。  
  
4.  BizTalk MessageAgent 元件會確保訊息是依下列順序傳送至 MessageBox：1、2、3。  
  
5.  MessageBox 會路由傳送訊息，並確保訊息路由傳送至協調流程或傳送埠的同一個執行個體時，會依相同的順序傳遞至此執行個體：1、2、3。  
  
 在 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 中，MSMQT 是唯一能夠保證端對端排序傳遞的配接器。 所有其他整合式 BizTalk 配接器都可能變更上述步驟 3 至 5 中的訊息排序。 大多數其他整合式配接器可以使用如「結束點管理員」這種元件來完成步驟 3，因為「結束點管理員」原本就是多執行緒處理，所以不會保留排序。 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 的 MSMQ 配接器可以使用保留步驟 3 排序的「連續處理」功能，不過到時它不會要求 MessageAgent 保留往前的排序，所以訊息可能會無順序地路由至協調流程或傳送埠。  
  
 **端對端排序的傳遞與 MSMQ 配接器**  
  
 若要達成端對端排序的傳遞與 MSMQ 配接器，請遵循下列步驟：  
  
1.  啟用**排序的傳遞**屬性上的接收訂閱的協調流程使用的連接埠或傳送埠。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程中的接收埠和傳送埠**排序的傳遞**組態選項。 若啟用這個選項，則協調流程接收埠或傳送埠會要求 MessageBox 以訊息提交到 MessageBox 的相同排序將訊息傳遞給它。  
  
2.  設定**排序的處理**繫結至 MSMQ 配接器的接收位置屬性`True`。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，使用 MSMQ 傳輸的接收位置可被設定為使用 [排序的處理]，若啟用這項功能，會確保訊息以接收它們時的相同排序傳送到 MessageBox。  
  
3.  設定**交易式**繫結至 MSMQ 配接器的接收位置屬性`True`。  
  
4.  確保任何由 MSMQ 接收位置正在監控的 MSMQ 佇列都會標示為「交易式」。 必須在佇列上設定此屬性，以確保訊息的排序傳遞。  
  
> [!NOTE]
>  只有當 BizTalk 接收位置正在監控的 MSMQ 佇列是僅由一部電腦提供服務時，才能保證排序的傳遞。 這可能會造成擴充性的問題，如下所述。  
  
## <a name="transaction-usage-when-processing-messages-with-the-msmqt-adapter-vs-the-msmq-adapter"></a>使用 MSMQT 配接器與 MSMQ 配接器處理訊息時的不同交易用法  
 關於交易用法，MSMQT 與 MSMQ 配接器在處理訊息方面有一個主要差異。  
  
 使用 MSMQT 配接器時，從網路接收訊息的程序與使用 BizTalk Server 處理訊息，是在單一交易之下進行。 使用 MSMQT 配接器時，為傳送者產生的 ACK 訊息是一項指示，指出已接收訊息且 BizTalk Server 已順利處理。  
  
 使用 MSMQ 配接器時，從網路接收訊息的程序與使用 BizTalk Server 處理訊息，是在兩個分開的交易之下進行，一個是從網路接收，另一個是使用 BizTalk 伺服器處理。 使用 MSMQ 配接器時，為傳送者產生的 ACK 訊息只是一項指示，指出已從網路順利接收訊息，但不會指出訊息已由 BizTalk Server 順利處理。 當訊息從網路接收並且保存至本機 MSMQ 佇列時，傳送者會從 Microsoft Message Queuing 伺服器接收一個 ACK，不論 BizTalk Server 是否已安裝。 在訊息已保存至 MSMQ 佇列之後，BizTalk MSMQ 配接器會拾取訊息、處理訊息並將訊息發佈至 MessageBox。 若這項程序失敗，訊息就會傳送到 BizTalk 擱置佇列或留在本機 MSMQ 佇列 (當使用交易式處理時)，而傳送者不會得知訊息在 BizTalk Server 中處理時已失敗。  
  
 若您的架構需要您在 BizTalk Server 順利處理訊息時接收 ACK，那麼當您從 MSMQT 配接器移轉至 MSMQ 配接器時，您必須新增應用程式層級的 ACK。 您必須更新協調流程和傳送應用程式，才能實作應用程式層級的通知。  
  
## <a name="high-availability-transactional-in-order"></a>高可用性 (交易式，依排序)  
 若要為 MSMQT 配接器提供高可用性您可以將多部電腦新增至接收主控件，並設定網路負載平衡 (NLB) 以支援容錯或可以叢集化預設 BizTalk 主控件。 若您結合 NLB 來執行 MSMQT 配接器，則其中一部伺服器當機時，其他伺服器就會接手處理負載。 若您在叢集化的主控件中執行 MSMQT 配接器處理常式，當其中一個主控件節點失敗時，叢集軟體就會將叢集化節點容錯移轉到其他節點。 使用 MSMQ 配接器時，若您需要交易式處理，且不遺失資料，則 NLB 不會運作，因為 MSMQ 配接器使用本機 MSMQ 佇列以進行中繼儲存。 在此實例中，若訊息已傳遞至本機 MSMQ 佇列但是沒有被 MSMQ 配接器取用，則在電腦當機時，就會遺失訊息。  
  
 若要使用 MSMQ 配接器提供高可用性與交易一致性，您應該執行下列作業：  
  
1.  在 BizTalk Server 的 Windows 伺服器叢集群組中將 Microsoft Message Queuing (MSMQ) 設定為叢集資源。  
  
2.  在 BizTalk 主控件執行個體中設定 MSMQ 配接器的傳送和接收處理常式，此執行個體已在與叢集 MSMQ 資源相同的叢集群組中設定為叢集資源。  
  
3.  設定 BizTalk 主控件執行個體的叢集資源，這樣它才會維持對叢集化 MSMQ 資源的相依性。  
  
 若要實作這種架構與排序的傳遞，請遵循上述"端對端排序的傳遞與 MSMQ 配接器。 」  
  
## <a name="high-availability-nontransactional-not-in-order"></a>高可用性 (非交易式，非依排序)  
 若您需要高可用性，但是不需要交易式處理，您可以實作 NLB 及執行主控件執行個體 (在 NLB 背後的多部 BizTalk 伺服器上使用 MSMQ 傳送與接收處理常式來設定)，使用 MSMQ 配接器來滿足需求。 當 MSMQ 實作 NLB 時您應該遵循最佳作法，如 Microsoft 知識庫文件 899611 中所述 」 如何訊息佇列可在透過網路負載平衡 (NLB) 」 可在[http://go.microsoft.com/fwlink/?LinkId = 57510](http://go.microsoft.com/fwlink/?LinkId=57510)。 在此實例中，若其中一部 BizTalk 伺服器當機，在 BizTalk 伺服器上的主控件執行個體中執行之訊息，在 BizTalk 伺服器復原以前都將無法使用。 這個組態可提供高可用性，因為若其中一部 BizTalk 伺服器無法使用，NLB 會將要求路由到其他 BizTalk 伺服器。  
  
## <a name="scalability-nontransactional-not-in-order"></a>擴充性 (非交易式，非依排序)  
 您可以遵循下列高可用性 (非交易式) 的指導方針來以及新增主控件執行個體來達到擴充性。 這個架構提供快速傳遞與擴充性，但是不提供排序的傳遞。  
  
## <a name="scalability-transactional-not-in-order"></a>擴充性 (交易式，非依排序)  
 如需訊息的交易式遞送而無須排序的傳遞，您可以同時使用 NLB 與 MSMQ 以及 Windows 叢集。 這個架構需要您遵循「高可用性 (交易，依排序)」之中的步驟，在兩個分開的 Windows 叢集環境中為每個 Windows 叢集設定至少兩個叢集群組。 然後您可以實作 NLB 來分散叢集群組之間的負載。 因為 Windows 叢集上不支援執行 Windows NLB，所以這個實例需要硬體 NLB 解決方案。 下圖說明這個架構。  
  
 ![叢集群組之間的負載平衡](../core/media/scaleclusteredmsmqwithnlb.gif "ScaleClusteredMSMQwithNLB")  
  
> [!NOTE]
>  這個架構不提供排序的傳遞。  
  
## <a name="scalability-transactional-in-order"></a>擴充性 (交易式，依排序)  
 當使用 MSMQ 3.0 或更早的版本時，提供高可用性、交易一致性和排序傳遞的向外擴充架構會有問題，因為不支援遠端交易讀取，除非 BizTalk Server 電腦和遠端 MSMQ 伺服器都執行 MSMQ 4.0。 當使用 MSMQ 3.0 或更早的版本時，必須使用多個本機 MSMQ 佇列達成向外擴充。 此外，在此案例中，如果 MSMQ 工作階段到 NLB 的 TCP/IP 連線已中斷，它可能後續還原 nlb 到不同的電腦，可能會導致不按照順序的傳遞。  
  
 對於這項限制的一個可能的解決方法，就是配置目的地佇列到不同的電腦來手動載入平衡訊息傳遞。 您也可以輸入特定 BizTalk 主控件執行個體到特定 MSMQ 佇列來達到這項目的。 例如，若您從某一個交易夥伴接收大量的文件，請為該交易夥伴在特定 BizTalk 伺服器上建立個別的主控件與接收佇列。  
  
 可能的話，需要遠端交易式讀取和負載平衡時，請在遠端電腦上執行 MSMQ 4.0。  
  
## <a name="summary"></a>摘要  
 下表摘要敘述您可以實作的架構，以啟動特定的功能。  
  
|**功能**|**NLB 和叢集都不**|**NLB**|**Cluster**|**NLB 和叢集**|  
|-----------------------|---------------------------------|-------------|-----------------|-------------------------|  
|端對端排序的傳遞|是|否|是|手動組態可能可行|  
|交易一致性|否 (若發生服務失敗，訊息可能會遺失或重複)|否|是|是|  
|高度可用|否|是|是|是|  
|可擴充|否|是|否|是|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)