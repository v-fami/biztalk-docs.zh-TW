---
title: "節點階層層級比對 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Field nodes
- BizTalk Mapper, processing
- Record node
- BizTalk Mapper, compiler directives
- destination schemas, matching nodes
- source schemas, matching nodes
- maps, links
- Target Links property
- BizTalk Mapper, links
- compiler directives, matching schema nodes
- compiler directives, flattening source hierarchies
- maps, processing
ms.assetid: 5ba1ac77-0e70-4c58-9b8c-1b379dbbb3bd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b2d0c363abfefb9e3d0eb8abfb332c59539bb67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="node-hierarchy-level-matching"></a><span data-ttu-id="55724-102">節點階層層級比對</span><span class="sxs-lookup"><span data-stu-id="55724-102">Node-Hierarchy Level Matching</span></span>
<span data-ttu-id="55724-103">BizTalk 對應工具可讓您設定連結屬性以控制編譯器與來源與目的結構描述之間的節點階層比對的方式。</span><span class="sxs-lookup"><span data-stu-id="55724-103">BizTalk Mapper enables you to configure a link property to control how the compiler matches node hierarchies between the source and destination schemas.</span></span> <span data-ttu-id="55724-104">當您在來源結構描述的欄位與目的結構描述的欄位之間建立連結時，BizTalk 對應工具會自動新增編譯器連結。</span><span class="sxs-lookup"><span data-stu-id="55724-104">When you create a link from a field in the source schema to a field in the destination schema, BizTalk Mapper automatically adds compiler links.</span></span> <span data-ttu-id="55724-105">這些編譯器連結視您所選取的比對而定。</span><span class="sxs-lookup"><span data-stu-id="55724-105">These compiler links depend on the matching you select.</span></span>  
  
 <span data-ttu-id="55724-106">當您在顯示的格線頁中選取的連結時，其中一個屬性顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗是**目標連結**屬性。</span><span class="sxs-lookup"><span data-stu-id="55724-106">When you select a link in the displayed grid page, one of the properties displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window is the **Target Links** property.</span></span> <span data-ttu-id="55724-107">您可以為對應中的每個連結選擇以下可能的值：</span><span class="sxs-lookup"><span data-stu-id="55724-107">You can choose among the following possible values for each link in your map:</span></span>  
  
-   <span data-ttu-id="55724-108">**簡維連結。**</span><span class="sxs-lookup"><span data-stu-id="55724-108">**Flatten links.**</span></span> <span data-ttu-id="55724-109">使用此值將所有來源階層簡維至目的結構描述節點中的父記錄。</span><span class="sxs-lookup"><span data-stu-id="55724-109">Use this value to flatten all source hierarchies to the parent record in the destination schema node.</span></span>  
  
-   <span data-ttu-id="55724-110">**連結由上往下比對。**</span><span class="sxs-lookup"><span data-stu-id="55724-110">**Match links top down.**</span></span> <span data-ttu-id="55724-111">使用此值由結構描述上方至結構描述下方比對節點層級。</span><span class="sxs-lookup"><span data-stu-id="55724-111">Use this value to match node levels from the top of the schemas to the bottom of the schemas.</span></span>  
  
-   <span data-ttu-id="55724-112">**比對下往上連結。**</span><span class="sxs-lookup"><span data-stu-id="55724-112">**Match links bottom up.**</span></span> <span data-ttu-id="55724-113">使用此值由結構描述下方至結構描述上方比對節點層級。</span><span class="sxs-lookup"><span data-stu-id="55724-113">Use this value to match node levels from the bottom of the schemas to the top of the schemas.</span></span>  
  
## <a name="flatten-links"></a><span data-ttu-id="55724-114">簡維連結</span><span class="sxs-lookup"><span data-stu-id="55724-114">Flatten Links</span></span>  
 <span data-ttu-id="55724-115">在此模式中，將所有來源階層簡維至目的節點的父記錄。</span><span class="sxs-lookup"><span data-stu-id="55724-115">In this mode, all the source hierarchies are flattened to the parent record of the destination node.</span></span> <span data-ttu-id="55724-116">在第一例中，來源結構描述比目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-116">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="55724-117">在第二例中，目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-117">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-flatten.gif "bts_tls_flatten")  
