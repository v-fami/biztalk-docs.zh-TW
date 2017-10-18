---
title: "安裝內嵌和配接器版本的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: "97"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbf374b4efb219f1221275819713787565a325b0
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution"></a>如何安裝服務導向解決方案的內嵌與配接器版本
下列步驟描述如何準備安裝服務導向解決方案內嵌與配接器版本的電腦，以及如何在此電腦上安裝解決方案。  
  
> [!NOTE]
>  - 服務導向的解決方案位於資料夾\< *BizTalk Server 安裝資料夾*> \SDK\Scenarios\SO。  
>  - 若您的解決方案沒有大型主機，可以修改連接埠繫結以使用虛設常式 Web 服務來進行擱置交易。 Web 服務會在本機產生交易，以模擬大型主機交易。  
  
##  <a name="step1"></a>準備安裝服務導向解決方案配接器與內嵌版本的電腦  
  
1.  如果您安裝 Windows SharePoint Services 時，排除 （根） 在預設的網站的 Windows SharePoint Services 受管理的路徑，如下所示： 按一下**啟動**，指向 **所有程式**，指向  **系統管理工具**，然後按一下 **SharePoint 管理中心內**。  
  
    1.  在下**虛擬伺服器設定**，選取**設定虛擬伺服器設定**。  
  
    2.  在**虛擬伺服器清單**頁面上，按一下**Default Web Site**。  
  
    3.  在**虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。  
  
    4.  在**包含路徑**區段**定義受管理的路徑**頁面上，選取**根**，然後按一下**移除選取的路徑**。  
  
    5.  在命令提示字元，執行 IISReset。  
  
2.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下 **電腦管理**主控台，然後再加入本機系統管理員群組的 BizTalk 服務帳戶。  
  
3.  登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。  
  
4.  在命令提示字元，輸入下列命令，然後按 ENTER 以設定 %BTSSolutionsPath% 環境變數。 然後結束命令提示字元。  
  
    -   setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  
  
        > [!NOTE]
        >  若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。  
  
        > [!NOTE]
        >  如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831)。  
  
##  <a name="step3"></a>移除服務導向解決方案的虛設常式版本  
  
1.  開啟**BizTalk Server 管理主控台**，如下所示： 按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **BizTalk Server 管理**。  
  
2.  在**BizTalk Server 管理主控台**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**的應用程式**，以滑鼠右鍵按一下**BTSScn.SO.CustomerService**，然後按一下**停止**。 在**停止應用程式**對話方塊中，選取**完全停止-終止執行個體**，然後按一下**停止**。  
  
    > [!NOTE]
    >  您不需要為了安裝內嵌和配接器版本而移除虛設常式版本。 若您要將所有版本放在一起，應該略過此步驟。  
  
3.  開啟命令提示字元，輸入下列命令，然後按 ENTER。 此命令會將預設指令碼主控件變更為 CScript.exe：  
  
    -   `cscript /H:CScript`  
  
4.  在命令提示字元，將目前的目錄變更為 %BTSSolutonsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER：  
  
    -   `UnEnlistStub.vbs`  
  
5.  在命令提示字元，輸入下列命令，然後按 ENTER：  
  
    -   `UndeployStub.vbs`  
  
6.  在命令提示字元執行下列命令  
  
     設定路徑 = %PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤 」  
  
     如此可設定尋找 BAM 公用程式的路徑。  
  
    > [!NOTE]
    >  如果您使用 64 位元電腦，輸入`%ProgramFiles(x86)%`而不是`%ProgramFiles%`。  
  
7.  在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM，然後執行下列命令：  
  
    -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  
  
8.  在命令提示字元中，將目錄變更\<*企業單一登入 」 安裝目錄*>，然後執行下列命令：  
  
    -   `ssomanage -tickets no no`  
  
9. 在命令提示字元，執行下列命令以刪除 WoodgroveBank.CustomerService SSO 附屬應用程式：  
  
    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  
  
10. 在命令提示字元，執行下列命令以刪除虛設常式版本所使用的網站。 如需有關 iisvdir.vbs 的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830)。  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  
  
11. 啟動 網際網路資訊服務 (IIS) 管理員，如下所示： 按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下 **Internet Information Services (IIS) 管理員**。  
  
    -   展開**應用程式集區**，以滑鼠右鍵按一下您先前的 Web 應用程式的建立應用程式集區，按一下**刪除**，然後按一下**確定**確認中對話方塊。  
  
12. 按一下**啟動**，指向 **控制台**，按一下 **新增或移除程式**，然後再解除安裝 IBM WebSphere MQ Client for Windows。  
  
13. 啟動**Visual Studio 命令提示字元**，然後執行下列命令以刪除您為虛設常式版本安裝的 amqmdnet.dll。  
  
    -   `gacutil /u amqmdnet`  
  
##  <a name="step5"></a>準備後端系統，服務導向解決方案存取  
  
1.  安裝 IBM WebSphere MQ for Windows Server，在本機電腦上。  
  
    1.  請保留所有預設設定。 設定**預設組態**結尾**準備 WebSphere MQ 精靈**。 佇列管理員則命名為 Qm_<\<*您的電腦名稱*>。  
  
    2.  安裝 Fix Pack 10 (CSD10)。 請保留所有預設設定。  
  
