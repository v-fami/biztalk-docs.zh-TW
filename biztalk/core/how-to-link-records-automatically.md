---
title: 如何自動連結記錄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc2926c7-07c2-45d1-afde-d3f894f6b88d
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5ab4e18a291321247655101d32d2bf7e35ff92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254846"
---
# <a name="how-to-link-records-automatically"></a><span data-ttu-id="61cd4-102">如何自動連結記錄</span><span class="sxs-lookup"><span data-stu-id="61cd4-102">How to Link Records Automatically</span></span>
<span data-ttu-id="61cd4-103">當您在來源與目的結構描述的兩個記錄項目間建立連結時，BizTalk 對應工具可透過捷徑功能表為您提供即時的協助。</span><span class="sxs-lookup"><span data-stu-id="61cd4-103">The BizTalk Mapper provides you with just-in-time assistance, through a shortcut menu, when you create links between two record elements of source and destination schemas.</span></span> <span data-ttu-id="61cd4-104">本主題提供如何使用捷徑功能表來執行連結作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="61cd4-104">This topic provides information about how to use the shortcut menu to perform the linking operations.</span></span>  
  
 <span data-ttu-id="61cd4-105">您可以使用下列方式來自動建立記錄與記錄間的連結：</span><span class="sxs-lookup"><span data-stu-id="61cd4-105">You can create record-to-record links automatically in the following ways:</span></span>  
  
-   <span data-ttu-id="61cd4-106">**直接連結。**</span><span class="sxs-lookup"><span data-stu-id="61cd4-106">**Direct Link.**</span></span> <span data-ttu-id="61cd4-107">使用此技術，BizTalk 對應工具會將來源結構描述中的記錄連結到目的結構描述中的選定記錄。</span><span class="sxs-lookup"><span data-stu-id="61cd4-107">Using this technique, the BizTalk Mapper links the record from source schema to the selected record in the destination schema.</span></span>  
  
-   <span data-ttu-id="61cd4-108">**依結構連結。**</span><span class="sxs-lookup"><span data-stu-id="61cd4-108">**Link by Structure.**</span></span> <span data-ttu-id="61cd4-109">使用這項技術，BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**節點所根據的那些結構連結**記錄**節點，不論這些結構內之相對應節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="61cd4-109">Using this technique, the BizTalk Mapper attempts to match the **Record** and **Field** nodes within the **Record** nodes being linked according to the structures of those **Record** nodes, regardless of names of the corresponding nodes within those structures.</span></span>  
  
-   <span data-ttu-id="61cd4-110">**依名稱連結。**</span><span class="sxs-lookup"><span data-stu-id="61cd4-110">**Link By Name.**</span></span> <span data-ttu-id="61cd4-111">使用這項技術，BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**根據名稱所連結的節點在對應節點，不論其結構，**記錄**所連結的節點。</span><span class="sxs-lookup"><span data-stu-id="61cd4-111">Using this technique, the BizTalk Mapper attempts to match the **Record** and **Field** nodes within the **Record** nodes being linked according to the names of the corresponding nodes, regardless of their structure, within the **Record** nodes being linked.</span></span>  
  
-   <span data-ttu-id="61cd4-112">**大量複製。**</span><span class="sxs-lookup"><span data-stu-id="61cd4-112">**Mass Copy.**</span></span> <span data-ttu-id="61cd4-113">**大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。</span><span class="sxs-lookup"><span data-stu-id="61cd4-113">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="61cd4-114">提供在 BizTalk 對應工具運算質的詳細資訊，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="61cd4-114">For information about the functoids available in BizTalk Mapper, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).</span></span>  
  
 <span data-ttu-id="61cd4-115">若要使用捷徑功能表，必須有個連結源自某個子階層父節點，並且終於另一個子階層父節點。</span><span class="sxs-lookup"><span data-stu-id="61cd4-115">To use the shortcut menu, a link must originate from a sub-hierarchy parent node and must end on another sub-hierarchy parent node.</span></span> <span data-ttu-id="61cd4-116">捷徑功能表的作用，在於協助您判斷在兩個結構描述節點之間應建立哪種類型的連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-116">The shortcut menu assists in what type of links should be created between the two schema nodes.</span></span> <span data-ttu-id="61cd4-117">以下是捷徑功能表上可用的選項清單。</span><span class="sxs-lookup"><span data-stu-id="61cd4-117">The following is a list of options available on the shortcut menu.</span></span>  
  
