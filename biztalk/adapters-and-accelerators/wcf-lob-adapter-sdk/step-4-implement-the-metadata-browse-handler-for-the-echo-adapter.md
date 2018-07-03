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
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a><span data-ttu-id="1010d-102">步驟 4： 實作 Echo 配接器中繼資料瀏覽處理常式</span><span class="sxs-lookup"><span data-stu-id="1010d-102">Step 4: Implement the Metadata Browse Handler for the Echo Adapter</span></span>
<span data-ttu-id="1010d-103">![步驟 4 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span><span class="sxs-lookup"><span data-stu-id="1010d-103">![Step 4 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span></span>  
  
 <span data-ttu-id="1010d-104">**若要完成的時間：** 45 分鐘的時間</span><span class="sxs-lookup"><span data-stu-id="1010d-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="1010d-105">在此步驟中，您可以實作 Echo 配接器的瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="1010d-105">In this step, you implement the browse capability of the Echo adapter.</span></span> <span data-ttu-id="1010d-106">這項功能可讓您的配接器進行連接為基礎的瀏覽 從目標系統中取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1010d-106">This capability allows your adapter to perform a connection-based browse to obtain metadata from the target system.</span></span> <span data-ttu-id="1010d-107">不論您的配接器的功能，您的配接器必須支援的瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="1010d-107">Regardless of your adapter's capabilities, your adapter must support the browse capability.</span></span>  
  
 <span data-ttu-id="1010d-108">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，以支援瀏覽功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="1010d-108">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support browse capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="1010d-109">Echo 配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生呼叫 EchoAdapterMetadataBrowseHandler 的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="1010d-109">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdapterMetadataBrowseHandler.</span></span>  
  
 <span data-ttu-id="1010d-110">在下列步驟中，您會更新這個類別，以進一步了解如何實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法，如何設定各種屬性`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，而中顯示的作業與配接器所支援的類別目錄節點的方式[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="1010d-110">In the following steps, you update this class to get a better understanding of how to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, how to set various properties of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the operation and category nodes supported by the adapter appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1010d-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="1010d-111">Prerequisites</span></span>  
 <span data-ttu-id="1010d-112">在開始此步驟之前，您必須先成功完成[步驟 3： 實作 Echo 配接器連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="1010d-112">Before you begin this step, you must have successfully completed [Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span></span> <span data-ttu-id="1010d-113">您也必須了解下列類別：</span><span class="sxs-lookup"><span data-stu-id="1010d-113">You must also understand the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a><span data-ttu-id="1010d-114">IMetadataBrowseHandler 介面</span><span class="sxs-lookup"><span data-stu-id="1010d-114">The IMetadataBrowseHandler Interface</span></span>  
 <span data-ttu-id="1010d-115">`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面定義如下：</span><span class="sxs-lookup"><span data-stu-id="1010d-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface is defined as:</span></span>  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="1010d-116">`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件為基礎的方法參數。</span><span class="sxs-lookup"><span data-stu-id="1010d-116">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the method parameters.</span></span> <span data-ttu-id="1010d-117">參數定義`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法詳述於下表。</span><span class="sxs-lookup"><span data-stu-id="1010d-117">The parameter definitions for the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method are described in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1010d-118">Echo 配接器實作會使用節點識別碼，並忽略的三個參數，因為 Echo 配接器支援只有少數的節點。</span><span class="sxs-lookup"><span data-stu-id="1010d-118">The Echo adapter implementation uses only the node ID and ignores the other three parameters, since the Echo adapter supports only a few nodes.</span></span>  
  
|  <span data-ttu-id="1010d-119">**參數**</span><span class="sxs-lookup"><span data-stu-id="1010d-119">**Parameter**</span></span>  |                                                                                                                                                                                                                               <span data-ttu-id="1010d-120">**定義**</span><span class="sxs-lookup"><span data-stu-id="1010d-120">**Definition**</span></span>                                                                                                                                                                                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     <span data-ttu-id="1010d-121">nodeId</span><span class="sxs-lookup"><span data-stu-id="1010d-121">nodeId</span></span>      | <span data-ttu-id="1010d-122">在 [中繼資料總管] 階層中的每個項目 ([!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和</span><span class="sxs-lookup"><span data-stu-id="1010d-122">Each item in the hierarchy of the metadata explorer (the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and</span></span><br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]<span data-ttu-id="1010d-123">) 有節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="1010d-123">) has a nodeId.</span></span> <span data-ttu-id="1010d-124">每個節點的識別碼必須是唯一的而且可以是類別或作業。</span><span class="sxs-lookup"><span data-stu-id="1010d-124">Each node ID must be unique and can be a category or an operation.</span></span> <span data-ttu-id="1010d-125">類別可以有子類別。</span><span class="sxs-lookup"><span data-stu-id="1010d-125">The category can have subcategories.</span></span> <span data-ttu-id="1010d-126">**注意：** 如果 null 或空字串 ("")，從根節點 （"/"） 依預設，會擷取作業。</span><span class="sxs-lookup"><span data-stu-id="1010d-126">**Note:**  If null or an empty string (""), operations are retrieved from the root node ("/") by default.</span></span> |
| <span data-ttu-id="1010d-127">childStartIndex</span><span class="sxs-lookup"><span data-stu-id="1010d-127">childStartIndex</span></span> |                                                                                                                                                                                           <span data-ttu-id="1010d-128">要傳回的第一個子系的索引。</span><span class="sxs-lookup"><span data-stu-id="1010d-128">The index of the first child to return.</span></span><br /><br /> <span data-ttu-id="1010d-129">不支援 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="1010d-129">Not supported by the Echo adapter.</span></span>                                                                                                                                                                                            |
|  <span data-ttu-id="1010d-130">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="1010d-130">maxChildNodes</span></span>  |                                                                                                                                                                  <span data-ttu-id="1010d-131">要傳回的結果節點的數目上限。</span><span class="sxs-lookup"><span data-stu-id="1010d-131">The maximum number of result nodes to return.</span></span> <span data-ttu-id="1010d-132">您可以使用 Int32.Max 來擷取結果的所有節點。</span><span class="sxs-lookup"><span data-stu-id="1010d-132">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="1010d-133">不支援 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="1010d-133">Not supported by the Echo adapter.</span></span>                                                                                                                                                                   |
|     <span data-ttu-id="1010d-134">timeout</span><span class="sxs-lookup"><span data-stu-id="1010d-134">timeout</span></span>     |                                                                                                                                                                                   <span data-ttu-id="1010d-135">若要完成此作業所允許的時間上限。</span><span class="sxs-lookup"><span data-stu-id="1010d-135">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="1010d-136">不支援 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="1010d-136">Not supported by the Echo adapter.</span></span>                                                                                                                                                                                    |
  
 <span data-ttu-id="1010d-137">實作時`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法中，您必須將每個類別目錄和作業的節點的陣列加入`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-137">When implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, you must add every category and operation node to the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="1010d-138">若要指定節點做為類別目錄，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`false`。</span><span class="sxs-lookup"><span data-stu-id="1010d-138">To specify a node as category, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `false`.</span></span> <span data-ttu-id="1010d-139">若要指定作業的節點，設定`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A`至`true`。</span><span class="sxs-lookup"><span data-stu-id="1010d-139">To specify a node as operation, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `true`.</span></span>  
  
## <a name="echo-adapter-metadata-browse"></a><span data-ttu-id="1010d-140">Echo 配接器中繼資料瀏覽</span><span class="sxs-lookup"><span data-stu-id="1010d-140">Echo Adapter Metadata Browse</span></span>  
 <span data-ttu-id="1010d-141">根據目標系統的類別和作業，有許多種方法，來建置的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-141">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="1010d-142">作業和您選擇的類別目錄應該代表您想要公開的作業。</span><span class="sxs-lookup"><span data-stu-id="1010d-142">The operations and categories you choose should represent the operations you want to expose.</span></span> <span data-ttu-id="1010d-143">但 Echo 配接器，它只會建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`列出物件給每個有節點識別碼的下列節點：</span><span class="sxs-lookup"><span data-stu-id="1010d-143">But for the Echo adapter, it simply creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each of the following nodes with node ID listed:</span></span>  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 <span data-ttu-id="1010d-144">EchoMainCategory 是 （"/"） 中的 [根] 節點下的 [類別目錄] 節點。</span><span class="sxs-lookup"><span data-stu-id="1010d-144">The EchoMainCategory is the category node under the root node ("/").</span></span> <span data-ttu-id="1010d-145">此節點也會做為類別目錄的輸入和輸出作業。</span><span class="sxs-lookup"><span data-stu-id="1010d-145">This node is also used as the category for both inbound and outbound operations.</span></span> <span data-ttu-id="1010d-146">因此，當建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件給該分類中，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1010d-146">Hence, when creating the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that category, you can do the following:</span></span>  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 <span data-ttu-id="1010d-147">例如 Echo/EchoString 屬於 EchoMainCategory 輸出作業，您可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1010d-147">For an outbound operation such as Echo/EchoString that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
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
  
 <span data-ttu-id="1010d-148">例如 Echo/OnReceiveEcho 屬於 EchoMainCategory 為輸入的作業，您可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1010d-148">For an inbound operation such as Echo/OnReceiveEcho that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
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
  
 <span data-ttu-id="1010d-149">當[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具探索 Echo 配接器中繼資料，根據預設，它會從 （"/"） 的根節點開始。</span><span class="sxs-lookup"><span data-stu-id="1010d-149">When the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools explore the Echo adapter metadata, by default, it starts from the root node ("/").</span></span>  
  
 <span data-ttu-id="1010d-150">下圖顯示 EchoMainCategory 節點之下的根節點 （"/"）：</span><span class="sxs-lookup"><span data-stu-id="1010d-150">The following figure shows that the EchoMainCategory node appears under the root node ("/"):</span></span>  
  
 <span data-ttu-id="1010d-151">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")</span><span class="sxs-lookup"><span data-stu-id="1010d-151">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")</span></span>  
  
 <span data-ttu-id="1010d-152">若要瀏覽中的三個輸出的作業，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）** 選項。</span><span class="sxs-lookup"><span data-stu-id="1010d-152">To browse the three outbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Client (Outbound operations)** option.</span></span> <span data-ttu-id="1010d-153">您會看到在這些作業**可用的類別和作業**清單方塊中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1010d-153">You see those operations in the **Available categories and operations** list box, as shown below:</span></span>  
  
 <span data-ttu-id="1010d-154">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")</span><span class="sxs-lookup"><span data-stu-id="1010d-154">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")</span></span>  
  
 <span data-ttu-id="1010d-155">在上圖中，注意`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`值會出現在**名稱**資料行**可用的類別和作業**清單方塊。</span><span class="sxs-lookup"><span data-stu-id="1010d-155">In the previous figure, notice that the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A` value appears in the **Name** column of the **Available categories and operations** list box.</span></span> <span data-ttu-id="1010d-156">參數傳遞至`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`建構函式會出現在**節點識別碼**資料行**可用的類別和作業**清單方塊中，而`Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A`值會顯示為工具提示當您以滑鼠右鍵按一下包含描述， `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`。</span><span class="sxs-lookup"><span data-stu-id="1010d-156">The parameter passed into the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` constructor appears in the **Node ID** column of the **Available categories and operations** list box, and the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A` value appears as the tool tip that contains the description, when you right-click the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`.</span></span>  
  
 <span data-ttu-id="1010d-157">若要查看輸入的作業，在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，在**選取合約的型別**下拉式清單中，選取**服務 （輸入作業）** 選項。</span><span class="sxs-lookup"><span data-stu-id="1010d-157">To see the inbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Service (Inbound operations)** option.</span></span> <span data-ttu-id="1010d-158">請參閱中的輸入的 OnReceiveEcho 作業**可用的類別和作業**清單方塊中，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="1010d-158">You see the inbound OnReceiveEcho operation in the **Available categories and operations** list box, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="1010d-159">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")</span><span class="sxs-lookup"><span data-stu-id="1010d-159">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")</span></span>  
  
