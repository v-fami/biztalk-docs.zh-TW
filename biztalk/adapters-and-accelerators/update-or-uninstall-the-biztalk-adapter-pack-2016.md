---
title: "更新或解除安裝 BizTalk 配接器組件 2016年 |Microsoft 文件"
description: "使用安裝精靈 」 或 msiexec 變更或解除安裝 BizTalk Server; 隨附的 BAP 2016包括移除繫結和移除自訂 Rfc"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3d6c001-1005-4d7b-a143-eaa37b48f898
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51c30fa3b107113991a8b4893fa2626a53d67159
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="update-or-uninstall-the-biztalk-adapter-pack-2016"></a>更新或解除安裝 BizTalk 配接器組件 2016
如何變更或解除安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。

<a name="BKMK_Modify_Adap"></a>
## <a name="change-or-update-the-installation"></a>變更或更新安裝  
執行安裝精靈來修改之前[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝。 
  
 您可以修改的安裝以互動模式 （安裝精靈中），或以無訊息模式 （命令列）。
  
### <a name="use-the-setup-wizard"></a>使用安裝精靈  
  
1.  使用 BizTalk Server 系統管理員群組的成員帳戶登入。  
  
2.  在**程式和功能**，選取**解除安裝程式**。  
  
3.  以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**變更**。  
  
4.  在 歡迎使用畫面上，選取**下一步**。  
  
5.  在**變更、 修復或移除安裝**:  
  
    -   若要選取您想要安裝的元件，請選取**變更**並移至步驟 6。  
  
    -   若要修復最近安裝中的錯誤，請選取**修復**並移至步驟 7。  
  
    -   若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從電腦中，選取**移除**然後移至步驟 10。  
  
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
  
### <a name="use-msiexec-in-silent-mode"></a>在無訊息模式中使用 msiexec  
  
1.  開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。  
  
2.  執行類似下列的命令：  
  
    > [!NOTE]
    >  若要修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]x64 平台上，在下列命令，以無訊息模式安裝取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，並安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。  
  
     使用不同的值`REMOVE`和`ADDLOCAL`屬性，您可以新增或移除特定元件。 中的資料表是指**以無訊息模式安裝**在[安裝 BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)有關您可以使用這些屬性的值。  
  
     您也可以使用 /f 選項 msiexec 命令的一部分來執行無訊息的修復。 例如：  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     您可以使用各種不同的組合使用 /f 選項。 如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。 或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。  
  
    > [!IMPORTANT]
    >  修改時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇加入或退出 CEIP。 即使您明確地設定為 true 或 false CEIP_OPTIN 安裝會保持在您選擇喜好設定。  

## <a name="uninstall-or-remove-the-biztalk-adapter-pack"></a>解除安裝或移除 BizTalk Adapter Pack  
  
> [!IMPORTANT]
>  如果您使用的 tRFC 功能的 SQL Server 資料庫中建立資料表[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，您必須先解除安裝，手動移除這些[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝複製`SapAdapter-DbScript-Uninstall.sql`檔案通常位於*\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* 。 執行這個檔案來移除您所建立的資料表。  
  
完成下列步驟來移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從您的電腦。 請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝之前執行安裝精靈。  
  
 您可以移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以互動模式 （安裝程式精靈），或以無訊息模式 （命令列）。
  
### <a name="uninstall-using-the-setup-wizard"></a>使用安裝精靈解除安裝  
  
1.  在**程式和功能**，選取**解除安裝程式**。  
  
2.  以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**解除安裝**。  
  
### <a name="uninstall-in-silent-mode"></a>在無訊息模式中解除安裝  
  
1.  開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。  
  
2.  執行下列命令：  
  
    > [!NOTE]
    >  若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在 x64 平台上，下列命令，在無訊息模式取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。  
  
     藉由提供不同的值`REMOVE`屬性，您可以移除特定元件從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。 中的資料表是指**以無訊息模式安裝**在[安裝 BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)有關您可以使用這個屬性的值。  
  
     若要完全移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，執行下列命令：  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。 或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。
  
## <a name="remove-the-bindings"></a>移除繫結  
 完成這些步驟*只*如果安裝精靈無法移除 machine.config 檔中的配接器繫結或.NET Framework 資料提供者註冊。  
  
1.  移至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在*\<系統磁碟機 >: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG*。  
  
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
  
## <a name="remove-the-custom-rfcs"></a>移除自訂 Rfc  
完成此步驟，移除您安裝在 SAP 系統的自訂 Rfc。 請參閱[安裝或移除自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
