---
title: "步驟 4： 實作中繼資料瀏覽的處理常式回應配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31fc6c1-e4b5-4529-ba3e-2a8cfb8ece1c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f93b4efeb65092c4ca61ab1fc2ef58a0ac53ae4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a>步驟 4： 回應配接器實作中繼資料瀏覽的處理常式
![步驟 4 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 **若要完成的時間：** 45 分鐘的時間  
  
 在此步驟中，您可以實作回應配接器的瀏覽功能。 這項功能可讓您的配接器執行連線為基礎的瀏覽至目標系統從取得中繼資料。 不論您的配接器的功能，您的配接器必須支援的瀏覽功能。  
  
 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援瀏覽功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 回應配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]呼叫 EchoAdapterMetadataBrowseHandler 的衍生的類別會自動產生。  
  
 在下列步驟中，您可以更新這個類別，以深入了解如何實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法時，如何設定各種屬性`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，以及作業和配接器所支援的類別目錄節點中如何顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，您必須已順利完成[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。 您也必須了解下列類別：  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a>IMetadataBrowseHandler 介面  
 `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面定義為：  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的方法參數。 參數定義`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法詳述於下表。  
  
> [!NOTE]
>  回應配接器實作會使用節點識別碼，並會忽略的三個參數，因為回應配接器支援只在少數節點。  
  
|**參數**|**定義**|  
|-------------------|--------------------|  
|節點識別碼|在 [中繼資料總管] 階層中的每個項目 ([!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和<br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]) 有節點識別碼。 每個節點識別碼必須是唯一的而且可以是類別或作業。 類別可以有子類別。 **注意：**如果 null 或空字串 ("")，從根節點 （"/"） 根據預設，會擷取作業。|  
|childStartIndex|要傳回的第一個子系的索引。<br /><br /> 不支援回應配接器。|  
|maxChildNodes|要傳回的結果節點數目上限。 您可以使用 Int32.Max 來擷取結果的所有節點。<br /><br /> 不支援回應配接器。|  
|timeout|允許的作業完成的時間上限。<br /><br /> 不支援回應配接器。|  
  
 當實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法，您必須將每個類別目錄和作業的節點加入陣列的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 若要指定的節點做為類別目錄，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`false`。 若要為作業指定的節點，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`true`。  
  
## <a name="echo-adapter-metadata-browse"></a>回應配接器中繼資料瀏覽  
 根據目標系統的類別和作業，會有許多方法可建立的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 作業和您選擇的類別應該代表您想要公開的作業。 但是回應配接器，它只會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`所列出的每個下列的節點，節點識別碼的物件：  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 EchoMainCategory 是根節點 （"/"） 下的類別目錄節點。 此節點也使用做為類別目錄的傳入和傳出作業。 因此，當建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`該分類中，您可以執行下列物件：  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 例如 Echo/EchoString 屬於 EchoMainCategory 輸出作業中，您可以執行下列作業：  
  
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
  
 用於將輸入 Echo/OnReceiveEcho EchoMainCategory 屬於這類作業，您可以執行下列作業：  
  
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
  
 當[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具瀏覽回應配接器中繼資料，根據預設，它會從根節點 （"/"） 開始。  
  
 下圖顯示 EchoMainCategory 節點之下的根節點 （"/"）：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
 若要瀏覽中的三個輸出的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**選項。 您會看到這些作業在**可用的類別和作業**清單方塊中，如下所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")  
  
 在上圖中，注意`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`值會出現在**名稱**資料行**可用的類別和作業**清單方塊。 參數傳遞至`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`建構函式會出現在**節點識別碼**資料行**可用的類別和作業**清單方塊中，而`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A`值會顯示為工具提示當您以滑鼠右鍵按一下包含描述， `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`。  
  
 若要查看在輸入的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具**選取合約型別**下拉式清單中選取**服務 （輸入操作）**選項。 您會看到中的輸入的 OnReceiveEcho 作業**可用的類別和作業**清單方塊中，如下圖所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")  
  
## <a name="implementing-the-imetadatabrowsehandler"></a>實作 IMetadataBrowseHandler  
 在此步驟中，您可以更新 EchoAdapterMetadataBrowseHandler 類別來實作回應配接器的中繼資料瀏覽，也就是，以實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每個類別目錄和作業的物件，設定適當的值，該物件，然後傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別和作業的物件。 請注意，當您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，您要傳入的節點識別碼，而不是顯示名稱。  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a>若要更新 EchoAdapterMetadataBrowseHandler 類別  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterMetadataBrowseHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。  
  
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
  
6.  繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 的物件。  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`回應的物件 / EchoGreetingFromFile。  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  繼續加入下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件或如果沒有符合項目為 null。  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. 在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
10. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 您應該成功建置專案。 如果沒有，請確定您已依照上述每個步驟。  
  
> [!NOTE]
>  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 5： 回應配接器實作中繼資料的搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 您只實作中繼資料瀏覽回應配接器的功能，藉由實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`分類中，物件，並再當成陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。 在您建立的每個作業，`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，然後再傳回所有這些物件的陣列中`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`。  
  
## <a name="next-steps"></a>後續步驟  
 您可以實作中繼資料的搜尋和解析功能，以及輸出的訊息交換。 最後，您會建置並部署回應配接器。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)   
 [步驟 5： 回應配接器實作的中繼資料搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)