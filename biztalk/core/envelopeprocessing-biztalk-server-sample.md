---
title: "EnvelopeProcessing （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, envelopes
- flat files, processing
- examples, flat files
- examples, messages
- examples, envelopes
- envelopes, messages
- flat files, examples
- envelopes, examples
ms.assetid: b4cd979b-c7b4-446c-be29-c9f3169afa1f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c2f2cd505aca89bbe72221b3a895dd21945cb5e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="envelopeprocessing-biztalk-server-sample"></a>EnvelopeProcessing （BizTalk Server 範例）
EnvelopeProcessing 範例示範如何在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線中處理訊息和訊息信封。 它也會進一步示範如何將一般檔案訊息處理為 XML 訊息。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會將 EnvInput 資料夾設定為接收位置。 將檔案 (例如範例檔案 EnvelopeProcessing_in.txt) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列步驟處理此檔案中的訊息：  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從接收位置資料夾 EnvInput 擷取訊息檔案。  
  
2.  在接收管線中，「一般檔案解譯器」管線元件會移除一般檔案訊息的標頭與結尾，並將這些訊息剖析為個別訊息。  
  
3.  在 MessageBox 資料庫中，訊息會透過訂閱篩選器路由傳送至傳送埠。  
  
4.  在傳送埠的傳送管線中，「XML 組合器」管線元件會以 XML 信封包裝訊息，然後將信封放入傳送配接器資料夾 EnvOutput。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 此範例的設計必須顧及兩個基本需求：  
  
-   接收及處理包含一或多份採購訂單的一般檔案訊息。  
  
-   將包含一份採購訂單和傳送者資訊的一個 XML 訊息傳送至目錄，讓後端處理系統取用。  
  
 為了符合這些需求，會使用一般檔案/XML 結構描述的組合和自訂管線。 這些和其他設計元素總結於下表中。  
  
|設計元素|已選取的原因|  
|--------------------|--------------------------|  
|自訂接收管線|-使用一般檔案解譯器和一般檔案結構描述來轉譯內送的採購訂單訊息。|  
|訊息標頭、內文和結尾的一般檔案結構描述|-定義的所有相同記錄與欄位特性 （包含結構） 為 XML 結構描述，並提供一個機制來定義一般檔案特性，將一般檔案執行個體訊息轉譯成相等的 XML 執行個體所需的所有訊息 （反之亦然）。<br />標頭、 內文和結尾結構描述可用來將內文分割成不連續區塊來處理。|  
|信封結構描述|-用來從標頭資訊與個別訂單一併包裝。|  
|訂閱篩選器|-訂用帳戶篩選器會執行實際的路由擷取符合根據屬性欄位的一或多個準則的訊息。|  
|自訂傳送管線|-若要將執行個體訊息轉譯成 XML 格式，會使用 XML 組合器和信封和內文結構描述的組合。|  
  
 下列考量適用於這個範例的設計。  
  
-   一般檔案結構描述 (PO.xsd) 包含擴充註解，會說明採購訂單一般檔案的結構。 這些檔案可以用手動方式建立，但有不少可以透過 [一般檔案精靈] 產生。  
  
-   採購訂單 (PO.xsd) 一般檔案結構描述會使用值為 Unqualified 的 elementFormDefault 屬性。 雖然產生的結果正確無誤，但包含其他未預期的 xmlns 限定性條件。 使用值為 Qualified 的 elementFormDefault 即可避免這個問題。  
  
-   標頭和結尾一般檔案結構描述用來分隔訊息中的標頭和結尾資料。 「一般檔案解譯器」標頭、文件和結尾結構描述屬性已分別設定為標頭、採購訂單和結尾結構描述。  
  
-   XML 信封結構描述會結合標頭和訂單中的項目，產生一個 XML 訊息。 標頭結構描述升級來源欄位中的 SourceParty 欄位**BTS.bts_system_properties**命名空間; 信封結構描述會升級此相同的值，就會降級為傳出訊息。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 `<Samples Path>`\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|EnvelopeProcessing.btproj、EnvelopeProcessing.sln|這個範例的專案及解決方案檔案。|  
|EnvelopeProcessing_in.txt|範例輸入檔案。|  
|Header.xsd、PO.xsd、Trailer.xsd|一般檔案標頭、內文和結尾各自的結構描述。|  
|XmlEnvelope.xsd|輸出 XML 信封的結構描述。|  
|EnvReceivePipeline.btp、EnvSendPipeline.btp|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 分別使用「一般檔案解譯器」和「XML 組合器」管線元件來接收和傳送管線檔案。|  
|EnvelopeProcessingBinding.xml|用於自動化設定，例如連接埠繫結。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 您可以使用此範例，做為自己的一般檔案處理解決方案基礎。 您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。 部分範例如下：  
  
-   除了 XML 版本之外，加強範例來撰寫每個採購訂單的一般檔案版本。 您可以建立新的自訂傳送管線及使用「一般檔案組合器」來完成這項作業。 在「一般檔案組合器」上，指定一般檔案標頭、採購訂單和結尾結構描述。 在傳送埠中使用時，它會產生具有標頭/結尾資訊的個別採購訂單。  
  
-   以採購訂單中的更多資訊加強信封。 若要將其他資訊寫入至輸出訊息，請使用「快速升級」升級 "ship to" 名稱或其他欄位，將欄位加入信封，然後將信封欄位升級為相同欄位。 透過組合器處理訊息時，升級的屬性會降級並複製到輸出訊息中。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-envelopeprocessing-sample"></a>若要建置及初始化 EnvelopeProcessing 範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     *\<範例路徑\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為檔案夾內的這個範例建立輸入 (EnvInput) 和輸出 (EnvOutput) 檔案夾：  
  
         *\<範例路徑\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  
  
    -   為這個範例編譯和部署 Visual Studio 專案。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
         這個範例會在建立和繫結連接埠時顯示下列警告：  
  
        ```  
        Warning: Receive handler not specified for receive location "EnvelopeProcessing_RL"; updating with first receive handler with matching transport type.  
        Warning: Host not specified for orchestration "EnvelopeProcessing"; updating with first available host.  
        ```  
  
         您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
> [!NOTE]
>  如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
  
> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-envelopeprocessing-sample"></a>若要執行 EnvelopeProcessing 範例  
  
1.  將檔案 EnvelopeProcessing_in.txt 複製到資料夾 EnvInput。  
  
2.  觀察資料夾 EnvOutput 中建立的三個 .xml 檔案。 這些 .xml 檔案的名稱是根據它們的訊息識別碼 GUID 為基礎。 這些檔案包含從輸入檔擷取和信封中包裝的訊息。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：  
  
-   啟動傳送埠\StartSendPort.vbs  
  
-   啟用接收位置\EnableRecLoc  
  
-   移除傳送埠\RemoveSendPort  
  
 安裝和清除批次檔使用的是下列 BTSTask：  
  
-   **BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結  
  
-   **BTSTask RemoveApp**用以移除 FlatFileReceiveApplication  
  
## <a name="see-also"></a>請參閱  
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)