---
title: "檢查清單： 設定 Windows Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebd7ea95-cc73-4c98-a796-193f394fb5b8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bffa095c4ed5834f93b3a8634915214ac7b9530
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-configuring-windows-server"></a>檢查清單： 設定 Windows Server
本主題列出 Windows Server 準備用於生產環境時所應遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
##  <a name="BKMK_Win2k8"></a>設定 Windows Server  
  
|步驟|參考|  
|-----------|---------------|  
|設定 MSDTC 以提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|-了解[如何啟用 BizTalk Server 上的 MSDTC](http://go.microsoft.com/fwlink/?LinkId=153236) (http://go.microsoft.com/fwlink/?LinkId=153236)。<br />-了解[MSDTC 問題疑難排解](http://go.microsoft.com/fwlink/?LinkId=153237)(http://go.microsoft.com/fwlink/?LinkId=153237)。|  
|設定為以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 **附註：**這個步驟是只需要一個或多個防火牆是否在位置中您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。|-了解[BizTalk Server 所需的連接埠](http://go.microsoft.com/fwlink/?LinkId=153238)(http://go.microsoft.com/fwlink/?LinkId=153238)。<br />-請參閱 Microsoft 知識庫文章 154596， [< 如何設定 RPC 動態連接埠配置以使用防火牆 >](http://go.microsoft.com/fwlink/?LinkId=153239) (http://go.microsoft.com/fwlink/?LinkId=153239)。|  
|關閉所有執行的電腦上的超執行緒[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。|-相當重要，該超執行緒執行的電腦已關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這是電腦的 BIOS 設定，通常位於 BIOS 設定的處理器設定。 超執行緒會讓伺服器可能沒有更多的處理器/處理器核心比實際;不過，超執行緒處理器通常介於 20%到 30%的實體處理器/處理器核心的效能之間提供。 當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]計數調整自我調整演算法，超執行緒處理器的處理器數目會導致這些調整會扭曲，即不利於整體效能。<br />-應該關閉超執行緒的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦因為可能會造成競爭的高等級的應用程式 (例如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) 可能會造成效能降低超執行緒的環境中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。|  
|請確定 Windows Server 處理器排程設為 「 背景服務 」。|確保您的環境中執行 Windows Server 的所有電腦上設定此組態選項，將會改善整體系統效能。 請遵循這些步驟，以確保 Windows 伺服器設定為喜好背景服務：<br /><br /> 1.按一下**啟動**，按一下 **執行**，然後輸入**sysdm.cpl**中**執行**方塊。<br />2.在**系統屬性**對話方塊中，按一下 **進階**索引標籤，然後再按一下**設定**下**效能**。<br />3.在**效能選項**對話方塊中，按一下 **進階**索引標籤上，請確定**背景服務**選項底下**處理器排程**，按一下**確定**，然後按一下  **確定**  以關閉 **系統屬性** 對話方塊。|  
|將 Windows 分頁檔，在個別的本機實體磁碟機。|執行 Windows Server 的電腦上，將分頁檔移到不同的實體磁碟區以外的作業系統會提高效能降低磁碟爭用情況。<br /><br /> 請遵循下列步驟，將分頁檔移至不同的實體磁碟區以外的作業系統：<br /><br /> 1.按一下**啟動**，按一下 **執行**，然後輸入**sysdm.cpl**中**開啟**方塊。<br />2.按一下**進階**索引標籤，然後再按一下**設定**下**效能**。<br />3.按一下**進階**索引標籤上，按一下 **變更**下**虛擬記憶體**、 指定的分頁檔的選項，請按一下**確定**然後按一下**確定** 以關閉 系統內容。 **注意：**您必須重新啟動電腦，新設定才會生效。|  
|-所有磁碟都重組 (本機和 SAN/NAS) 上定期排程離峰時間磁碟重組。<br />重組 Windows 分頁檔，並預先配置主版檔案資料表中每個磁碟的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以提升整體系統效能。|使用[PageDefrag 公用程式](http://go.microsoft.com/fwlink/?LinkId=108976)(http://go.microsoft.com/fwlink/?LinkId=108976) 重組 Windows 分頁檔，並預先配置主檔案表格。|  
|如果執行的電腦上安裝防毒軟體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，停用的資料和交易的檔案 （.mdf、.ndf、.ldf 和.mdb） 的即時掃描。|即時掃描[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料和交易檔可以增加磁碟 I/O 競爭，並減少[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能。|  
|如果執行的電腦上安裝防毒軟體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，停用的任何參考的非可執行檔的檔案類型的即時掃描[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收位置 （通常是。XML，但也可能是.csv 或.txt 等。)。|非可執行檔所參考的即時掃描[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收位置可以增加這些檔案的 I/O 競爭，並減少[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。|  
|如果入侵偵測軟體安裝，停用網路掃描之間執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和外部資料儲存機制 ([!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]) 或訊息 （例如訊息佇列和 WebSphere MQSeries） 服務。|入侵偵測軟體可以變慢或甚至阻止在網路上的有效通訊。|  
|網路卡 (NIC) 驅動程式中的所有電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境應微調的效能。|調整要最大化的封包緩衝區、 可用的記憶體數量，傳入和傳出的網路裝置驅動程式。 也最大化緩衝區計數，尤其是傳輸緩衝區和聯合緩衝區。 預設值為這些參數，，及是否即使提供，而有所不同製造商與驅動程式版本。 目標是以最大化網路介面卡硬體，所完成的工作，並允許以降低網路流量爆發和相關聯的壅塞的網路作業的最大可能的緩衝區空間。|  
|將網路卡設定為固定的速度和雙工|使用固定的速度和雙工 (1 Gb 或更高版本與全雙工) 的 BizTalk 和 SQL 伺服器上的網路連線。 這可確保，網路介面不會不自動交涉較低速度或雙面列印設定，在過去已有些企業參數有問題。 此外，在高容量環境中，建議您擁有 Gigabit 網路。|  
|停止或停用任何不是絕對必要 （例如 列印多工緩衝處理器與索引服務） 的 Windows 服務中的所有電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。|在實際執行伺服器上執行不必要的服務會使用系統資源，否則無法使用由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [安裝 COM + Hotfix 彙總套件](../technical-guides/installing-com-hotfix-rollup-packages.md)  
  
## <a name="see-also"></a>另請參閱  
 [作業的檢查清單](../technical-guides/operations-checklists.md)