---
title: 如何新增基本運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a81fb73-cccf-4f74-af92-39e4af13e255
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c033ce9dff8b5d9a07dca574d089f575b4eaa5e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008935"
---
# <a name="how-to-add-basic-functoids-to-a-map"></a><span data-ttu-id="a9474-102">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a9474-102">How to Add Basic Functoids to a Map</span></span>
<span data-ttu-id="a9474-103">許多運算質都很易於使用。</span><span class="sxs-lookup"><span data-stu-id="a9474-103">Many functoids are very simple to use.</span></span> <span data-ttu-id="a9474-104">這些稱為這裡以便區別中的運算質的基本運算質**進階**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="a9474-104">These are referred to here as basic functoids to distinguish them from the functoids in the **Advanced** category.</span></span> <span data-ttu-id="a9474-105">基本運算質包含其餘的類別，例如轉換、 累計、 資料庫、 日期和時間、 邏輯、 數學、 科學，以及字串運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-105">Basic functoids comprise the remaining categories of functoids such as Conversion, Cumulative, Database, Date and Time, Logical, Mathematical, Scientific, and String.</span></span>  
  
 <span data-ttu-id="a9474-106">一般而言，基本運算質有一些簡單的型別 (例如數字和字串) 作為其輸入和輸出連結。</span><span class="sxs-lookup"><span data-stu-id="a9474-106">Basic functoids, in general, have simple types, such as numbers and strings, as their input and output links.</span></span>  
  
 <span data-ttu-id="a9474-107">使用基本運算質包含將它新增至格線頁，建立從左邊輸入至運算質的連結，並建立從運算質輸出至右邊的連結。</span><span class="sxs-lookup"><span data-stu-id="a9474-107">Using a basic functoid involves adding it to a grid page, creating input links to the functoid, coming from the left, and creating output link from the functoid, leaving to the right.</span></span> <span data-ttu-id="a9474-108">本主題提供這些作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="a9474-108">This topic provides step-by-step instructions for these operations.</span></span>  
  
## <a name="add-a-basic-functoid-to-a-map"></a><span data-ttu-id="a9474-109">新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a9474-109">Add a basic functoid to a map</span></span>  
  
1. <span data-ttu-id="a9474-110">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱啟用的情況下，按一下適當的索引標籤，以選取您要使用的運算質類別。</span><span class="sxs-lookup"><span data-stu-id="a9474-110">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the appropriate tab to select the category of the functoid you want to use.</span></span>  
  
    <span data-ttu-id="a9474-111">顯示所選擇類別中的可用運算質清單。</span><span class="sxs-lookup"><span data-stu-id="a9474-111">The list of available functoids in the chosen category appears.</span></span>  
  
2. <span data-ttu-id="a9474-112">將所要使用的運算質從工具箱拖曳至格線頁的適當位置。</span><span class="sxs-lookup"><span data-stu-id="a9474-112">Drag the functoid you want to use from the Toolbox to the appropriate location on a grid page.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a9474-113">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="a9474-113">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="a9474-114">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9474-114">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a9474-115">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="a9474-115">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="a9474-116">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="a9474-116">Functoids are executed from left to right.</span></span> <span data-ttu-id="a9474-117">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="a9474-117">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
## <a name="create-input-links-to-a-basic-functoid"></a><span data-ttu-id="a9474-118">建立基本運算質的輸入的連結</span><span class="sxs-lookup"><span data-stu-id="a9474-118">Create input links to a basic functoid</span></span>  
  
1. <span data-ttu-id="a9474-119">將記錄或欄位節點從來源結構描述拖曳至顯示的格線頁中的基本運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-119">Drag a record or field node from the source schema to the basic functoid in the displayed grid page.</span></span>  
  
    <span data-ttu-id="a9474-120">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-120">**- Or -**</span></span>  
  
    <span data-ttu-id="a9474-121">在顯示的格線頁中，拖曳另一個運算質，位於往左邊，您要建立輸入的連結的基本運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-121">In the displayed grid page, drag another functoid, which is located farther to the left, to the basic functoid to which you want to create an input link.</span></span>  
  
    <span data-ttu-id="a9474-122">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-122">**- Or -**</span></span>  
  
    <span data-ttu-id="a9474-123">將顯示的格線頁中的基本運算質拖曳至來源結構描述中的記錄或欄位節點。</span><span class="sxs-lookup"><span data-stu-id="a9474-123">Drag the basic functoid in the displayed grid page to a record or field node in the source schema.</span></span>  
  
    <span data-ttu-id="a9474-124">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-124">**- Or -**</span></span>  
  
    <span data-ttu-id="a9474-125">在顯示的格線頁中，將您要建立輸入連結的基本運算質拖曳另一個位於左邊較遠的運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-125">In the displayed grid page, drag the basic functoid to which you want to create an input link to another functoid that is located farther to the left.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a9474-126">在拖曳時，與錨定的連結結束點相對的移動連結結束點，會變成十字形狀圖示以允許更精確地鎖定第二個結束點。</span><span class="sxs-lookup"><span data-stu-id="a9474-126">While dragging, the moving endpoint of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint.</span></span> <span data-ttu-id="a9474-127">若您將移動的連結結束點暫留在不適當的第二個連結結束點的物件上，十字形狀圖示就會變成有斜線劃過的圓圈圖示 (例如，當資料型別不符時就會發生)。</span><span class="sxs-lookup"><span data-stu-id="a9474-127">If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.</span></span>  
  
