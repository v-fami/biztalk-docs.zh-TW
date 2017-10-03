---
title: "撰寫訊息處理器 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, examples
- messages, processing
- messages, aggregated
- examples, pipelines
ms.assetid: a0f87f98-6f5f-4edb-8f65-49d22df5de97
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3853a5b903215b6f716a13c33727e60c67107b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="composed-message-processor-biztalk-server-sample"></a>撰寫訊息處理器 (BizTalk Server 範例)
此範例的目的是建置撰寫訊息處理器應用程式，可處理來自彙總訊息的個別明細項目。  
  
 具體而言，我們建置的協調流程排程會：  
  
1.  接收包含多筆訂單的批次交換訊息。  
  
2.  將交換訊息解譯為個別訂單文件。  
  
3.  處理每份文件，將每筆訂單轉換為發票訊息。  
  
4.  將所有發票訊息組合為一個批次交換。  
  
 步驟 3 已經過簡化供範例使用。 例如，在更複雜的應用程式中，協調流程可能會將解譯的訂單傳送至不同的後端庫存系統，然後在收集所有回應後，再將它們彙總為一個批次發票訊息。  
  
 如需撰寫訊息處理器模式的詳細資訊，請參閱 [1]。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 範例解決方案內有兩種專案，將在以下章節中詳細描述。  
  
### <a name="pipelines-and-schemas"></a>管線和結構描述  
 管線和結構描述專案包含：  
  
-   輸入訂單交換和輸出發票交換所用的一般檔案結構描述。  
  
-   將訂單文件轉換為發票文件的對應。  
  
-   接收管線和傳送管線。  
  
#### <a name="flat-file-schemas-for-input-and-output-interchanges"></a>輸入交換和輸出交換所用的一般檔案結構描述  
 我們的範例應用程式會搭配一般檔案格式的交換使用。 以下是訂單交換和發票交換的範例：  
  
 訂單交換 (CMPInput.txt)：  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
PO1999-10-21  
US    John Dow       123 Elm Street      Mill Valley    CA 90952  
US    July Dow       8 Pine Avenue       Old Town       PA 95819  
Please ship it urgent!  
ITEMS,ITEM398-BB|Tire|4|324.99|Wrap them up nicely,ITEM201-BB|Engine Oil|1|12.99|SAE10W30|1999-05-22  
PO1999-10-23  
US    John Connor    123 Cedar Street    Mill Valley    CA 90952  
US    Sarah Connor   8 Grass Avenue      Old Town       PA 95819  
Use cheapest shipping method.  
ITEMS,ITEM101-TT|Plastic flowers|10|4.99|Fragile handle with care,ITEM202-RR|Fertilizer|1|10.99|Lawn fertilizer,ITEM453-XS|Weed killer|1|5.99|Lawn weed killer|1999-05-25  
```  
  
 交換或訂單文件的標頭，都會識別其包含的文件類型：  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
```  
  
 此交換包含三筆訂單文件。 一個執行個體會包含以下資訊。 如您所見，其包含帳單地址和送貨地址以及所訂購項目的清單之類的資訊。  
  
```  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
```  
  
 我們要為此產生的發票交換應該如下所示：  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
INVOICE1999-10-21  
BILLTO,US,John Dow,123 Elm Street,Mill Valley,CA,90952  
398-BB    Tire              4    324.99    Wrap them up nicely  
201-BB    Engine Oil        1    12.99     SAE10W30  
INVOICE1999-10-20  
BILLTO,US,John Connor,123 Cedar Street,Mill Valley,CA,90952  
101-TT    Plastic flowers   10   4.99      Fragile handle with care  
202-RR    Fertilizer        1    10.99     Lawn fertilizer  
453-XS    Weed killer       1    5.99      Lawn weed killer  
```  
  
 此交換包含訂單交換內的資訊子集，且交換的格式與標頭的格式不同。  
  
 標頭如下所示：  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
```  
  
 文件執行個體包含下列項目：  
  
