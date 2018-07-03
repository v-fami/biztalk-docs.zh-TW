---
title: 步驟 4： 實作 Echo 配接器中繼資料瀏覽處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d31fc6c1-e4b5-4529-ba3e-2a8cfb8ece1c
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c50110fff32b81bdaa429a479cefe8041d919356
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003415"
---
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a>步驟 4： 實作 Echo 配接器中繼資料瀏覽處理常式
![步驟 4 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 **若要完成的時間：** 45 分鐘的時間  
  
 在此步驟中，您可以實作 Echo 配接器的瀏覽功能。 這項功能可讓您的配接器進行連接為基礎的瀏覽 從目標系統中取得中繼資料。 不論您的配接器的功能，您的配接器必須支援的瀏覽功能。  
  
 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，以支援瀏覽功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 Echo 配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生呼叫 EchoAdapterMetadataBrowseHandler 的衍生的類別。  
  
 在下列步驟中，您會更新這個類別，以進一步了解如何實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法，如何設定各種屬性`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，而中顯示的作業與配接器所支援的類別目錄節點的方式[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，您必須先成功完成[步驟 3： 實作 Echo 配接器連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。 您也必須了解下列類別：  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a>IMetadataBrowseHandler 介面  
 `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面定義如下：  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的方法參數。 參數定義`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法詳述於下表。  
  
> [!NOTE]
>  Echo 配接器實作會使用節點識別碼，並忽略的三個參數，因為 Echo 配接器支援只有少數的節點。  
  
|  **參數**  |                                                                                                                                                                                                                               **定義**                                                                                                                                                                                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     nodeId      | 在 [中繼資料總管] 階層中的每個項目 ([!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和<br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]) 有節點識別碼。 每個節點的識別碼必須是唯一的而且可以是類別或作業。 類別可以有子類別。 **注意：** 如果 null 或空字串 ("")，從根節點 （"/"） 依預設，會擷取作業。 |
| childStartIndex |                                                                                                                                                                                           要傳回的第一個子系的索引。<br /><br /> 不支援 Echo 配接器。                                                                                                                                                                                            |
|  maxChildNodes  |                                                                                                                                                                  要傳回的結果節點的數目上限。 您可以使用 Int32.Max 來擷取結果的所有節點。<br /><br /> 不支援 Echo 配接器。                                                                                                                                                                   |
|     timeout     |                                                                                                                                                                                   若要完成此作業所允許的時間上限。<br /><br /> 不支援 Echo 配接器。                                                                                                                                                                                    |
  
 實作時`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法中，您必須將每個類別目錄和作業的節點的陣列加入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 若要指定節點做為類別目錄，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`false`。 若要指定作業的節點，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`true`。  
  
## <a name="echo-adapter-metadata-browse"></a>Echo 配接器中繼資料瀏覽  
 根據目標系統的類別和作業，有許多種方法，來建置的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 作業和您選擇的類別目錄應該代表您想要公開的作業。 但 Echo 配接器，它只會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`列出物件給每個有節點識別碼的下列節點：  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 EchoMainCategory 是 （"/"） 中的 [根] 節點下的 [類別目錄] 節點。 此節點也會做為類別目錄的輸入和輸出作業。 因此，當建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件給該分類中，您可以執行下列動作：  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 例如 Echo/EchoString 屬於 EchoMainCategory 輸出作業，您可以執行下列作業：  
  
```  
if( "EchoMainCategory".CompareTo(nodeId) == 0 ) //category is EchoMainCategory  
      {  
          // Outbound operations  
          MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
          outOpNode1.DisplayName = "EchoStrings";  
          outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
          outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
          outOpNode1.IsOperation = true;  
```  
  
 例如 Echo/OnReceiveEcho 屬於 EchoMainCategory 為輸入的作業，您可以執行下列作業：  
  
```  
  if( "EchoMainCategory".CompareTo(nodeId) == 0 ) //category is EchoMainCategory  
        {             
// Inbound operations  
            MetadataRetrievalNode inOpNode1 = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
            inOpNode1.DisplayName = "OnReceiveEcho";  
            inOpNode1.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
            inOpNode1.Direction = MetadataRetrievalNodeDirections.Inbound;  
            inOpNode1.IsOperation = true;  
```  
  
 當[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具探索 Echo 配接器中繼資料，根據預設，它會從 （"/"） 的根節點開始。  
  
 下圖顯示 EchoMainCategory 節點之下的根節點 （"/"）：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
 若要瀏覽中的三個輸出的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）** 選項。 您會看到在這些作業**可用的類別和作業**清單方塊中，如下所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")  
  
 在上圖中，注意`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`值會出現在**名稱**資料行**可用的類別和作業**清單方塊。 參數傳遞至`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`建構函式會出現在**節點識別碼**資料行**可用的類別和作業**清單方塊中，而`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A`值會顯示為工具提示當您以滑鼠右鍵按一下包含描述， `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`。  
  
 若要查看輸入的作業，在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約的型別**下拉式清單中，選取**服務 （輸入作業）** 選項。 請參閱中的輸入的 OnReceiveEcho 作業**可用的類別和作業**清單方塊中，如下圖所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")  
  
## <a name="implementing-the-imetadatabrowsehandler"></a>實作 IMetadataBrowseHandler  
 在此步驟中，您會更新 EchoAdapterMetadataBrowseHandler 類別來實作 Echo 配接器中繼資料瀏覽，也就是，以實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每個類別目錄和作業物件，設定適當的值，該物件，則傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別和作業的物件。 請記住，當您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，您需要將節點識別碼，而不是顯示名稱。  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a>若要更新 EchoAdapterMetadataBrowseHandler 類別  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterMetadataBrowseHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何地方在編輯器中，在內容功能表中，指向**大綱**，然後按一下**取消大綱**。  
  
3.  在 Visual Studio 編輯器中，內部**瀏覽**方法，以建立下列內容取代現有的邏輯`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`EchoMainCategory 的物件。  
  
    ```csharp  
    if (MetadataRetrievalNode.Root.NodeId.Equals(nodeId))  
    {  
        MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
        node.DisplayName = "Main Category";  
        node.IsOperation = false;  
        node.Description = "This category contains inbound and outbound categories.";  
        node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound;  
        return new MetadataRetrievalNode[] { node };  
    }  
    ```  
  
4.  繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 的物件。  
  
    ```csharp  
    if( "EchoMainCategory".CompareTo(nodeId) == 0 )  
    {  
        // Inbound operations  
        MetadataRetrievalNode inOpNode1 = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
        inOpNode1.DisplayName = "OnReceiveEcho";  
        inOpNode1.Description = "This operation echos the location and length of a file dropped in the specified file system.";  
        inOpNode1.Direction = MetadataRetrievalNodeDirections.Inbound;  
        inOpNode1.IsOperation = true;  
    ```  
  
5.  繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 的物件。  
  
    ```csharp  
    // Outbound operations  
    MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
    outOpNode1.DisplayName = "EchoStrings";  
    outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
    outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode1.IsOperation = true;  
    ```  
  
6.  繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 的物件。  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo 物件 / EchoGreetingFromFile。  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  繼續新增下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件或 null，如果不相符。  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. 在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。  
  
10. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 您應該已成功建置專案。 如果沒有，請確定您已遵循上述每個步驟。  
  
> [!NOTE]
>  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio，或移至下一個步驟中，[步驟 5： 實作 Echo 配接器中繼資料搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您只會實作中繼資料瀏覽的 Echo 配接器的功能，藉由實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別物件，並再次為陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 在您建立的每個作業，`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，然後再傳回陣列中的 所有這些物件`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`。  
  
## <a name="next-steps"></a>後續步驟  
 您會實作中繼資料搜尋和解析功能，以及輸出的訊息交換。 最後，您會建置並部署 Echo 配接器。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [步驟 3： 實作 Echo 配接器的連接](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)   
 [步驟 5：實作 Echo 配接器的中繼資料搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)