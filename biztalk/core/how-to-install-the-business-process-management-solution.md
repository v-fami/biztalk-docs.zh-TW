---
title: 如何安裝商務程序管理解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, examples
- process management solution tutorial, installing
- process management solution tutorial, deployment prerequisites
ms.assetid: 930f3bb1-05e6-4b02-852d-6139aaf341f0
caps.latest.revision: 61
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffb067c206018996bc48641bcd8211921b0294dd
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752519"
---
# <a name="how-to-install-the-business-process-management-solution"></a>如何安裝商務程序管理解決方案
下列步驟說明如何準備安裝商務程序管理 (BPM) 解決方案的電腦，以及如何在此電腦上安裝解決方案。  
  
-   [準備安裝商務程序管理解決方案的電腦](#step1)  
  
     在準備步驟中，您會建立由接收埠和傳送埠使用的資料夾、佇列和 SQL 資料庫。 您也會為用戶端應用程式、CSRWebApp 和 OrderBroker Proxy Web 服務建立兩個虛擬目錄。  
  
-   [設定安裝商務程序管理解決方案的電腦](#step3)  
  
-   [安裝商務程序管理解決方案](#step5)  
  
> [!NOTE]
>  您將會執行幾個批次檔以部署解決方案。 建議您將批次檔的輸出重新導向至文字檔以確認指令碼是否成功完成。  
  
##  <a name="step1"></a> 準備安裝商務程序管理解決方案的電腦  
  
#### <a name="to-prepare-the-computer-for-installing-the-business-process-management-solution"></a>準備安裝商務程序管理解決方案的電腦  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**Services**。 使用**Services**主控台中，請確定下列服務正在執行：  
  
    -   **FTP 發行**  
  
    -   **訊息佇列**  
  
    -   **World Wide Web 發行**  
  
2.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，按一下 **電腦管理**主控台，然後再新增以本機 Administrators 群組的 BizTalk 服務帳戶。  
  
3.  如果您安裝 Windows SharePoint Services 時，排除 （根）。 **Default Web Site**從 Windows SharePoint Services 受管理的路徑，如下所示： 按一下 **開始**，指向 **所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。  
  
    1.  底下**虛擬伺服器組態**，選取**設定虛擬伺服器設定**。  
  
    2.  在 **虛擬伺服器清單**頁面上，按一下**Default Web Site**。  
  
    3.  在 **虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。  
  
    4.  在 **包含路徑**一節**定義受管理的路徑**頁面上，選取**根**，然後按一下 **移除選取的路徑**。  
  
    5.  在命令提示字元，執行 IISReset。  
  
##  <a name="step3"></a> 設定安裝商務程序管理解決方案的電腦  
  
#### <a name="to-configure-the-computer-for-installing-the-business-process-management-solution"></a>設定安裝商務程序管理解決方案的電腦  
  
1.  登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。  
  
2.  開啟命令提示字元，輸入下列命令，然後按 ENTER，設定 %BTSSolutionsPath% 環境變數以指出 E2E 解決方案的基底資料夾。 然後結束命令提示字元。  
  
    -   `setx BTSSolutionsPath "%ProgramFiles%\Microsoft BizTalk Server 2009\SDK\Scenarios"`  
  
        > [!NOTE]
        >  若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。  
  
        > [!NOTE]
        >  如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，在[ http://go.microsoft.com/fwlink/?LinkId=67831 ](http://go.microsoft.com/fwlink/?LinkId=67831)。  
  
3.  開啟命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\BPM\HistoryDB 資料夾，輸入`CreateDatabase.cmd`，然後按 ENTER，以建立歷程記錄資料庫。  
  
    > [!NOTE]
    >  執行指定為 SQL 傳送配接器處理常式的主控件之使用者，則必須具有相關權限可執行 SouthridgeVideoHistory 資料庫上的預存程序。  
  
4.  在命令提示字元，執行下列命令，將預設指令碼主控件變更為 CScript.exe  
  
    -   `CScript /H:CScript`  
  
5.  在命令提示字元，執行下列命令以建立 CSRWebApp Web 應用程式  
  
    -   `iisvdir /create "Default Web Site" CSRWebApp "%BTSSolutionsPath%\BPM\CSRWebApp"`  
  
        > [!NOTE]
        >  如需有關 iisvdir.vbs 的詳細資訊，請參閱 Microsoft TechNet 網站，在[ http://go.microsoft.com/fwlink/?LinkId=67830 ](http://go.microsoft.com/fwlink/?LinkId=67830)。  
  
6.  在命令提示字元，執行下列命令，為 OrderBroker_Proxy 建立新的 IIS 虛擬目錄。  
  
    -   `iisvdir /create "Default Web Site" BTSScn.BPM.OrderBroker_Proxy "%BTSSolutionsPath%\BPM\OrderBroker_Proxy"`  
  
    > [!NOTE]
    >  您可以使用 Internet Information Services (IIS) 管理員來建立 Web 應用程式。 如需如何在 IIS 7.0 中建立應用程式的詳細資訊，請參閱 < IIS 7.0 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=59263 ](http://go.microsoft.com/fwlink/?LinkId=59263)。  
  
7.  建立新的 IIS 應用程式集區，並將其識別設定為「BizTalk 外掛式主控件使用者」群組成員和「IIS_WPG」群組成員的使用者，方式如下：  
  
    1.  在 [Internet Information Services (IIS) 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**。  
  
    2.  型別**應用程式集區識別碼**（任何值），然後按一下**確定**。  
  
    3.  以滑鼠右鍵按一下 建立，並選取您的應用程式集區**進階設定**。  
  
    4.  依序展開**處理序模型**，如右邊資料行中按一下 **身分識別**設定，然後再按一下 **...**  
  
    5.  選取的使用者帳戶 (任一**內建帳戶**或是**自訂帳戶**) 具有權限來建立和執行在 Windows\Temp 目錄中的檔案。 當您設定 BizTalk 時，組態程序已經為它所新增至「BizTalk 外掛式主控件使用者」群組的使用者設定這些權限。 建議您指定相同的使用者。  
  
8.  在 Internet Information Services (IIS) 管理員 中，依序展開**Web Sites**，展開**Default Web Site**，以滑鼠右鍵按一下**BTSScn.BPM.OrderBroker_Proxy**，指向**管理的應用程式**，然後按一下**進階設定**。  
  
9. 設定**應用程式集區**您在上一個步驟中建立應用程式集區。  
  
10. 重複先前的兩個步驟，如**CSRWebApp**應用程式。  
  
11. 重設 IIS 以確定所有變更均立即生效。 若要這樣做，請執行**iisreset**在命令提示字元。  
  
12. 在命令提示字元，請將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`CreateQueues.vbs`，然後按 ENTER，以建立下列私用佇列。  
  
    |名稱|異動|交易通訊協定|  
    |----------|-------------------|--------------------------|  
    |ToFacilitiesQ|是|原生|  
    |FromFacilitiesQ|是|原生|  
    |FromFixedOrdersQ|是|原生|  
    |ToServicingSystemQ|是|原生|  
    |ToCSRSystemQ|否|HTTP|  
    |ToVendorSystemQ|否|HTTP|  
  
    > [!NOTE]
    >  您可以使用**電腦管理**嵌入式管理單元來建立佇列。 如需如何建立私用佇列的詳細資訊，請參閱 < 訊息佇列的文件，網址[ http://go.microsoft.com/fwlink/?LinkId=59264 ](http://go.microsoft.com/fwlink/?LinkId=59264)。 如需如何安裝 MSMQ 3.0 的詳細資訊，請參閱 < 訊息佇列的文件，網址[ http://go.microsoft.com/fwlink/?LinkId=59265 ](http://go.microsoft.com/fwlink/?LinkId=59265)。  
  
13. 在命令提示字元，請將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`CreateTestDirectories.cmd`，然後按 ENTER 鍵。  
  
    -   下列資料夾建立在 %SystemDrive%\BPMTest 資料夾中  
  
         CSRResponse-DSP  
  
         VendorResponse-DSP  
  
         OrderErrors-SP  
  
         ErrorResponse-RP-TestRL  
  
         Facilities-SP  
  
         Facilities-RP-TestRL  
  
         HistoryInsert-SP  
  
         HistoryUpdate-SP  
  
         Order-RP-TestRL  
  
         ServicingSystem-SP  
  
         Vendor-RP-TestRL  
  
         BizTalkErrors-SP  
  
    -   FromVendor 資料夾建立在 %SystemDrive%\Inetpub\ftproot 資料夾中。  
  
        > [!NOTE]
        >  若 Windows 系統不是安裝在 C 磁碟機，則應該以 C: 取代 %SystemDrive%。 必須比對資料夾名稱與 BPM 解決方案提供之繫結檔案中的位址。  
  
        > [!NOTE]
        >  BizTalk 服務帳戶必須具有 FromVendor 資料夾的讀取/寫入權限。  
  
##  <a name="step5"></a> 安裝商務程序管理解決方案  
  
#### <a name="to-install-the-business-process-management-solution"></a>安裝商務程序管理解決方案  
  
1. 在命令提示字元中，將目前資料夾變更為 %btssolutionspath%\bpm，型別`SetupBPM.bat`，然後按 ENTER 鍵。  
  
   > [!NOTE]
   >  在檔案中執行 SetupBPM.bat 之前， **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.wsdl**和 **%BTSInstallPath%/SDK/Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**，所有 8f8bbebbb3fb375a 執行個體都取代為 XXXXXXXXXXXXXXXX。  
  
    SetupBPM.bat 會執行下列工作：  
  
   1.  建立唯一的強式名稱金鑰 (SNK) 以簽章 BPM 解決方案的組件。  
  
   2.  從 SNK 擷取公開金鑰 Token。  
  
   3.  以公開 Token 更新繫結檔案。  
  
   4.  建置 BPM 解決方案並安裝 OpsAdapter。  
  
   5.  在 %BTSSolutionsPath%\Common 資料夾中建置 SSOApplicationConfig。  
  
2. 使用商務規則引擎部署精靈部署 Southridge Video 商務規則：  
  
   1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**商務規則引擎部署精靈**。  
  
      > [!NOTE]
      >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
   2. 在 [**歡迎**頁面上，按一下**下一步]**。  
  
   3. 在 [**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下**下一步]**。  
  
   4. 在 **原則存放區**頁面上，保留所有其他預設設定，然後按一下 **下一步**。  
  
   5. 在 **匯入規則引擎原則/詞彙檔案**頁面上，按一下**瀏覽**，在 %BTSSolutionsPath%\BPM\Rules 資料夾中，選取 DecodeAndValidateOrderRules.xml 檔案，然後按一下  **下一步**。  
  
   6. 在上**就緒**頁面上，按一下**下一步**，然後在**匯入原則/詞彙**頁面上，按一下**下一步**  
  
   7. 在 完成 頁面上，選取 **再次執行精靈**來開啟精靈，然後再按一下**完成**。  
  
   8. 在 [**歡迎**頁面上，按一下**下一步]**。  
  
   9. 在 [**部署工作**頁面上，選取 **[deploypolicy]**，然後按一下**下一步]**。  
  
   10. 在 **原則存放區**頁面上，保留所有其他預設設定，然後按一下 **下一步**。  
  
   11. 在 [**部署原則**頁面上，選取**DecodeAndValidateOrder 1.0**中**規則引擎原則**下拉式清單中，然後再按一下**下一步]**.  
  
   12. 在上**準備**頁面上，按一下**下一步**，然後在**部署的原則**頁面上，按一下**下一步**。  
  
   13. 在 完成 頁面上，按一下 **完成**。  
  
3. 若您將 BPM 方案安裝在 64 位元電腦上，請  
  
   1.  開啟 32 位元命令提示字元，如下： 按一下**開始**，按一下**執行**，型別`%SYSTEMROOT%\SYSWOW64\CMD.EXE`，然後按 ENTER 鍵。  
  
   2.  在 32 位元命令提示字元，將目錄變更為 %BTSSolutionsPath%\BPM\Scripts 資料夾。  
  
   3.  使用「記事本」開啟 CreateSouthridgeVideoApplication.cmd，然後以 "%SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe" 取代 "%CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe"。  
  
       > [!NOTE]
       >  在 32 位元命令提示字元，%CommonProgramFiles% 變數變更為 "%ProgramFiles(x86)%\Common Files"。 因為即使在 64 位元的電腦上，SSO 系統管理公用程式還是安裝在 %ProgramFiles% 中，因此您必須修正路徑。 DeployBPM.cmd 會呼叫 CreateSouthridgeVideoApplication.cmd。  
  
   4.  在 32 位元命令提示字元中，輸入`DeployBPM.cmd`，然後按 ENTER 鍵。  
  
       > [!NOTE]
       >  DeployBPM.cmd 必須在 32-bit 命令提示字元執行，因為它包含存取 x86 物件的 VB Script，必須要有 x86 版本的 cscript.exe。  
  
4. 在命令提示字元中，將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`DeployBPM.cmd`，然後按 ENTER 鍵。 DeployBPM.cmd 會執行下列工作：  
  
   1.  建立 BPM 解決方案的 BizTalk 應用程式。  
  
   2.  新增應用程式之間的參考。  
  
   3.  匯入繫結檔案。  
  
   4.  部署 BAM 定義檔案。  
  
   5.  註冊 SouthridgeVideo 事件來源。  
  
   6.  建立「單一登入」(SSO) 附屬應用程式，並將組態值儲存至 SSO 應用程式。  
  
5. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
   1.  在  **BizTalk Server 管理主控台**，展開**BizTalk 群組**，展開**應用程式**，展開  **BTSScn.BPM.OrderBrokerApp**，依序展開**接收位置**，以滑鼠右鍵按一下**廠商-RP-RL**，然後按一下 內容。  
  
   2.  在上**屬性** 對話方塊中，按一下**設定**，然後輸入值為下表**傳輸屬性** 對話方塊中：  
  
       |屬性名稱|值|  
       |-------------------|-----------|  
       |**Server**|`localhost`|  
       |**使用者名稱**|\<*BizTalk 服務帳戶名稱*\>|  
       |**密碼**|\<*BizTalk 服務帳戶密碼*\>|  
  
6. 執行 BPM 解決方案。 如需執行解決方案的詳細資訊，請參閱[如何執行商務程序管理解決方案](../core/how-to-run-the-business-process-management-solution.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您可以測試商務管理解決方案中的運作方式[如何執行商務程序管理解決方案](../core/how-to-run-the-business-process-management-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安裝商務程序管理解決方案之前](../core/before-installing-the-business-process-management-solution.md)   
 [商務程序管理解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-business-process-management-solution.md)