```  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
```  
  
 首先必須建立一般檔案結構描述，用於：  
  
-   訂單文件 (PO.xsd)  
  
-   發票文件 (Invoice.xsd)  
  
-   訂單標頭 (POHeader.xsd)  
  
-   發票標頭 (InvoiceHeader.xsd)  
  
 針對這個範例，我們不會解釋建立一般文件結構描述的程序。 若要學習如何從文件執行個體建立一般文件結構描述，請參閱＜從文件執行個體建立一般檔案結構描述＞文件章節。  
  
#### <a name="map-to-transform-purchase-order-document-into-invoice-document"></a>將訂單文件轉換為發票文件的對應  
 將訂單執行個體轉換為發票文件的對應 (PO2Invoice.btm)。  
  
#### <a name="receive-and-send-pipelines"></a>接收管線和傳送管線  
 接收管線 (FFReceivePipeline.btp) 包含用於處理訂單交換的一般檔案解譯器元件。 尤其是針對 CMPInput.txt 檔案內的交換，它會移除交換標頭，並產生三份對應至三筆訂單的 XML 文件。  
  
 接收管線內一般檔案解譯器的設定如下所示：  
  
-   **文件結構描述：** PipelinesAndSchemas.PO  
  
-   **標頭結構描述：** PipelinesAndSchemas.POHeader  
  
-   **保留標頭：** False  
  
-   **可復原交換：** False  
  
-   **結尾結構描述：** （無）  
  
-   **驗證文件結構：** False  
  
 傳送管線 (FFSendPipeline.btp) 包含用於建立彙總發票交換的一般檔案組合器元件。  
  
 傳送管線內一般檔案組合器的設定如下所示：  
  
-   **文件結構描述：** PipelinesandSchemas.Invoice  
  
-   **標頭結構描述：** PipelinesAndSchemas.InvoiceHeader  
  
-   **保留位元順序標記：** False  
  
-   **目標字元集：** （無）  
  
-   **結尾結構描述：** （無）  
  
### <a name="orchestration-schedule"></a>協調流程排程  
 協調流程排程 (CMP.odx) 就是所有主要處理發生的位置。 尤其會執行下列動作：  
  
-   執行接收管線以解譯訂單交換  
  
-   轉換接收管線的每個輸出訊息  
  
-   執行傳送管線以組合發票交換  
  
#### <a name="creating-orchestration-schedule-and-defining-global-variables"></a>建立協調流程排程和定義全域變數  
 我們的協調流程會接收一般檔案交換做為輸入，傳送一般檔案交換做為輸出。 因此我們必須將輸入訊息和輸出訊息 (分別稱為 InputInterchange 和 OutputInterchange) 定義為無從驗證的型別 (也就是 System.Xml.XmlDocument 型別)。  
  
 另外，還必須定義不可部分完成的範圍，我們將在此範圍處理訊息。 這是必要的，因為接收管線可以在不可部分完成的範圍內執行。  
  
#### <a name="executing-receive-pipeline"></a>執行接收管線  
 下一步我們會新增邏輯，以便執行協調流程中所接收之訊息的接收管線。 若要執行這項操作，首先必須在範圍內宣告 Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages 型別的變數 (稱為 RcvPipeOutput)。 此變數是允許我們循環接收管線輸出訊息的列舉值。 請注意，為了存取此型別及執行來自協調流程之管線的其他型別，必須新增對下列組件的參考：  
  
-   Microsoft.XLANGs.Pipeline.dll  
  
-   Microsoft.BizTalk.Pipeline.dll：  
  
 接收管線不一定都能成功執行。 有時候訊息可能格式不正確，導致管線處理失敗。 管線在協調流程執行失敗時，就有可攔截之擲回的例外狀況，且可執行錯誤處理邏輯。 為了攔截管線所擲回的例外狀況，我們必須以例外狀況處理在非不可部分完成範圍內執行管線。 執行管線的實際程式碼是該範圍內從「運算式」圖形叫用。  
  
 在 ExecuteRcvPipe「運算式」圖形內，寫入下列這行執行接收管線的程式碼：  
  
