---
title: "安裝 BizTalk Adapter Pack 2013 R2 和 2013年 |Microsoft 文件"
description: "必要條件和步驟以安裝 BAP 2013 R2 和 BizTalk Server 隨附的 BAP 2013"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9980953a-8d38-476f-af38-4f4214ba61f2
caps.latest.revision: "107"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8bc1ebbdaf2973f4749da6c0832d49204588b6c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-biztalk-adapter-pack-2013-r2-and-2013"></a>安裝 BizTalk Adapter Pack 2013 R2 和 2013
本文件列出的軟體需求，以及的步驟，安裝 Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (BAP) 隨附於 BizTalk Server 2013 或[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]。  
  
## <a name="change-log"></a>變更記錄  
  
|日期|變更|  
|---|---|  
|2016 年 3 月|在**之後安裝...**，加入步驟來設定 Oracle 資料庫配接器使用較新的 Oracle.DataAccess.dll 版本。|  
  
<a name="BKMK_Prereqs"></a>   
## <a name="software-prerequisites"></a>軟體必要條件  
 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]可以取用從：  
  
-   .NET 應用程式  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   ADO 介面  
  
-   Microsoft SharePoint 入口網站  
  
 根據您如何使用配接器，所需的軟體而異。  
  
### <a name="prerequisites-when-using-a-net-application"></a>使用.NET 應用程式時的必要條件  
當取用配接器使用.NET 應用程式，下列的軟體需要在開發電腦 （您要在其中建立.NET 應用程式的電腦）。 列出的順序安裝軟體。
  
|BizTalk Adapter Pack 2013 R2|BizTalk Adapter Pack 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)][!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|  

### <a name="prerequisites-when-using-a-biztalk-server"></a>當您使用 BizTalk Server 的必要條件  
當使用 BizTalk Server 使用配接器時，BizTalk Server 上需要下列軟體。 列出的順序安裝軟體。
  
|BizTalk Adapter Pack 2013 R2|BizTalk Adapter Pack 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)][!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。|  
|BizTalk Server 2013 R2|BizTalk Server 2013|  
|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|  

### <a name="prerequisites-when-using-ado"></a>使用 ADO 時的必要條件  
  **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]** 和 **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]** 包括 ADO 層 ( *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* 和 *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]* )。 這個 ADO 層可用來撰寫 ADO.NET 用戶端連接至 SAP 系統或 Siebel 系統。 您也可以使用 ADO 圖層與 SQL Server Integration Services (SSIS) 匯入和匯出資料從 LOB 應用程式和 SQL Server Reporting Services (SSRS) 來產生報表呈現資料從 LOB 系統。  
  
> [!NOTE]
>  僅適用於支援搭配使用 ADO 提供者與 SSRS  *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* 。  
  
使用的電腦上需要下列軟體[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]ADO 介面。 列出的順序安裝軟體。
  
|BizTalk Adapter Pack 2013 R2|BizTalk Adapter Pack 2013|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)][!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]|  
|Visual Studio 2013|Visual Studio 2012|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|[!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)], [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]|[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]|  
|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。|  

### <a name="prerequisites-when-using-microsoft-sharepoint"></a>使用 Microsoft SharePoint 時的必要條件  
 使用 Microsoft SharePoint 配接器的目標是為 SharePoint 入口網站上顯示資料的 LOB 應用程式。  
  
典型的安裝過程中，使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]SharePoint 可以在單一電腦或針對不同工作使用不同的電腦。 下表摘要說明每一部電腦的軟體必要條件。 如果您使用單一電腦，該電腦上需要的所有軟體。 列出的順序安裝軟體。  
  
