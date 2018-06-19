---
title: BizTalk 配接器組件 2016 軟體必要元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65a063ca-37ae-420b-9d48-e6730caf17e3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0b33203d1e8e5b36c9fb8a54167c111a427b244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22227118"
---
# <a name="software-prerequisites-for-biztalk-adapter-pack-2016"></a>BizTalk 配接器組件 2016 軟體必要元件
列出 Microsoft 的軟體需求[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)](BAP) 隨附[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。
  
[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]可以取用從：  
  
-   .NET 應用程式  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   ADO 介面  
  
-   Microsoft SharePoint 入口網站  
  
 根據您如何使用配接器，所需的軟體而異。  
  
## <a name="prerequisites-when-using-a-net-application"></a>使用.NET 應用程式時的必要條件  
當取用配接器使用.NET 應用程式，下列的軟體需要在開發電腦 （您要在其中建立.NET 應用程式的電腦）。 列出的順序安裝軟體。
  
|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|
|企業應用程式用戶端和相關聯的軟體。 請參閱**支援企業應用程式版本**（在本主題中）。|

## <a name="prerequisites-when-using-biztalk-server"></a>使用 BizTalk Server 時的必要條件  
當使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上需要下列軟體，若要取用配接器，您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 列出的順序安裝軟體。
 
|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。|
|[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]|
|企業應用程式用戶端和相關聯的軟體。 請參閱**支援企業應用程式版本**（在本主題中）。|

## <a name="prerequisites-when-using-ado"></a>使用 ADO 時的必要條件  
  **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]** 和 **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]** 包括 ADO 層 ( *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* 和 *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]* )，可以用於寫入 ADO.NET 用戶端連接至 SAP 系統或 Siebel 系統。 您也可以使用 ADO 圖層與 SQL Server Integration Services (SSIS) 匯入和匯出資料從 LOB 應用程式和 SQL Server Reporting Services (SSRS) 來產生報表呈現資料從 LOB 系統。  
  
> [!NOTE]
>  僅適用於支援搭配使用 ADO 提供者與 SSRS [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。  
  
使用的電腦上需要下列軟體[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]ADO 介面。 列出的順序安裝軟體。  

|BizTalk Adapter Pack 2016|
|---|
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1  </li></ul>|
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|
|<ul><li>Microsoft SQL Server 2016</li><li>Microsoft SQL Server 2014 SP1</li></ul> |
|企業應用程式用戶端和相關聯的軟體。 請參閱**支援企業應用程式版本**（在本主題中）。|

## <a name="prerequisites-when-using-sharepoint"></a>使用 SharePoint 時的必要條件  
使用 Microsoft SharePoint 配接器的目標是為 SharePoint 入口網站上顯示資料的 LOB 應用程式。  
  
典型的安裝過程中，使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]SharePoint 可以使用單一電腦或針對不同工作使用不同的電腦。 下表列出每一部電腦的軟體必要條件。 如果您使用單一電腦，必須在該電腦上安裝所有軟體。 列出的順序安裝軟體。  
  
