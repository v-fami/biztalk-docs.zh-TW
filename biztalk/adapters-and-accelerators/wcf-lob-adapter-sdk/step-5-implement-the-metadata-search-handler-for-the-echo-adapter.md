---
title: 步驟 5： 實作 Echo 配接器中繼資料搜尋處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a133a99-1d6c-4634-b928-0f4f23c6f6e4
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29768fa47fd26f32308d517f175d906ec088ff7b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004087"
---
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a>步驟 5： 實作 Echo 配接器中繼資料搜尋處理常式
![步驟 5 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 **若要完成的時間：** 30 分鐘  
  
 在此步驟的教學課程中，您可以實作 Echo 配接器的搜尋功能。 不同於瀏覽，搜尋是選擇性的。 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援搜尋功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 Echo 配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生一個衍生的類別，稱為 EchoAdapterMetadataSearchHandler。  
  
 您第一次更新 EchoAdapterMetadataSearchHandler 類別以進一步了解如何實作這個介面，如何以填入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，並搜尋結果會出現在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，請先完成[步驟 4： 實作 Echo 配接器的中繼資料瀏覽處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。 您也必須清楚了解關於下列類別：  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
## <a name="the-imetadatasearchhandler-interface"></a>IMetadataSearchHandler 介面  
 `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`定義為：  
  
```  
public interface IMetadataSearchHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Search(string nodeId, string searchCriteria, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的搜尋準則。 下表中詳述的搜尋方法的參數定義：  
  
|**參數**|**定義**|  
|-------------------|--------------------|  
|nodeId|節點識別碼，做為搜尋起點。 如果 null 或空字串 ("")，作業將會擷取從根節點 （"/"）。|  
|searchCriteria|搜尋準則，也就是配接器特有。 如果未不指定任何搜尋準則，則配接器應該傳回所有節點。|  
|maxChildNodes|要傳回的結果節點的數目上限。 您可以使用 Int32.Max 來擷取結果的所有節點。<br /><br /> 不支援 Echo 配接器。|  
|timeout|若要完成此作業所允許的時間上限。<br /><br /> 不支援 Echo 配接器。|  
  
 搜尋結果中，您的配接器可以選擇傳回分類節點或運算節點，或這兩者。 是由搜尋功能的型別配接器支援。  
  
## <a name="echo-adapter-metadata-search"></a>Echo 配接器中繼資料搜尋  
 根據目標系統的類別和作業，有許多種方法，來建置的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`来傳回的物件。 Echo 配接器實作搜尋功能的方式是瀏覽其節點識別碼，下列清單中的每一項作業：  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
- 如果節點識別碼，然後在符合搜尋條件，它會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件使用之作業中，節點識別碼，然後將指派值的屬性。 例如，  
  
  ```  
  MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
  nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
  nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
  nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
  nodeInbound.IsOperation = true;  //It is an operation, not category.  
  ```  
  
- 然後將物件加入至集合的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s，比方說，  
  
  ```  
  resultList.Add(nodeInbound);  
  ```  
  
- 以陣列格式，最後傳回的集合。  
  
  ```  
  return resultList.ToArray();  
  ```  
  
  您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具執行連接為基礎的搜尋可用的作業。 比方說下, 圖顯示的搜尋準則時將字串**問候語**，則搜尋會傳回**EchoGreetings**並**EchoGreetingFromFile**作業。  
  
  ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")  
  
  如果找到相符項目，則任何一項工具會傳回如下圖所示的錯誤訊息。  
  
  ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")  
  
## <a name="implementing-the-imetadatasearchhandler"></a>實作 IMetadataSearchHandler  
 您將實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 如果作業的顯示名稱符合搜尋準則，您會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`該作業中，物件，並再將該物件加入至陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a>若要更新 EchoAdapterMetadataSearchHandler 類別  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterMetadataSearchHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，內部**搜尋**方法，以下列內容取代現有的邏輯。 此邏輯會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 是否符合指定的搜尋準則的物件。  
  
    ```csharp  
    List<MetadataRetrievalNode> resultList = new List<MetadataRetrievalNode>();  
    if ("OnReceiveEcho".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
        nodeInbound.DisplayName = "OnReceiveEcho";  
        nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
        nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;  
        nodeInbound.IsOperation = true;  
        resultList.Add(nodeInbound);  
    }  
    ```  
  
3.  繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 是否符合指定的搜尋準則的物件。  
  
    ```csharp  
    if ("EchoStrings".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
        outOpNode1.DisplayName = "EchoStrings";  
        outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
        outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
        outOpNode1.IsOperation = true;  
        resultList.Add(outOpNode1);  
    }  
    ```  
  
4.  繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 是否符合指定的搜尋準則的物件。  
  
    ```csharp  
    if ("EchoGreetings".ToLower().Contains(searchCriteria.ToLower()))  
        {  
            MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
            outOpNode2.DisplayName = "EchoGreetings";  
            outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
            outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
            outOpNode2.IsOperation = true;  
            resultList.Add(outOpNode2);  
        }  
    ```  
  
5.  繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetingFromFile 是否符合指定的搜尋準則的物件。  
  
    ```csharp  
    if ("EchoCustomGreetingFromFile".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
        outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
        outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
        outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
        outOpNode3.IsOperation = true;  
        resultList.Add(outOpNode3);  
    }  
    ```  
  
6.  繼續新增下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。  
  
8.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 您應該已成功編譯專案。 如果沒有，請確定您已遵循上述每個步驟。  
  
    > [!NOTE]
    >  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio，或移至下一個步驟中，[步驟 6： 實作 Echo 配接器的中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您只實作搜尋功能的 Echo 配接器，藉由實作的中繼資料`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每項作業符合準則，則傳回的陣列物件`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
## <a name="next-steps"></a>後續步驟  
 您會實作中繼資料解析功能，以及在傳出和傳入的訊息交換功能。 最後，您會建置並部署 Echo 配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 實作 Echo 配接器中繼資料瀏覽處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)   
 [步驟 6： 實作 Echo 配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)   
 [教學課程 1：開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)