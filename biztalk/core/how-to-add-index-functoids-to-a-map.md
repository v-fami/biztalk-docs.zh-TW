---
title: 如何新增索引運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbfccfcc-c333-422f-b40b-13ca4152e588
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68b560b1565638c7d82d6f497319387fc5f58755
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976183"
---
# <a name="how-to-add-index-functoids-to-a-map"></a><span data-ttu-id="b796f-102">如何新增索引運算質至對應</span><span class="sxs-lookup"><span data-stu-id="b796f-102">How to Add Index Functoids to a Map</span></span>
<span data-ttu-id="b796f-103">**Index**運算質可讓您選取從一系列迴圈記錄中的特定記錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="b796f-103">The **Index** functoid enables you to select information from a specific record in a series of looping records.</span></span> <span data-ttu-id="b796f-104">每個**Index**運算質會從單一欄位中選取資訊。</span><span class="sxs-lookup"><span data-stu-id="b796f-104">Each **Index** functoid selects information from a single field.</span></span>  
  
 <span data-ttu-id="b796f-105">如需概念性資訊**Index**運算質，請參閱[索引運算質](../core/index-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="b796f-105">For conceptual information about the **Index** functoid, see [Index Functoid](../core/index-functoid.md).</span></span>  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="b796f-106">新增索引運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="b796f-106">To add the Index functoid to a map and configure it</span></span>  
  
1. <span data-ttu-id="b796f-107">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b796f-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
    <span data-ttu-id="b796f-108">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="b796f-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2. <span data-ttu-id="b796f-109">拖曳**Index**運算質 (![](../core/media/bts-tls-index.gif "bts_tls_index")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="b796f-109">Drag the **Index** functoid (![](../core/media/bts-tls-index.gif "bts_tls_index")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b796f-110">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="b796f-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="b796f-111">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="b796f-111">If you want to put the functoid onto a different grid page, you need to display the other grid page first.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b796f-112">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="b796f-112">If you are constructing a map using more than one functoid together, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="b796f-113">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="b796f-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="b796f-114">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="b796f-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3. <span data-ttu-id="b796f-115">若要建立的欄位輸入的參數**索引**運算質建立輸入的連結，將迴圈記錄中的欄位拖曳至來源結構描述**索引**運算質，或拖曳**索引**」 運算質，在來源結構描述中迴圈記錄內的欄位。</span><span class="sxs-lookup"><span data-stu-id="b796f-115">To establish the field input parameter for the **Index** functoid, create an input link by dragging a field within a looping record from the source schema to the **Index** functoid, or dragging the **Index** functoid to a field within the looping record in the source schema.</span></span>  
  
4. <span data-ttu-id="b796f-116">若要建立至少一個索引輸入的參數**Index**運算質，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b796f-116">To establish at least one index input parameter for the **Index** functoid, perform the following steps:</span></span>  
  
   1.  <span data-ttu-id="b796f-117">具有**Index**運算質選取，按一下省略符號 (**...**) 按鈕相關聯**輸入參數**中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="b796f-117">With the **Index** functoid selected, click the ellipsis (**...**) button associated with the **Input Parameters** property in the **Properties** window.</span></span>  
  
   2.  <span data-ttu-id="b796f-118">在 [**設定索引運算質** 對話方塊中，按一下![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters")  按鈕。</span><span class="sxs-lookup"><span data-stu-id="b796f-118">In the **Configure Index Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button.</span></span>  
  
   3.  <span data-ttu-id="b796f-119">在編輯方塊中，輸入索引輸入的參數做為數值。</span><span class="sxs-lookup"><span data-stu-id="b796f-119">In the edit box, type the index input parameter as a numeric value.</span></span> <span data-ttu-id="b796f-120">如果其他的索引值是必要的然後按一下 視需要重複**確定**。</span><span class="sxs-lookup"><span data-stu-id="b796f-120">Repeat as necessary if additional index values are required, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="b796f-121">若要使用的輸出參數**Index**運算質，拖曳以建立輸出連結**索引**」 運算質，欄位與目的結構描述中，或是將目的結構描述中的欄位拖曳到**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="b796f-121">To use the output parameter from the **Index** functoid, create an output link by dragging the **Index** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Index** functoid.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b796f-122">與其他運算質的輸出一樣**Index**運算質可用來當做另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="b796f-122">As with other functoids, the output of the **Index** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b796f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b796f-123">See Also</span></span>  
 [<span data-ttu-id="b796f-124">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="b796f-124">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)