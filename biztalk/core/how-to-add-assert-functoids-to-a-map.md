---
title: "如何新增判斷提示運算質至對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdd79a2-b70f-489b-8711-e00a50d8e2d8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 553daa0c6e97d09e8284d2369e801c5d2ff8beee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-assert-functoids-to-a-map"></a><span data-ttu-id="a9a65-102">如何新增判斷提示運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a9a65-102">How to Add Assert Functoids to a Map</span></span>
<span data-ttu-id="a9a65-103">**Assert**運算質可讓您測試對應中條件的相關假設。</span><span class="sxs-lookup"><span data-stu-id="a9a65-103">The **Assert** functoid enables you to test your assumptions about conditions in your map.</span></span> <span data-ttu-id="a9a65-104">例如，如果您執行幾項計算來確定產品採購時，您可能會判斷提示額外折扣，是使用邏輯運算質不能超過 $100 (**Greater Than**或**Less Than**)。</span><span class="sxs-lookup"><span data-stu-id="a9a65-104">For example, if you perform some calculations to determine an additional discount on product purchases, you might assert that the additional discount be no more than $100 by using a logical functoid (**Greater Than** or **Less Than**).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9a65-105">**Assert**運算質只會引發在開發組建中或當**產生偵錯資訊**專案組建設定中的屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="a9a65-105">The **Assert** functoid only fires in development builds or when the **Generate Debugging Information** property in the project build settings is set to **True**.</span></span> <span data-ttu-id="a9a65-106">當編譯 BizTalk 應用程式以供部署及**產生偵錯資訊**屬性設定為**False** （預設值），判斷提示都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a9a65-106">When your BizTalk application is compiled for deployment and the **Generate Debugging Information** property is set to **False** (the default), assertions are ignored.</span></span>  
  
 <span data-ttu-id="a9a65-107">如需概念資訊**Assert**運算質，請參閱[判斷提示運算質](../core/assert-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a65-107">For conceptual information about the **Assert** functoid, see [Assert Functoid](../core/assert-functoid.md).</span></span>  
  
## <a name="add-the-assert-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="a9a65-108">新增判斷提示運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="a9a65-108">Add the Assert functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="a9a65-109">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="a9a65-109">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span> <span data-ttu-id="a9a65-110">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="a9a65-110">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="a9a65-111">拖曳**Assert**運算質 (![判斷提示運算質](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="a9a65-111">Drag the **Assert** functoid (![Assert functoid](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a65-112">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="a9a65-112">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="a9a65-113">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9a65-113">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span> 
    >    
    >  <span data-ttu-id="a9a65-114">若您要建構使用一個以上運算質的對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="a9a65-114">If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="a9a65-115">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="a9a65-115">Functoids are executed from left to right.</span></span> <span data-ttu-id="a9a65-116">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="a9a65-116">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="a9a65-117">此運算質必須有正好三個輸入參數，而且會產生一個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="a9a65-117">The functoid must have exactly three input parameters and it generates one output parameter.</span></span> <span data-ttu-id="a9a65-118">若要建立的第一個參數**Assert**運算質建立輸入的連結，將輸出拖曳某個其他**邏輯**運算質或從輸入執行個體訊息中的變數布林值欄位。</span><span class="sxs-lookup"><span data-stu-id="a9a65-118">To establish the first parameter for the **Assert** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.</span></span>  
  
4.  <span data-ttu-id="a9a65-119">若要建立的第二個輸入的參數**Assert**運算質，依來源結構描述中的欄位節點建立輸入的連結**Assert**運算質，或是插入常數。</span><span class="sxs-lookup"><span data-stu-id="a9a65-119">To establish the second input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.</span></span>  
  
5.  <span data-ttu-id="a9a65-120">若要建立的第三個輸入的參數**Assert**運算質，依來源結構描述中的欄位節點建立輸入的連結**Assert**運算質，或是插入常數。</span><span class="sxs-lookup"><span data-stu-id="a9a65-120">To establish the third input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.</span></span>  
  
6.  <span data-ttu-id="a9a65-121">若要使用的輸出參數**Assert**運算質，拖曳以建立輸出連結**Assert**運算質至目的結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a9a65-121">To use the output parameter from the **Assert** functoid, create an output link by dragging the **Assert** functoid to a field in the destination schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a65-122">與其他運算質的輸出**Assert**運算質可用做為另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="a9a65-122">As with other functoids, the output of the **Assert** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a65-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9a65-123">See Also</span></span>  
-  <span data-ttu-id="a9a65-124">**判斷提示運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a65-124">**Assert Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>   
-  [<span data-ttu-id="a9a65-125">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a9a65-125">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)