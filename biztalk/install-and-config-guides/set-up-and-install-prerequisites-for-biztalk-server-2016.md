---
title: "設定並安裝 BizTalk Server 2016 的必要條件 |Microsoft 文件"
description: "安裝及設定必要的軟體和設定 BizTalk Server 2016 的逐步指示"
author: MandiOhlinger
manager: anneta
ms.prod: biztalk-server
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b621-903a-4cfa-9cb0-c6a82ed8f733
caps.latest.revision: "11"
ms.author: mandia
ms.openlocfilehash: 2f03aaf7d33cc494320d1ef0944b48286bc1b24c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="set-up-and-install-prerequisites-for-biztalk-server-2016"></a>設定及安裝 BizTalk Server 2016 的必要元件
設定伺服器，以及安裝與設定軟體必要條件。

## <a name="join-the-administrators-group"></a>加入系統管理員群組
若要安裝與設定 BizTalk Server，請登入本機電腦上使用系統管理員帳戶的伺服器。 將任何管理 BizTalk Server 的使用者帳戶加入本機系統管理員群組︰

1.  在 [開始] 功能表中，開啟 [電腦管理]。

    * 或開啟 [系統管理工具]，然後選取 [電腦管理]。
    * 或開啟 [伺服器管理員]，然後依序選取 [工具] 及 [電腦管理]。
  
2.  展開 [本機使用者和群組]，然後選取 [群組]。
3.  以滑鼠右鍵按一下**系統管理員**群組，並選取 [加入群組]。 [新增] 您的帳戶，然後選取 [確定] 儲存變更。 

## <a name="change-the-computer-name-optional"></a>變更電腦名稱 （選用）
如果您的電腦名稱長度超過 15 個字元，BizTalk Server 組態失敗。 若要變更電腦名稱不超過 15 個字元：

1.  在 [伺服器管理員] > [儀表板] 中，選取 [本機伺服器]。 
2.  在 [內容] 中選取電腦名稱屬性予以變更。
3. 重新啟動電腦。 

**另請參閱**：Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)

## <a name="enable-network-dtc-access"></a>啟用網路 DTC 存取
如果 BizTalk 和 SQL Server 安裝在不同的電腦上，請啟用 BizTalk Server 和 SQL Server 上的網路 DTC 存取。 

1. 在 [開始] 功能表中，開啟 "dcomcnfg"。

    * 或開啟 [系統管理工具]，然後選取 [Component Services]。
    * 或開啟 [伺服器管理員]，然後依序選取 [工具] 及 [Component Services]。
  
2. 依序展開 [Component Services]、[電腦]、[我的電腦] 和 [分散式交易協調器]。
3. 以滑鼠右鍵按一下 [本機 DTC]，然後選取 [內容]。
4. 在 [安全性] 索引標籤上，檢查以下項目：  
    * 網路 DTC 存取
    * 允許輸入
    * 允許輸出
    * 不需要驗證
5. 選取 [確定]。 如果提示您重新啟動 MS DTC，請選取**是**。 

