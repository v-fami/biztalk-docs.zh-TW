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
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a><span data-ttu-id="e3d93-102">步驟 4： 回應配接器實作中繼資料瀏覽的處理常式</span><span class="sxs-lookup"><span data-stu-id="e3d93-102">Step 4: Implement the Metadata Browse Handler for the Echo Adapter</span></span>
<span data-ttu-id="e3d93-103">![步驟 4 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span><span class="sxs-lookup"><span data-stu-id="e3d93-103">![Step 4 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span></span>  
  
 <span data-ttu-id="e3d93-104">**若要完成的時間：** 45 分鐘的時間</span><span class="sxs-lookup"><span data-stu-id="e3d93-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="e3d93-105">在此步驟中，您可以實作回應配接器的瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="e3d93-105">In this step, you implement the browse capability of the Echo adapter.</span></span> <span data-ttu-id="e3d93-106">這項功能可讓您的配接器執行連線為基礎的瀏覽至目標系統從取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3d93-106">This capability allows your adapter to perform a connection-based browse to obtain metadata from the target system.</span></span> <span data-ttu-id="e3d93-107">不論您的配接器的功能，您的配接器必須支援的瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="e3d93-107">Regardless of your adapter's capabilities, your adapter must support the browse capability.</span></span>  
  
 <span data-ttu-id="e3d93-108">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，若要支援瀏覽功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="e3d93-108">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support browse capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="e3d93-109">回應配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]呼叫 EchoAdapterMetadataBrowseHandler 的衍生的類別會自動產生。</span><span class="sxs-lookup"><span data-stu-id="e3d93-109">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdapterMetadataBrowseHandler.</span></span>  
  
 <span data-ttu-id="e3d93-110">在下列步驟中，您可以更新這個類別，以深入了解如何實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法時，如何設定各種屬性`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，以及作業和配接器所支援的類別目錄節點中如何顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="e3d93-110">In the following steps, you update this class to get a better understanding of how to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, how to set various properties of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the operation and category nodes supported by the adapter appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e3d93-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="e3d93-111">Prerequisites</span></span>  
 <span data-ttu-id="e3d93-112">在開始此步驟之前，您必須已順利完成[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d93-112">Before you begin this step, you must have successfully completed [Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span></span> <span data-ttu-id="e3d93-113">您也必須了解下列類別：</span><span class="sxs-lookup"><span data-stu-id="e3d93-113">You must also understand the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a><span data-ttu-id="e3d93-114">IMetadataBrowseHandler 介面</span><span class="sxs-lookup"><span data-stu-id="e3d93-114">The IMetadataBrowseHandler Interface</span></span>  
 <span data-ttu-id="e3d93-115">`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面定義為：</span><span class="sxs-lookup"><span data-stu-id="e3d93-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface is defined as:</span></span>  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="e3d93-116">`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的方法參數。</span><span class="sxs-lookup"><span data-stu-id="e3d93-116">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the method parameters.</span></span> <span data-ttu-id="e3d93-117">參數定義`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法詳述於下表。</span><span class="sxs-lookup"><span data-stu-id="e3d93-117">The parameter definitions for the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method are described in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d93-118">回應配接器實作會使用節點識別碼，並會忽略的三個參數，因為回應配接器支援只在少數節點。</span><span class="sxs-lookup"><span data-stu-id="e3d93-118">The Echo adapter implementation uses only the node ID and ignores the other three parameters, since the Echo adapter supports only a few nodes.</span></span>  
  
|<span data-ttu-id="e3d93-119">**參數**</span><span class="sxs-lookup"><span data-stu-id="e3d93-119">**Parameter**</span></span>|<span data-ttu-id="e3d93-120">**定義**</span><span class="sxs-lookup"><span data-stu-id="e3d93-120">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="e3d93-121">節點識別碼</span><span class="sxs-lookup"><span data-stu-id="e3d93-121">nodeId</span></span>|<span data-ttu-id="e3d93-122">在 [中繼資料總管] 階層中的每個項目 ([!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和</span><span class="sxs-lookup"><span data-stu-id="e3d93-122">Each item in the hierarchy of the metadata explorer (the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and</span></span><br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]<span data-ttu-id="e3d93-123">) 有節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="e3d93-123">) has a nodeId.</span></span> <span data-ttu-id="e3d93-124">每個節點識別碼必須是唯一的而且可以是類別或作業。</span><span class="sxs-lookup"><span data-stu-id="e3d93-124">Each node ID must be unique and can be a category or an operation.</span></span> <span data-ttu-id="e3d93-125">類別可以有子類別。</span><span class="sxs-lookup"><span data-stu-id="e3d93-125">The category can have subcategories.</span></span> <span data-ttu-id="e3d93-126">**注意：**如果 null 或空字串 ("")，從根節點 （"/"） 根據預設，會擷取作業。</span><span class="sxs-lookup"><span data-stu-id="e3d93-126">**Note:**  If null or an empty string (""), operations are retrieved from the root node ("/") by default.</span></span>|  
|<span data-ttu-id="e3d93-127">childStartIndex</span><span class="sxs-lookup"><span data-stu-id="e3d93-127">childStartIndex</span></span>|<span data-ttu-id="e3d93-128">要傳回的第一個子系的索引。</span><span class="sxs-lookup"><span data-stu-id="e3d93-128">The index of the first child to return.</span></span><br /><br /> <span data-ttu-id="e3d93-129">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="e3d93-129">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="e3d93-130">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="e3d93-130">maxChildNodes</span></span>|<span data-ttu-id="e3d93-131">要傳回的結果節點數目上限。</span><span class="sxs-lookup"><span data-stu-id="e3d93-131">The maximum number of result nodes to return.</span></span> <span data-ttu-id="e3d93-132">您可以使用 Int32.Max 來擷取結果的所有節點。</span><span class="sxs-lookup"><span data-stu-id="e3d93-132">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="e3d93-133">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="e3d93-133">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="e3d93-134">timeout</span><span class="sxs-lookup"><span data-stu-id="e3d93-134">timeout</span></span>|<span data-ttu-id="e3d93-135">允許的作業完成的時間上限。</span><span class="sxs-lookup"><span data-stu-id="e3d93-135">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="e3d93-136">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="e3d93-136">Not supported by the Echo adapter.</span></span>|  
  
 <span data-ttu-id="e3d93-137">當實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法，您必須將每個類別目錄和作業的節點加入陣列的`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-137">When implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, you must add every category and operation node to the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="e3d93-138">若要指定的節點做為類別目錄，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`false`。</span><span class="sxs-lookup"><span data-stu-id="e3d93-138">To specify a node as category, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `false`.</span></span> <span data-ttu-id="e3d93-139">若要為作業指定的節點，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`true`。</span><span class="sxs-lookup"><span data-stu-id="e3d93-139">To specify a node as operation, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `true`.</span></span>  
  
## <a name="echo-adapter-metadata-browse"></a><span data-ttu-id="e3d93-140">回應配接器中繼資料瀏覽</span><span class="sxs-lookup"><span data-stu-id="e3d93-140">Echo Adapter Metadata Browse</span></span>  
 <span data-ttu-id="e3d93-141">根據目標系統的類別和作業，會有許多方法可建立的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-141">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="e3d93-142">作業和您選擇的類別應該代表您想要公開的作業。</span><span class="sxs-lookup"><span data-stu-id="e3d93-142">The operations and categories you choose should represent the operations you want to expose.</span></span> <span data-ttu-id="e3d93-143">但是回應配接器，它只會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`所列出的每個下列的節點，節點識別碼的物件：</span><span class="sxs-lookup"><span data-stu-id="e3d93-143">But for the Echo adapter, it simply creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each of the following nodes with node ID listed:</span></span>  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 <span data-ttu-id="e3d93-144">EchoMainCategory 是根節點 （"/"） 下的類別目錄節點。</span><span class="sxs-lookup"><span data-stu-id="e3d93-144">The EchoMainCategory is the category node under the root node ("/").</span></span> <span data-ttu-id="e3d93-145">此節點也使用做為類別目錄的傳入和傳出作業。</span><span class="sxs-lookup"><span data-stu-id="e3d93-145">This node is also used as the category for both inbound and outbound operations.</span></span> <span data-ttu-id="e3d93-146">因此，當建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`該分類中，您可以執行下列物件：</span><span class="sxs-lookup"><span data-stu-id="e3d93-146">Hence, when creating the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that category, you can do the following:</span></span>  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 <span data-ttu-id="e3d93-147">例如 Echo/EchoString 屬於 EchoMainCategory 輸出作業中，您可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e3d93-147">For an outbound operation such as Echo/EchoString that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
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
  
 <span data-ttu-id="e3d93-148">用於將輸入 Echo/OnReceiveEcho EchoMainCategory 屬於這類作業，您可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e3d93-148">For an inbound operation such as Echo/OnReceiveEcho that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
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
  
 <span data-ttu-id="e3d93-149">當[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具瀏覽回應配接器中繼資料，根據預設，它會從根節點 （"/"） 開始。</span><span class="sxs-lookup"><span data-stu-id="e3d93-149">When the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools explore the Echo adapter metadata, by default, it starts from the root node ("/").</span></span>  
  
 <span data-ttu-id="e3d93-150">下圖顯示 EchoMainCategory 節點之下的根節點 （"/"）：</span><span class="sxs-lookup"><span data-stu-id="e3d93-150">The following figure shows that the EchoMainCategory node appears under the root node ("/"):</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
 <span data-ttu-id="e3d93-151">若要瀏覽中的三個輸出的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**選項。</span><span class="sxs-lookup"><span data-stu-id="e3d93-151">To browse the three outbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Client (Outbound operations)** option.</span></span> <span data-ttu-id="e3d93-152">您會看到這些作業在**可用的類別和作業**清單方塊中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e3d93-152">You see those operations in the **Available categories and operations** list box, as shown below:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")  
  
 <span data-ttu-id="e3d93-153">在上圖中，注意`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`值會出現在**名稱**資料行**可用的類別和作業**清單方塊。</span><span class="sxs-lookup"><span data-stu-id="e3d93-153">In the previous figure, notice that the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A` value appears in the **Name** column of the **Available categories and operations** list box.</span></span> <span data-ttu-id="e3d93-154">參數傳遞至`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`建構函式會出現在**節點識別碼**資料行**可用的類別和作業**清單方塊中，而`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A`值會顯示為工具提示當您以滑鼠右鍵按一下包含描述， `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`。</span><span class="sxs-lookup"><span data-stu-id="e3d93-154">The parameter passed into the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` constructor appears in the **Node ID** column of the **Available categories and operations** list box, and the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A` value appears as the tool tip that contains the description, when you right-click the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`.</span></span>  
  
 <span data-ttu-id="e3d93-155">若要查看在輸入的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具**選取合約型別**下拉式清單中選取**服務 （輸入操作）**選項。</span><span class="sxs-lookup"><span data-stu-id="e3d93-155">To see the inbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Service (Inbound operations)** option.</span></span> <span data-ttu-id="e3d93-156">您會看到中的輸入的 OnReceiveEcho 作業**可用的類別和作業**清單方塊中，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="e3d93-156">You see the inbound OnReceiveEcho operation in the **Available categories and operations** list box, as shown in the following figure:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")  
  
## <a name="implementing-the-imetadatabrowsehandler"></a><span data-ttu-id="e3d93-157">實作 IMetadataBrowseHandler</span><span class="sxs-lookup"><span data-stu-id="e3d93-157">Implementing the IMetadataBrowseHandler</span></span>  
 <span data-ttu-id="e3d93-158">在此步驟中，您可以更新 EchoAdapterMetadataBrowseHandler 類別來實作回應配接器的中繼資料瀏覽，也就是，以實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="e3d93-158">In this step, you update the EchoAdapterMetadataBrowseHandler class to implement the Echo adapter's metadata browse, that is, to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="e3d93-159">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每個類別目錄和作業的物件，設定適當的值，該物件，然後傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別和作業的物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-159">Specifically, you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each category and operation, set appropriate values for that object, and then return the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects for category and operations.</span></span> <span data-ttu-id="e3d93-160">請注意，當您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，您要傳入的節點識別碼，而不是顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e3d93-160">Keep in mind that when you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, you need to pass in the node ID, not the display name.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a><span data-ttu-id="e3d93-161">若要更新 EchoAdapterMetadataBrowseHandler 類別</span><span class="sxs-lookup"><span data-stu-id="e3d93-161">To update the EchoAdapterMetadataBrowseHandler class</span></span>  
  
1.  <span data-ttu-id="e3d93-162">在 [方案總管] 中，按兩下**EchoAdapterMetadataBrowseHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="e3d93-162">In Solution Explorer, double-click the **EchoAdapterMetadataBrowseHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="e3d93-163">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="e3d93-163">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="e3d93-164">在 Visual Studio 編輯器中，內部**瀏覽**方法，以建立下列內容取代現有的邏輯`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`EchoMainCategory 的物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-164">In the Visual Studio editor, inside the **Browse** method, replace the existing logic with the following to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for EchoMainCategory.</span></span>  
  
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
  
4.  <span data-ttu-id="e3d93-165">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 的物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-165">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/OnReceiveEcho.</span></span>  
  
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
  
5.  <span data-ttu-id="e3d93-166">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 的物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-166">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoStrings.</span></span>  
  
    ```csharp  
    // Outbound operations  
    MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
    outOpNode1.DisplayName = "EchoStrings";  
    outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
    outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode1.IsOperation = true;  
    ```  
  
6.  <span data-ttu-id="e3d93-167">繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 的物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-167">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoGreetings.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  <span data-ttu-id="e3d93-168">繼續加入下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`回應的物件 / EchoGreetingFromFile。</span><span class="sxs-lookup"><span data-stu-id="e3d93-168">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/ EchoGreetingFromFile.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  <span data-ttu-id="e3d93-169">繼續加入下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件或如果沒有符合項目為 null。</span><span class="sxs-lookup"><span data-stu-id="e3d93-169">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects or null if not matched.</span></span>  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. <span data-ttu-id="e3d93-170">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="e3d93-170">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
10. <span data-ttu-id="e3d93-171">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="e3d93-171">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="e3d93-172">您應該成功建置專案。</span><span class="sxs-lookup"><span data-stu-id="e3d93-172">You should successfully build the project.</span></span> <span data-ttu-id="e3d93-173">如果沒有，請確定您已依照上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="e3d93-173">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d93-174">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="e3d93-174">You saved your work.</span></span> <span data-ttu-id="e3d93-175">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 5： 回應配接器實作中繼資料的搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d93-175">You can safely close Visual Studio at this time or go to the next step, [Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="e3d93-176">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="e3d93-176">What Did I Just Do?</span></span>  
 <span data-ttu-id="e3d93-177">您只實作中繼資料瀏覽回應配接器的功能，藉由實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="e3d93-177">You just implemented the metadata browsing capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="e3d93-178">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`分類中，物件，並再當成陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="e3d93-178">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for the category, and then returned it as an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="e3d93-179">在您建立的每個作業，`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，然後再傳回所有這些物件的陣列中`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`。</span><span class="sxs-lookup"><span data-stu-id="e3d93-179">For each operation, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and then returned all those objects in an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e3d93-180">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e3d93-180">Next Steps</span></span>  
 <span data-ttu-id="e3d93-181">您可以實作中繼資料的搜尋和解析功能，以及輸出的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e3d93-181">You implement metadata searching and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="e3d93-182">最後，您會建置並部署回應配接器。</span><span class="sxs-lookup"><span data-stu-id="e3d93-182">Finally, you build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d93-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3d93-183">See Also</span></span>  
 <span data-ttu-id="e3d93-184">[教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="e3d93-184">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="e3d93-185">[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="e3d93-185">[Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="e3d93-186">步驟 5： 回應配接器實作的中繼資料搜尋處理常式</span><span class="sxs-lookup"><span data-stu-id="e3d93-186">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)