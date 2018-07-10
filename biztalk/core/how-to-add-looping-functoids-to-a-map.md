---
title: 如何新增迴圈運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 659b9b39beea4bf5efed4c6d1553fca173191cc5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988759"
---
# <a name="how-to-add-looping-functoids-to-a-map"></a><span data-ttu-id="26a2c-102">如何新增迴圈運算質至對應</span><span class="sxs-lookup"><span data-stu-id="26a2c-102">How to Add Looping Functoids to a Map</span></span>

## <a name="overview"></a><span data-ttu-id="26a2c-103">概觀</span><span class="sxs-lookup"><span data-stu-id="26a2c-103">Overview</span></span>
<span data-ttu-id="26a2c-104">**迴圈**運算質結合多個記錄或欄位在來源結構描述中的目的地結構描述中的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="26a2c-104">The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.</span></span>  

 <span data-ttu-id="26a2c-105">如需概念性資訊**迴圈**運算質，請參閱[迴圈 」 運算質](../core/looping-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="26a2c-105">For conceptual information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).</span></span>  

 <span data-ttu-id="26a2c-106">某些狀況下，某些運算質可能無法如預期般 map 中索引使用時**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="26a2c-106">Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid.</span></span> <span data-ttu-id="26a2c-107">如果這樣的運算質符合下列條件，則不會產生預期的結果：</span><span class="sxs-lookup"><span data-stu-id="26a2c-107">If such a functoid meets the following conditions, it does not produce the expected results:</span></span>  

-   <span data-ttu-id="26a2c-108">此運算質擁有一個以上的輸入連結。</span><span class="sxs-lookup"><span data-stu-id="26a2c-108">The functoid has more than one input link.</span></span>  

-   <span data-ttu-id="26a2c-109">兩個或多個運算質輸入連結連結至子欄位來輸入資料錄**迴圈**運算質，其中的子欄位並非同層級項目。</span><span class="sxs-lookup"><span data-stu-id="26a2c-109">Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.</span></span>  

-   <span data-ttu-id="26a2c-110">運算質有輸出連結連結到的輸出記錄的子欄位**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="26a2c-110">The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.</span></span>  

## <a name="add-the-looping-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="26a2c-111">新增迴圈運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="26a2c-111">Add the Looping functoid to a map and configure it</span></span>  

1. <span data-ttu-id="26a2c-112">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="26a2c-112">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  

    <span data-ttu-id="26a2c-113">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="26a2c-113">The list of advanced functoids in the chosen category appears.</span></span>  

2. <span data-ttu-id="26a2c-114">拖曳**迴圈**」 運算質從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="26a2c-114">Drag the **Looping** functoid from the Toolbox to the appropriate location on a grid page.</span></span>  

    <span data-ttu-id="26a2c-115">![](../core/media/bts-tls-looping.gif "bts_tls_looping")</span><span class="sxs-lookup"><span data-stu-id="26a2c-115">![](../core/media/bts-tls-looping.gif "bts_tls_looping")</span></span>  
   <span data-ttu-id="26a2c-116">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="26a2c-116">Looping functoid</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="26a2c-117">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="26a2c-117">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="26a2c-118">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="26a2c-118">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
   > 
   >  <span data-ttu-id="26a2c-119">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="26a2c-119">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="26a2c-120">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="26a2c-120">Functoids are executed from left to right.</span></span> <span data-ttu-id="26a2c-121">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="26a2c-121">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  

3. <span data-ttu-id="26a2c-122">若要建立的輸入的參數**迴圈**運算質建立輸入的連結，藉由拖曳記錄或欄位從 來源結構描述**迴圈**運算質，或拖曳**迴圈**的記錄或欄位在來源結構描述中的運算質。</span><span class="sxs-lookup"><span data-stu-id="26a2c-122">To establish the input parameters for the **Looping** functoid, create an input link by dragging a record or field from the source schema to the **Looping** functoid, or dragging the **Looping** functoid to a record or field in the source schema.</span></span> <span data-ttu-id="26a2c-123">依規定必須納入所有相關的輸入的記錄或欄位，以重複**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="26a2c-123">Repeat as required to include all of the relevant input records or fields to the **Looping** functoid.</span></span>  

4. <span data-ttu-id="26a2c-124">若要使用的輸出參數**迴圈**運算質，建立輸出連結，藉由拖曳**迴圈**記錄或欄位與目的結構描述，或藉由拖曳記錄或欄位到運算質至目的結構描述**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="26a2c-124">To use the output parameter from the **Looping** functoid, create an output link by dragging the **Looping** functoid to a record or field in the destination schema, or by dragging a record or field in the destination schema to the **Looping** functoid.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="26a2c-125">不同於許多其他運算質的輸出**迴圈**運算質只可以連結至目的結構描述的項目。</span><span class="sxs-lookup"><span data-stu-id="26a2c-125">Unlike many other functoids, the output of the **Looping** functoid can only be linked to an element of the destination schema.</span></span>  

## <a name="see-also"></a><span data-ttu-id="26a2c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a2c-126">See Also</span></span>  
- [<span data-ttu-id="26a2c-127">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="26a2c-127">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)   
- <span data-ttu-id="26a2c-128">**迴圈運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="26a2c-128">**Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