<span data-ttu-id="55724-118">簡維連結</span><span class="sxs-lookup"><span data-stu-id="55724-118">Flatten Links</span></span>  
  
 ![](../core/media/bts-tls-flatten-2.gif "bts_tls_flatten_2")  
<span data-ttu-id="55724-119">簡維連結，第二例</span><span class="sxs-lookup"><span data-stu-id="55724-119">Flatten Links, Second Case</span></span>  
  
## <a name="match-links-top-down"></a><span data-ttu-id="55724-120">由上往下比對連結</span><span class="sxs-lookup"><span data-stu-id="55724-120">Match Links Top-Down</span></span>  
 <span data-ttu-id="55724-121">此模式由上往下比對層級。</span><span class="sxs-lookup"><span data-stu-id="55724-121">This mode matches level to level from the top down.</span></span> <span data-ttu-id="55724-122">在第一例中，來源結構描述比目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-122">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="55724-123">在第二例中，目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-123">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-topdown.gif "bts_tls_topdown")  
<span data-ttu-id="55724-124">由上往下比對</span><span class="sxs-lookup"><span data-stu-id="55724-124">Top-Down Matching</span></span>  
  
 ![](../core/media/bts-tls-topdown-2.gif "bts_tls_topdown_2")  
<span data-ttu-id="55724-125">由上往下比對，第二例</span><span class="sxs-lookup"><span data-stu-id="55724-125">Top-Down Matching, Second Case</span></span>  
  
## <a name="match-links-bottom-up"></a><span data-ttu-id="55724-126">由下往上比對連結</span><span class="sxs-lookup"><span data-stu-id="55724-126">Match Links Bottom-Up</span></span>  
 <span data-ttu-id="55724-127">此模式由下往上比對層級。</span><span class="sxs-lookup"><span data-stu-id="55724-127">This mode matches level to level from the bottom up.</span></span> <span data-ttu-id="55724-128">在第一例中，來源結構描述比目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-128">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="55724-129">在第二例中，目的結構描述較為複雜。</span><span class="sxs-lookup"><span data-stu-id="55724-129">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-bottomup.gif "bts_tls_bottomup")  
<span data-ttu-id="55724-130">由下往上比對</span><span class="sxs-lookup"><span data-stu-id="55724-130">Bottom-Up Matching</span></span>  
  
 ![](../core/media/bts-tls-bottomup-2.gif "bts_tls_bottomup_2")  
<span data-ttu-id="55724-131">由下往上比對，第二例</span><span class="sxs-lookup"><span data-stu-id="55724-131">Bottom-Up Matching, Second Case</span></span>  
  
## <a name="how-biztalk-mapper-processes-link-types"></a><span data-ttu-id="55724-132">BizTalk 對應工具如何處理連結類型</span><span class="sxs-lookup"><span data-stu-id="55724-132">How BizTalk Mapper Processes Link Types</span></span>  
 <span data-ttu-id="55724-133">因為您可以設定**目標連結**為不同的連結的不同值的屬性，BizTalk 對應工具需要解決它們衝突時的不同設定的方法。</span><span class="sxs-lookup"><span data-stu-id="55724-133">Because you can set the **Target Links** property to different values for different links, BizTalk Mapper needs a way to resolve the different settings when they may conflict.</span></span>  
  
 <span data-ttu-id="55724-134">例如，如果您使用簡維編譯器指示詞、 由上而下編譯器指示詞和由下往上編譯器指示詞從連結的**欄位**節點**欄位**中目的結構描述，而這些節點節點共用相同的父系**記錄**節點，BizTalk 對應工具會忽略衝突的由上而下和由下往上編譯器指示詞，並將所有連結當作已設定簡維編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="55724-134">For example, if you use a flatten compiler directive, a top-down compiler directive, and a bottom-up compiler directive for links from **Field** nodes to **Field** nodes in the destination schema, and these nodes share the same parent **Record** node, BizTalk Mapper ignores the conflicting top-down and bottom-up compiler directives and treats all the links as if they were set to the flatten compiler directive.</span></span>  
  
 <span data-ttu-id="55724-135">下表顯示 BizTalk 對應工具如何處理連結**欄位**中相同的節點**記錄**目的結構描述中的節點為基礎的設定**目標連結**在相同的連結屬性**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="55724-135">The following table shows how BizTalk Mapper treats links to **Field** nodes in the same **Record** node in the destination schema, based on the settings for the **Target Links** property for the links within the same **Record** node.</span></span>  
  
