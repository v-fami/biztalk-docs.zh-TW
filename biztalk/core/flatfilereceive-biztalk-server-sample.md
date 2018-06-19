---
title: FlatFileReceive （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90bd9e8d-6ed9-49c4-8437-c0c8b2a9a78d
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db996437cce8cb6f89fb00b589fcbc95429e72f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970164"
---
# <a name="flatfilereceive-biztalk-server-sample"></a>FlatFileReceive （BizTalk Server 範例）
FlatFileReceive 範例會示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將一般檔案處理成相等的 .xml 檔案。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例將 [FFInput] 資料夾設定為接收位置。 當您將檔案 (例如範例檔案 FlatFileReceive_in.txt) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會依序使用下列步驟處理此檔案內的訊息。  
  
1.  讀取接收位置內 [FFInput] 資料夾中輸入檔的訊息。  
  
2.  在接收管線中，「一般檔案解譯器」元件會將訊息由一般檔案格式轉換為相等的 XML 訊息。  
  
3.  在 MessageBox 資料庫中，訊息會路由至 FILE 傳送埠，該傳送埠會將 XML 訊息寫入傳送配接器檔案夾 FFOutput 內的檔案。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 範例訊息大致指出了此範例的基本設計。 一般檔案訊息必須使用一般檔案解譯器和自訂接收管線內一般檔案結構描述進行反組譯。 這些和其他設計元素總結於下表中。  
  
|設計元素|已選取的原因|  
|--------------------|--------------------------|  
|自訂接收管線|-自訂管線會使用一般檔案解譯器和一般檔案結構描述來轉譯內送訂單訊息。 「一般檔案解譯器」本身並非管線，在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中設定接收管線時無法使用它。|  
|一般檔案結構描述|-定義的所有相同記錄與欄位特性 （包含結構） 的 XML 結構描述，並提供一個機制來定義一般檔案特性，將一般檔案執行個體訊息轉譯成相等的 XML 執行個體所需的所有訊息 （反之亦然）。|  
|訂閱篩選器|-訂用帳戶篩選器會執行實際的路由擷取符合根據屬性欄位的一或多個準則的訊息。|  
|XMLTransmit|-執行基本組件外寄 XML 訊息所需。 PassThruTransmit 管線不會提供其他支援。|  
  
 這些元素結合後產生的解決方案，可從接收位置接受一般檔案格式的訂單訊息，再將產生的 XML 表示法寫出至傳送位置。  
  
 下列考量適用於此範例的設計：  
  
-   一般檔案結構描述 (PO.xsd) 包含擴充註解，會說明採購訂單一般檔案的結構。 這些檔案可以用手動方式建立，但有不少可以透過 [一般檔案精靈] 產生。  
  
-   一般檔案結構描述使用的是 Unqualified 的 elementFormDefault 值。 雖然產生的結果正確無誤，但包含其他未預期的 XML 命名空間 (xmlns) 限定性條件。 使用值為 Qualified 的 elementFormDefault 即可避免這個問題。  
  
-   傳送管線會使用 XmlTransmit。 傳送埠不需要屬性降級或其他訊息的處理時，請使用 PassThruTransmit 管線。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileReceive\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|FFReceivePipeline.btp|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收管線檔案，含「一般檔案解譯器」元件。|  
|FlatFileReceive.btproj, FlatFileReceive.sln|這個範例的專案及解決方案檔案。|  
|FlatFileReceive_in.txt|範例輸入檔案。|  
|FlatFileReceiveBinding.xml|用於自動化設定，例如連接埠繫結。|  
|PO.xsd|內送一般檔案的結構描述。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 您可以使用此範例，做為自己的一般檔案處理解決方案基礎。 您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileReceive  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為資料夾內的這個範例建立輸入 (FFInput) 和輸出 (FFOutput) 資料夾。  
  
         *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileReceive  
  
    -   為這個範例編譯和部署 Visual Studio 專案。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
        > [!NOTE]
        >  此範例會顯示下列警告時建立並繫結連接埠：`Warning: Receive handler not specified for receive location "FlatFileReceive_RL"; updating with first receive handler with matching transport type.`您可以放心忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
> [!NOTE]
>  如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
  
> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
  
1.  請將 FlatFileReceive_in.txt 檔案的複本放在 [FFInput] 資料夾中。  
  
2.  觀察建立於 [FFOutput] 資料夾內的 .xml 檔案。 輸出檔的名稱的根據是訊息識別碼 GUID。 此檔案包含置於接收資料夾內與一般檔案相等的 XML。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：  
  
-   啟動傳送埠\StartSendPort.vbs  
  
-   啟用接收位置\EnableRecLoc  
  
-   移除傳送埠\RemoveSendPort  
  
 安裝和清除批次檔使用的是下列 BTSTask：  
  
-   **BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結  
  
-   **BTSTask RemoveApp**用以移除 FlatFileReceiveApplication  
  
## <a name="see-also"></a>請參閱  
-  [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
-  [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
-  [一般檔案結構描述](../core/flat-file-schemas.md)   
-  [預設管線](../core/default-pipelines.md)   
-  **WMI 指令碼範例**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
-  [FlatFileSend (BizTalk Server 範例)](../core/flatfilesend-biztalk-server-sample.md)