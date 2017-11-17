---
title: "使用運算質建立更複雜的對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d53e3a3-5ccd-4733-8c2f-3101e41fca61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b6fa99844182c59db582182056faea1d3f322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-functoids-to-create-more-complex-mappings"></a><span data-ttu-id="637ee-102">使用運算質建立更多複雜的對應</span><span class="sxs-lookup"><span data-stu-id="637ee-102">Using Functoids to Create More Complex Mappings</span></span>

## <a name="overview"></a><span data-ttu-id="637ee-103">概觀</span><span class="sxs-lookup"><span data-stu-id="637ee-103">Overview</span></span>
<span data-ttu-id="637ee-104">運算質在許多對應實例中扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="637ee-104">Functoids play a crucial role in many mapping scenarios.</span></span> <span data-ttu-id="637ee-105">若沒有運算質，您仍可以複製項目和屬性資料，但最嚴重的是，您無法操控這些值。</span><span class="sxs-lookup"><span data-stu-id="637ee-105">Without functoids, you can copy element and attribute data, but you cannot, to any significant extent, manipulate the values themselves.</span></span> <span data-ttu-id="637ee-106">使用運算質，可讓您進行幾乎所有的轉換。</span><span class="sxs-lookup"><span data-stu-id="637ee-106">Using functoids, almost any transformation is possible.</span></span> <span data-ttu-id="637ee-107">例如，您可以使用運算質從完全不同的位置取得兩個值、將它們相加，並將總和放置在目的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="637ee-107">For example, with a functoid you can take two values from entirely different locations, add them together, and place the sum in the destination schema.</span></span>  
  
 <span data-ttu-id="637ee-108">當您編輯 BizTalk 對應時，運算質會出現在「[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱」中 (每個類別都有一個工具箱索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="637ee-108">Functoids appear in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox, one toolbox tab per category, when you are editing a BizTalk map.</span></span> <span data-ttu-id="637ee-109">在您按一下對應的索引標籤以開啟「工具箱」並選擇運算質類別之後，將運算質拖曳至格線頁。</span><span class="sxs-lookup"><span data-stu-id="637ee-109">After you open the Toolbox and choose a category of functoids by clicking on the corresponding tab, you drag the functoid onto a grid page.</span></span> <span data-ttu-id="637ee-110">然後您可以建立運算質之間的輸入和輸出連結，可以是結構描述節點，或是另一個運算質。</span><span class="sxs-lookup"><span data-stu-id="637ee-110">Then you create input and output links between the functoid and either schema nodes or another functoid.</span></span> <span data-ttu-id="637ee-111">輸入連結對應到輸入參數，並從左邊帶出運算質；輸出連結對應到輸入參數，並將運算質留在右邊。</span><span class="sxs-lookup"><span data-stu-id="637ee-111">Input links correspond to input parameters and lead to a functoid from the left; an output link corresponds to the output parameter and leaves a functoid to the right.</span></span>  
  
 <span data-ttu-id="637ee-112">如同其他對應項目，運算質也具有屬性。</span><span class="sxs-lookup"><span data-stu-id="637ee-112">Like other map elements, functoids have properties.</span></span> <span data-ttu-id="637ee-113">運算質最重要的屬性之一是其輸入參數集。</span><span class="sxs-lookup"><span data-stu-id="637ee-113">One of the most important properties of a functoid is its set of input parameters.</span></span> <span data-ttu-id="637ee-114">如需詳細資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="637ee-114">For more information, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md).</span></span>  
  
 <span data-ttu-id="637ee-115">本節提供在 BizTalk 對應中使用運算質的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="637ee-115">This section provides step-by-step instructions for working with functoids within BizTalk maps.</span></span> <span data-ttu-id="637ee-116">如需運算質的參考資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="637ee-116">For reference information about functoids, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="637ee-117">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="637ee-117">Next steps</span></span> 
  
-   [<span data-ttu-id="637ee-118">如何開啟運算質工具箱</span><span class="sxs-lookup"><span data-stu-id="637ee-118">How to Open the Functoid Toolbox</span></span>](../core/how-to-open-the-functoid-toolbox.md)  
  
-   [<span data-ttu-id="637ee-119">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="637ee-119">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="637ee-120">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="637ee-120">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="637ee-121">編輯運算質屬性和輸入的參數</span><span class="sxs-lookup"><span data-stu-id="637ee-121">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)  
  
-   [<span data-ttu-id="637ee-122">如何選取多個運算質</span><span class="sxs-lookup"><span data-stu-id="637ee-122">How to Select Multiple Functoids</span></span>](../core/how-to-select-multiple-functoids.md)  
  
-   [<span data-ttu-id="637ee-123">如何刪除運算質</span><span class="sxs-lookup"><span data-stu-id="637ee-123">How to Delete Functoids</span></span>](../core/how-to-delete-functoids.md)  
  
-   [<span data-ttu-id="637ee-124">如何複製、 剪下和貼上運算質</span><span class="sxs-lookup"><span data-stu-id="637ee-124">How to Copy, Cut, and Paste a Functoid</span></span>](../core/how-to-copy-cut-and-paste-a-functoid.md)