|您用來執行 WCF 配接器服務開發精靈的電腦|您用來裝載 WCF 服務的電腦|您可以在其中定義外部內容類型使用 SharePoint Designer 的電腦|您使用 SharePoint 來呈現的資訊從 LOB 應用程式的電腦|  
|---|---|---|---|  
|**BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li> Visual Studio 2013</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>個別的企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</li></ul> **BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>Visual Studio 2012</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>個別的企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</li></ul>|**BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>個別的企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</li><li>隨附於作業系統的網際網路資訊服務 (IIS) 版本。 KB 224609 列出的版本。</li></ul>**BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>個別的企業應用程式用戶端和相關聯的軟體。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</li><li>隨附於作業系統的網際網路資訊服務 (IIS) 版本。 KB 224609 列出的版本。</li></ul>|Microsoft Office SharePoint Server 軟體開發套件 (SDK)|Microsoft Office 伺服器基礎結構已更新。 從下列網址下載[http://go.microsoft.com/fwlink/?LinkId=128344](http://go.microsoft.com/fwlink/?LinkId=128344)。|  
  
<a name="BKMK_SuppLOB"></a>   
## <a name="supported-enterprise-application-versions"></a>支援的企業應用程式版本  

若要查看特定的 LOB 系統版本所支援的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱**[支援的特定業務 (LOB) 系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**。 

此區段會列出每張介面卡，任何額外的資訊，例如 Dll 的任何用戶端所需的每個介面卡。  
  
### <a name="oracle-database-adapter"></a>Oracle 資料庫配接器  
  
-   選擇性： 如果您使用分散式的交易與 Oracle 資料庫時，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。  
  
-   若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。 請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。  

### <a name="oracle-e-business-adapter"></a>Oracle E-Business 配接器  
  
-   選擇性： 若要使用分散式的交易與 Oracle 資料庫，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。  
  
-   若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。 請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。  
  
### <a name="sap-adapter"></a>SAP adapter (SAP 配接器)  
  
-   [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]需要 RFC SDK，不論是否 SAP 系統是 Unicode 或非 Unicode 的 Unicode 版本。  
  
-   **必要驅動程式**： 下表列出所需的 Dll[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]與 SAP 系統的介面。 大部分的包含這些 Dll 的套件，必須先下載 SAP 服務商場。 若要取得 SAP 服務商場的下載項目： 
  
    1.  安裝 SAP 服務商場的下載管理員使用。  
  
    2.  設定的下載管理員 SAP 服務 marketplace 使用您的認證。  
  
    3.  授權您組織中的 SAP 系統管理員從 SAP 服務網站下載軟體。 這是必要的因為對 SAP 軟體發佈中心的存取權受到下載軟體的授權物件。 這可確保由授權的使用者只會下載軟體。  
  
    4.  安裝 SAPCAR 程式才可從您下載 SAP 服務商場上的封裝解壓縮檔案。 SAPCAR 也會提供 SAP 服務商場中。  
  
     32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，您必須擁有各自的 32 位元和 64 位元版本的 Dll。  
  
    -   在 32 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\System32 資料夾。  
  
    -   在 64 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\SysWow64 資料夾。 64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾。  
  
    |SAP 用戶端版本|必要的驅動程式|  
    |------------------------|----------------------|  
    |6.4|**BizTalk Adapter Pack 2013 只**<br /><br /> - **SAP RFC SDK 6.40 UNICODE**。 使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，請將所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾都複製到前面這個資料表的相關位置所述。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。 您可以下載.zip 檔案，從[http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。<br /><br /> -如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。 這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> * </sup> 352295。 您可以下載從 Dll [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。 Dll 的名稱為：<br /><br /> - **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll<br /><br /> -  **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll|  
    |7.0|- **SAP RFC SDK 7.00 UNICODE**。 使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，前面這個資料表所述複製所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾和相關的位置。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。 您可以下載.zip 檔案，從[http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。<br /><br /> -如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。 這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> * </sup> 352295。 您可以下載從 Dll [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。 Dll 的名稱為：<br /><br /> - **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll<br /><br /> - **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll|  
    |7.1|- **SAP RFC SDK 7.10 UNICODE**。 使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，請將所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾都複製到前面這個資料表的相關位置所述。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。 您可以下載.zip 檔案，從[http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。<br /><br /> Microsoft Visual c + + 執行階段 Dll 所需的 SAP 7.1 用戶端可從下列連結：<br /><br /> - **32 位元 SAP 7.1 用戶端**： 從 Vcredist_x86.exe [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086)。<br /><br /> -                                 **64 位元 SAP 7.1 用戶端**： 從 Vcredist_x64.exe [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087)。<br /><br /> -如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。 這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> * </sup> 352295。 您可以下載從 Dll [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。 Dll 的名稱為：<br /><br /> - **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll<br /><br /> - **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll|  
  
     * SNOTEs 是隨附於修正由 SAP 發行的版本資訊。  

### <a name="siebel-adapter"></a>Siebel 配接器  
沒有額外的步驟。
  
### <a name="sql-adapter"></a>SQL adapter (SQL 配接器)  
  
**必要驅動程式**:  
  
-   **適用於 SQL Server 2005**： 如果您在 SQL Server 中建立使用者定義型別 (Udt)，請確定 Udt 的個別的組件加入 GAC。  
  
-   **適用於 SQL Server 2014、 SQL Server 2012、 SQL Server 2008 R2、 SQL Server 2008 SP1**:  
  
    -   如果您使用 Udt 隨附於 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。 例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業，這些 Dll 必須存在於執行 BizTalk Server 電腦上。  
  
        -   請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。  
  
        -   請確定 SqlServerSpatial.dll System32 資料夾中。    
        
        您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，並選取**管理工具 – 基本**和**管理工具-完整**中**特徵選取**精靈頁面。          
  
    -   如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定已安裝 SQL 用戶端連接性 SDK。 您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  

    -   如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。

## <a name="64-bit-support"></a>64 位元支援

Siebel 配接器支援的 32 位元主控件執行個體。 它不支援在 64 位元主控件執行個體中執行 Siebel 配接器。 

所有其他配接器可以在 32 位元或 64 位元的主控件執行個體執行。 


  
 如需有關安裝 32 位元和 64 位元支援的安裝案例[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱[32 位元和 64 位元平台上安裝 BizTalk Adapter Pack 狀況](#BKMK_Install_Scenarios)。  
  
<a name="BKMK_Install_Adap"></a>   
## <a name="installing-the-biztalk-adapter-pack"></a>安裝 BizTalk Adapter Pack  
 請確定所有[軟體必要條件](#BKMK_Prereqs)會安裝，才能安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 您可以安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]下列兩種方式：  
  
-   **以互動模式**： 執行安裝精靈  
  
-   **以無訊息模式**： 使用命令列  
  
    > [!IMPORTANT]
    >  您必須在您安裝的電腦上系統管理權限[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，不論您是否要安裝使用精靈或命令列。  

### <a name="typical-vs-custom-installation"></a>一般與自訂安裝  
此區段會列出的安裝類型，以及與每個選項一起安裝的功能：  
  
-   **一般**和**完成**選項會安裝為配接器，與相關聯的資料提供者。 您沒有選擇特定的配接器的安裝的選項。  
  
-   **自訂**選項會與相關聯的資料提供者安裝一或多個介面卡。 您可以選擇要安裝哪一個配接器。 如果您選擇安裝資料提供者，您也必須安裝對應的配接器。 不過，您可以安裝配接器，而不需要安裝對應的資料提供者。 這樣做展開**ADO 提供者**節點，然後再選取您不想要安裝的提供者。 請參閱[以互動模式安裝 BizTalk Adapter Pack](#BKMK_Install_wizard)。  
  
     例如，如果您安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，您也必須安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。 不過，您可以安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]而不需要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。  
  
<a name="BKMK_Install_Scenarios"></a>   
### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-32-bit-and-64-bit-platforms"></a>在 32 位元和 64 位元平台上安裝 BizTalk Adapter Pack 狀況  
 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]適用於： 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]設計階段 （當產生作業的 LOB 應用程式上的中繼資料）
  
-   BizTalk Server 管理主控台設計階段 （適用於建立實體連接埠）
  
    > [!NOTE]
    >  BizTalk Server 管理主控台會以 32 位元 Microsoft Management Console (MMC) 應用程式執行。  
  
-   BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）

您可以使用單一電腦的所有這些 taks，或使用不同的電腦。 因為同時[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和 BizTalk MMC 是 32 位元處理程序，您必須安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]您完成設計階段工作的電腦上。 

#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-32-bit-platform"></a>在 32 位元平台上安裝 BizTalk Adapter Pack 狀況  
 在 32 位元平台上支援的案例包括：  
  
|Visual Studio 設計階段的|MMC 的 biztalk 設計階段|Biztalk 執行階段|Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段|  
|---|---|---|---|  
|安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|  
  
#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-64-bit-platform"></a>在 64 位元平台上安裝 BizTalk Adapter Pack 狀況  
 在 64 位元平台上支援的案例包括：  
  
|Visual Studio 設計階段的|MMC 的 biztalk 設計階段|Biztalk 執行階段|Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段|  
|---|---|---|---|  
|安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|**32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 64 位元 LOB 用戶端和其他必要的 Dll。|**32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 64 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。|  
  
> [!NOTE]
>  任何在電腦上您要執行設計階段工作，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-interactive-mode"></a>以互動模式安裝 BizTalk Adapter Pack  
完成下列步驟來安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用安裝精靈。  
  
1.  從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體上，執行**Setup.exe**。  
  
2.  選取**安裝 Microsoft BizTalk Adapter**。 在下一步 視窗中，選取**安裝 Microsoft BizTalk Adapter Pack**或**安裝 Microsoft BizTalk Adapter Pack (x64)**，視您的平台。  
  
    > [!NOTE]
    >  如果您要安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上為虛擬機器，安裝精靈可能會繼續進行通知的安裝程式正在檢查可用磁碟空間的對話方塊。 在這種情況下，我們建議您使用無訊息安裝選項。 請參閱[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題中）。  
  
3.  在 歡迎使用畫面上，選取**下一步**。  
  
4.  接受使用者授權合約 (EULA)，然後再選取**下一步**。  
  
5.  在**選擇安裝類型**:  
  
    -   若要安裝最常見的功能，請選取**一般**。  
  
    -   若要選取您想要安裝的配接器，請選取**自訂**，然後繼續進行下一個步驟。  
  
    -   若要安裝所有功能，請選取**完成**。  
  
        > [!IMPORTANT]
        >  若要安裝與您的企業應用程式互動，請選取您使用的介面卡**自訂**安裝。  
  
6. **需要**只有當您選擇自訂安裝。 如果您選擇**一般**或**完成**安裝，然後略過此步驟中，並移至步驟 7。  
  
    1.  在**自訂安裝程式**，依序展開**基底介面卡**若要查看可用的介面卡。  
  
    2.  您不想為配接器，請選取介面卡旁的圖示，然後選取**整個功能將無法使用**。  
  
    3.  展開**ADO 提供者**，然後選取您不想要安裝的提供者。  
  
    4.  選取 **[下一步]**。  
  
7.  選取 [安裝]。  
  
8.  在**客戶經驗改進計畫**，您可以選擇註冊。 如果您註冊時，您可以與 Microsoft 共用的下列資料：  
  
    -   您要安裝的電腦硬體的相關資料[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  
  
    -   資料與企業應用程式版本，您正在使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  
  
     選取 [確定]。 [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699)提供詳細資訊。  
  
    > [!NOTE]
    >  您隨時可以變更此設定處於修復模式，從執行安裝程式**程式**。  
  
9. 選取 [完成]。  
  
<a name="BKMK_SilentInst"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-silent-mode"></a>以無訊息模式安裝 BizTalk Adapter Pack  
 使用**msiexec**命令來執行無訊息安裝。 Msiexec 命令的一部分，請輸入您想要安裝的個別元件。 下表列出每個元件中的值[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 若要安裝 （移除） 特定元件使用這些值。 若要安裝 （移除） 多個元件，您可以使用以逗號分隔這些值的組合。  
  
|元件名稱|命令列屬性的對應值|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|DbFeature|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|OracleEBSFeature|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|SapBaseAdapterFeature|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|SiebelBaseAdapterFeature|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|SqlFeature|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|SapAdoFeature<br /><br /> **請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]也。|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|SiebelAdoFeature<br /><br /> **請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]也。|  
|所有元件|ALL|  
  
> [!IMPORTANT]
>  功能名稱會區分大小寫。  
  
 下列步驟說明如何完成的無訊息安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]為不同的元件。  
  
##### <a name="install-in-silent-mode"></a>以無訊息模式安裝  
  
1.  開啟命令提示字元，並移至[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]根中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。  
  
2.  執行下列命令，根據您想要安裝：  
  
    > [!NOTE]
    >  若要執行無訊息安裝在 x64 架構的平台上，取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`在下列命令。  
  
    -   若要執行完整安裝，安裝所有包括.NET Framework 資料提供者的介面卡，請輸入：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   只安裝[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   只安裝[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   只安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]連同[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   只安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   若要安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]連同[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   只安裝[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   若要安裝的所有基底介面卡，請輸入：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   若要安裝兩個.NET Framework 資料提供者，請輸入：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   以逗號分隔之元件的自訂安裝的任何類型。 例如，若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]與[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，而[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   您也可以選擇的 CEIP 註冊為無訊息安裝的一部分。 類型：  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         根據預設選項是 false。 
  
        > [!IMPORTANT]
        >  在安裝時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式的評估版，CEIP 的預設選項為 true。  
  
     如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。 或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。
  
<a name="BKMK_PostInst"></a>   
### <a name="after-installing-the-biztalk-adapter-pack"></a>安裝 BizTalk Adapter Pack 之後  
 您可能需要在安裝之後，執行下列工作[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，根據您想要使用每張介面卡執行哪些作業：  
  
-   [設定 Oracle 資料庫配接器使用較新版的 Oracle.DataAccess.dll](#BKMK_ConfigNewOracleDLL) OracleDB 組態檔中。  
  
-   [建立 SQL Server 資料庫物件 （僅適用於 SAP 配接器）](#BKMK_CreateSQLServer) SAP 系統中叫用交易式 Rfc (tRFCs)。  
  
-   [註冊配接器繫結](#BKMK_Register_Bindings)和.NET Framework 資料提供者安裝精靈時若要這樣做。  
  
-   [判斷公開金鑰和版本](#BKMK_PubKey)的不同配接器檔案。  
  
-   [安裝自訂 Rfc](#BKMK_InstallCustomRFC)如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。  
  
<a name="BKMK_ConfigNewOracleDLL"></a>   
#### <a name="configure-the-oracle-database-adapter-to-use-a-newer-oracledataaccessdll-version"></a>設定 Oracle 資料庫配接器使用較新版的 Oracle.DataAccess.dll  
 當您設定要使用 Wcf-oracledb 配接器，或使用 Visual Studio 使用產生的配接器的連接埠時，會顯示訊息，配接器需要 Oracle.DataAccess.dll 2.111.7.0 版本。 若要解決此訊息，請安裝支援的 Oracle.DataAccess.dll 版本 (請參閱[支援版本清單](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))，然後更新`bindingRedirect`OracleDB 組態檔中的項目。 步驟：  
  
1.  在 BizTalk 伺服器上，請移至下列資料夾：  
  
     *磁碟機*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin  
  
     *磁碟機*: \Program 檔案 (x86) \Microsoft BizTalk Adapter Pack\bin  
  
2.  開啟 Microsoft.Adapters.OracleDB.config 檔案。  
  
3.  找不到下列區段，並複製/貼上下列：  
  
    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  
  
    ```  
  
    > [!NOTE]
    >  在此範例中，我們設定*newVersion* 2.112.1.00 至。 此值設為已安裝的版本。  
  
> [!IMPORTANT]
>  -   如果此群組中有多個 BizTalk 伺服器，請在群組中的所有 BizTalk 伺服器上進行這項變更。  
> -   *NewVersion*值需要更新 Oracle.DataAccess.dll 檔案的電腦上安裝的版本為基礎。  Oracle.DataAccess.dll 隨附於您從 Oracle 安裝 Oracle 用戶端。  您只必須安裝 Oracle 用戶端版本， [BizTalk 配接器組件支援](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)。  
  
<a name="BKMK_CreateSQLServer"></a>   
#### <a name="create-sql-server-database-objects-only-for-the-sap-adapter"></a>建立 SQL Server 資料庫物件 （僅適用於 SAP 配接器）  
 若要啟動 tRFCs SAP 系統中，執行*SapAdapter-DbScript-Install.sql* SQL 指令碼。 此指令碼會隨[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，並在 SQL Server 中建立資料庫物件。 指令碼通常會安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 只要您輸入該資料庫名稱來叫用 tRFCs 使用配接器時，您可以針對任何 SQL Server 資料庫，執行此指令碼。  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-adapter-bindings"></a>註冊配接器繫結  
 期間[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，安裝精靈可能無法註冊配接器繫結或.NET Framework Data Provider for mySAP Business Suite，但安裝程式才能繼續使用配接器安裝。 這可能會造成問題的 Windows Communication Foundation (WCF) 安裝，因為[!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。  
  
完成這些步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結或.NET Framework 資料提供者。  
  
###### <a name="register-the-adapter-bindings-or-the-net-framework-data-providers"></a>註冊配接器繫結或.NET Framework 資料提供者  
  
1.  移至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  註冊配接器繫結：  
  
    1.  搜尋`system.serviceModel`項目，並將其下的面一行加入：  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。  
  
    3.  尋找遺漏的配接器繫結。 新增下列各節下的`bindingElementExtensions`節點，根據遺失的配接器繫結。 如果安裝精靈無法註冊任何，您必須註冊的所有繫結。  
  
         如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。  
  
    5.  尋找遺漏的配接器繫結。 新增下列各節下的`bindingExtensions`節點，根據遺失的配接器繫結。 如果安裝精靈無法註冊任何，您必須註冊的所有繫結。  
  
         如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  如需如何判斷公開金鑰資訊，請參閱[判斷公開金鑰和版本](#BKMK_PubKey)。  
  
4.  註冊.NET Framework 資料提供者：  
  
    1.  搜尋`DbProviderFactories`system.data 節點下的項目。  
  
    2.  尋找遺漏的.NET Framework 資料提供者。 新增下列各節下的`DbProviderFactories`節點，根據遺失的提供者。 如果安裝精靈無法註冊任何，您必須註冊所有提供者。  
  
         如[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，加入：  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，加入：  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  關閉並儲存 machine.config 檔。  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determine-the-public-key-and-version"></a>判斷公開金鑰和版本  
 完成下列步驟來判斷公開金鑰和配接器或.NET Framework Data Provider 的版本。  
  
###### <a name="determine-the-public-key"></a>判斷公開金鑰  
  
1.  移至 Windows 目錄，通常 C:\WINDOWS\assembly。  
  
2.  以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。 下表列出每個配接器和提供者 Dll 的名稱：  
  
    |配接器/.NET Framework Data Provider|DLL 的名稱|  
    |---|---|  
    |[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|Microsoft.Adapters.SAP|  
    |[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|Microsoft.Adapters.Siebel|  
    |[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|Microsoft.Adapters.OracleDB|  
    |[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|Microsoft.Adapters.OracleEBS|  
    |[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|Microsoft.Adapters.Sql.dll|  
    |[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|Microsoft.Data.SAPClient|  
    |[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|Microsoft.Data.SiebelClient|  
  
3.  在**一般**索引標籤上，**公開金鑰語彙基元**值是 DLL 的公開金鑰。 **版本**值是 DLL 的版本號碼。  
  
4.  複製的公開金鑰，然後選取**取消**。  
  
<a name="BKMK_InstallCustomRFC"></a>   
#### <a name="install-the-custom-rfcs"></a>安裝自訂的 Rfc  
 您只需要執行這項工作，如果您想要使用[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。 如需安裝自訂 Rfc 的指示，請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)中[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]文件。 
  
> [!IMPORTANT]
>  如果您使用較早版本所提供的自訂 Rfc 的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，則您必須將它們升級為此版本提供的 Rfc。 藉由移除舊版的 Rfc，執行這項操作，然後安裝 Rfc 隨附於此版本。  

## <a name="installing-the-enterprise-applications"></a>安裝企業應用程式  
步驟和指示，以安裝不同的企業部署 LOB 系統，我們會引導您使用其特定安裝 recommendnd。 如果有的話，也參照特定的組態變更，及其配接器文件。   

## <a name="installation-and-post-installation-checklist"></a>安裝及安裝後的檢查清單  
  
-   請確定您已安裝所有[軟體必要條件](#BKMK_Prereqs)使用正確的安裝選項。
  
-   請確定您已安裝在電腦上安裝企業 LOB 應用程式的支援的版本[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。  
  
-   若要安裝的企業 LOB 系統，您想要連接的介面卡，請確定您已安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**自訂**安裝選項。 請確定您並未安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**完成**安裝選項。 請參閱[安裝 BizTalk Adapter Pack](#BKMK_Install_Adap)。  
  
-   如果您想要進行 tRFC 呼叫 SAP 系統使用[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，請確定您在 SQL Server 資料庫中建立必要的資料表。 請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。
  
-   執行時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝精靈中，您可能會收到錯誤訊息，表示安裝程式無法註冊繫結。 如果是的話，手動註冊它們。 請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。  
  
-   如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]一部分[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定您已安裝自訂 Rfc SAP 系統上。 請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="change-the-biztalk-adapter-pack-installation"></a>變更 BizTalk Adapter Pack 安裝  
 完成下列步驟來變更[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。 請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝您執行安裝精靈來修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。  
  
 您可以修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝在互動模式 （安裝精靈中），或以無訊息模式 （命令列）。
  
#### <a name="change-the-bap-installation-in-interactive-mode"></a>變更以互動模式 BAP 安裝  
  
1.  使用 BizTalk Server 系統管理員群組的成員帳戶登入。  
  
2.  在**程式和功能**，選取**解除安裝程式**。  
  
3.  以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**變更**。  
  
4.  在 歡迎使用畫面上，選取**下一步**。  
  
5.  在**變更、 修復或移除安裝**:  
  
    -   若要選取您想要安裝的元件，請選取**變更**並移至步驟 6。  
  
    -   若要修復最近安裝中的錯誤，請選取**修復**並移至步驟 7。  
  
    -   若要移除 Microsoft[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從電腦中，選取**移除**然後移至步驟 10。  
  
6.  如果您選擇修改安裝：  
  
    -   展開**Microsoft BizTalk Adapter Pack**節點，選擇要安裝的基底介面卡、.NET Framework 資料提供者，或兩者。  
  
    -   展開**基底介面卡**節點，選擇要安裝的所有介面卡或特定介面卡。  
  
    -   展開**ADO 提供者**節點，選擇要安裝所有的提供者或特定的提供者。  
  
    -   選取 **[下一步]**。  
  
    -   選取**變更**，然後選取**完成**。  
  
7.  如果您選擇要在修復安裝，**準備好修復 Microsoft BizTalk Adapter Pack**對話方塊中，選取**修復**。 精靈會啟動修復安裝。  
  
8.  若有需要，變更您的喜好設定有關選擇加入 ceip，，然後選取 **確定**。 
  
9. 選取 [完成]。  
  
10. 如果您選擇要移除介面卡，在**準備好要移除 Microsoft BizTalk Adapter Pack**對話方塊中，選取**移除**，然後選取**完成**。  
  
#### <a name="change-the-bap-installation-in-silent-mode"></a>變更 BAP 安裝以無訊息模式  
  
1.  開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。  
  
2.  執行類似下列的命令：  
  
    > [!NOTE]
    >  若要修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]x64 平台上，在下列命令，以無訊息模式安裝取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，並安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。  
  
     使用不同的值`REMOVE`和`ADDLOCAL`屬性，您可以新增或移除特定元件。 中的資料表是指[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題） 有關您可以使用這些屬性的值。  
  
     您也可以使用 /f 選項 msiexec 命令的一部分來執行無訊息的修復。 例如：  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     您可以使用各種不同的組合使用 /f 選項。 如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。 或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。  
  
    > [!IMPORTANT]
    >  修改時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇加入或退出 CEIP。 即使您明確地設定為 true 或 false CEIP_OPTIN 安裝會保持在您選擇喜好設定。  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="removing-the-biztalk-adapter-pack"></a>移除 BizTalk Adapter Pack  
  
> [!IMPORTANT]
>  如果您使用的 tRFC 功能的 SQL Server 資料庫中建立資料表[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，您必須手動移除之後再移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝會複製 SapAdapter-DbScript-Uninstall.sql 檔案通常位於\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 執行這個檔案來移除您所建立的資料表。  
  
完成下列步驟來移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從您的電腦。 請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝您執行安裝精靈來移除介面卡。  
  
 您可以移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以互動模式 （安裝程式精靈），或以無訊息模式 （命令列）。
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-interactive-mode"></a>解除安裝 BizTalk Adapter Pack，以互動模式  
  
1.  在**程式和功能**，選取**解除安裝程式**。  
  
2.  以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**解除安裝**。  
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-silent-mode"></a>解除安裝 BizTalk Adapter Pack，以無訊息模式  
  
1.  開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。  
  
2.  執行下列命令：  
  
    > [!NOTE]
    >  若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在 x64 平台上，下列命令，在無訊息模式取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。  
  
     藉由提供不同的值`REMOVE`屬性，您可以移除特定元件從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。 中的資料表是指[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題） 有關您可以使用這個屬性的值。  
  
     若要完全移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，執行下列命令：  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。 或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。
  
<a name="BKMK_PostRemove"></a>   
### <a name="after-removing-the-biztalk-adapter-pack"></a>移除 BizTalk Adapter Pack 之後  
 您可能需要執行下列步驟移除後[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]:  
  
-   如果安裝精靈無法執行這項操作，移除配接器繫結或.NET Framework 資料提供者註冊，
  
-   移除自訂 Rfc，如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]
  
<a name="BKMK_Remove_Binding"></a>   
#### <a name="remove-the-bindings-or-the-net-framework-data-provider-registration"></a>移除繫結或.NET Framework 資料提供者登錄  
 完成這些步驟*只*如果安裝精靈無法移除 machine.config 檔中的配接器繫結或.NET Framework 資料提供者註冊。  
  
###### <a name="remove-the-adapter-bindings-or-net-framework-data-provider-registration"></a>移除配接器繫結或.NET Framework 資料提供者登錄  
  
1.  移至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  移除配接器繫結註冊：  
  
    1.  搜尋`system.serviceModel`項目，並移除下列項目底下：  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。  
  
    3.  移除下列各節下的`bindingElementExtensions`節點，根據可用的配接器繫結。 如果安裝精靈會移除任何失敗，您必須移除所有的繫結。  
  
         如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。  
  
    5.  移除下列各節下的`bindingExtensions`節點，根據可用的配接器繫結。 如果安裝精靈會移除任何失敗，您必須移除所有的繫結。  
  
         如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  移除.NET Framework 資料提供者的登錄：  
  
    -   搜尋`DbProviderFactories`system.data 節點下的項目。  
  
    -   尋找中仍登錄的.NET Framework 資料提供者。 移除下列各節下的`DbProviderFactories`節點，根據現有的.NET Framework 資料提供者。 如果有的話，您必須移除所有的提供者。  
  
         如[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，移除：  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         如[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，移除：  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  關閉並儲存 machine.config 檔。  
  
<a name="BKMK_Remove_SAP_Pro"></a>   
#### <a name="remove-the-custom-rfcs"></a>移除自訂 Rfc  
完成此步驟，移除您安裝在 SAP 系統的自訂 Rfc。 請參閱[安裝或移除自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
## <a name="troubleshoot-biztalk-adapter-pack-installation"></a>BizTalk Adapter Pack 安裝問題疑難排解  
 以下是安裝時，您可能會面臨一些問題[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 安裝相關問題的完整清單，請參閱**疑難排解**每個配接器的主題。  
  
-   **在 64 位元電腦上的執行安裝程式可能會擲回錯誤存取結構描述檔案時發生**  
  
     [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝存取時擲回錯誤 **Microsoft.Adapters。*\<AdapterName\>*_schema.xml** 檔案，但配接器的安裝會繼續進行。  
  
     **可能的原因**  
  
     如果 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]已安裝的相同電腦上，目標結構描述所用的檔案都相同。 如此一來，檔案安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]64 位元安裝程式會嘗試存取權限時，可能是由 IIS 所使用。  
  
     **解決方式**  
  
     手動複製 **Microsoft.Adapters。*\<AdapterName\>*_schema.xml** 檔案從`C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas`」 至`C:\Windows\System32\inetsrv\config\schema`。  