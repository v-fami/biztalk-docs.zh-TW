---
title: "如何管理密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], applications
- Password Synchronization [SSO], notifications
- applications, Password Synchronization [SSO]
- SSOPS command line utility [SSO]
- administering, Password Synchronization [SSO]
- Password Synchronization [SSO], adapters
- Password Synchronization [SSO], administering
- notifications [SSO]
- Password Synchronization [SSO], SSOPS command line utility
ms.assetid: e5568cc2-7530-452c-9902-d7ffcad66088
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b85fd34a016fe013f10dd618dd551c9467d4b530
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-administer-password-synchronization"></a>如何管理密碼同步處理
您可以透過 MMC 嵌入式管理單元或命令列來管理「密碼同步」。  
  
 MMC 嵌入式管理單元會顯示配接器清單及其屬性。 您可使用滑鼠右鍵按一下配接器，再使用功能表來執行下列命令：  
  
-   建立配接器  
  
-   設定屬性  
  
-   Update  
  
-   DELETE  
  
-   啟用  
  
-   Disable  
  
-   新增應用程式至配接器  
  
-   從配接器刪除應用程式  
  
-   重設通知  
  
-   新增配接器至配接器群組  
  
-   從配接器群組刪除配接器  
  
 您也可以使用 SSOPS 命令列公用程式來管理您的密碼同步。 本節中的大部分命令僅供系統管理員使用。  
  
 對大部分命令而言，命令輸出會在畫面上顯示為兩欄。 因為特定畫面設定可能導致資料被截斷，為求最佳效果，您應將畫面緩衝區大小/Windows 大小變更為 120 個字元。  
  
 SSOPS 命令列示在下表中。 程序和進一步的說明位於本主題其他部分。  
  
|Command|函數|  
|-------------|--------------|  
|-list|列出現有的配接器|  
|-display|顯示配接器資訊|  
|-create|建立新的配接器|  
|-setprops|設定配接器屬性|  
|-update|更新現有的配接器|  
|-delete|刪除現有的配接器|  
|-enable|啟用配接器|  
|-disable|停用配接器|  
|-addapp|新增配接器的應用程式|  
|-deleteapp|刪除配接器的應用程式|  
|-reset|重設通知或禁止的佇列|  
|-addtogroup|新增配接器至配接器群組|  
|-deletefromgroup|從配接器群組刪除配接器|  
  
### <a name="to-list-existing-adapters"></a>列出現有的配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-清單**按下 Enter。  
  
     會列出配接器和描述。 (E) 代表配接器已啟用，(D) 代表配接器已停用。  
  
### <a name="to-display-adapter-information"></a>顯示配接器資訊  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-顯示\<配接器名稱 >**按下 Enter。  
  
     畫面輸出會顯示特定配接器的資訊。  
  
     除了名稱、類型、描述、電腦和帳戶之外，會顯示下列資訊。  
  
    |配接器旗標|詳細資料|  
    |------------------|-------------|  
    |啟用的配接器|決定配接器是否已啟用。<br /><br /> 旗標： SSO_FLAG_ENABLED<br /><br /> 屬性名稱： enableApp<br /><br /> 預設：否|  
    |允許本機帳戶|決定「應用程式系統管理員」或「應用程式使用者」帳戶是否可為本機帳戶。<br /><br /> 旗標： SSO_FLAG_APP_ALLOW_LOCAL<br /><br /> 屬性名稱： allowLocalAccounts<br /><br /> 預設：否|  
    |接收來自配接器的密碼變更|決定配接器是否可接收外部密碼變更。<br /><br /> 旗標： SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB<br /><br /> 屬性名稱： syncFromAdapter<br /><br /> 預設：否|  
    |驗證舊密碼|決定配接器是否將在收到外部密碼變更時驗證舊密碼。 若設定此旗標而之後有外部密碼變更，外部配接器就必須提供舊的外部密碼以及新的外部密碼。 然後比較該外部帳戶在 SSO 資料庫中的現有外部密碼與舊外部密碼。 若兩者相符，便會接受變更密碼。 若兩者不相符，便會拒絕變更密碼。<br /><br /> 旗標： SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS<br /><br /> 屬性名稱： verifyOldPassword<br /><br /> 預設：是|  
    |變更 Windows 密碼|決定收到外部密碼變更 (完全同步) 時，是否也要一併變更 Windows 密碼。 ENTSSO 永遠使用儲存在 SSO 資料庫中的舊 Windows 密碼來將 Windows 密碼變更為新值 (Windows 同時需要新舊密碼才能變更使用者密碼)，因此必須初始化才能使 Windows 密碼變更成功。 如果已針對特定對應設定密碼同步，然後當透過系統管理工具 （ssomanage 或 ssoclient-setcredentials) 設定的外部認證儲存在 SSO 資料庫中的 Windows 密碼也將。旗標： SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS<br /><br /> 屬性名稱： changeWindowsPassword<br /><br /> 預設：否|  
    |傳送 Windows 密碼變更至配接器|決定 Windows 密碼變更是否會傳送至外部配接器。<br /><br /> 旗標： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL<br /><br /> 屬性名稱： syncToAdapter<br /><br /> 預設：否|  
    |傳送舊密碼至配接器|若為 [是]，舊的密碼值 (來自 SSO 資料庫) 將會連同新的密碼值一起傳送至外部配接器。 某些外部系統可能會同時需要新舊密碼值才能變更密碼。<br /><br /> 旗標： SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS<br /><br /> 屬性名稱： sendOldPassword<br /><br /> 預設：否|  
    |允許對應衝突|決定配接器是否將允許對應衝突。<br /><br /> 當對應不是唯一時就會發生對應衝突。 在單一的 SSO 個別應用程式中，對應永遠都是一對一：一個 Windows 帳戶只會對應至一個外部帳戶，反之亦然。<br /><br /> 但是有可能會將一個以上的應用程式指派給配接器。 因此，某個應用程式中的對應可能會與另一個應用程式中的對應衝突。<br /><br /> 此旗標的用途在避免發生此情況。 除非能明確、充分瞭解此行為的需求，否則不允許發生對應衝突會較為安全。<br /><br /> 旗標： SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS<br /><br /> 屬性名稱： allowMappingConflicts<br /><br /> 預設：否|  
  
    |配接器描述|詳細資料|  
    |-------------------------|-------------|  
    |通知重試計數|預設值為 1。|  
    |通知重試延遲 (分鐘)|預設值為 5。|  
    |擱置通知的上限|預設值為 8。|  
    |存放區通知 (離線時)|True/False。|  
    |伺服器名稱|伺服器名稱。|  
    |通訊埠編號|連接埠編號。|  
    |此配接器的應用程式|目前指派給配接器的應用程式清單。|  
  
