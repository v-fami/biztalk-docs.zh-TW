---
title: "高可用性的 BizTalk 主控件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3153f7f7-7e82-4b0c-9b48-e9f871de285d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f500deb38df3f8145a2cba582164f14c87ac33d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-biztalk-hosts"></a>BizTalk 主控件的高可用性
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]提供更多的彈性來處理高可用性，因為您可以策略性地指定邏輯主控件執行特定的功能，例如接收和傳送訊息或處理協調流程可以實際部署至區域多部伺服器。  
  
 BizTalk 主控件是中的邏輯容器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可包含的群組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]項目，例如配接器傳送處理常式 （包括管線），接收位置，以及協調流程。 您通常會將具有相似擴充屬性的項目群組成特定的主控件。  
  
 建立主控件之後，可以部署至實體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與主控件執行個體的電腦。 主控件執行個體上所指定執行 Windows 服務，BTSNTSvc.exe （或 64 位元主控件執行個體 BTSNTSvc64.exe），[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 對於每個主控件，您可以有只有一個執行個體，在特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 不過，您可以有一個或多個特定主控件執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，而且您可以有不同的主控件執行個體在特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
 BizTalk 主控件中所包含的項目可以執行下列功能：  
  
-   **接收**。 在接收位置拾取訊息之後，這些項目會進行訊息的初始處理。 當主控件包含接收項目，例如接收位置 （使用管線），訊息解碼和解密發生在主控件中的管線。  
  
-   **傳送**。 這些項目會在訊息傳送到傳送埠之前，進行訊息的最後處理。 當主控件包含傳送項目，例如傳送埠，訊息簽署和加密，就會發生的管線中的主機。  
  
-   **處理**。 這些項目處理協調流程中指示為基礎的訊息。  
  
 一個 BizTalk 主控件可以包含接收、傳送和處理訊息的項目。 為了更容易管理和延展性，我們建議您建立不同的主控件指定每個函式。 特別是，我們建議您在進行處理、 接收/傳送作業使用不同的主控件。  
  
 例如，若您接收一個訊息、執行協調流程，並傳送十個訊息，您要將接收和傳送功能分成兩個獨立的主控件，因為傳送項目將會比接收項目多出十倍的流量。 若您接收一個訊息、執行協調流程，並傳送一個訊息，您可以將這些項目視為一個工作單位並將它們群組為單一主控件。 或者，您可以將它們分成三個不同的主控件以增加效能和彈性，不過這也可能增加管理成本。  
  
 BizTalk 主控件為下列其中一種，*同處理序*或*隔離*。 內含式主控件內執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（BTSNTSvc.exe 或 BTSNTSvc64.exe） 的執行階段程序，在外掛式主控的件不會執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段程序。 外掛式接收配接器的外掛式主控的件才會使用接收端上。 下表列出每個主控件類型可能包含的項目。  
  
|主機類型|邏輯容器|  
|---------------|---------------------------|  
|內含式|-協調流程<br />配接器傳送處理常式<br />為內含式配接器接收處理常式|  
|外掛式|HTTP、 SOAP 接收處理常式<br />-任何其他外掛式配接器接收處理常式|  
  
 如需管理 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154191)(http://go.microsoft.com/fwlink/?LinkID=154191) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
 若要為 BizTalk 主控件提供高可用性，您必須的兩個或多個主控件執行個體 （在兩個或多部電腦） 上的每一部主機環境中。 有一個以上的主控件執行個體的確認，一個主控件執行個體變成無法使用，如果主控件執行個體正在執行相同的主控件執行個體的其他電腦上每個主機可以繼續有問題或失敗的主控件執行個體中，函式和整體系統可以繼續執行的干擾。  
  
## <a name="disadvantages-of-additional-hosts"></a>其他主機的缺點  
 雖然建立其他主控件執行個體的優點，也有缺點如果太多的主控件執行個體所建立。 每個主控件執行個體是 Windows 服務 （BTSNTSvc.exe 或 BTSNTSvc64.exe） 會產生對 MessageBox 資料庫的額外負載，並使用電腦資源，例如 CPU、 記憶體和執行緒。 以外，您有未設定太多其他主控件執行個體的原因如下：  
  
-   有太多資料粒度，數個效能計數器會報告每個主機。 這會影響可用性的系統管理員必須周遊大量資料。 這對系統管理員將擁有的整體檢視有負面影響。  
  
-   每一部主機會耗用相當多的記憶體節流的情況下，可能會造成而降低效能。  
  
-   如果主機有接收配接器持續執行輪詢，每一部主機將輪詢資料庫在短時間內，進而導致效能降低的問題。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [向外擴充接收主控件](../technical-guides/scaling-out-receiving-hosts.md)  
  
-   [叢集接收主控件](../technical-guides/clustering-receiving-hosts.md)  
  
-   [向外延展處理主控件](../technical-guides/scaling-out-processing-hosts.md)  
  
-   [向外延展傳送主控件](../technical-guides/scaling-out-sending-hosts.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定主控件和主控件執行個體](../technical-guides/configuring-hosts-and-host-instances.md)   
 [專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)   
 [規劃高 Availability2](../technical-guides/planning-for-high-availability2.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)