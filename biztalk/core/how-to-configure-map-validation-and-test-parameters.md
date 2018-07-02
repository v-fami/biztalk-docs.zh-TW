---
title: 如何設定對應驗證和測試參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1768918c-e94f-476f-b288-9e030c691177
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7aaa62e74f1c49f2e43d96c7d546af023847d91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967407"
---
# <a name="how-to-configure-map-validation-and-test-parameters"></a><span data-ttu-id="bc304-102">如何設定對應驗證和測試參數</span><span class="sxs-lookup"><span data-stu-id="bc304-102">How to Configure Map Validation and Test Parameters</span></span>
<span data-ttu-id="bc304-103">之前驗證和測試對應時，您必須在中設定對應驗證和測試參數**屬性**對應的視窗。</span><span class="sxs-lookup"><span data-stu-id="bc304-103">Before validating and testing a map, you need to set the map validation and test parameters in the **Properties** window of the map.</span></span>  
  
## <a name="configure-the-map-validation-and-test-parameters"></a><span data-ttu-id="bc304-104">設定對應驗證和測試參數</span><span class="sxs-lookup"><span data-stu-id="bc304-104">Configure the map validation and test parameters</span></span>  
  
1.  <span data-ttu-id="bc304-105">在 [方案總管] 中，使用滑鼠右鍵按一下您想要設定，然後再按一下其屬性頁**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bc304-105">In Solution Explorer, right-click the map whose property pages you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bc304-106">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bc304-106">In the Properties window, do the following.</span></span>  
  
    |<span data-ttu-id="bc304-107">使用</span><span class="sxs-lookup"><span data-stu-id="bc304-107">Use this</span></span>|<span data-ttu-id="bc304-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="bc304-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="bc304-109">**驗證 TestMap 輸入**</span><span class="sxs-lookup"><span data-stu-id="bc304-109">**Validate TestMap Input**</span></span>|<span data-ttu-id="bc304-110">設定是否要在測試對應之前，針對來源結構描述驗證執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="bc304-110">Configure whether you want to have the instance message validated against the source schema before you test the map.</span></span>|  
    |<span data-ttu-id="bc304-111">**驗證 TestMap 輸出**</span><span class="sxs-lookup"><span data-stu-id="bc304-111">**Validate TestMap Output**</span></span>|<span data-ttu-id="bc304-112">設定是否要在測試對應之後，針對目的結構描述驗證執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="bc304-112">Configure whether you want to have the instance message validated against the destination schema after you test the map.</span></span>|  
    |<span data-ttu-id="bc304-113">**TestMap 輸入執行個體**</span><span class="sxs-lookup"><span data-stu-id="bc304-113">**TestMap Input Instance**</span></span>|<span data-ttu-id="bc304-114">設定測試對應時要使用的執行個體訊息資料的位置。</span><span class="sxs-lookup"><span data-stu-id="bc304-114">Configure the location of the instance message data to use when you test the map.</span></span><br /><br /> <span data-ttu-id="bc304-115">如果您設定這個屬性時，您也必須設定**TestMap 輸入**屬性。</span><span class="sxs-lookup"><span data-stu-id="bc304-115">If you configure this property, you must also configure the **TestMap Input** property.</span></span>|  
    |<span data-ttu-id="bc304-116">**TestMap 輸出執行個體**</span><span class="sxs-lookup"><span data-stu-id="bc304-116">**TestMap Output Instance**</span></span>|<span data-ttu-id="bc304-117">設定想要儲存測試對應作業輸出檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="bc304-117">Configure the location of the file where you want the output of the test map operation to be stored.</span></span><br /><br /> <span data-ttu-id="bc304-118">如果您設定這個屬性時，您也必須設定**TestMap 輸出**屬性。</span><span class="sxs-lookup"><span data-stu-id="bc304-118">If you configure this property, you must also configure the **TestMap Output** property.</span></span>|  
    |<span data-ttu-id="bc304-119">**TestMap 輸入**</span><span class="sxs-lookup"><span data-stu-id="bc304-119">**TestMap Input**</span></span>|<span data-ttu-id="bc304-120">設定輸入執行個體資料格式。</span><span class="sxs-lookup"><span data-stu-id="bc304-120">Configure the input instance data format.</span></span>|  
    |<span data-ttu-id="bc304-121">**TestMap 輸出**</span><span class="sxs-lookup"><span data-stu-id="bc304-121">**TestMap Output**</span></span>|<span data-ttu-id="bc304-122">設定測試對應時要使用的輸出資料型別。</span><span class="sxs-lookup"><span data-stu-id="bc304-122">Configure the output data type to use when you test the map.</span></span>|  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bc304-123">若要測試對應，首先必須設定對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="bc304-123">If you want to test your map, you must configure the map properties first.</span></span>  