2.  安裝 MQSeries 代理程式。  
  
    1.  請重新執行[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝程式。  
  
    2.  在**程式維護**頁面上，選取**修改**，然後按一下**下一步**。  
  
    3.  在**元件安裝**頁面上，展開**其他軟體**節點，然後再選取**MQSeries 代理程式**。  
  
    4.  在**完成**頁面上，請確定**啟動 BizTalk MQSeries 代理程式組態精靈**未選取。  
  
    > [!NOTE]
    >  **MQSeries 代理程式**是 IBM WebSphere MQ 之後才會啟動的核取方塊為已安裝 Windows。  
  
3.  開啟**Visual Studio 命令提示字元**，將目錄變更\< *IBM MQSeries 安裝目錄*> \bin 資料夾，然後執行下列命令：  
  
    -   `gacutil /i amqmdnet.dll`  
  
4.  若您要安裝 Microsoft Host Integration Server 2004 以存取大型主機，請安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 在安裝程式，在**選項**頁面上，選取**Visual C#.NET**，然後清除其他元件核取方塊。 您不需要安裝其他元件比**Visual C#.NET**。  
  
    > [!NOTE]
    >  Host Integration Server 2004 中的 TI 設計師需要 [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)]。  
  
5.  安裝和設定 Microsoft Host Integration Server 2004，如果您有存取大型主機。 請保留所有預設設定。  
  
#### <a name="create-the-mqseries-queues"></a>建立 MQSeries 佇列  
  
1.  開啟 WebSphere MQ Explorer，依序展開**佇列管理員**，然後展開您要建立佇列的佇列管理員。 一般而言，佇列管理員則命名為 Qm_<\<*您的電腦名稱*>。  
  
2.  在 WebSphere MQ explorer 中，以滑鼠右鍵按一下**佇列**，指向 **新增**，按一下 **本機佇列**，然後建立下列本機佇列的配接器版本解決方案：  
  
    -   AdapterSOAInputQueue  
  
    -   AdapterSOAOutputQueue  
  
    > [!NOTE]
    >  佇列可共用 MQSeries 叢集，不過，這並非必要的。  
  
    > [!NOTE]
    >  MQSeries 佇列管理員名稱和佇列名稱有區分大小寫。  
  
3.  重複上一個步驟為內嵌版本建立下列本機佇列：  
  
    -   InlineSOAOutputQueue  
  
    -   InlineSOAInputQueue  
  
4.  重複上一個步驟為付款追蹤器模擬器建立下列本機佇列。 (付款追蹤器模擬器同時用於配接器和內嵌版本)：  
  
    -   LastPaymentsInputQueue  
  
    -   LastPaymentsOutputQueue  
  
#### <a name="complete-configuration-of-the-mqseries-adapter"></a>完成 MQSeries 配接器的組態設定  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **BizTalk MQSeries 代理程式組態精靈**。  
  
2.  在**歡迎**頁面上，按一下**下一步**。  
  
3.  在**應用程式識別**頁面上，選取**本使用者**，然後輸入使用者名稱和密碼。 MQSeries 代理程式的 COM+ 應用程式會在此使用者帳戶之下執行。 對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。 如果不是，使用者帳戶以裝載 MQSeries 配接器的 BizTalk 服務必須可加入至**CreatorOwner** COM + 應用程式角色。  
  
4.  按一下**是**上**MQSConfigWiz**對話方塊中，如果系統提示您在上一個步驟中輸入的使用者帳戶具有系統管理權限。  
  
5.  在**角色名稱**頁面上，按一下**下一步**。  
  
6.  在**建立 MQSAgent COM + 應用程式**頁面上，按一下**下一步**，然後按一下**完成**上**完成**頁面。  
  
#### <a name="configure-the-mainframe-cics-application"></a>設定大型主機 CICS 應用程式  
  
1.  使用「記事本」開啟 %BTSSolutionsPath%\SO\MFAccess\HISTIComponent 資料夾中的 bizcbl.txt 及其 "Copy Book" (MainFrameProgramVTCS2Description.txt)，然後檢視內容。  
  
    -   Bizcbl.txt 包括從輸入的帳戶號碼傳回隨機帳戶陳述式的 COBOL 程序。  
  
    -   MainFrameProgramVTCS2Descriptoin.txt 包含說明輸入和輸出資料資訊的 COMMAREA。 COMMAREA 是連續記憶體區塊，用來在被呼叫與呼叫的程式之間來回傳遞資料。  
  
    > [!NOTE]
    >  您也可以使用 copy book 產生交易整合器 (TI) 中繼資料檔案搭配 TI 設計師外掛程式使用 Visual Studio。  
  
    > [!NOTE]
    >  雖然下列步驟是成功部署的重要步驟，不過，通常不是由 BizTalk Server 開發人員執行。 您必須依賴大型主機人員以適當地設定主機環境。 此逐步說明所需的軟體通常安裝在大多數的大型主機環境中。 如需最小大型主機作業系統環境的詳細資訊，請參閱 Host Integration Server 文件。  
  
2.  以 FTP 之類的方法將 COBOL 程式碼複製到主控件。  
  
