---
title: "高可用性的主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b99cb04-61a5-41cc-a409-35897c17b789
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4c8c18f394b800ffeee9994294b2d2dbf0cb3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-the-master-secret-server"></a>主要密碼伺服器的高可用性
即使您未使用 「 企業單一登入 (SSO) 功能來對應認證和單一登入，SSO 會是很重要的一部分整體 Microsoft[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]基礎結構，因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用 SSO 協助保護連接埠的資訊組態設定。 連接埠組態資料已加密，並儲存在 SSO 資料庫中。 每個 BizTalk server 已用於加密及解密連接埠組態資料的 SSO 服務 (ENTSSO.exe)。  
  
 SSO 服務啟動時，它會從主要密碼伺服器擷取加密金鑰。 此加密金鑰稱為主要密碼。 主要密碼伺服器是另一個有額外的子服務會維護並散發主要密碼的 SSO 服務。 擷取主要密碼之後，SSO 服務會快取它。 每隔 60 秒，SSO 服務會同步處理主要密碼主要密碼伺服器。  
  
 如果主要密碼伺服器失敗，以及 SSO 服務中的其中一個它的重新整理間隔會偵測失敗，SSO 服務及伺服器失敗，包括解密的憑證之前執行的所有執行階段作業繼續成功。 不過，您也無法加密新的認證或連接埠組態資料。 因此，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境具有主要密碼伺服器的可用性相依性。  
  
## <a name="making-the-master-secret-server-available"></a>讓主要密碼伺服器可用  
 可用的 SSO 系統，因此的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，相當重要，因為它會產生備份主要密碼。 若遺失該主要密碼，您將遺失使用它來加密的 SSO 系統資料。 如需備份主要密碼的詳細資訊，請參閱[如何重新設定主要密碼](http://go.microsoft.com/fwlink/?LinkID=151934)(http://go.microsoft.com/fwlink/?LinkID=151934) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
 可使用兩種方法讓主要密碼伺服器可用：  
  
-   **可用，但不是高度可用**。 您可以建立主要密碼伺服器會變成無法使用，而您可以再手動將升級主要密碼伺服器並還原主要密碼，此伺服器上的另一部 SSO 伺服器時通知您的 Microsoft System Center Operations Manager 事件。  
  
     雖然這項設定不具高可用性，但它仍可滿足大部分的情況下，而且很與向外擴充接收、 傳送和處理主控件一致。  
  
-   **高可用性**。 若要提供主要密碼伺服器的備援，請在不同的主要密碼伺服器叢集上使用 Windows 叢集，或在現有的資料庫叢集上設定主要密碼伺服器。 主要密碼伺服器所提供的服務不會耗用太多資源，且在資料庫叢集上安裝時，通常不會影響資料庫的功能或效能。 下圖顯示如何讓主要密碼伺服器高度可用。  
  
     ![高可用性的主要密碼伺服器](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")  
  
     雖然此組態高度可用，它仍然需要額外的硬體資源。 如需 SSO 的高可用性安裝選項的詳細資訊，請參閱[高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(http://go.microsoft.com/fwlink/?LinkId=156838) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
     本節包含設定為高可用性的叢集資源的 SSO 主要密碼伺服器上的詳細的資訊[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集。  
  
    > [!NOTE]  
    >  若要減少高度可用的方案的硬體資源，可將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。 請注意，您不需要購買其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]授權安裝 SSO 服務在執行 SQL Server 的電腦上。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)  
  
-   [手動指定新的主要密碼伺服器](../technical-guides/designating-a-new-master-secret-server-manually.md)  
  
## <a name="see-also"></a>另請參閱  
 [規劃高 Availability2](../technical-guides/planning-for-high-availability2.md)   
 [BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)