|<span data-ttu-id="61cd4-118">對應自</span><span class="sxs-lookup"><span data-stu-id="61cd4-118">Map from</span></span>|<span data-ttu-id="61cd4-119">對應至</span><span class="sxs-lookup"><span data-stu-id="61cd4-119">Map to</span></span>|<span data-ttu-id="61cd4-120">連結行為</span><span class="sxs-lookup"><span data-stu-id="61cd4-120">Link Behavior</span></span>|  
|--------------|------------|-------------------|  
|<span data-ttu-id="61cd4-121">欄位</span><span class="sxs-lookup"><span data-stu-id="61cd4-121">Field</span></span>|<span data-ttu-id="61cd4-122">欄位</span><span class="sxs-lookup"><span data-stu-id="61cd4-122">Field</span></span>|<span data-ttu-id="61cd4-123">直接連結</span><span class="sxs-lookup"><span data-stu-id="61cd4-123">Direct link</span></span>|  
|<span data-ttu-id="61cd4-124">記錄</span><span class="sxs-lookup"><span data-stu-id="61cd4-124">Record</span></span>|<span data-ttu-id="61cd4-125">欄位</span><span class="sxs-lookup"><span data-stu-id="61cd4-125">Field</span></span>|<span data-ttu-id="61cd4-126">直接連結</span><span class="sxs-lookup"><span data-stu-id="61cd4-126">Direct link</span></span>|  
|<span data-ttu-id="61cd4-127">欄位</span><span class="sxs-lookup"><span data-stu-id="61cd4-127">Field</span></span>|<span data-ttu-id="61cd4-128">記錄</span><span class="sxs-lookup"><span data-stu-id="61cd4-128">Record</span></span>|<span data-ttu-id="61cd4-129">直接連結</span><span class="sxs-lookup"><span data-stu-id="61cd4-129">Direct link</span></span>|  
|<span data-ttu-id="61cd4-130">記錄</span><span class="sxs-lookup"><span data-stu-id="61cd4-130">Record</span></span>|<span data-ttu-id="61cd4-131">記錄</span><span class="sxs-lookup"><span data-stu-id="61cd4-131">Record</span></span>|<span data-ttu-id="61cd4-132">會出現捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="61cd4-132">Shortcut menu appears</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="61cd4-133">必要條件</span><span class="sxs-lookup"><span data-stu-id="61cd4-133">Prerequisites</span></span>  
 <span data-ttu-id="61cd4-134">這些作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="61cd4-134">These operations require that the BizTalk Mapper is running.</span></span>  
  
### <a name="to-link-the-record-elements-directly"></a><span data-ttu-id="61cd4-135">若要直接連結記錄項目</span><span class="sxs-lookup"><span data-stu-id="61cd4-135">To link the record elements directly</span></span>  
  
1.  <span data-ttu-id="61cd4-136">從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="61cd4-136">Drag the mouse from a sub-hierarchy parent node in source schema, and then drop it to the sub-hierarchy parent node in the target schema.</span></span>  
  