3.  編譯 COBOL 程式碼和 Copy Book。 下列程式碼顯示 COBOL 編譯器的工作控制語言 (Job Control Language，JCL) 範例。  
  
    ```  
    //COB      EXEC PGM=IGYCRCTL,  
    //            PARM=&COBPARM,  
    //            REGION=&REG  
    //STEPLIB  DD DSN=&COMPINDX..SIGYCOMP,DISP=SHR  
    //SYSLIB   DD DSN=&INDEX..SDFHCOB,DISP=SHR  
    //         DD DSN=&INDEX..SDFHMAC,DISP=SHR  
    //         DD DSN=&HLQ..&COMP..COBCOPY,DISP=SHR  
    //SYSPRINT DD SYSOUT=&OUTC  
    //*SYSPRINT DD DSN=&&INPUT,DISP=(,PASS),UNIT=SYSDA,  
    //*         SPACE=(TRK,(100,50)),  
    //*         DCB=(DSORG=PS,LRECL=121,BLKSIZE=2420,RECFM=FBA)  
    //SYSIN    DD DSN=&&SYSCIN,DISP=(OLD,DELETE)  
    //SYSLIN   DD DSN=&&LOADSET,  
    //            DISP=(MOD,PASS),  
    //            UNIT=&WORK,  
    //            SPACE=(80,(250,100))  
    //SYSUT1   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT2   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT3   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT4   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT5   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT6   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT7   DD UNIT=&WORK,SPACE=(460,(350,150))  
    ```  
  
4.  連結編輯已編譯的來源以建立可執行檔。 下列程式碼顯示 COBOL 連結編輯的 JCL 範例。  
  
    ```  
    //LKED     EXEC PGM=IEWL,REGION=&REG,  
    //            PARM=&LNKPARM,COND=(5,LT,COB)  
    //SYSLIB   DD DSN=&INDEX..SDFHLOAD,DISP=SHR  
    //         DD DSN=CEE.SCEELKED,DISP=SHR  
    //         DD DSN=&TCPINDX..SEZATCP,DISP=SHR  
    //SYSLMOD  DD DSN=&LMINDX..&COMP..LOADLIB,DISP=SHR  
    //SYSUT1   DD UNIT=&WORK,  
    //            DCB=BLKSIZE=1024,  
    //            SPACE=(1024,(200,20))  
    //SYSPRINT DD SYSOUT=&OUTC  
    //SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)  
    //         DD DSN=&&COPYLINK,DISP=(OLD,DELETE)  
    ```  
  
5.  設定 CICS 大型主機應用程式。  
  
    -   在此步驟中，大型主機系統程式設計師或 CICS 開發人員必須安裝 TCPIPSERVICE、工作階段、連線、交易和程式等資源定義。  
  
    -   請諮詢大型主機系統管理員以取得 IP 位址、連接埠編號和您可存取的程式連結名稱。  
  
        > [!NOTE]
        >  此逐步解說假設大型主機使用 CICS 應用程式伺服器，而交易的程式設計模型為 TCP/IP (增強的接聽程式模式 (Enhanced Listener Mode，ELM) 連結)。  
  
##  <a name="step7"></a>設定 Web 伺服器針對安全通訊端層 (SSL)  
  
#### <a name="install-certificate-services"></a>安裝憑證服務  
  
1.  按一下**啟動**，指向 **控制台**，然後按一下**新增或移除程式**。  
  
2.  在**新增或移除程式**對話方塊中，按一下 **新增/移除 Windows 元件**。  
  
3.  在**Windows 元件精靈**，選取**憑證服務**，按一下**下一步**，然後依照螢幕上指示完成安裝。  
  
#### <a name="create-a-certificate-request"></a>建立憑證要求  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，按一下 **屬性**按一下 **目錄安全性**索引標籤，然後再按一下**伺服器憑證**。  
  
2.  在**歡迎**頁面**Web 伺服器憑證精靈**，按一下 **下一步**。  
  
3.  在**服務憑證**頁面上，選取**建立新的憑證**，然後按一下**下一步**。  
  
4.  在**延遲或立即要求**頁面上，按一下**準備要求，但於稍後傳送**，然後按一下**下一步**。  
  
5.  在**名稱和安全性設定**頁面上，保留所有預設設定，然後按**下一步**。  
  
6.  在**組織資訊**頁面上，輸入您的公司組織和組織單位名稱，然後按一下**下一步**。  
  
7.  在**您站台的一般名稱**頁面上，輸入您的電腦名稱中**一般名稱**方塊，然後再按一下**下一步**。  
  
8.  在**地理資訊**頁面上，填寫您的地理資訊，然後按一下**下一步**。  
  
9. 在**憑證要求檔案名稱**頁面上，輸入`c:\certreq.txt`中**檔案名稱**方塊，然後再按一下**下一步**。  
  
10. 在**要求檔案摘要**頁面上，按一下**下一步**，然後按一下**完成**上**完成**頁面。  
  
#### <a name="submit-the-certificate-request-to-the-certification-authority"></a>將憑證要求提交給憑證授權單位  
  
1.  在 Internet Explorer，在位址方塊中，輸入`http://localhost/certsrvt`，然後按 ENTER 鍵。  
  
2.  在**歡迎**頁面上，按一下**要求憑證**，然後按一下**進階的憑證要求**上**要求憑證**頁面。  
  
3.  在**進階憑證要求**頁面上，按一下**提交憑證要求，使用 base64 編碼 PKCS #10 檔案或更新要求使用 base64 編碼 PKCS #7 檔案**。  
  
4.  從您在 < 若要建立憑證要求 」，將它貼到程序中建立的 c:\certreq.txt 複製的所有文字**已儲存的要求**方塊**提交憑證要求或更新要求**頁面，然後再按一下**送出**。  
  
#### <a name="issue-a-certificate-using-certification-authority-management-tool"></a>使用憑證授權單位管理工具來發行憑證  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下**憑證授權單位**。  
  
2.  在**憑證授權單位**主控台中，展開憑證授權單位的名稱，展開**暫止要求**，以滑鼠右鍵按一下您在上一個步驟中，點提交憑證要求若要**所有工作**，然後按一下**問題**。  
  
