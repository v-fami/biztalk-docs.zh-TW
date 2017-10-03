---
title: "執行 「 命名空間元件 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f334a8-06de-4a56-a41a-3df088bf4a72
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fc142ca70971f023e491dbdeee693a8d41c42fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-sample"></a><span data-ttu-id="85ec5-102">執行命名空間 」 元件範例</span><span class="sxs-lookup"><span data-stu-id="85ec5-102">Running the Namespace Component Sample</span></span>
<span data-ttu-id="85ec5-103">命名空間 」 元件範例應用程式包含四個接收位置/傳送連接埠配對。</span><span class="sxs-lookup"><span data-stu-id="85ec5-103">The Namespace Component sample application contains four receive location/send port pairs.</span></span> <span data-ttu-id="85ec5-104">每一組代表測試。</span><span class="sxs-lookup"><span data-stu-id="85ec5-104">Each pair represents a test.</span></span> <span data-ttu-id="85ec5-105">下面是四個測試：</span><span class="sxs-lookup"><span data-stu-id="85ec5-105">The following are the four tests:</span></span>  
  
-   <span data-ttu-id="85ec5-106">**將加入傳遞至**。</span><span class="sxs-lookup"><span data-stu-id="85ec5-106">**Add to Pass-through**.</span></span> <span data-ttu-id="85ec5-107">這項測試將命名空間加入至 XML 文件訊息，並將訊息直接寫入檔案，以便您可以看到新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="85ec5-107">This test adds a namespace to an XML message document and writes the message directly to a file so that you can see the new namespace.</span></span> <span data-ttu-id="85ec5-108">這項測試的輸入的檔是 TEST_Add_to_PassThrough.0000.ns.xml。</span><span class="sxs-lookup"><span data-stu-id="85ec5-108">The input file for this test is TEST_Add_to_PassThrough.0000.ns.xml.</span></span> <span data-ttu-id="85ec5-109">這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件。</span><span class="sxs-lookup"><span data-stu-id="85ec5-109">This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component.</span></span>  
  
-   <span data-ttu-id="85ec5-110">**加入移除**。</span><span class="sxs-lookup"><span data-stu-id="85ec5-110">**Add to Remove**.</span></span> <span data-ttu-id="85ec5-111">這項測試將命名空間加入至 XML 文件訊息，並將其移除。</span><span class="sxs-lookup"><span data-stu-id="85ec5-111">This test adds a namespace to an XML document message and then removes it.</span></span> <span data-ttu-id="85ec5-112">然後，它會將訊息直接寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="85ec5-112">It then writes the message directly to a file.</span></span> <span data-ttu-id="85ec5-113">這項測試的輸入的檔是 TEST_ Add_to_Remove.0000.ns.xml。</span><span class="sxs-lookup"><span data-stu-id="85ec5-113">The input file for this test is TEST_ Add_to_Remove.0000.ns.xml.</span></span> <span data-ttu-id="85ec5-114">這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件和**NamespaceSampleSendPipeline**包含**RemoveNamespace**元件。</span><span class="sxs-lookup"><span data-stu-id="85ec5-114">This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component and the **NamespaceSampleSendPipeline** that contains a **RemoveNamespace** component.</span></span>  
  
-   <span data-ttu-id="85ec5-115">**移除傳遞**。</span><span class="sxs-lookup"><span data-stu-id="85ec5-115">**Pass-through to Remove**.</span></span> <span data-ttu-id="85ec5-116">這項測試的所有命名空間移除 XML 文件訊息，並將訊息直接寫入檔案，以便您可以確認這。</span><span class="sxs-lookup"><span data-stu-id="85ec5-116">This test removes all namespaces from an XML document message and writes the message directly to a file so that you can confirm this.</span></span> <span data-ttu-id="85ec5-117">這項測試的輸入的檔是 TEST_PassThrough_to_Remove.0000.ns.xml。</span><span class="sxs-lookup"><span data-stu-id="85ec5-117">The input file for this test is TEST_PassThrough_to_Remove.0000.ns.xml.</span></span> <span data-ttu-id="85ec5-118">這項測試會使用**NamespaceSampleSendPipeline**包含**RemoveNamespace**元件。</span><span class="sxs-lookup"><span data-stu-id="85ec5-118">This test uses the **NamespaceSampleSendPipeline** that contains a **RemoveNamespace** component.</span></span>  
  
-   <span data-ttu-id="85ec5-119">**擷取傳遞至透過加入**。</span><span class="sxs-lookup"><span data-stu-id="85ec5-119">**Add Via Extraction to Pass-through**.</span></span> <span data-ttu-id="85ec5-120">這項測試會擷取**OrderDetails**元素的 XML 文件訊息和寫入新的訊息，包含這個項目的直接到檔案。</span><span class="sxs-lookup"><span data-stu-id="85ec5-120">This test extracts the **OrderDetails** element of an XML document message and writes a new message containing this element directly to a file.</span></span> <span data-ttu-id="85ec5-121">這項測試的輸入的檔是 TEST_AddViaExtraction_to_PassThrough.0000.ns.xml。</span><span class="sxs-lookup"><span data-stu-id="85ec5-121">The input file for this test is TEST_AddViaExtraction_to_PassThrough.0000.ns.xml.</span></span> <span data-ttu-id="85ec5-122">這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件**ExtractionNodeXPath**屬性設定為**/CanonicalOrder/OrderDetails** （此屬性，都可以使用任何有效的 XPath，傳回的項目）。</span><span class="sxs-lookup"><span data-stu-id="85ec5-122">This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component with the **ExtractionNodeXPath** property set to **/CanonicalOrder/OrderDetails** (any valid XPath that returns an element will suffice for this property).</span></span>  
  
 <span data-ttu-id="85ec5-123">範例應用程式中的基礎接收位置有檔案遮罩適用於每個測試類型，以及相關傳送連接埠篩選器的接收埠名稱。</span><span class="sxs-lookup"><span data-stu-id="85ec5-123">The underlying receive locations in the sample application have file masks that are appropriate for each of the test types, and the related send ports filter on the receive port name.</span></span> <span data-ttu-id="85ec5-124">因此，若要執行測試，您只要適當命名的訊息放入輸入的資料夾。</span><span class="sxs-lookup"><span data-stu-id="85ec5-124">Therefore, to execute a test, you just drop the appropriately named message into the input folder.</span></span> <span data-ttu-id="85ec5-125">範例應用程式執行測試，然後將更新的訊息置放到輸出資料夾中使用目前的測試中，適當的名稱，包括訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="85ec5-125">The sample application executes the test and drops the updated message into the output folder using a name appropriate for the current test, and including the Message ID.</span></span>  
  
 <span data-ttu-id="85ec5-126">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="85ec5-126">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="85ec5-127">執行測試命名空間元件</span><span class="sxs-lookup"><span data-stu-id="85ec5-127">Running the Namespace Component Tests</span></span>](../esb-toolkit/running-the-namespace-component-tests.md)  
  
-   [<span data-ttu-id="85ec5-128">如何新增命名空間範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="85ec5-128">How the Add Namespace Sample Works</span></span>](../esb-toolkit/how-the-add-namespace-sample-works.md)  
  
-   [<span data-ttu-id="85ec5-129">移除命名空間範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="85ec5-129">How the Remove Namespace Sample Works</span></span>](../esb-toolkit/how-the-remove-namespace-sample-works.md)