---
title: 如何比對對應中的結構描述節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 584f85d2-6198-4ef3-90d9-a322f1457d9a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e2ce880489ca49b0b55d2e6f45b9e887d719a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253934"
---
# <a name="how-to-match-schema-nodes-in-a-map"></a><span data-ttu-id="c173f-102">如何比對對應中的結構描述節點</span><span class="sxs-lookup"><span data-stu-id="c173f-102">How to Match Schema Nodes in a Map</span></span>
<span data-ttu-id="c173f-103">當來源或目的地結構描述均很複雜時，對應項目會是很困難的工作。</span><span class="sxs-lookup"><span data-stu-id="c173f-103">When the source or destination schemas are complex, it can be difficult to map the elements.</span></span> <span data-ttu-id="c173f-104">BizTalk 對應工具引進**指示符合**功能，可讓您透過建議最佳對應對應複雜的結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="c173f-104">The BizTalk Mapper introduces the **Indicative Match** feature, which enables you to map complex schema elements by suggesting the best possible matches.</span></span> <span data-ttu-id="c173f-105">本主題提供如何執行此作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c173f-105">This topic provides information about how to perform this operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c173f-106">BizTalk 對應工具會為結構描述節點建議可能的對應。</span><span class="sxs-lookup"><span data-stu-id="c173f-106">The BizTalk Mapper suggests possible matches for a schema node.</span></span> <span data-ttu-id="c173f-107">此功能目前只支援英文名稱。</span><span class="sxs-lookup"><span data-stu-id="c173f-107">This feature is currently supported only for English names.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c173f-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c173f-108">Prerequisites</span></span>  
 <span data-ttu-id="c173f-109">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="c173f-109">These instructions require that the BizTalk Mapper is running.</span></span>  
  
### <a name="to-match-relevant-schema-nodes"></a><span data-ttu-id="c173f-110">對應相關的結構描述節點</span><span class="sxs-lookup"><span data-stu-id="c173f-110">To match relevant schema nodes</span></span>  
  
1.  <span data-ttu-id="c173f-111">選取並以滑鼠右鍵按一下您要知道最符合項目，然後按一下 結構描述項目**表示符合**。</span><span class="sxs-lookup"><span data-stu-id="c173f-111">Select and right-click the schema element for which you need to know the best matches, and then click **Indicate Matches**.</span></span> <span data-ttu-id="c173f-112">BizTalk 對應工具會反白顯示最符合項目 （限制為七個），以選取最適合的對應。</span><span class="sxs-lookup"><span data-stu-id="c173f-112">The BizTalk Mapper highlights the best matches (restricted to seven), with the most optimum match selected.</span></span>  
  
     <span data-ttu-id="c173f-113">或者，您可以選取**指出相符項目**從 [BizTalk] 功能表中或按下 SHIFT + 空格鍵。</span><span class="sxs-lookup"><span data-stu-id="c173f-113">Alternatively, you can select **Indicate Matches** from the BizTalk menu, or press SHIFT + SPACE keys.</span></span>  
  
     <span data-ttu-id="c173f-114">下圖顯示選取之節點的暗示性符合目的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="c173f-114">The following figure shows suggestive matches for the selected node in destination schema.</span></span>  
  
     <span data-ttu-id="c173f-115">![暗示性對應](../core/media/suggestive-mapping.gif "Suggestive_Mapping")</span><span class="sxs-lookup"><span data-stu-id="c173f-115">![Suggestive mapping](../core/media/suggestive-mapping.gif "Suggestive_Mapping")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c173f-116">按住 SHIFT 鍵可來回瀏覽建議的對應。</span><span class="sxs-lookup"><span data-stu-id="c173f-116">Hold down the SHIFT key to traverse among the suggestive matches.</span></span>  
  
2.  <span data-ttu-id="c173f-117">您可以進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c173f-117">You can now do the following:</span></span>  
  
    -   <span data-ttu-id="c173f-118">按下 ENTER 以確認反白顯示最佳 （可能的話） 比對。</span><span class="sxs-lookup"><span data-stu-id="c173f-118">Press ENTER to confirm the highlighted (best possible) match.</span></span>  
  
    -   <span data-ttu-id="c173f-119">使用向上 / 向下鍵，循環的喜好順序反白顯示相符項目。</span><span class="sxs-lookup"><span data-stu-id="c173f-119">Use the UP/DOWN ARROW keys to cycle through the highlighted matches in the order of preference.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c173f-120">按向下鍵來周遊至下一個最符合項目，並向上鍵反白顯示的前一個最符合項目。</span><span class="sxs-lookup"><span data-stu-id="c173f-120">Press the DOWN ARROW key to traverse to the next best match, and the UP ARROW key highlights the previous best match.</span></span>  
  
    -   <span data-ttu-id="c173f-121">按 HOME 鍵以返回最上方的對應。</span><span class="sxs-lookup"><span data-stu-id="c173f-121">Press the HOME key to return to the top match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c173f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c173f-122">See Also</span></span>  
 [<span data-ttu-id="c173f-123">使用 BizTalk 對應工具中的增強的功能</span><span class="sxs-lookup"><span data-stu-id="c173f-123">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)