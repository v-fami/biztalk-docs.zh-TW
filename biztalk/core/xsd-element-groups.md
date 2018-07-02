---
title: XSD 項目群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XSLT, XSLT variations
- BizTalk Mapper, XSLT variations
- maps, groups
- Choice Group node
- XSD element groups
- XSLT, warnings
ms.assetid: a6ea22cb-6066-480e-8a2a-75fade3e5970
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80b6fdd65067599ed14c37ff00507279ce9b2f47
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006687"
---
# <a name="xsd-element-groups"></a><span data-ttu-id="3c70e-102">XSD 項目群組</span><span class="sxs-lookup"><span data-stu-id="3c70e-102">XSD Element Groups</span></span>
<span data-ttu-id="3c70e-103">在結構描述中使用某些特定的結構，可能會在 BizTalk 對應工具所產生的「可延伸樣式語言轉換」(Extensible Stylesheet Language Transformations，XSLT) 中製造一些變化。</span><span class="sxs-lookup"><span data-stu-id="3c70e-103">The use of certain structures in a schema may create variations in the Extensible Stylesheet Language Transformations (XSLT) that BizTalk Mapper generates.</span></span>  
  
 <span data-ttu-id="3c70e-104">在定義 Sequence、Choice 或所有項目群組的對應包括結構描述時，就會發生這個變化。</span><span class="sxs-lookup"><span data-stu-id="3c70e-104">This can occur when you include a schema in your map that defines sequence, choice, or all element groups.</span></span> <span data-ttu-id="3c70e-105">例如，如果您使用的結構描述包括**Choice 群組**節點，就可以為您建立的地圖，需要兩個以上的子系**Choice 群組**才會出現在輸出執行個體的節點訊息。</span><span class="sxs-lookup"><span data-stu-id="3c70e-105">For example, if you use a schema that includes a **Choice Group** node, it is possible for you to create a map that requires two or more of the children of the **Choice Group** node to appear in an output instance message.</span></span> <span data-ttu-id="3c70e-106">在此例中，BizTalk 對應工具會在您編譯對應時顯示警告。</span><span class="sxs-lookup"><span data-stu-id="3c70e-106">In this case, BizTalk Mapper displays a warning when you compile the map.</span></span> <span data-ttu-id="3c70e-107">此項警告會告知您，在您已對應的必要欄位中，只有一個可以在執行階段中填入父迴圈的相同重複項目中。</span><span class="sxs-lookup"><span data-stu-id="3c70e-107">The warning tells you that only one of the required fields you have mapped may be populated in the same iteration of the parent loop at run time.</span></span> <span data-ttu-id="3c70e-108">BizTalk 對應工具不會提供錯誤訊息，來告知您的對應邏輯不正確。</span><span class="sxs-lookup"><span data-stu-id="3c70e-108">BizTalk Mapper does not give you an error message stating that your mapping logic is incorrect.</span></span>  
  
 <span data-ttu-id="3c70e-109">若符合下列條件，您將能夠在 XSLT 中產生變化：</span><span class="sxs-lookup"><span data-stu-id="3c70e-109">Another situation in which you might generate variations in the XSLT is when the following conditions are met:</span></span>  
  
- <span data-ttu-id="3c70e-110">**A 記錄**其子**欄位項目 B**。</span><span class="sxs-lookup"><span data-stu-id="3c70e-110">**Record A** has a child **Field Element B**.</span></span>  
  
- <span data-ttu-id="3c70e-111">**記錄 A**和子系**欄位項目 B**出現一次。</span><span class="sxs-lookup"><span data-stu-id="3c70e-111">**Record A** and child **Field Element B** occur once.</span></span>  
  
- <span data-ttu-id="3c70e-112">**A 記錄**屬於**Choice 群組**重複。</span><span class="sxs-lookup"><span data-stu-id="3c70e-112">**Record A** is part of a **Choice Group** that repeats.</span></span>  
  
  <span data-ttu-id="3c70e-113">在此狀況中，BizTalk 對應工具所產生的 XSLT 會包含重複項目邏輯，以處理來源記錄產生許多變化的可能性。</span><span class="sxs-lookup"><span data-stu-id="3c70e-113">In this situation, BizTalk Mapper generates XSLT that contains iteration logic to handle the possibility of the many variations of the source records.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c70e-114">您必須明確了解所涉及之群組的對應。</span><span class="sxs-lookup"><span data-stu-id="3c70e-114">You must be explicit with respect to mappings involving groups.</span></span> <span data-ttu-id="3c70e-115">例如，若目的結構描述**Choice 群組**節點有子節點 A 和 B，不正確擁有 A 和 B，同時在其父群組中的相同重複項目上。</span><span class="sxs-lookup"><span data-stu-id="3c70e-115">For example, if a destination schema contains a **Choice Group** node with child nodes A and B, it is not valid to have A and B simultaneously on the same iteration of their parent group.</span></span> <span data-ttu-id="3c70e-116">BizTalk 對應工具並不會阻止您建立無效的對應。</span><span class="sxs-lookup"><span data-stu-id="3c70e-116">BizTalk Mapper does not prevent you from creating mappings that are not valid.</span></span> <span data-ttu-id="3c70e-117">所以，您必須使用邏輯運算質來設定對應，讓 A 和 B 永遠不同時出現。</span><span class="sxs-lookup"><span data-stu-id="3c70e-117">Therefore, you must use logical functoids to set up mappings in which A and B can never occur at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c70e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c70e-118">See Also</span></span>  
 <span data-ttu-id="3c70e-119">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="3c70e-119">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="3c70e-120">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="3c70e-120">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)