---
title: "BizTalk 配接器組件 2016 後安裝步驟 |Microsoft 文件"
description: "步驟完成之後安裝 BAP 2016，包括新增配接器至 BizTalk 管理、 Oracle、 更新和註冊配接器繫結。"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8946bfe-92bb-470d-bec4-9bc3a07ce0d2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17bd0a76cacb35563448f31f79c2275c79b92ab8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="post-installation-steps-for-biztalk-adapter-pack-2016"></a>BizTalk 配接器組件 2016 後安裝步驟
安裝之後[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，一些安裝後步驟。 本主題列出這些步驟。   

## <a name="add-the-adapter-to-biztalk-administration"></a>新增配接器至 BizTalk 管理
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  展開**BizTalk 群組**，依序展開**平台設定**，然後選取**配接器**。  
  
3.  以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。  
  
     ![新增配接器](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  在**配接器屬性**，從下拉式清單中，選取配接器，例如**WCF SAP**，然後輸入名稱，例如**WCF SAP**。  
  
     ![新增 SAP 配接器至 BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")  
  
5.  選取 [確定]。  

## <a name="use-a-newer-oracledataaccessdll-version"></a>使用較新版的 Oracle.DataAccess.dll  

當您設定要使用 Wcf-oracledb 配接器，或使用 Visual Studio 使用產生的配接器的連接埠時，會顯示訊息，配接器需要 Oracle.DataAccess.dll 2.111.7.0 版本。 若要解決此訊息，請安裝支援的 Oracle.DataAccess.dll 版本 (請參閱[支援版本清單](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))，然後更新`bindingRedirect`OracleDB 組態檔，請使用下列步驟中的項目：  
  
1.  在 BizTalk 伺服器上，請移至下列資料夾：  
  
     *磁碟機*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin  
  
     *磁碟機*: \Program 檔案 (x86) \Microsoft BizTalk Adapter Pack\bin  
  
2.  開啟 Microsoft.Adapters.OracleDB.config 檔案。  
  
3.  尋找下列區段，，然後再複製/貼上下列：  
  
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
> - 如果此群組中有多個 BizTalk 伺服器，請在群組中的所有 BizTalk 伺服器上進行這項變更。  
> - *NewVersion*值需要更新 Oracle.DataAccess.dll 檔案的電腦上安裝的版本為基礎。  Oracle.DataAccess.dll 隨附於您從 Oracle 安裝 Oracle 用戶端。  您只必須安裝 Oracle 用戶端版本， [BizTalk 配接器組件支援](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)。  
  
## <a name="create-sql-server-database-objects-sap-adapter-only"></a>建立 SQL Server 資料庫物件 （只 SAP 配接器）  
 若要啟動 tRFCs SAP 系統中，執行*SapAdapter-DbScript-Install.sql* SQL 指令碼。 此指令碼會隨[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，並在 SQL Server 中建立資料庫物件。 指令碼通常會安裝在*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* 。 只要您輸入該資料庫名稱來叫用 tRFCs 使用配接器時，您可以針對任何 SQL Server 資料庫，執行此指令碼。
  
## <a name="register-the-adapter-bindings"></a>註冊配接器繫結
期間[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，安裝精靈可能無法註冊配接器繫結或.NET Framework Data Provider for mySAP Business Suite。 然後配接器安裝進行安裝。 這可能因 Windows Communication Foundation (WCF) 安裝，[!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。  

> [!IMPORTANT]
> 完成下列步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結或.NET Framework 資料提供者。  
  
1.  移至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在*\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG*。  
  
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
    >  若要取得的公開金鑰值，請參閱**判斷公開金鑰和版本**（在本主題中）。  
  
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
  
## <a name="determine-the-public-key-and-version"></a>判斷公開金鑰和版本  
 完成下列步驟來判斷公開金鑰和配接器或.NET Framework Data Provider 的版本。  
  
1.  請移至 Windows 目錄中，通常*C:\WINDOWS\assembly*。  
  
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
  
## <a name="install-the-custom-rfcs"></a>安裝自訂的 Rfc  
只有需要*如果*您想要使用[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。 請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)中[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]文件。 
  
> [!IMPORTANT]
>  如果您使用較早版本所提供的自訂 Rfc 的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，則您必須將它們升級為此版本提供的 Rfc。 移除早 Rfc，並再安裝此版本所隨附的 Rfc 這麼做。  

## <a name="install-the-enterprise-applications"></a>安裝企業應用程式  
這些步驟與安裝不同的企業部署 LOB 系統的指引，我們建議您針對使用企業系統所提供的安裝指南。 如果有的話，也參照特定的組態變更，及其配接器文件。   

## <a name="installation-and-post-installation-checklist"></a>安裝及安裝後的檢查清單  
  
-   請確定您已安裝所有[軟體必要條件](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)使用正確的安裝選項。
  
-   請確定您已安裝在電腦上安裝企業 LOB 應用程式的支援的版本[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 請參閱[支援的特定業務 (LOB) 系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)。  
  
-   若要安裝的企業 LOB 系統，您想要連接的介面卡，請確定您已安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**自訂**安裝選項。 請確定您未使用**完成**安裝選項。 請參閱[安裝 BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)。  
  
-   如果您想要進行 tRFC 呼叫 SAP 系統使用[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，請確定您在 SQL Server 資料庫中建立必要的資料表。 請參閱**建立 SQL Server 資料庫物件**（在本主題中）。
  
-   執行時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝精靈中，您可能會收到錯誤訊息，表示安裝程式無法註冊繫結。 如果是的話，手動註冊它們。 請參閱**註冊配接器繫結**（在本主題中）。  
  
-   如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]一部分[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定您已安裝自訂 Rfc SAP 系統上。 請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。

## <a name="more-good-info"></a>良好的詳細資訊
[變更或移除 BizTalk Adapter Pack](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)  
[BizTalk Adapter Pack 常見問題集](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)