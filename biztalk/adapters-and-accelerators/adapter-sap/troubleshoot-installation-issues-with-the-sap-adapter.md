---
title: "SAP 配接器疑難排解安裝問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, installation
- installation, troubleshooting
ms.assetid: fdfdaf44-c32d-43a5-998d-02032c0b9211
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf06cc866249e929c9ddf368f4594af58af1d6fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-installation-issues-with-the-sap-adapter"></a>SAP 配接器疑難排解安裝問題
安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。 本章節將討論解決安裝錯誤的疑難排解技術。  
  
## <a name="logging-messages-for-setup-actions"></a>安裝程式動作的記錄訊息  
 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。 您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。  
  
-   [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。 因此，安裝程式的記錄是標準的 MSI 記錄。  
  
-   安裝程式會執行自訂動作的記錄檔位於 %temp%\adaptersetup.log。 如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。  
  
##  <a name="BKMK_SAPSetupBinding"></a>安裝程式無法註冊配接器繫結或資料提供者  
 **問題**  
  
 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊配接器繫結或[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，但會繼續進行配接器安裝。  
  
 **可能的原因**  
  
 這可能會因為發生問題造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。 配接器繫結會寫入至 machine.config 檔。  
  
 **解決方式**  
  
 您應該手動註冊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結或[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
### <a name="register-the-adapter-bindings-or-the-data-provider"></a>註冊配接器繫結或資料提供者  
  
1.  瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機 >: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
     在此路徑中\<版本 > 是.NET Framework 的版本。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  若要註冊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結：  
  
    1.  搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        </client>  
        ```  
  
    2.  搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。  
  
    3.  尋找遺漏[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結。 新增下列區段，"bindingElementExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，加入：  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。  
  
    5.  尋找遺漏[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結。 新增下列區段，"bindingExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，加入：  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  如需如何判斷公開金鑰資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。  
  
4.  若要註冊[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  
  
    1.  搜尋如"system.data 」 節點下的項目 」 DbProviderFactories"。  
  
    2.  尋找遺漏[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。 新增下列區段，"DbProviderFactories 」 節點下。  
  
         如[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，加入：  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient" description=".NET Framework Data Provider for mySAP Business Suite" type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  關閉並儲存 machine.config 檔。  
  
###  <a name="BKMK_PubKey"></a>判斷公開金鑰和版本  
 執行下列步驟來判斷公開金鑰[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]或[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
1.  瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。  
  
2.  以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。 下表列出的 Dll 名稱[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
    |配接器/資料提供者|DLL 的名稱|  
    |----------------------------|---------------------|  
    |[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]|Microsoft.Adapters.SAP|  
    |[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]|Microsoft.Data.SAPClient|  
  
3.  在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。 同樣地，針對值**版本**標籤指定 dll 的版本號碼。  
  
4.  複製的公開金鑰，然後按一下**取消**。  
  
##  <a name="BKMK_SAPConsumeBinding"></a>任何有效的配接器不的安裝的錯誤

 **問題**  
  
 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：  
  
```  
No valid adapters are installed on this machine  
```  
  
 **可能的原因**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。 因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。 不過，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查 machine.config 檔案的 32 位元版本中的繫結和失敗時提供錯誤。  
  
 **解決方式**  
  
-   同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  
  
    > [!IMPORTANT]
    >  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  
  
-   加入兩個 32 位元和 64 位元版本的用戶端 Dll [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] （例如 librfc32u.dll) 至 PATH 變數。 32 位元版本的 dll 必須加入至 C:\Windows\SysWow64 資料夾中。 64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾。  
  
    > [!IMPORTANT]
    >  如果配接器 （32 或 64 位元） 有 64 位元的作業系統，在電腦上執行，而且您用來撰寫應用程式配接器，您應該將標示要與相同類型 （32 或 64 位元） 配接器的應用程式。 此外，RFC SDK （32 或 64 位元） 版本必須是相同的版本 （32 或 64 位元） 的介面卡。  
    >   
    >  例如，如果使用 64 位元作業系統的電腦上執行 32 位元的配接器，配接器用戶端應用程式必須標示為 32 位元。  
  
     如需有關 SAP 用戶端 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
##  <a name="BKMK_SAPInvalidBinding"></a>設定 SAP 配接器連接埠時發生的不正確的繫結錯誤  
 **問題**  
  
 當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sapBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 **可能的原因**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。 因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台執行以 32 位元處理序，因此當您設定配接器的連接埠，它會檢查 machine.config 檔案的 32 位元版本中的繫結而會失敗，提供錯誤。  
  
 **解決方式**  
  
-   同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  
  
    > [!IMPORTANT]
    >  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  
  
-   加入兩個 32 位元和 64 位元版本的用戶端 Dll [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] （例如 librfc32u.dll) 至 PATH 變數。 32 位元版本的 dll 必須加入至 C:\Windows\SysWow64 資料夾中。 64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾。  
  
    > [!IMPORTANT]
    >  如果配接器 （32 或 64 位元） 有 64 位元的作業系統，在電腦上執行，而且您用來撰寫應用程式配接器，您應該將標示要與相同類型 （32 或 64 位元） 配接器的應用程式。 此外，RFC SDK （32 或 64 位元） 版本必須是相同的版本 （32 或 64 位元） 的介面卡。  
    >   
    >  例如，如果使用 64 位元作業系統的電腦上執行 32 位元的配接器，配接器用戶端應用程式必須標示為 32 位元。  
  
     如需有關 SAP 用戶端 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。
  
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)