```  
RcvPipeOutput = Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteReceivePipeline(typeof(PipelinesAndSchemas.FFReceivePipeline), InputInterchange);  
```  
  
 我們來以更詳細的方式分析這行程式碼。 如您所見，我們呼叫了 ExecuteReceivePipeline 靜態方法，該方法會將參數當成要執行的接收管線類型和輸入訊息。 因此會產生含輸出訊息集的列舉器物件。 結果會被指派為 ReceivePipelineOutputMessages 型別的變數，該型別先前已經在此範圍內加以定義了。  
  
 我們還針對這個管線執行範圍加入了例外狀況處理區塊。 此區塊會攔截 XLANGPipelineManagerException 型別的例外狀況，接著為了簡化起見，直接終止含自訂錯誤訊息的協調流程執行個體。  
  
 在更複雜的案例中，可以在此執行其他錯誤處理，例如產生錯誤通知訊息，然後用電子郵件將它傳送給商務使用者或系統管理員。  
  
#### <a name="transforming-pipeline-output-messages"></a>轉換管線輸出訊息  
 我們執行管線並產生解譯訊息集後，必須將每則輸出訊息轉換為不同的格式。  
  
 若要在協調流程中使用轉換，我們必須定義轉換輸入和轉換輸出這兩種訊息。 我們會在不可部分完成的範圍內定義那些訊息。 名為 TmpMessageIn 的轉換輸入訊息將屬於 PipelinesAndSchemas.PO 型別。 名為 TmpMessageOut 的轉換輸出訊息則屬於 PipeliensAndSchemas.Invoice 型別。 我們會套用 PipelinesAndSchemas 專案中所定義的 PO2Invoice.btm 對應。  
  
 如果要對應各管線輸出訊息，我們必須在迴圈中執行轉換。 我們會使用具下列結束條件的「迴圈」圖形：  
  
```  
RcvPipeOutput.MoveNext()  
```  
  
 MoveNext() 方法是 IEnumerator .NET 介面的標準方法，允許在管線輸出訊息的集合內移動。 當它到達集合的結尾時，會傳回 false。  
  
 第一個「建構」圖形會用來從管線輸出訊息，建構 TmpMessageIn 協調流程訊息。  
  
 「建構」圖形內的程式碼：  
  
```  
TmpMessageIn = null;  
RcvPipeOutput.GetCurrent(TmpMessageIn);  
```  
  
 在此程式碼中，我們會先初始化協調流程訊息為空值，然後將它自管線輸出訊息集合設定為目前的訊息。  
  
 在第二個「建構」圖形中，會實際執行 TmpMessageIn 的轉換，並建構 PipelinesAndSchemas.Invoice 型別的 TmpMessageOut。  
  
#### <a name="executing-send-pipeline"></a>執行傳送管線  
 協調流程中的最後一個處理步驟，就是執行一般檔案傳送管線，將所有轉換的 xml 訊息組合為一個一般檔案交換。  
  
 為了執行傳送管線，我們必須使用 Microsoft.XLANGs.Pipeline.SendPipelineInputMessages 型別之名為 SendPipeInput 的變數，該變數會保存需要在傳送管線內處理的協調流程訊息集合。  
  
 我們會在執行轉換之迴圈內的最後一個運算式中寫入程式碼，將每則轉換的訊息加入至傳送管線的訊息集合。  
  
```  
SendPipeInput.Add(TmpMessageOut);  
```  
  
 與執行接收管線的方式類似，用來執行傳送管線的程式碼，會放在具例外狀況處理區塊的非不可部分完成的範圍內。 傳送管線執行程式碼位在建構區塊的「訊息指派」圖形內。  
  