## <a name="implementing-the-imetadatabrowsehandler"></a><span data-ttu-id="1010d-160">實作 IMetadataBrowseHandler</span><span class="sxs-lookup"><span data-stu-id="1010d-160">Implementing the IMetadataBrowseHandler</span></span>  
 <span data-ttu-id="1010d-161">在此步驟中，您會更新 EchoAdapterMetadataBrowseHandler 類別來實作 Echo 配接器中繼資料瀏覽，也就是，以實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="1010d-161">In this step, you update the EchoAdapterMetadataBrowseHandler class to implement the Echo adapter's metadata browse, that is, to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="1010d-162">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`針對每個類別目錄和作業物件，設定適當的值，該物件，則傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別和作業的物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-162">Specifically, you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each category and operation, set appropriate values for that object, and then return the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects for category and operations.</span></span> <span data-ttu-id="1010d-163">請記住，當您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，您需要將節點識別碼，而不是顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1010d-163">Keep in mind that when you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, you need to pass in the node ID, not the display name.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a><span data-ttu-id="1010d-164">若要更新 EchoAdapterMetadataBrowseHandler 類別</span><span class="sxs-lookup"><span data-stu-id="1010d-164">To update the EchoAdapterMetadataBrowseHandler class</span></span>  
  
1.  <span data-ttu-id="1010d-165">在 [方案總管] 中，按兩下**EchoAdapterMetadataBrowseHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="1010d-165">In Solution Explorer, double-click the **EchoAdapterMetadataBrowseHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="1010d-166">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何地方在編輯器中，在內容功能表中，指向**大綱**，然後按一下**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="1010d-166">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="1010d-167">在 Visual Studio 編輯器中，內部**瀏覽**方法，以建立下列內容取代現有的邏輯`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`EchoMainCategory 的物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-167">In the Visual Studio editor, inside the **Browse** method, replace the existing logic with the following to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for EchoMainCategory.</span></span>  
  
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
  