3.  關閉**憑證授權單位**主控台。  
  
#### <a name="download-the-certificate-to-the-web-server"></a>下載至 Web 伺服器憑證  
  
1.  在 Internet Explorer，在位址方塊中，輸入`http://localhost/certsrvt`，然後按 ENTER 鍵。  
  
2.  在**歡迎**頁面上，按一下**檢視擱置的憑證要求狀態**。  
  
3.  在**檢視擱置的憑證要求狀態**頁面上，按一下憑證**要求**您在 「 建立憑證要求 」 程序中建立。  
  
4.  在**憑證核發**頁面上，選取其中一個編碼配置，然後按**下載憑證**。  
  
5.  在**安全性警告**對話方塊中，按一下 **儲存**，然後將憑證儲存為 c:\certnew.cer。  
  
#### <a name="install-the-certificate-to-the-web-server"></a>將憑證安裝至 Web 伺服器  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，展開**網站**，以滑鼠右鍵按一下**Default Web Site**為您建立憑證要求，然後按一下**屬性**。  
  
2.  在**屬性**對話方塊中，按一下 **目錄安全性**索引標籤，然後再按一下**伺服器憑證**。  
  
3.  在**歡迎**頁面**Web 伺服器憑證精靈**，按一下 **下一步**。  
  
4.  在**擱置的憑證要求**頁面上，選取**處理擱置要求及安裝憑證**，然後按一下**下一步**。  
  
5.  在**處理擱置要求**頁面上，輸入`c:\certnew.cer`中**路徑和檔案名稱**文字方塊，然後再按一下**下一步**。  
  
6.  按一下**下一步**上**SSL 連接埠**頁面上，按一下**下一步**上**憑證摘要**頁面，然後再按一下**完成**上**確認**頁面。  
  
    > [!NOTE]
    >  在此逐步解說中，您不需要將伺服器憑證安裝至本機電腦上「信任的根憑證授權單位」存放區，因為憑證服務和 Web 伺服器均安裝在同一部電腦上。  
  
##  <a name="step9"></a>建立後端系統的 Web 服務  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**.  
  
    > [!NOTE]
    >  服務導向解決方案透過此 Web 服務存取大型主機。  
  
2.  上**新增應用程式集區**對話方塊方塊中，輸入**應用程式集區識別碼**（任意值），然後按一下**確定**。  
  
3.  在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下您剛應用程式集區建立，並選取**屬性**。  
  
4.  上**屬性**頁面上，按一下**識別**索引標籤上，選取**可設定**，輸入**使用者名**和**密碼**，然後按一下**確定**。 對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。  
  
#### <a name="create-the-pendingtransactions-web-service-for-runtime"></a>建立擱置交易 Web 服務的執行階段  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\MFAccess\PendingTransactions  
  
     存取權限 = 讀取，執行指令碼  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions，然後再按一下**屬性**。  
  
    1.  在**目錄安全性**索引標籤上，按一下 **編輯**修改**驗證和存取控制**。 選取**基本驗證 （密碼會以純文字傳送）**，清除其他**驗證存取**核取方塊。 按一下**確定**關閉**驗證方法** 對話方塊。  
  
    2.  在**目錄安全性**索引標籤上，按一下 [**編輯**下**安全通訊**群組方塊，然後再檢查**需要安全通道 (SSL)**中**安全通訊**] 對話方塊。  
  
    3.  在**虛擬目錄**索引標籤上，設定**應用程式集區**建立擱置交易 Web 服務的新 IIS 應用程式集區 」 程序所建立的應用程式集區。  
  
#### <a name="create-the-pendingtransactions-web-service-for-development-environment"></a>建立擱置交易 Web 服務的開發環境  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：  
  
     Alias = PendingTransactions  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\MFAccess\PendingTransactions  
  
     存取權限 = 讀取，執行指令碼  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下 PendingTransactions，，然後按一下 **屬性**。  
  
    1.  在**目錄安全性**索引標籤上，按一下 **編輯**修改**驗證和存取控制**。 選取**啟用匿名存取**。 按一下**確定**結束。  
  
        > [!NOTE]
        >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將使用適用於供開發環境的擱置交易 Web 應用程式。 在生產環境中不需要此 Web 應用程式。  
  
    2.  在**虛擬目錄**索引標籤上，設定**應用程式集區**建立擱置交易 Web 服務的新 IIS 應用程式集區 」 程序所建立的應用程式集區。  
  
#### <a name="create-the-stub-sap-web-service"></a>建立虛設常式 SAP Web 服務  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  
  
     存取權限 = 讀取，執行指令碼  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP，按一下 **屬性**，，然後修改設定，如下所示：  
  
    1.  在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立新的 IIS 應用程式的程序中建立集區的擱置交易 Web 服務 」。  
  
    2.  在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下**確定**結束。  
  
##  <a name="step11"></a>建立服務導向解決方案的 TI 元件  
  
#### <a name="create-a-com-application-for-the-ti-component"></a>建立 TI 元件的 COM + 應用程式  
  
1.  在命令提示字元，執行 %systemroot%\system32\com\comexp.msc。  
  
