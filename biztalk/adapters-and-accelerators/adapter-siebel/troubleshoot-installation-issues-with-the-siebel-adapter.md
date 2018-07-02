---
title: 使用 Siebel 配接器疑難排解安裝問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, installation
- installation, troubleshooting
ms.assetid: f9f066d9-37b6-4a18-9f60-d0931ea91a18
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed3fab4973950b70a49efc90e1bc947561e602c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983495"
---
# <a name="troubleshoot-installation-issues-with-the-siebel-adapter"></a>使用 Siebel 配接器疑難排解安裝問題
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上安裝，並註冊每個配接器的繫結。 本章節將討論解決安裝錯誤的疑難排解技巧。  

## <a name="setup-logging"></a>安裝程式記錄  
 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。 您可以記錄這兩個標準，以及自訂動作執行安裝程式的訊息。  

- [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。 因此，安裝程式的記錄會為標準的 MSI 記錄。  

- 安裝程式所執行的自訂動作的記錄檔位於 %temp%\adaptersetup.log。 如果記錄檔追蹤失敗，追蹤也有事件記錄檔中。  

## <a name="known-issues"></a>已知問題  

### <a name="setup-fails-to-register-adapter-bindings"></a>安裝程式無法註冊配接器繫結  
 **問題**  

 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，但會繼續進行配接器安裝。  

 **原因**  

 因為 WCF 安裝問題，這可能會造成[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config。 配接器繫結會寫入至 machine.config 檔案中。  

 **解決方式**  

手動註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結和[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用下列步驟： 

1. 瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  

    在此路徑中，\<版本\>是.NET Framework 的版本。  

2. 開啟使用文字編輯器的檔案。  

3. 若要註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結：  

   1. 搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：  

      ```  
      <client>  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
      </client>  
      ```  

   2. 搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。  

   3. 尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。 新增"bindingElementExtensions 」 節點的下一節。  

       針對[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：  

      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. 搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。  

   5. 尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。 新增下列各節的 「 bindingExtensions 」 節點下。  

       針對[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：  

      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

      > [!NOTE]
      >  如需如何判斷公開金鑰的資訊，請參閱[判斷的公開金鑰和版本](#BKMK_PubKey)。  

4. 若要註冊[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:  

   1. 搜尋項目 DbProviderFactories system.data 節點下。  

   2. 尋找遺漏[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。 新增下列區段的 DbProviderFactories 節點下。  

       針對[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，加入：  

      ```  
      <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
          description=".NET Framework Data Provider for Siebel eBusiness Applications"  
          type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

5. 關閉並儲存 machine.config 檔。  

####  <a name="BKMK_PubKey"></a> 判斷的公開金鑰和版本  
 執行下列步驟來判斷的公開金鑰[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。  

###### <a name="to-determine-the-public-key"></a>若要判斷公開金鑰  

1. 瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。  

2. 以滑鼠右鍵按一下要為其公用金鑰，然後選取的 DLL**屬性**。 下表列出每個配接器和提供者 Dll 的名稱。  


   |                              配接器/ADO 提供者                               |       DLL 的名稱       |
   |---------------------------------------------------------------------------------|-----------------------------|
   |    [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]    |  Microsoft.Adapters.Siebel  |
   | [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] | Microsoft.Data.SiebelClient |


3. 在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。 同樣地，針對值**版本**標籤都會指定 dll 的版本號碼。  

4. 複製公開金鑰，然後再按**取消**。  

## <a name="see-also"></a>另請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)