|<span data-ttu-id="55724-136">簡維</span><span class="sxs-lookup"><span data-stu-id="55724-136">Flatten</span></span>|<span data-ttu-id="55724-137">由上往下</span><span class="sxs-lookup"><span data-stu-id="55724-137">Top-down</span></span>|<span data-ttu-id="55724-138">由下往上</span><span class="sxs-lookup"><span data-stu-id="55724-138">Bottom-up</span></span>|<span data-ttu-id="55724-139">結果</span><span class="sxs-lookup"><span data-stu-id="55724-139">Result</span></span>|  
|-------------|---------------|----------------|------------|  
|<span data-ttu-id="55724-140">0 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-140">0 or more</span></span>|<span data-ttu-id="55724-141">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-141">1 or more</span></span>|<span data-ttu-id="55724-142">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-142">1 or more</span></span>|<span data-ttu-id="55724-143">BizTalk 對應工具將所有連結當作已設定為簡維編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="55724-143">BizTalk Mapper treats all the links as if they were set to the flatten compiler directive.</span></span>|  
|<span data-ttu-id="55724-144">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-144">1 or more</span></span>|<span data-ttu-id="55724-145">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-145">1 or more</span></span>|<span data-ttu-id="55724-146">0</span><span class="sxs-lookup"><span data-stu-id="55724-146">0</span></span>|<span data-ttu-id="55724-147">BizTalk 對應工具將所有連結當作已設定為由上往下編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="55724-147">BizTalk Mapper treats all the links as if they were set to the top-down compiler directive.</span></span>|  
|<span data-ttu-id="55724-148">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-148">1 or more</span></span>|<span data-ttu-id="55724-149">0</span><span class="sxs-lookup"><span data-stu-id="55724-149">0</span></span>|<span data-ttu-id="55724-150">1 或更多</span><span class="sxs-lookup"><span data-stu-id="55724-150">1 or more</span></span>|<span data-ttu-id="55724-151">BizTalk 對應工具將所有連結當作已設定為由下往上編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="55724-151">BizTalk Mapper treats all the links as if they were set to the bottom-up compiler directive.</span></span>|  
  
 <span data-ttu-id="55724-152">由上往下和由下往上編譯器指示詞的優先順序高於簡維編譯器指示詞，但兩者均存在時會相互抵銷。</span><span class="sxs-lookup"><span data-stu-id="55724-152">The top-down and bottom-up compiler directives take precedence over the flatten compiler directive, but cancel each other out when both are present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55724-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55724-153">See Also</span></span>  
 <span data-ttu-id="55724-154">[大量複製運算質](../core/mass-copy-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="55724-154">[Mass Copy Functoid](../core/mass-copy-functoid.md) </span></span>  
 <span data-ttu-id="55724-155">[如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md) </span><span class="sxs-lookup"><span data-stu-id="55724-155">[How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md) </span></span>  
 [<span data-ttu-id="55724-156">編譯對應</span><span class="sxs-lookup"><span data-stu-id="55724-156">Compiling Maps</span></span>](../core/compiling-maps.md)