|您用來執行 WCF 配接器服務開發精靈的電腦|您用來裝載 WCF 服務的電腦|您可以在其中定義外部內容類型使用 SharePoint Designer 的電腦| 
|---|---|---|  
|<ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1</li><br/><br/><li>.NET Framework 4.6.*x*</li><br/><br/><li>Visual Studio 2015</li><br/><br/><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><br/><br/><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><br/><br/><li>企業應用程式用戶端和相關聯的軟體。 請參閱**支援企業應用程式版本**（在本主題中）。</li></ul> | <ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1</li><br/><br/><li>.NET Framework 4.6.*x*</li><br/><br/><li>Visual Studio 2015</li><br/><br/><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><br/><br/><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><br/><br/><li>企業應用程式用戶端和相關聯的軟體。 請參閱**支援企業應用程式版本**（在本主題中）。</li><br /><br /><li>隨附於作業系統的網際網路資訊服務 (IIS) 版本。 [KB 224609](https://support.microsoft.com/kb/224609)列出的版本。</li> </ul>| Microsoft SharePoint 的軟體開發套件 (SDK)|
  
<a name="BKMK_SuppLOB"></a>   
## <a name="supported-enterprise-application-versions"></a>支援的企業應用程式版本  
若要查看特定的 LOB 系統版本所支援的 BizTalk Adapter Pack，請參閱**[支援的特定業務 (LOB) 系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**。

此區段會列出每張介面卡，任何額外的資訊，例如 Dll 的任何用戶端所需的每個介面卡。  
  
### <a name="oracle-database-adapter"></a>Oracle 資料庫配接器  
  
-   選擇性： 如果您使用分散式的交易與 Oracle 資料庫時，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。  
  
-   若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。 請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。  

### <a name="oracle-e-business-adapter"></a>Oracle E-Business 配接器  
  
-   選擇性： 若要使用分散式的交易與 Oracle 資料庫，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。  
  
-   若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。 請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。  
  
### <a name="sap-adapter"></a>SAP adapter (SAP 配接器)  
  
-   [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]需要 RFC SDK，不論是否 SAP 系統是 Unicode 或非 Unicode 的 Unicode 版本。  
  
-   **必要驅動程式**： 下表列出所需的 Dll[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]與 SAP 系統互動：  
  
    |SAP 用戶端版本|必要的驅動程式|  
    |---|---|  
    |7.2|- **SAP RFC SDK 7.10 UNICODE**。 使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，請將所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾都複製到前面這個資料表的相關位置所述。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。 您可以下載.zip 檔案，從[http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。<br /><br /> Microsoft Visual c + + 執行階段 Dll 所需的 SAP 7.1 用戶端可從下列連結：<br /><br /> - **32 位元 SAP 7.1 用戶端**： 從 Vcredist_x86.exe [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086)。<br /><br /> -                                 **64 位元 SAP 7.1 用戶端**： 從 Vcredist_x64.exe [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087)。<br /><br /> -如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。 這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> * </sup> 352295。 您可以下載從 Dll [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032)。 此連結會有 「 附件 」 選項，從您可以在此下載封裝。 Dll 的名稱為：<br /><br /> - **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll<br /><br /> - **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll|  
  
     > [!TIP]
     > SNOTEs 是隨附於修正由 SAP 發行的版本資訊。  

    大部分的包含這些 Dll 的套件，必須先下載 SAP 服務商場。 若要取得 SAP 服務商場的下載項目： 
  
    1.  安裝 SAP 服務商場的下載管理員使用。  
  
    2.  設定的下載管理員 SAP 服務 marketplace 使用您的認證。  
  
    3.  授權您組織中的 SAP 系統管理員從 SAP 服務網站下載軟體。 這是必要的因為對 SAP 軟體發佈中心的存取權受到下載軟體的授權物件。 這可確保由授權的使用者只會下載軟體。  
  
    4.  安裝 SAPCAR 程式才可從您下載 SAP 服務商場上的封裝解壓縮檔案。 SAPCAR 也會提供 SAP 服務商場中。  
  
     32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，您必須擁有各自的 32 位元和 64 位元版本的 Dll。  
  
    -   在 32 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\System32 資料夾。  
  
    -   在 64 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\SysWow64 資料夾。 64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾。  
    
    
### <a name="siebel-adapter"></a>Siebel 配接器  
沒有額外的步驟。
  
### <a name="sql-adapter"></a>SQL adapter (SQL 配接器)  
  
**必要驅動程式**適用於 SQL Server 2014:  
  
-   如果您使用 Udt 隨附於 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。 例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業，這些 Dll 必須存在於執行 BizTalk Server 電腦上。  
  
    -   請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。  
  
    -   請確定 SqlServerSpatial.dll System32 資料夾中。    
        
    您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，並選取**管理工具 – 基本**和**管理工具-完整**中**特徵選取**精靈頁面。          
  
-   如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定已安裝 SQL 用戶端連接性 SDK。 您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  

-   如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。

## <a name="64-bit-host-instance-support"></a>64 位元主控件執行個體的支援

Siebel 配接器支援的 32 位元主控件執行個體。 它不支援在 64 位元主控件執行個體中執行 Siebel 配接器。 

所有其他配接器可以在 32 位元或 64 位元的主控件執行個體執行。 
  
 如需有關安裝 32 位元和 64 位元支援的安裝案例[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱**32 位元和 64 位元安裝案例**在[安裝 BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)。  
 
## <a name="next-step"></a>下一步
[安裝 BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)  
