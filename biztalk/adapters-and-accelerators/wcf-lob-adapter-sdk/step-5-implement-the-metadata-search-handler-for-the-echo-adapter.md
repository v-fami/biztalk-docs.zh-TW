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
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a><span data-ttu-id="cf921-102">步驟 5： 實作 Echo 配接器中繼資料搜尋處理常式</span><span class="sxs-lookup"><span data-stu-id="cf921-102">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>
<span data-ttu-id="cf921-103">![步驟 5 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span><span class="sxs-lookup"><span data-stu-id="cf921-103">![Step 5 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span></span>  
  
 <span data-ttu-id="cf921-104">**若要完成的時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="cf921-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="cf921-105">在此步驟的教學課程中，您可以實作 Echo 配接器的搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="cf921-105">In this step of the tutorial, you implement the search capability of the Echo adapter.</span></span> <span data-ttu-id="cf921-106">不同於瀏覽，搜尋是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="cf921-106">Unlike browse, search is optional.</span></span> <span data-ttu-id="cf921-107">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援搜尋功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="cf921-107">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support search capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="cf921-108">Echo 配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生一個衍生的類別，稱為 EchoAdapterMetadataSearchHandler。</span><span class="sxs-lookup"><span data-stu-id="cf921-108">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates one derived class called EchoAdapterMetadataSearchHandler.</span></span>  
  
 <span data-ttu-id="cf921-109">您第一次更新 EchoAdapterMetadataSearchHandler 類別以進一步了解如何實作這個介面，如何以填入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，並搜尋結果會出現在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="cf921-109">You first update the EchoAdapterMetadataSearchHandler class to get a better understanding of how to implement this interface, how to populate  `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the search results appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cf921-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="cf921-110">Prerequisites</span></span>  
 <span data-ttu-id="cf921-111">在開始此步驟之前，請先完成[步驟 4： 實作 Echo 配接器的中繼資料瀏覽處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cf921-111">Before you begin this step, complete [Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="cf921-112">您也必須清楚了解關於下列類別：</span><span class="sxs-lookup"><span data-stu-id="cf921-112">You must also have a clear understanding about the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
## <a name="the-imetadatasearchhandler-interface"></a><span data-ttu-id="cf921-113">IMetadataSearchHandler 介面</span><span class="sxs-lookup"><span data-stu-id="cf921-113">The IMetadataSearchHandler Interface</span></span>  
 <span data-ttu-id="cf921-114">`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`定義為：</span><span class="sxs-lookup"><span data-stu-id="cf921-114">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` is defined as:</span></span>  
  
```  
public interface IMetadataSearchHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Search(string nodeId, string searchCriteria, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="cf921-115">`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="cf921-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the search criteria.</span></span> <span data-ttu-id="cf921-116">下表中詳述的搜尋方法的參數定義：</span><span class="sxs-lookup"><span data-stu-id="cf921-116">The parameter definitions for the Search method are described in the following table:</span></span>  
  
|<span data-ttu-id="cf921-117">**參數**</span><span class="sxs-lookup"><span data-stu-id="cf921-117">**Parameter**</span></span>|<span data-ttu-id="cf921-118">**定義**</span><span class="sxs-lookup"><span data-stu-id="cf921-118">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="cf921-119">nodeId</span><span class="sxs-lookup"><span data-stu-id="cf921-119">nodeId</span></span>|<span data-ttu-id="cf921-120">節點識別碼，做為搜尋起點。</span><span class="sxs-lookup"><span data-stu-id="cf921-120">The node ID to start searching from.</span></span> <span data-ttu-id="cf921-121">如果 null 或空字串 ("")，作業將會擷取從根節點 （"/"）。</span><span class="sxs-lookup"><span data-stu-id="cf921-121">If null or an empty string (""), operations will be retrieved from the root node ("/").</span></span>|  
|<span data-ttu-id="cf921-122">searchCriteria</span><span class="sxs-lookup"><span data-stu-id="cf921-122">searchCriteria</span></span>|<span data-ttu-id="cf921-123">搜尋準則，也就是配接器特有。</span><span class="sxs-lookup"><span data-stu-id="cf921-123">The search criteria, which is adapter-specific.</span></span> <span data-ttu-id="cf921-124">如果未不指定任何搜尋準則，則配接器應該傳回所有節點。</span><span class="sxs-lookup"><span data-stu-id="cf921-124">If no search criteria are specified, the adapter should return all nodes.</span></span>|  
|<span data-ttu-id="cf921-125">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="cf921-125">maxChildNodes</span></span>|<span data-ttu-id="cf921-126">要傳回的結果節點的數目上限。</span><span class="sxs-lookup"><span data-stu-id="cf921-126">The maximum number of result nodes to return.</span></span> <span data-ttu-id="cf921-127">您可以使用 Int32.Max 來擷取結果的所有節點。</span><span class="sxs-lookup"><span data-stu-id="cf921-127">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="cf921-128">不支援 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="cf921-128">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="cf921-129">timeout</span><span class="sxs-lookup"><span data-stu-id="cf921-129">timeout</span></span>|<span data-ttu-id="cf921-130">若要完成此作業所允許的時間上限。</span><span class="sxs-lookup"><span data-stu-id="cf921-130">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="cf921-131">不支援 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="cf921-131">Not supported by the Echo adapter.</span></span>|  
  
 <span data-ttu-id="cf921-132">搜尋結果中，您的配接器可以選擇傳回分類節點或運算節點，或這兩者。</span><span class="sxs-lookup"><span data-stu-id="cf921-132">For search result, your adapter can choose to return either category nodes or operation nodes, or both.</span></span> <span data-ttu-id="cf921-133">是由搜尋功能的型別配接器支援。</span><span class="sxs-lookup"><span data-stu-id="cf921-133">It is up to the type of search feature your adapter supports.</span></span>  
  
## <a name="echo-adapter-metadata-search"></a><span data-ttu-id="cf921-134">Echo 配接器中繼資料搜尋</span><span class="sxs-lookup"><span data-stu-id="cf921-134">Echo adapter Metadata Search</span></span>  
 <span data-ttu-id="cf921-135">根據目標系統的類別和作業，有許多種方法，來建置的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`来傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-135">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects to return.</span></span> <span data-ttu-id="cf921-136">Echo 配接器實作搜尋功能的方式是瀏覽其節點識別碼，下列清單中的每一項作業：</span><span class="sxs-lookup"><span data-stu-id="cf921-136">The way Echo adapter implements the search functionality is to go through every operation with its node ID in the following list:</span></span>  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
- <span data-ttu-id="cf921-137">如果節點識別碼，然後在符合搜尋條件，它會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件使用之作業中，節點識別碼，然後將指派值的屬性。</span><span class="sxs-lookup"><span data-stu-id="cf921-137">If the node ID then matches the search criteria, it creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object using the node ID of the operation, and then assigns the properties with values.</span></span> <span data-ttu-id="cf921-138">例如，</span><span class="sxs-lookup"><span data-stu-id="cf921-138">For example,</span></span>  
  
  ```  
  MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
  nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
  nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
  nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
  nodeInbound.IsOperation = true;  //It is an operation, not category.  
  ```  
  
- <span data-ttu-id="cf921-139">然後將物件加入至集合的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s，比方說，</span><span class="sxs-lookup"><span data-stu-id="cf921-139">And then add the object to a collection of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s, for example,</span></span>  
  
  ```  
  resultList.Add(nodeInbound);  
  ```  
  
- <span data-ttu-id="cf921-140">以陣列格式，最後傳回的集合。</span><span class="sxs-lookup"><span data-stu-id="cf921-140">Lastly returns the collection in an array format.</span></span>  
  
  ```  
  return resultList.ToArray();  
  ```  
  
  <span data-ttu-id="cf921-141">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具執行連接為基礎的搜尋可用的作業。</span><span class="sxs-lookup"><span data-stu-id="cf921-141">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools to perform a connection-based search for the available operations.</span></span> <span data-ttu-id="cf921-142">比方說下, 圖顯示的搜尋準則時將字串**問候語**，則搜尋會傳回**EchoGreetings**並**EchoGreetingFromFile**作業。</span><span class="sxs-lookup"><span data-stu-id="cf921-142">For example, the following figure shows that when the searching criteria is the string **Greeting**, the search returns the **EchoGreetings** and **EchoGreetingFromFile** operations.</span></span>  
  
  <span data-ttu-id="cf921-143">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")</span><span class="sxs-lookup"><span data-stu-id="cf921-143">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")</span></span>  
  
  <span data-ttu-id="cf921-144">如果找到相符項目，則任何一項工具會傳回如下圖所示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cf921-144">If no match is found, either tool will return the error message shown in the following figure.</span></span>  
  
  <span data-ttu-id="cf921-145">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")</span><span class="sxs-lookup"><span data-stu-id="cf921-145">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")</span></span>  
  
## <a name="implementing-the-imetadatasearchhandler"></a><span data-ttu-id="cf921-146">實作 IMetadataSearchHandler</span><span class="sxs-lookup"><span data-stu-id="cf921-146">Implementing the IMetadataSearchHandler</span></span>  
 <span data-ttu-id="cf921-147">您將實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="cf921-147">You will implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="cf921-148">如果作業的顯示名稱符合搜尋準則，您會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`該作業中，物件，並再將該物件加入至陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-148">If the operation's display name matches the search criteria, you will create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that operation, and then add that object to an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a><span data-ttu-id="cf921-149">若要更新 EchoAdapterMetadataSearchHandler 類別</span><span class="sxs-lookup"><span data-stu-id="cf921-149">To update the EchoAdapterMetadataSearchHandler class</span></span>  
  
1.  <span data-ttu-id="cf921-150">在 [方案總管] 中，按兩下**EchoAdapterMetadataSearchHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="cf921-150">In Solution Explorer, double-click the **EchoAdapterMetadataSearchHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="cf921-151">在 Visual Studio 編輯器中，內部**搜尋**方法，以下列內容取代現有的邏輯。</span><span class="sxs-lookup"><span data-stu-id="cf921-151">In the Visual Studio editor, inside the **Search** method, replace the existing logic with the following.</span></span> <span data-ttu-id="cf921-152">此邏輯會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-152">This logic creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/OnReceiveEcho matches the specified search criteria.</span></span>  
  
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
  
3.  <span data-ttu-id="cf921-153">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-153">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoStrings matches the specified search criteria.</span></span>  
  
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
  
4.  <span data-ttu-id="cf921-154">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-154">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetings matches the specified search criteria.</span></span>  
  
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
  
5.  <span data-ttu-id="cf921-155">繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetingFromFile 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-155">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetingFromFile matches the specified search criteria.</span></span>  
  
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
  
6.  <span data-ttu-id="cf921-156">繼續新增下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-156">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  <span data-ttu-id="cf921-157">在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="cf921-157">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
8.  <span data-ttu-id="cf921-158">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="cf921-158">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="cf921-159">您應該已成功編譯專案。</span><span class="sxs-lookup"><span data-stu-id="cf921-159">You should successfully compiled the project.</span></span> <span data-ttu-id="cf921-160">如果沒有，請確定您已遵循上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="cf921-160">If not, ensure that you have followed every step above.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf921-161">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="cf921-161">You saved your work.</span></span> <span data-ttu-id="cf921-162">您可以安全地關閉目前的 Visual Studio，或移至下一個步驟中，[步驟 6： 實作 Echo 配接器的中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cf921-162">You can safely close Visual Studio at this time or go to the next step, [Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="cf921-163">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="cf921-163">What Did I Just Do?</span></span>  
 <span data-ttu-id="cf921-164">您只實作搜尋功能的 Echo 配接器，藉由實作的中繼資料`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="cf921-164">You just implemented the metadata searching capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="cf921-165">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每項作業符合準則，則傳回的陣列物件`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="cf921-165">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for every operation that matches the criteria and then returned an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cf921-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cf921-166">Next Steps</span></span>  
 <span data-ttu-id="cf921-167">您會實作中繼資料解析功能，以及在傳出和傳入的訊息交換功能。</span><span class="sxs-lookup"><span data-stu-id="cf921-167">You will implement the metadata resolving capability, and the outbound and inbound message exchange capabilities.</span></span> <span data-ttu-id="cf921-168">最後，您會建置並部署 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="cf921-168">Finally, you will build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf921-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf921-169">See Also</span></span>  
 <span data-ttu-id="cf921-170">[步驟 4： 實作 Echo 配接器中繼資料瀏覽處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="cf921-170">[Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="cf921-171">[步驟 6： 實作 Echo 配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="cf921-171">[Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="cf921-172">教學課程 1：開發 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="cf921-172">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)