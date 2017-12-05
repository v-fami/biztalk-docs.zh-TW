---
title: "自訂 BAM 入口網站組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 507bd5f0-b2a0-4d52-85f8-9d984138ca79
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd99c0746c09f88d71e3a44e625ae5c52458f2f3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="customizing-the-bam-portal-configuration"></a>自訂 BAM 入口網站組態
BAM 入口網站上有許多組態選項。 下列程序顯示如何修改 BAM 入口網站，以獲得最佳使用者體驗。  
  
> [!NOTE]
>  以非系統管理員的模擬使用者設定入口網站時，您可能必須在存取 BAM 入口網站功能前先登出再登入，以避免系統要求您輸入認證。 例如，考慮下列實例：  
>   
>  您使用非系統管理員的模擬使用者設定 Web 服務或 BAM 入口網站。 接著，您在入口網站上設定使用權限，如此 Everyone 群組便沒有入口網站的存取權限。 然後，您建立名為 PortalUsersGroup 的本機群組，並指派該群組為「入口網站使用者群組」。 這表示只有該群組中的使用者可以存取入口網站。 設定 BAM 入口網站之後，請將目前使用者新增至「入口網站使用者群組」。 當您開啟 BAM 入口網站時，系統將會要求您輸入認證。 然而，如果您登出並再次登入，就可以直接開啟 BAM 入口網站，而不會被要求輸入認證。  
>   
>  BizTalk Server 僅在單一電腦組態中支援本機群組和使用者帳戶。 BizTalk Server 在單一電腦組態和多電腦組態中都支援網域群組和使用者帳戶。  
  
## <a name="running-the-bam-portal-in-a-64-bit-environment"></a>在 64 位元環境中執行 BAM 入口網站  
 如果您在 64 位元環境中使用網際網路資訊服務 (IIS)，您必須設定 IIS 以 32 位元模式來執行 BAM 入口網站。 
  
> [!IMPORTANT]
>  您不需要將 IIS7 設定為 32 位元模式。  
  
#### <a name="to-set-a-64-bit-mode-iis-installation-to-32-bit-mode"></a>若要將 64 位元模式的 IIS 安裝設定成 32 位元模式  
  
1.  開啟命令提示字元並執行**adsutil**命令。 若要這樣做，請按一下**啟動**，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令提示字元輸入下列命令： `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`。  
  
3.  關閉命令提示字元。  
  
## <a name="configuring-the-bam-portal-banner"></a>設定 BAM 入口網站橫幅  
 您可以修改 BAM 入口網站頁面，以顯示與商務相關的文字和圖形：  
  
-   Windows Server System 標誌，位於 BAM 入口網站頁面的右上角。  
  
 在下列程序中，您將編輯階層式樣式表檔案 (.css 檔案) 以自訂 BAM 入口網站的外觀。 只支援修改特定的類別。 修改類別所造成的影響已經儘可能地加以隔離，如此，在修改過程中造成的錯誤會將 BAM 入口網站保持在運作狀態。  
  
> [!CAUTION]
>  修改 styles.css 檔案中的其他類別將會隱藏資料和入口網站功能，並且可能造成入口網站無法使用。  
  
#### <a name="to-configure-the-banner"></a>若要設定橫幅  
  
1.  編輯 BAM 入口網站的 web.config 檔案。 若要這樣做，請按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。  
  
2.  主頁面的快速入門內容是可取代藉由修改下行：\<新增機碼 ="MainPageContentUrl"value="~/MainPageContent.htm"/\>。 變更**MainPageContent.htm**值欄位，以指向您自己的 HTML 檔案中。 HTML 檔案必須位於與 web.config 檔案相同的目錄中。  
  
3.  變更頁面識別文字將下列這一行加入至 web.config 檔案：\<新增機碼 ="PortalTitle"value ="新識別 text"/\>。 變更數值欄位以包含用來識別入口網站的文字。  
  
4.  編輯 BAM 入口網站的 styles.css 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\Styles.css，然後再按一下**確定**。  
  
5.  尋找找出.headerLogo div 類別，並將下列行以變更右上角中的標誌： 背景影像： url("../ images/WSS_Logo.gif");以指向您所建立的映像檔。 我們建議您使用 .gif 格式影像。  
  
