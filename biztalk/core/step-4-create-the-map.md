---
title: 步驟 4： 建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f7f1f6d-0e57-4a65-b91d-c81fcc832961
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fcbce54a488cb687ad0fb2c7a1931243c8cd882
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973980"
---
# <a name="step-4-create-the-map"></a><span data-ttu-id="b8968-102">步驟 4：建立對應</span><span class="sxs-lookup"><span data-stu-id="b8968-102">Step 4: Create the Map</span></span>
<span data-ttu-id="b8968-103">![步驟 4，5 個](../core/media/step-4of5.gif "Step_4of5")</span><span class="sxs-lookup"><span data-stu-id="b8968-103">![Step 4 of 5](../core/media/step-4of5.gif "Step_4of5")</span></span>  
  
 <span data-ttu-id="b8968-104">**若要完成的時間：** 6 分鐘</span><span class="sxs-lookup"><span data-stu-id="b8968-104">**Time to complete:** 6 minutes</span></span>  
  
 <span data-ttu-id="b8968-105">**目標：** 在此步驟中，您會建立要求拒絕訊息的要求訊息轉換的對應。</span><span class="sxs-lookup"><span data-stu-id="b8968-105">**Objective:** In this step, you create a map that transforms Request message to RequestDecline message.</span></span>  
  
 <span data-ttu-id="b8968-106">**用途：** 此對應會確定要求識別碼編號與總計包含在傳回給倉儲庫存系統的要求拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="b8968-106">**Purpose:** The map ensures that the request ID number and the grand total are included in the request decline message returned to the warehouse inventory system.</span></span> <span data-ttu-id="b8968-107">您將使用 [BizTalk 對應工具] 將內送訊息中的欄位連結至為外寄訊息定義的欄位。</span><span class="sxs-lookup"><span data-stu-id="b8968-107">You use BizTalk Mapper to link fields in an incoming message to fields defined for the outgoing message.</span></span> <span data-ttu-id="b8968-108">由於這兩個訊息沒有相同的結構，因此這是必要的。</span><span class="sxs-lookup"><span data-stu-id="b8968-108">This is necessary because these two messages do not have the same schema structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8968-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="b8968-109">Prerequisites</span></span>  
 <span data-ttu-id="b8968-110">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="b8968-110">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="b8968-111">在開始此步驟之前必須先完成[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)和[步驟 3： 建立要求拒絕結構描述](../core/step-3-create-the-request-decline-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="b8968-111">Before you begin this step you must complete [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) and [Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="b8968-112">程序</span><span class="sxs-lookup"><span data-stu-id="b8968-112">Procedures</span></span>  
 <span data-ttu-id="b8968-113">此對應會仰賴要求結構描述與要求拒絕結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8968-113">The map depends on the Request schema and the RequestDecline schema.</span></span>  <span data-ttu-id="b8968-114">您必須先使用結構描述來編譯專案，然後才能在對應上使用它們。</span><span class="sxs-lookup"><span data-stu-id="b8968-114">You much compile the project with the schema before you can use them on a map.</span></span>  
  
#### <a name="to-compile-the-eaischemas-project"></a><span data-ttu-id="b8968-115">若要編譯 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="b8968-115">To compile the EAISchemas project</span></span>  
  
-   <span data-ttu-id="b8968-116">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="b8968-116">In Solution Explorer, right-click **EAISchemas**, and then click **Build**.</span></span>  
  
#### <a name="to-create-the-map"></a><span data-ttu-id="b8968-117">若要建立對應</span><span class="sxs-lookup"><span data-stu-id="b8968-117">To create the map</span></span>  
  
1.  <span data-ttu-id="b8968-118">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="b8968-118">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="b8968-119">在**加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b8968-119">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="b8968-120">使用</span><span class="sxs-lookup"><span data-stu-id="b8968-120">Use this</span></span>|<span data-ttu-id="b8968-121">動作</span><span class="sxs-lookup"><span data-stu-id="b8968-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8968-122">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="b8968-122">**Installed Templates**</span></span>|<span data-ttu-id="b8968-123">按一下**對應檔**，然後按一下 **對應**。</span><span class="sxs-lookup"><span data-stu-id="b8968-123">Click **Map Files**, and then click **Map**.</span></span>|  
    |<span data-ttu-id="b8968-124">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8968-124">**Name**</span></span>|<span data-ttu-id="b8968-125">型別**MapToReqDecline.btm**。</span><span class="sxs-lookup"><span data-stu-id="b8968-125">Type **MapToReqDecline.btm**.</span></span>|  
  
3.  <span data-ttu-id="b8968-126">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="b8968-126">Click **Add**.</span></span>  
  
     <span data-ttu-id="b8968-127">下圖顯示 [來源結構描述]、[目的結構描述] 和 [對應工具格線]。</span><span class="sxs-lookup"><span data-stu-id="b8968-127">The following figure shows the Source Schema, Destination Schema, and Mapper Grid.</span></span>  
  
     <span data-ttu-id="b8968-128">![MapToReqDenied 對應](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")</span><span class="sxs-lookup"><span data-stu-id="b8968-128">![MapToReqDenied map](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")</span></span>  
  
4.  <span data-ttu-id="b8968-129">在**來源結構描述**] 窗格中，按一下 [**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="b8968-129">In the **Source Schema** pane, click **Open Source Schema**.</span></span>  
  
5.  <span data-ttu-id="b8968-130">在**BizTalk 型別選擇器**對話方塊方塊中，展開  **EAISchemas**，依序展開**結構描述**，按一下  **eaischemas.request**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8968-130">In the **BizTalk Type Picker** dialog box, expand **EAISchemas**, expand **Schemas**, click **EAISchemas.Request**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="b8968-131">在**來源結構描述**] 窗格中，以滑鼠右鍵按一下**\<結構描述\>**，然後按一下 [**展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="b8968-131">In the **Source Schema** pane, right-click **\<Schema\>**, and then click **Expand Tree Node**.</span></span>  
  
7.  <span data-ttu-id="b8968-132">在**目的結構描述**] 窗格中，按一下 [**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="b8968-132">In the **Destination Schema** pane, click **Open Destination Schema**.</span></span>  
  
8.  <span data-ttu-id="b8968-133">在**BizTalk 型別選擇器**對話方塊方塊中，展開  **EAISchemas**，展開**結構描述**，按一下**EAISchemas.RequestDecline**，然後按一下按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b8968-133">In the **BizTalk Type Picker** dialog box, expand **EAISchemas**, expand **Schemas**, click **EAISchemas.RequestDecline**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="b8968-134">在**目的結構描述**] 窗格中，以滑鼠右鍵按一下**\<結構描述\>**，然後按一下 [**展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="b8968-134">In the **Destination Schema** pane, right-click **\<Schema\>**, and then click **Expand Tree Node**.</span></span>  
  
10. <span data-ttu-id="b8968-135">在**來源結構描述**窗格拖曳**ReqID**欄位設為**ReqID**中**目的結構描述**窗格。</span><span class="sxs-lookup"><span data-stu-id="b8968-135">In the **Source Schema** pane, drag the **ReqID** field to the **ReqID** in the **Destination Schema** pane.</span></span> <span data-ttu-id="b8968-136">會顯示連接兩個項目的直線。</span><span class="sxs-lookup"><span data-stu-id="b8968-136">A line appears connecting the two elements.</span></span>  
  
11. <span data-ttu-id="b8968-137">在**來源結構描述**窗格拖曳**GrandTotal**欄位設為**GrandTotal**欄位**目的結構描述** 窗格來對應資料從另一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8968-137">In the **Source Schema** pane, drag the **GrandTotal** field to the **GrandTotal** field in the **Destination Schema** pane to map the data from one schema to the other.</span></span>  
  
12. <span data-ttu-id="b8968-138">在**檔案**功能表上，按一下 **全部儲存**，儲存工作。</span><span class="sxs-lookup"><span data-stu-id="b8968-138">On the **File** menu, click **Save All** to save your work.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="b8968-139">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="b8968-139">What did I just do?</span></span>  
 <span data-ttu-id="b8968-140">在此步驟中，您已建立將要求訊息轉換成要求拒絕訊息的對應。</span><span class="sxs-lookup"><span data-stu-id="b8968-140">In this step, you created a map that transforms Request message to RequestDecline message.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b8968-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b8968-141">Next Steps</span></span>  
 <span data-ttu-id="b8968-142">您會建置 EAISchemas 專案。</span><span class="sxs-lookup"><span data-stu-id="b8968-142">You build the EAISchemas project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8968-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8968-143">See Also</span></span>  
 <span data-ttu-id="b8968-144">[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="b8968-144">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="b8968-145">[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="b8968-145">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="b8968-146">[步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="b8968-146">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="b8968-147">[步驟 4： 建立地圖](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="b8968-147">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="b8968-148">[步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="b8968-148">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 [<span data-ttu-id="b8968-149">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="b8968-149">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)