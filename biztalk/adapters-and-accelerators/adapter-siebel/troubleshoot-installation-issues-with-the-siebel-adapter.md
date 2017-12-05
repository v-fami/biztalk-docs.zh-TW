---
title: "使用 Siebel 配接器疑難排解安裝問題 |Microsoft 文件"
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
ms.assetid: f9f066d9-37b6-4a18-9f60-d0931ea91a18
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff49285df7e43103f2ad7441cbc82b96bb59eaa4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-siebel-adapter"></a>使用 Siebel 配接器疑難排解安裝問題
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上安裝，並註冊每個配接器的繫結。 本章節將討論解決安裝錯誤的疑難排解技術。  
  
## <a name="setup-logging"></a>安裝程式記錄  
 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。 您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。  
  
-   [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。 因此，安裝程式的記錄將會是標準的 MSI 記錄。  
  
-   安裝程式所執行的自訂動作的記錄檔位於 %temp%\adaptersetup.log。 如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。  
  
## <a name="known-issues"></a>已知問題  
  
### <a name="setup-fails-to-register-adapter-bindings"></a>安裝程式無法註冊配接器繫結  
 **問題**  
  
 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，但會繼續進行配接器安裝。  
  
 **可能的原因**  
  
 這可能會造成與 WCF 安裝問題[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config。 配接器繫結會寫入至 machine.config 檔。  
  
 **解決方式**  
  
手動註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結和[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用下列步驟： 
  
1.  瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
     在此路徑中\<版本\>是.NET Framework 的版本。  
  
2.  開啟檔案，使用文字編輯器。  
  
3.  若要註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結：  
  
    1.  搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：  
  
        ```  
        <client>  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        </client>  
        ```  
  
    2.  搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。  
  
    3.  尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。 新增下列區段，"bindingElementExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。  
  
    5.  尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。 新增下列各節的 「 bindingExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  如需如何判斷公開金鑰資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。  
  
4.  若要註冊[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:  
  
    1.  搜尋項目 DbProviderFactories system.data 節點下。  
  
    2.  尋找遺漏[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。 新增下列區段，DbProviderFactories 節點下。  
  
         如[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，加入：  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  關閉並儲存 machine.config 檔。  
  
####  <a name="BKMK_PubKey"></a>判斷公開金鑰和版本  
 執行下列步驟來判斷公開金鑰[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。  
  
###### <a name="to-determine-the-public-key"></a>判斷公開金鑰  
  
1.  瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。  
  
2.  以滑鼠右鍵按一下您想公開索引鍵，然後選取 DLL**屬性**。 下表列出每個配接器和提供者 Dll 的名稱。  
  
    |配接器/ADO 提供者|DLL 的名稱|  
    |---------------------------|---------------------|  
    |[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]|Microsoft.Adapters.Siebel|  
    |[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]|Microsoft.Data.SiebelClient|  
  
3.  在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。 同樣地，針對值**版本**標籤指定 dll 的版本號碼。  
  
4.  複製的公開金鑰，然後按一下**取消**。  
  
## <a name="see-also"></a>請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)