<span data-ttu-id="bc304-124">在開發您的對應之後，接下來的步驟之一就是要對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="bc304-124">After you have developed your map, one of the next steps is to validate it.</span></span> <span data-ttu-id="bc304-125">此主題提供驗證對應的逐步說明。</span><span class="sxs-lookup"><span data-stu-id="bc304-125">This topic provides step-by-step instructions for validating maps.</span></span>  
  
## <a name="validate-a-biztalk-map"></a><span data-ttu-id="bc304-126">驗證 BizTalk 對應</span><span class="sxs-lookup"><span data-stu-id="bc304-126">Validate a BizTalk map</span></span>  
  
1.  <span data-ttu-id="bc304-127">在 [方案總管] 中開啟您想驗證的對應。</span><span class="sxs-lookup"><span data-stu-id="bc304-127">In Solution Explorer, open the map that you want to validate.</span></span>  
  
2.  <span data-ttu-id="bc304-128">在 [方案總管] 中，以滑鼠右鍵按一下地圖，然後按**驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="bc304-128">In Solution Explorer, right-click the map, and then select **Validate Map**.</span></span>  
  
3.  <span data-ttu-id="bc304-129">在 [**輸出**] 視窗中，驗證結果。</span><span class="sxs-lookup"><span data-stu-id="bc304-129">In the **Output** window, verify the results.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc304-130">若您在輸出中使用自訂資料或常數，則必須確認來源測試資料和目標常數值的資料型別是否有效。</span><span class="sxs-lookup"><span data-stu-id="bc304-130">If you use custom data or constants in your output, you must verify that the data types of your source test data and target constant values are valid.</span></span> <span data-ttu-id="bc304-131">當您驗證對應時，BizTalk 對應工具不會檢查的執行個體資料是否違反在結構描述中定義的任何資料型別。</span><span class="sxs-lookup"><span data-stu-id="bc304-131">When you validate a map, BizTalk Mapper does not check if the instance data violates any data types defined in the schemas.</span></span> <span data-ttu-id="bc304-132">在您使用「BizTalk 編輯器」測試對應或驗證執行個體資料時，已完成此項檢查。</span><span class="sxs-lookup"><span data-stu-id="bc304-132">This is done when you test the map or validate the instance data with BizTalk Editor.</span></span> 

## <a name="test-a-biztalk-map"></a><span data-ttu-id="bc304-133">測試 BizTalk 對應</span><span class="sxs-lookup"><span data-stu-id="bc304-133">Test a BizTalk map</span></span>

<span data-ttu-id="bc304-134">在開發對應之後，以下其中一個步驟是進行測試。</span><span class="sxs-lookup"><span data-stu-id="bc304-134">After you have developed your map, one of the next steps is to test it.</span></span> <span data-ttu-id="bc304-135">本主題提供測試對應的逐步指示，包括檢視對應編譯器產生之 XSLT 的步驟。</span><span class="sxs-lookup"><span data-stu-id="bc304-135">This topic provides step-by-step instructions for testing maps including steps to view the XSLT generated by the map compiler.</span></span>  
  
1.  <span data-ttu-id="bc304-136">在 方案總管 中，以滑鼠右鍵按一下您想要測試，然後選取 的地圖**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="bc304-136">In Solution Explorer, right-click the map you want to test, and then select **Test Map**.</span></span>  
  
