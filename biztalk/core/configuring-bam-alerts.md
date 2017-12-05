---
title: "設定 BAM 警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, alerts
- alerts, timeout values
- Notification Services, configuration tips
- alerts, configuring
- managing [BAM definitions], configuring alerts
ms.assetid: 29327466-c8e9-41e8-bc12-f3ac6b5d3096
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8198b17d07288bff04b64b0a1ad05db0cde4fd91
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-bam-alerts"></a>設定 BAM 警示
系統管理員可以修改 BAM 警示架構的特定項目。 本主題描述系統管理員可以使用的組態選項。  
  
> [!NOTE]
>  建立警示時，請務必記得，時間資料是以本地時間格式儲存在 OLAP、星狀結構描述以及 Notification Services 資料庫中。 同時假設這三個資料庫都位於相同時區。 在主要匯入資料庫上，資訊是以 UTC 時間格式儲存，可以是同一個時區，也可以是不同時區。  
  
## <a name="changing-the-adf-configuration"></a>變更 ADF 組態  
 部署 BAM 管理公用程式會使用 bm.exe.config 檔案中指定的 CommandTimeout 值來填入 Notification Services 應用程式定義檔的檢視時\<EventRule\>\\< ActionTimeout\>項目。  
  
 變更 bm.exe.config 中的 CommandTimeout 值，並不會影響變更前所部署檢視的 CommandTimeout 值。  
  
 下列程序使用 ProcessBamNSFiles.vbs 取得組態檔案與 Notification Services 應用程式定義檔案。 如需有關此指令碼的詳細資訊，請參閱[BAM Notification Services 組態檔的命令列指令碼](../core/bam-command-line-script-for-notification-services-configuration-files.md)。  
  
 如何變更已部署檢視 NS 的 ActionTimeout：  
  
#### <a name="to-change-the-command-timeout-value"></a>變更命令逾時值  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽至追蹤資料夾，在命令提示字元中輸入**cd"C:\Program Files\Microsoft BizTalk Server\<版本\>\Tracking"**或**cd"C:\Program Files (x86) \Microsoft BizTalk伺服器\<版本\>\Tracking"** 64 位元電腦上。 按 ENTER 鍵。  
  
3.  擷取 ADF 檔案。 型別**cscript ProcessBamNSFiles.vbs-Get \<ConfigFilePath\> \<組態檔路徑\> \< PID Server\> \< PID 資料庫\>** . 請以適合您安裝的值取代 ConfigFilePath、ADFFilePath、PID Server 與 PID database。  
  
4.  按 ENTER 鍵。  
  
5.  在編輯器中開啟 ADF 檔案，並搜尋\<ActionTimeout\>、 更新與所要的值，並請注意，這個值會是 XML 持續時間。  
  
6.  儲存 ADF 檔案。 型別**cscript ProcessBamNSFiles.vbs-Update \<ConfigFilePath\> \<組態檔路徑\> \< PID Server\> \< PID 資料庫\>**.  
  
7.  按 ENTER 鍵。  
  
### <a name="notification-service-configuration-tips"></a>Notification Service 設定秘訣  
 如果您將 BAM 警示設定成在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的遠端電腦上放置警示資料庫，則此 SQL Server 執行個體上必須安裝 Notification Services 資料庫元件。 如果 SQL 執行個體上沒有這些元件，BAM 警示的組態將會失敗並傳回錯誤，指出無法將權限授與 Notification Services 延伸預存程序。 如需有關安裝 Notification Services 元件的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999)。  
  
 BAM 可以讓您變更 BAM 存取 Notification Services 所使用的帳戶。 如果您不是透過執行 NSControl 來變更此帳戶，將會收到錯誤，通知您使用 NSControl 變更帳戶。  
  
> [!NOTE]
>  您不能使用 LocalSystem 或 SYSTEM 帳戶來安裝和設定 Notification Services。 您無法登入一些特殊帳戶，而且不能用這些帳戶來對 BAM 警示使用者授與檔案和 SQL Server 權限。  
>   
>  若要安裝和設定 Notification Services，請在本機電腦上建立新的使用者帳戶，對其授與所有必要權限，然後使用該帳戶來設定 Notification Services。  
  
##### <a name="to-change-ns-user-account-for-bam"></a>變更 BAM 的 NS 使用者帳戶  
  
1.  請使用 NSControl 更新使用者帳戶。  
  
2.  授與 NS 使用者讀取、寫入與變更 BAM 警示檔案位置共用的權限。  
  
3.  新增 NS 使用者做為 BAMAlerts 執行個體和應用程式資料庫中 NSRunService 角色的成員。  
  
4.  權利授與 NS 使用者本機上使用的文件[http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005)。  
  
5.  授與 NS 資料庫權限 ns 根據[http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008)。  
  
6.  授與 NS 使用者登入 SQL 伺服器以及存取主要匯入資料庫的權限。  
  
7.  將 NS 使用者新增至 BAM_ManagmentNSReader SQL 角色。  
  
8.  將 NS 使用者新增至 BamAnalysis 資料庫中的「BAM 警示」角色。  
  
 如果您修改檔案所傳遞之警示的檔案放置位置， 就必須重新啟動 SQL Notifications Services。  
  
 如果 NS 服務未重新啟動，將會繼續傳遞警示至原始檔案放置位置。  
  
 修改 BAM 組態檔案的下面這一列，並使用 BAM 管理公用程式 update-config 命令，即可變更檔案放置位置。  
  
 \<屬性名稱 ="FileDropUNC"\>\\\\< 電腦名稱\>\alerts\</Property\>  
  
 如需 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。