6.  找出.headerPageIcon div 類別，並將變更下列行以變更 SharePoint 圖示： 背景影像： url("../ images/btsSuiteProduction.gif");以指向您所建立的映像檔。  
  
7.  儲存檔案。  
  
8.  開啟 BAM 入口網站以檢視變更。  
  
## <a name="modifying-the-bam-portal-webconfig-file"></a>修改 BAM 入口網站的 web.config 檔案  
 如果您的 BAM 入口網站位於使用企業單一登入 (SSO) 憑證以實作安全通訊端層 (SSL) 的伺服器上，您必須設定入口網站接受適當的憑證 URL。  
  
#### <a name="to-modify-the-bam-portal-to-support-ssl-sites"></a>若要修改 BAM 入口網站以支援 SSL 網站  
  
1.  使用 [記事本] 開啟 web.config 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。  
  
2.  修改檔案中的下列兩行以指向啟用 SSL 的入口網站位置：  
  
    ```  
    <add key="BamQueryWSUrl" value="http://localhost/BAM/BamQueryService/BamQueryService.asmx"/>  
    <add key="BamManagementWSUrl" value="http://localhost/BAM/BamManagementService/BamManagementService.asmx"/>  
    ```  
  
3.  儲存檔案。  
  
 BAM 入口網站會根據所設定的文化特性顯示並接受格式化的資料。 組態可以在 web.config 檔案中指定。 入口網站會忽略 Internet Explorer 所傳送的「接受語言」資訊。 例如，假設您正在執行 Internet Explorer，設定為 「 日文 」 文化特性設定，而且已經設定 BAM 入口網站，用於在美國太平洋時區英文文化特性設定。 在此情況下資料項目，例如日期和整數，將會顯示，接受，以及使用適用於在美國太平洋時區的排序英文的文化特性設定而不是日文 」 文化特性設定適用的規則。 使用 「 日文 」 格式輸入任何特定文化特性的資訊會視為無效，BAM 入口網站因為它預期能美國的格式化資料英國)」。  
  
 若要以一致的處理方式顯示和格式化隨著文化特性設定而變更的資料，請選擇適用於所有 BAM 入口網站用戶端的語言。 請設定 BAM 入口網站使用此文化特性。 您必須確認每個用戶端都已安裝「多語系使用者介面 (MUI) 套件」且已設定為選擇的文化特性。  
  
 非美國地區BAM 的英文版安裝可能需要在 web.config 檔案中設定文化特性參數。 在下列情況中，您可能需要執行這項操作：  
  
-   當地語系化日期和時間顯示的格式。  
  
-   當地語系化貨幣顯示的格式。  
  
#### <a name="to-modify-the-culture-setting-of-the-portal"></a>若要修改入口網站的文化特性設定  
  
1.  使用 [記事本] 開啟 web.config 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。  
  
2.  修改檔案下列行中的文化特性屬性，以反映適當的全球化設定：  
  
    ```  
    <globalization requestEncoding="utf-8" responseEncoding="utf-8" culture="de-DE" uiCulture="en" />  
    ```  
  
3.  儲存檔案。  
  
 如果您在等候大量 SQL 查詢時遇到逾時的情形，可能必須增加查詢服務逾時值。  
  
#### <a name="to-increase-the-query-service-time-out-value"></a>增加查詢服務逾時值  
  
1.  使用 [記事本] 開啟 web.config 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config，然後再按一下**確定**。  
  
2.  QueryServiceTimeout 的預設值為 45 秒。 請修改下列行中的值以增加或減少逾時間隔：  
  
    ```  
    <add key="QueryServiceTimeout" value="45" />  
    ```  
  
3.  儲存檔案。  
  
 在多伺服器環境中，有時可能會發生伺服器離線的情況。 發生這種情況時，入口網站的使用者可能因為 BAM 入口網站停止回應而遭遇到時間延遲。 為了改善使用者體驗，您可以修改伺服器重試間隔。 這將會增加 BAM 查詢 Web 服務在連線失敗後，假設伺服器處於離線狀態的最小時間。  
  
 這個值表示，如果本機資料庫嘗試連線遠端資料庫逾時，資料會標示為未完成，並且本機電腦在經過指定的時間之前，將不會嘗試連線到遠端資料庫。  
  
