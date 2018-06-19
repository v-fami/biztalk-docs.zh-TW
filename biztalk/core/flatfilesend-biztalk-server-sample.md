---
title: FlatFileSend （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52dd0018-e272-40db-a26a-509d444d7106
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a9e967a8127a07b561e950b084bf799b0e2a4ee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969692"
---
# <a name="flatfilesend-biztalk-server-sample"></a>FlatFileSend (BizTalk Server 範例)
FlatFileSend 範例示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將 XML 檔案處理成相等的一般檔案。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例將 [FFInput] 資料夾設定為接收位置。 當您將檔案 (例如範例檔案 FlatFileSend_in.xml) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 便會使用下列步驟來處理此檔案中的訊息：  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 讀取接收位置資料夾 [FFInput] 中輸入檔的訊息。  
  
2.  訊息透過 XML 接收管線傳遞。  
  
3.  在 MessageBox 資料庫中，訊息路由傳送至 FILE 傳送埠，這個傳送埠具有使用「一般檔案組合器」元件設定的傳送管線。 「一般檔案組合器」元件會使用一般檔案結構描述，將 XML 訊息轉換成相等的一般檔案表示。  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將轉換後的訊息寫入至傳送配接器資料夾 [FFOutput] 中的文字檔。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 範例訊息大致指出了此範例的基本設計。 一般檔案訊息必須使用「一般檔案組合器」和自訂傳送管線內的一般檔案結構描述來組合。 這些和其他設計元素總結於下表中。  
  
|設計元素|已選取的原因|  
|--------------------|--------------------------|  
|自訂傳送管線|-自訂管線會使用一般檔案組合器和一般檔案結構描述將執行個體訊息轉譯成一般檔案格式。一般檔案組合器 」 本身並非管線，設定傳送管線中的時，無法使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。|  
|一般檔案結構描述|-定義的所有相同記錄與欄位特性 （包含結構） 的 XML 結構描述，並提供用來定義所有轉譯 XML 執行個體訊息轉換一般檔案訊息 （反之亦然） 所需的一般檔案特性的機制。|  
|訂閱篩選器|-訂用帳戶篩選器會執行實際的路由擷取符合根據屬性欄位的一或多個準則的訊息。|  
|XMLReceive|-執行對內送 XML 訊息的處理。 在本範例中，來源訊息使用的是訂單的 XML 表示。|  
  
 這些項目結合後產生的解決方案，可從接收位置接受 XML 檔案格式的訂單訊息，再將一般檔案訂單寫出至傳送位置。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|FlatFileSend.btproj、FlatFileSend.sln|這個範例的專案及解決方案檔案。|  
|FlatFileSendBinding.xml|用於自動化設定，例如連接埠繫結。|  
|FlatFileSend_in.xml|範例輸入檔案。|  
|PO.xsd|輸出一般檔案的結構描述。|  
|SendPipeline.btp|使用「一般檔案組合器」元件設定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送管線檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 您可以使用此範例，做為自己的一般檔案處理解決方案基礎。 您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為資料夾內的這個範例建立輸入 (FFInput) 和輸出 (FFOutput) 資料夾。  
  
         *\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend  
  
    -   為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
        > [!NOTE]
        >  此範例會顯示下列警告時建立並繫結連接埠：`Warning: Receive handler not specified for receive location "FlatFileSend_RL"; updating with first receive handler with matching transport type. Warning: Host not specified for orchestration "FlatFileSend"; updating with first available host.`您可以放心忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
> [!NOTE]
>  如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
  
> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
  
1.  將 FlatFileSend_in.xml 檔案的複本放在 FFInput 資料夾中。  
  
2.  觀察建立於 FFOutput 資料夾內的一般檔案。 這個文字檔的名稱是以訊息識別碼 GUID 為根據。 此檔案包含相當於 XML 輸入檔 FlatFileSend_in.xml 的一般檔案。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：  
  
-   啟動傳送埠\StartSendPort.vbs  
  
-   啟用接收位置\EnableRecLoc  
  
-   移除傳送埠\RemoveSendPort  
  
 安裝和清除批次檔使用的是下列 BTSTask：  
  
-   **BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結  
  
-   **BTSTask RemoveApp**用以移除 FlatFileSendApplication  
  
## <a name="see-also"></a>請參閱  
-  [一般檔案結構描述](../core/flat-file-schemas.md)   
-  [預設管線](../core/default-pipelines.md)   
-  [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
-  **WMI 指令碼範例**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
-  [FlatFileReceive (BizTalk Server 範例)](../core/flatfilereceive-biztalk-server-sample.md)