2. <span data-ttu-id="a9474-128">依需要重複步驟 1 來建立完整的基本運算質輸入連結集 (可能不是整個輸入參數集)。</span><span class="sxs-lookup"><span data-stu-id="a9474-128">Repeat step 1 as necessary to establish the complete set of input links (though perhaps not the entire set of input parameters) to the basic functoid.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a9474-129">少數運算質不需要任何輸入連結。</span><span class="sxs-lookup"><span data-stu-id="a9474-129">There are a few functoids that do not require any input links.</span></span> <span data-ttu-id="a9474-130">例如，**日期**，**時間**，和**日期和時間**中的運算質**日期和時間**運算質類別提供目前的日期，時間或日期和時間，分別在其執行個體訊息處理。</span><span class="sxs-lookup"><span data-stu-id="a9474-130">For example, the **Date**, **Time**, and **Date and Time** functoids in the **Date and Time** functoid category provide the current date, time, or date and time, respectively, at which an instance message is being processed.</span></span> <span data-ttu-id="a9474-131">因此，它們不需要來源結構描述的任何輸入參數。</span><span class="sxs-lookup"><span data-stu-id="a9474-131">Thus, they do not require any input parameters from the source schema.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="a9474-132">許多運算質的輸入參數的順序很重要，，對應的運算質參考主題中所示 (請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)])。</span><span class="sxs-lookup"><span data-stu-id="a9474-132">The order of input parameters to many functoids is significant, as indicated in the corresponding functoid reference topic (see **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]).</span></span> <span data-ttu-id="a9474-133">您建立連結的順序將會設定運算質的輸入參數順序。</span><span class="sxs-lookup"><span data-stu-id="a9474-133">The order in which you create links sets the order of input parameters to the functoid.</span></span> <span data-ttu-id="a9474-134">如需運算質屬性和指定的運算質輸入參數順序的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a9474-134">For more information about functoid properties and specifying the order of functoid input parameters, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span> <span data-ttu-id="a9474-135">如需如何設定運算質的輸入的參數的詳細資訊，請參閱[如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a9474-135">For information about how to configure the input parameters of a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="a9474-136">在開始連結之前，請確定要連結的運算質或來源結構描述節點可以在顯示的格線頁或來源結構描述視窗中看到。</span><span class="sxs-lookup"><span data-stu-id="a9474-136">Ensure the functoids or source schema node you want to link are visible in the displayed grid page or source schema window before you begin linking.</span></span>  
  
## <a name="create-the-output-link-from-a-basic-functoid"></a><span data-ttu-id="a9474-137">建立基本運算質的輸出連結</span><span class="sxs-lookup"><span data-stu-id="a9474-137">Create the output link from a basic functoid</span></span>  
  
1.  <span data-ttu-id="a9474-138">將記錄或欄位節點從目的結構描述拖曳至顯示的格線頁中的基本運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-138">Drag a record or field node from the destination schema to the basic functoid in the displayed grid page.</span></span>  
  
     <span data-ttu-id="a9474-139">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-139">**- Or -**</span></span>  
  
     <span data-ttu-id="a9474-140">在顯示的格線頁中，將另一個位於右邊較遠的運算質拖曳至您要建立輸出連結的基本運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-140">In the displayed grid page, drag another functoid, which is located farther to the right, to the basic functoid to which you want to create the output link.</span></span>  
  
     <span data-ttu-id="a9474-141">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-141">**- Or -**</span></span>  
  
     <span data-ttu-id="a9474-142">將顯示的格線頁中的基本運算質拖曳至目的結構描述中的記錄或欄位節點。</span><span class="sxs-lookup"><span data-stu-id="a9474-142">Drag the basic functoid in the displayed grid page to a record or field node in the destination schema.</span></span>  
  
     <span data-ttu-id="a9474-143">**-或者-**</span><span class="sxs-lookup"><span data-stu-id="a9474-143">**- Or -**</span></span>  
  
2.  <span data-ttu-id="a9474-144">在顯示的格線頁中，將您要建立輸出連結的基本運算質拖曳另一個位於右邊較遠的運算質。</span><span class="sxs-lookup"><span data-stu-id="a9474-144">In the displayed grid page, drag the basic functoid to which you want to create the output link to another functoid that is located farther to the right.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9474-145">在開始連結作業之前，請確定要連結的運算質或來源結構描述節點可以在顯示的格線頁和來源結構描述視窗中看到。</span><span class="sxs-lookup"><span data-stu-id="a9474-145">Ensure the functoids and source schema node that you want to link are already visible in the displayed grid page and source schema window, respectively, before you begin the linking operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9474-146">運算質連結永遠會嘗試不允許不適當的連結，例如來源和目標資料型別不符的連結。</span><span class="sxs-lookup"><span data-stu-id="a9474-146">Functoid linking always attempts to disallow inappropriate linking, such as links where source and target data types do not match.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9474-147">在拖曳時，與錨定的連結結束點相對的移動連結結束點，會變成十字形狀圖示以允許更精確地鎖定第二個結束點。</span><span class="sxs-lookup"><span data-stu-id="a9474-147">While dragging, the moving end point of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint.</span></span> <span data-ttu-id="a9474-148">若您將移動的連結結束點暫留在不適當的第二個連結結束點的物件上，十字形狀圖示就會變成有斜線劃過的圓圈圖示 (例如，當資料型別不符時就會發生)。</span><span class="sxs-lookup"><span data-stu-id="a9474-148">If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9474-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9474-149">See Also</span></span>  
<span data-ttu-id="a9474-150">**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a9474-150">**Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>