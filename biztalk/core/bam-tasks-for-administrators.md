---
title: "系統管理員的 BAM 工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d9ae9a6-50fa-4f82-8e48-8dffa55c127f
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b529a0510ee56a92d3957a84a91d635666016f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-tasks-for-administrators"></a>系統管理員的 BAM 工作
這個主題說明 BAM 系統管理員在管理 BAM 基礎結構時從事的一般工作。  
  
## <a name="configuring-bam"></a>設定 BAM  
 BAM 的初始組態是使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態精靈來完成。 使用組態精靈，系統管理員可以：  
  
-   啟用商務活動監控工具  
  
-   啟用 BAM 彙總的 SQL Server Analysis Services  
  
-   指定 BAM 工具所使用的伺服器名稱和資料庫  
  
-   啟用 BAM 警示的 SQL Server Notification Services  
  
-   指定用來執行 BAM Notification Service 的帳戶  
  
-   指定用來傳送 BAM 警示的 SMTP 伺服器  
  
-   指定用來儲存 BAM 警示的檔案位置  
  
-   指定的 BAM 警示資料庫的 SQL server 的名稱  
  
-   指定警示資料庫名稱的前置詞  
  
-   啟用電腦上的 BAM 入口網站  
  
-   指定用來執行 BAM 入口網站的 Web 服務帳戶  
  
-   指定可以存取 BAM 入口網站的 Windows 群組  
  
-   指定 BAM 入口網站的位置  
  
 如需有關使用組態精靈的詳細資訊，請參閱下列主題：  
  
