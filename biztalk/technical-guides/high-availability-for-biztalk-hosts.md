---
title: 為 BizTalk 主控件的高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3153f7f7-7e82-4b0c-9b48-e9f871de285d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 959160bdf8e4e81715c77946663a9e4fc70fb077
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978663"
---
# <a name="high-availability-for-biztalk-hosts"></a>BizTalk 主控件的的高可用性
BizTalk Server 提供更多的彈性來處理高可用性策略，您就可以專心邏輯主控件執行特定部分的功能，例如接收和傳送訊息或處理協調流程，可以放在一起，部署到多部伺服器。  
  
 BizTalk 主控件是中的邏輯容器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組可以裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]項目，例如配接器傳送處理常式 （包括管線），接收位置，以及協調流程。 您通常會將具有相似擴充屬性的項目群組成特定的主控件。  
  
 建立主機之後，您就可以將它部署至實體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與主控件執行個體的電腦。 主控件執行個體上指定執行 Windows 服務，BTSNTSvc.exe （或 64 位元主控件執行個體的 BTSNTSvc64.exe）[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 對於每個主機，您可以有只有一個執行個體特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 不過，您可以在一或多個特定主控件執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，而且您可以有不同的主控件執行個體特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
 包含 BizTalk 主控件中的項目可以執行下列功能：  
  
- **接收**。 在接收位置拾取訊息之後，這些項目會進行訊息的初始處理。 當主控件包含接收項目，例如接收位置 （其中有管線），訊息解碼和解密會發生在主控件內的管線中。  
  
- **傳送**。 這些項目會在訊息傳送到傳送埠之前，進行訊息的最後處理。 當主控件包含傳送項目時，傳送埠，例如訊息簽署和加密就會發生在主控件內的管線中。  
  
- **處理**。 這些項目處理協調流程中指示為基礎的訊息。  
  
  一個 BizTalk 主控件可以包含接收、傳送和處理訊息的項目。 為了更容易管理和延展性，我們建議您建立不同的主控件指定每個函式。 特別是，我們建議您在進行處理、 接收/傳送作業使用不同的主控件。  
  
  例如，若您接收一個訊息、執行協調流程，並傳送十個訊息，您要將接收和傳送功能分成兩個獨立的主控件，因為傳送項目將會比接收項目多出十倍的流量。 若您接收一個訊息、執行協調流程，並傳送一個訊息，您可以將這些項目視為一個工作單位並將它們群組為單一主控件。 或者，您可以將它們分成三個不同的主控件以增加效能和彈性，不過這也可能增加管理成本。  
  
  BizTalk 主控件是一種類型的其中一個*同處理序*或是*隔離*。 內含式主控件內執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段程序 （BTSNTSvc.exe 或 BTSNTSvc64.exe） 和外掛式主控件不會執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段程序。 外掛式接收配接器的外掛式主控件才會使用接收端上。 下表列出每個主控件類型可能包含的項目。  
  
|主機類型|邏輯容器|  
|---------------|---------------------------|  
|內含式|-協調流程<br />配接器傳送處理常式<br />為內含式配接器接收處理常式|  
|外掛式|HTTP、 SOAP 接收處理常式<br />-任何其他外掛式配接器接收處理常式|  
  
 如需管理 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱 <<c0> [ 管理 BizTalk 主控件和主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154191)(http://go.microsoft.com/fwlink/?LinkID=154191)在 BizTalk Server 說明中。  
  
 若要為 BizTalk 主控件提供高可用性，您必須兩個或多個主控件執行個體 （在兩個或多部電腦） 的每個主機環境中。 有一個以上的主控件執行個體的每一部主機，您要確定，如果一個主控件執行個體變成無法使用，主控件執行個體上執行相同的主控件執行個體的其他電腦可以繼續有問題或失敗的主控件執行個體中，函式和整體系統可以繼續執行，盡可能減少服務中斷。  
  
## <a name="disadvantages-of-additional-hosts"></a>其他主機的缺點  
 建立其他主控件執行個體的優點時，也有缺點如果建立太多的主控件執行個體。 每個主控件執行個體是 Windows 服務 （BTSNTSvc.exe 或 BTSNTSvc64.exe），這會產生額外的負載，對 MessageBox 資料庫，並使用電腦資源，例如 CPU、 記憶體和執行緒。 以外，您有未設定太多其他主控件執行個體，原因如下：  
  
-   數個效能計數器會報告每個主機，使用太多資料粒度。 這會影響可用性的系統管理員想要瀏覽大量資料。 在系統管理員將擁有的整體檢視，這就會有負面的影響。  
  
-   每一部主機會耗用相當多的記憶體，可能會導致的節流的情況並降低效能。  
  
-   如果主機有收到持續執行輪詢的配接器，每一部主機會輪詢資料庫在短時間內，進而導致效能降低。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [向外擴充接收主控件](../technical-guides/scaling-out-receiving-hosts.md)  
  
-   [叢集接收主控件](../technical-guides/clustering-receiving-hosts.md)  
  
-   [向外擴充處理主控件](../technical-guides/scaling-out-processing-hosts.md)  
  
-   [向外擴充傳送主控件](../technical-guides/scaling-out-sending-hosts.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定主控件和主控件執行個體](../technical-guides/configuring-hosts-and-host-instances.md)   
 [專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)   
 [規劃高 Availability2](../technical-guides/planning-for-high-availability2.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)