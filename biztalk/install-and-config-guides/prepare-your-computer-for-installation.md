---
title: 準備您的電腦安裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bba64728220eb2fc5be99153892d68e93eb8e22c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017204"
---
# <a name="prepare-your-computer-for-installation"></a>準備安裝電腦
本主題列出藉由安裝和設定所有必要軟體，然後建立帳戶並設定權限，以便備妥電腦的步驟。  

> [!TIP] 
> 我們的整合 MVP 已準備了一份安裝必要條件與 BizTalk Server 的詳細逐步指南：[BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)。  
> 
> 不過，Microsoft 不建議您採取停用使用者帳戶控制 (UAC) 或 Windows 防火牆這類步驟。 
  
> [!IMPORTANT]
>  請依照所列的順序完成這些工作。  
  
##  <a name="BKMK_InstUpdates"></a> 安裝 Windows Update  
  
- **Windows 7**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入 **Windows Update**。  
  
- **Windows 8.1、 Windows Server 2012 和 Windows Server 2012 R2**： 按一下 [Windows] 按鈕上的鍵盤和型別**Windows Update**。 按一下搜尋結果中的 **Windows Update**。  
  
  安裝更新之後，您可能需要重新啟動電腦。  
  
##  <a name="BKMK_IIS"></a> 啟用 Internet Information Services  
 Microsoft Internet Information Services (IIS) 提供許多 BizTalk Server 功能，包括 Web 應用程式基礎結構：  
  
-   HTTP 配接器  
  
-   SOAP adapter (SOAP 配接器)  
  
-   Windows SharePoint Services 配接器  
  
-   安全通訊端層 (SSL) 加密  
  
-   BAM 入口網站  
  
#### <a name="install-iis"></a>安裝 IIS

特定安裝步驟，請參閱： 

[安裝 IIS （Windows 8 和 Windows Server 2012）](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012)

[安裝 IIS （Windows 7 和 Windows Vista）](https://docs.microsoft.com/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)


當您安裝 IIS，除了預設已核取選項時，也請檢查下列：  
  
- **Web 管理工具**：另請核取：  
  
    - IIS 6 管理相容性：  
  
        - IIS 6 管理主控台  
  
        - IIS Metabase 及 IIS 6 設定相容性  
  
    - IIS 管理主控台  
  
- **World Wide Web 服務**：展開 [安全性] 再一併選取：  
  
    - 基本驗證  
  
    - Windows 驗證  

同時應考慮下列情況：  
  
- **.Net framework 3.5 功能**:.NET Framework 4.5 和.NET Framework 3.5 可用來開發包含 BizTalk 配接器組件的.Net 應用程式。 通常 **.NET Framework 4.5 功能**已安裝。 如果您將此電腦上建立應用程式，然後使用.NET Framework 3.5 **.Net Framework 3.5 功能**也可以安裝。  
  
- **訊息佇列**：如果您是使用 MSMQ 配接器，可以核取 [訊息佇列] 以建立本機 MSMQ 存放區。  
  
- **SMTP 伺服器**：如果您是使用 SMTP 配接器，可以核取 [SMTP 伺服器] 以建立本機 SMTP 伺服器。  
  
- **Windows Identity Foundation 3.5**： 使用 CSOM 安裝選項時 SharePoint 配接器需要 Windows Identity Foundation (WIF)。 [附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)描述 SharePoint 配接器的 CSOM 安裝選項。    
  
 
##  <a name="BKMK_XLS"></a> 安裝 Microsoft Office Excel  
  
1. 執行 Microsoft Office 安裝程式。  
  
2. 到達 [安裝類型] 畫面時，請選取 [自訂安裝]，然後選取 [下一步]。  
  
3. 在 [自訂安裝] 畫面上，選取 [Excel]，然後選取 [下一步]。  
  
4. 選取 [安裝]。  
  
5. 在 [安裝完成] 中，請選取 [完成]。  
  
   **其他**  
  
-   BizTalk Server 只支援 32 位元版本的 Microsoft Office。  
  
-   Microsoft Office Excel 需要的商務活動監控 (BAM) 在 BizTalk Server 中。 BAM Office Excel 活頁簿可定義您想監控的商務程序。 您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。  
  
-   若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用功能] 下的 [Visual Basic for Applications]。 否則，您可能會接收到「此活頁簿的 VBA 專案、ActiveX 控制項以及其他的程式設計相關功能已遺失」的錯誤。  
  
