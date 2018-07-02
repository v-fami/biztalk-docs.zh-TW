---
title: 如何設定來源連結編譯器值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ad777bc5b4df2717d20fd95aa60fdf5d59d1f6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975167"
---
# <a name="how-to-set-the-source-links-compiler-value"></a><span data-ttu-id="ac41b-102">如何設定來源連結編譯器值</span><span class="sxs-lookup"><span data-stu-id="ac41b-102">How to Set the Source Links Compiler Value</span></span>
<span data-ttu-id="ac41b-103">您可以使用**來源連結**來指定從來源節點擷取及套用到目的地節點值的方式連結的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac41b-103">You can use the **Source Links** property of a link to specify how a value is retrieved from the source node and applied to the destination node.</span></span> <span data-ttu-id="ac41b-104">本主題說明可用的選項以及如何在其中選擇。</span><span class="sxs-lookup"><span data-stu-id="ac41b-104">This topic explains the available choices and how to choose among them.</span></span>  
  
### <a name="to-set-the-source-links-link-property"></a><span data-ttu-id="ac41b-105">設定來源連結連結屬性</span><span class="sxs-lookup"><span data-stu-id="ac41b-105">To set the Source Links link property</span></span>  
  
1. <span data-ttu-id="ac41b-106">在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。</span><span class="sxs-lookup"><span data-stu-id="ac41b-106">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
    <span data-ttu-id="ac41b-107">格線頁中所選連結的端點會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ac41b-107">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2. <span data-ttu-id="ac41b-108">在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性] 視窗中，設定**來源連結**屬性設為其中包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="ac41b-108">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, set the **Source Links** property to one of the following choices:</span></span>  
  
   -   <span data-ttu-id="ac41b-109">**複製名稱。**</span><span class="sxs-lookup"><span data-stu-id="ac41b-109">**Copy Name.**</span></span> <span data-ttu-id="ac41b-110">來源結構描述中的節點名稱作為目的結構描述中連結節點的值。</span><span class="sxs-lookup"><span data-stu-id="ac41b-110">The name of the node in the source schema is used as the value of the linked node in the destination schema.</span></span>  
  
   -   <span data-ttu-id="ac41b-111">**複製文字值。**</span><span class="sxs-lookup"><span data-stu-id="ac41b-111">**Copy Text Value.**</span></span> <span data-ttu-id="ac41b-112">對應至來源結構描述中節點的值 (項目資料或屬性值) 作為目的結構描述中連結節點的值。</span><span class="sxs-lookup"><span data-stu-id="ac41b-112">The value corresponding to the node in the source schema (element data or an attribute value) is used as the value of the linked node in the destination schema.</span></span> <span data-ttu-id="ac41b-113">此選項為預設。</span><span class="sxs-lookup"><span data-stu-id="ac41b-113">This choice is the default.</span></span> <span data-ttu-id="ac41b-114">例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello"。</span><span class="sxs-lookup"><span data-stu-id="ac41b-114">For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello".</span></span>  
  
   -   <span data-ttu-id="ac41b-115">**複製文字與子內容值。**</span><span class="sxs-lookup"><span data-stu-id="ac41b-115">**Copy Text and Subcontent Value.**</span></span> <span data-ttu-id="ac41b-116">將對應至來源結構描述中記錄節點、所有子節點的值，以及其子節點的值 (項目資料或屬性值) 結合起來，當做目的結構描述中連結之節點的值。</span><span class="sxs-lookup"><span data-stu-id="ac41b-116">The value corresponding to the record node, and the value of all its child nodes, and their child nodes, in the source schema (element data and attribute values) are combined as the value of the linked node in the destination schema.</span></span> <span data-ttu-id="ac41b-117">例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello Chris Barry"。</span><span class="sxs-lookup"><span data-stu-id="ac41b-117">For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello Chris Barry".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac41b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac41b-118">See Also</span></span>  
 <span data-ttu-id="ac41b-119">[使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ac41b-119">[Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md) </span></span>  
 [<span data-ttu-id="ac41b-120">編譯器指示詞和連結</span><span class="sxs-lookup"><span data-stu-id="ac41b-120">Compiler Directives and Links</span></span>](../core/compiler-directives-and-links.md)