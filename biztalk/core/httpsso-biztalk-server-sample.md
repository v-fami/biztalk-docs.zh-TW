---
title: "HTTPSSO （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- SSO, examples
- SSO, HTTP adapters
- examples, HTTP adapters
- HTTP adapters, SSO
- examples, SSO
ms.assetid: 322360df-81d2-4a73-9512-bda9382351a2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f056b05c492e0ca4151c5a70652ee74ea46a464
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="httpsso-biztalk-server-sample"></a>HTTPSSO （BizTalk Server 範例）
HTTPSSO 範例將示範如何搭配 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器使用「企業單一登入」(SSO) 功能。  
  
> [!NOTE]
>  64 位元作業系統不支援這個範例。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會示範使用 SSO 和 BizTalk HTTP 傳送和接收配接器模擬 SSO 如何允許使用者不需提供額外認證以登入非 Microsoft Windows 系統之後通過 Windows 驗證的端對端案例。  
  
 此範例還會使用 SSO 管理和對應模組，建立使用 SSO 之 interop 用戶端 DLL 的分支機構應用程式和 SSO 對應。  
  
 此範例將示範透過實作下列各方面的端對端實例使用 SSO：  
  
-   表示 Microsoft 網際網路資訊服務 (IIS) 虛擬目錄設定為使用 Windows 整合式的驗證的使用者介面。  
  
-   設定為使用基本驗證的 IIS 虛擬目錄所代表的後端系統。  
  
-   SQL 範例資料庫 Northwind 所代表的後端資料庫。  
  
 此範例假設您已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SSO。 您必須擁有系統管理員權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，IIS、 SSO 和 COM + Windows XP Professional 上。 您也必須是 SSO 系統管理員、BizTalk Server 系統管理員和 BizTalk 外掛式主控件使用者 Windows 群組的成員。  
  
 有效使用此範例的前提為，您具備 SSO 和 BizTalk HTTP 配接器的足夠知識。 例如，您應該了解什麼是 SSO 內容中的分支機構應用程式。 如需這些主題的資訊，請參閱[使用 SSO](../core/using-sso.md)。 另請參閱[HTTP 配接器](../core/http-adapter.md)。  
  
 在您完成設定之後，此範例的運作方式如下：  
  
1.  當您按一下**完成**在此範例使用者介面的精靈應用程式，Internet Explorer 的執行個體啟動並傳遞 BizTalk HTTP 接收 DLL 的 URL。  
  
2.  BizTalk Server 搭配 SSO 便能有效地將 HTTP 要求轉寄至已設定為使用基本驗證的 IIS 虛擬目錄中的 EmployeeData.aspx 檔。 此 ASPX 檔會模擬進入非 Windows 後端系統的進入點。 由於您使用的是 SSO，因此 HTTP 要求會包含設定為模擬登入帳戶至所模擬後端系統的憑證。  
  
3.  ASPX 檔會存取修改的 SQL 範例資料庫 Northwind 版本，以擷取對應至模擬後端系統憑證的員工資料。  
  
4.  ASPX 檔會在 HTTP 回應中傳回擷取的員工資料。  
  
5.  BizTalk Server 會將 HTTP 回應傳遞至 Internet Explorer，而 Internet Explorer 會對使用者顯示傳回的員工資料。  
  
 如果您略過 BizTalk Server 和 SSO，並且直接瀏覽至 EmployeeData.aspx 檔，則 Windows 對話方塊會提示您提供憑證。  
  
 如需範例，示範如何使用命令列公用程式 ssomanage.exe 設定 SSO，例如建立分支機構應用程式和使用者對應，請參閱[管理 （BizTalk Server 範例）](../core/manage-biztalk-server-sample.md)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*> \SSO\HTTPSSO\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs，SsoSample.csproj|此 HTTP SSO 範例的專案及相關檔案。|  
