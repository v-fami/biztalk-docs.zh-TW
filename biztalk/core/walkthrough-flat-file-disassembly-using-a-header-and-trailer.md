---
title: 逐步解說： 使用標頭和結尾的一般檔案解譯 |Microsoft Docs
description: 使用 「 一般檔案結構描述精靈 」 來建立標頭結構描述、 結尾結構描述和內文結構描述，並再解譯 BizTalk Server 的一般檔案
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715af9cc-d718-483d-b593-64462aa5a58b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a39361e4da6dec9acf023911466f07572a3de13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983911"
---
# <a name="walkthrough-flat-file-disassembly-using-a-header-and-trailer"></a>逐步解說：使用標頭和結尾進行一般檔案解譯

## <a name="overview"></a>概觀
此逐步解說示範如何使用由「一般檔案結構描述精靈」所建立的結構描述，對包含標頭、結尾及重複訊息內文的檔案進行一般檔案解譯。 在此逐步解說中，您將開發部分虛構的錯誤追蹤系統，使其符合下列需求：  
  
- 錯誤訊息記錄到公司內各個不同的實體網站，再傳送至一個集中位置處理後放入各個後端系統。  
  
- 會以一般檔案格式寫入錯誤訊息，其標頭指出位置，內文含有一或多個錯誤訊息，且結尾指出批次編號。  
  