2.  在**元件服務**主控台中，展開**元件服務**，依序展開**電腦**，展開**我的電腦**，以滑鼠右鍵按一下**COM + 應用程式**，指向 **新增**，然後按一下**應用程式**。  
  
    1.  在**歡迎**頁面上，按一下**下一步**，然後按一下**建立空白的應用程式**上**安裝或建立新的應用程式**頁面。  
  
    2.  型別`BTSScn SO TI Component`中**輸入新的應用程式的名稱**方塊中，選取**伺服器應用程式**為**啟動型別**，然後按一下**下一步**.  
  
    3.  在**帳戶**群組方塊**設定應用程式識別碼**頁面上，選取**這位使用者**，然後輸入使用者名稱和密碼**使用者**和**密碼**方塊。 新的 COM+ 應用程式會在此帳戶之下執行。 此使用者帳戶必須為本機「HIS 執行階段使用者」群組的成員。 對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。  
  
    4.  在**新增應用程式角色**頁面上，按一下**下一步**。  
  
    5.  上**將使用者加入角色**頁面上，展開**CreatorOwner**，按一下 **使用者**，然後按一下**新增**。  
  
    6.  在**選取使用者或群組**對話方塊方塊中，選取將用於存取大型主機的使用者帳戶。 對於此逐步解說，請新增 UserID 本機帳戶。  
  
        > [!NOTE]
        >  若要透過 TI 元件存取 CICS 交易，您可以使用 COM+ 應用程式或裝載 .NET Remoting 元件的 Web 應用程式。 此逐步解說使用 TI 元件的 COM+ 應用程式和 COM Interop 存取大型主機以改善效能。  
  
    7.  在**完成**頁面上，按一下**完成**。  
  
#### <a name="create-a-remote-environment-to-access-the-mainframe"></a>建立遠端環境，以存取大型主機  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft Host Integration Server 2004**，然後按一下 **TI 管理員**。  
  
2.  在**TI 管理員**主控台中，按一下**交易整合器 （組態）**，依序展開**Windows 啟始的處理**，以滑鼠右鍵按一下**遠端環境**，指向 **新增**，然後按一下**遠端環境**。  
  
    1.  在**歡迎**頁面上，按一下**下一步**。  
  
    2.  在**設定新的遠端環境**頁面上，輸入**遠端應用程式名稱**，然後按一下**下一步**。 對於此逐步解說，請使用 Mainframe_TCP 做為名稱。  
  
    3.  在**設定主機環境和程式設計模型**頁面上，選取**CICS**如**目標主機**和**茱萸連結**的**程式設計模型**，然後按一下**下一步**。  
  
    4.  在**設定結束點 TCP/IP**頁面上，輸入在大型主機的 IP 位址**IP/DNS 位址**方塊，然後再按一下**編輯**新增連接埠號碼。 您的 HIS COM 將會透過結束點位址存取交易。  
  
    5.  在**完成**頁面上，按一下**完成**。  
  
#### <a name="create-the-ti-component-for-the-service-oriented-solution"></a>建立服務導向解決方案的 TI 元件  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft Host Integration Server 2004**，然後按一下 **TI 管理員**。  
  
2.  在**TI 管理員**主控台中，按一下**交易整合器 （組態）**，按一下  **Windows 啟始的處理**，然後按一下 **物件**. 以滑鼠右鍵按一下**物件**，按一下 **新增**，然後按一下**物件**。  
  
    1.  在**歡迎**頁面上，按一下**下一步**。  
  
    2.  在**指定或尋找物件**頁面上，按一下**瀏覽**，在 %BTSSolutionsPath%\SO\MFAccess\HISTIComponent 資料夾中，選擇 SOHISTIUsingCOM.TLB，然後按一下**下一步**.  
  
    3.  上**COM 物件的定義環境特性**頁面上，選取**BTSScn SO TI Component**如**COM + 應用程式**，然後按一下**下一步**.  
  
    4.  在**定義遠端環境**頁面上，選取您在先前的程序中建立的遠端環境**遠端環境，然後按一下下一步。**  
  
    5.  在**建立 WIP 物件**頁面上，按一下**下一步**，然後按一下**完成**上**完成**頁面。  
  
#### <a name="test-the-connectivity-to-the-mainframe"></a>測試大型主機連線  
  
1.  在 Windows 檔案總管中，瀏覽至 %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester 資料夾，然後按兩下 Interop.SOHISTIUsingCOM.dll.reg 檔案。 如此可新增 HISTISimpleTester 應用程式的登錄值，以透過「執行階段可呼叫包裝函式」(RCW) 呼叫 TI 元件。  
  
2.  在 Windows 檔案總管中，瀏覽至 %BTSSolutionsPath%\SO\MFAccess\ 資料夾，然後執行 SetupMFAccess.bat。  
  
3.  在 Windows 檔案總管中，巡覽至 %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug 資料夾，然後執行 BTSScnSOHISTIComponentSimpleTester.exe。  
  
    -   在 HISTISimpleTester 應用程式中，按一下**呼叫大型主機程式-使用 COM**。 它會從在大型主機上執行的 COBOL 應用程式傳回五筆記錄。  
  
##  <a name="step13"></a>建立協調流程的虛擬目錄的 Web 服務  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**.  
  
    1.  上**新增應用程式集區**對話方塊方塊中，輸入**應用程式集區識別碼**（任意值），然後按一下**確定**。  
  
    2.  以滑鼠右鍵按一下您剛應用程式集區建立，，然後選取**屬性**。  
  
    3.  上**屬性**頁面上，按一下**識別**索引標籤上，選取**可設定**，輸入**使用者名**和**密碼**，然後按一下**確定**。 對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。  
  
    > [!NOTE]
    >  此使用者必須具有執行協調流程 Proxy Web 服務的權限，並且必須新增至 BizTalk Server 系統管理員、SSO 系統管理員或 SSO 分支機構系統管理員群組其中之一  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter  
  
     存取權限 = 讀取，執行指令碼  
  