2.  <span data-ttu-id="bc304-137">驗證會導致**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="bc304-137">Verify the results in the **Output** window.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bc304-138">建議您在測試對應之前，先在 [屬性] 視窗上設定輸入和輸出執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="bc304-138">It is recommended that you configure the input and output instance properties in the Properties window before you test a map.</span></span>  
  
## <a name="review-the-xslt"></a><span data-ttu-id="bc304-139">檢閱 XSLT</span><span class="sxs-lookup"><span data-stu-id="bc304-139">Review the XSLT</span></span>  
 <span data-ttu-id="bc304-140">檢查對應編譯器產生的 XSLT 通常很有用。</span><span class="sxs-lookup"><span data-stu-id="bc304-140">It is often useful to inspect the XSLT generated by the map compiler.</span></span> <span data-ttu-id="bc304-141">查看 XSLT 的優點包括：</span><span class="sxs-lookup"><span data-stu-id="bc304-141">Some of the benefits of inspecting XSLT include:</span></span>  
  
- <span data-ttu-id="bc304-142">如果您使用迴圈或自訂運算質，將更瞭解迴圈執行的方式以及自訂運算質叫用的方式。</span><span class="sxs-lookup"><span data-stu-id="bc304-142">If you are using looping or custom functoids, you will better understand how the looping is performed and how the custom functoid is invoked.</span></span>  
  
- <span data-ttu-id="bc304-143">如果您有複雜的對應，檢視 XSLT 可讓您查看對應如何編譯為轉換，而且可能會提供深入解析如何更好的結構、 取代或簡化一個或多個部分。</span><span class="sxs-lookup"><span data-stu-id="bc304-143">If you have a complicated map, reviewing the XSLT will enable you to see how the map is translated into a transform, and may give you insight on how to better structure, replace, or streamline one or more parts.</span></span>  
  
- <span data-ttu-id="bc304-144">如果您要使用自訂的指令碼或其他成品，檢閱 XSLT 可讓您查看指令碼、成品和其他對應部分互動的方式。</span><span class="sxs-lookup"><span data-stu-id="bc304-144">If you are using custom scripts or other artifacts, reviewing the XSLT will enable you to see how the scripts, artifacts, and other parts of the map interact.</span></span>  
  
  <span data-ttu-id="bc304-145">換句話說，檢視 XSLT 是一個偵錯對應的好方法。</span><span class="sxs-lookup"><span data-stu-id="bc304-145">In other words, reviewing the XSLT is a great way to debug a map.</span></span>  
  
#### <a name="view-the-xslt-generated-by-the-map-compiler"></a><span data-ttu-id="bc304-146">檢視對應編譯器產生的 XSLT</span><span class="sxs-lookup"><span data-stu-id="bc304-146">View the XSLT generated by the map compiler</span></span>  
  
1.  <span data-ttu-id="bc304-147">從 Visual Studio BizTalk 專案中，選取**方案總管**索引標籤上，以滑鼠右鍵按一下對應，然後選取**驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="bc304-147">From a Visual Studio BizTalk project, select the **Solution Explorer** tab, right-click a map, and then select **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="bc304-148">捲動至 [輸出] 視窗，以尋找 XSL 檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="bc304-148">Scroll the Output window to find the URL for the XSL file.</span></span> <span data-ttu-id="bc304-149">按下**CTRL**，然後選取要檢視檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="bc304-149">Press **CTRL**, and select the URL to view the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc304-150">XSL 檔案所做的變更不會反映在對應中，並在下次建置就會覆寫。</span><span class="sxs-lookup"><span data-stu-id="bc304-150">Changes made to the XSL file are not reflected in the map and are overwritten on the next build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc304-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc304-151">See also</span></span>  

[<span data-ttu-id="bc304-152">如何偵錯對應</span><span class="sxs-lookup"><span data-stu-id="bc304-152">How to Debug Maps</span></span>](../core/how-to-debug-maps.md)  
[<span data-ttu-id="bc304-153">地圖疑難排解</span><span class="sxs-lookup"><span data-stu-id="bc304-153">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)  