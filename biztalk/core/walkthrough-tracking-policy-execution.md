---
title: 逐步解說： 追蹤 BizTalk Server 中的原則執行 |Microsoft 文件
description: 若要啟用追蹤，並檢視追蹤詳細資料原則的 BizTalk Server 中的教學課程
ms.custom: ''
ms.date: 04/05/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef88eae7-f0f8-4f3f-85d0-3961a47395b6
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f20b35aca2c4fb35419153ccfb149aa34501b21a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975092"
---
# <a name="walkthrough-tracking-policy-execution"></a><span data-ttu-id="76ae8-103">逐步解說： 追蹤原則執行</span><span class="sxs-lookup"><span data-stu-id="76ae8-103">Walkthrough: Tracking Policy Execution</span></span>
<span data-ttu-id="76ae8-104">啟用追蹤的逐步程序**ProcessPurchaseOrder**原則，以及在執行原則之後檢視追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="76ae8-104">Step-by-step procedures for enabling tracking for the **ProcessPurchaseOrder** policy, and for viewing the tracking information after the policy is executed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76ae8-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="76ae8-105">Prerequisites</span></span>  
<span data-ttu-id="76ae8-106">完成[逐步解說： 修改原則](../core/walkthrough-modifying-the-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="76ae8-106">Complete the [Walkthrough: Modifying the Policy](../core/walkthrough-modifying-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="enable-tracking-for-the-processpurchaseorder-policy"></a><span data-ttu-id="76ae8-107">啟用 ProcessPurchaseOrder 原則的追蹤</span><span class="sxs-lookup"><span data-stu-id="76ae8-107">Enable tracking for the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="76ae8-108">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="76ae8-108">Open **BizTalk Server Administration**.</span></span> <span data-ttu-id="76ae8-109">如果您已經開啟，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="76ae8-109">If it's already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="76ae8-110">展開**主控台根目錄**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**RuleTestApp**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-110">Expand **Console Root**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="76ae8-111">以滑鼠右鍵按一下**原則**，選取**新增**，然後選取**原則**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-111">Right-click **Policies**, select **Add**, and then select **Policy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76ae8-112">若要啟用原則的追蹤，您必須使用 [BizTalk Server 管理] 主控台，將原則新增至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="76ae8-112">To enable tracking for a policy, you must add the policy to a BizTalk application by using the BizTalk Server Administration console.</span></span>  
  
4.  <span data-ttu-id="76ae8-113">在**新增原則**對話方塊方塊中，展開  **ProcessPurchaseOrder**，然後選取版本**1.3**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-113">In the **Add Policies** dialog box, expand **ProcessPurchaseOrder**, and select Version **1.3**.</span></span>  
  
5.  <span data-ttu-id="76ae8-114">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="76ae8-115">如果您沒有看到**ProcessPurchaseOrder**在清單中，選取 F5 重新整理檢視。</span><span class="sxs-lookup"><span data-stu-id="76ae8-115">If you don't see **ProcessPurchaseOrder** in the list, select F5 to refresh the view.</span></span>
  
7.  <span data-ttu-id="76ae8-116">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後選取**追蹤。**</span><span class="sxs-lookup"><span data-stu-id="76ae8-116">Right-click **ProcessPurchaseOrder**, and then select **Tracking.**</span></span>  
  
8.  <span data-ttu-id="76ae8-117">在**原則追蹤選項**對話方塊中，選取所有核取方塊**事實活動**，**條件評估**，**規則引發**，和**議程更新**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-117">In the **Policy Tracking Options** dialog box, select all the check boxes for **Fact activity**, **Condition evaluation**, **Rule firings**, and **Agenda updates**.</span></span>  
  
9. <span data-ttu-id="76ae8-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-118">Click **OK**.</span></span>  
  
## <a name="test-the-solution-and-view-the-tracking-information"></a><span data-ttu-id="76ae8-119">測試方案，並檢視追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="76ae8-119">Test the solution and view the tracking information</span></span>  
  
1.  <span data-ttu-id="76ae8-120">開啟**SamplePO.xml**和**SamplePO2.xml** [記事本]，然後將值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-120">Open **SamplePO.xml** and **SamplePO2.xml** in notepad, and change the value of the **Status** field to **XYZ**.</span></span>  
  
2.  <span data-ttu-id="76ae8-121">複製**SamplePO.xml**您在建立[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)協調流程的輸入目錄。</span><span class="sxs-lookup"><span data-stu-id="76ae8-121">Copy **SamplePO.xml** that you created in [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) to the input directory for the orchestration.</span></span>  
  
3.  <span data-ttu-id="76ae8-122">您應該會在協調流程的輸出目錄中看到輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="76ae8-122">You should see an output file in the output directory for the orchestration.</span></span> <span data-ttu-id="76ae8-123">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-123">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
4.  <span data-ttu-id="76ae8-124">在**BizTalk Server 管理**，請移至**群組概觀**頁面上，按一下**群組中樞**索引標籤，然後再按一下**追蹤服務執行個體**.</span><span class="sxs-lookup"><span data-stu-id="76ae8-124">In **BizTalk Server Administration**, go to the **Group Overview** page, click on the **Group Hub** tab, and then click on **Tracked Service Instances**.</span></span>  
  
5.  <span data-ttu-id="76ae8-125">以滑鼠右鍵按一下協調流程 (RuleTest.Orchestration_1)，名稱，然後按一下**訊息流程**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-125">Right-click the name of the Orchestration (RuleTest.Orchestration_1), and then click **Message Flow**.</span></span>  
  
6.  <span data-ttu-id="76ae8-126">按一下**跟隨此連結以檢視此協調流程執行個體的原則執行詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-126">Click **Follow this link to view the Policy execution details for this orchestration instance**.</span></span> <span data-ttu-id="76ae8-127">請確定您看到的視窗中看起來像下圖：</span><span class="sxs-lookup"><span data-stu-id="76ae8-127">Make sure you see the window that looks like the following figure:</span></span>  
  
     <span data-ttu-id="76ae8-128">![BRE &#45;逐步解說 &#45;FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")</span><span class="sxs-lookup"><span data-stu-id="76ae8-128">![BRE&#45;Walkthrough&#45;FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")</span></span>  
  
7. <span data-ttu-id="76ae8-129">按一下時間或 **[processpurchaseorder1.3]** 看到下列畫面。</span><span class="sxs-lookup"><span data-stu-id="76ae8-129">Click the time or **ProcessPurchaseOrder1.3** to see the following screen.</span></span> <span data-ttu-id="76ae8-130">在這個畫面中，您可以看到要求原則執行的服務 (協調流程)、協調流程的識別碼、原則執行的時間，以及原則的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76ae8-130">In this screen, you can see the service (orchestration) that requested the policy execution, the ID of the orchestration, the time at which the policy was executed, and the ID of the policy.</span></span>  
  
     <span data-ttu-id="76ae8-131">![BRE &#45;逐步解說 &#45;PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")</span><span class="sxs-lookup"><span data-stu-id="76ae8-131">![BRE&#45;Walkthrough&#45;PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")</span></span>  
  
8. <span data-ttu-id="76ae8-132">按一下**事實活動**查看事實 （資料） 已判斷提示至規則引擎的工作記憶體與已從規則引擎工作記憶體撤回的事實。</span><span class="sxs-lookup"><span data-stu-id="76ae8-132">Click **Fact Activity** to see the facts (data) that were asserted into the rule engine's working memory and the facts that were retracted from the rule engine's working memory.</span></span>  
  
     <span data-ttu-id="76ae8-133">![BRE &#45;逐步解說 &#45;FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")</span><span class="sxs-lookup"><span data-stu-id="76ae8-133">![BRE&#45;Walkthrough&#45;FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")</span></span>  
  
9. <span data-ttu-id="76ae8-134">在**檔案**功能表上，按一下 **瀏覽回**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-134">On the **File** menu, click **Navigate back**.</span></span>  
  
10. <span data-ttu-id="76ae8-135">按一下**條件評估**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-135">Click **Conditions that Evaluated**.</span></span> <span data-ttu-id="76ae8-136">您會看到有關所評估之條件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="76ae8-136">You see the details about the conditions that were evaluated.</span></span> <span data-ttu-id="76ae8-137">在這種情況下，原則中有兩個規則，且每個原則具有一個條件。</span><span class="sxs-lookup"><span data-stu-id="76ae8-137">In this case, there are two rules in the policy, and each policy has a condition.</span></span> <span data-ttu-id="76ae8-138">您可以看到，評估兩個條件。其中一個評估為`true`，和另一個評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="76ae8-138">You can see that two conditions were evaluated; one evaluated to `true`, and the other one evaluated to `false`.</span></span>  
  
     <span data-ttu-id="76ae8-139">![BRE &#45;逐步解說 &#45;ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")</span><span class="sxs-lookup"><span data-stu-id="76ae8-139">![BRE&#45;Walkthrough&#45;ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")</span></span>  
  
11. <span data-ttu-id="76ae8-140">在**檔案**功能表上，按一下 **瀏覽回**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-140">On the **File** menu, click **Navigate back**.</span></span>  
  
12. <span data-ttu-id="76ae8-141">按一下**議程更新**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-141">Click **Agenda Updates**.</span></span> <span data-ttu-id="76ae8-142">您可以看到只有 ApprovalRule 會新增至議程。</span><span class="sxs-lookup"><span data-stu-id="76ae8-142">You can see that only the ApprovalRule is added to the agenda.</span></span> <span data-ttu-id="76ae8-143">DeniedRule 不會加入到議程因為其條件評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="76ae8-143">The DeniedRule is not added to the agenda because its condition evaluates to `false`.</span></span>  
  
     <span data-ttu-id="76ae8-144">![BRE &#45;逐步解說 &#45;議程](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")</span><span class="sxs-lookup"><span data-stu-id="76ae8-144">![BRE&#45;Walkthrough&#45;Agenda](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")</span></span>  
  
13. <span data-ttu-id="76ae8-145">按一下**ApprovalRule**以查看 ApprovalRule 的定義。</span><span class="sxs-lookup"><span data-stu-id="76ae8-145">Click **ApprovalRule** to see the definition of the ApprovalRule.</span></span>  
  
14. <span data-ttu-id="76ae8-146">在**檔案**功能表上，按一下 **瀏覽回**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-146">On the **File** menu, click **Navigate back**.</span></span>  
  
15. <span data-ttu-id="76ae8-147">在**檔案**功能表上，按一下 **瀏覽回**一次。</span><span class="sxs-lookup"><span data-stu-id="76ae8-147">On **File** menu, click **Navigate back** again.</span></span>  
  
16. <span data-ttu-id="76ae8-148">按一下**規則引發**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-148">Click **Rules that fired**.</span></span> <span data-ttu-id="76ae8-149">您可以看到只有 ApprovalRule 已經引發 (已執行 ApprovalRule 的動作)。</span><span class="sxs-lookup"><span data-stu-id="76ae8-149">You can see that only ApprovalRule was fired (actions for the ApprovalRule were executed).</span></span>  
  
17. <span data-ttu-id="76ae8-150">在**檔案**功能表上，按一下 **瀏覽回**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-150">On the **File** menu, click **Navigate back**.</span></span>  
  
18. <span data-ttu-id="76ae8-151">按一下**未引發的規則**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-151">Click **Rules that did not fire**.</span></span> <span data-ttu-id="76ae8-152">您可以看到 DeniedRule 並未引發，因為它不在議程之中。</span><span class="sxs-lookup"><span data-stu-id="76ae8-152">You can see that DeniedRule was not fired because it was not in the agenda.</span></span>  
  
19. <span data-ttu-id="76ae8-153">重複步驟 1-18 與**SamplePO2.xml**。</span><span class="sxs-lookup"><span data-stu-id="76ae8-153">Repeat steps 1-18 with **SamplePO2.xml**.</span></span>  
  
## <a name="key-details"></a><span data-ttu-id="76ae8-154">索引鍵的詳細資料</span><span class="sxs-lookup"><span data-stu-id="76ae8-154">Key details</span></span>  
  
-   <span data-ttu-id="76ae8-155">追蹤資訊的原則是非常類似於您在商務規則編輯器 」 中測試原則時看到的追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="76ae8-155">The policy tracking information is very similar to the tracking information you see in Business Rule Composer when you test a policy.</span></span>  
  
-   <span data-ttu-id="76ae8-156">雖然協調流程的名稱是 RuleTest.odx，但您看到的協調流程名稱卻是 Orchestration_1，因為協調流程的「類型名稱」是設定為 Orchestration_1，即使變更「名稱」也是如此。</span><span class="sxs-lookup"><span data-stu-id="76ae8-156">Although the orchestration name is RuleTest.odx, you see the name of the orchestration as Orchestration_1, because the Type Name for the orchestration is set to Orchestration_1 even though the Name is changed.</span></span> <span data-ttu-id="76ae8-157">追蹤中會顯示您的協調流程的名稱格式\<命名空間\>。\<輸入名稱\>。</span><span class="sxs-lookup"><span data-stu-id="76ae8-157">Tracking is showing you the orchestration name in the format \<Namespace\>.\<Type Name\>.</span></span>  
  
-   <span data-ttu-id="76ae8-158">當您使用 BizTalk Server 管理主控台從 BizTalk 應用程式刪除原則時，該工具不但會從應用程式刪除原則，也會將該原則從規則引擎資料庫刪除。</span><span class="sxs-lookup"><span data-stu-id="76ae8-158">If you delete a policy from a BizTalk application by using the BizTalk Server Administration console, the tool deletes the policy not only from the application, but also from the rule engine database.</span></span> <span data-ttu-id="76ae8-159">您將無法再於「商務規則編輯器」中看到該原則 (請按 F5 以重新整理畫面)。</span><span class="sxs-lookup"><span data-stu-id="76ae8-159">You will no longer see the policy in Business Rule Composer (press F5 to refresh).</span></span> <span data-ttu-id="76ae8-160">因此，從應用程式刪除原則時應該相當謹慎。</span><span class="sxs-lookup"><span data-stu-id="76ae8-160">Therefore, you should be careful when deleting a policy from an application.</span></span>  
  
-   <span data-ttu-id="76ae8-161">當您停止 RuleTestApp 並選取**完全停止**選項時，ProcessPurchaseOrder 原則 （版本 1.3） 會自動解除部署。</span><span class="sxs-lookup"><span data-stu-id="76ae8-161">When you stop the RuleTestApp and select the **Full Stop** option, the ProcessPurchaseOrder policy (version 1.3) is automatically undeployed.</span></span>  
  
-   <span data-ttu-id="76ae8-162">如果原則是由多個應用程式所使用，您應該針對此原則建立一個個別的應用程式，然後從用戶端應用程式建立該應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="76ae8-162">If a policy is used by multiple applications, create a separate application for the policy and then create references to it from the client applications.</span></span> <span data-ttu-id="76ae8-163">如果將該原則加入所有的用戶端應用程式，則在您停止其中一個用戶端應用程式時，該原則就會解除部署，所有其他的用戶端應用程式都無法再使用該原則。</span><span class="sxs-lookup"><span data-stu-id="76ae8-163">If you add the policy to all the client applications, when you stop one of the client applications, the policy is undeployed, and the other client applications can no longer use the policy.</span></span> <span data-ttu-id="76ae8-164">因此，針對兩個或兩個以上應用程式所共用的原則建立個別的應用程式，是較理想的作法。</span><span class="sxs-lookup"><span data-stu-id="76ae8-164">Therefore it is a good practice to create a separate application for a policy that is shared across two or more applications.</span></span>  
  
-   <span data-ttu-id="76ae8-165">當您啟動 RuleTestApp 時，ProcessPurchaseOrder 原則 (版本 1.3) 會自動部署。</span><span class="sxs-lookup"><span data-stu-id="76ae8-165">When you start the RuleTestApp, the ProcessPurchaseOrder policy (version 1.3) is automatically deployed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="76ae8-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="76ae8-166">Next Steps</span></span>  
 <span data-ttu-id="76ae8-167">既然您已完成此逐步解說，請移至[逐步解說： 部署原則](../core/walkthrough-deploying-the-policy.md)逐步解說，它可讓您部署原則的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="76ae8-167">Now that you have completed this walkthrough, go to the [Walkthrough: Deploying the Policy](../core/walkthrough-deploying-the-policy.md) walkthrough, which gives you step-by-step instructions for deploying policies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ae8-168">請參閱</span><span class="sxs-lookup"><span data-stu-id="76ae8-168">See Also</span></span>  
 <span data-ttu-id="76ae8-169">[如何設定原則的追蹤](../core/how-to-configure-tracking-for-a-policy.md) </span><span class="sxs-lookup"><span data-stu-id="76ae8-169">[How to Configure Tracking for a Policy](../core/how-to-configure-tracking-for-a-policy.md) </span></span>  
 [<span data-ttu-id="76ae8-170">管理原則</span><span class="sxs-lookup"><span data-stu-id="76ae8-170">Managing Policies</span></span>](../core/managing-policies.md)