如需可能需要的其他設定，請參閱 [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。

## <a name="configure-application-event-log-optional"></a>設定應用程式事件記錄檔 （選擇性）

BizTalk Server 安裝程式會將事件記錄保留在應用程式事件記錄檔中。 隨安裝的 BizTalk Server 功能而定，記錄檔需要的空間量可能會超過其限制。 如果應用程式事件記錄檔在安裝期間用盡空間，安裝就會失敗。 變更應用程式事件記錄檔設定可防止此失敗。

1. 在 [開始] 功能表中，開啟 [事件檢視器]：

    * 或開啟 [系統管理工具]，然後選取 [事件檢視器]。
    * 或開啟 [伺服器管理員]，然後依序選取 [工具] 和 [事件檢視器]。
  
2. 展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後選取 [內容]。 
3. 若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。 

    * 若要增加空間，請在 [最大記錄檔大小] 中輸入較大的數字。
    * 若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。
    * 若要清除記錄檔事件，請選取 [清除記錄檔]。

4. 選取 [確定]。

## <a name="edge-cant-be-opened-optional"></a>邊緣無法開啟 （選擇性）

當使用 Edge 時，會顯示下列訊息︰  
`Microsoft Edge can't be opened using the Built-in Administrator account. Sign in with a different account and try again.`

允許使用內建的系統管理員帳戶開啟 Edge：

1. 在 [開始] 功能表中開啟 [本機安全性原則]。 或開啟 [伺服器管理員]，然後依序選取 [工具] 和 [本機安全性原則]。
2.  展開 [本機原則]，然後選取 [安全性選項]。 
3.  在 [使用者帳戶控制: 內建的 Administrator 帳戶的管理員核准模式] 原則中 [啟用] 原則。 
4. 選取 [確定] 重新啟動電腦。

## <a name="install-windows-updates"></a>安裝 Windows 更新

請務必安裝最新的 Windows 重大更新。 

1. 在 [開始] 功能表中，開啟 [Windows Update] 並檢查更新。 您也可以開啟 [設定]，然後選取 [更新與安全性]。
2. 安裝更新之後，您可能需要重新啟動電腦。

## <a name="enable-iis"></a>啟用 IIS
BizTalk Server 的下列功能需要 IIS：

- HTTP 配接器
- SOAP adapter (SOAP 配接器)
- Windows SharePoint Services 配接器
- 安全通訊端層 (SSL) 加密
- BAM 入口網站
- EDI

IIS 是隨附於作業系統的**角色**或**功能**，視作業系統而定。 安裝：

1. 在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。 或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。
2. 選取 [Internet Information Services] 或 [網頁伺服器 (IIS)]。 除了預設已核取的選項之外，另請選取下列項目： 

    **Windows 10**
    - 在 **Web 管理工具**中亦請核取：  
        - IIS 6 管理相容性
        - IIS 6 管理主控台
        - IIS 6 指令碼工具 (安裝 adsutil.vbs)
        - IIS Metabase 及 IIS 6 設定相容性
        - IIS 管理主控台
    - 在 **World Wide Web 服務**中展開 [安全性] 再一併核取：
        - 基本驗證
        - Windows 驗證    

    **Windows Server**
    - 在 [安全性] 中亦請核取︰ 
        - 基本驗證
        - Windows 驗證    
    - 在 [管理工具] 中亦請核取：  
        - IIS 管理主控台
        - IIS 6 管理相容性
        - IIS 6 Metabase 相容性
        - IIS 6 管理主控台
        - IIS 6 指令碼工具 (安裝 adsutil.vbs)

3. 繼續安裝作業，並在出現提示時重新啟動電腦。 

**另請參閱**︰在 [Windows 8 或 Windows Server 2012 (英文)](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012) 上安裝 IIS。


## <a name="run-64-bit-bam-portal-optional"></a>執行 64 位元 BAM 入口網站 （選用）
如果您不使用 BAM 入口網站，然後您可以略過本節。 

BAM 入口網站在 32 位元模式中執行。 如果您在 64 位元環境中使用網際網路資訊服務 (IIS)，然後設定在 32 位元模式中執行的應用程式集區。 

#### <a name="using-adsutilvbs"></a>使用 adsutil.vbs
1.  以系統管理員身分開啟命令提示字元。 
2.  在命令提示字元中，輸入：  
    `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`
3. 選取 [輸入]。

#### <a name="using-iis-manager"></a>使用 IIS Manager
1. 在 [開始] 功能表中，開啟 "inetmgr"。
2.  展開電腦名稱，然後選取 [應用程式集區]。
3.  以滑鼠右鍵按一下 [DefaultAppPool]，然後選取 [進階設定]。 
4.  將 [啟用 32 位元應用程式] 的值變更為 **True**。 
5.  選取 [確定]。

## <a name="install-windows-identity-foundation-wif-optional"></a>安裝 Windows Identity Foundation (WIF) (選擇性)
如果您使用 SharePoint Services 配接器，BizTalk Server 需要 WIF。 如果不使用 SharePoint Services 配接器，您可以略過本節。

Windows Identity Foundation 是隨附於作業系統的**功能**。

1. 在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。 或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。
2. 選取 **Windows Identity Foundation 3.5** 並繼續安裝作業。 
3. 出現提示時，請重新啟動電腦。

## <a name="install--configure-smtp-server-optional"></a>安裝及設定 SMTP 伺服器 （選擇性）
如果您使用 BAM 警示時，BizTalk Server 需要 SMTP 伺服器。 如果不使用 BAM 警示，您可以略過本節。

SQL Server Database Mail 使用 SMTP 伺服器傳送 BAM 警示。 SMTP 伺服器可以安裝在本機 BizTalk Server 上，或安裝在安裝了 IIS 的另一部伺服器上。 Windows 8.1 或 Windows 10 等用戶端作業系統無法使用 SMTP 伺服器。 

SMTP 伺服器是隨附於伺服器作業系統的**功能**。

1. 在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。 或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。
2. 選取 [SMTP 伺服器] 並繼續安裝作業。 
3. 出現提示時，請重新啟動電腦。

## <a name="install-excel-2016-or-2013-optional"></a>安裝 Excel 2016 或 2013 （選擇性）
如果您使用商務活動監控 (BAM)，BizTalk Server 需要 Excel。 如果不使用 BAM，您可以略過本節。

BAM Office Excel 活頁簿可定義您想監控的商務程序。 您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。

> [!IMPORTANT] 
> * BizTalk Server 只支援 32 位元版本的 Microsoft Office。 
> * 若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用的功能] 下的 [Visual Basic for Applications]。 否則，您可能會收到錯誤︰`This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`