- 如果訊息中沒有標頭、內文和結尾，則視同無效訊息。  
  
  完成此逐步解說後，將會建立 BizTalk Server 應用程式用於處理一般檔案，並將其輸出為 XML 以供後端系統處理。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本範例，您必須已熟悉如何建立 BizTalk Server 專案和簽署組件，及使用「BizTalk Server 管理主控台」檢視應用程式和連接埠。 您也應該事先瞭解中提到的觀念[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。 對「一般檔案結構描述精靈」稍具基本認識的話亦有所助益，但並非必要條件。  
  
## <a name="what-this-example-does"></a>本範例的工作項目  
 本範例使用自訂管線和「一般檔案解譯器」元件來處理內送一般檔案訊息。 訊息將使用標頭、結尾和內文結構描述進行剖析，然後輸出至傳送位置再交由後端系統處理。  
  
## <a name="example"></a>範例  
 若要建立範例，請依照以下各節所列的步驟進行。  
  
### <a name="create-a-new-biztalk-project"></a>建立新的 BizTalk 專案  
 建置方案前，您必須建立 BizTalk 專案、確定其具備強式名稱，並為其指定應用程式名稱。 指定應用程式名稱可避免 BizTalk Server 將方案部署至預設的 BizTalk 應用程式。  
  
1. 使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立新的 BizTalk 專案。 呼叫專案**FFDisassemblerWalkthrough**。  
  
2. 產生金鑰檔並將其指派給專案。 如需有關這項工作的詳細資訊，請參閱 <<c0> [ 專案設計工具、 簽署頁](http://go.microsoft.com/fwlink/?LinkId=125876)。  
  
3. 在 專案部署屬性，將**應用程式名稱**為"FlatFileExample 」，並將**重新啟動主控件執行個體**到`True`。 設定此旗標係指示主控件清除組件所有已快取的執行個體。  
  
### <a name="create-the-sample-data-file"></a>建立範例資料檔案  
若要產生結構描述，您必須先建立測試檔案。   
  
1.  啟動「記事本」或其他文字編輯器。  
  
2.  建立範例測試檔案。 此檔案包含標頭指出回報錯誤的位置，結尾指出該批次的批次 ID，且內文含有一或多筆錯誤記錄。 檔案的格式如下：  
  
    ```  
    Location  
    ERRORid|type|priority|description|errorDateTime  
    …additional error records   
    BatchID  
    ```  
  
    錯誤記錄會加上"ERROR"文字，而且以分隔 」&#124;"字元 （有別於位置）。 ERROR 記錄的資料項目如下表所述。  
  
    |元素|資料類型|描述|  
    |---|---|---|  
    |ID|integer|此錯誤的 ID。|  
    |類型|integer|錯誤的類型。|  
    |優先權|string|優先順序指標：「低」、「中」或「高」。|  
    |描述|string|錯誤的描述。|  
    |錯誤日期時間|DateTime|發生錯誤的日期和時間。|  
  
    檔案中可能有一筆或多筆 ERROR 記錄。  
  
     * *-或--* *
  
     將下列的範例資料複製到新的檔案。 最後一行包含尾端換行字元：
  
    ```  
    East Coast Facility  
    ERROR102|0|High|Sprocket query fails.|1999-05-31T13:20:00.000-05:00  
    ERROR16502|2|Low|Time threshold exceeded.|1999-05-31T13:20:00.000-05:00  
    8675309  
  
    ```  
  
3.  將新的範例檔案儲存到專案目錄中。 請使用描述性名稱如 "ErrorFile.txt" 以方便找到檔案。  
  
### <a name="create-and-test-the-header-trailer-and-body-schemas"></a>建立並測試標頭、結尾和內文結構描述  
 建立範例資料檔案後，下一步驟就是建立標頭、結尾和內文結構描述。 這些結構描述將供「一般檔案解譯器」接收管線元件用來處理接收的訊息。  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-header-schema"></a>使用一般檔案結構描述精靈建立標頭結構描述  
  
1.  在專案中新增結構描述。 在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。  
  
2.  在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。 命名新的結構描述"命名為 Header.xsd"，然後按一下**新增**。  
  
3.  在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。  
  
4.  在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。 變更**記錄名稱**為"Header"，確認字碼頁，然後**下一步**。  
  
    > [!NOTE]
    >  如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。 這對本範例不會造成不良影響。  
  
5.  接著選取文件資料。 在 **選取文件資料**頁面上，反白顯示的第一行的資料，包括新行字元 {CR} 和 {LF} 所示：  
  
     ![選取為標頭結構描述的資料](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")  
  
     按 [下一步] 。  
  
6.  在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。 可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。  
  
7.  在 [**分隔記錄**頁面上，按一下**下一步]**。  
  
8.  接著指定子項目。 標頭含有一個項目，名為 "Location"：  
  
     ![定義的標頭位置節點](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")  
  
     按 **[下一步]** ，繼續進行。  
  
9. 在 **結構描述檢視**頁面上，確認結構描述。  
  
     ![已完成的結構描述檢視顯示標頭結構描述](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")  
  
     當您滿意，請按一下**完成**以完成精靈。  
  
10. 按一下 [ **\<結構描述\>** 標頭結構描述] 窗格中的節點。 在 [屬性] 窗格中，變更**Element FormDefault**要**Qualified**。 這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-trailer-schema"></a>使用一般檔案結構描述精靈建立結尾結構描述  
  
1.  在專案中新增結構描述。 在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。  
  
2.  在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。 命名新的結構描述"命名為 Trailer.xsd"，然後按一下**新增**。  
  
3.  在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。  
  
4.  在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。 變更**記錄名稱**改為"Trailer"，確認字碼頁，然後再按一下**下一步**。  
  
    > [!NOTE]
    >  如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。 這對本範例不會造成不良影響。  
  
5.  接著選取文件資料。 在 **選取文件資料**頁面上，反白顯示的最後一行的資料，包括新行字元 {CR} 和 {LF} 所示：  
  
     ![選取為結尾結構描述的資料](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")  
  
     按 [下一步] 。  
  
6.  在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。 可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。  
  
7.  在 [**分隔記錄**頁面上，按一下**下一步]**。  
  
8.  接著指定子項目。 結尾含有一個項目，名為 "BatchID"：  
  
     ![為結尾定義的位置節點](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")  
  
     按 **[下一步]** ，繼續進行。  
  
9. 在 **結構描述檢視**頁面上，確認結構描述。  
  
     ![結構描述檢視顯示已完成結尾結構描述](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")  
  
     當您滿意，請按一下**完成**以完成精靈。  
  
10. 按一下 [ **\<結構描述\>** 結尾結構描述] 窗格中的節點。 在 [屬性] 窗格中，變更**elementFormDefault**要**Qualified**。 這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-body-schema"></a>使用 「 一般檔案結構描述精靈 」 建立的內文結構描述  
  
1.  在專案中新增結構描述。 在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。  
  
2.  在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。 命名新的結構描述"命名為 Body.xsd"，然後按一下**新增**。  
  
3.  在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。  
  
4.  在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。 變更**記錄名稱**為"Body"，確認字碼頁，然後再按一下**下一步**。  
  
    > [!NOTE]
    >  如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。 這對本範例不會造成不良影響。  
  
5.  接著選取文件資料。 在 **選取文件資料**頁面上，反白顯示兩個和第三的資料行含有新行字元 {CR} 和 {LF} 所示：  
  
     ![選取為內文結構描述的資料](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")  
  
     按 [下一步] 。  
  
6.  在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。 可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。  
  
7.  在 [**分隔記錄**頁面上，選取**下一步]**。  
  
8.  接著定義子項目。 變更**Body_Child1**要**錯誤**並將其項目類型設定為**重複記錄**。 設定**Body_Child2**項目記錄型別**忽略**。  
  
9. 在 [**結構描述檢視**頁面上，按一下**下一步]** 定義 Error 記錄的子項目。  
  
10. 在 [**選取文件資料**頁面上，按一下**下一步]**。 精靈會正確選擇記錄定義的資料。  
  
11. 在 [**選取記錄格式**頁面上，按一下**下一步]**。 資料會以分隔符號進行格式化。  
  
12. 在 **分隔記錄**頁面上，選取 **&#124;** 如**子分隔符號**。 接下來，選取**記錄具有標記識別項**核取方塊，然後輸入**錯誤**做為標記值。  
  
     ![設定分隔記錄具有標記識別項](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")  
  
     按 [下一步] 。  
  
13. 接著定義 Error 記錄的子項目。  
  
     ![定義包含五個元素的錯誤記錄](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")  
  
     按 [下一步] 。  
  
14. 在 **結構描述檢視**頁面上，確認結構描述。  
  
     ![結構描述檢視顯示已完成的內文結構描述](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")  
  
     如果您所做的任何錯誤，請按一下**回**並進行必要的修正。 當您滿意，請按一下**完成**以完成精靈。  
  
15. 按一下 [ **\<結構描述\>** Body] 結構描述窗格中的節點。 在 [屬性] 窗格中，變更**Element FormDefault**要**Qualified**。 這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。  
  
16. 按一下 [ **\<錯誤\>** Body] 結構描述窗格上的節點。 在 [屬性] 窗格中，變更**Max Occurs**要**1**。 這可讓「一般檔案解譯器」將每項錯誤分割為個別的訊息。  
  
##### <a name="test-the-schemas-using-ffdasm"></a>測試使用 FFDasm 的結構描述  
  
1.  開啟命令提示字元，再將目錄變更為您的專案目錄。  
  
2.  從命令提示字元執行 FFDasm.exe，如下所示。  
  
    ```  
    <Samples Path>\SDK\Utilities\PipelineTools\FFDasm ErrorFile.txt  -hs header.xsd -bs body.xsd -ts Trailer.xsd  
    ```  
  
     這和其他管線工具的位置相關資訊，請參閱[管線工具](../core/pipeline-tools.md)。  
  
3.  FFDasm.exe 會產生兩個名為 {GUID}.xml 的輸出檔，分別代表測試檔案中的一筆 ERROR 記錄。 高優先順序的錯誤記錄看起來像這樣：  
  
    ```  
    <Body xmlns="http://FFDisassemblerWalkthrough.Body">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <DateTime>1999-05-31T13:20:00.000-05:00</DateTime>  
      </Error>  
    </Body>  
    ```  
  
### <a name="create-a-custom-receive-pipeline"></a>建立自訂接收管線  
 如今一般檔案結構描述已經定義完成，您必須建立自訂管線以使用「一般檔案解譯器」元件。 然後即可將「一般檔案解譯器」元件設定為使用標頭、內文和結尾結構描述來拆解訊息。    
 
1.  在專案中新增接收管線。 在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**專案，指向**新增**，然後按一下**新項目**。  
  
2.  在 **加入新項目** 對話方塊中，指向**管線檔案**，然後按一下 **接收管線**。 命名新的管線"為 FFReceivePipeline"，然後按一下**新增**。  
  
3.  將「一般檔案解譯器」元件從 [工具箱] 窗格拖曳到「解譯」步驟以設定新管線。  
  
4.  在 [屬性] 窗格中，設定**文件結構描述**要**FFDisassemblerWalkthrough.Body**，則**標頭結構描述**至**FFDisassemblerWalkthrough.Header**而**結尾結構描述**要**FFDisassemblerWalkthrough.Trailer**。  
  
### <a name="deploy-the-application-and-configure-the-send-and-receive-ports"></a>部署應用程式並設定傳送埠和接收埠  
 建立結構描述和自訂接收管線後，您必須編譯並部署專案。 一旦專案部署完成，即可使用「BizTalk Server 管理主控台」設定傳送埠和接收埠。  

##### <a name="deploy"></a>部署  
1. 內在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，將方案部署的專案上按一下滑鼠右鍵，然後按一下**部署**。  
  
2. 使用 BizTalk Server 管理主控台中，依序展開**應用程式**群組，以確認**FlatFileExample**呈現為自訂的應用程式。  
  
##### <a name="configure-the-receive-port"></a>設定接收埠  
  
1.  使用 Windows 檔案總管來建立名為"Receive"目錄，底下**FFDisassemblerWalkthrough**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，依序展開**FlatFileExample**應用程式，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下  **單向接收埠**。  
  
3.  在 **接收埠屬性**對話方塊方塊中，設定為"ReceiveError"的連接埠的名稱。  
  
4.  按一下 **接收位置**，然後按一下**新增**新增接收位置。 將新的接收位置命名為 "ReceiveErrorLocation"。 設定**接收管線**要**FFReceivePipeline**。 針對**傳輸類型**，選取**檔案**，然後按一下**設定**。 選取的接收目錄，您建立，並將**檔案遮罩**至 *.txt。  
  
5.  按一下 [確定] 。 接收埠即設定完成。 按一下 **確定**關閉。  
  
##### <a name="configure-the-send-port"></a>設定傳送埠  
  
1.  使用 Windows 檔案總管底下建立名為 「 傳送 」 的目錄**FFDisassemblerWalkthrough**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，依序展開**FlatFileExample**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向傳送埠...**.  
  
3.  在 **傳送埠屬性**對話方塊方塊中，設定 「 傳送 」 的連接埠的名稱。  
  
4.  傳輸類型 選取**檔案**，然後按一下**設定**。 將目的資料夾設定為剛才建立的傳送目錄。  
  
5.  接著設定篩選條件。 按一下 **篩選器**並加入下列運算式：  
  
    -   BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**  
  
6.  按一下 **確定**完成傳送埠組態。 傳送埠即設定完成。  
  
### <a name="run-the-example"></a>執行範例  
 現在即可開始執行範例。 之後您可以使用 BizTalk Server 管理主控台來啟動應用程式，請將測試檔案複製到接收位置，並觀察 傳送位置中所產生的結果。  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**FlatFileExample**應用程式，，然後按一下**開始**。 此登錄和啟動傳送埠和接收埠。  
  
2.  將範例 Errorfile.txt 複本放到接收目錄中。 傳送目錄中應該就會產生兩個輸出檔。  
  
