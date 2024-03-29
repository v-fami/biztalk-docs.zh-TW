---
title: 安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013年 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56c31d0d-783b-41ee-8265-56c9547e9dca
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f248e1db8bc57e928e85e908e679d4ded1ec38aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969639"
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2013-r2-and-2013"></a>安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013
安裝[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]隨附[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]，或隨附[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]2013年。

 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：  

- .NET 應用程式  

- Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  

  根據您如何使用介面卡，所需的軟體而異。  

<a name="BKMK_Prereqs_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a>使用.NET 應用程式中的配接器時的必要條件  
您要在其中撰寫取用的.NET 應用程式的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 所列，請在順序中安裝軟體。  


|                                 2013 R2                                 |                                  2013                                   |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
|          [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]          |      Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]      |
|                           Visual Studio 2013                            |                           Visual Studio 2012                            |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] |
|                   SQL Server 用戶端程式庫。 執行個體時提供 SQL Server 登入。                    |                    SQL Server 用戶端程式庫...                    |

<a name="BKMK_Prereqs_BTS"></a>    
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a>使用 BizTalk Server 中的配接器時的必要條件  
會使用您的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 我們建議您安裝軟體的相同順序，如此處所列。  


|                                                                                                                                                                                                                                                               2013 R2                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                2013                                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                                                                        [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                    Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]                                                                                                                                                                                                                                    |
|                                                                                                                                                                                                                                                         Visual Studio 2013                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                         Visual Studio 2012                                                                                                                                                                                                                                                          |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]for[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> 安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]for[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 |
|                                                                                                                                                                                                                                                       BizTalk Server 2013 R2                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                         BizTalk Server 2013                                                                                                                                                                                                                                                         |
|                                                                                                                                                                                                                                                  SQL Server 用戶端程式庫。                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                  SQL Server 用戶端程式庫。                                                                                                                                                                                                                                                   |

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a>支援的 SQL Server 版本和用戶端程式庫  
 下列章節提供支援的 SQL Server 版本和用戶端所需的程式庫[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

- **支援的伺服器版本**: SQL Server 2005，SQL Server 2008 SP1 中，SQL Server 2008 R2，SQL Server 2012  

- **支援的用戶端版本**: Microsoft[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]連接到 SQL Server 所需的用戶端 Dll 的套件組合。 您不需要明確地在您的電腦上安裝任何用戶端 Dll。  

- **必要驅動程式**:  

  - 如果您使用的 Udt 隨附的 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。 例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業時，這些 Dll 必須存在於執行 BizTalk Server 的電腦上。  

    - 請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。  

    - 請確定 SqlServerSpatial.dll 位於 System32 資料夾中。  

      您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，然後選取**管理工具-基本**並**管理工具-完整**在**特徵選取**精靈頁面。  

  - 如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定您已安裝的 SQL 用戶端連接性 SDK。 您可以安裝 SQL 用戶端連接性 SDK，以執行 SQL Server 安裝程式，然後選取**SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器會使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  

  - 如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。  

<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a>64 位元支援 

[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以在 32 位元或 64 位元的主控件執行個體中執行。

 如需有關支援的安裝案例，32 位元和 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 

<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a>安裝 SQL 配接器  
 請確定您已安裝，才能安裝的必要條件[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

 您可以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：  

- **在互動模式中**使用安裝精靈  

- **以無訊息模式**命令中使用 msiexec 連結  

  > [!IMPORTANT]
  >  您必須安裝在電腦上擁有系統管理權限[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，不論您要安裝使用精靈或命令列。  

<a name="BKMK_Install_Scenarios"></a>   
### <a name="32-bit-and-64-bit-install-scenarios"></a>32 位元和 64 位元安裝案例
 具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：  

- [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 設計階段 （當產生作業的中繼資料）。  

- BizTalk Server 管理主控台 （用於建立實體連接埠） 的設計階段。  

  > [!NOTE]
  >  BizTalk Server 管理主控台會以 32 位元的 Microsoft Management Console (MMC) 應用程式執行。  

- BizTalk 執行階段 （當傳送和接收來自 LOB 應用程式的訊息）。  

  您可以安裝在同一部電腦或不同的電腦執行所有這些工作地方。 因為這兩[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 和 32 位元處理序，您必須安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您要執行設計階段工作的電腦上。 安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元和 64 位元平台上。  

#### <a name="install-scenarios-on-a-32-bit-platform"></a>在 32 位元平台上安裝案例  
 安裝時支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元平台上。  


|                                                                                                               Visual Studio 設計階段                                                                                                                |                                                                                                                BizTalk MMC 設計階段                                                                                                                 |                                                                                                                    BizTalk 執行階段                                                                                                                    |                                                                                      Visual Studio 設計階段及/或 BizTalk MMC 設計階段 + BizTalk 執行階段                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 | -安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 | -安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 | -安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 |

#### <a name="install-scenarios-on-a-64-bit-platform"></a>在 64 位元平台上安裝案例  
 安裝時支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]64 位元平台上。  

> [!NOTE]
>  在您要執行設計階段工作使用的任何電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

|                                                                                                               Visual Studio 設計階段                                                                                                                |                                                                                                                BizTalk MMC 設計階段                                                                                                                 |                                                                                                                                                                                                                                                                                                   BizTalk 執行階段                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                    Visual Studio 設計階段及/或 BizTalk MMC 設計階段 + BizTalk 執行階段                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 | 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 | **32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 64 位元用戶端和其他必要的 Dll。 | **32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 64 位元用戶端和其他必要的 Dll。<br /><br /> -安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。<br /><br /> -安裝 32 位元用戶端和其他必要的 Dll。 |

<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-sql-adapter-in-interactive-mode"></a>在互動模式中安裝 SQL 配接器  

1. 執行安裝程式。  

   > [!NOTE]
   >  如果您要安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]虛擬機器上，安裝精靈可能會繼續進行對話方塊，通知的安裝程式正在檢查可用磁碟空間。 在此情況下，我們建議您使用無訊息安裝選項。   

2. 閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。  

3. 閱讀並接受使用者授權合約 (EULA)，然後再按一下**下一步**。  

4. 在 **目的地資料夾**對話方塊方塊中，指定您要安裝的位置[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，按一下**下一步]**，然後按一下 **安裝**。  

5. 在 **客戶經驗改進計畫**對話方塊方塊中，指定您想要註冊的客戶經驗改進計畫 (CEIP)。 一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您會將分享 Microsoft 中的下列資料：  

   - 您安裝所在的電腦硬體的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

   - 您用來連接使用的 SQL Server 版本的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

     指定您選擇，然後按一下**確定**。  

   > [!NOTE]
   >  您可以隨時變更您的喜好設定有關在修復模式下執行安裝程式，從 控制台註冊 ceip。  

6. 按一下 **[完成]**。  

<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a>以無訊息模式安裝 SQL 配接器  
 下列程序示範如何執行無訊息安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用`msiexec`命令。  

1. 開啟命令提示字元並瀏覽至您已安裝程式的資料夾。  

2. 執行下列命令以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  

   > [!NOTE]
   >  若要執行無訊息安裝在 x64 架構的平台，在下列命令中，取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn  
   ```  

    您也可以選擇加入 ceip 的無訊息安裝的一部分。 一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您會將分享 Microsoft 中的下列資料：  

   - 您安裝所在的電腦硬體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

   - 您用來連接使用的 SQL Server 版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

     若要註冊 ceip，執行下列命令：  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
   ```  

    根據預設，此選項為 false。  

    如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。  

<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a>後續安裝工作  

<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a>註冊繫結  
完成這些步驟*只*如果 machine.config 檔案中註冊的配接器繫結失敗的安裝精靈。  

1. 瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  

   - Microsoft.NET framework 3.5 SP1 \<*版本*\>是.NET framework 版本 v2.0.50727。  

   - Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。  

2. 開啟使用文字編輯器的檔案。  

3. 若要註冊配接器繫結：  

   1. 搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. 搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。  

   3. 新增"bindingElementExtensions 」 節點的下一節。  

       針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. 搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。  

   5. 新增"bindingExtensions 」 節點的下一節。  

       針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  



4. 關閉並儲存 machine.config 檔。  

<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a>判斷的公開金鑰和版本  
完成下列步驟來判斷的公開金鑰和版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

1. 瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。  

2. 以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。 下表列出的 Dll 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  


   |                              配接器                              |      DLL 的名稱       |
   |-------------------------------------------------------------------|----------------------------|
   | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] | Microsoft.Adapters.Sql.dll |


3. 在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。 同樣地，根據的值才**版本**標籤都會指定 dll 的版本號碼。  

4. 複製公開金鑰，然後再按**取消**。  

<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a>更新或變更 SQL 配接器安裝  
 執行下列步驟，以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。 請確定您已[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝在執行安裝精靈來修改之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。  

 您可以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式安裝：  

-   **在互動模式中**執行安裝程式精靈。  

-   **以無訊息模式**使用命令列。  

#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a>更新 SQL 配接器安裝在互動模式中  

1.  按一下 **開始**，然後按一下**控制台**。  

2.  在控制台中，按兩下**程式和功能**。  

3.  在 **程式和功能**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下**變更**。  

4.  閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。  

5.  在 [**變更、 修復或移除安裝**] 對話方塊中，按一下**修復**。  

6.  在 [**準備好修復 Microsoft BizTalk Adapter for SQL Server** ] 對話方塊中，按一下**修復**。  

7.  如有需要，變更您的喜好設定有關選擇加入 ceip，，然後按一下 **確定**。  

8.  按一下 **[完成]**。  

#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a>SQL 配接器安裝，以無訊息模式更新  

1. 開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。  

2. 執行下列命令：  

   > [!NOTE]
   >  若要修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式的 x64 型的平台，在下列命令中，在安裝取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn /f  
   ```  

   > [!IMPORTANT]
   >  同時修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇參與或退出 CEIP。 喜好設定會維持不變您指定在安裝時，即使您明確地設定 CEIP_OPTIN 為 true 或 false。  

    如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。   

<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a>解除安裝或移除 SQL 配接器  
 執行下列步驟來移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從您的電腦。 請確定您已[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝在執行安裝精靈來移除之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

 您可以移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：  

-   **在互動模式中**執行安裝程式精靈。  

-   **以無訊息模式**使用命令列。  

#### <a name="uninstall-in-interactive-mode"></a>在互動模式中解除安裝  

1.  按一下 **開始**，然後按一下**控制台**。  

2.  在控制台中，按兩下**程式和功能**。  

3.  在 **新增或移除程式**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下**移除**。  

4.  在對話方塊中，按一下**是**。  

#### <a name="uninstall-in-silent-mode"></a>解除安裝以無訊息模式  

1. 開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。  

2. 執行下列命令：  

   > [!NOTE]
   >  若要移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在無訊息模式的 x64 型的平台，在下列命令中，取代 SqlAdapterSetup.msi SqlAdapterSetup64.msi。  

   ```  
   msiexec /x SqlAdapterSetup.msi /qn  
   ```  

    此命令會移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從電腦。  

    如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。  

<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a>解除安裝後工作  
 如果[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式無法移除配接器繫結同時移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須手動移除它們。 下節描述如何手動移除的繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

<a name="BKMK_Remove_Binding"></a>   
#### <a name="manually-remove-the-bindings"></a>以手動方式移除繫結  
 執行這些步驟*只*如果安裝精靈 無法移除 machine.config 檔案中的配接器繫結。  

1. 瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  

   - Microsoft.NET framework 3.5 SP1 \<*版本*\>是.NET framework 版本 v2.0.50727。  

   - Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。  

2. 開啟使用文字編輯器的檔案。  

3. 若要移除介面卡繫結註冊：  

   1. 搜尋 [system.serviceModel] 的項目，並移除下列項目底下：  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  

      ```  

   2. 搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。  

   3. 移除 「 bindingElementExtensions 」 節點的下一節。  

       針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. 搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。  

   5. 移除 「 bindingExtensions 」 節點的下一節。  

       針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

4. 關閉並儲存 machine.config 檔。  

## <a name="see-also"></a>另請參閱
[安裝 SQL 配接器](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)