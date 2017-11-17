---
title: "類型的連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compiler directives, links
- elastic links [maps]
- maps, links
- BizTalk Mapper, links
- partial links [maps]
- fixed links [maps]
ms.assetid: 348fae77-2e25-4b79-93bb-d42f3d18a3f7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d6f1039e65989a2de0243a1a9a09f30165e603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-links"></a><span data-ttu-id="16a41-102">連結的類型</span><span class="sxs-lookup"><span data-stu-id="16a41-102">Types of Links</span></span>
<span data-ttu-id="16a41-103">下列清單摘要敘述可在「BizTalk 對應工具」中使用的各種連結類型：</span><span class="sxs-lookup"><span data-stu-id="16a41-103">The following list summarizes the various types of links available in BizTalk Mapper:</span></span>  
  
-   <span data-ttu-id="16a41-104">**彈性連結。**</span><span class="sxs-lookup"><span data-stu-id="16a41-104">**Elastic links.**</span></span> <span data-ttu-id="16a41-105">「彈性」這個詞表示這個連結已建立但兩邊端點尚未連接。</span><span class="sxs-lookup"><span data-stu-id="16a41-105">The term elastic applies to a link as it is being created, before both ends of the link are connected.</span></span> <span data-ttu-id="16a41-106">例如，當您從來源結構描述的欄位拖曳連結，但尚未連接到其在目的結構描述的對應欄位時，該連結就是彈性連結。</span><span class="sxs-lookup"><span data-stu-id="16a41-106">For example, if you are dragging a link from a field in the source schema, but you have not yet connected it to its corresponding field in the destination schema, the link is elastic.</span></span> <span data-ttu-id="16a41-107">當您完成整個連接時，此彈性連結就變成固定連結。</span><span class="sxs-lookup"><span data-stu-id="16a41-107">As you complete the connection, the elastic link becomes a fixed link.</span></span>  
  
     <span data-ttu-id="16a41-108">您可以將連結的其中一個端點拖曳至另一個節點或運算質。</span><span class="sxs-lookup"><span data-stu-id="16a41-108">You can drag one endpoint of a link to another node or a functoid.</span></span> <span data-ttu-id="16a41-109">如需連結取代的詳細資訊，請參閱[如何建立連結](../core/how-to-create-links.md)。</span><span class="sxs-lookup"><span data-stu-id="16a41-109">For more information about link replacement, see [How to Create Links](../core/how-to-create-links.md).</span></span>  
  
-   <span data-ttu-id="16a41-110">**固定連結。**</span><span class="sxs-lookup"><span data-stu-id="16a41-110">**Fixed Links.**</span></span> <span data-ttu-id="16a41-111">「固定」這個詞是指連結已明確建構以代表某值從某來源執行個體訊息移動到目的執行個體訊息，或至少部分代表該移動的特性。</span><span class="sxs-lookup"><span data-stu-id="16a41-111">The term fixed applies to a link that you have explicitly constructed to represent the movement of a value from a source instance message to a destination instance message, or at least a part of that movement.</span></span> <span data-ttu-id="16a41-112">固定直接連接的連結**記錄**或**欄位**來源結構描述中的節點**記錄**或**欄位**目的地中的節點結構描述代表直接複製資料在執行階段。</span><span class="sxs-lookup"><span data-stu-id="16a41-112">Fixed links that directly connect a **Record** or **Field** node in the source schema to a **Record** or **Field** node in the destination schema represent a straight copying of data at run time.</span></span> <span data-ttu-id="16a41-113">從端點或是另一個端點連接到運算質的固定連結，可代表資料在執行階段時從輸入執行個體訊息到輸出執行個體訊息的移動部分。</span><span class="sxs-lookup"><span data-stu-id="16a41-113">Fixed links connecting to a functoid at one end or the other represent part of the movement of data from an input instance message to an output instance message at run time.</span></span> <span data-ttu-id="16a41-114">透過幾個這類連結共同構成來源與目的結構描述之間的連結，便可以代表資料項目的整個移動部分。</span><span class="sxs-lookup"><span data-stu-id="16a41-114">Several of these together, completing the link between the source and destination schemas, represent the entire movement of an item of data.</span></span>  
  
-   <span data-ttu-id="16a41-115">**部分連結。**</span><span class="sxs-lookup"><span data-stu-id="16a41-115">**Partial links.**</span></span> <span data-ttu-id="16a41-116">部分的詞彙會套用到連結，您無法為其目前看到的確切**記錄**或**欄位**它們連線的來源或目的結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="16a41-116">The term partial applies to links for which you cannot currently see the exact **Record** or **Field** node to which they are connected in the source or destination schemas.</span></span> <span data-ttu-id="16a41-117">發生這種情況時**記錄**或**欄位**所連接的節點不會顯示因為其中一個上階節點已摺疊結構描述樹狀結構表示法中。</span><span class="sxs-lookup"><span data-stu-id="16a41-117">This occurs when the **Record** or **Field** node to which they are attached is not shown because one of its ancestor nodes is collapsed in the tree representation of the schema.</span></span> <span data-ttu-id="16a41-118">如需部分連結的詳細資訊，請參閱[如何最佳化連結顯示的](../core/how-to-optimize-the-display-of-links.md)。</span><span class="sxs-lookup"><span data-stu-id="16a41-118">For more information about partial links, see [How to Optimize the Display of Links](../core/how-to-optimize-the-display-of-links.md).</span></span>  
  
-   <span data-ttu-id="16a41-119">**編譯器連結。**</span><span class="sxs-lookup"><span data-stu-id="16a41-119">**Compiler links.**</span></span> <span data-ttu-id="16a41-120">「編譯器」這個詞是指建置 BizTalk 專案時，BizTalk 對應工具自動建立連結的特性。</span><span class="sxs-lookup"><span data-stu-id="16a41-120">The term compiler applies to links that BizTalk Mapper creates automatically when you build a BizTalk project.</span></span> <span data-ttu-id="16a41-121">例如，當您設定表格驅動迴圈時，編譯器連結會顯示分別位於來源結構描述和目的結構描述之記錄和欄位之間的關係和連結。</span><span class="sxs-lookup"><span data-stu-id="16a41-121">For example, if you configure table-driven looping, the compiler links show the relationship and the links between the records and fields in the source schema and the records and fields in the destination schema.</span></span> <span data-ttu-id="16a41-122">這類連結可以依編譯器指示詞自動產生，或是由使用者指示產生。</span><span class="sxs-lookup"><span data-stu-id="16a41-122">This type of link can be generated automatically by compiler directives, or it can be user-directed.</span></span>  
  
 <span data-ttu-id="16a41-123">依照預設，BizTalk 對應工具會應用不同顏色的線條顯示這些不同類型的連結，協助您辨識對應的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="16a41-123">BizTalk Mapper, by default, displays these various types of links using different colored lines to help you distinguish the detail of your maps.</span></span> <span data-ttu-id="16a41-124">您可以變更用於這些不同種類的連結的色彩**選項**命令**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="16a41-124">You can change the colors used for these different kinds of links with the **Options** command on the **Tools** menu.</span></span> <span data-ttu-id="16a41-125">如需色彩的變更如何呈現不同連結類別的詳細資訊，請參閱[如何自訂色彩和字型，在 BizTalk 對應工具](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="16a41-125">For more information about how change in color renders different categories of links, see [How to Customize Colors and Font in BizTalk Mapper](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a41-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16a41-126">See Also</span></span>  
 [<span data-ttu-id="16a41-127">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="16a41-127">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)