-   [使用 BizTalk Server 組態設定 BAM 警示](http://msdn.microsoft.com/library/04d79f8c-9e7f-4ba8-83ce-f79c33fb8e60)  
  
-   [使用 BizTalk Server 組態設定 BAM 工具](http://msdn.microsoft.com/library/075a1627-5bc2-488c-a88c-42c86cc8c3bb)  
  
-   [設定 BAM 入口網站使用 BizTalk Server 組態](http://msdn.microsoft.com/library/8af7cccb-823e-48bd-9743-dfbba4bafa11)  
  
### <a name="distributed-notification-services"></a>分散式 Notification Services  
 將 BAM 設定在分散式環境中執行，可以在處理警示和通知時提供效能上的好處。 當您這麼做時，Notification Services 的「提供者」、「產生器」和「散發者」角色會分散在不同的電腦上，因此必須在多部電腦環境中安裝 Notification Services。  
  
##### <a name="to-configure-distributed-notification-services"></a>設定分散式 Notification Services  
  
1.  安裝 [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Notification Services。 如需有關分散式 Notification Services 的詳細資訊，請參閱[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]Notification Services 文件，網址[http://go.microsoft.com/fwlink/?LinkId=68095](http://go.microsoft.com/fwlink/?LinkId=68095)。  
  
    > [!NOTE]
    >  [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 中並未隨附 Notification Services。 如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，安裝[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Notification Services，當您安裝[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]選取**BAM Alert Provider for SQL Notification Services**選項在**其他軟體**上**元件安裝**安裝精靈頁面。  
  
2.  建立 BAM notification 執行 C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol 在分散式環境中的每一部電腦上服務 register-name bamalerts-server\<伺服器名稱 >-服務-serviceusername \<a >-servicepassword \<passwd > 從命令提示字元。  
  
3.  編輯每一台要設定為提供分散式 Notifications Service 之電腦上的 BAM 基礎結構組態檔。 若要取得組態檔，請使用**bm.exe get-config-FileName:\<輸出檔 >**命令。  
  
4.  編輯組態檔以參考分散式 Notification Services 環境中的伺服器：  
  
    ```  
    <Property Name="GeneratorServerName">PFIDWYUK</Property>  
    <Property Name="ProviderServerName">PFIDWYUK</Property>  
    <Property Name="DistributorServerName">PFIDWYUK</Property>  
    ```  
  
5.  使用 bm.exe 更新-config-FileName:\<組態檔 > 更新 BAM 組態。  
  
6.  重新啟動分散式環境中所有電腦上的 Notification Services。  
  
 如需有關在多重電腦環境中安裝 BAM 的詳細資訊，請參閱[安裝指南相關的 BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582)和[安裝及設定 BAM （商務活動監控） 在多部電腦環境](http://go.microsoft.com/fwlink/p/?LinkID=208597)。  
  
### <a name="moving-the-bam-primary-import-database"></a>移動 BAM 主要匯入資料庫  
 有時候，移動 BAM 主要匯入資料庫是必要的，例如當您升級硬體或進行擴充作業時。 若要移動資料庫，您應該執行備份和還原作業。 如需此程序的詳細資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。  
  
### <a name="working-with-bam-definitions"></a>處理 BAM 定義  
 系統管理員經常要處理 BAM 定義。 您用來處理 BAM 定義的主要工具是 BAM 管理公用程式。 您可以使用這個公用程式來執行下列工作：  
  
-   變更活動。 您可以使用**deploy-all-definitionfile**，**更新所有**，**移除活動**， **set-actvitywindow** BAM 管理公用程式的命令若要變更已部署的活動。  
  
-   將索引套用至活動資料表以增進效能。 您使用**建立索引**和**刪除索引**命令以修改活動的索引。  
  
-   設定檢視上的安全性。 您可以使用**新增帳戶**和**移除帳戶**命令，授與使用者存取檢視的權限。  
  
-   設定活動的分散式導覽。 您使用**啟用參考**和**停用參考**命令，設定活動的分散式的導覽。 如需活動的分散式導覽的詳細資訊，請參閱[管理分散式導覽的遠端活動](../core/managing-distributed-navigation-of-remote-activities.md)。  
  
-   稽核變更。 您可以列出 BAM 動態基礎結構使用變更**get 變更**命令。  
  
 如需可透過 BAM 管理公用程式的所有命令的說明，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。 如需使用 BAM 管理公用程式來處理 BAM 定義的範例，請參閱[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)。  
  
## <a name="configuring-multiple-biztalk-groups-to-reference-a-single-bam-database"></a>設定多個 BizTalk 群組參考單一 BAM 資料庫  
 當設定為使用新的或現有的 BAM[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中，您可以設定要使用相同的 BAM 資料庫已由另一個使用中的群組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  若要以這種方式設定 BAM，您必須執行下列工作：  
  
-   使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態精靈，從現有的 BAM 主要匯入資料庫取得組態資訊。 這包括伺服器及資料庫名稱。 記下核取方塊的狀態。 請務必要取得「BAM 工具」和「BAM 警示」這兩個頁面的組態資訊。  
  
-   為新的群組設定 BAM，並輸入與目標 PIT 所設定的完全相同資訊。 為新群組輸入組態資訊時，除了 BAM 警示使用者必須保留空白之外，您將會用到從現有群組收集的所有資訊來設定新群組。  
  
## <a name="backing-up-and-restoring-bam"></a>Backing Up and Restoring BAM  
 系統管理員應該為損毀修復狀況進行規劃。 您應該備份 BAM 分析、追蹤分析、BAM 星狀結構描述、BAM 封存和 BAM 主要匯入資料庫，以便在必須還原的狀況下使用。  如需備份和還原 BAM 資料庫的資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。  
  
## <a name="working-with-renamed-servers"></a>使用重新命名的伺服器  
 當您重新命名伺服器，或在伺服器之間移動 BAM 基礎結構時，就必須更新 Excel 活頁簿中的 BAM 定義以便更新該 Excel 活頁簿。  
  
 您需要更新活頁簿的情況包括：  
  
-   將 BAM 基礎結構移動到新資料庫的臨時情況。 為了確保 Excel 活頁簿繼續正常運作，您必須重新部署或移轉活頁簿，然後重新更新活頁簿。  
  
-   重新命名執行 BizTalk Server 之電腦的情況。 除了更新活頁簿之外，這個情況還需要更新 DTS 封裝和 OLAP 資料來源。  
  
 您可以用二個方法來更新 Excel 活頁簿：  
  
-   從新的伺服器執行下列 BAM 管理員命令：  
  
     **bm.exe 更新 livedataworkbook-Name:\<update.xls 即時資料活頁簿 >**  
  
    > [!NOTE]
    >  您也可以指定新的伺服器名稱和/或 BAM 主要匯入資料庫名稱： **bm.exe 更新 livedataworkbook-名稱：\<update.xls 即時資料活頁簿 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**  
  
-   或者，您也可以更新 Excel 中的 Excel 活頁簿：  
  
    1.  開啟您要更新的活頁簿。  
  
    2.  從 BAM 功能表按一下  **BAM Db 連線**。  
  
    3.  輸入新的伺服器名稱 和 BAM 主要匯入資料庫名稱。  
  
## <a name="managing-alerts"></a>管理警示  
 系統管理員管理警示的方式有數種：  
  
 您可以使用 BAM 管理公用程式進行部署和移除警示。 您也可以使用公用程式來新增和移除訂閱，以及啟用和停用警示。 如需有關如何使用 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)，[管理 BAM 安全性](../core/managing-bam-security.md)，和[管理 BAM 定義](../core/managing-bam-definitions.md)。  
  
 您也可以透過 BAM 入口網站建立和移除警示。  建立使用 BAM 入口網站的警示的詳細資訊，請參閱[BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)。  
  
### <a name="cleaning-up-the-alerts-chronicle-table"></a>清除警示紀事輯資料表  
 如果已設定 BAM 警示，就會為所建立的每個活動檢視建立 SQL 作業。 使用下列範例將會為作業命名：  
  
 bam_\<檢視名稱 > _\<活動檢視 > _DelAlertHistJob  
  
 這個工作會清除稽核資料所指定的執行個體警示\<活動檢視 > Bam_Metadata_AlertChronicle 資料表中。 如果您已經在特定的活動檢視上定義執行個體警示，則每次引發警示，此資料表就會新增新的資料列。  
  
 您可以手動執行這項作業，以清除資料表，或根據應用程式或環境的需求排程作業的執行時間。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)