### <a name="to-create-new-adapters"></a>建立新的配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-建立\<配接器檔案 >**按下 Enter。  
  
     畫面輸出會顯示最新建立配接器的資訊。  
  
### <a name="to-set-properties-for-an-adapter"></a>若要設定配接器屬性  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-setprops\<配接器名稱 >**按下 Enter。  
  
     畫面輸出會顯示特定配接器的屬性。 如有需要，您可以編輯它們，但是不會驗證新值。  
  
### <a name="to-update-existing-adapters"></a>更新現有的配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-更新\<配接器檔案 >**按下 Enter。  
  
     使用此命令可更新特定配接器的設定和旗標。 請勿使用此命令來設定屬性；請使用 -setprops 命令替代。  
  
### <a name="to-delete-an-existing-adapter"></a>刪除現有的配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-刪除\<配接器名稱 >**按下 Enter。  
  
     將刪除指定的配接器。  
  
### <a name="to-enable-an-adapter"></a>啟用配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-啟用\<配接器名稱 >**按下 Enter。  
  
     將啟用指定的配接器。  
  
### <a name="to-disable-an-adapter"></a>停用配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-停用\<配接器名稱 >**按下 Enter。  
  
     將停用指定的配接器。  
  
### <a name="to-add-an-application-to-an-adapter"></a>新增應用程式至配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-addapp\<配接器名稱 >\<應用程式名稱 >**按下 Enter。  
  
     會將特定 SSO 應用程式指派給特定配接器。 這表示，該應用程式中對應的密碼現在將使用此配接器來同步。  
  
     多個應用程式可指派給一個配接器，但任何指定的應用程式僅能指派給一個配接器。  
  
### <a name="to-delete-an-application-from-an-adapter"></a>從配接器刪除應用程式  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-deleteapp\<應用程式名稱 >**按下 Enter。  
  
     會將特定 SSO 應用程式從配接器移除。 (因為應用程式僅可指定給一個配接器，所以不需要指定配接器名稱。)  
  
### <a name="to-reset-notification"></a>重設通知  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-重設\<配接器名稱 &#124; 所有 &#124; 禁止 >**按下 Enter。  
  
     此命令會依指定清除單一配接器或所有配接器禁止的資料表和 (或) 通知佇列。 禁止的資料表會儲存 10 分鐘的密碼變更歷程記錄。 在「企業單一登入」系統接受或傳送密碼變更之前，會檢查禁止的資料表，以查看最近是否執行過相同變更。 若有，則會捨棄變更。  
  
### <a name="to-add-an-adapter-to-an-adapter-group"></a>新增配接器至配接器群組  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-addtogroup\<配接器名稱 >\<配接器群組 >**按下 Enter。  
  
     此命令會將特定配接器新增至特定配接器群組。 配接器僅可屬於一個配接器群組，但配接器群組可包含多個配接器。  
  
### <a name="to-delete-an-adapter-from-an-adapter-group"></a>從配接器群組刪除配接器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssops-deletefromgroup\<配接器名稱 >\<配接器群組 >**按下 Enter。  
  
     此命令會刪除特定配接器群組的特定配接器。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步處理](../core/password-synchronization2.md)