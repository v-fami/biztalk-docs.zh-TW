---
title: 使用 Oracle E-business Suite 配接器疑難排解安裝問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09b3af20-ab87-44e8-8ded-c19432552be7
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fb1d5f0e1f17870c9824b30e5da55a2740cb81b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968127"
---
# <a name="troubleshoot-installation-issues-with-the-oracle-e-business-suite-adapter"></a>使用 Oracle E-business Suite 配接器疑難排解安裝問題
安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。 本節將討論使用來解決安裝錯誤的疑難排解技巧。  

## <a name="logging-messages-for-setup-actions"></a>安裝動作的記錄訊息  
 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。 您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。  

- [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。 因此，安裝程式記錄是標準的 MSI 記錄。 [Windows Installer 記錄](https://msdn.microsoft.com/library/windows/desktop/aa372847.aspx)提供更多詳細資料。 

- 安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。 如果記錄檔追蹤失敗，追蹤也有事件記錄檔中。  

## <a name="known-issues"></a>已知問題  
 以下是您在安裝時可能會遇到最常見的錯誤[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，以及其可能的原因和解決方式。  



###  <a name="BKMK_OraAppBinding"></a> 安裝程式無法註冊配接器繫結  
 **問題**  

 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊配接器繫結，但會繼續進行配接器安裝。  

 **原因**  

 因為有問題，這可能會造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝，[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。 配接器繫結會寫入至 machine.config 檔案中。  

 **解決方式**  

 您應該手動註冊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。  

##### <a name="to-register-the-adapter-binding"></a>若要註冊的配接器繫結  

1. 瀏覽至電腦上的 machine.config 檔案。 例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  

    在此路徑中， \<*版本*\>是.NET Framework 的版本。  

2. 使用文字編輯器中開啟檔案。  

3. 若要註冊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結：  

   1. 搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：  

      ```  
      <client>  
        <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleebs" />  
      </client>  
      ```  

   2. 搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。  

   3. 尋找遺漏[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。 新增"bindingElementExtensions 」 節點的下一節。  

       針對[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，加入：  

      ```  
      <add name="oracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. 搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。  

   5. 尋找遺漏[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。 新增"bindingExtensions 」 節點的下一節。  

       針對[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，加入：  

      ```  
      <add name="oracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   > [!NOTE]
   >  如需如何判斷公開金鑰和版本資訊，請參閱[判斷的公開金鑰和版本](#BKMK_PubKey)。  

4. 關閉並儲存 machine.config 檔。  

####  <a name="BKMK_PubKey"></a> 判斷的公開金鑰和版本  
 執行下列步驟來判斷公開金鑰[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  

###### <a name="to-determine-the-public-key"></a>若要判斷公開金鑰  

1. 瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。  

2. 以滑鼠右鍵按一下，想要的公開金鑰和版本，並選取您的 DLL**屬性**。 下表列出的 DLL 名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  


   |                                         配接器                                         |       DLL 的名稱        |
   |-----------------------------------------------------------------------------------------|------------------------------|
   | [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] | Microsoft.Adapters.OracleEBS |


3. 在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。 同樣地，針對值**版本**標籤都會指定 dll 的版本號碼。  

4. 複製公開金鑰，然後再按**取消**。  

###  <a name="BKMK_ConsumeOraApp"></a> 使用 64 位元安裝上的 取用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤  
 **問題**  

 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：  

```  
No valid adapters are installed on this machine  
```  

 **原因**  

 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。 所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。 不過， [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查是否有 32 位元版本的 machine.config 檔案中的繫結和失敗時提供錯誤。  

 **解決方式**  

- 同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  

  > [!IMPORTANT]
  >  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  

- 安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。  

  > [!NOTE]
  >  若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。 詳細資訊，請參閱 「 Oracle 資料提供者的.NET 常見問題集 」，網址[ http://go.microsoft.com/fwlink/p/?LinkId=92834 ](http://go.microsoft.com/fwlink/p/?LinkId=92834)。  

###  <a name="BKMK_OraAppInvalidBinding"></a> 在 BizTalk Server 管理主控台中設定 Oracle E-business Suite 配接器連接埠，在 64 位元安裝上時無效的繫結錯誤  
 **問題**  

 當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleEBSBinding".  
Verify the binding extension is registered in machine.config."  
```  

 **原因**  

 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。 64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。 所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中執行做為 32 位元處理序，並因此當您設定配接器的連接埠時，它會檢查 machine.config 檔案的 32 位元版本中的繫結並失敗時提供錯誤。  

 **解決方式**  

- 同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。  

  > [!IMPORTANT]
  >  您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。  

- 安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。  

  > [!NOTE]
  >  若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。 詳細資訊，請參閱 「 Oracle 資料提供者的.NET 常見問題集 」，網址[ http://go.microsoft.com/fwlink/p/?LinkId=92834 ](http://go.microsoft.com/fwlink/p/?LinkId=92834)。  

## <a name="see-also"></a>另請參閱  
[Oracle EBS 配接器疑難排解](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)