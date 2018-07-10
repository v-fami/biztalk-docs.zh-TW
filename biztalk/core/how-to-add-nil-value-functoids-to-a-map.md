---
title: 如何新增 Nil 值運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b2e193ed-fe5c-4b12-aab8-ff2d81fd45e1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8488ea03fb40e1616b98e3ac8a1fc68b18e70e9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011863"
---
# <a name="how-to-add-nil-value-functoids-to-a-map"></a><span data-ttu-id="1adf2-102">如何新增 Nil 值運算質至對應</span><span class="sxs-lookup"><span data-stu-id="1adf2-102">How to Add Nil Value Functoids to a Map</span></span>
<span data-ttu-id="1adf2-103">**值，Nil**運算質設定的目的地節點值**Nil**。</span><span class="sxs-lookup"><span data-stu-id="1adf2-103">The **Nil Value** functoid sets the value of the destination node to **Nil**.</span></span>  

 <span data-ttu-id="1adf2-104">如需概念性資訊 **「 Nil 值**運算質，請參閱[Nil 值運算質](../core/nil-value-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="1adf2-104">For conceptual information about the **Nil Value** functoid, see [Nil Value Functoid](../core/nil-value-functoid.md).</span></span>  

## <a name="add-the-nil-value-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="1adf2-105">新增 「 Nil 值 」 運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="1adf2-105">Add the Nil Value functoid to a map and configure it</span></span>  

1. <span data-ttu-id="1adf2-106">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1adf2-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span> <span data-ttu-id="1adf2-107">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="1adf2-107">The list of advanced functoids in the chosen category appears.</span></span>  

2. <span data-ttu-id="1adf2-108">拖曳**值，Nil**運算質 (![Nil 值 」 運算質](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="1adf2-108">Drag the **Nil Value** functoid (![Nil Value functoid](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) from the Toolbox to the appropriate location on a grid page.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="1adf2-109">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="1adf2-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="1adf2-110">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="1adf2-110">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
   >
   >  <span data-ttu-id="1adf2-111">若您要建構使用一個以上運算質的對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="1adf2-111">If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="1adf2-112">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="1adf2-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="1adf2-113">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="1adf2-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  

3. <span data-ttu-id="1adf2-114">**「 Nil 值**運算質可以有零個到一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1adf2-114">The **Nil Value** functoid can have zero to one input parameters.</span></span> <span data-ttu-id="1adf2-115">如果沒有為此運算質輸入的參數，在目標節點設定為**Nil**。</span><span class="sxs-lookup"><span data-stu-id="1adf2-115">If there is no input parameter for this functoid, the target node is set to **Nil**.</span></span> <span data-ttu-id="1adf2-116">若要建立的輸入的參數 **「 Nil 值**運算質建立輸入的連結，方法是將輸出拖曳某個其他**邏輯**運算質或從輸入執行個體訊息中的變數布林值欄位。</span><span class="sxs-lookup"><span data-stu-id="1adf2-116">To establish the input parameter for the **Nil Value** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.</span></span>  

4. <span data-ttu-id="1adf2-117">若要使用的輸出參數 **「 Nil 值**運算質，建立輸出連結，藉由拖曳 **「 Nil 值**」 運算質的記錄或欄位與目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1adf2-117">To use the output parameter from the **Nil Value** functoid, create an output link by dragging the **Nil Value** functoid to a record or field in the destination schema.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="1adf2-118">與其他運算質的輸出一樣 **「 Nil 值**運算質可用來當做另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="1adf2-118">As with other functoids, the output of the **Nil Value** functoid can be used as input to another functoid.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1adf2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1adf2-119">See Also</span></span>  
- <span data-ttu-id="1adf2-120">**Nil 值運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="1adf2-120">**Nil Value Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>   
- [<span data-ttu-id="1adf2-121">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="1adf2-121">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