4.  <span data-ttu-id="1010d-168">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/OnReceiveEcho 的物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-168">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/OnReceiveEcho.</span></span>  
  
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
  
5.  <span data-ttu-id="1010d-169">繼續新增下列邏輯來建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoStrings 的物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-169">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoStrings.</span></span>  
  
    ```csharp  
    // Outbound operations  
    MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
    outOpNode1.DisplayName = "EchoStrings";  
    outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
    outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode1.IsOperation = true;  
    ```  
  
6.  <span data-ttu-id="1010d-170">繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo/EchoGreetings 的物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-170">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoGreetings.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  <span data-ttu-id="1010d-171">繼續新增下列程式碼，以建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`Echo 物件 / EchoGreetingFromFile。</span><span class="sxs-lookup"><span data-stu-id="1010d-171">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/ EchoGreetingFromFile.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  <span data-ttu-id="1010d-172">繼續新增下列程式碼，傳回的陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件或 null，如果不相符。</span><span class="sxs-lookup"><span data-stu-id="1010d-172">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects or null if not matched.</span></span>  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. <span data-ttu-id="1010d-173">在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="1010d-173">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
10. <span data-ttu-id="1010d-174">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="1010d-174">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="1010d-175">您應該已成功建置專案。</span><span class="sxs-lookup"><span data-stu-id="1010d-175">You should successfully build the project.</span></span> <span data-ttu-id="1010d-176">如果沒有，請確定您已遵循上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="1010d-176">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1010d-177">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="1010d-177">You saved your work.</span></span> <span data-ttu-id="1010d-178">您可以安全地關閉目前的 Visual Studio，或移至下一個步驟中，[步驟 5： 實作 Echo 配接器中繼資料搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="1010d-178">You can safely close Visual Studio at this time or go to the next step, [Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="1010d-179">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="1010d-179">What Did I Just Do?</span></span>  
 <span data-ttu-id="1010d-180">您只會實作中繼資料瀏覽的 Echo 配接器的功能，藉由實作`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A`方法的`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="1010d-180">You just implemented the metadata browsing capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="1010d-181">具體來說，您建立`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`類別物件，並再次為陣列`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-181">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for the category, and then returned it as an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="1010d-182">在您建立的每個作業，`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`物件，然後再傳回陣列中的 所有這些物件`Microsoft.ServiceModel.Channels.MetadataRetrievalNode`。</span><span class="sxs-lookup"><span data-stu-id="1010d-182">For each operation, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and then returned all those objects in an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1010d-183">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1010d-183">Next Steps</span></span>  
 <span data-ttu-id="1010d-184">您會實作中繼資料搜尋和解析功能，以及輸出的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="1010d-184">You implement metadata searching and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="1010d-185">最後，您會建置並部署 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="1010d-185">Finally, you build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1010d-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1010d-186">See Also</span></span>  
 <span data-ttu-id="1010d-187">[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="1010d-187">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="1010d-188">[步驟 3： 實作 Echo 配接器的連接](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="1010d-188">[Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="1010d-189">步驟 5：實作 Echo 配接器的中繼資料搜尋處理常式</span><span class="sxs-lookup"><span data-stu-id="1010d-189">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)