3.  在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter，按一下 **屬性**，，然後修改設定，如下所示：  
  
    1.  在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在上一個步驟中建立。  
  
    2.  在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，選取**只整合式 Windows 驗證啟用**，然後清除其他**驗證存取**核取方塊。 按一下**確定**結束。  
  
4.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，proxy 的內嵌版本的 Web 服務建立下列虛擬目錄：  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline  
  
     存取權限 = 讀取，執行指令碼  
  
5.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline，按一下 **屬性**，，然後修改設定，如下所示：  
  
    1.  在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您剛剛建立。  
  
    2.  按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，選取**只整合式 Windows 驗證啟用**，然後清除其他**驗證存取**核取方塊。 按一下**確定**結束。  
  
##  <a name="step15"></a>建置服務導向解決方案  
  
-   在命令提示字元中，將目錄變更至 %btssolutionspath%\so\btssoln，型別`SetupBTSSoln.bat`，然後按 ENTER 鍵。 SetupBTSSoln.bat 會執行下列工作：  
  
    -   建立唯一的強式名稱金鑰 (SNK) 以簽署 SO 方案的組件。  
  
    -   從 SNK 擷取公開金鑰 Token 並以公開 Token 更新繫結檔案。  
  
    -   建置 SO 解決方案。  
  
    -   在 %BTSSolutionsPath%\Common 資料夾中建置 SSOApplicationConfig。  
  
##  <a name="step17"></a>建立 SSO 分支機構應用程式  
  
1.  開啟命令提示字元，然後將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。  
  
2.  在命令提示字元，使用「記事本」開啟 PendTransAffApp.xml，並加以檢視。 不需要變更此檔案。  
  
    > [!NOTE]
    >  PendTransAffApp.xml 檔案為擱置交易後端系統定義 SSO 分支機構應用程式 (WoodgroveBank.PendingTransactions)。 它也為 SSO 分支機構應用程式定義使用者和系統管理群組。 本逐步解說中，使用**BizTalk 應用程式使用者**和**BizTalk Server 系統管理員**。  
    >   
    >  如果您想要針對 SSO 分支機構應用程式使用不同的群組，您需要在 Active Directory 中，建立 Windows 群組 （以任何名稱），然後變更**appAdminAccount**和**appUserAccount**PendTransAffApp.xml 中的節點。 如果您這樣做，您應該設定的值**groupApp**屬性**旗標**節點為"yes"。  
    >   
    >  如需 SSO 分支機構應用程式的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。  
  
3.  在命令提示字元，使用「記事本」開啟 PendTransUserMap.xml 檔案，然後進行下列編輯：  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  PendTransUserMap.xml 檔案包含擱置交易後端系統的使用者對應。  
  
    > [!NOTE]
    >  如**externalUserId**  節點，用於擱置交易後端系統的外部使用者識別碼。 對於此逐步解說，請使用 UserID 做為外部識別碼。  
  
    > [!NOTE]
    >  如**windowsUserId**節點中，輸入使用者名稱**externalUserId**會對應至。 您可以使用網域群組和網域使用者帳戶。 此使用者必須為被允許使用擱置交易後端系統的群組成員。 對於此逐步解說，請使用 BizTalk 服務的使用者名稱。  
  
    > [!NOTE]
    >  如**windowsDomain**節點中，輸入網域名稱的**windowsUserId**。  
  
4.  在命令提示字元，使用「記事本」開啟 PmntTrckAffApp.xml 檔案，並檢視檔案的內容。 不需要變更此檔案。  
  
    > [!NOTE]
    >  PmntTrckAffApp.xml 檔案為付款追蹤器後端系統定義 SSO 分支機構應用程式 (WoodgroveBank.PaymentTracker)。  
  
5.  在命令提示字元，使用「記事本」開啟 PmntTrckUserMap.xml 檔案，然後進行下列編輯：  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  付款追蹤器 SSO 附屬應用程式將用於 MQSeries 配接器，並透過 MQSeries 標頭屬性傳送對應的外部使用者識別碼/密碼。 MQSeries Server 僅驗證 MQSeries 配接器在其下執行的 BizTalk 服務帳戶。 它不會驗證任何外部使用者認證。  
    >   
    >  如需有關 SSO 附屬 MQSeries 配接器的應用程式，請參閱 <<c0> [ 如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)。  
  
    > [!NOTE]
    >  PmntTrckUserMap.xml 檔案包含付款追蹤器後端系統的 SSO 使用者對應。 付款追蹤器模擬器程式可模擬使用者驗證的成功與錯誤狀況。  
    >   
    >  程式順利驗證所有以字母開頭的使用者識別碼**PT** (例如， **PTUserID**)，而無法驗證使用者識別碼不是以**PT**. 這樣可讓您依照想要測試的條件來選擇適合的使用者識別碼。 您也可以重複整個**對應**針對每個使用者識別碼的節點並在相同的檔案中定義多個對應。  
  
    > [!NOTE]
    >  如**externalUserId**節點中，輸入付款追蹤器後端系統的外部使用者識別碼。 對於此逐步解說，請使用 PTUserID 做為外部識別碼。  
  
    > [!NOTE]
    >  如**windowsUserId**節點中，輸入使用者名稱**externalUserId**會對應至。 此使用者必須為被允許使用付款追蹤器後端系統的群組成員。 對於此逐步解說，請使用 BizTalk 服務的使用者名稱。  
  
    > [!NOTE]
    >  如**windowsDomain**節點中，輸入網域名稱的**windowsUserId**。  
  
