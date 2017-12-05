---
title: "逐步解說： 建立和使用的原則中的詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c306a6e-3384-4f43-9c75-c5407cd9aed2
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fb64a0548fefb816e1975e4c858934fc3dceb7c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-creating-and-using-a-vocabulary-in-the-policy"></a><span data-ttu-id="032ba-102">逐步解說： 建立和使用的原則中的詞彙</span><span class="sxs-lookup"><span data-stu-id="032ba-102">Walkthrough: Creating and Using a Vocabulary in the Policy</span></span>
<span data-ttu-id="032ba-103">本逐步解說提供逐步程序建立詞彙和使用詞彙**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="032ba-103">This walkthrough provides step-by-step procedures for creating a vocabulary and using the vocabulary in the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="032ba-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="032ba-104">Prerequisites</span></span>  
 <span data-ttu-id="032ba-105">您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="032ba-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before performing this walkthrough.</span></span> <span data-ttu-id="032ba-106">不過，我們建議您先完成在此文件中列在此逐步解說之前的所有逐步解說。</span><span class="sxs-lookup"><span data-stu-id="032ba-106">However, we recommend that you complete all the walkthroughs that are listed before this walkthrough in the documentation.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="032ba-107">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="032ba-107">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="032ba-108">此逐步解說包含三個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="032ba-108">This walkthrough contains three procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="032ba-109">程序標題</span><span class="sxs-lookup"><span data-stu-id="032ba-109">Procedure title</span></span>|<span data-ttu-id="032ba-110">程序描述</span><span class="sxs-lookup"><span data-stu-id="032ba-110">Procedure descritpion</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="032ba-111">建立 POVocabulary 詞彙</span><span class="sxs-lookup"><span data-stu-id="032ba-111">To create the POVocabulary vocabulary</span></span>|<span data-ttu-id="032ba-112">提供逐步指示，建立**POVocabulary**具有三個定義的詞彙： 要求的數量、 最大項目允許的數目，以及要求狀態。</span><span class="sxs-lookup"><span data-stu-id="032ba-112">Provides step-by-step instructions for creating the **POVocabulary** vocabulary with three definitions: Requested Quantity, Maximum Number of Items Allowed, and Request Status.</span></span>|  
|<span data-ttu-id="032ba-113">在 ProcessPurchaseOrder 原則中使用 POVocabulary</span><span class="sxs-lookup"><span data-stu-id="032ba-113">To use the POVocabulary in the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="032ba-114">提供建立新版的逐步指示**ProcessPurchaseOrder**原則使用**POVocabulary**。</span><span class="sxs-lookup"><span data-stu-id="032ba-114">Provides step-by-step instructions for creating a new version of the **ProcessPurchaseOrder** policy using **POVocabulary**.</span></span>|  
|<span data-ttu-id="032ba-115">測試方案</span><span class="sxs-lookup"><span data-stu-id="032ba-115">To test the solution</span></span>|<span data-ttu-id="032ba-116">提供測試方案的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="032ba-116">Provides step-by-step instructions for testing the solution.</span></span>|  
  
### <a name="to-create-the-povocabulary-vocabulary"></a><span data-ttu-id="032ba-117">建立 POVocabulary 詞彙</span><span class="sxs-lookup"><span data-stu-id="032ba-117">To create the POVocabulary vocabulary</span></span>  
  
1.  <span data-ttu-id="032ba-118">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="032ba-118">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="032ba-119">如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="032ba-119">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="032ba-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="032ba-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="032ba-121">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="032ba-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="032ba-122">在 事實總管 視窗中，按一下**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="032ba-122">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
3.  <span data-ttu-id="032ba-123">以滑鼠右鍵按一下**詞彙**，按一下 **新增詞彙**，然後輸入**POVocabulary**做為詞彙的名稱。</span><span class="sxs-lookup"><span data-stu-id="032ba-123">Right-click **Vocabularies**, click **Add New Vocabulary**, and then type **POVocabulary** as the name for the vocabulary.</span></span>  
  
4.  <span data-ttu-id="032ba-124">如果您未變更詞彙的名稱為 POVocabulary 步驟 3 中，變更將詞彙的名稱**POVocabulary**屬性 視窗中。</span><span class="sxs-lookup"><span data-stu-id="032ba-124">If you did not change the name of the vocabulary to POVocabulary in step 3, change the name of the vocabulary to **POVocabulary**in the Properties window.</span></span>  
  