|SsoSample.cs|構成此範例大部分的 HTTP SSO 圖形應用程式的最上層 Microsoft Visual C# 原始程式檔。 這個檔案包含名為類別中的 SSO 組態程式碼**SsoConfigurator** ，最終都會是這個範例的點。|  
|在 \Scripts 資料夾中：<br /><br /> EmployeeData.aspx|當員工直接或使用 SSO 發出檢視個人資料的要求時，用來存取和查詢後端資料庫 (在此案例中為 SQL Northwind 資料庫)。|  
|在 \Scripts 資料夾中：<br /><br /> ValidateUser.aspx|直接或使用 SSO 簡單進行測試以驗證使用者，並報告該使用者是否通過驗證。|  
|在 \UI 資料夾中：<br /><br /> AddApplication.cs、AddApplication.resx、AddMapping.cs、AddMapping.resx、App.ico、BtsPage.cs、BtsPage.resx、ExecutePage.cs、ExecutePage.resx、FinishPage.cs、FinishPage.resx、IisPage.cs、IisPage.resx、InfoPage.cs、InfoPage.resx、PageBase.cs、PageBase.resx、SsoPage.cs、SsoPage.resx、SsoSampleWizard.cs、SsoSampleWizard.resx、WelcomePage.cs、WelcomePage.resx、WorkPage.cs、WorkPage.resx|輔助 Visual C# 原始程式檔及其相關的 XML 格式資源檔，用於構成此範例大部分的 HTTP SSO 圖形應用程式。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-httpsso-sample"></a>建置與初始化 HTTPSSO 範例  
  
1.  建立 Microsoft Internet Information Services (IIS) 可用於基本驗證的本機 Windows 帳戶。 SSO 會將 Windows 網域帳戶對應至此本機 Windows 帳戶。 例如，使用您的姓氏建立本機 Windows 帳戶。  
  
    > [!NOTE]
    >  如果您是在網域控制站上執行，則可以建立網域帳戶並將您的登入網域帳戶對應至此帳戶。  
  
2.  使用 Microsoft SQL Server Enterprise Manager，開啟**員工**資料表中的 Northwind 範例資料庫，然後再加入對應至您剛剛建立，包括的各種範例資料的本機 Windows 帳戶的資料列資料行。 您新增至 [員工] 資料表中 [姓氏] 資料欄的值，必須與您在步驟 1 中新增的本機 Windows 帳戶的使用者名稱相同。  
  
3.  確認 ASP.NET 帳戶 (ASPNET) 具備 Northwind 資料庫的讀取權限。  
  
4.  使用 Visual Studio 開啟專案檔 SsoSample.csproj。  
  
5.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  
  
    > [!NOTE]
    >  此時可能會要求您先儲存方案檔，才能繼續建置。  
  
     如果您找不到專案的下列 BizTalk 組件參照，請將它們刪除，再從指示的位置重新加入，並且再次建置：  
  
    -   **Microsoft.BizTalk.ExplorerOM**。 根據預設，Microsoft.BizTalk.ExplorerOM.dll 檔位於資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]開發人員工具\\。  
  
    -   **Ipropertybag**。 根據預設，Microsoft.BizTalk.Interop.SSOClient.dll 檔位於資料夾\< *ProgramFiles*> 單一登入 \Common Files\Enterprise\\。  
  
     這樣做會在下列資料夾中產生可執行檔 SsoSample.exe：  
  
     \<*範例路徑*> \SSO\HTTPSSO\bin\Debug\  
  
## <a name="running-this-sample"></a>執行此範例  
  
> [!NOTE]
>  如果您在 IIS 6.0 上以「背景工作處理序隔離模式」執行此範例，系統會為這兩個虛擬目錄建立應用程式集區。 您必須在 Windows 帳戶中手動設定這兩個應用程式集區的識別 (您可以在 Internet Information Services Manager 中設定識別)。  
  
#### <a name="to-run-the-httpsso-sample"></a>執行 HTTPSSO 範例  
  
1.  執行可執行檔 SsoSample.exe，該檔案位於下列資料夾中：  
  
     \<*範例路徑*> \SSO\HTTPSSO\bin\Debug\  
  
     此範例的精靈應用程式隨即開啟。  
  
2.  在 [歡迎使用] 頁面上，接受預設設定來設定 IIS、 SSO 和 BizTalk 中，，然後按**下一步**。  
  
3.  在 IIS 組態 頁面上，接受預設設定的兩個 IIS 虛擬目錄來建立，然後按一下您想**下一步**。  
  
4.  在 SSO 組態 頁面上，接受預設設定分支機構應用程式，也就是可存取使用**新增應用程式** 按鈕。  
  
5.  在 SSO 組態 頁面上，接受大部分的使用者對應，預設設定可存取使用**新增對應** 按鈕。 根據建置和啟始此範例時新增的本機 Windows 帳戶，為下面兩個設定提供值。  
  
    |設定|值|  
    |-------------|-----------|  
    |外部使用者名稱|設定為新增的本機 Windows 使用者帳戶名稱。|  
    |外部使用者密碼|設定為新增的本機 Windows 使用者帳戶密碼。|  
  
