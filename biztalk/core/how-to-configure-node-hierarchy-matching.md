---
title: 如何設定節點階層比對 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5302e194-cbc7-4d26-b25b-eb4e38abfe23
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1eb785793b865e36c5b37bd6b32199ab3e34f5d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009575"
---
# <a name="how-to-configure-node-hierarchy-matching"></a><span data-ttu-id="aee57-102">如何設定節點階層比對</span><span class="sxs-lookup"><span data-stu-id="aee57-102">How to Configure Node Hierarchy Matching</span></span>
<span data-ttu-id="aee57-103">在對應中建立連結時，BizTalk 對應工具會自動建立編譯器連結以實作已建立的連結。</span><span class="sxs-lookup"><span data-stu-id="aee57-103">When you create a link in a map, the BizTalk Mapper automatically creates compiler links to implement the link you have drawn.</span></span> <span data-ttu-id="aee57-104">**目標連結**連結的屬性會控制 BizTalk 對應工具建立編譯器連結的方式。</span><span class="sxs-lookup"><span data-stu-id="aee57-104">The **Target Links** property of a link controls how the BizTalk Mapper draws the compiler links.</span></span> <span data-ttu-id="aee57-105">本主題提供如何設定目標連結的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="aee57-105">This topic provides information about how to set the target links.</span></span>  
  
 <span data-ttu-id="aee57-106">**來源連結**屬性會指定如何從來源節點擷取並套用至目的地節點值。</span><span class="sxs-lookup"><span data-stu-id="aee57-106">The **Source Links** property specifies how a value is retrieved from the source node and applied to the destination node.</span></span> <span data-ttu-id="aee57-107">如需有關如何設定來源連結的資訊，請參閱[如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md)。</span><span class="sxs-lookup"><span data-stu-id="aee57-107">For information about how to set source links, see [How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aee57-108">此作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="aee57-108">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-set-the-target-links-property"></a><span data-ttu-id="aee57-109">設定目標連結屬性</span><span class="sxs-lookup"><span data-stu-id="aee57-109">To set the Target Links property</span></span>  
  
1. <span data-ttu-id="aee57-110">在對應格線頁中，按一下要設定目標連結屬性的連結。</span><span class="sxs-lookup"><span data-stu-id="aee57-110">On the map grid page, click a link to which you want to set the target links property.</span></span>  
  
2. <span data-ttu-id="aee57-111">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**屬性**視窗中，將**目標連結**屬性設為其中包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="aee57-111">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**Properties** window, set the **Target Links** property to one of the following choices:</span></span>  
  
   -   <span data-ttu-id="aee57-112">**簡維連結。**</span><span class="sxs-lookup"><span data-stu-id="aee57-112">**Flatten Links.**</span></span> <span data-ttu-id="aee57-113">來源記錄節點中的階層簡維至目的結構描述中的連結到記錄節點。</span><span class="sxs-lookup"><span data-stu-id="aee57-113">The hierarchy in the source record node is flattened to the linked-to-record node in the destination schema.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="aee57-114">根據預設，BizTalk 對應工具會將**目標連結**屬性設**壓平合併**。</span><span class="sxs-lookup"><span data-stu-id="aee57-114">By default, the BizTalk Mapper sets the **Target Links** property to **Flatten**.</span></span>  
  
   -   <span data-ttu-id="aee57-115">**相符項目連結的由上往下。**</span><span class="sxs-lookup"><span data-stu-id="aee57-115">**Match Links Top Down.**</span></span> <span data-ttu-id="aee57-116">節點比對是由上往下以層級對層級的比對方式執行。</span><span class="sxs-lookup"><span data-stu-id="aee57-116">Node matching is performed level-to-level from the top down.</span></span>  
  
   -   <span data-ttu-id="aee57-117">**比對下往上連結。**</span><span class="sxs-lookup"><span data-stu-id="aee57-117">**Match Links Bottom Up.**</span></span> <span data-ttu-id="aee57-118">節點比對是由下往上以層級對層級的比對方式執行。</span><span class="sxs-lookup"><span data-stu-id="aee57-118">Node matching is performed level-to-level from the bottom up.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee57-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aee57-119">See Also</span></span>  
 <span data-ttu-id="aee57-120">[節點階層層級比對](../core/node-hierarchy-level-matching.md) </span><span class="sxs-lookup"><span data-stu-id="aee57-120">[Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md) </span></span>  
 <span data-ttu-id="aee57-121">[編譯器指示詞和連結](../core/compiler-directives-and-links.md) </span><span class="sxs-lookup"><span data-stu-id="aee57-121">[Compiler Directives and Links](../core/compiler-directives-and-links.md) </span></span>  
 [<span data-ttu-id="aee57-122">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="aee57-122">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)