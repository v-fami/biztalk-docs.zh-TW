---
title: "步驟 5： 回應配接器實作的中繼資料搜尋處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a133a99-1d6c-4634-b928-0f4f23c6f6e4
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d241499e10a944eb1941b680bc73b97ce6ffd93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a>步驟 5： 回應配接器實作的中繼資料搜尋處理常式
![步驟 5 之 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 **若要完成的時間：** 30 分鐘  
  
 在此步驟的教學課程中，您可以實作回應配接器的搜尋功能。 不同於瀏覽，搜尋是選擇性的。 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援搜尋功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 回應配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]自動產生一個稱為 EchoAdapterMetadataSearchHandler 的衍生的類別。  
  
 您第一次更新 EchoAdapterMetadataSearchHandler 類別，以取得更深入了解如何實作這個介面，如何填入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，以及如何搜尋結果顯示在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，請先完成[步驟 4： 實作回應配接器中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。 您也必須清楚了解有關的下列類別：  
  
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
  
 `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的搜尋準則。 下表中說明的搜尋方法的參數定義：  
  
|**參數**|**定義**|  
|-------------------|--------------------|  
|節點識別碼|若要開始搜尋的節點識別碼。 如果 null 或空字串 ("")，作業將會擷取從根節點 （"/"）。|  
|searchCriteria|搜尋準則，是針對配接器。 如果未不指定任何搜尋準則，配接器應傳回的所有節點。|  
|maxChildNodes|要傳回的結果節點數目上限。 您可以使用 Int32.Max 來擷取結果的所有節點。<br /><br /> 不支援回應配接器。|  
|timeout|允許的作業完成的時間上限。<br /><br /> 不支援回應配接器。|  
  
 搜尋結果，您的配接器可以選擇傳回分類節點或運算節點，或兩者。 最多的搜尋功能的類型是您的配接器支援。  
  
## <a name="echo-adapter-metadata-search"></a>回應配接器中繼資料的搜尋  
 根據目標系統的類別和作業，會有許多方法可建立的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`来傳回的物件。 回應配接器實作搜尋功能的方法是瀏覽每項作業，其下面清單中的節點識別碼：  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
-   如果節點識別碼，然後符合搜尋準則，它會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件使用的作業，節點識別碼，然後將指定的屬性值。 例如，  
  
    ```  
    MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
    nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
    nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
    nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
    nodeInbound.IsOperation = true;  //It is an operation, not category.  
    ```  
  
-   然後將物件加入至集合的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s，例如，  
  
    ```  
    resultList.Add(nodeInbound);  
    ```  
  
-   最後傳回的集合陣列格式。  
  
    ```  
    return resultList.ToArray();  
    ```  
  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具執行連線為基礎的搜尋可用的作業。 例如，如下圖所示的搜尋準則時將字串**問候語**，搜尋會傳回**EchoGreetings**和**EchoGreetingFromFile**作業。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")  
  
 如果找到相符項目，其中任何一個工具就會傳回錯誤訊息，如下圖所示。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")  
  
## <a name="implementing-the-imetadatasearchhandler"></a>實作 IMetadataSearchHandler  
 您將實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 如果作業的顯示名稱符合搜尋準則，您將建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件該作業，並再將該物件加入至陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a>若要更新 EchoAdapterMetadataSearchHandler 類別  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterMetadataSearchHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，內部**搜尋**方法，以下列取代現有的邏輯。 此邏輯會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 是否符合指定的搜尋準則的物件。  
  
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
  
5.  繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetingFromFile 是否符合指定的搜尋準則的物件。  
  
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
  
6.  繼續加入下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
8.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 您應該成功編譯專案。 如果沒有，請確定您已依照上述每個步驟。  
  
    > [!NOTE]
    >  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 6： 實作回應配接器中繼資料解析的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 您只實作搜尋功能的回應配接器，藉由實作的中繼資料`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。 具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件符合準則，則傳回陣列的每個作業`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。  
  
## <a name="next-steps"></a>後續步驟  
 您將實作中繼資料解析功能，以及在傳出和傳入的訊息交換功能。 最後，您將建置和部署回應配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 回應配接器實作中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)   
 [步驟 6： 實作回應配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)   
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)