---
title: "逐步解說： 使用 XML 信封 （基本） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content-based routing, promoting properties
- promoting properties, routing messages
- promoting properties, content-based routing
- routing, messages
- routing, promoting properties
ms.assetid: 02d0c596-0cfe-4bae-9f1b-d7dbc17e18a9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9090c4ee7d576bb7ab610cd81637680d837b2cae
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-using-xml-envelopes-basic"></a>逐步解說： 使用 XML 信封 （基本）
此範例藉由實作虛構錯誤追蹤系統的一部分，示範基本的 XML 信封解譯。 這個範例符合下列需求：  
  
1.  錯誤訊息記錄到公司內各個不同的實體網站，再傳送至一個集中位置處理後放入各個後端系統。  
  
2.  錯誤訊息會以 XML 格式寫入。  
  
3.  錯誤訊息可以單獨傳送，而不使用信封，也可以包含在信封中進行批次傳送。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本範例，您必須已熟悉如何建立 BizTalk Server 專案、簽署組件，及使用 BizTalk Server 管理主控台檢視應用程式和連接埠。 您也應該事先瞭解中提到的觀念[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。  
  
## <a name="what-this-example-does"></a>本範例的工作項目  
 此範例定義信封結構描述並使用 XmlDisassembler 管線，以處理內含單一錯誤訊息或批次錯誤訊息的內送訊息。  
  
## <a name="example"></a>範例  
 若要建立範例，請依照以下各節所列的步驟進行。  
  
### <a name="create-a-new-biztalk-project"></a>建立新的 BizTalk 專案  
 建置方案前，您必須建立 BizTalk 專案、確定其具備強式名稱，並為其指定應用程式名稱。 指定應用程式名稱可避免 BizTalk Server 將方案部署至預設的 BizTalk 應用程式。  
  
##### <a name="to-create-and-configure-a-new-biztalk-project"></a>建立和設定新的 BizTalk 專案  
  
1.  使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立新的 BizTalk 專案。 呼叫專案**BasicXMLEnvelope**。  
  
2.  產生金鑰檔並將其指派給專案。 如需有關這項工作的詳細資訊，請參閱[如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)。  
  
3.  在專案的部署組態屬性，將指派**應用程式名稱**並設定**重新啟動主控件執行個體**至`True`。 設定此旗標係指示主控件清除組件所有已快取的執行個體。  
  
### <a name="create-the-error-schema"></a>建立 Error 結構描述  
 在此步驟中，您要建立 Error 結構描述。 它會定義系統的關鍵訊息。  
  
##### <a name="to-create-the-error-schema"></a>若要建立 Error 結構描述  
  
1.  新增名稱為 "Error" 的結構描述至專案。  
  
2.  變更結構描述目標命名空間**http://BasicXMLEnvelope**。  
  
3.  變更結構描述屬性**Element FormDefault**下**進階**類別**Qualified**。 這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。  
  
4.  重新命名根節點為 "Error"，並建立下列五個子項目 (括號內顯示其個別的類型)：  
  
    -   ID (xs:int)  
  
    -   Type (xs:int)  
  
    -   Priority (xs:string)  
  
    -   Description (xs:string)  
  
    -   ErrorDateTime (xs:string)  
  
     您的結構描述應該如下所示：  
  
     ![已完成的錯誤結構描述](../core/media/error-schema.gif "error_schema")  
  
5.  建立此結構描述的範例訊息。 這會用來確認是否正確處理了信封外部的單一訊息。 下列是範例訊息：  
  
    ```  
    <Error xmlns="http://BasicXMLEnvelope">  
      <ID>1</ID>  
      <Type>5</Type>  
      <Priority>Low</Priority>  
      <Description>Sprocket widget prints reports slowly.</Description>  
      <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
    </Error>  
    ```  
  
     將此訊息儲存到專案目錄中的檔案。  
  
### <a name="create-the-envelope-schema"></a>建立信封結構描述  
 信封包含一或多個錯誤訊息。 在這個基本範例中，信封本身沒有屬性和項目。  
  
##### <a name="to-create-the-envelope-schema"></a>若要建立信封結構描述  
  
1.  新增名稱為 "Envelope" 的結構描述至 BasicXMLEnvelope 專案。  
  
2.  變更的目標命名空間**http://BasicXMLEnvelope**。  
  
3.  將根節點的名稱，由 "Root" 變更為 "Envelope"。  
  
4.  現在將結構描述標示為信封結構描述。 按一下**\<結構描述\>**節點。 在 屬性 窗格中，設定 結構描述參考屬性**信封**至`OK`。  
  
5.  設定**Body XPath**屬性。 若要這樣做，請按一下**信封**節點。 在 屬性 視窗中，按一下省略符號 (**...**) 按鈕**Body XPath**屬性選取**信封**，然後按一下 **確定**。  
  
6.  新增 Any 項目子系至 [Envelope] 節點。 錯誤訊息將會包含在此項目中。 您的結構描述應該如下所示：  
  
     ![已完成的信封結構描述](../core/media/envelope-schema.gif "envelope_schema")  
  
7.  建立包含信封及一或多則範例訊息的範例訊息。 範例訊息如下：  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error>  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
     將此訊息儲存到專案目錄中的檔案。  
  
### <a name="deploy-and-configure-the-send-and-receive-ports"></a>部署並設定傳送埠和接收埠  
 建立結構描述後，您必須編譯並部署專案。 一旦專案部署完成，即可使用「BizTalk Server 管理主控台」設定傳送埠和接收埠。  
  
##### <a name="to-deploy-basicxmlenvelope"></a>若要部署 BasicXMLEnvelope  
  
1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，選擇**部署 basicxmlenvelope** [建置] 功能表。 這會在 BizTalk Server 中建置並部署為應用程式 "BasicXMLEnvelope"。  
  
2.  在 BizTalk Server 管理主控台中，展開 **應用程式**群組可讓您確認**BasicXMLEnvelope**呈現為自訂應用程式。  
  
##### <a name="to-configure-the-receive-port"></a>設定接收埠  
  
1.  使用 Windows 檔案總管底下建立名為"Receive"目錄**BasicXMLEnvelope**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下  **單向接收埠**。  
  
3.  在**接收埠屬性**對話方塊方塊中，設定為"Receive"的連接埠的名稱。  
  
4.  以滑鼠右鍵按一下接收位置，然後**新增**新增接收埠。 將新連接埠命名為 "ReceiveError"。 設定**接收管線**至**XMLReceive**。 如**傳輸類型**，選取**檔案**，然後按一下 **設定**。  
  
5.  選取上面所建立的接收目錄，然後按一下**確定**。 接收埠即設定完成。 按一下**確定**關閉。  
  
##### <a name="to-configure-the-send-port"></a>設定傳送埠  
  
1.  使用 Windows 檔案總管 底下建立名為 「 傳送 」 的目錄**BasicXMLEnvelope**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下  **靜態單向**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，設定 「 傳送 」 的連接埠的名稱。  
  
4.  如**傳輸類型**，選取**檔案**，然後按一下 **設定**。 將目的資料夾設定為您稍早建立的傳送目錄，然後按一下**確定**。  
  
5.  按一下**篩選**並加入單一篩選條件：  
  
    -   BTS。MessageType = = **http://BasicXMLEnvelope#Error**  
  
6.  按一下**確定**完成傳送埠組態。 傳送埠即設定完成。  
  
### <a name="run-the-example"></a>執行範例  
 現在即可開始執行範例。 在使用 BizTalk Server 管理主控台啟動 BasicXMLEnvelope 應用程式後，您應將測試檔案複製到接收位置，然後檢查傳送位置所產生的結果。  
  
##### <a name="to-run-the-basicxmlenvelope-example"></a>若要執行 BasicXMLEnvelope 範例  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**BasicXMLEnvelope**應用程式，然後按一下**啟動**。 這樣就會登錄並啟動傳送埠和接收埠。  
  
2.  將每一個範例檔案拖曳到接收目錄中。 如果使用先前提供的範例，您應該會在處理完成時發現傳送位置中有三則個別的錯誤訊息。  
  
## <a name="extending-the-example"></a>擴充範例  
 您可以擴充這個範例以配合其他需求。 本節說明兩種常見的案例：  
  
-   如果是將錯誤批次放在信封中提交，則解譯中的個別訊息失敗應該不會阻止進一步處理其他未失敗的訊息。  
  
-   這些錯誤應該會按照優先順序，傳送到不同的位置。 高優先順序的訊息會被加速處理，而其他優先順序則透過一般通道處理。  
  
 下列各節會擴充範例以處理這些需求。  
  
### <a name="recoverable-interchange-processing"></a>可復原交換處理  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援可復原交換處理。 藉由使用這項功能，您可以確保訊息批次在解譯中發生失敗時，不會整個批次都失敗，而只限於個別的訊息。  
  
##### <a name="to-configure-the-example-for-recoverable-interchange-processing"></a>若要設定可復原交換處理的範例。  
  
1.  在 BizTalk Server 管理主控台中，展開  **BasicXMLEnvelope**應用程式中，按一下 **接收埠**，然後按兩下 接收埠。 這是您先前建立的連接埠。  
  
2.  在**接收埠屬性**對話方塊中，按一下 **接收位置**。 按一下**屬性**啟動**ReceiveError 接收位置屬性** 對話方塊。 按一下省略符號 (**...**) 按鈕**接收管線**。  
  
3.  中**設定管線-XMLReceive** ] 對話方塊中，將**可復原交換處理**屬性`True`，然後按一下 [**確定**。  
  
4.  按一下**確定**關閉**接收位置屬性**對話方塊，然後按一下**[確定]**關閉**接收埠屬性**對話方塊方塊。  
  
##### <a name="to-create-a-sample-file-and-run-the-example"></a>若要建立範例檔案，然後執行範例  
  
1.  若要建立範例檔案，請產生範例中所建立之信封範例檔案的複本、將不存在的命名空間加入至其中一個 Error 執行個體，然後儲存檔案：  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails to return any sprockets even though some exist</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error xmlns="http://ThisIsAnError">  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
2.  在 BizTalk Server 管理主控台中，按一下 **應用程式**並確認**BasicXMLEnvelope**應用程式正在執行。  
  
3.  將訊息拖曳到接收位置中。 處理之後，您應該會發現傳送位置中有第一個訊息，而第二個 (低優先順序) 訊息則是在擱置佇列中。  
  
### <a name="content-based-routing-cbr"></a>以內容為基礎的路由 (CBR)  
 您可以使用以內容為基礎的路由，根據訊息的內容來傳送路由訊息。 在此案例中，路由會根據優先順序進行，「高」優先順序訊息會進入一個傳送位置，而「低」和「中」優先順序訊息則進入不同的傳送位置。  
  
 若要擴充範例，您必須完成下列工作：  
  
1.  升級**優先順序**BasicXMLEnvelope 專案中 Error 結構描述中的欄位。 以內容為基礎的路由需要升級的屬性才能路由傳送訊息。 如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。  
  
2.  建立和設定兩個額外的傳送埠。 這些連接埠會使用篩選條件來確保收到適當的訊息。  
  
##### <a name="to-promote-the-priority-field-in-the-error-schema"></a>升級 Error 結構描述中的 Priority 欄位  
  
1.  與**BasicXMLEnvelope**中開啟專案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**錯誤**結構描述並展開**錯誤**節點。  
  
2.  以滑鼠右鍵按一下**優先順序**項目，指向**升階**，然後按一下 **快速升級**。  
  
3.  按一下**確定**以確認要升級屬性的新屬性結構描述。  
  
4.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，開啟 新增屬性結構描述 propertyschema.xsd 結構描述。 從結構描述中移除"Field1"。  
  
5.  現在，重新編譯並重新部署方案。 在 [建置] 功能表中，選擇 [部署 BasicXMLEnvelope]。  
  
6.  此專案已設定為要在重新部署方案時重設主控件執行個體。 如果您變更了這個設定，就必須先停止再啟動主控件。  
  
##### <a name="to-configure-the-low-and-medium-priority-send-port"></a>設定低和中等優先順序的傳送埠  
  
1.  使用 Windows 檔案總管底下建立名為"SendLowMediumPriority"目錄**BasicXMLEnvelope**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下  **靜態單向**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，設定為"SendLowMediumPriority"的連接埠的名稱。  
  
4.  如**傳輸類型**，選取**檔案**，然後按一下 **設定**。 將目的資料夾設定為剛才建立的目錄。 按一下**確定**關閉。  
  
5.  按一下**篩選**並加入三個篩選條件運算式：  
  
    -   BTS.MessageType == http://BasicXMLEnvelope#Error And  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == Low Or  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == Medium  
  
6.  按一下**確定**以完成低和中等優先順序的傳送埠設定。  
  
##### <a name="to-configure-the-high-priority-send-port"></a>設定高優先順序的傳送埠  
  
1.  使用 Windows 檔案總管底下建立名為"SendHighPriority"目錄**BasicXMLEnvelope**專案目錄。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下  **靜態單向**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，設定為"SendHighPriority"的連接埠的名稱。  
  
4.  如**傳輸類型**，選取**檔案**，然後按一下 **設定**。 將目的資料夾設定為剛才建立的目錄。 按一下**確定**關閉。  
  
5.  按一下**篩選**並加入兩個篩選條件運算式：  
  
    -   BTS.MessageType == http://BasicXMLEnvelope#Error And  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == High  
  
6.  按一下**確定**以完成高優先順序的傳送埠設定。  
  
##### <a name="to-test-the-routing-solution"></a>測試路由方案  
  
1.  在 BizTalk Server 管理主控台中，展開 **應用程式**群組中，以滑鼠右鍵按一下**BasicXMLEnvelope**應用程式，，然後按一下**啟動**。 當提示確認，請按一下 **啟動**。 這樣就會登錄新的傳送埠。  
  
2.  將測試訊息拖曳到接收位置中。 請注意錯誤訊息是如何路由傳送至不同的傳送位置：  
  
    -   具有「低」、「中」或「高」優先順序，且順利通過訊息處理的錯誤訊息，會路由傳送至原始傳送位置 (基本範例中所設定的) 及依優先順序區分的傳送位置。 如果是具有「低」或「中」優先順序的訊息，原始傳送位置及「低/中」傳送位置內都會出現其複本。  
  
    -   如果已啟用可復原交換處理，失敗的錯誤訊息就不會路由，並如預期般，將正確路由 nonfailed 的訊息。 之所以不會傳送失敗訊息，是因為其訊息類型與篩選條件中使用的類型不相符。  
  
## <a name="see-also"></a>請參閱  
 [可復原交換處理](../core/recoverable-interchange-processing.md)   
 [升級屬性](../core/promoting-properties.md)   
 [CBRSample (BizTalk Server 範例)](../core/cbrsample-biztalk-server-sample.md)