#### <a name="install-excel-2016"></a>安裝 Excel 2016

Office 2016 是使用「隨選即用」或 "C2R Installer" 安裝。 C2R 安裝會下載並安裝 Office 中的所有程式。 至於 BAM，我們只需要 Excel。 為解決這個問題，請下載並安裝 [Office 2016 部署工具](https://www.microsoft.com/download/details.aspx?id=49117) 自訂 C2R Installer。

1. 下載並安裝 [Office 2016 部署工具](https://www.microsoft.com/download/details.aspx?id=49117)。
2. 在 Office 2016 部署工具檔案解壓縮的資料夾中，使用記事本等文字編輯器開啟 **configuration.xml** 檔案。
3. 以下列內容取代 `<Configuration>` 區段：  

    ```
    <Configuration>
    <Add SourcePath="D:\" OfficeClientEdition="32">
    <Product ID="O365ProPlusRetail" >
      <Language ID="en-us" />
      <ExcludeApp ID="Access" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="InfoPath" />
      <ExcludeApp ID="Lync" />
      <ExcludeApp ID="OneDrive" />
      <ExcludeApp ID="OneNote" />
      <ExcludeApp ID="Outlook" />
      <ExcludeApp ID="PowerPoint" />
      <ExcludeApp ID="Project" />
      <ExcludeApp ID="Publisher" />
      <ExcludeApp ID="SharePointDesigner" />
      <ExcludeApp ID="Visio" />
      <ExcludeApp ID="Word" />
    </Product>
    </Add>
    </Configuration>
    ```
    
    以 Office 2016 ISO 檔案的位置取代 "SourcePath"。
4. 在 Office 2016 部署工具檔案所在資料夾中，按住 **SHIFT** 鍵，再以滑鼠右鍵按一下資料夾的空白區域。 選取 [在此處開啟命令視窗]。 
5. 輸入下列命令啟動 Excel 安裝︰  
  `setup.exe /configure configuration.xml`

    > [!TIP]
    > `setup.exe /download configuration.xml`下載所需的 Office 安裝程式檔案。
 
6. 選取 Excel 並繼續安裝作業。 
 
**另請參閱**：[Office 部署工具的設定選項](https://technet.microsoft.com/library/jj219426.aspx)和[安裝 Office 2016 或 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)

#### <a name="install-excel-2013"></a>安裝 Excel 2013
1. 執行 Microsoft Office 安裝程式。
2. 選取 [自訂安裝]，然後選取 Excel。
3. 繼續安裝作業。   

## <a name="install-visual-c-redistributable-package"></a>安裝 Visual c + + 可轉散發套件

下載並安裝[Visual c + + 可轉散發套件](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)。 即使使用 Visual Studio 2015，2013 還是必要版本。

[Visual c + + 下載](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)列出所有可用的版本。

## <a name="install-visual-studio-2015-optional"></a>安裝 Visual Studio 2015 (選擇性)
BizTalk Server 需要 Visual Studio 才能使用開發工具建立 BizTalk 專案。 如果這是暫存或實際執行伺服器，或您不進行任何 BizTalk 開發，請略過本節。

建議使用 Visual Studio Enterprise 版，但也支援 Professional 及 Community 版。 

1. 以系統管理員身分執行 Visual Studio 安裝程式。
2. 選取**預設**安裝。 BizTalk Server 不需要任何選用的功能。

    > [!NOTE]
    > 如果您還有將 Visual Studio 用於 BizTalk 專案之外的工作，請選取 [自訂]安裝以安裝其他功能。 一些常用功能包括 Microsoft Web 開發人員工具、Microsoft Office 開發人員工具、PowerShell Tools for Visual Studio 和 ClickOnce 發行工具。
 
3. 繼續安裝作業，並在出現提示時重新啟動電腦。

**另請參閱**：[安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)

> [!IMPORTANT]
> - 如果您是先安裝 Visual Studio 之後才安裝 BizTalk Server，則升級至 Visual Studio Team Explorer 時，可能需要修復 BizTalk Server 安裝。
> - Visual Studio 會自動安裝 BizTalk Server 不使用的 Microsoft SQL Server Express。 解除安裝 Microsoft SQL Server Express。 您也可以解除安裝 Microsoft SQL Server Compact。  
> - BizTalk Server 開發工具是以 Visual Studio 為基礎。 您至少要先安裝 Microsoft Visual C#® .NET 元件，再安裝 BizTalk Server 開發者工具與 SDK。
> - BizTalk Server 執行階段需要 .NET Framework 4.6。 如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，.NET Framework 3.0 則需要

#### <a name="uninstall-sql-server-express"></a>解除安裝 SQL Server Express
1. 在 [開始] 功能表中，開啟 [程式和功能]。 或者，開啟 [控制台]，選取 [解除安裝程式]。
2. 解除安裝： 
    - Microsoft SQL Server 2014 Express LocalDb
    - Microsoft SQL Server Compact 4.0 SP1 x64 ENU
    - Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)
    
3. 繼續解除安裝，並在出現提示時重新啟動電腦。 

## <a name="install-sql-server-2016"></a>安裝 SQL Server 2016
BizTalk Server 需要 SQL Server。 SQL Server 和 BizTalk 可以安裝在同一部電腦或不同的電腦上。 大部分的生產環境都會將 BizTalk 和 SQL 安裝在不同的伺服器上。 

> [!IMPORTANT]
> - 不建議或支援 SQL Server Express 版。 Express 版不包含 BizTalk Server 需要的特定功能。
> - BizTalk Server 支援 SQL 標準版。 不過，若要使用商務活動監控即時彙總 (BAM RTA)，請安裝 SQL Server Enterprise 版。 SQL Server Standard Edition 不支援 BAM 即時彙總 (RTA)。
> - 若要充分運用 BizTalk Server SDK 或從 Visual Studio 部署 BizTalk Server 應用程式，請安裝 SQL Server 開發工具。
> - 除了二進位定序之外，BizTalk Server 支援所有區分大小寫及不區分大小寫的 SQL Server 定序。 不支援二進位定序。

**如需特定安裝步驟，請參閱**[安裝 SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup)或[安裝 SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx)。

1. 啟動 SQL Server 安裝。 
2. 在安裝功能時，選取下列選項：
    - Database Engine Services
        - SQL Server 複寫
        - R 服務 （資料庫） (**選擇性**; 在資訊[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))
        - 搜尋的全文檢索和語意擷取
    - Analysis Services
    - Reporting Services - 原生
    - 共用功能
        - 用戶端工具連接性
        - Integration Services

    > [!NOTE]
    > SQL Server 預設安裝不包含 **SQL Server Data Tools**。 它不是必要的，但可在 [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) 下載。 下載適用於所有支援的 SQL Server 版本的 [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，包括 Azure SQL Database。 

3. 繼續安裝作業，並在出現提示時重新啟動電腦。

## <a name="disable-shared-memory"></a>停用共用的記憶體

1. 開啟 **SQL Server 組態管理員**。
2. 在 「 SQL Server 組態管理員 」 中，展開**SQL Server 網路組態**，然後選取**MSSQLSERVER 的通訊協定**。
3. 以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。
4. 選取**SQL Server 服務**，以滑鼠右鍵按一下 SQL **Server (MSSQLSERVER)**，然後選取**停止**。 服務已停止之後，以滑鼠右鍵按一下**SQL Server (MSSQLSERVER)**，然後選取**啟動**。
5. 關閉 [SQL Server 組態管理員]。

一般而言，共用記憶體通訊協定只會影響與 SQL Server 在相同電腦安裝的用戶端 (BizTalk Server)。 某些壓力狀況下 （例如從同一部電腦存取 SQL Server 用戶端），SQL Server Shared Memory 通訊協定可能會降低執行 BizTalk Server 效能。 停用 Shared Memory 網路通訊協定會解決問題。

> [!TIP]
> SQL Server 代理程式無法停用 Shared Memory 之後, 啟動，然後確認[ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)安裝。

## <a name="install-sql-xml-4"></a>安裝 SQL XML 4
BizTalk Server 執行階段、系統管理工具和 BAM 的必要項目。 

下載並安裝[SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403)。

## <a name="configure-sql-database-mail-optional"></a>設定 SQL Database Mail （選擇性）
如果您使用 BAM 警示時，BizTalk Server 需要 SQL Server Database Mail。 如果不使用 BAM 警示，您可以略過本節。 

**另請參閱**︰更多 [Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail) 資訊。

> [!IMPORTANT]
> - 您需要知道 SMTP 伺服器的伺服器名稱和 TCP 通訊埠編號。 如果 IIS 和 SMTP 伺服器都安裝在這部電腦上，您使用的是本機 SMTP 伺服器。 如果 SMTP 伺服器需要驗證，請準備好使用者名稱和密碼。
> - BAM 入口網站和 BAM 警示是不同的功能。 如果使用 BAM 警示，則需要 SQL Server Database Mail。 如果不使用 BAM 警示，則不需要 SQL Server Database Mail。

**針對特定的設定步驟，請參閱**： 設定[SQL Server 2016 Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail)或[SQL Server 2014 Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx)。

   
傳送測試電子郵件︰ 
1.  以滑鼠右鍵按一下 **Database Mail**，然後選取 [傳送測試電子郵件]。 
2.  輸入**收件者**電子郵件地址，然後選取 [傳送測試電子郵件]。  
 
如果「收件者」收信人收到電子郵件，即表示已設定 Database Mail。 

## <a name="install-winscp-optional"></a>安裝 WinSCP （選擇性）
所需的 FTP 配接器。 如果您不使用 FTP 配接器，然後略過本節。 

下載並安裝[WinSCP](http://winscp.net)。 

## <a name="next-step"></a>下一步
安裝 [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md)。