6.  在命令提示字元，使用「記事本」開啟 ConfigStoreApp.xml 檔案，然後檢視檔案的內容。  
  
     此檔案會定義 SSO 中實例用以保存組態參數的組態存放區應用程式。 部分組態參數包括在與 SAP (配接器與內嵌版本) 通訊時的 [逾時] 值，以及佇列管理員名稱和使用內嵌版本時使用的佇列。 不需要變更此檔案。  
  
7.  在命令提示字元，使用「記事本」開啟 SetConfigValuesInSSO.cmd 檔案，檢視並變更檔案的內容，如下表所示。  
  
    > [!NOTE]
    >  此命令檔設定 SSO 資料庫中的組態參數值。 它包含數個可為命令檔開頭的本機變數指派值的設定命令。  
    >   
    >  SAPAdapterTimeout、PendingTransactionsAdapterTimeout 和 PaymentTrackingAdapterTimeout 值用於配接器版本。 其餘的值則用於內嵌版本中。  
  
    > [!NOTE]
    >  您可以輸入""（兩個雙引號） 標記的預設值\<使用者指定 > 下表中。  
  
    |參數|預設值|Description|  
    |---------------|-------------------|-----------------|  
    |SAPAdapterTimeout|20000|對 SAP 後端要求的最大逾時 (毫秒)|  
    |SAPInlineTimeout|20000|對 SAP 後端要求的最大逾時 (毫秒)|  
    |SAPInlineHostName|\<指定使用者 >|SAP 後端識別項|  
    |SAPInlineClientNumber|\<指定使用者 >|SAP 用戶端編號|  
    |SAPInlineSystemNumber|\<指定使用者 >|SAP 系統編號|  
    |SAPInlineUserName|\<指定使用者 >|用以連接到 SAP 後端的使用者名稱|  
    |SAPInlinePassword|\<指定使用者 >|用以連接到 SAP 後端的密碼|  
    |PendingTransactionsAdapterTimeout|20000|對擱置交易伺服器要求的最大逾時 (毫秒)|  
    |PendingTransactionsInlineTimeout|20000|對擱置交易伺服器要求的最大逾時 (毫秒)|  
    |PendingTransactionsInlineURL|https://\<*您的電腦名稱*> /Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx|擱置交易服務的 URL。 \<*您的電腦名稱*> 必須符合**一般名稱**中建立憑證要求 」 程序。 您必須使用"localhost"的\<*您的電腦名稱*>。|  
    |PendingTransactionsInlineSSOAffiliateApp|WoodgroveBank.PendingTransactions|擱置交易 SSO 應用程式名稱|  
    |PaymentTrackingAdapterTimeout|20000|對付款追蹤系統要求的最大逾時 (毫秒)|  
    |PaymentTrackingInlineTimeout|20000|對付款追蹤系統要求的最大逾時 (毫秒)|  
    |PaymentTrackingInlineQManager|\<使用者指定 > (通常是 Qm_<\<*您的電腦名稱*>)。|MQSeries 佇列管理員名稱|  
    |PaymentTrackingInlineMQChannelDefinition|" " (必須輸入兩個雙引號)。|若為本機則為空字串，或為遠端 MQ 伺服器的格式化通道名稱。 如果您在設定 IBM WebSphere MQ 保留所有預設設定，則通道定義將 S__<\<*您的電腦名稱*> /TCP/\<*您的電腦名稱*> (1414)。|  
    |PaymentTrackingInlineRequestQueue|LastPaymentsInputQueue|付款追蹤要求的 MQ 佇列名稱|  
    |PaymentTrackingInlineResponseQueue|LastPaymentsOutputQueue|付款追蹤回應的 MQ 佇列名稱|  
    |PaymentTrackingInlineSSOAffiliateApp|WoodgroveBank.PaymentTracker|付款追蹤 SSO 應用程式名稱|  
    |StubSAPWebServiceURL|http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx|信用限制 SAP 系統的虛設常式 Web 服務 URL|  
  
8.  在命令提示字元，執行下列命令以設定 PATH 環境：  
  
    -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  
  
9. 在命令提示字元中，執行 CreateInitialConfigInSSO.cmd。 它會建立「SSO 分支機構應用程式」、SSO 組態存放區應用程式，以及分支機構應用程式的使用者對應。 然後會執行 SetConfigValuesInSSO.cmd，將組態值儲存在 SSO 組態存放區應用程式中。  
  
10. 在命令提示字元，執行下列命令以設定擱置交易分支機構應用程式的使用者認證。 使用\< **DomainName**> 和\< **UserID**> 針對 PendTransUserMap.xml 中定義\<WindowsDomain >\\<做為 <windowsdomain>\<windowsuserid>\>。 此命令會要求您輸入用於此逐步解說的外部使用者 (UserID) 的密碼。  
  
    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  
  
11. 在命令提示字元，執行下列命令以設定付款追蹤器分支機構應用程式的使用者認證。 使用\< **DomainName**> 和\< **UserID**> 針對 PmntTrckUserMap.xml 中定義\<WindowsDomain >\\< WindowsUserId\>. 此命令會要求您輸入用於此逐步解說的外部使用者 (PTUserID) 的密碼。  
  
    > [!NOTE]
    >  付款追蹤器模擬器不會驗證外部使用者認證。 您可以為 PTUserID 輸入任何密碼。  
  
    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  
  
##  <a name="step19"></a>部署服務導向解決方案的 BAM 定義檔案  
  
