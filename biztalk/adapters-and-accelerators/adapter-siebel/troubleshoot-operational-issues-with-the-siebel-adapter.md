---
title: Siebel 配接器在 BizTalk 中的疑難排解操作問題 |Microsoft Docs
description: 常見的問題和 Siebel 配接器在 BizTalk 配接器組件 (BAP) 中的解決方式
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74d152d9-9893-4f93-894a-350bae8be7bd
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d17e325465ce5aa575a6d499aa6b8bf73e07696
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978935"
---
# <a name="troubleshoot-operational-issues-with-the-siebel-adapter"></a>使用 Siebel 配接器疑難排解操作問題
本節提供使用時，可能會遇到操作問題的相關資訊的集中式的位置[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 如需有關追蹤中的支援資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 診斷追蹤和訊息記錄 Siebel 配接器的](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是一些問題和建議的解決方案可能會遇到同時使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
  
###  <a name="BKMK_SiebelBindingError"></a> 載入配接器繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，GUI 會產生下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **原因**  
  
 當您啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結均依存於特定企業應用程式用戶端軟體。 因此，您可能需要面臨此問題的一個或兩個原因如下：  
  
- 在您安裝配接器的電腦上未安裝必要的 LOB 用戶端軟體。  
  
- 未安裝中的所有介面卡的配接器的 「 一般 」 或 「 完成 」 安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
  **解決方式**  
  
- 請確定您已安裝在電腦上安裝必要的用戶端版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
- 請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。  
  
###  <a name="BKMK_SiebelDispAdap"></a> Siebel 配接器不會顯示在清單中，BizTalk Server 管理主控台中的配接器  
 **問題**  
  
 與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]的隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未顯示在 BizTalk Server 管理主控台中的配接器清單中。  
  
 **原因**  
  
 最新[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_SiebelConnecting"></a> 連接至 Siebel 系統時發生錯誤  
 **問題**  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]當您嘗試連接至 Siebel 系統時，會產生下列錯誤：  
  
```  
Connecting to the system LOB has failed. Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154  
```  
  
 **原因**  
  
 Siebel Web 用戶端可能未安裝在電腦上。  
  
 **解決方式**  
  
 請確定電腦上安裝 Siebel Web 用戶端的支援的版本。 請參閱支援的用戶端的安裝指南和 siebel 伺服器版本。 安裝指南位於\<系統磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
###  <a name="BKMK_SiebelXMLRetrieve"></a> 具有多個 65536 的節點擷取 Xml 時發生錯誤  
 **問題**  
  
 配接器會提供擷取 XML 輸出具有多個 65536 的節點時發生下列錯誤。  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **原因**  
  
 配接器無法序列化和還原序列化的物件超過 65536 的項目。  
  
 **解決方式**  
  
 您可以修正此問題，藉由設定`maxItemsInObjectGraph`參數。 您可以將它設定在任何兩種：  
  