2.  <span data-ttu-id="61cd4-137">在捷徑功能表，按一下 **直接連結**。</span><span class="sxs-lookup"><span data-stu-id="61cd4-137">On the shortcut menu, click **Direct Link**.</span></span> <span data-ttu-id="61cd4-138">下圖顯示隨即出現的從所選來源節點到目標節點的直接連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-138">The following figure shows a direct link appearing from the selected source node to the target node.</span></span>  
  
     <span data-ttu-id="61cd4-139">![從來源節點至目標節點的直接連結](../core/media/linkrecordelements-directly.gif "Linkrecordelements_directly")</span><span class="sxs-lookup"><span data-stu-id="61cd4-139">![Direct link from source node to target node](../core/media/linkrecordelements-directly.gif "Linkrecordelements_directly")</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="61cd4-140">您可以建立從來源結構描述的子階層父節點，到目標結構描述的非子階層父節點的直接連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-140">You can place a direct link from a sub-hierarchy parent node in source schema to a non-sub-hierarchy parent node in target schema.</span></span> <span data-ttu-id="61cd4-141">下圖顯示從 “Root” (來源結構描述的父節點) 到 “Record1” (目標結構描述中 “Root” 的子項) 的直接連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-141">The following figure shows a direct link from “Root” that is a parent node in source schema to “Record1” that is a child to “Root” in target schema.</span></span>  
  
     <span data-ttu-id="61cd4-142">![直接連結記錄元素](../core/media/linkrecordelements-directly2.gif "Linkrecordelements_directly2")</span><span class="sxs-lookup"><span data-stu-id="61cd4-142">![Linking record elements directly](../core/media/linkrecordelements-directly2.gif "Linkrecordelements_directly2")</span></span>  
  
### <a name="to-link-the-record-elements-by-structure"></a><span data-ttu-id="61cd4-143">若要依結構來連結記錄項目</span><span class="sxs-lookup"><span data-stu-id="61cd4-143">To link the record elements by structure</span></span>  
  
1.  <span data-ttu-id="61cd4-144">從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="61cd4-144">Drag the mouse from a sub-hierarchy parent node in source schema, and then drop it to the sub-hierarchy parent node in the target schema.</span></span>  
  