##  <a name="BKMK_VS"></a> 安裝 Visual Studio  
  
1. 以系統管理員身分執行 Visual Studio 安裝程式。  
  
2. 接受授權合約，然後按一下 [下一步]。  
  
3. 在 [要安裝的選擇性功能] 中，選取您需要的選項，然後選取 [安裝]。 BizTalk Server 不需要任何選用的功能。  
  
4. 在 [完成] 頁面上，關閉視窗，或按一下 [啟動] 以開啟 Visual Studio。  
  
   **其他**  
  
-   如果您安裝 Visual Studio 安裝 BizTalk Server 之前，再升級至 Visual Studio Team Explorer，您可能需要修復從 BizTalk Server 安裝**控制台中** / **程式**選項。  
  
-   Visual Studio 會自動安裝 BizTalk Server 不使用的 Microsoft SQL Server Express。 因此最佳做法是解除安裝 Microsoft SQL Server Express。  
  
-   BizTalk Server 開發工具是以 Visual Studio 為基礎。 至少，您必須安裝 Visual Studio 的 Microsoft Visual C#®.NET 元件安裝 BizTalk Server 之前，先**開發人員工具和 SDK**。  
  
-   Visual studio*不*需要若要安裝 BizTalk Server 的實際執行電腦 （只有執行階段），在任何應用程式開發或偵錯是必要項。  
  
-   BizTalk Server 執行階段需要.NET Framework 4.5。 如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，就需要使用 .NET Framework 3.0。  
  
##  <a name="BKMK_SQL"></a> 安裝 SQL Server  
 安裝 [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)  
  
 安裝 [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)  
  
 安裝 [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)  
  
 當您安裝 SQL Server 時，請選取下列功能：  
  
- Database Engine 服務  
  
  -   SQL Server 複寫  
  
  -   全文檢索搜尋  
  
- Analysis Services  
  
- Reporting Services  
  
