---
title: 如何建立連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670b831f-be03-4612-93d5-a894f7bb3c11
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7315b4cd568c6107dcab25cf1fe471428b58da8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014743"
---
# <a name="how-to-create-links"></a><span data-ttu-id="520d3-102">如何建立連結</span><span class="sxs-lookup"><span data-stu-id="520d3-102">How to Create Links</span></span>
<span data-ttu-id="520d3-103">建立的連結**記錄**或**欄位**來源結構描述中的節點**記錄**或是**欄位**目的結構描述中的節點是最基本建立對應的活動。</span><span class="sxs-lookup"><span data-stu-id="520d3-103">Creating a link from a **Record** or **Field** node in a source schema to a **Record** or **Field** node in a destination schema is the most basic activity in creating maps.</span></span> <span data-ttu-id="520d3-104">本主題提供此活動數個變化的逐步指示，包括建立運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-104">This topic provides step-by-step instructions for several variations of this activity, including creating links to and from functoids.</span></span> <span data-ttu-id="520d3-105">如需有關使用運算質的詳細資訊，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="520d3-105">For additional information about working with functoids, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).</span></span>  
  
 <span data-ttu-id="520d3-106">本主題中的指示假設您已開啟 BizTalk 對應，且您已選擇對應的來源與目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="520d3-106">The instructions in this topic assume you already have a BizTalk map open, and that you have chosen source and destination schemas for the map.</span></span> <span data-ttu-id="520d3-107">如需有關開啟對應以及選擇對應結構描述的詳細資訊，請參閱 < [Managing 對應內 Projects](../core/managing-maps-within-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="520d3-107">For more information about opening maps and choosing schemas for the map, see [Managing Maps Within Projects](../core/managing-maps-within-projects.md).</span></span>  
  
### <a name="to-create-links-between-field-and-record-nodes"></a><span data-ttu-id="520d3-108">建立欄位和記錄節點之間的連結</span><span class="sxs-lookup"><span data-stu-id="520d3-108">To create links between Field and Record nodes</span></span>  
  
1. <span data-ttu-id="520d3-109">在 BizTalk 對應工具中，拖曳**欄位**或**記錄**從來源結構描述樹狀結構節點**欄位**或**記錄**目的結構描述的節點樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="520d3-109">In BizTalk Mapper, drag a **Field** or **Record** node from the source schema tree to a **Field** or **Record** node in the destination schema tree.</span></span>  
  
    <span data-ttu-id="520d3-110">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="520d3-110">**- Or -**</span></span>  
  
2. <span data-ttu-id="520d3-111">在 BizTalk 對應工具中，拖曳**欄位**或**記錄**節點從目的結構描述樹狀結構，以**欄位**或是**記錄**來源結構描述中的節點樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="520d3-111">In BizTalk Mapper, drag a **Field** or **Record** node from the destination schema tree to a **Field** or **Record** node in the source schema tree.</span></span>  
  
   <span data-ttu-id="520d3-112">建立連結時必須考慮以下事項：</span><span class="sxs-lookup"><span data-stu-id="520d3-112">There are several things to consider when creating links:</span></span>  
  
-   <span data-ttu-id="520d3-113">資料類型**欄位**或**記錄**來源結構描述樹狀結構中的節點應該符合的資料型別**欄位**或是**記錄**它的節點已連結在目的結構描述樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="520d3-113">The data type of a **Field** or **Record** node in the source schema tree should match the data type of a **Field** or **Record** node to which it is linked in the destination schema tree.</span></span>  
  
-   <span data-ttu-id="520d3-114">如果**欄位**或是**記錄**來源結構描述中的節點是選擇性的與特定的來源執行個體訊息不包含對應的項目或屬性，BizTalk 對應工具將不會建立對應項目或屬性，在目的地執行個體訊息中，即使**欄位**或是**記錄**節點有其間對應中的直接連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-114">If a **Field** or **Record** node in the source schema is optional, and a particular source instance message does not contain the corresponding element or attribute, BizTalk Mapper will not create a corresponding element or attribute in the destination instance message, even if the **Field** or **Record** nodes have a direct link between them in the map.</span></span>  
  
-   <span data-ttu-id="520d3-115">您無法連結到**欄位**或是**記錄**具有與其相關聯的常數值與目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-115">You cannot link to a **Field** or **Record** node in the destination schema that has a constant value associated with it.</span></span> <span data-ttu-id="520d3-116">相反地，您可以連結至包含所需**欄位**或是**記錄**與其相關聯的預設值到目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-116">On the other hand, you can link to a required **Field** or **Record** node in the destination schema that has a default value associated with it.</span></span> <span data-ttu-id="520d3-117">不過，請注意當您測試對應時，將會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="520d3-117">Note, however, that when you test the map, the default value will be used.</span></span>  
  
-   <span data-ttu-id="520d3-118">您無法建立連結，或從**Any 項目**， **Any 屬性**， **Sequence 群組**，或**Choice 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-118">You cannot create a link to or from the **Any Element**, **Any Attribute**, **Sequence Group**, or **Choice Group** nodes.</span></span> <span data-ttu-id="520d3-119">如需這些類型的節點的詳細資訊，請參閱下列主題，請參閱 < [Any 項目節點](../core/any-element-nodes.md)， [Sequence 群組節點](../core/sequence-group-nodes.md)或是[Choice 群組節點](../core/choice-group-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="520d3-119">For more information about these types of nodes, see the following topics, see [Any Element Nodes](../core/any-element-nodes.md), [Sequence Group Nodes](../core/sequence-group-nodes.md) or [Choice Group Nodes](../core/choice-group-nodes.md).</span></span>  
  
-   <span data-ttu-id="520d3-120">您可能需要展開結構描述樹狀結構以檢視您要對應的欄位。</span><span class="sxs-lookup"><span data-stu-id="520d3-120">You may need to expand the schema trees to view the fields that you want to map.</span></span> <span data-ttu-id="520d3-121">如需詳細資訊，請參閱 <<c0> [ 如何展開和摺疊結構描述樹狀結構](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="520d3-121">For more information, see [How to Expand and Collapse the Schema Trees](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx).</span></span>  
  
#### <a name="to-create-links-between-record-or-field-nodes-and-functoids"></a><span data-ttu-id="520d3-122">建立記錄或欄位節點與運算質之間的連結</span><span class="sxs-lookup"><span data-stu-id="520d3-122">To create links between Record or Field nodes and functoids</span></span>  
  
1.  <span data-ttu-id="520d3-123">在 BizTalk 對應工具中，拖曳**記錄**或是**欄位**格線頁中運算質從來源或目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-123">In BizTalk Mapper, drag a **Record** or **Field** node from the source or destination schema to a functoid in a grid page.</span></span>  
  
     <span data-ttu-id="520d3-124">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="520d3-124">**- Or -**</span></span>  
  
2.  <span data-ttu-id="520d3-125">從格線頁，以將運算質**記錄**或**欄位**來源或目的結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-125">Drag the functoid from a grid page to a **Record** or **Field** node in the source or destination schema.</span></span>  
  
     <span data-ttu-id="520d3-126">當您建立之間的連結**記錄**或是**欄位**來源結構描述和運算質中的節點，您會建立該運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="520d3-126">When you create a link between a **Record** or **Field** node in the source schema and a functoid, you are creating an input to that functoid.</span></span> <span data-ttu-id="520d3-127">當您建立之間的連結**記錄**或是**欄位**目的結構描述和運算質中的節點，您會從該運算質建立輸出。</span><span class="sxs-lookup"><span data-stu-id="520d3-127">When you create a link between a **Record** or **Field** node in the destination schema and a functoid, you are creating an output from that functoid.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="520d3-128">您無法連結運算質之間及**Any 項目** 節點或有**Any 屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-128">You cannot link between a functoid and an **Any Element** node or an **Any Attribute** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="520d3-129">您必須先新增運算質至格線頁之間的連結新增之前**記錄**或是**欄位**節點與該運算質。</span><span class="sxs-lookup"><span data-stu-id="520d3-129">You must first add a functoid to a grid page before you can add a link between a **Record** or **Field** node and that functoid.</span></span> <span data-ttu-id="520d3-130">如需新增運算質至格線頁的詳細資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="520d3-130">For more information about adding functoids to a grid page, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md).</span></span> <span data-ttu-id="520d3-131">另請參閱[新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="520d3-131">Also see [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="520d3-132">您無法連結到**欄位**具有與其相關聯的常數值與目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-132">You cannot link to a **Field** node in the destination schema that has a constant value associated with it.</span></span> <span data-ttu-id="520d3-133">相反地，您可以連結至包含所需**欄位**與其相關聯的預設值到目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="520d3-133">On the other hand, you can link to a required **Field** node in the destination schema that has a default value associated with it.</span></span> <span data-ttu-id="520d3-134">不過，請注意當您測試對應時，將會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="520d3-134">Note, however, that when you test the map, the default value will be used.</span></span>  
  
#### <a name="to-create-links-between-functoids"></a><span data-ttu-id="520d3-135">建立運算質之間的連結</span><span class="sxs-lookup"><span data-stu-id="520d3-135">To create links between functoids</span></span>  
  
-   <span data-ttu-id="520d3-136">在 BizTalk 對應工具中，將某個運算質拖曳至格線頁中的另一個運算質。</span><span class="sxs-lookup"><span data-stu-id="520d3-136">In BizTalk Mapper, drag one functoid to another functoid in a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="520d3-137">格線頁中的連結是由左向右處理。</span><span class="sxs-lookup"><span data-stu-id="520d3-137">Links are processed left-to-right in a grid page.</span></span> <span data-ttu-id="520d3-138">您無法建立從某個運算質連至其正上方或正下方的另一個運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-138">You cannot make a link from one functoid to another functoid directly above or below it.</span></span> <span data-ttu-id="520d3-139">運算質之間的連結將解譯為某個連結表示從運算質往左的輸出，及往右到運算值的輸入。</span><span class="sxs-lookup"><span data-stu-id="520d3-139">Links between functoids are interpreted such that a link signifies output from the functoid to the left and input to the functoid to the right.</span></span>  
  
### <a name="to-change-the-endpoint-of-a-link"></a><span data-ttu-id="520d3-140">變更連結的端點</span><span class="sxs-lookup"><span data-stu-id="520d3-140">To change the endpoint of a link</span></span>  
 <span data-ttu-id="520d3-141">在對應中，您可以拖曳連結的端點並放在另一個節點或運算質上。</span><span class="sxs-lookup"><span data-stu-id="520d3-141">In a map, you can drag an endpoint of a link and drop it over another node or functoid.</span></span>  
  
 <span data-ttu-id="520d3-142">若要變更連結的端點：</span><span class="sxs-lookup"><span data-stu-id="520d3-142">To change the endpoint of a link:</span></span>  
  
1. <span data-ttu-id="520d3-143">按一下您要變更來源或目的地節點/運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-143">Click the link for which you want to change the source or destination node/functoid.</span></span> <span data-ttu-id="520d3-144">連結的端點變成粗體。</span><span class="sxs-lookup"><span data-stu-id="520d3-144">The endpoints of the link become bold.</span></span>  
  
2. <span data-ttu-id="520d3-145">按住滑鼠上的索引鍵的任何粗體的端點，並將所需的節點/運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-145">Hold down the mouse key on any of the bold endpoints and drag the link to the desired node/functoid.</span></span> <span data-ttu-id="520d3-146">這會變更至新的節點/運算質從先前的節點/運算質連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-146">This changes the linking from the previous node/functoid to the new node/functoid.</span></span>  
  
   <span data-ttu-id="520d3-147">不過，您無法執行這項作業無效連結，例如：</span><span class="sxs-lookup"><span data-stu-id="520d3-147">However, you cannot perform this operation for invalid linking, such as:</span></span>  
  
-   <span data-ttu-id="520d3-148">將連結加入做為日期/時間運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="520d3-148">Adding a link as an input to Date/Time functoids.</span></span> <span data-ttu-id="520d3-149">日期/時間運算質不需要任何輸入的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-149">The Date/Time functoids do not need any input links.</span></span>  
  
-   <span data-ttu-id="520d3-150">複製與中繼的運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="520d3-150">Duplicating links from intermediate functoids.</span></span>  
  
     <span data-ttu-id="520d3-151">如果到 Node2，以及從 Node1 到 Node3 連結 Node1，您就無法變更，並將連結到 Node3 Node2 在拖曳連結的端點。</span><span class="sxs-lookup"><span data-stu-id="520d3-151">If you link Node1 to Node2, and also from Node1 to Node3, you cannot drag the endpoint of the link at Node2 to change and link to Node3.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520d3-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="520d3-152">See Also</span></span>  
 [<span data-ttu-id="520d3-153">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="520d3-153">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)