6.  在 SSO 組態] 頁面上，按一下 [**下一步**。  
  
7.  在 BizTalk 組態 頁面上，接受預設設定為傳送和接收連接埠，並依此類推，，然後按一下**下一步**。  
  
    > [!NOTE]
    >  您可以變更預設的傳送埠設定，從**EmployeeData.aspx**至**ValidateUser.aspx**如果您想要看到簡單的使用者驗證，而非範例資料取自的 Employee 資料表Northwinds SQL 資料庫。 進行這項變更會改變之後按一下 瀏覽器中顯示的輸出**完成**在步驟 9。  
  
8.  查閱對應至所執行 IIS、SSO 和 BizTalk 組態的狀態訊息。 您可以找到此階段中執行的程式碼**IisConfigurator**， **SsoConfigurator**，和**BtsConfigurator** ssosample.cs 中定義的類別。 組態完成之後，請按一下**下一步**。  
  
9. 在精靈應用程式的最後一個頁面上，接受預設設定**啟動瀏覽器在**(選取的核取方塊和 url http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll? 文字方塊\<訊息 / >)，然後按一下 **完成**。  
  
     Internet Explorer 的執行個體將會開啟，並且很快地顯示您新增至 Northwinds SQL 資料庫的 [員工] 資料表中的範例員工資料。  
  
 基於比較的目的，您可以略過 BizTalk 和 SSO，並直接瀏覽至任一個 ASPX 檔：  
  
-   http://localhost/SsoSampleServerApplication/ValidateUser.aspx  
  
-   http://localhost/SsoSampleServerApplication/EmployeeData.aspx  
  
 在這兩個案例中，由於您略過 BizTalk 和 SSO，因此會提示您提供 IIS 的驗證資訊 (使用您之前建立的本機 Windows 帳戶資訊)。  
  
## <a name="comments"></a>註解  
 SsoSample.exe 精靈應用程式會設定這兩個 IIS 虛擬目錄：  
  
-   第一個虛擬目錄設定為使用 Windows 整合式驗證，並且對應至 BizTalk HTTP 接收 ISAPI 延伸模組。 該目錄必須與位於下列資料夾中的 .dll 檔 BTSHTTPReceive.dll 相關：  
  
     \<*安裝路徑*> \HttpReceive  
  
-   第二個虛擬目錄設定為使用基本驗證，並且會模擬接受使用者識別碼和密碼來驗證使用者的後端系統。 該目錄必須與位於下列資料夾中的任一個 ASPX 檔 ValidateUser.aspx 或 EmployeeData.aspx 相關：  
  
     \<*範例路徑*> \SSO\HTTPSSO\Scripts  
  
 您可以使用 SsoSample.exe 精靈應用程式設定一或多個分支機構應用程式。 針對每個分支機構應用程式，可以建立一或多個使用者對應。 每個使用者對應都會將一個 Windows 使用者帳戶對應到您用來存取特定後端系統的帳戶。 在此範例中，該帳戶為您用來對模擬實際後端系統的第二個 IIS 虛擬資料夾驗證的本機 Windows 帳戶。  
  
 若要重新執行此範例，可從下列數個選項中選擇：  
  
-   直接瀏覽至 Internet Explorer 中的下列 URL：  
  
     http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?\<訊息 / >  
  
-   再次執行精靈應用程式，但清除第一頁上的所有組態設定核取方塊。  
  
-   再次執行精靈應用程式，保留第一頁上選取的組態設定何取方塊，但謹慎且適當地設定其他 BizTalk 項目、分支機構應用程式等，以避免發生組態錯誤。  
  
 若要清除此範例，請使用下列程序。  
  
#### <a name="to-clean-up-from-this-sample"></a>清除此範例  
  
1.  採取適當的方式，反向您執行的手動組態設定，例如移除本機 Windows 帳戶。  
  
2.  移除對應至虛擬目錄的 IIS 應用程式，然後刪除此範例建立的 IIS 虛擬目錄。  
  
3.  使用 [BizTalk 管理] 主控台取消登錄，然後刪除與此範例關聯的傳送埠。 接著刪除與此範例相關的接收埠 (及其接收位置)，  
  
4.  使用 Ssomanage 應用程式 (位於 Files\Enterprise Single Sign-on \Program Files\Common\\) 若要刪除此範例的 SSO 應用程式：  
  
    ```  
    Ssomanage –deleteapp SsoSampleApplication  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [SSO （BizTalk Server 範例資料夾）](../core/sso-biztalk-server-samples-folder.md)