1.  開啟命令提示字元，輸入下列命令，然後按 ENTER 以設定尋找 BAM 公用程式的路徑：  
  
    -   設定路徑 = %PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤 」  
  
2.  在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM，輸入下列命令，然後按 ENTER：  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
##  <a name="step21"></a>部署服務導向解決方案  
  
#### <a name="update-the-binding-files-for-the-service-oriented-solution"></a>服務導向解決方案會更新繫結檔案  
  
1.  在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，使用「記事本」開啟 Deployallbinding.xml，然後進行下列編輯：  
  
    -   將 SET MGMT_DB_SERVER 和 MBMT_DB 中的伺服器名稱變更為 BizTalk Server 正在使用的伺服器和資料庫名稱。  
  
    -   將 SOLNDIR 變數值變更為 "%BTSSolutionsPath%\SO\BTSSoln"。  
  
2.  在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Bindings 資料夾。  
  
3.  對於配接器版本，使用「記事本」開啟 AdapterSOAOrchBindings.xml，然後編輯如下：  
  
    -   取代所有出現之 __MQ_SERVER_NAME\_ \_ MQSeries Server 名稱。  
  
    -   取代所有出現之 __MQ_QMANAGER_NAME\_ \_與 MQSeries 佇列管理員名稱。  
  
    -   取代所有出現之 __PT_WS_SERVER_NAME\_ \_字串中"\<位址 > https://\__PT_WS_SERVER_NAME\_\_"伺服器名稱與位置暫止的交易部署 web 服務。 伺服器名稱必須符合**一般名稱**在步驟中，「 將設定為使用 SSL 的 Web 伺服器 」。 不可使用 localhost。  
  
    > [!NOTE]
    >  繫結檔案 AdapterSOAOrchBindings.xml 會針對下列項目使用虛設常式 Web 服務：  
    >   
    >  1.  「信用限制」後端 SAP 系統。  
    > 2.  MQSeries 配接器與付款追蹤後端系統整合。  
    > 3.  擱置交易 Web 服務呼叫 HIS TI.NET 元件，將與大型主機後端系統整合。  
    >   
    >  若您未使用大型主機，則必須使用虛設常式 Web 服務以產生擱置交易系統的資料。  
  
4.  對於內嵌版本，使用「記事本」開啟 InlineSOAOrchBindings.xml，然後編輯如下：  
  
    -   取代所有出現之 __MQ_SERVER_NAME\_ \_ MQSeries Server 名稱。  
  
    -   取代所有出現之 __MQ_QMANAGER_NAME\_ \_與 MQSeries 佇列管理員名稱。  
  
#### <a name="deploy-the-service-oriented-solution"></a>部署服務導向解決方案  
  
-   在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER。  
  
    -   `Deployallbinding.cmd`  
  
    > [!NOTE]
    >  Deployallbinding.cmd 建立命名為 BTSScn.SO.CustomerService 的 BizTalk 應用程式，並匯入配接器和內嵌版本的繫結檔案。  
  
##  <a name="step23"></a>設定大型主機無法使用時的虛設常式擱置交易 Web 服務  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-adapter-version-without-a-mainframe"></a>設定虛設常式擱置交易 Web 服務 （適用於使用大型主機配接器版本）  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式擱置交易 Web 服務配接器版本：  
  
     別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
     存取權限 = 讀取，執行指令碼  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下 [**屬性**，然後修改設定，如下所示使用**屬性**] 對話方塊。  
  
    1.  在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立的虛擬目錄的 IIS 中的步驟中，建立解決方案 」。  
  
    2.  在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下**確定**結束。  
  
3.  在**BizTalk Server 管理主控台**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開 BTSScn.SO.CustomerService**傳送連接埠**，以滑鼠右鍵按一下**PendingTransactionSolicitResponsePort**，然後按一下**屬性**。  
  
    1.  在**一般**頁面上，按一下**設定**顯示**傳輸屬性**對話方塊方塊中，然後再修改**Web 服務 URL**至虛設常式擱置交易 Web 服務，例如：  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
    2.  關閉所有對話方塊。  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-inline-version-without-a-mainframe"></a>設定虛設常式擱置交易 Web 服務 （適用於使用大型主機無法內嵌版本）  
  
1.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下**虛擬目錄**執行**虛擬目錄建立精靈**。  
  
     使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式擱置交易 Web 服務配接器版本：  
  
     別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
     路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
     存取權限 = 讀取，執行指令碼  
  
2.  在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下 **屬性**，，然後修改設定，如下所示：  
  
    1.  在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立的虛擬目錄的 IIS 中的步驟中，建立解決方案 」。  
  
    2.  在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**. 按一下**確定**結束。  
  
3.  開啟命令提示字元，然後將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。  
  
4.  在命令提示字元中，開啟 SetConfigValuesInSSO.cmd 檔案，使用 [記事本]，然後設定的值**PendingTransactionsInlineURL**的虛設常式擱置交易 Web 服務的 url。  
  
    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
5.  在命令提示字元中輸入 `SetConfigValuesInSSO.cmd`，然後按下 ENTER。  
  
##  <a name="step25"></a>啟動服務導向解決方案  
  
1.  開啟命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER 以啟動內嵌和配接器版本的所有協調流程。  
  
    -   `startAll.vbs`  
  
2.  執行服務導向解決方案。 如需執行解決方案的詳細資訊，請參閱[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。  
  
## <a name="next-steps"></a>後續步驟  
 測試服務導向解決方案的內嵌和配接器版本[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md)   
 [How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [服務導向解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-service-oriented-solution.md)