#### <a name="to-increase-the-retry-interval-for-distributed-activities-in-a-multiserver-environment"></a>若要增加多伺服器環境中分散式活動的重試間隔  
  
1.  使用 [記事本] 開啟 web.config 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config，然後再按一下**確定**。  
  
2.  ServerRetryInterval 的預設值為 5 分鐘。 請修改下列行中的值以增加或減少伺服器重試間隔：  
  
    ```  
    <add key="ServerRetryInterval" value="5"/>  
    ```  
  
3.  儲存檔案。  
  
#### <a name="to-configure-how-alert-notification-options-are-presented-in-the-bam-portal"></a>若要設定 BAM 入口網站顯示警示通知選項的方式  
  
1.  使用 [記事本] 開啟 web.config 檔案。 按一下**啟動**，按一下 **執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。  
  
2.  修改中的數值欄位\<新增機碼 ="AlertNotificationOptions"value =""/\>逗點分隔的清單，指定有效的通知選項與下列值之一的 web.config 檔案的行。 如果設定為空值，將會以伺服器傳回的順序在伺服器上顯示所有可用的通知選項。 任何無法辨識的值同等於空值。  
  
    |值|Description|  
    |-----------|-----------------|  
    |檔案、電子郵件|顯示檔案和電子郵件選項。 在下拉式清單中，會先顯示檔案，再顯示電子郵件。|  
    |電子郵件、檔案|顯示檔案和電子郵件選項。 在下拉式清單中，會先顯示電子郵件，再顯示檔案。|  
    |檔案|只會在入口網站中顯示「檔案」通知。|  
    |Email|只會在入口網站中顯示「電子郵件」通知。|  
  
3.  儲存檔案。  
  
## <a name="distributed-server-environments"></a>分散式伺服器環境  
 如果您安裝 BAM 入口網站會將警示和 BAM 入口網站放在不同伺服器上，您會看到事件記錄檔中的下列錯誤:"System.Reflection.TargetInvocationException: 叫用的目標傳回例外狀況。 ---> 的登錄中找不到指定的 Notification Services 執行個體的項目。 」  
  
#### <a name="to-configure-the-portal-and-alerts-on-different-servers"></a>若要在不同伺服器上設定入口網站和警示  
  
1.  開啟命令提示字元。  
  
2.  執行**C:\Program Files\Microsoft SQL Server\90\Notification Services\9.0.242\Bin\nscontrol register-name bamalerts-server***\<伺服器名稱\>*取代*\<伺服器名稱\>*與伺服器的名稱。  
  
3.  按下 F5 以重新整理瀏覽器。  
  
## <a name="configuring-iis-to-allow-the-bam-portal-to-use-the-kerberos-network-protocol"></a>設定 IIS 以允許 BAM 入口網站使用 Kerberos 網路通訊協定  
 如果您想要在 BAM 入口網站使用 Kerberos 網路通訊協定，您必須修改入口網站的 ACL 安全性。 如果 IIS 未正確地設定，使用者將收到下列錯誤：  
  
 HTTP 錯誤 401.1-未經授權： 因為認證無效而拒絕存取。  
  
 如需有關修改 IIS 安全性設定的詳細資訊，請參閱知識庫文章，網址[http://go.microsoft.com/fwlink/?LinkId=57922](http://go.microsoft.com/fwlink/?LinkId=57922)。  
  
## <a name="viewing-aggregate-bam-data-in-the-bam-portal-in-sql-server-2008--deployments"></a>在 SQL Server 2008 部署 BAM 入口網站中檢視彙總 BAM 資料  
 若要檢視 BAM 入口網站，從用戶端電腦連線到 BAM 入口網站時的部署環境使用 SQL Server 2008 中的彙總資料，您必須在用戶端電腦上安裝 Microsoft SQL Server 2008 Analysis Services 10.0 OLE DB 提供者。 如果未安裝分析服務，使用者便會收到下列錯誤訊息：  
  
 伺服器 *\<servername\>* 無法連絡或太忙碌。  
  

  
## <a name="see-also"></a>請參閱  
 [規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)