- 設定此參數，進而`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。  
  
- 將下列內容新增至您的應用程式的 app.config 檔。  
  
  ```  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="NewBehavior">  
        <dataContractSerializer maxItemsInObjectGraph="65536000" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  ```  
  
  範例 app.config 看起來像：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="siebelBinding"  
       contract="IOutboundContract" name="siebel_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_SiebelConnURI"></a> 在 BizTalk 中指定的 WCF 自訂連接埠的連線 URI 時發生錯誤  
 **問題**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 當您指定的連接來連接到 Siebel 系統的 URI 時，請提供下列的錯誤。  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 **原因**  
  
 連線 URI 不會遵守標準的編碼格式。 例如，參數的值可能會包含空格。  
  
 **解決方式**  
  
 請確定您指定的 URI 符合標準的編碼格式的連接。 例如，"%20"必須取代空格。  
  
###  <a name="BKMK_SiebelPerfOps"></a> Siebel 系統上執行作業時發生錯誤  
 **問題**  
  
 在執行任何作業在 Siebel 系統使用時，配接器會提供下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
- **BizTalk server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **原因**  
  
  未指定訊息的 WCF 動作。 WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。  
  
  **解決方式**  
  
  指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。 如需相關指示，請參閱 <<c0> [ 設定 Siebel 的 SOAP 動作](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md)。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)的每個作業的動作清單。  
  
###  <a name="BKMK_SiebelXmlParsing"></a> 因為不正確的作業名稱中指定的動作而 XmlReaderParsingException  
 **問題**  
  
 Siebel 系統傳送訊息時，BizTalk Server 管理主控台就會產生下列錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 **原因**  
  
 如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 上述的格式，作業名稱係由您選擇在產生結構描述時的作業。 比方說，如果您產生一個 Siebel 商務元件上的查詢作業的結構描述時，動作中的作業名稱會是 「 查詢 」。 不過，作業名稱的邏輯連接埠中建立 BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。  
  
 **解決方式**  
  
 請確定作業的名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 與 （在 BizTalk Server 管理主控台） 的實體連接埠相同。  
  
###  <a name="BKMK_SiebelTerminate"></a> 使用 Siebel 配接器的應用程式不會終止  
 **問題**  
  
 使用的應用程式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 7.5 版的用戶端不會終止。  
  
 **原因**  
  
 這是因為 Siebel 用戶端的問題程序無法從 Siebel 伺服器登出時終止。  
  
 **解決方式**  
  
 請確定您有安裝 Siebel 伺服器，以及快速檢修 QF0H05 7.5.3.17 的修補程式。  
  
###  <a name="BKMK_SiebelHang"></a> Siebel 配接器可能會停止回應，如果 Siebel 伺服器重新啟動  
 **問題**  
  
 如果 Siebel 伺服器重新啟動時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]正在傳送訊息到 Siebel 伺服器使用，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可能會停止回應。  
  
 **解決方式**  
  
 重新啟動 BizTalk 應用程式主控件執行個體。 若要這樣做從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在主控台樹狀目錄中展開**BizTalk 群組**，展開**平台設定**，然後按一下**主控件執行個體**。 從右窗格中，以滑鼠右鍵按一下 主機名稱，然後按**重新啟動**。  
  
###  <a name="BKMK_SiebelAction"></a> 配接器無法辨識的實體連接埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠  
 **問題**  
  
 使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生 Siebel 系統上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。 您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。 不過，當您將訊息傳送至 Siebel 系統使用這類連接埠時，配接器無法了解指定的連接埠上的動作，並提供類似下列的錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **原因**  
  
 當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠的作業，或您只使用預設名稱，例如 Operation_1、 Operation_2 等。不過，在所產生之繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是您要為其產生中繼資料作業的名稱相同。 比方說，如果您產生帳戶商務元件上的插入作業的中繼資料時，動作會設定如下：  
  
```  
<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
```  
  
 當您匯入繫結檔案時，實體連接埠上設定相同的動作。 因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符的實體連接埠，導致錯誤的動作中指定的作業名稱。  
  
 **解決方式**  
  
 請確定作業中的名稱的邏輯連接埠是與實體連接埠中的動作中指定的作業名稱相同。 執行下列其中之一：  
  
-   從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱，您可以為其產生中繼資料，例如 Insert 作業。  
  
-   將邏輯連接埠中的作業名稱的實體連接埠動作中的作業名稱。 例如，您可以變更如下所示的實體連接埠中的動作：  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
    ```  
  
###  <a name="BKMK_SiebelXMLEncode"></a> Siebel 配接器不會處理在名稱中的 XML 編碼字串的 Siebel 物件  
 **問題**  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]無法執行作業牽涉到的名稱中有編碼的 XML 字串的 Siebel 物件 （商務物件，商務元件、 商務服務、 挑選清單、 方法、 欄位、 引數，等等）。 比方說，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不能叫用商務服務方法名稱 Time_x0020_Stamp。  
  
 **解決方式**  
  
 請確定您的 Siebel 物件不包含其名稱中編碼的 XML 字串。  
  
###  <a name="BKMK_SiebelRootNode"></a> 在 BizTalk 專案中的根節點類型名稱錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。  
  
2.  針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_SiebelVS2008"></a> 在 Visual Studio 中使用配接器時，會產生無效的繫結警告。  
 **問題**  
  
 當 Visual Studio 中建立應用程式的情況下，您在使用配接器，並開啟 配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'siebelBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **原因**  
  
 會出現這個警告，因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結`siebelBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
## <a name="see-also"></a>另請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)