```  
OutputInterchange = null;  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(typeof(PipelinesAndSchemas.FFSendPipeline), SendPipeInput, OutputInterchange);  
```  
  
 建構區塊是用於建構無從驗證的型別 (也就是 System.Xml.XmlDocument) 管線輸出訊息 OutputInterchange。 接著，在「訊息指派」圖形內，新建構的訊息會初始化為 null。 然後，就會叫用 ExecuteSendPipeline 靜態方法執行傳送管線。 該方法會將參數當成要執行的傳送管線類型、輸入訊息，及對儲存管線輸出之輸出訊息的參考。  
  
 與執行接收管線的方式類似，管線執行範圍也會有例外狀況處理區塊。 此區塊會攔截 XLANGPipelineManagerException 型別的例外狀況，接著為了簡化起見，直接終止含自訂錯誤訊息的協調流程執行個體。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 下表列出此範例使用的檔案。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。<br /><br /> 移除傳送埠和接收埠。<br /><br /> 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|ComposedMessageProcessor.sln|此範例的 Visual Studio 方案檔案。|  
|ComposedMessageProcessorBinding.xml|此範例的繫結檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 [協調流程] 資料夾中：<br /><br /> CMP.odx|該協調流程會執行接收管線來解譯訊息、轉換每個已解譯的訊息，然後執行傳送管線將訊息組合成一個交換。|  
|在 [協調流程] 資料夾中：<br /><br /> Orchestration.btproj|協調流程所使用的 BizTalk 專案。|  
|在 [協調流程] 資料夾中：<br /><br /> SuspendMessage.odx|協調流程用於擱置管線處理失敗的訊息。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> CMPInput.xml, CMPOutput.xml|此範例的輸入和輸出文件執行個體。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> FFReceivePipeline.btp, FFSendPipeline.btp|具一般檔案元件的接收和傳送管線。 這些管線是在協調流程中執行。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> Invoice.xsd, InvoiceHeader.xsd|輸出文件和標頭所用的一般檔案結構描述。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PO.xsd, POHeader.xsd|輸入文件和標頭所用的一般檔案結構描述。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PropertySchema.xsd|此範例的屬性結構描述。|  
  
## <a name="building-and-initializing-the-sample"></a>建置和初始化範例  
 請使用下列程序，建置和初始化「編輯」範例。  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a>若要建置及初始化「編輯」範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<範例路徑 > \Pipelines\ComposedMessageProcessor  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  
  
         \<範例路徑 > \Pipelines\ComposedMessageProcessor  
  
    -   編譯此範例的 Visual Studio 專案。  
  
    -   建立名為「CMP 範例」的新應用程式，並將範例組件部署到其中。  
  
    -   建立並繫結 BizTalk Server 接收位置以及傳送和接收埠。  
  
    -   登錄和啟動協調流程、啟用接收位置，並啟動傳送埠。  
  
         若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 這個金鑰組的用途是簽署產生的組件。  
  
3.  在嘗試執行此範例之前，請確認 BizTalk Server 未在建置和初始化期間報告任何錯誤。  
  
     若要復原 Setup.bat 所做的變更，您必須執行下列動作：  
  
    1.  從 [BizTalk Server 管理] 主控台中，停止並重新啟動主控件執行個體。  
  
    2.  執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-the-sample"></a>執行範例  
 使用下列程序執行 ComposedMessageProcessor 範例。  
  
#### <a name="to-run-the-composedmessageprocessor-sample"></a>若要執行 ComposedMessageProcessor 範例  
  
1.  複製 PipelinesAndSchemas 資料夾內的 CMPInput.txt 文字檔。 將複製的檔案貼入 [In] 資料夾中。  
  
2.  請觀察建立於 Out 資料夾中的文字檔。此檔案包含的記錄與 CMPInput.txt 相同，但是檔案內的資料格式不同。  
  
     訊息通過 BizTalk Server 時，會發生以下狀況：  
  
    1.  訊息會被解譯並轉換為 XML 訊息。 每個訊息都會對應至不同的格式。  
  
    2.  所有對應的訊息都會組合在一起，並轉換為一般檔案格式。  
  
## <a name="see-also"></a>另請參閱  
 [管線 （BizTalk Server 範例資料夾）](../core/pipelines-biztalk-server-samples-folder.md)