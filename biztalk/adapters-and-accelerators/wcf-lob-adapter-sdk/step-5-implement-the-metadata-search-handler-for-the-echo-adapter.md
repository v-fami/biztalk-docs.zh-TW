---
title: 步驟 5： 回應配接器實作的中繼資料搜尋處理常式 |Microsoft 文件
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
ms.openlocfilehash: 8d241499e10a944eb1941b680bc73b97ce6ffd93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226398"
---
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a><span data-ttu-id="5eaa7-102">步驟 5： 回應配接器實作的中繼資料搜尋處理常式</span><span class="sxs-lookup"><span data-stu-id="5eaa7-102">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>
<span data-ttu-id="5eaa7-103">![步驟 5 之 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span><span class="sxs-lookup"><span data-stu-id="5eaa7-103">![Step 5 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span></span>  
  
 <span data-ttu-id="5eaa7-104">**若要完成的時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="5eaa7-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="5eaa7-105">在此步驟的教學課程中，您可以實作回應配接器的搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-105">In this step of the tutorial, you implement the search capability of the Echo adapter.</span></span> <span data-ttu-id="5eaa7-106">不同於瀏覽，搜尋是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-106">Unlike browse, search is optional.</span></span> <span data-ttu-id="5eaa7-107">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援搜尋功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-107">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support search capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="5eaa7-108">回應配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]自動產生一個稱為 EchoAdapterMetadataSearchHandler 的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-108">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates one derived class called EchoAdapterMetadataSearchHandler.</span></span>  
  
 <span data-ttu-id="5eaa7-109">您第一次更新 EchoAdapterMetadataSearchHandler 類別，以取得更深入了解如何實作這個介面，如何填入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，以及如何搜尋結果顯示在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-109">You first update the EchoAdapterMetadataSearchHandler class to get a better understanding of how to implement this interface, how to populate  `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the search results appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5eaa7-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="5eaa7-110">Prerequisites</span></span>  
 <span data-ttu-id="5eaa7-111">在開始此步驟之前，請先完成[步驟 4： 實作回應配接器中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-111">Before you begin this step, complete [Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="5eaa7-112">您也必須清楚了解有關的下列類別：</span><span class="sxs-lookup"><span data-stu-id="5eaa7-112">You must also have a clear understanding about the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
## <a name="the-imetadatasearchhandler-interface"></a><span data-ttu-id="5eaa7-113">IMetadataSearchHandler 介面</span><span class="sxs-lookup"><span data-stu-id="5eaa7-113">The IMetadataSearchHandler Interface</span></span>  
 <span data-ttu-id="5eaa7-114">`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`定義為：</span><span class="sxs-lookup"><span data-stu-id="5eaa7-114">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` is defined as:</span></span>  
  
```  
public interface IMetadataSearchHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Search(string nodeId, string searchCriteria, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="5eaa7-115">`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the search criteria.</span></span> <span data-ttu-id="5eaa7-116">下表中說明的搜尋方法的參數定義：</span><span class="sxs-lookup"><span data-stu-id="5eaa7-116">The parameter definitions for the Search method are described in the following table:</span></span>  
  
|<span data-ttu-id="5eaa7-117">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eaa7-117">**Parameter**</span></span>|<span data-ttu-id="5eaa7-118">**定義**</span><span class="sxs-lookup"><span data-stu-id="5eaa7-118">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="5eaa7-119">節點識別碼</span><span class="sxs-lookup"><span data-stu-id="5eaa7-119">nodeId</span></span>|<span data-ttu-id="5eaa7-120">若要開始搜尋的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-120">The node ID to start searching from.</span></span> <span data-ttu-id="5eaa7-121">如果 null 或空字串 ("")，作業將會擷取從根節點 （"/"）。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-121">If null or an empty string (""), operations will be retrieved from the root node ("/").</span></span>|  
|<span data-ttu-id="5eaa7-122">searchCriteria</span><span class="sxs-lookup"><span data-stu-id="5eaa7-122">searchCriteria</span></span>|<span data-ttu-id="5eaa7-123">搜尋準則，是針對配接器。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-123">The search criteria, which is adapter-specific.</span></span> <span data-ttu-id="5eaa7-124">如果未不指定任何搜尋準則，配接器應傳回的所有節點。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-124">If no search criteria are specified, the adapter should return all nodes.</span></span>|  
|<span data-ttu-id="5eaa7-125">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="5eaa7-125">maxChildNodes</span></span>|<span data-ttu-id="5eaa7-126">要傳回的結果節點數目上限。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-126">The maximum number of result nodes to return.</span></span> <span data-ttu-id="5eaa7-127">您可以使用 Int32.Max 來擷取結果的所有節點。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-127">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="5eaa7-128">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-128">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="5eaa7-129">timeout</span><span class="sxs-lookup"><span data-stu-id="5eaa7-129">timeout</span></span>|<span data-ttu-id="5eaa7-130">允許的作業完成的時間上限。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-130">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="5eaa7-131">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-131">Not supported by the Echo adapter.</span></span>|  
  
 <span data-ttu-id="5eaa7-132">搜尋結果，您的配接器可以選擇傳回分類節點或運算節點，或兩者。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-132">For search result, your adapter can choose to return either category nodes or operation nodes, or both.</span></span> <span data-ttu-id="5eaa7-133">最多的搜尋功能的類型是您的配接器支援。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-133">It is up to the type of search feature your adapter supports.</span></span>  
  
## <a name="echo-adapter-metadata-search"></a><span data-ttu-id="5eaa7-134">回應配接器中繼資料的搜尋</span><span class="sxs-lookup"><span data-stu-id="5eaa7-134">Echo adapter Metadata Search</span></span>  
 <span data-ttu-id="5eaa7-135">根據目標系統的類別和作業，會有許多方法可建立的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`来傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-135">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects to return.</span></span> <span data-ttu-id="5eaa7-136">回應配接器實作搜尋功能的方法是瀏覽每項作業，其下面清單中的節點識別碼：</span><span class="sxs-lookup"><span data-stu-id="5eaa7-136">The way Echo adapter implements the search functionality is to go through every operation with its node ID in the following list:</span></span>  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
-   <span data-ttu-id="5eaa7-137">如果節點識別碼，然後符合搜尋準則，它會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件使用的作業，節點識別碼，然後將指定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-137">If the node ID then matches the search criteria, it creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object using the node ID of the operation, and then assigns the properties with values.</span></span> <span data-ttu-id="5eaa7-138">例如，</span><span class="sxs-lookup"><span data-stu-id="5eaa7-138">For example,</span></span>  
  
    ```  
    MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
    nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
    nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
    nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
    nodeInbound.IsOperation = true;  //It is an operation, not category.  
    ```  
  
-   <span data-ttu-id="5eaa7-139">然後將物件加入至集合的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s，例如，</span><span class="sxs-lookup"><span data-stu-id="5eaa7-139">And then add the object to a collection of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s, for example,</span></span>  
  
    ```  
    resultList.Add(nodeInbound);  
    ```  
  
-   <span data-ttu-id="5eaa7-140">最後傳回的集合陣列格式。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-140">Lastly returns the collection in an array format.</span></span>  
  
    ```  
    return resultList.ToArray();  
    ```  
  
 <span data-ttu-id="5eaa7-141">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具執行連線為基礎的搜尋可用的作業。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-141">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools to perform a connection-based search for the available operations.</span></span> <span data-ttu-id="5eaa7-142">例如，如下圖所示的搜尋準則時將字串**問候語**，搜尋會傳回**EchoGreetings**和**EchoGreetingFromFile**作業。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-142">For example, the following figure shows that when the searching criteria is the string **Greeting**, the search returns the **EchoGreetings** and **EchoGreetingFromFile** operations.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")  
  
 <span data-ttu-id="5eaa7-143">如果找到相符項目，其中任何一個工具就會傳回錯誤訊息，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-143">If no match is found, either tool will return the error message shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")  
  
## <a name="implementing-the-imetadatasearchhandler"></a><span data-ttu-id="5eaa7-144">實作 IMetadataSearchHandler</span><span class="sxs-lookup"><span data-stu-id="5eaa7-144">Implementing the IMetadataSearchHandler</span></span>  
 <span data-ttu-id="5eaa7-145">您將實作`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-145">You will implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="5eaa7-146">如果作業的顯示名稱符合搜尋準則，您將建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件該作業，並再將該物件加入至陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-146">If the operation's display name matches the search criteria, you will create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that operation, and then add that object to an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a><span data-ttu-id="5eaa7-147">若要更新 EchoAdapterMetadataSearchHandler 類別</span><span class="sxs-lookup"><span data-stu-id="5eaa7-147">To update the EchoAdapterMetadataSearchHandler class</span></span>  
  
1.  <span data-ttu-id="5eaa7-148">在 [方案總管] 中，按兩下**EchoAdapterMetadataSearchHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-148">In Solution Explorer, double-click the **EchoAdapterMetadataSearchHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="5eaa7-149">在 Visual Studio 編輯器中，內部**搜尋**方法，以下列取代現有的邏輯。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-149">In the Visual Studio editor, inside the **Search** method, replace the existing logic with the following.</span></span> <span data-ttu-id="5eaa7-150">此邏輯會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-150">This logic creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/OnReceiveEcho matches the specified search criteria.</span></span>  
  
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
  
3.  <span data-ttu-id="5eaa7-151">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-151">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoStrings matches the specified search criteria.</span></span>  
  
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
  
4.  <span data-ttu-id="5eaa7-152">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-152">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetings matches the specified search criteria.</span></span>  
  
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
  
5.  <span data-ttu-id="5eaa7-153">繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetingFromFile 是否符合指定的搜尋準則的物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-153">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetingFromFile matches the specified search criteria.</span></span>  
  
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
  
6.  <span data-ttu-id="5eaa7-154">繼續加入下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-154">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  <span data-ttu-id="5eaa7-155">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-155">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
8.  <span data-ttu-id="5eaa7-156">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-156">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="5eaa7-157">您應該成功編譯專案。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-157">You should successfully compiled the project.</span></span> <span data-ttu-id="5eaa7-158">如果沒有，請確定您已依照上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-158">If not, ensure that you have followed every step above.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5eaa7-159">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-159">You saved your work.</span></span> <span data-ttu-id="5eaa7-160">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 6： 實作回應配接器中繼資料解析的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-160">You can safely close Visual Studio at this time or go to the next step, [Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="5eaa7-161">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="5eaa7-161">What Did I Just Do?</span></span>  
 <span data-ttu-id="5eaa7-162">您只實作搜尋功能的回應配接器，藉由實作的中繼資料`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-162">You just implemented the metadata searching capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="5eaa7-163">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件符合準則，則傳回陣列的每個作業`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-163">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for every operation that matches the criteria and then returned an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5eaa7-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5eaa7-164">Next Steps</span></span>  
 <span data-ttu-id="5eaa7-165">您將實作中繼資料解析功能，以及在傳出和傳入的訊息交換功能。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-165">You will implement the metadata resolving capability, and the outbound and inbound message exchange capabilities.</span></span> <span data-ttu-id="5eaa7-166">最後，您將建置和部署回應配接器。</span><span class="sxs-lookup"><span data-stu-id="5eaa7-166">Finally, you will build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eaa7-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eaa7-167">See Also</span></span>  
 <span data-ttu-id="5eaa7-168">[步驟 4： 回應配接器實作中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="5eaa7-168">[Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="5eaa7-169">[步驟 6： 實作回應配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="5eaa7-169">[Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="5eaa7-170">教學課程 1： 在開發回應配接器</span><span class="sxs-lookup"><span data-stu-id="5eaa7-170">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)