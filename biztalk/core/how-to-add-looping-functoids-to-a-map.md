---
title: "如何新增迴圈運算質至對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa380b4a92de685ad8dc19c27a98f6578d12dc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-looping-functoids-to-a-map"></a><span data-ttu-id="73fd3-102">如何新增迴圈運算質至對應</span><span class="sxs-lookup"><span data-stu-id="73fd3-102">How to Add Looping Functoids to a Map</span></span>

## <a name="overview"></a><span data-ttu-id="73fd3-103">概觀</span><span class="sxs-lookup"><span data-stu-id="73fd3-103">Overview</span></span>
<span data-ttu-id="73fd3-104">**迴圈**運算質結合多個記錄或欄位在來源結構描述至目的結構描述中的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="73fd3-104">The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.</span></span>  
  
 <span data-ttu-id="73fd3-105">如需概念資訊**迴圈**運算質，請參閱[迴圈 」 運算質](../core/looping-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="73fd3-105">For conceptual information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).</span></span>  
  
 <span data-ttu-id="73fd3-106">某些狀況下，某些運算質可能無法如預期般與對應中使用時**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="73fd3-106">Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid.</span></span> <span data-ttu-id="73fd3-107">如果這樣的運算質符合下列條件，則不會產生預期的結果：</span><span class="sxs-lookup"><span data-stu-id="73fd3-107">If such a functoid meets the following conditions, it does not produce the expected results:</span></span>  
  
-   <span data-ttu-id="73fd3-108">此運算質擁有一個以上的輸入連結。</span><span class="sxs-lookup"><span data-stu-id="73fd3-108">The functoid has more than one input link.</span></span>  
  
-   <span data-ttu-id="73fd3-109">兩個或多個運算質輸入連結連結至輸入資料錄的子欄位至**迴圈**運算質，其中子欄位不是同層級。</span><span class="sxs-lookup"><span data-stu-id="73fd3-109">Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.</span></span>  
  
-   <span data-ttu-id="73fd3-110">運算質有輸出連結連結至之輸出記錄的子欄位**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="73fd3-110">The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.</span></span>  
  
## <a name="add-the-looping-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="73fd3-111">新增迴圈運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="73fd3-111">Add the Looping functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="73fd3-112">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="73fd3-112">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="73fd3-113">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="73fd3-113">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="73fd3-114">拖曳**迴圈**運算質從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="73fd3-114">Drag the **Looping** functoid from the Toolbox to the appropriate location on a grid page.</span></span>  
  
     ![](../core/media/bts-tls-looping.gif "bts_tls_looping")  
<span data-ttu-id="73fd3-115">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="73fd3-115">Looping functoid</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73fd3-116">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="73fd3-116">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="73fd3-117">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="73fd3-117">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
    > 
    >  <span data-ttu-id="73fd3-118">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="73fd3-118">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="73fd3-119">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="73fd3-119">Functoids are executed from left to right.</span></span> <span data-ttu-id="73fd3-120">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="73fd3-120">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="73fd3-121">若要建立的輸入的參數**迴圈**運算質建立輸入的連結，將記錄拖曳，或從來源結構描述欄位**迴圈**運算質，或拖曳**迴圈**的記錄或欄位在來源結構描述中的運算質。</span><span class="sxs-lookup"><span data-stu-id="73fd3-121">To establish the input parameters for the **Looping** functoid, create an input link by dragging a record or field from the source schema to the **Looping** functoid, or dragging the **Looping** functoid to a record or field in the source schema.</span></span> <span data-ttu-id="73fd3-122">重複為必要項目包含所有相關的輸入的記錄或欄位至**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="73fd3-122">Repeat as required to include all of the relevant input records or fields to the **Looping** functoid.</span></span>  
  
4.  <span data-ttu-id="73fd3-123">若要使用的輸出參數**迴圈**運算質，拖曳以建立輸出連結**迴圈**記錄或欄位與目的結構描述，或藉由拖曳記錄或欄位到運算質目的地結構描述為**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="73fd3-123">To use the output parameter from the **Looping** functoid, create an output link by dragging the **Looping** functoid to a record or field in the destination schema, or by dragging a record or field in the destination schema to the **Looping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73fd3-124">不同於許多其他運算質的輸出**迴圈**運算質只能連結至目的結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="73fd3-124">Unlike many other functoids, the output of the **Looping** functoid can only be linked to an element of the destination schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fd3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73fd3-125">See Also</span></span>  
-  [<span data-ttu-id="73fd3-126">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="73fd3-126">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)   
-  <span data-ttu-id="73fd3-127">**迴圈運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="73fd3-127">**Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>