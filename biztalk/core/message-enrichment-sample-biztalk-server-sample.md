---
title: 訊息豐富 」 範例 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41ed707-dbdb-46b7-97a6-86fdbc8ad285
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3413345c4e2d0a2ce4cd7ee1cb5ebda50b1dea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265206"
---
# <a name="message-enrichment-sample-biztalk-server-sample"></a>訊息豐富範例 (BizTalk Server 範例)
「訊息豐富」範例會示範如何將交換標頭附加至 X12 和 EDIFACT 文件的交易集訊息。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何將針對 EDIFACT 的 UNA、UNB 和 UNG 標頭及針對 X12 的 ISA 標頭附加至交易集。 具體來說，本範例執行下列工作：  
  
1.  將測試訊息放置到 \Message Enrichment\In 資料夾後，接收埠會拾取訊息，處理後再放到 MessageBox。  
  
2.  MessageEnrichmentOrchestration 會從 MessageBox 拾取測試訊息，因為它是根據其「接收」圖形上設定的篩選條件運算式訂閱訊息。  
  
3.  協調流程會讀取訊息之內容屬性的交換標頭。  
  
    > [!NOTE]
    >  UNA 和 UNG 標頭為 EDIFACT 訊息中的選用項目，因此訊息的內容屬性中可能沒有這兩個標頭。  
  
4.  協調流程會將交換標頭和訊息內文皆寫入單一新訊息中。  
  
5.  協調流程會將設定於 ReceivePortNameCorrelationType 相互關聯類型中的其他屬性升級至訊息。 這樣一來，協調流程的使用者就可以選取其訂閱所需的屬性清單。 這些屬性寫在「建構訊息」圖形中。 並非所有寫入原始訊息的內容屬性都會寫入新訊息中。  
  
6.  協調流程會將新訊息放至 MessageBox 中。  
  
7.  傳送埠會拾取新訊息，並透過 FILE 配接器傳送至 \Message Enrichment\Out 資料夾。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝資料夾： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message 擴充。  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|解除部署範例實例。 協調流程的執行個體不得為作用中才能成功。 否則會失敗。|  
|MessageEnrichment.sln|包含 MessageEnrichment 和 MessageEnrichmentLibrary 專案。|  
|Setup.bat|部署包含接收埠、傳送埠和協調流程的範例實例。|  
|EDIFACT_example.edi|為輸入 EDIFACT 訊息。|  
|X12_example.edi|為輸入 X12 訊息。|  
|MessageEnrichment.btproj|包含 MessageEnrichment 協調流程和結構描述的專案。|  
|MessageEnrichmentBindings.xml|包含協調流程、連接埠和合作對象繫結的檔案。|  
|MessageEnrichmentOrchestration.odx|將標頭附加至訊息的協調流程。|  
|MessageEnrichmentOrchestration.odx.cs|將標頭附加至訊息的協調流程程式碼。|  
|EFACT_D98B_APERAK.xsd|輸入訊息的 EDIFACT 結構描述。|  
|Enriched_EFACT_D98B_APERAK.xsd|輸出訊息的 EDIFACT 結構描述。|  
|X12_00401_864.xsd|輸入訊息的 X12 結構描述。|  
|Enriched_X12_00401_864.xsd|輸出訊息的 X12 結構描述。|  
|Headers.xsd|加入至輸入訊息之標頭的結構描述。|  
|MessageEnrichmentLibrary.csproj|包含 Headers.cs、OrchestrationUtilities.cs 和 ParseHeaders.cs 檔案的專案。|  
|Headers.cs|包含代表標頭資料類別。|  
|OrchestrationUtilities.cs|包含協調流程所使用的公用程式方法。|  
|ParseHeaders.cs|包含新訊息中所使用之 UNA 的預設值。 這些值取自 ParseHeaders.cs 中的 SerializeEDIFACTHeaders 方法。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 使用此範例做為附加交換標頭至 EDI 交易集訊息所需動作的實用範例。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 若要建置和初始化「訊息豐富」範例，必須為此範例建置和部署 BizTalk 專案、設定接收埠和位置，以及設定兩個不同的傳送埠。  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a>若要為此範例建置和部署 BizTalk 專案  
  
1.  使用 Notepad.Exe 開啟[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\  
    MessageEnrichment\properties\AssemblyInfo.cs 然後在檔案最下方加入下行：  
  
    ```  
    [assembly: Microsoft.XLANGs.BaseTypes.BizTalkAssembly(typeof(Microsoft.BizTalk.XLANGs.BTXEngine.BTXService))]  
    ```  
  
2.  儲存修改的 AssemblyInfo.cs 檔案，然後結束 [記事本]。  
  
3.  在命令視窗中，移動至下列資料夾：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message 擴充  
  
4.  執行**Setup.bat**，它會執行下列動作：  
  
    -   建立接收 (**中**) 和傳送 (**出**) \MessageEnrichment 資料夾中建立此範例的資料夾。  
  
    -   將金鑰組寫入 MessageEnrichmentLibrary\testkey.snk  
  
    -   建置並部署 MessageEnrichmentLibrary.btproj 專案。  
  
    -   建置並部署 MessageEnrichment.btproj 專案。  
  
    -   讀取 MessageEnrichmentBindings.xml 內的繫結資訊。  
  
        > [!NOTE]
        >  這個專案的繫結需要的 BizTalk 主控件標示為信任的驗證。  若要使用此功能不受信任的主機，修改 MessageEnrichmentBindings.xml 以及如何變更 HostTrusted ="true"的項目，以 HostTrusted ="false"。  
  
    -   更新協調流程繫結。  
  
    -   更新傳送埠、傳送埠群組和接收埠。  
  
    -   更新合作對象和登錄。  
  
    -   啟動傳送埠。  
  
    -   啟用接收位置。  
  
    -   登錄並啟動協調流程。  
  
 BizTalk Server 現在已準備就緒可使用此範例。  
  
## <a name="running-this-sample"></a>執行此範例  
 使用下列程序執行「訊息豐富」範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  將 EDIFACT_examples.edi 檔案從 \MessageEnrichment\Instances 資料夾複製至 \MessageEnrichment\In 資料夾。  
  
2.  確認 EDIFACT_examples.edi 檔案已從 \MessageEnrichment\In 資料夾消失並出現在 \MessageEnrichment\Out 資料夾內。  
  
3.  開啟 \MessageEnrichment\Out 資料夾內的檔案。 確認 \MessageEnrichment\Instances 資料夾中有 EDIFACT_examples.edi 檔案的 XML 表示法，而且除輸出檔案具有 EDIFACT UNA、UNB 和 UNG 標頭之外，其內容與 EDIFACT_examples.edi 檔案相同。  
  
4.  重複步驟 1 和 2 處理 \MessageEnrichment\Instances 資料夾內的 X12_examples.edi 檔案。  
  
5.  開啟 \MessageEnrichment\Out 資料夾內的新檔案。 確認 \MessageEnrichment\Instances 資料夾中有 X12_examples.edi 檔案的 XML 表示法，而且除輸出檔案具有 X12 ISA 標頭之外，其內容與 X12_examples.edi 檔案相同。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 無  
  
## <a name="see-also"></a>另請參閱  
 [EDI 和 AS2 （BizTalk Server 範例資料夾）](../core/edi-and-as2-biztalk-server-samples-folder.md)