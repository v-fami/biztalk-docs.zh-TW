---
title: 主要密碼伺服器的高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b99cb04-61a5-41cc-a409-35897c17b789
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9227715e30405217cdb9c13c2dc83dc0e236eef8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975847"
---
# <a name="high-availability-for-the-master-secret-server"></a>主要密碼伺服器的高可用性
即使您未使用企業單一登入 (SSO) 功能來對應認證和單一登入，SSO 是不可或缺的一部分整體的 Microsoft BizTalk Server 基礎結構，因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用 SSO 協助保護的連接埠資訊組態設定。 連接埠組態資料會加密，並儲存在 SSO 資料庫。 每個 BizTalk server 已用於加密及解密連接埠組態資料的 SSO 服務 (ENTSSO.exe)。  
  
 SSO 服務啟動時，它會從主要密碼伺服器擷取加密金鑰。 此加密金鑰稱為主要祕密。 主要密碼伺服器是另一個有額外的子服務，會維護及並分散主要密碼的 SSO 服務。 擷取主要祕密之後，SSO 服務會快取它。 每隔 60 秒，SSO 服務會與主要密碼伺服器，同步主要祕密。  
  
 如果主要密碼伺服器失敗，而且其中一種其重新整理間隔的 SSO 服務偵測到的失敗，SSO 服務和所有的執行階段作業失敗，則該伺服器，包括解密認證前, 執行成功的繼續。 不過，您無法加密新的認證或連接埠組態資料。 因此，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境具有相依性的主要密碼伺服器的可用性。  
  
## <a name="making-the-master-secret-server-available"></a>讓主要密碼伺服器可用  
 SSO 系統的可用性，因此的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請務必依產生備份主要祕密。 若遺失該主要密碼，您將遺失使用它來加密的 SSO 系統資料。 如需備份主要祕密的詳細資訊，請參閱[如何重新啟動主要祕密](http://go.microsoft.com/fwlink/?LinkID=151934)(<http://go.microsoft.com/fwlink/?LinkID=151934>) 在 BizTalk Server 說明中。  
  
 可使用兩種方法讓主要密碼伺服器可用：  
  
- **可供使用，但不是高度可用**。 您可以建立主要密碼伺服器變成無法使用，然後您可以再手動升階主要密碼伺服器並還原主要祕密，在此伺服器上的另一部 SSO 伺服器時通知您的 Microsoft System Center Operations Manager 事件。  
  
   雖然這項設定不具高可用性，它仍可滿足大部分的情況下，而且與向外擴充接收、 傳送和處理主控件一致。  
  
- **高可用性**。 若要提供主要密碼伺服器的備援，請在不同的主要密碼伺服器叢集上使用 Windows 叢集，或在現有的資料庫叢集上設定主要密碼伺服器。 主要密碼伺服器所提供的服務不會耗用太多資源，且在資料庫叢集上安裝時，通常不會影響資料庫的功能或效能。 下圖顯示如何讓主要密碼伺服器高度可用。  
  
   ![高可用性的主要密碼伺服器](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")  
  
   雖然此組態高度可用，它仍然需要額外的硬體資源。 如需 sso 的高可用性安裝選項的詳細資訊，請參閱[高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(http://go.microsoft.com/fwlink/?LinkId=156838)在 BizTalk Server 說明中。  
  
   本節包含設定為高可用性的叢集資源的 SSO 主要祕密伺服器上的詳細的資訊[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集。  
  
  > [!NOTE]
  >  若要減少高度可用的方案的硬體資源，可以將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。 請注意，您不需要購買其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]授權，才能安裝 SSO 服務在執行 SQL Server 的電腦上。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)  
  
-   [手動指定新的主要密碼伺服器](../technical-guides/designating-a-new-master-secret-server-manually.md)  
  
## <a name="see-also"></a>另請參閱  
 [規劃高 Availability2](../technical-guides/planning-for-high-availability2.md)   
 [BizTalk 主控件的的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)