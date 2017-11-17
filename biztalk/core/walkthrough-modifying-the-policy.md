---
title: "逐步解說： 修改的原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd74440-2a45-4a1a-8e36-98796e1e1392
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7292d541adaf0ae2242d1c504f1a845dde66f5dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-modifying-the-policy"></a><span data-ttu-id="d637f-102">逐步解說： 修改原則</span><span class="sxs-lookup"><span data-stu-id="d637f-102">Walkthrough: Modifying the Policy</span></span>
<span data-ttu-id="d637f-103">本逐步解說提供建立新版的逐步指示**POVocabulary**，建立新版本的**ProcessPurchaseOrder**原則，並使用最新版**POVocabulary**在新版的**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d637f-103">This walkthrough provides step-by-step instructions for creating a new version of the **POVocabulary**, creating a new version of the **ProcessPurchaseOrder** policy, and using the latest version of the **POVocabulary** in the new version of the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d637f-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="d637f-104">Prerequisites</span></span>  
 <span data-ttu-id="d637f-105">您必須先完成[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d637f-105">You must complete the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="d637f-106">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="d637f-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="d637f-107">此逐步解說包含三個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="d637f-107">This walkthrough contains three procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="d637f-108">程序標題</span><span class="sxs-lookup"><span data-stu-id="d637f-108">Procedure title</span></span>|<span data-ttu-id="d637f-109">程序說明</span><span class="sxs-lookup"><span data-stu-id="d637f-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="d637f-110">若要修改 POVocabulary 詞彙</span><span class="sxs-lookup"><span data-stu-id="d637f-110">To modify the POVocabulary vocabulary</span></span>|<span data-ttu-id="d637f-111">提供逐步指示來建立新的詞彙版本的值修改為**允許的項目數目上限**從**500**至**1000年**。</span><span class="sxs-lookup"><span data-stu-id="d637f-111">Provides step-by-step instructions for creating a new vocabulary version to modify the value of **Maximum number of items allowed** from **500** to **1000**.</span></span>|  
|<span data-ttu-id="d637f-112">若要修改 ProcessPurchaseOrder 原則來使用更新的詞彙</span><span class="sxs-lookup"><span data-stu-id="d637f-112">To modify the ProcessPurchaseOrder policy to use the updated vocabulary</span></span>|<span data-ttu-id="d637f-113">提供建立新版的逐步指示**ProcessPurchaseOrder**原則以使用新版本的**POVocabulary**。</span><span class="sxs-lookup"><span data-stu-id="d637f-113">Provides step-by-step instructions for creating a new version of the **ProcessPurchaseOrder** policy to use the new version of **POVocabulary**.</span></span>|  
|<span data-ttu-id="d637f-114">測試方案</span><span class="sxs-lookup"><span data-stu-id="d637f-114">To test the solution</span></span>|<span data-ttu-id="d637f-115">提供測試方案及驗證新原則已生效的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="d637f-115">Provides step-by-step instructions for testing the solution and verifying that the new policy is in effect.</span></span>|  
  
### <a name="to-modify-the-povocabulary-vocabulary"></a><span data-ttu-id="d637f-116">若要修改 POVocabulary 詞彙</span><span class="sxs-lookup"><span data-stu-id="d637f-116">To modify the POVocabulary vocabulary</span></span>  
  
1.  <span data-ttu-id="d637f-117">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d637f-117">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d637f-118">如果您有商務規則編輯器已開啟，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。</span><span class="sxs-lookup"><span data-stu-id="d637f-118">If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d637f-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d637f-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d637f-120">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d637f-120">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d637f-121">在 [事實總管] 視窗中，依序展開**詞彙**，然後展開**POVocabulary**。</span><span class="sxs-lookup"><span data-stu-id="d637f-121">In the Facts Explorer window, expand **Vocabularies**, and then expand **POVocabulary**.</span></span>  
  
3.  <span data-ttu-id="d637f-122">以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="d637f-122">Right-click **Version 1.0 - Published**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="d637f-123">以滑鼠右鍵按一下**POVocabulary**，然後按一下 **貼上詞彙版本**。</span><span class="sxs-lookup"><span data-stu-id="d637f-123">Right-click **POVocabulary**, and then click **Paste Vocabulary Version**.</span></span>  
  
5.  <span data-ttu-id="d637f-124">按兩下**數目的項目允許的最大**中**版本 1.1 （未儲存）**啟動 [詞彙定義精靈]。</span><span class="sxs-lookup"><span data-stu-id="d637f-124">Double-click **Maximum Number of Items Allowed** in **Version 1.1 (not saved)** to start the Vocabulary Definition Wizard.</span></span>  
  
6.  <span data-ttu-id="d637f-125">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d637f-125">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d637f-126">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d637f-126">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d637f-127">將值從變更**500**至**1000年**。</span><span class="sxs-lookup"><span data-stu-id="d637f-127">Change the value from **500** to **1000**.</span></span>  
  
9. <span data-ttu-id="d637f-128">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d637f-128">Click **Finish**.</span></span>  
  
10. <span data-ttu-id="d637f-129">以滑鼠右鍵按一下**版本 1.1 （未儲存）**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="d637f-129">Right-click **Version 1.1 (not saved)**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="d637f-130">以滑鼠右鍵按一下**1.1 版**，然後按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="d637f-130">Right-click **Version 1.1**, and then click **Publish**.</span></span>  
  
### <a name="to-modify-the-processpurchaseorder-policy-to-use-the-updated-vocabulary"></a><span data-ttu-id="d637f-131">若要修改 ProcessPurchaseOrder 原則來使用更新的詞彙</span><span class="sxs-lookup"><span data-stu-id="d637f-131">To modify the ProcessPurchaseOrder policy to use the updated vocabulary</span></span>  
  
1.  <span data-ttu-id="d637f-132">在 [原則總管] 中，展開**原則**，然後展開**ProcessPurchaseOrder**。</span><span class="sxs-lookup"><span data-stu-id="d637f-132">In Policy Explorer, expand **Policies**, and then expand **ProcessPurchaseOrder**.</span></span>  
  
2.  <span data-ttu-id="d637f-133">以滑鼠右鍵按一下**1.2 版**，然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="d637f-133">Right-click **Version 1.2**, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="d637f-134">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下  **pastepolicyversion**。</span><span class="sxs-lookup"><span data-stu-id="d637f-134">Right-click **ProcessPurchaseOrder**, and then click **PastePolicyVersion**.</span></span>  
  
4.  <span data-ttu-id="d637f-135">按一下**ApprovalRule**中**（未儲存） 1.3 版**。</span><span class="sxs-lookup"><span data-stu-id="d637f-135">Click **ApprovalRule** in **Version 1.3 (not saved)**.</span></span>  
  
5.  <span data-ttu-id="d637f-136">在 [事實總管] 中，展開**詞彙**，依序展開**POVocabulary**，然後展開**1.1 版-已發佈**。</span><span class="sxs-lookup"><span data-stu-id="d637f-136">In Facts Explorer, expand **Vocabularies**, expand **POVocabulary**, and then expand **Version 1.1 - Published**.</span></span>  
  
6.  <span data-ttu-id="d637f-137">拖曳**數目的項目允許的最大**中**1.1 版-已發佈**取代**數目的項目允許的最大**IF 窗格中的 版本 1.0。</span><span class="sxs-lookup"><span data-stu-id="d637f-137">Drag **Maximum Number of Items Allowed** in **Version 1.1 - Published** to replace **Maximum Number of Items Allowed** of version 1.0 in the IF pane.</span></span>  
  
7.  <span data-ttu-id="d637f-138">重複步驟 4-6 **DeniedRule**。</span><span class="sxs-lookup"><span data-stu-id="d637f-138">Repeat steps 4-6 with **DeniedRule**.</span></span>  
  
8.  <span data-ttu-id="d637f-139">以滑鼠右鍵按一下**（未儲存） 1.3 版**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="d637f-139">Right-click **Version 1.3 (not saved)**, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="d637f-140">以滑鼠右鍵按一下**1.3 版**，然後按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="d637f-140">Right-click **Version 1.3**, and then click **Publish**.</span></span>  
  
10. <span data-ttu-id="d637f-141">以滑鼠右鍵按一下**1.3 版**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="d637f-141">Right-click **Version 1.3**, and then click **Deploy**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="d637f-142">測試方案</span><span class="sxs-lookup"><span data-stu-id="d637f-142">To test the solution</span></span>  
  
1.  <span data-ttu-id="d637f-143">按一下**啟動**，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d637f-143">Click **Start**, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="d637f-144">如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。</span><span class="sxs-lookup"><span data-stu-id="d637f-144">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="d637f-145">以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="d637f-145">Right-click **RuleTestApp**, and then click **Start**.</span></span> <span data-ttu-id="d637f-146">如果**啟動**是停用，應用程式已經在執行且您可以略過下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d637f-146">If **Start** is disabled, the application is already running and you can ignore the next step.</span></span>  
  
3.  <span data-ttu-id="d637f-147">按一下 **[啟動]**。</span><span class="sxs-lookup"><span data-stu-id="d637f-147">Click **Start**.</span></span>  
  
4.  <span data-ttu-id="d637f-148">複製**SamplePO2.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。</span><span class="sxs-lookup"><span data-stu-id="d637f-148">Copy the **SamplePO2.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
5.  <span data-ttu-id="d637f-149">您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d637f-149">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory.</span></span> <span data-ttu-id="d637f-150">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="d637f-150">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d637f-151">值**數量**SamplePO2.xml 中的欄位為 700。</span><span class="sxs-lookup"><span data-stu-id="d637f-151">The value of the **Quantity** field in SamplePO2.xml is 700.</span></span> <span data-ttu-id="d637f-152">1.3 版**ProcessPurchaseOrder**原則會比較此值與 1000，而不是比較它與 500 1.2 版一樣。</span><span class="sxs-lookup"><span data-stu-id="d637f-152">Version 1.3 of the **ProcessPurchaseOrder** policy compares this value with 1000 instead of comparing it with 500 as version 1.2 did.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d637f-153">註解</span><span class="sxs-lookup"><span data-stu-id="d637f-153">Comments</span></span>  
  
-   <span data-ttu-id="d637f-154">已發佈的原則便無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="d637f-154">A published policy cannot be modified.</span></span> <span data-ttu-id="d637f-155">您必須建立新版的原則，才能加以修改。</span><span class="sxs-lookup"><span data-stu-id="d637f-155">You must create a new version of the policy to modify it.</span></span> <span data-ttu-id="d637f-156">同樣地，已發佈的詞彙便無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="d637f-156">Similarly, a published vocabulary cannot be modified.</span></span> <span data-ttu-id="d637f-157">您必須建立新版的詞彙，才能加以修改。</span><span class="sxs-lookup"><span data-stu-id="d637f-157">You must create a new version of the vocabulary to modify it.</span></span>  
  
-   <span data-ttu-id="d637f-158">協調流程叫用原則使用**呼叫規則**圖形會使用最新部署的原則版本。</span><span class="sxs-lookup"><span data-stu-id="d637f-158">The orchestration invoking a policy by using the **Call Rules** shape uses the latest deployed version of the policy.</span></span> <span data-ttu-id="d637f-159">例如，如果您已部署 1.0、1.1、1.2 和 1.3 版的原則，則協調流程會使用 1.3 版。</span><span class="sxs-lookup"><span data-stu-id="d637f-159">For example, if you have versions 1.0, 1.1, 1.2, and 1.3 of the policy deployed, the orchestration uses version 1.3.</span></span> <span data-ttu-id="d637f-160">如果未部署 1.3 版，但是已部署 1.2 版，則協調流程會使用 1.2 版。</span><span class="sxs-lookup"><span data-stu-id="d637f-160">If version 1.3 is not deployed and version 1.2 is deployed, the orchestration uses version 1.2.</span></span> <span data-ttu-id="d637f-161">因此，如果您想要切換回 1.2 版，只需要解除部署 1.3 版，並確定 1.2 版已經部署。</span><span class="sxs-lookup"><span data-stu-id="d637f-161">Therefore if you want to switch back to using version 1.2, you just need to undeploy version 1.3, and make sure that version 1.2 is deployed.</span></span>  
  
-   <span data-ttu-id="d637f-162">若要使用特定版本的原則，以從協調流程，您應該使用**運算式**圖形，並叫用規則引擎來執行原則以程式設計方式使用**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="d637f-162">To use a specific version of a policy from an orchestration, you should use an **Expression** shape and invoke the rule engine to execute the policy programmatically by using the **Policy.Execute** method.</span></span>  
  
-   <span data-ttu-id="d637f-163">請注意，1.3 版的原則會使用來自 1.0 和 1.1 版 POVocabulary 詞彙的詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="d637f-163">Note that version 1.3 of the policy uses the vocabulary definitions from both version 1.0 and version 1.1 of the POVocabulary vocabulary.</span></span> <span data-ttu-id="d637f-164">如果您將 1.3 版的原則匯出到 XML 檔案，並在另一部電腦上匯入它來建立原則，則此匯入程序會尋找這兩個版本的詞彙。</span><span class="sxs-lookup"><span data-stu-id="d637f-164">If you export version 1.3 of the policy to an XML file, and import it to create the policy on a different computer, the import process looks for both versions of the vocabulary.</span></span> <span data-ttu-id="d637f-165">因此，在您匯入 1.3 版的原則之前，必須先匯出 1.0 和 1.1 版的詞彙，並將其匯入。</span><span class="sxs-lookup"><span data-stu-id="d637f-165">Therefore you need to export both version 1.0 and version 1.1 of the vocabulary and import them before importing version 1.3 of the policy.</span></span>  
  
-   <span data-ttu-id="d637f-166">在您部署更新版的原則之後，您應該等候大約 60 秒鐘，才能開始測試方案。</span><span class="sxs-lookup"><span data-stu-id="d637f-166">After you deploy a newer version of the policy, you should wait approximately 60 seconds before testing the solution.</span></span> <span data-ttu-id="d637f-167">根據預設，規則引擎更新服務會每隔 60 秒鐘 (1 分鐘) 尋找一次原則的任何更新。</span><span class="sxs-lookup"><span data-stu-id="d637f-167">The rule engine update service looks for any updates to a policy every 60 seconds (1 minute) by default.</span></span> <span data-ttu-id="d637f-168">如果有更新，它會以更新的資訊重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="d637f-168">If there are updates, it refreshes the cache with the updated information.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d637f-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d637f-169">Next Steps</span></span>  
  
-   <span data-ttu-id="d637f-170">現在您已完成此逐步解說中，執行[逐步解說： 追蹤原則執行](../core/walkthrough-tracking-policy-execution.md)逐步解說，它提供追蹤原則執行細節的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="d637f-170">Now that you have completed this walkthrough, perform the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough, which gives you step-by-step instructions for tracking policy execution details.</span></span>