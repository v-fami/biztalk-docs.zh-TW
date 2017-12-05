---
title: "安裝 Microsoft BizTalk Adapter for SQL Server-2016年 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc6b94e-1cac-4b90-8567-05b33caa9bf3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bab2a1edc7f3f19a8f76a041472a8c6d01b7743d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2016"></a>安裝 Microsoft BizTalk Adapter for SQL Server-2016
安裝[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]隨附[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。

 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以搭配使用：  
  
-   .NET 應用程式  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
 根據您如何使用配接器，所需的軟體而異。  
 
  
<a name="BKMK_prereq_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a>當配接器使用.NET 應用程式的必要條件  
您要在其中撰寫可取用的.NET 應用程式的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 安裝軟體的順序，如下所列。  

||
|---|
|Windows Server 2016 <br />Windows Server 2012 R2 <br />Windows 10 <br />-Windows 8.1    |
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|
|SQL Server 用戶端程式庫。 請參閱[支援的版本，](#BKMK_SuppLOB) （在本主題中）。|

<a name="BKMK_prereq_BTS"></a>     
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a>搭配 BizTalk Server 使用配接器時的必要條件  
如果您使用的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 列出的順序安裝軟體。  

||
|---|
|Windows Server 2016 <br />Windows Server 2012 R2 <br />Windows 10 <br />-Windows 8.1    |
|.NET Framework 4.6.*x*|
|Visual Studio 2015|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。|
|[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|
|SQL Server 用戶端程式庫。 請參閱[支援的版本，](#BKMK_SuppLOB) （在本主題中）。|

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a>支援的 SQL Server 版本與用戶端程式庫  
 下列章節提供支援的 SQL Server 版本與用戶端所需的程式庫[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
-   **支援的伺服器版本**: SQL Server 2016、 SQL Server 2014
  
-   **支援的用戶端版本**: Microsoft[!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]連接到 SQL Server 所需的用戶端 Dll 的組合。 您不需要明確安裝在電腦上的任何用戶端 Dll。  
  
-   **必要驅動程式**:  
  
    -   如果您使用 Udt 隨附於 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。 例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業，這些 Dll 必須存在於執行 BizTalk Server 電腦上。  
  
        -   請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。  
  
        -   請確定 SqlServerSpatial.dll System32 資料夾中。  
  
         您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，並選取**管理工具 – 基本**和**管理工具-完整**中**特徵選取**精靈頁面。  
  
    -   如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定已安裝 SQL 用戶端連接性 SDK。 您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  
  
    -   如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。  
  
<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a>64 位元支援 

[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以在 32 位元或 64 位元的主控件執行個體中執行。

 如需支援的安裝案例，32 位元和 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[32 位元和 64 位元安裝案例](#BKMK_Install_Scenarios)（在本主題中）。
  
<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a>安裝 SQL 配接器  
 請確定您已安裝之前安裝的必要條件[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 請參閱[.NET 必要條件](#BKMK_prereq_NET)（本主題中），或[BizTalk Server 必要條件](#BKMK_prereq_BTS)（在本主題中）。
  
 您可以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：  
  
-   **以互動模式**使用安裝精靈
  
-   **以無訊息模式**使用 msiexec 命令列中  
  
    > [!IMPORTANT]
    >  您必須在您安裝的電腦上系統管理權限[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，不論是否使用精靈或命令列安裝。    

### <a name="BKMK_Install_Scenarios"></a>32 位元和 64 位元安裝案例
 與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：  
  
-   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計階段 （當產生作業的中繼資料）。  
  
-   BizTalk Server 管理主控台 （用於建立實體連接埠） 的設計階段。  
  
    > [!NOTE]
    >  BizTalk Server 管理主控台會以 32 位元 Microsoft Management Console (MMC) 應用程式執行。  
  
-   BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）。  
  
 您可以安裝在同一部電腦或不同的電腦執行所有這些工作地方。 因為同時[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和 BizTalk MMC 是 32 位元處理程序，您必須安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您要執行設計階段工作的電腦上。 支援下列案例安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元和 64 位元平台上。  
  
#### <a name="32-bit-install-scenarios"></a>32 位元的安裝案例  
 當安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元平台上。  
  
|Visual Studio 設計階段|BizTalk MMC 設計階段|BizTalk 執行階段|Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段|  
|---|---|---|---|  
|安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|  
  
#### <a name="64-bit-install-scenarios"></a>64 位元的安裝案例  
 當安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]64 位元平台上。  
  
> [!NOTE]
>  在您要執行設計階段工作使用的任何電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
|Visual Studio 設計階段|BizTalk MMC 設計階段|BizTalk 執行階段|Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段|  
|---|---|---|---|  
|安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|**32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 64 位元用戶端和其他必要的 Dll。|**32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 64 位元用戶端和其他必要的 Dll。<br /><br /> 安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。|  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-adapter-in-interactive-mode"></a>在互動模式中安裝配接器  
完成下列步驟來安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用安裝精靈。  
  
1.  執行安裝程式。  
  
    > [!NOTE]
    >  如果您要安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上為虛擬機器，安裝精靈可能會繼續進行通知的安裝程式正在檢查可用磁碟空間的對話方塊。 在這種情況下，我們建議您使用無訊息安裝選項。 如需詳細資訊，請參閱[以無訊息模式安裝 SQL 配接器](#BKMK_SilentInst)（在本主題中）。
  
2.  閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。  
  
3.  閱讀並接受使用者授權合約 (EULA)，，然後按一下**下一步**。  
  
4.  在**目的地資料夾**對話方塊方塊中，指定您要安裝的位置[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，按一下 **下一步**，然後按一下 **安裝**。  
  
5.  在**客戶經驗改進計畫**對話方塊方塊中，指定您想要註冊的客戶經驗改進計畫 (CEIP)。 一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，將會與 Microsoft 共用的下列資料：  
  
    -   您要安裝的電腦硬體的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    -   您用來連接使用的 SQL Server 版本的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
     指定您的選擇，然後按一下**確定**。  
  
    > [!NOTE]
    >  您可以隨時變更您的喜好設定有關在修復模式中執行安裝程式，從 控制台註冊 CEIP。  
  
6.  按一下 **[完成]**。  
  
<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a>以無訊息模式安裝 SQL 配接器 
完成下列步驟來執行的無訊息安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用`msiexec`命令。  
  
1.  開啟命令提示字元並瀏覽至您用來讓安裝程式的資料夾。  
  
2.  執行下列命令以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
    > [!NOTE]
    >  若要執行無訊息安裝在 x64 架構的平台，在下列命令，取代 SqlAdapterSetup64.msi 為 SqlAdapterSetup.msi。  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn  
    ```  
  
     您也可以選擇的 CEIP 註冊為無訊息安裝的一部分。 一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，將會與 Microsoft 共用的下列資料：  
  
    -   您要安裝的電腦硬體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    -   您用來連接使用的 SQL Server 版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
     若要註冊 ceip，執行下列命令：  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
    ```  
  
     根據預設，此選項為 false。  
  
     如需有關`msiexec`命令中，輸入`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。  
  
<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a>後續安裝工作  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a>註冊繫結  
完成這些步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結。  
  
1.  瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  若要註冊配接器繫結：  
  
    1.  搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。  
  
    3.  新增下列區段，"bindingElementExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。  
  
    5.  新增下列區段，"bindingExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  如需如何判斷公開金鑰資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。  
  
4.  關閉並儲存 machine.config 檔。  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a>判斷公開金鑰和版本  
完成下列步驟來判斷公開金鑰和版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
1.  瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。  
  
2.  以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。 下表列出的 Dll 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    |配接器|DLL 的名稱|  
    |---|---|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|Microsoft.Adapters.Sql.dll|  
  
3.  在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。 同樣地，根據值**版本**標籤指定 dll 的版本號碼。  
  
4.  複製的公開金鑰，然後按一下**取消**。  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a>更新或變更 SQL 配接器安裝  
 執行下列步驟來修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。 請確定您有[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝您執行安裝精靈來修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。  
  
 您可以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式安裝：  
  
-   **以互動模式**執行安裝精靈。  
  
-   **以無訊息模式**使用命令列。  
  
#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a>更新 SQL 配接器安裝在互動模式中  
  
1.  按一下**啟動**，然後按一下 **控制台**。  
  
2.  在控制台中，按兩下**程式和功能**。  
  
3.  在**程式和功能**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下 **變更**。  
  
4.  閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。  
  
5.  在**變更、 修復或移除安裝**對話方塊中，按一下 **修復**。  
  
6.  在**準備好修復 Microsoft BizTalk Adapter for SQL Server**對話方塊中，按一下 **修復**。  
  
7.  若有需要，變更您的喜好設定有關選擇加入 ceip，，然後按一下 **確定**。  
  
8.  按一下 **[完成]**。  
  
#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a>SQL 配接器安裝，以無訊息模式更新  
  
1.  開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。  
  
2.  執行下列命令：  
  
    > [!NOTE]
    >  若要修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]x64 平台上，下列命令，在無訊息模式中的安裝取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn /f  
    ```  
  
    > [!IMPORTANT]
    >  修改時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇加入或退出 CEIP。 喜好設定會維持您指定在安裝時，即使您明確地設定 CEIP_OPTIN 為 true 或 false。  
  
     如需有關`msiexec`命令類型`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a>解除安裝或移除 SQL 配接器  
 執行下列步驟來移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從您的電腦。 請確定您有[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝在執行安裝程式精靈，以移除之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 您可以移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：  
  
-   **以互動模式**執行安裝精靈。  
  
-   **以無訊息模式**使用命令列。  
  
#### <a name="uninstall-the-sql-adapter-in-interactive-mode"></a>解除安裝 SQL 配接器以互動模式  
  
1.  按一下**啟動**，然後按一下 **控制台**。  
  
2.  在控制台中，按兩下**程式和功能**。  
  
3.  在**新增或移除程式**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下 **移除**。  
  
4.  在對話方塊中，按一下 **是**。  
  
#### <a name="uninstall-the-sql-adapter-in-silent-mode"></a>解除安裝 SQL 配接器，以無訊息模式  
  
1.  開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。  
  
2.  執行下列命令：  
  
    > [!NOTE]
    >  若要移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在 x64 平台上，下列命令，在無訊息模式取代 SqlAdapterSetup.msi SqlAdapterSetup64.msi。  
  
    ```  
    msiexec /x SqlAdapterSetup.msi /qn  
    ```  
  
     此命令會移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從電腦。  
  
     如需有關`msiexec`命令中，輸入`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。  
  
<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a>解除安裝後工作  
 如果[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式無法移除配接器繫結同時移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須手動移除它們。 下列章節描述如何手動移除的繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
完成這些步驟*只*如果安裝精靈無法移除 machine.config 檔案中的配接器繫結。  
  
1.  瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
    -   Microsoft.NET framework 3.5 SP1、 \<*版本*\>是.NET framework 版本 v2.0.50727。  
  
    -   Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  若要移除介面卡繫結註冊：  
  
    1.  搜尋 「 system.serviceModel 的項目，並移除下列項目底下：  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。  
  
    3.  移除 「 bindingElementExtensions 」 節點下的下一節。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。  
  
    5.  移除 「 bindingExtensions 」 節點下的下一節。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  關閉並儲存 machine.config 檔。  
  
## <a name="see-also"></a>另請參閱
[安裝 SQL 配接器](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)