5.  <span data-ttu-id="032ba-125">以滑鼠右鍵按一下**版本 1.0 （未儲存）**中**POVocabulary**，然後按一下 **新增定義**。</span><span class="sxs-lookup"><span data-stu-id="032ba-125">Right-click **Version 1.0(not saved)** in **POVocabulary**, and then click **Add New Definition**.</span></span>  
  
6.  <span data-ttu-id="032ba-126">在 詞彙定義精靈 中，選取**XML 文件項目或屬性**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="032ba-126">In the Vocabulary Definition Wizard, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="032ba-127">如**定義名稱**，型別**要求數量**。</span><span class="sxs-lookup"><span data-stu-id="032ba-127">For the **Definition name**, type **Requested Quantity**.</span></span>  
  
8.  <span data-ttu-id="032ba-128">按一下**瀏覽**，然後選取**PO.xsd**檔案中所建立[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="032ba-128">Click **Browse**, and select the **PO.xsd** file you created in [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md).</span></span>  
  
9. <span data-ttu-id="032ba-129">在**選取繫結**對話方塊方塊中，展開  **PurchaseOrder**，依序展開**項目**，然後按兩下**數量**。</span><span class="sxs-lookup"><span data-stu-id="032ba-129">In the **Select Binding** dialog box, expand **PurchaseOrder**, expand **Item**, and then double-click **Quantity**.</span></span>  
  
10. <span data-ttu-id="032ba-130">請確定**文件類型**設**[ruletest.po]**。</span><span class="sxs-lookup"><span data-stu-id="032ba-130">Make sure that the **document type** is set to **RuleTest.PO**.</span></span> <span data-ttu-id="032ba-131">如果不是，將文件類型變更為 [ruletest.po]。</span><span class="sxs-lookup"><span data-stu-id="032ba-131">If it is not, change the document type to RuleTest.PO.</span></span> <span data-ttu-id="032ba-132">這個步驟非常重要。</span><span class="sxs-lookup"><span data-stu-id="032ba-132">This step is very important.</span></span>  
  
     <span data-ttu-id="032ba-133">![BRE &#45;逐步解說 &#45;ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")</span><span class="sxs-lookup"><span data-stu-id="032ba-133">![BRE&#45;Walkthrough&#45;ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")</span></span>  
  
11. <span data-ttu-id="032ba-134">指定**選取作業**中**選取作業**群組做為**執行取得作業**。</span><span class="sxs-lookup"><span data-stu-id="032ba-134">Specify the **select operation** in the **Select operation** group as **Perform Get Operation**.</span></span>  
  
     <span data-ttu-id="032ba-135">![BRE &#45;逐步解說 &#45;SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")</span><span class="sxs-lookup"><span data-stu-id="032ba-135">![BRE&#45;Walkthrough&#45;SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")</span></span>  
  
12. <span data-ttu-id="032ba-136">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="032ba-136">Click **Finish**.</span></span>  
  
13. <span data-ttu-id="032ba-137">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**。</span><span class="sxs-lookup"><span data-stu-id="032ba-137">Right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
14. <span data-ttu-id="032ba-138">選取**XML 文件項目或屬性**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="032ba-138">Select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
15. <span data-ttu-id="032ba-139">如**定義名稱**，型別**Request Status**。</span><span class="sxs-lookup"><span data-stu-id="032ba-139">For the **Definition name**, type **Request Status**.</span></span>  
  
16. <span data-ttu-id="032ba-140">按一下**瀏覽**，然後選取**PO.xsd**檔案。</span><span class="sxs-lookup"><span data-stu-id="032ba-140">Click **Browse**, and select the **PO.xsd** file.</span></span>  
  
17. <span data-ttu-id="032ba-141">在**選取繫結**對話方塊方塊中，展開  **PurchaseOrder**，然後按兩下**狀態**。</span><span class="sxs-lookup"><span data-stu-id="032ba-141">In the **Select Binding** dialog box, expand **PurchaseOrder**, and then double-click **Status**.</span></span>  
  
18. <span data-ttu-id="032ba-142">變更**文件類型**至**[ruletest.po]**。</span><span class="sxs-lookup"><span data-stu-id="032ba-142">Change the **document type** to **RuleTest.PO**.</span></span> <span data-ttu-id="032ba-143">這個步驟非常重要。</span><span class="sxs-lookup"><span data-stu-id="032ba-143">This step is very important.</span></span>  
  
19. <span data-ttu-id="032ba-144">請確定**執行設定作業**選項已選取，然後按一下 [**下一步]。**</span><span class="sxs-lookup"><span data-stu-id="032ba-144">Make sure that the  **Perform Set operation** option is selected, and then click **Next.**</span></span>  
  
20. <span data-ttu-id="032ba-145">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="032ba-145">Click **Finish**.</span></span>  
  
21. <span data-ttu-id="032ba-146">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**。</span><span class="sxs-lookup"><span data-stu-id="032ba-146">Right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
22. <span data-ttu-id="032ba-147">請確定**常數值、 值的範圍或值的集合**已選取，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="032ba-147">Make sure that **Constant Value, Range of Values, or Set of Values** is selected, and then click **Next**.</span></span>  
  
23. <span data-ttu-id="032ba-148">如**定義名稱**，型別**數目的項目允許的最大**。</span><span class="sxs-lookup"><span data-stu-id="032ba-148">For the **Definition name**, type **Maximum Number of Items Allowed**.</span></span>  
  
24. <span data-ttu-id="032ba-149">請確定**常數值定義類型**已選取，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="032ba-149">Make sure that **Constant Value definition type** is selected, and then click **Next**.</span></span>  
  
25. <span data-ttu-id="032ba-150">型別**500**為值，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="032ba-150">Type **500** for the value, and then click **Finish**.</span></span>  
  
26. <span data-ttu-id="032ba-151">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="032ba-151">Right-click **Version 1.0(not saved)**, and then click **Save**.</span></span>  
  
27. <span data-ttu-id="032ba-152">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="032ba-152">Right-click **Version 1.0(not saved)**, and then click **Publish**.</span></span>  
  
### <a name="to-use-the-povocabulary-in-the-processpurchaseorder-policy"></a><span data-ttu-id="032ba-153">在 ProcessPurchaseOrder 原則中使用 POVocabulary</span><span class="sxs-lookup"><span data-stu-id="032ba-153">To use the POVocabulary in the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="032ba-154">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **複製**.</span><span class="sxs-lookup"><span data-stu-id="032ba-154">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="032ba-155">以滑鼠右鍵按一下**ProcessPurchaseOrder** ，然後按一下 **貼上原則版本**。</span><span class="sxs-lookup"><span data-stu-id="032ba-155">Right-click **ProcessPurchaseOrder** and then click **Paste Policy Version**.</span></span>  
  
3.  <span data-ttu-id="032ba-156">按一下**ApprovalRule**中**版本 1.1 （未儲存）**。</span><span class="sxs-lookup"><span data-stu-id="032ba-156">Click **ApprovalRule** in **Version 1.1(not saved)**.</span></span>  
  
4.  <span data-ttu-id="032ba-157">在 [事實總管] 視窗中，依序展開**詞彙**，依序展開**POVocabulary**，依序展開**1.0 版**，然後將拖曳**要求數量**至 IF 窗格，以取代 LessThanOrEqual 述詞的左邊 (lhs) 引數。</span><span class="sxs-lookup"><span data-stu-id="032ba-157">In the Facts Explorer window, expand **Vocabularies**, expand **POVocabulary**, expand **Version 1.0**, and then drag **Requested Quantity** to the IF pane to replace the left hand side (LHS) argument of the LessThanOrEqual predicate.</span></span>  
  
     <span data-ttu-id="032ba-158">![BRE &#45;逐步解說 &#45; DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")</span><span class="sxs-lookup"><span data-stu-id="032ba-158">![BRE&#45;Walkthrough&#45;DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")</span></span>  
  
     <span data-ttu-id="032ba-159">![BRE &#45;逐步解說 &#45;ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")</span><span class="sxs-lookup"><span data-stu-id="032ba-159">![BRE&#45;Walkthrough&#45;ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")</span></span>  
  
5.  <span data-ttu-id="032ba-160">拖曳**數目的項目允許的最大**取代條件的右手邊右邊 (RHS) 引數 (**500**)。</span><span class="sxs-lookup"><span data-stu-id="032ba-160">Drag **Maximum Number of Items Allowed** to replace the right hand side (RHS) argument of the condition (**500**).</span></span>  
  
6.  <span data-ttu-id="032ba-161">選取現有的動作中 THEN 窗格中，按一下滑鼠右鍵，然後按一下**刪除動作**。</span><span class="sxs-lookup"><span data-stu-id="032ba-161">Select the existing action in the THEN pane, right-click, and then click **Delete action**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="032ba-162">您也可以在選取動作之後，按下 DELETE 鍵以刪除該動作。</span><span class="sxs-lookup"><span data-stu-id="032ba-162">You can also press DELETE after selecting the action to delete the action.</span></span>  
  
7.  <span data-ttu-id="032ba-163">拖曳**Request Status**至**然後**窗格。</span><span class="sxs-lookup"><span data-stu-id="032ba-163">Drag **Request Status** to the **THEN** pane.</span></span>  
  
8.  <span data-ttu-id="032ba-164">按一下**\<空字串\>** ，然後輸入**Approved**。</span><span class="sxs-lookup"><span data-stu-id="032ba-164">Click **\<empty string\>** and then type **Approved**.</span></span>  
  
9. <span data-ttu-id="032ba-165">以滑鼠右鍵按一下**版本 1.1 （未儲存）**在原則總管 視窗中，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="032ba-165">Right-click **Version 1.1(not saved)** in the Policy Explorer window, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="032ba-166">以滑鼠右鍵按一下**版本 1.1 （未儲存）**在原則總管 視窗中，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="032ba-166">Right-click **Version 1.1(not saved)** in the Policy Explorer window, and then click **Publish**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="032ba-167">測試方案</span><span class="sxs-lookup"><span data-stu-id="032ba-167">To test the solution</span></span>  
  
1.  <span data-ttu-id="032ba-168">在商務規則編輯器 中展開 **原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**版本 1.0 – 已部署**，然後按一下 **解除部署**.</span><span class="sxs-lookup"><span data-stu-id="032ba-168">In Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0 - Deployed**, and then click **Undeploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="032ba-169">這個步驟是選擇性的，因為協調流程一定都會挑選原則的最新部署版本，也就是在執行步驟 2 之後的 1.1。</span><span class="sxs-lookup"><span data-stu-id="032ba-169">This step is optional because the orchestration always picks the latest deployed version of the policy, which is 1.1 after you perform step 2.</span></span>  
  
2.  <span data-ttu-id="032ba-170">以滑鼠右鍵按一下**版本 1.1-已發佈**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="032ba-170">Right-click **Version 1.1- Published**, and then click **Deploy**.</span></span>  
  
3.  <span data-ttu-id="032ba-171">大約等候**60**秒。</span><span class="sxs-lookup"><span data-stu-id="032ba-171">Wait for approximately **60** seconds.</span></span> <span data-ttu-id="032ba-172">如果有快取原則的任何更新，規則引擎更新服務便會每隔 60 秒鐘重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="032ba-172">The rule engine update service refreshes its cache every 60 seconds if there are any updates to a policy that it caches.</span></span> <span data-ttu-id="032ba-173">無論您是否有執行步驟 1 都沒關係，協調流程會挑選原則的最新部署版本，也就是 1.1。</span><span class="sxs-lookup"><span data-stu-id="032ba-173">It does not matter whether you perform step 1—the orchestration picks up the latest deployed version of the policy, which is 1.1</span></span>  
  
4.  <span data-ttu-id="032ba-174">開啟**SamplePO.xml**和**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="032ba-174">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
5.  <span data-ttu-id="032ba-175">複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。</span><span class="sxs-lookup"><span data-stu-id="032ba-175">Copy the **SamplePO.xml** file from C:\BRE-Walkthroughs directory to C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
6.  <span data-ttu-id="032ba-176">您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="032ba-176">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="032ba-177">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="032ba-177">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
7.  <span data-ttu-id="032ba-178">重複步驟 5 和 6 **SamplePO2.xml**，並注意值**狀態**輸出文件中的欄位會與輸入文件中的相同 (**XYZ**)。</span><span class="sxs-lookup"><span data-stu-id="032ba-178">Repeat steps 5 and 6 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**XYZ**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="032ba-179">值**狀態**欄位會保持相同 (XYZ)，因為 「 規則引擎不會執行中的動作**ApprovalRule**規則，因為條件評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="032ba-179">The value of the **Status** field remains the same (XYZ) because the rule engine does not execute the action in the **ApprovalRule** rule because the condition evaluated to `false`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="032ba-180">註解</span><span class="sxs-lookup"><span data-stu-id="032ba-180">Comments</span></span>  
  
-   <span data-ttu-id="032ba-181">在儲存詞彙之後，您依然能夠予以修改。</span><span class="sxs-lookup"><span data-stu-id="032ba-181">After you save the vocabulary, you can still modify it.</span></span> <span data-ttu-id="032ba-182">在發佈詞彙之後，您就不能夠加以修改。</span><span class="sxs-lookup"><span data-stu-id="032ba-182">After you publish the vocabulary, you cannot modify it.</span></span>  
  
-   <span data-ttu-id="032ba-183">如果需要修改定義、新增定義或刪除定義，您就應該建立詞彙的新版本。</span><span class="sxs-lookup"><span data-stu-id="032ba-183">If you need to modify a definition, add a new definition, or delete a definition, you should create a new version of the vocabulary.</span></span>  
  
-   <span data-ttu-id="032ba-184">只有已發佈的詞彙才能在原則中使用。</span><span class="sxs-lookup"><span data-stu-id="032ba-184">Only published vocabularies can be used in policies.</span></span>  
  
-   <span data-ttu-id="032ba-185">在 「 建立 POVocabulary 詞彙 」 程序中，您可以變更的文件類型**[ruletest.po]**。</span><span class="sxs-lookup"><span data-stu-id="032ba-185">In the "To create the POVocabulary vocabulary" procedure, you changed the document type to **RuleTest.PO**.</span></span> <span data-ttu-id="032ba-186">若要查看這項變更，結果在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，按一下  **PO.xsd**。</span><span class="sxs-lookup"><span data-stu-id="032ba-186">To see the results of this change, in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, click **PO.xsd**.</span></span> <span data-ttu-id="032ba-187">在 [屬性] 視窗中，請注意， **RuleTest**是命名空間、 名稱和**PO**名稱**類型**。</span><span class="sxs-lookup"><span data-stu-id="032ba-187">In the Properties window, note that **RuleTest** is the name of the namespace, and **PO** is the name of the **Type**.</span></span>  
  
-   <span data-ttu-id="032ba-188">在此逐步解說中，您只有使用 XML 文件做為原則的事實。</span><span class="sxs-lookup"><span data-stu-id="032ba-188">In this walkthrough, you used only an XML document as a fact to the policy.</span></span> <span data-ttu-id="032ba-189">您也可以在建立原則時使用 .NET 事實和資料庫事實。</span><span class="sxs-lookup"><span data-stu-id="032ba-189">You can also use .NET facts and database facts when you create policies</span></span>  
  
-   <span data-ttu-id="032ba-190">當您選取**執行 「 設定 」 作業**在 詞彙定義精靈的第二個頁面上，您可以指定**顯示格式字串**接下來的頁面上。</span><span class="sxs-lookup"><span data-stu-id="032ba-190">When you select **Perform "Set" operation** on the second page of the Vocabulary Definition Wizard, you can specify a **Display format string** on the page that follows.</span></span> <span data-ttu-id="032ba-191">例如，您可以變更顯示格式字串從**Request Status {0}**至**要求的狀態是： {0}**後，再按一下**完成**在步驟 20 的 「 建立詞彙 」 程序。</span><span class="sxs-lookup"><span data-stu-id="032ba-191">For example, you could change the display format string from **Request Status {0}** to **Request status is: {0}** before clicking **Finish** in the step 20 of the "create vocabulary" procedure.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="032ba-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="032ba-192">Next Steps</span></span>  
 <span data-ttu-id="032ba-193">現在您已完成此逐步解說中，執行[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說中，它將提供逐步指示，加入新的規則， **ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="032ba-193">Now that you have completed this walkthrough, perform the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough, which gives you step-by-step instructions for adding a new rule to the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032ba-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="032ba-194">See Also</span></span>  
 <span data-ttu-id="032ba-195">[詞彙](../core/vocabularies.md) </span><span class="sxs-lookup"><span data-stu-id="032ba-195">[Vocabularies](../core/vocabularies.md) </span></span>  
 <span data-ttu-id="032ba-196">[如何開發詞彙](../core/how-to-develop-vocabularies.md) </span><span class="sxs-lookup"><span data-stu-id="032ba-196">[How to Develop Vocabularies](../core/how-to-develop-vocabularies.md) </span></span>  
 <span data-ttu-id="032ba-197">[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="032ba-197">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 [<span data-ttu-id="032ba-198">議程與優先順序</span><span class="sxs-lookup"><span data-stu-id="032ba-198">Agenda and Priority</span></span>](../core/agenda-and-priority.md)