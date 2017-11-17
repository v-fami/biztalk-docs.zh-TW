---
title: "逐步解說： 將規則新增至原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2a682c0-a5d7-4550-924d-be9fa29b84d2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 343dc2e9c7965ffb27a806d18944da99777dd3ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-adding-a-rule-to-the-policy"></a><span data-ttu-id="43009-102">逐步解說： 將規則新增原則</span><span class="sxs-lookup"><span data-stu-id="43009-102">Walkthrough: Adding a Rule to the Policy</span></span>
<span data-ttu-id="43009-103">此逐步解說提供逐步程序加入名為的規則**DeniedRule**至**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="43009-103">This walkthrough provides step-by-step procedures for adding a rule named **DeniedRule** to the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="43009-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="43009-104">Prerequisites</span></span>  
 <span data-ttu-id="43009-105">您必須先完成[逐步解說： 建立和使用詞彙的原則中](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="43009-105">You must complete the [Walkthrough: Creating and Using a Vocabulary in the Policy](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="43009-106">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="43009-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="43009-107">此逐步解說包含三個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="43009-107">This walkthrough contains three procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="43009-108">程序標題</span><span class="sxs-lookup"><span data-stu-id="43009-108">Procedure title</span></span>|<span data-ttu-id="43009-109">程序說明</span><span class="sxs-lookup"><span data-stu-id="43009-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="43009-110">若要將 DeniedRule 加入到 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="43009-110">To add DeniedRule to the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="43009-111">提供逐步指示，加入名為的新規則**DeniedRule**至**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="43009-111">Provides step-by-step instructions for adding a new rule named **DeniedRule** to the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="43009-112">**DeniedRule**規則設定的值**狀態**欄位設為**拒絕**如果的值**數量**大於 500。</span><span class="sxs-lookup"><span data-stu-id="43009-112">The **DeniedRule** rule sets the value of the **Status** field to **Denied** if the value of the **Quantity** is greater than 500.</span></span>|  
|<span data-ttu-id="43009-113">使用商務規則編輯器進行測試</span><span class="sxs-lookup"><span data-stu-id="43009-113">To test with Business Rule Composer</span></span>|<span data-ttu-id="43009-114">提供逐步指示，測試**ProcessPurchaseOrder**使用商務規則編輯器 」 的原則。</span><span class="sxs-lookup"><span data-stu-id="43009-114">Provides step-by-step instructions for testing the **ProcessPurchaseOrder** policy by using Business Rule Composer.</span></span>|  
|<span data-ttu-id="43009-115">測試方案</span><span class="sxs-lookup"><span data-stu-id="43009-115">To test the solution</span></span>|<span data-ttu-id="43009-116">提供測試方案的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="43009-116">Provides step-by-step instructions for testing the solution.</span></span>|  
  
### <a name="to-add-deniedrule-to-the-processpurchaseorder-policy"></a><span data-ttu-id="43009-117">若要將 DeniedRule 加入到 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="43009-117">To add DeniedRule to the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="43009-118">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="43009-118">On the **Start** menu, open **Business Rule Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43009-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="43009-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="43009-120">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="43009-120">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="43009-121">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.1 版**，然後按一下 **複製**.</span><span class="sxs-lookup"><span data-stu-id="43009-121">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.1**, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="43009-122">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **貼上原則版本**。</span><span class="sxs-lookup"><span data-stu-id="43009-122">Right-click **ProcessPurchaseOrder**, and then click **Paste Policy Version**.</span></span>  
  
4.  <span data-ttu-id="43009-123">以滑鼠右鍵按一下**（未儲存） 1.2 版**，按一下 **新增規則**，然後將變更之規則的名稱**DeniedRule**。</span><span class="sxs-lookup"><span data-stu-id="43009-123">Right-click **Version 1.2(not saved)**, click **Add New Rule**, and then change the name of the rule to **DeniedRule**.</span></span>  
  
5.  <span data-ttu-id="43009-124">如果您忘了要變更之規則的名稱**DeniedRule**在步驟 4 中，按一下**Rule1**，並將名稱變更為**DeniedRule**屬性 視窗中。</span><span class="sxs-lookup"><span data-stu-id="43009-124">If you forgot to change the name of the rule to **DeniedRule** in step 4, click **Rule1**, and change the name to **DeniedRule** in the Properties window.</span></span>  
  
6.  <span data-ttu-id="43009-125">在 IF 窗格中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下  **Greater Than**。</span><span class="sxs-lookup"><span data-stu-id="43009-125">In the IF pane, right-click **Conditions**, point to **Predicates**, and then click **Greater Than**.</span></span>  
  
7.  <span data-ttu-id="43009-126">在 事實總管 視窗中，按一下**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="43009-126">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
8.  <span data-ttu-id="43009-127">展開**詞彙**，依序展開**POVocabulary**，依序展開**1.0 版-已發佈**，然後拖曳**要求數量**至**引數 1** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="43009-127">Expand **Vocabularies**, expand **POVocabulary**, expand **Version 1.0 - Published**, and then drag **Request Quantity** to **argument1** in the IF pane.</span></span>  
  
9. <span data-ttu-id="43009-128">拖曳**允許的項目數目上限**至**引數 2** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="43009-128">Drag **Maximum number of items allowed** to **argument2** in the IF pane.</span></span>  
  
10. <span data-ttu-id="43009-129">拖曳**Request Status**到 [THEN] 窗格。</span><span class="sxs-lookup"><span data-stu-id="43009-129">Drag **Request Status** to the THEN pane.</span></span>  
  
11. <span data-ttu-id="43009-130">按一下**\<空字串 >** ，然後輸入**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="43009-130">Click **\<empty string>** and then type **Denied**.</span></span>  
  
12. <span data-ttu-id="43009-131">以滑鼠右鍵按一下**（未儲存） 1.2 版**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="43009-131">Right-click **Version 1.2 (not saved)**, and then click **Save**.</span></span>  
  
13. <span data-ttu-id="43009-132">以滑鼠右鍵按一下**1.2 版**，然後按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="43009-132">Right-click **Version 1.2**, and then click **Publish**.</span></span>  
  
14. <span data-ttu-id="43009-133">以滑鼠右鍵按一下**1.2 版**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="43009-133">Right-click **Version 1.2**, and then click **Deploy**.</span></span>  
  
### <a name="to-test-with-business-rule-composer"></a><span data-ttu-id="43009-134">使用商務規則編輯器進行測試</span><span class="sxs-lookup"><span data-stu-id="43009-134">To test with Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="43009-135">在記事本中開啟 SamplePO.xml 和 SamplePO2.xml 檔案，然後將值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="43009-135">Open the SamplePO.xml and SamplePO2.xml files in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
2.  <span data-ttu-id="43009-136">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.2 版**，然後按一下 **測試原則**.</span><span class="sxs-lookup"><span data-stu-id="43009-136">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.2**, and then click **Test Policy**.</span></span>  
  
3.  <span data-ttu-id="43009-137">在下**XMLDocuments**節點中，選取**ruletest.po**，然後按一下 **新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="43009-137">Under the **XMLDocuments** node, select **RuleTest.PO**, and then click **Add Instance**.</span></span>  
  
4.  <span data-ttu-id="43009-138">選取**SamplePO.xml**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="43009-138">Select **SamplePO.xml**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="43009-139">按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="43009-139">Click **Test**.</span></span>  
  
6.  <span data-ttu-id="43009-140">查看**議程更新**區段在輸出中，然後注意只有**ApprovalRule**新增至議程。</span><span class="sxs-lookup"><span data-stu-id="43009-140">Look at the **Agenda Update** section in the output, and notice that only **ApprovalRule** is added to the agenda.</span></span> <span data-ttu-id="43009-141">因此，它是引發的唯一規則 (會執行與此規則相關的動作)。</span><span class="sxs-lookup"><span data-stu-id="43009-141">Therefore it is the only rule that fires (actions associated with the rule are executed).</span></span>  
  
7.  <span data-ttu-id="43009-142">開啟**SamplePO.xml**在 [記事本]，請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="43009-142">Open **SamplePO.xml** in Notepad and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
8.  <span data-ttu-id="43009-143">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.2 版**，然後按一下 **測試原則。**</span><span class="sxs-lookup"><span data-stu-id="43009-143">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.2**, and then click **Test Policy.**</span></span>  
  
9. <span data-ttu-id="43009-144">選取**SamplePO.xml**，按一下 **移除執行個體**，然後按一下 **新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="43009-144">Select **SamplePO.xml**, click **Remove instance**, and then click **Add Instance**.</span></span>  
  
10. <span data-ttu-id="43009-145">選取**SamplePO2.xml**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="43009-145">Select **SamplePO2.xml**, and then click **Open**.</span></span>  
  
11. <span data-ttu-id="43009-146">按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="43009-146">Click **Test**.</span></span>  
  
12. <span data-ttu-id="43009-147">查看**議程更新**區段在輸出中，然後注意只有**DeniedRule**新增至議程。</span><span class="sxs-lookup"><span data-stu-id="43009-147">Look at the **Agenda Update** section in the output, and notice that only **DeniedRule** is added to the agenda.</span></span> <span data-ttu-id="43009-148">因此，它是引發的唯一規則。</span><span class="sxs-lookup"><span data-stu-id="43009-148">Therefore it is the only rule that fires.</span></span>  
  
13. <span data-ttu-id="43009-149">開啟**SamplePO2.xml**在 [記事本]，請注意，值**狀態**欄位是**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="43009-149">Open **SamplePO2.xml** in Notepad and notice that the value of the **Status** field is **Denied**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="43009-150">測試方案</span><span class="sxs-lookup"><span data-stu-id="43009-150">To test the solution</span></span>  
  
1.  <span data-ttu-id="43009-151">開啟**SamplePO.xml**和**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="43009-151">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
2.  <span data-ttu-id="43009-152">複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。</span><span class="sxs-lookup"><span data-stu-id="43009-152">Copy the **SamplePO.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
3.  <span data-ttu-id="43009-153">您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="43009-153">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="43009-154">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="43009-154">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
4.  <span data-ttu-id="43009-155">重複步驟 2 和 3。 **SamplePO2.xml**，並注意值**狀態**欄位設定為**拒絕**輸出文件中。</span><span class="sxs-lookup"><span data-stu-id="43009-155">Repeat steps 2 and 3 with **SamplePO2.xml**, and notice that the value of the **Status** field is set to **Denied** in the output document.</span></span> <span data-ttu-id="43009-156">這證明協調流程使用 1.2 版**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="43009-156">This proves that the orchestration is using version 1.2 of the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="43009-157">協調流程會使用最新的部署的版本**ProcessPurchaseOrder**原則，這是**1.2**。</span><span class="sxs-lookup"><span data-stu-id="43009-157">The orchestration uses the latest deployed version of the **ProcessPurchaseOrder** policy, which is **1.2**.</span></span> <span data-ttu-id="43009-158">您不需要解除部署 1.1 版的原則，也可以使用 1.2 版的原則。</span><span class="sxs-lookup"><span data-stu-id="43009-158">You do not need to undeploy version 1.1 of the policy to use version 1.2 of the policy.</span></span> <span data-ttu-id="43009-159">但是，在測試此解決方案之前，您需要等候大約 60 秒鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="43009-159">However, you need to wait for approximately 60 seconds before testing the solution.</span></span> <span data-ttu-id="43009-160">如需詳細資訊，請參閱「註解」一節。</span><span class="sxs-lookup"><span data-stu-id="43009-160">For more information, see the Comments section.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="43009-161">註解</span><span class="sxs-lookup"><span data-stu-id="43009-161">Comments</span></span>  
  
-   <span data-ttu-id="43009-162">原則中可能有一或多個規則。</span><span class="sxs-lookup"><span data-stu-id="43009-162">A policy can have one or more rules.</span></span> <span data-ttu-id="43009-163">原則中的規則數目沒有邏輯限制。</span><span class="sxs-lookup"><span data-stu-id="43009-163">There is no logical limit on the number of rules in a policy.</span></span>  
  
-   <span data-ttu-id="43009-164">此規則引擎會使用「條件評估」、「衝突解決」和「動作執行」演算法。</span><span class="sxs-lookup"><span data-stu-id="43009-164">The rule engine uses a Condition Evaluation - Conflict Resolution - Action Execution algorithm.</span></span> <span data-ttu-id="43009-165">在**條件評估**階段中，規則引擎會評估所有規則的條件。</span><span class="sxs-lookup"><span data-stu-id="43009-165">In the **Condition Evaluation** stage, the rule engine evaluates conditions in all the rules.</span></span> <span data-ttu-id="43009-166">條件評估為 True 的規則會變成執行的候選規則。</span><span class="sxs-lookup"><span data-stu-id="43009-166">The rules whose conditions evaluate to true become candidate rules for execution.</span></span> <span data-ttu-id="43009-167">在**衝突解決**階段中，的候選規則新增至規則的優先權順序議程。</span><span class="sxs-lookup"><span data-stu-id="43009-167">In the **Conflict Resolution** stage, the candidate rules are added to the agenda in the order of the priority of the rule.</span></span> <span data-ttu-id="43009-168">在**動作執行**階段中，會執行的候選規則中的動作。</span><span class="sxs-lookup"><span data-stu-id="43009-168">In the **Action Execution** stage, the actions in the candidate rules are executed.</span></span> <span data-ttu-id="43009-169">如果候選規則具有相同的優先順序，執行這些規則的動作時，並沒有決定性的順序。</span><span class="sxs-lookup"><span data-stu-id="43009-169">If candidate rules have the same priority, there is no deterministic order in which the actions for those rules are executed.</span></span> <span data-ttu-id="43009-170">您應該假設這些動作是以平行方式執行。</span><span class="sxs-lookup"><span data-stu-id="43009-170">You should assume that they are executed in parallel.</span></span>  
  
-   <span data-ttu-id="43009-171">在此案例下，任何給定的範例檔案只會引發其中一個規則。</span><span class="sxs-lookup"><span data-stu-id="43009-171">In this scenario, for any given sample file, only one of the rules is fired.</span></span> <span data-ttu-id="43009-172">請確定您的值變更**狀態**欄位之前執行測試。</span><span class="sxs-lookup"><span data-stu-id="43009-172">Make sure that you change the value of the **Status** field before running a test.</span></span>  
  
-   <span data-ttu-id="43009-173">在您部署新版的原則時，您應該等候大約 60 秒鐘，才能開始測試。</span><span class="sxs-lookup"><span data-stu-id="43009-173">When a new version of the policy is deployed, you should wait approximately 60 seconds before testing.</span></span> <span data-ttu-id="43009-174">規則引擎更新服務會定期輪詢規則引擎資料庫 (預設為每隔 60 秒鐘)，以查看是否有新部署的原則。</span><span class="sxs-lookup"><span data-stu-id="43009-174">The rule engine update service polls the rule engine database on a periodic basis (every 60 seconds by default) to look for newly deployed policies.</span></span> <span data-ttu-id="43009-175">規則引擎更新服務會使用規則引擎資料庫中最新部署之原則版本的相關資訊來更新記憶體中的原則物件。</span><span class="sxs-lookup"><span data-stu-id="43009-175">The rule engine update service updates the policy object in memory with the information about the latest deployed version of the policy from the rule engine database.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="43009-176">後續步驟</span><span class="sxs-lookup"><span data-stu-id="43009-176">Next Steps</span></span>  
 <span data-ttu-id="43009-177">現在您已完成此逐步解說中，執行[逐步解說： 修改原則](../core/walkthrough-modifying-the-policy.md)逐步解說，它可讓您修改原則的逐步指示核准採購訂單的值**數量**小於或等於 1000 （而不是 500)。</span><span class="sxs-lookup"><span data-stu-id="43009-177">Now that you have completed this walkthrough, perform the [Walkthrough: Modifying the Policy](../core/walkthrough-modifying-the-policy.md) walkthrough, which gives you step-by-step instructions for modifying the policy to approve purchase orders with the value of **quantity** less than or equal to 1000 (instead of 500).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43009-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43009-178">See Also</span></span>  
 <span data-ttu-id="43009-179">[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="43009-179">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 [<span data-ttu-id="43009-180">議程與優先順序</span><span class="sxs-lookup"><span data-stu-id="43009-180">Agenda and Priority</span></span>](../core/agenda-and-priority.md)