2.  <span data-ttu-id="61cd4-145">在捷徑功能表，按一下 **依結構連結**。</span><span class="sxs-lookup"><span data-stu-id="61cd4-145">On the shortcut menu, click **Link by Structure**.</span></span> <span data-ttu-id="61cd4-146">BizTalk 對應工具符合**記錄**和**欄位**節點內**記錄**節點的結構根據要進行連結**記錄**節點，不論這些結構內之相對應節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="61cd4-146">The BizTalk Mapper matches the **Record** and **Field** nodes within the **Record** nodes being linked according to the structure of those **Record** nodes, regardless of names of the corresponding nodes within those structures.</span></span>  
  
     <span data-ttu-id="61cd4-147">![連結記錄項目) (&#95; 結構](../core/media/linkrecordelements-bystructure.gif "Linkrecordelements_bystructure")</span><span class="sxs-lookup"><span data-stu-id="61cd4-147">![Link record elements&#95;by structure](../core/media/linkrecordelements-bystructure.gif "Linkrecordelements_bystructure")</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="61cd4-148">當您嘗試將來源結構描述的子階層父節點連結到目標結構描述的非子階層父節點時，BizTalk 對應工具會依結構，將來源父節點的子項，分別對應到目標父節點的子項。</span><span class="sxs-lookup"><span data-stu-id="61cd4-148">When you try to link a sub-hierarchy parent node in source schema to a non-sub-hierarchy parent node in target schema, by structure, the BizTalk Mapper maps the children of the source parent node to the children of the target parent node, respectively.</span></span> <span data-ttu-id="61cd4-149">下圖顯示依結構進行的連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-149">The following figure shows the linking by structure.</span></span>  
  
     <span data-ttu-id="61cd4-150">![依結構連結記錄元素](../core/media/linkrecordelements-bystructure2.gif "Linkrecordelements_bystructure2")</span><span class="sxs-lookup"><span data-stu-id="61cd4-150">![Linking record elements by structure](../core/media/linkrecordelements-bystructure2.gif "Linkrecordelements_bystructure2")</span></span>  
  
### <a name="to-link-the-record-elements-by-name"></a><span data-ttu-id="61cd4-151">若要依名稱來連結記錄項目</span><span class="sxs-lookup"><span data-stu-id="61cd4-151">To link the record elements by name</span></span>  
  
1.  <span data-ttu-id="61cd4-152">從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="61cd4-152">Drag the mouse from a sub-hierarchy parent node in source schema, and then drop it to the sub-hierarchy parent node in the target schema.</span></span>  
  
2.  <span data-ttu-id="61cd4-153">在捷徑功能表，按一下 **依名稱連結**。</span><span class="sxs-lookup"><span data-stu-id="61cd4-153">On the shortcut menu, click **Link by Name**.</span></span> <span data-ttu-id="61cd4-154">BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**根據對應的節點名稱，不論所連結的節點其結構的內**記錄**您要連結的節點。</span><span class="sxs-lookup"><span data-stu-id="61cd4-154">The BizTalk Mapper attempts to match the **Record** and **Field** nodes within the **Record** nodes being linked according to the names of the corresponding nodes, regardless of their structure, within the **Record** nodes to which you are linking.</span></span>  
  
     <span data-ttu-id="61cd4-155">![依名稱連結記錄元素](../core/media/linkrecordelements-byname.gif "Linkrecordelements_byname")</span><span class="sxs-lookup"><span data-stu-id="61cd4-155">![Linking record elements by name](../core/media/linkrecordelements-byname.gif "Linkrecordelements_byname")</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="61cd4-156">您可以將來源結構描述的子階層父節點，依名稱連結到目標結構描述的非子階層父節點。</span><span class="sxs-lookup"><span data-stu-id="61cd4-156">You can link a sub-hierarchy parent node in source schema to a non-sub-hierarchy parent node in target schema, by name.</span></span> <span data-ttu-id="61cd4-157">BizTalk 對應工具會將來源節點子項與目標節點子項的名稱進行對應。</span><span class="sxs-lookup"><span data-stu-id="61cd4-157">The BizTalk Mapper matches the names of the children of source node with the children of target node.</span></span> <span data-ttu-id="61cd4-158">如果找到相同的子項，就會在相應的子項之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="61cd4-158">If it finds identical children, then a link is established between the respective children.</span></span> <span data-ttu-id="61cd4-159">下圖說明此概念。</span><span class="sxs-lookup"><span data-stu-id="61cd4-159">The following figure explains this concept.</span></span>  
  
## <a name="to-link-using-a-mass-copy-functoid"></a><span data-ttu-id="61cd4-160">若要使用大量複製運算質來進行連結</span><span class="sxs-lookup"><span data-stu-id="61cd4-160">To link using a mass copy functoid</span></span>  
 <span data-ttu-id="61cd4-161">**大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。</span><span class="sxs-lookup"><span data-stu-id="61cd4-161">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="61cd4-162">這些項目實際上是以 XML 結構描述定義語言提供的萬用字元對應未知的結構或屬性。</span><span class="sxs-lookup"><span data-stu-id="61cd4-162">These elements are, in essence, wildcards provided in the XML Schema definition language to match unknown structures or attributes.</span></span>  
  
 <span data-ttu-id="61cd4-163">除了處理具有未知結構的資料**大量複製**運算質可讓您簡化結構描述開發： 需要詳細指定只將處理結構描述的部分。</span><span class="sxs-lookup"><span data-stu-id="61cd4-163">In addition to handling data with unknown structure, the **Mass Copy** functoid enables you to simplify schema development: only the portions of a schema that will be processed need to be specified in detail.</span></span>  
  
 <span data-ttu-id="61cd4-164">![依大量複製運算質連結記錄元素](../core/media/linkrecordelements-masscopyfunctoid.gif "Linkrecordelements_MassCopyfunctoid")</span><span class="sxs-lookup"><span data-stu-id="61cd4-164">![Linking record elements by Mass Copy functoid](../core/media/linkrecordelements-masscopyfunctoid.gif "Linkrecordelements_MassCopyfunctoid")</span></span>  
  
 <span data-ttu-id="61cd4-165">如需有關**大量複製**運算質，請參閱[大量複製運算質](../core/mass-copy-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="61cd4-165">For more information about the **Mass Copy** functoid, see [Mass Copy Functoid](../core/mass-copy-functoid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cd4-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61cd4-166">See Also</span></span>  
 <span data-ttu-id="61cd4-167">[使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="61cd4-167">[Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md) </span></span>  
 [<span data-ttu-id="61cd4-168">如何新增大量複製運算質至對應</span><span class="sxs-lookup"><span data-stu-id="61cd4-168">How to Add Mass Copy Functoids to a Map</span></span>](../core/how-to-add-mass-copy-functoids-to-a-map.md)