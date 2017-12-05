---
title: "SQl 配接器疑難排解安裝問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48778158-6064-4731-be72-1af855ebe373
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ba1d7e105a1ea09724950f4c0f8b778e45dad46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-sql-adapter"></a>SQl 配接器疑難排解安裝問題
> [!IMPORTANT]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可做為屬於[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]以及使用個別介面卡。 如果您要存取本主題來了解安裝問題的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，所有參考[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式必須解譯為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。  
  
 安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。 本節將討論使用來解決安裝錯誤的疑難排解技術。  
  
## <a name="logging-messages-for-setup-actions"></a>安裝程式動作的記錄訊息  
 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。 您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。  
  
-   [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝在使用 MSI 的配接器特定檔案。 因此，安裝程式的記錄是標準的 MSI 記錄。  
  
-   安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。 如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤，安裝時，可能會遇到[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]、 以及它們的可能原因和解決方式。  
  
  
  
###  <a name="BKMK_SQLSetupBinding"></a>安裝程式無法註冊配接器繫結  
 **問題**  
  
 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈無法註冊配接器繫結，但會繼續進行配接器安裝。  
  
 **可能的原因**  
  
 這可能會因為發生問題造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。 配接器繫結會寫入至 machine.config 檔。  
  
 **解決方式**  
  
 您應該手動註冊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。  
  
##### <a name="to-register-the-adapter-binding"></a>若要註冊的配接器繫結  
  
1.  瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  
  
     在此路徑中\<版本\>是.NET Framework 的版本。  
  
2.  使用文字編輯器開啟檔案。  
  
3.  若要註冊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結：  
  
    1.  搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。  
  
    3.  尋找遺漏[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。 新增下列區段，"bindingElementExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。  
  
    5.  尋找遺漏[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。 新增下列區段，"bindingExtensions 」 節點下。  
  
         如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  如需如何判斷公開金鑰和版本資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。  
  
4.  關閉並儲存 machine.config 檔。  
  
####  <a name="BKMK_PubKey"></a>判斷公開金鑰和版本  
 執行下列步驟來判斷公開金鑰[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
###### <a name="to-determine-the-public-key"></a>判斷公開金鑰  
  
1.  瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。  
  
2.  以滑鼠右鍵按一下您想要的公開金鑰和版本，然後選取 DLL**屬性**。 下表列出的 DLL 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    |配接器|DLL 的名稱|  
    |-------------|---------------------|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|Microsoft.Adapters.Sql|  
  
3.  在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。 同樣地，針對值**版本**標籤指定 dll 的版本號碼。  
  
4.  複製的公開金鑰，然後按一下**取消**。  
  
###  <a name="BKMK_SQLConsumeBinding"></a>使用 64 位元安裝上使用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤  
 **問題**  
  
 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：  
  
```  
No valid adapters are installed on this machine  
```  
  
 **可能的原因**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。 因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。 不過，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查 machine.config 檔案的 32 位元版本中的繫結和失敗時提供錯誤。  
  
 **解決方式**  
  
 同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  
  
> [!IMPORTANT]
>  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  
  
###  <a name="BKMK_SQLInvalidBinding"></a>無效的繫結時發生的 64 位元安裝上設定 BizTalk Server 管理主控台中的 SQL 配接器連接埠  
 **問題**  
  
 當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sqlBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 **可能的原因**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。 因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台執行以 32 位元處理序，因此當您設定配接器的連接埠，它會檢查 machine.config 檔案的 32 位元版本中的繫結而會失敗，提供錯誤。  
  
 **解決方式**  
  
 同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  
  
> [!IMPORTANT]
>  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  
  
## <a name="see-also"></a>請參閱  
 [SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)