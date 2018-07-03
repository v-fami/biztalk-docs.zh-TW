---
title: How to Install 虛設常式版本的服務導向解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IIS, installing virtual directories [service solutions]
- service solution tutorial, IIS virtual directories
- service solution tutorial, stub version
- deploying, BAM solutions [service solutions]
- service solution tutorial, solutions [BAM]
- service solution tutorial, service solutions
- SSO, configuring
- IBM WebSphere MQ Client
- service solution tutorial, IBM WebSphere MQ Client
- installing, tutorials
- service solutions, deploying
- service solution tutorial, SSO
- BAM, deploying solutions
- service solution tutorial, building solutions
- service solution tutorial, installing
ms.assetid: 45de7681-4df0-47a4-a02c-509140423a1e
caps.latest.revision: 53
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d42b559afb89c931aec44080beaa4c00dea89ba2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023660"
---
# <a name="how-to-install-the-stub-version-of-the-service-oriented-solution"></a>如何安裝服務導向解決方案的虛設常式版本
下列步驟描述在安裝服務導向解決方案的虛設常式版本之前，應如何準備電腦，以及如何在電腦上安裝解決方案。  
  
-   [準備安裝服務導向解決方案的虛設常式版本的電腦](#step1)  
  
-   [安裝 IBM WebSphere MQ Client for Windows](#step3)  
  
-   [在 IIS 中建立服務導向解決方案的虛擬目錄](#step5)  
  
-   [建置服務導向解決方案](#step7)  
  
-   [在 SSO 資料庫中建立的企業單一登入 (SSO) 項目和值](#step9)  
  
-   [部署服務導向解決方案的 BAM 定義](#step11)  
  
-   [部署服務導向解決方案](#step13)  
  
##  <a name="step1"></a> 準備安裝服務導向解決方案的虛設常式版本的電腦  
  
#### <a name="to-prepare-the-computer-for-installing-the-stub-version-of-the-service-oriented-solution"></a>準備安裝服務導向解決方案之虛設常式版本的電腦  
  
1. 請確定**Default Web Site**設定為使用 ASP.NET 2.X。  
  
   1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
   2.  在  **Internet Information Services (IIS) 管理員**，機器名稱時，展開**站台**，展開**Default Web Site**，展開**aspnet_client**，依序展開**system_web**。  
  
   3.  請確定子資料夾 2.X。  
  
2. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**Services**。 使用**Services**主控台中，請確定下列服務正在執行：  
  
   -   **World Wide Web 發行**  
  
3. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，按一下 **電腦管理**主控台，然後再新增以本機 Administrators 群組的 BizTalk 服務帳戶。  
  
4. 如果您安裝 Windows SharePoint Services 時，排除 （根）。 **Default Web Site**從 Windows SharePoint Services 受管理的路徑，如下所示： 按一下 **開始**，指向 **所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。  
  
   1.  底下**虛擬伺服器組態**，選取**設定虛擬伺服器設定**。  
  
   2.  在 **虛擬伺服器清單**頁面上，按一下**Default Web Site**。  
  
   3.  在 **虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。  
  
   4.  在 **包含路徑**一節**定義受管理的路徑**頁面上，選取**根**，然後按一下 **移除選取的路徑**。  
  
   5.  在命令提示字元，執行 IISReset。  
  
5. 登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。  
  
6. 開啟命令提示字元，輸入下列命令，然後按 ENTER 以設定 %BTSSolutionsPath% 環境。 然後結束命令提示字元。  
  
   - setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  
  
     > [!NOTE]
     >  若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。  
  
     > [!NOTE]
     >  如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，在[ http://go.microsoft.com/fwlink/?LinkId=67831 ](http://go.microsoft.com/fwlink/?LinkId=67831)。  
  
##  <a name="step3"></a> 安裝 IBM WebSphere MQ Client for Windows  
  
#### <a name="to-install-the-ibm-websphere-mq-client-for-windows"></a>安裝 IBM WebSphere MQ Client for Windows  
  
1. 下載最新版本的 IBM WebSphere MQ Client for Windows。  
  
   > [!NOTE]
   >  即使解決方案的虛設常式版本不需要 IBM WebSphere Server，但因為用戶端應用程式會參考 IBM WebSphere MQ Client for Windows 提供的 amqmdnet.dll 檔案，所以您必須安裝它。 虛設常式版本的用戶端實際上不會呼叫 DLL 中的 API。 只有編譯和執行用戶端應用程式才需要它。 您可以從 IBM 網站下載 IBM WebSphere MQ Client for Windows。  
  
2. 安裝 IBM WebSphere MQ Client for Windows。  
  
   > [!NOTE]
   >  您不需要設定 IBM WebSphere MQ Client for Windows。 請保留所有預設設定。  
  
3. 將 .NET 組件的 WebSphere MQ 類別新增至全域組件快取 (GAC)。  
  
   1. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，瀏覽至目錄\<IBM MQSeries 安裝目錄\>\bin。  
  
   2. 執行下列命令 (請確定 gacutil.exe 在路徑環境中)：  
  
       `gacutil.exe /i amqmdnet.dll`  
  
##  <a name="step5"></a> 在 IIS 中建立服務導向解決方案的虛擬目錄  
  
#### <a name="to-create-the-virtual-directories-in-iis-for-the-service-oriented-solution"></a>在 IIS 中建立服務導向解決方案的虛擬目錄  
  
1.  在  **Internet Information Services (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增應用程式集區**。  
  
     上**新增的應用程式集區** 對話方塊中，輸入`SSOStubAppPool`中**名稱**文字方塊中，然後按一下**確定**。  
  
     服務導向解決方案使用的虛擬目錄包括協調流程之虛設常式版本的已發佈 Web 服務、虛設常式 SAP Web 服務、虛設常式付款追蹤器 Web 服務，以及虛設常式擱置交易 Web 服務。  
  
2.  在  **Internet Information Services (IIS) 管理員**，以滑鼠右鍵按一下您剛才的應用程式集區建立，，然後按一下**進階設定**。  
  
3.  按一下右邊的資料行**身分識別**屬性，然後按一下省略符號 (**...**) 按鈕。  
  
4.  在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**選項，然後再按一下**設定**。  
  
5.  在 [**設定認證**] 對話方塊中，指定使用者名稱和密碼，確認密碼，，然後按一下**確定**。  
  
    > [!NOTE]
    >  此使用者必須具有執行協調流程 Proxy Web 服務的權限，並且必須新增至 BizTalk Server 系統管理員、SSO 系統管理員或 SSO 分支機構系統管理員群組其中之一  
  
6.  按一下 [ **[確定]** 以關閉**應用程式集區識別**] 對話方塊。  
  
7.  按一下 **[確定]** 以關閉 **[進階設定]** 對話方塊。  
  
8.  在  **Internet Information Services (IIS) 管理員**，展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**來執行**虛擬目錄建立精靈**。  
  
    1.  使用**虛擬目錄建立精靈**，為該 proxy Web 服務配接器版本建立下列虛擬目錄：  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub  
  
         路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub  
  
         存取權限 = 讀取，執行指令碼  
  
    2.  使用**虛擬目錄建立精靈**，為該 proxy Web 服務配接器版本建立下列虛擬目錄：  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  
  
         路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  
  
         存取權限 = 讀取，執行指令碼  
  
    3.  使用**虛擬目錄建立精靈**，為該 proxy Web 服務配接器版本建立下列虛擬目錄：  
  
         別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
         路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
         存取權限 = 讀取，執行指令碼  
  
    4.  使用**虛擬目錄建立精靈**，為該 proxy Web 服務配接器版本建立下列虛擬目錄：  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker  
  
         路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack  
  
         存取權限 = 讀取，執行指令碼  
  
9. 在**Internet Information Services (IIS) 管理員**，展開**Web Sites**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub，按一下**屬性**，，然後修改設定，如下所示：  
  
    1.  在 **虛擬目錄**索引標籤上，設定**應用程式集區**來**SSOStubAppPool**您剛剛建立。  
  
    2.  按一下 **目錄安全**索引標籤上，按一下**編輯**中**驗證和存取控制**群組方塊中，選取**僅整合式 Windows 驗證已啟用**，然後清除其他**驗證存取**核取方塊。 按一下 **確定**結束。  
  
10. 在**Internet Information Services (IIS) 管理員**，展開**Web Sites**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP，按一下**屬性**，，然後修改設定，如下所示：  
  
    1.  在 **虛擬目錄**索引標籤上，設定**應用程式集區**來**SSOStubAppPool**您剛剛建立。  
  
    2.  按一下 **目錄安全**索引標籤上，按一下**編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下 **確定**結束。  
  
11. 在**Internet Information Services (IIS) 管理員**，展開**Web Sites**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下**屬性**，，然後修改設定，如下所示：  
  
    1.  在 **虛擬目錄**索引標籤上，設定**應用程式集區**來**SSOStubAppPool**您剛剛建立。  
  
    2.  按一下 **目錄安全**索引標籤上，按一下**編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下 **確定**結束。  
  
12. 在**Internet Information Services (IIS) 管理員**，展開**Web Sites**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker，按一下**屬性**，，然後修改設定，如下所示：  
  
    1.  在 **虛擬目錄**索引標籤上，設定**應用程式集區**來**SSOStubAppPool**您剛剛建立。  
  
    2.  按一下 **目錄安全**索引標籤上，按一下**編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下 **確定**結束。  
  
##  <a name="step7"></a> 建置服務導向解決方案  
  
#### <a name="to-build-the-service-oriented-solution"></a>建置服務導向解決方案  
  
1. 開始**Visual Studio 命令提示字元**。  
  
   > [!NOTE]
   >  在檔案 **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs**和 **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\customerserviceport.asmx.cs**，17f20caea2afcc8c 的所有執行個體取代為 a1054514fc67bded。  
  
2. 在 Visual Studio 命令提示字元中，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln 資料夾，然後執行下列命令，以建置服務導向方案的虛設常式版本。  
  
   -   `SetupBTSSoln.bat`  
  
   > [!NOTE]
   >  在下列檔案中，將所有 17f20caea2afcc8c 執行個體取代為目前的公開金鑰 Token。  
   > 
   > - %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs  
  
##  <a name="step9"></a> 在 SSO 資料庫中建立的企業單一登入 (SSO) 項目和值  
  
#### <a name="to-create-the-enterprise-single-sign-on-sso-entries-and-values-in-the-sso-database"></a>在 SSO 資料庫中建立企業單一登入 (SSO) 項目與值  
  
1.  開啟命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts，然後執行下列目錄以設定「企業單一登入」資料夾的 PATH 環境。  
  
    -   `Set PATH=%PATH%;%ProgramFiles%\"Common Files\Enterprise Single Sign-On"`  
  
2.  在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，使用「記事本」開啟 ConfigStoreApp.xml，然後檢視檔案的內容。  
  
    > [!NOTE]
    >  此檔案會定義 SSO 中實例用以儲存組態參數的組態存放區應用程式。 部分組態參數包括**逾時**用來與 SAP 通訊 （適用於所有的三個版本） 的值。 不需要變更此檔案。  
  
3.  在命令提示字元，執行下列命令以建立 SSO 組態存放區應用程式。  
  
    -   `ssomanage -createapps ConfigStoreApp.xml`  
  
4.  在命令提示字元，使用「記事本」開啟 SetConfigValuesInSSO.cmd，然後檢視檔案的內容  
  
    > [!NOTE]
    >  此命令檔設定 SSO 資料庫中的組態參數值。 它包含數組設定命令檔開頭處本機變數值的陳述式。 **SAPAdapterTimeout**， **PendingTransactionsAdapterTimeout**，並**PaymentTrackingAdapterTimeout**值用於虛設常式和配接器版本。 其餘的值則用於內嵌版本中。 對於虛設常式版本，此檔案不需要變更。  
  
5.  在命令提示字元中，輸入`SetConfigValuesInSSO.cmd`，然後按 ENTER，以將值儲存在 SSO 組態存放區應用程式。  
  
6.  在命令提示字元，執行下列命令以便在 SSO 中啟用票證：  
  
    -   `ssomanage -tickets yes yes`  
  
##  <a name="step11"></a> 部署服務導向解決方案的 BAM 定義  
  
#### <a name="to-deploy-the-bam-definition-for-the-service-oriented-solution"></a>部署服務導向解決方案的 BAM 定義  
  
1.  在命令提示字元，輸入下列命令，然後按 ENTER。 如此可設定尋找 BAM 公用程式的路徑：  
  
    -   設定 PATH=%PATH%;%programfiles%\Microsoft BizTalk Server\Tracking  
  
2.  在命令提示字元中，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM 資料夾，輸入下列命令，然後按 ENTER：  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
        > [!NOTE]
        >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
##  <a name="step13"></a> 部署服務導向解決方案  
  
#### <a name="to-deploy-the-service-oriented-solution"></a>部署服務導向解決方案  
  
1.  開啟命令提示字元，並將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。  
  
2.  修改**DeployStubBinding.cmd**以 「 發行 」 取代 「 偵錯 」 和 「 開發 」 的所有執行個體的檔案。  
  
3.  開啟命令提示字元，並將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。 輸入下列命令，然後按 ENTER：  
  
    -   `DeployStubBinding.cmd`  
  
4.  在命令提示字元，執行下列命令以啟動虛設常式版本的協調流程  
  
    -   `Startstub.vbs`  
  
## <a name="next-steps"></a>後續步驟  
 您可以測試服務導向解決方案的虛設常式版本中的運作方式[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安裝服務導向解決方案之前](../core/before-installing-the-service-oriented-solution.md)   
 [如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [服務導向解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-service-oriented-solution.md)