- 共用功能  
  
  -   SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) 或 Business Intelligence Development Studio (SQL Server 2008 R2)  
  
       [下載 SQL Server 2014 Data Tools](http://www.microsoft.com/download/details.aspx?id=42313)  
  
  -   用戶端工具連接性  
  
  -   Integration Services  
  
  -   管理工具 - 基本  
  
      -   管理工具 - 完整  
  
  **其他**  
  
- 除了二進位定序之外，BizTalk Server 還支援所有區分大小寫和不區分大小寫的 SQL Server 定序。 不支援二進位定序。  
  
- 為了達到最佳效能，Microsoft 建議使用 SQL Server Enterprise Edition。 請參閱 [SQL Server 2008 R2 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx)、[SQL Server 2012 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx)或 [SQL Server 2014 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx)。  
  
- 系統支援 Service Pack 和 Windows Update，因此皆應安裝。  
  
- 當 BizTalk Server 和 SQL Server 位於不同的電腦上時，分散式交易協調器 (MS DTC) 會處理電腦間交易。 SQL Server AlwaysOn 功能不支援 MSDTC 交易。 不支援將 SQL Server AlwaysOn 功能。  
  
##  <a name="BKMK_MQSeries"></a> 安裝 MQSeries 必要條件  
 **MQSeries 配接器**：在安裝 BizTalk Server 時即會自動安裝。  
  
 **MQSeries 用戶端 (MQSC) 配接器**：  
  
1. 執行 Host Integration Server (HIS) 安裝  
  
2. 在元件安裝中，展開 [BizTalk 配接器]。  
  
3. 選取 [BizTalk Adapter for WebSphere MQ (Client-Based) (適用於 WebSphere MQ (以用戶端為基礎) 的 BizTalk 配接器)]。  
  
   **支援的 IBM WebSphere MQ 版本**：  
  
-   IBM WebSphere MQ 6.0.2.12 及更新版  
  
-   IBM WebSphere MQ 7.0.1.9 及更新版  
  
-   IBM WebSphere MQ 7.1.0.5 及更新版  
  
-   IBM WebSphere MQ 7.5.0.3 及更新版  
  
-   IBM WebSphere MQ 8 (僅限執行階段；而非系統管理 API)  
  
     [Host Integration Server CU3](https://support.microsoft.com/kb/3019572) 中包含針對 MQ 第 8 版的支援。  
  
> [!NOTE]
>  如果未列出特定的 WebSphere MQ 版本，例如 MQ 5.x，則不支援使用此 BizTalk Server 版本。  
  
 **其他**  
  
- 最佳做法是一律安裝最新的 WebSphere MQ Fix Pack。 請參閱[ http://www.ibm.com/support/docview.wss?uid=swg27006037 ](http://www.ibm.com/support/docview.wss?uid=swg27006037)。  
  
- 如果 IBM WebSphere MQ 是安裝在非 Windows 電腦上，請將 **MQSAgent COM+ 應用程式** (MQSConfigWiz.exe) 和 **MQSeries Server for Windows** 安裝在同一部電腦上。 如果 IBM WebSphere MQ 是安裝在 Windows 電腦上，則不需使用 **MQSAgent COM+ 應用程式**和 **MQSeries Server for Windows** 程式。  
  
   **MQSConfigWiz.exe**包含在 BizTalk Server 安裝檔案。  
  
   **MQSeries Server for Windows** 不是 Microsoft 程式，而必須透過 IBM WebSphere MQ 程式取得。  
  
- [MQSeries 配接器](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx)提供 MQSeries 配接器的詳細資訊，包括不同元件的設定。 [BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) (BizTalk Server：MQSeries 和 MQSeries 用戶端 (MQSC) 配接器) 提供 MQSeries 和 MQSC 配接器的其他詳細資料。  
  
- IBM WebSphere 並非 Microsoft 產品，因此 Microsoft 不提供支援服務。 Microsoft 亦不保證此程式的適用性。 如需 IBM WebSphere MQ 的詳細資訊，包括下載指示，請參閱 www.ibm.com 。  
  
##  <a name="BKMK_BAMAlerts"></a> BAM 警示  
 SQL Server 2012 和較新版本的 BAM 警示使用 SQL Server 中的 Database Mail。 使用 SQL Server 2008 R2 和較舊版本的 BAM 警示使用 SQL Notification Services。 然後才能安裝或設定 BAM 警示，您必須在 SQL Server 中設定 Notification Services 或 Database Mail。  
  
###  <a name="BKMK_DBMail"></a> 使用 SQL Server 2012/2014 的 BAM 警示  
 設定 [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx)。  
  
 設定 [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx)。  
  
 **其他**  
  
-   Database Mail 會使用 SMTP 伺服器來傳送 BAM 警示。 在 BizTalk Server 上或在另一部 IIS 伺服器上，可以在本機安裝 SMTP 伺服器。 [附錄 D：建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)中有提列安裝及設定 SMTP 伺服器的步驟。  
  
###  <a name="BKMK_SSNS"></a> 使用 SQL Server 2008 R2 的 BAM 警示 – 安裝 SQL Server 2005 Notification Services  
  
1. 請前往 [Microsoft SQL Server 2005 SP4 功能套件](http://go.microsoft.com/fwlink/p/?LinkId=286285)。  
  
2. 針對下列元件，下載並安裝適當的平台套件：  
  
    **Microsoft SQL Server Native Client**  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi>"X86 封裝 (sqlncli.msi)  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi>"X64 封裝 (sqlncli_x64.msi)  
  
     **Microsoft SQL Server 2005 管理物件集合**  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi>"X86 封裝 (SQLServer2005_XMO.msi)  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi>"X64 封裝 (SQLServer2005_XMO_x64.msi)  
  
     **Microsoft SQL Server 2005 Notification Services 用戶端元件**  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi>"X86 封裝 (SQLServer2005_NS.msi)  
  
   - 超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi>"X64 封裝 (SQLServer2005_NS_x64.msi)  
  
   **其他**  
  
-   不需要設定 SQL Notification Services僅安裝在 BizTalk Server。  
  
##  <a name="BKMK_WIF"></a> Windows Identity Foundation  
  
|                                                              |                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows 8.1、 Windows Server 2012 和 Windows Server 2012 R2 |                                Windows Identity Foundation 隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。                                |
|                      Windows Vista SP1                       | 可下載[Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK"<http://www.microsoft.com/download/details.aspx?id=17331>」。 |
  
 **其他**  
  
-   SharePoint 配接器，或選取 SharePoint Online 使用與 SharePoint 用戶端端物件模型 (CSOM) 時需要 Windows Identity Foundation (WIF)。 具體來說：  
  
    |安裝選項|WIF 為必要項目|  
    |-------------------------|------------------|  
    |使用 CSOM SharePoint 配接器|是|  
    |SharePoint Online (含 CSOM)|是|  
    |SharePoint 配接器 Web 服務 （已過時）|否|  
    |沒有 SharePoint|否|  
  
-   [附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供 SharePoint 安裝選項的相關特定資訊。  
  
##  <a name="BKMK_WSS"></a> 安裝及設定 Microsoft SharePoint  
 安裝 [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)  
  
 安裝 [SharePoint Online 服務](http://technet.microsoft.com/library/jj819267.aspx)  
  
 安裝 [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)  
  
 安裝 [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)  
  
 **其他**  
  
-   如果您要安裝 SharePoint，您必須這樣再繼續進行其餘的 BizTalk Server 必要條件。  
  
-   安裝和設定 SharePoint 包含下列程序：  
  
    -   安裝 SharePoint  
  
    -   設定 SharePoint  
  
    -   將預設的網站擴充成虛擬伺服器  
  
-   [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 BizTalk Server 適用的 SharePoint 配接器安裝選項。  
  
-   使用 SharePoint 配接器時，建議您安裝新的 CSOM 選項，而不是 SharePoint Web 服務 (如[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)所述)。  
  
##  <a name="BKMK_SharedMem"></a> 停用共用記憶體通訊協定  
  
1. 開啟 [SQL Server 組態管理員]。  
  
2. 在 [SQL Server 組態管理員] 中，依序展開 [SQL Server 網路組態] 和 [Protocols for MSSQLSERVER (MSSQLSERVER 的通訊協定)]。  
  
3. 以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。  
  
4. 選取 [SQL Server 服務]，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [停止]。 服務停止之後，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [啟動]。  
  
5. 關閉 [SQL Server 組態管理員]。  
  
   **其他**  
  
-   某些壓力狀況下 （例如從在同一部電腦存取 SQL Server 用戶端），SQL Server 共用記憶體通訊協定可能會降低 BizTalk 伺服器的效能。 您可以停用 [SQL Server 網路組態] 中的 [共用記憶體網路通訊協定] 來解決這個問題。  
  
-   ReplaceThisText  
  
##  <a name="BKMK_LocalAdmin"></a> 加入本機系統管理員群組  
 **Windows Server 2012** : [Windows Server 2012： 如何將帳戶新增至本機系統管理員群組](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)  
  
 **Windows 8.1**：若要開啟 Windows 8 的 [本機使用者和群組]，請按一下鍵盤上的 Windows 鍵，並輸入**群組**。 在 [搜尋] 視窗中，按一下 [設定]。 在 [結果] 視窗中，按一下 [編輯本機使用者和群組]。 按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。  
  
 **Windows 7 SP1**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入**電腦管理**，並按一下以開啟該項目。 展開 [本機使用者和群組]，按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。  
  
 **其他**  
  
-   您必須是本機 Administrators 群組的成員，才能安裝和設定 BizTalk Server。  
  
##  <a name="BKMK_AppLog"></a> 設定應用程式事件記錄檔  
  
1. 開啟 [事件檢視器]：  
  
    **Windows Server 2012** ： 按一下 [Windows] 按鈕上的鍵盤和型別**事件檢視器**。 在 [結果] 視窗中，按一下 [事件檢視器]。  
  
    **Windows 8.1**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。 在 [搜尋] 視窗中，按一下 [設定]。 在 [結果] 視窗中，按一下 [檢視事件記錄檔]。  
  
    **Windows 7 SP1**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入**事件檢視器**，並按一下以開啟該項目。  
  
2. 展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後按一下 [屬性]。 在 [記錄內容] 中：  
  
   -   若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。  
  
   -   若要提供更多空間，請輸入 [最大記錄檔大小] 中較高的數字。  
  
   -   若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。  
  
   -   若要清除記錄檔事件，請選取 [清除記錄檔]。  
  
3. 按一下 [確定]，關閉 [事件檢視器]。  
  
   **其他**  
  
-   BizTalk Server 安裝程式會將事件記錄保留在應用程式事件記錄檔中。 隨安裝的 BizTalk Server 功能而定，記錄檔需要的空間量可能會超過其限制。 如果應用程式事件記錄檔會在 BizTalk Server 安裝期間用盡空間，則安裝將會失敗。 變更應用程式事件記錄檔設定可防止此失敗。  
  
## <a name="next"></a>下一個  
 [選擇 BizTalk Server 功能和元件](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)   
 [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [附錄 C：可轉散發的封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [附錄 D︰建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
