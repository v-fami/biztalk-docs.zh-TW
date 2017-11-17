---
title: "逐步解說： 叫用從協調流程原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb2d2974-8a36-4d36-905c-799e4236ef99
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36de942d34a4235b689b464192a460451e7c921a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-invoking-the-policy-from-an-orchestration"></a><span data-ttu-id="efe82-102">逐步解說： 叫用的原則，從協調流程</span><span class="sxs-lookup"><span data-stu-id="efe82-102">Walkthrough: Invoking the Policy from an Orchestration</span></span>
<span data-ttu-id="efe82-103">您可以使用下列其中一種方式，從協調流程叫用原則：</span><span class="sxs-lookup"><span data-stu-id="efe82-103">You can invoke a policy from an orchestration in one of the following ways:</span></span>  
  
-   <span data-ttu-id="efe82-104">使用**呼叫規則**圖形</span><span class="sxs-lookup"><span data-stu-id="efe82-104">By using the **Call Rules** shape</span></span>  
  
-   <span data-ttu-id="efe82-105">使用**運算式**圖形，並以程式設計方式叫用規則引擎來執行原則 (**Policy.Execute**方法)</span><span class="sxs-lookup"><span data-stu-id="efe82-105">By using the **Expression** shape, and programmatically invoking the rule engine to execute the policy (**Policy.Execute** method)</span></span>  
  
 <span data-ttu-id="efe82-106">使用**呼叫規則**圖案是最常見的方式，而叫用原則，以從協調流程的建議的方式。</span><span class="sxs-lookup"><span data-stu-id="efe82-106">Using the **Call Rules** shape is the most common way and also the recommended way to invoke a policy from an orchestration.</span></span> <span data-ttu-id="efe82-107">此逐步解說提供逐步程序使用**呼叫規則**圖形來叫用**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-107">This walkthrough provides step-by-step procedures for using the **Call Rules** shape to invoke the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="efe82-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="efe82-108">Prerequisites</span></span>  
 <span data-ttu-id="efe82-109">您必須先完成[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="efe82-109">You must complete the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="efe82-110">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="efe82-110">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="efe82-111">此逐步解說包含七個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="efe82-111">This walkthrough contains seven procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="efe82-112">程序標題</span><span class="sxs-lookup"><span data-stu-id="efe82-112">Procedure title</span></span>|<span data-ttu-id="efe82-113">程序說明</span><span class="sxs-lookup"><span data-stu-id="efe82-113">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="efe82-114">使用結構描述和協調流程建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="efe82-114">To create a BizTalk project with a schema and an orchestration</span></span>|<span data-ttu-id="efe82-115">提供逐步指示來建立結構描述和協調流程叫用**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-115">Provides step-by-step instructions for creating a schema and an orchestration that invokes the **ProcessPurchaseOrder** policy.</span></span>|  
|<span data-ttu-id="efe82-116">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="efe82-116">To create message variables</span></span>|<span data-ttu-id="efe82-117">提供逐步指示，說明如何建立協調流程中所使用的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="efe82-117">Provides step-by-step instructions for creating message variables used in the orchestration.</span></span>|  
|<span data-ttu-id="efe82-118">設定圖形</span><span class="sxs-lookup"><span data-stu-id="efe82-118">To configure shapes</span></span>|<span data-ttu-id="efe82-119">提供逐步指示，說明如何在協調流程中設定圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-119">Provides step-by-step instructions for configuring shapes in the orchestration.</span></span>|  
|<span data-ttu-id="efe82-120">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="efe82-120">To create ports</span></span>|<span data-ttu-id="efe82-121">提供逐步指示，說明如何在協調流程中建立連接埠。</span><span class="sxs-lookup"><span data-stu-id="efe82-121">Provides step-by-step instructions for creating ports in the orchestration.</span></span>|  
|<span data-ttu-id="efe82-122">連接連接埠與圖形</span><span class="sxs-lookup"><span data-stu-id="efe82-122">To connect ports with the shapes</span></span>|<span data-ttu-id="efe82-123">提供逐步指示，說明如何連接連接埠與圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-123">Provides step-by-step instructions for connecting ports with the shapes.</span></span>|  
|<span data-ttu-id="efe82-124">建置和部署解決方案</span><span class="sxs-lookup"><span data-stu-id="efe82-124">To build and deploy the solution</span></span>|<span data-ttu-id="efe82-125">提供逐步指示，說明如何建置和測試解決方案。</span><span class="sxs-lookup"><span data-stu-id="efe82-125">Provides step-by-step instructions for building and deploying the solution.</span></span>|  
|<span data-ttu-id="efe82-126">測試方案</span><span class="sxs-lookup"><span data-stu-id="efe82-126">To test the solution</span></span>|<span data-ttu-id="efe82-127">提供測試方案的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="efe82-127">Provides step-by-step instructions for testing the solution.</span></span>|  
  
### <a name="to-create-a-biztalk-project-with-a-schema-and-an-orchestration"></a><span data-ttu-id="efe82-128">使用結構描述和協調流程建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="efe82-128">To create a BizTalk project with a schema and an orchestration</span></span>  
  
1.  <span data-ttu-id="efe82-129">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="efe82-129">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="efe82-130">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="efe82-130">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="efe82-131">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="efe82-131">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="efe82-132">使用</span><span class="sxs-lookup"><span data-stu-id="efe82-132">Use this</span></span>|<span data-ttu-id="efe82-133">動作</span><span class="sxs-lookup"><span data-stu-id="efe82-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="efe82-134">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="efe82-134">**Project types**</span></span>|<span data-ttu-id="efe82-135">按一下**BizTalk 專案**。</span><span class="sxs-lookup"><span data-stu-id="efe82-135">Click **BizTalk Projects**.</span></span>|  
    |<span data-ttu-id="efe82-136">**範本**</span><span class="sxs-lookup"><span data-stu-id="efe82-136">**Templates**</span></span>|<span data-ttu-id="efe82-137">按一下**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="efe82-137">Click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="efe82-138">**名稱**</span><span class="sxs-lookup"><span data-stu-id="efe82-138">**Name**</span></span>|<span data-ttu-id="efe82-139">型別**RuleTest**。</span><span class="sxs-lookup"><span data-stu-id="efe82-139">Type **RuleTest**.</span></span>|  
    |<span data-ttu-id="efe82-140">**位置**</span><span class="sxs-lookup"><span data-stu-id="efe82-140">**Location**</span></span>|<span data-ttu-id="efe82-141">指定**C:\BRE-Walkthroughs**。</span><span class="sxs-lookup"><span data-stu-id="efe82-141">Specify **C:\BRE-Walkthroughs**.</span></span>|  
    |<span data-ttu-id="efe82-142">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="efe82-142">**Solution Name**</span></span>|<span data-ttu-id="efe82-143">型別**RuleTestSol**。</span><span class="sxs-lookup"><span data-stu-id="efe82-143">Type **RuleTestSol**.</span></span>|  
    |<span data-ttu-id="efe82-144">**為方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="efe82-144">**Create directory for solution**</span></span>|<span data-ttu-id="efe82-145">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="efe82-145">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="efe82-146">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-146">Click **OK**.</span></span> <span data-ttu-id="efe82-147">**RuleTest**專案應該會出現在 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="efe82-147">The **RuleTest** project should appear in Solution Explorer.</span></span> <span data-ttu-id="efe82-148">如果看不到方案總管 中，按一下**方案總管 中**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="efe82-148">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="efe82-149">在 方案總管 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="efe82-149">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **Existing Item**.</span></span>  
  
6.  <span data-ttu-id="efe82-150">瀏覽並加入**PO.xsd**在所建立的結構描述檔案[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="efe82-150">Browse and add the **PO.xsd** schema file you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough.</span></span> <span data-ttu-id="efe82-151">Visual Studio 會建立一份**PO.xsd**檔案，並將它加入至專案。</span><span class="sxs-lookup"><span data-stu-id="efe82-151">Visual Studio makes a copy of the **PO.xsd** file and adds it to the project.</span></span>  
  
7.  <span data-ttu-id="efe82-152">在 方案總管 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="efe82-152">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **New Item**.</span></span>  
  
8.  <span data-ttu-id="efe82-153">在**加入新項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="efe82-153">In the **Add New Item** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="efe82-154">使用</span><span class="sxs-lookup"><span data-stu-id="efe82-154">Use this</span></span>|<span data-ttu-id="efe82-155">動作</span><span class="sxs-lookup"><span data-stu-id="efe82-155">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="efe82-156">**類別**</span><span class="sxs-lookup"><span data-stu-id="efe82-156">**Categories**</span></span>|<span data-ttu-id="efe82-157">按一下**協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="efe82-157">Click **Orchestration Files**.</span></span>|  
    |<span data-ttu-id="efe82-158">**範本**</span><span class="sxs-lookup"><span data-stu-id="efe82-158">**Templates**</span></span>|<span data-ttu-id="efe82-159">按一下**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="efe82-159">Click **BizTalk Orchestration**.</span></span>|  
    |<span data-ttu-id="efe82-160">**名稱**</span><span class="sxs-lookup"><span data-stu-id="efe82-160">**Name**</span></span>|<span data-ttu-id="efe82-161">型別**RuleTest.odx**。</span><span class="sxs-lookup"><span data-stu-id="efe82-161">Type **RuleTest.odx**.</span></span>|  
  
9. <span data-ttu-id="efe82-162">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-162">Click **Add**.</span></span>  
  
10. <span data-ttu-id="efe82-163">以滑鼠右鍵按一下**從 工具箱 拖曳圖形**，指向 **插入圖形**，然後按一下 **接收**。</span><span class="sxs-lookup"><span data-stu-id="efe82-163">Right-click **Drop a shape from the toolbox here**, point to **Insert Shape**, and then click **Receive**.</span></span>  
  
11. <span data-ttu-id="efe82-164">在 [屬性] 視窗中變更名稱**接收**圖形至**ReceivePO**，和設定的值**啟動**屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="efe82-164">In the Properties window, change the name of the **Receive** shape to **ReceivePO**, and set the value of the **Activate** property to `true`.</span></span>  
  
12. <span data-ttu-id="efe82-165">在工具箱中，在**BizTalk 協調流程**索引標籤，拖曳**呼叫規則**圖形下方的連接線到**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-165">In the Toolbox, on the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line below the **Receive** shape.</span></span>  
  
13. <span data-ttu-id="efe82-166">在 [屬性] 視窗中變更名稱**呼叫規則**圖形至**CallProcessPOPolicy**。</span><span class="sxs-lookup"><span data-stu-id="efe82-166">In the Properties window, change the name of the **Call Rules** shape to **CallProcessPOPolicy**.</span></span>  
  
14. <span data-ttu-id="efe82-167">以滑鼠右鍵按一下下面的**呼叫規則**圖形中，指向 **插入圖形**，然後按一下 **傳送**。</span><span class="sxs-lookup"><span data-stu-id="efe82-167">Right-click below the **Call Rules** shape, point to **Insert Shape**, and then click **Send**.</span></span>  
  
15. <span data-ttu-id="efe82-168">在 [屬性] 視窗中變更名稱**傳送**圖形至**SendPO**。</span><span class="sxs-lookup"><span data-stu-id="efe82-168">In the Properties window, change the name of the **Send** shape to **SendPO**.</span></span> <span data-ttu-id="efe82-169">協調流程的外觀應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="efe82-169">The orchestration should look like the following figure.</span></span>  
  
     <span data-ttu-id="efe82-170">![BRE &#45;逐步解說 &#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span><span class="sxs-lookup"><span data-stu-id="efe82-170">![BRE&#45;Walkthrough&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span></span>  
  
### <a name="to-create-message-variables"></a><span data-ttu-id="efe82-171">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="efe82-171">To create message variables</span></span>  
  
1.  <span data-ttu-id="efe82-172">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**訊息**，然後按一下 [**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="efe82-172">In the Orchestration View window, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="efe82-173">如果看不到 協調流程檢視 視窗，請按一下**檢視**功能表上，指向**其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="efe82-173">If you do not see the Orchestration View window, click the **View** menu, point to **Other Windows**, and then click **Orchestration View**.</span></span> <span data-ttu-id="efe82-174">[協調流程檢視] 視窗通常是顯示在 [方案總管] 索引標籤旁邊的索引標籤上。根據預設，新的訊息會命名為**Message_1**。</span><span class="sxs-lookup"><span data-stu-id="efe82-174">Typically, the Orchestration View window is on the tab next to the Solution Explorer tab. By default, the new message is named **Message_1**.</span></span>  
  
     <span data-ttu-id="efe82-175">![BRE &#45;逐步解說 &#45; OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span><span class="sxs-lookup"><span data-stu-id="efe82-175">![BRE&#45;Walkthrough&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span></span>  
  
2.  <span data-ttu-id="efe82-176">在 [協調流程檢視] 視窗中，按一下**Message_1**。</span><span class="sxs-lookup"><span data-stu-id="efe82-176">In the Orchestration View window, click **Message_1**.</span></span>  
  
3.  <span data-ttu-id="efe82-177">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="efe82-177">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="efe82-178">使用</span><span class="sxs-lookup"><span data-stu-id="efe82-178">Use this</span></span>|<span data-ttu-id="efe82-179">動作</span><span class="sxs-lookup"><span data-stu-id="efe82-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="efe82-180">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="efe82-180">**Identifier**</span></span>|<span data-ttu-id="efe82-181">型別**[poinst]**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="efe82-181">Type **POInst**, and then press ENTER.</span></span>|  
    |<span data-ttu-id="efe82-182">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="efe82-182">**Message Type**</span></span>|<span data-ttu-id="efe82-183">從下拉式清單中，展開 **結構描述**，然後選取**ruletest.po**。</span><span class="sxs-lookup"><span data-stu-id="efe82-183">From the drop-down list, expand **Schemas**, and then select **RuleTest.PO**.</span></span>|  
  
     <span data-ttu-id="efe82-184">![BRE &#45;逐步解說 &#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span><span class="sxs-lookup"><span data-stu-id="efe82-184">![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span></span>  
  
### <a name="to-configure-shapes"></a><span data-ttu-id="efe82-185">設定圖形</span><span class="sxs-lookup"><span data-stu-id="efe82-185">To configure shapes</span></span>  
  
1.  <span data-ttu-id="efe82-186">選取**接收**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-186">Select the **Receive** shape in Orchestration Designer.</span></span>  
  
2.  <span data-ttu-id="efe82-187">在 [屬性] 視窗中，選取**[poinst]**如**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="efe82-187">In the Properties window, select **POInst** for the **Message** property.</span></span>  
  
3.  <span data-ttu-id="efe82-188">按兩下**呼叫規則**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-188">Double-click the **Call Rules** shape in Orchestration Designer.</span></span>  
  
4.  <span data-ttu-id="efe82-189">在**呼叫規則原則組態**對話方塊中，選取**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-189">In the **Call Rules policy configuration** dialog box, select **ProcessPurchaseOrder** for the policy.</span></span>  
  
5.  <span data-ttu-id="efe82-190">按一下 下一步 **\***底下**參數名稱**，然後選取**poinst**做為參數的原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-190">Click next to **\***, below **Parameter Name**, and select **POInst** as a parameter to the policy.</span></span>  
  
     <span data-ttu-id="efe82-191">![BRE &#45;逐步解說 &#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span><span class="sxs-lookup"><span data-stu-id="efe82-191">![BRE&#45;Walkthrough&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span></span>  
  
6.  <span data-ttu-id="efe82-192">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-192">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="efe82-193">選取**傳送**圖形在協調流程中的。</span><span class="sxs-lookup"><span data-stu-id="efe82-193">Select the **Send** shape in the orchestration.</span></span>  
  
8.  <span data-ttu-id="efe82-194">在 [屬性] 視窗中設定的值**訊息類型**屬性**[poinst]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-194">In the Properties window, set the value of the **Message Type** property to **POInst**.</span></span>  
  
### <a name="to-create-ports"></a><span data-ttu-id="efe82-195">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="efe82-195">To create ports</span></span>  
  
1.  <span data-ttu-id="efe82-196">建立兩個資料夾，**輸入**和**輸出**，C:\BRE-Walkthroughs\RuleTestSol 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="efe82-196">Create two folders, **Input** and **Output**, in the C:\BRE-Walkthroughs\RuleTestSol folder.</span></span>  
  
2.  <span data-ttu-id="efe82-197">以滑鼠右鍵按一下協調流程中，左連接埠介面，然後按一下**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="efe82-197">Right-click the left port surface of the orchestration, and then click **New Configured Port**.</span></span>  
  
3.  <span data-ttu-id="efe82-198">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-198">Click **Next**.</span></span> <span data-ttu-id="efe82-199">型別**[receivepoprt]**連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="efe82-199">Type **ReceivePOPrt** for the port name.</span></span>  
  
4.  <span data-ttu-id="efe82-200">按一下**下一步**兩次。</span><span class="sxs-lookup"><span data-stu-id="efe82-200">Click **Next** twice.</span></span>  
  
5.  <span data-ttu-id="efe82-201">選取**立即指定**如**連接埠繫結**。</span><span class="sxs-lookup"><span data-stu-id="efe82-201">Select **Specify Now** for the **port binding**.</span></span>  
  
6.  <span data-ttu-id="efe82-202">指定**檔案**如**傳輸**，然後輸入做為輸入的目錄名稱**C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml**檔案遮罩 (**\*.xml**) uri。</span><span class="sxs-lookup"><span data-stu-id="efe82-202">Specify **FILE** for the **transport**, and type the name of the input directory as **C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml** along with the file mask (**\*.xml**) for the URI.</span></span>  
  
7.  <span data-ttu-id="efe82-203">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-203">Click **Next**, and then click **Finish**.</span></span>  
  
8.  <span data-ttu-id="efe82-204">以滑鼠右鍵按一下協調流程，在右側連接埠介面，然後按一下**新組態連接埠**。</span><span class="sxs-lookup"><span data-stu-id="efe82-204">Right-click the right port surface of the orchestration, and then click **New Configuration Port**.</span></span>  
  
9. <span data-ttu-id="efe82-205">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-205">Click **Next**.</span></span> <span data-ttu-id="efe82-206">型別**SendPOPort**連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="efe82-206">Type **SendPOPort** for the port name.</span></span>  
  
10. <span data-ttu-id="efe82-207">按一下**下一步**兩次。</span><span class="sxs-lookup"><span data-stu-id="efe82-207">Click **Next** twice.</span></span>  
  
11. <span data-ttu-id="efe82-208">變更**連接埠通訊方向**至**我將總是傳送訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="efe82-208">Change the **Port direction of communication** to **I'll always be sending messages on this port**.</span></span>  
  
12. <span data-ttu-id="efe82-209">選取**立即指定**如**連接埠繫結**。</span><span class="sxs-lookup"><span data-stu-id="efe82-209">Select **Specify Now** for the **port binding**.</span></span>  
  
13. <span data-ttu-id="efe82-210">指定**檔案**如**傳輸**，然後輸入做為輸出目錄的名稱**C:\BRE-Walkthroughs\RuleTestSol\Output**，和 %MessageID%.xml 和輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="efe82-210">Specify **FILE** for the **transport**, and type the name of the output directory as **C:\BRE-Walkthroughs\RuleTestSol\Output**,and %MessageID%.xml as the output file name.</span></span>  
  
14. <span data-ttu-id="efe82-211">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-211">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-connect-ports-with-the-shapes"></a><span data-ttu-id="efe82-212">連接連接埠與圖形</span><span class="sxs-lookup"><span data-stu-id="efe82-212">To connect ports with the shapes</span></span>  
  
1.  <span data-ttu-id="efe82-213">連接**[receivepoprt]**埠連接到**ReceivePO**圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-213">Connect the **ReceivePOPrt** port to the **ReceivePO** shape.</span></span> <span data-ttu-id="efe82-214">(將連接埠介面上 [ReceivePOPrt] 連接埠右邊的箭號，拖曳到 [ReceivePO] 上的方塊)。</span><span class="sxs-lookup"><span data-stu-id="efe82-214">(Drag the arrow to the right of ReceivePOPrt port on the port surface to the box on the ReceivePO shape.)</span></span>  
  
     <span data-ttu-id="efe82-215">![BRE &#45;逐步解說 &#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span><span class="sxs-lookup"><span data-stu-id="efe82-215">![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span></span>  
  
2.  <span data-ttu-id="efe82-216">連接**SendPO**圖形至**[sendpoprt]**連接埠。</span><span class="sxs-lookup"><span data-stu-id="efe82-216">Connect the **SendPO** shape to the **SendPOPrt** port.</span></span>  
  
     <span data-ttu-id="efe82-217">![BRE &#45;逐步解說 &#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span><span class="sxs-lookup"><span data-stu-id="efe82-217">![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span></span>  
  
### <a name="to-build-and-deploy-the-solution"></a><span data-ttu-id="efe82-218">建置和部署解決方案</span><span class="sxs-lookup"><span data-stu-id="efe82-218">To build and deploy the solution</span></span>  
  
1.  <span data-ttu-id="efe82-219">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="efe82-219">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="efe82-220">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="efe82-220">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the **RuleTest** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="efe82-221">在 專案設計工具 （在中間窗格） 中，按一下 **簽署**。</span><span class="sxs-lookup"><span data-stu-id="efe82-221">In Project Designer (in the center pane), click **Signing**.</span></span>  
  
4.  <span data-ttu-id="efe82-222">在 簽署 索引標籤中，核取**簽署組件**核取方塊。在下拉式清單中**選擇強式名稱金鑰檔**，按一下 **新增**;在**金鑰檔案名稱**欄位中，輸入規則測試。在**密碼**欄位 （選擇性）、 設定密碼，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="efe82-222">In Signing tab, Check **Sign the assembly** checkbox; In the dropdown list **Choose a strong name key file**, click **New**; In the **Key File name** field, enter Rule Test; In the **Password** field (Optional),  set Password, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="efe82-223">在 專案設計工具中，按一下 **部署**切換至 部署 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="efe82-223">In Project Designer, click **Deployment** to switch to the Deployment tab.</span></span>  
  
6.  <span data-ttu-id="efe82-224">指定**RuleTestApp**做為應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="efe82-224">Specify **RuleTestApp** as the application name.</span></span>  
  
     <span data-ttu-id="efe82-225">![BRE &#45;逐步解說 &#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span><span class="sxs-lookup"><span data-stu-id="efe82-225">![BRE&#45;Walkthrough&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span></span>  
  
7.  <span data-ttu-id="efe82-226">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-226">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="efe82-227">以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="efe82-227">Right-click the **RuleTest** project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="efe82-228">以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="efe82-228">Right-click the **RuleTest** project, and then click **Deploy**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="efe82-229">測試方案</span><span class="sxs-lookup"><span data-stu-id="efe82-229">To test the solution</span></span>  
  
1.  <span data-ttu-id="efe82-230">在 商務規則編輯器 中展開 **原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**.</span><span class="sxs-lookup"><span data-stu-id="efe82-230">In Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="efe82-231">以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="efe82-231">Right-click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
3.  <span data-ttu-id="efe82-232">在**啟動**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="efe82-232">In the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="efe82-233">如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。</span><span class="sxs-lookup"><span data-stu-id="efe82-233">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
4.  <span data-ttu-id="efe82-234">展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="efe82-234">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
5.  <span data-ttu-id="efe82-235">以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="efe82-235">Right-click **RuleTestApp**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="efe82-236">按一下**Orchestration_1**，並指定**BizTalkServerApplication**為主機。</span><span class="sxs-lookup"><span data-stu-id="efe82-236">Click **Orchestration_1**, and specify **BizTalkServerApplication** as the host.</span></span>  
  
     <span data-ttu-id="efe82-237">![BRE &#45;逐步解說 &#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span><span class="sxs-lookup"><span data-stu-id="efe82-237">![BRE&#45;Walkthrough&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span></span>  
  
7.  <span data-ttu-id="efe82-238">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="efe82-238">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="efe82-239">以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="efe82-239">Right-click **RuleTestApp**, and then click **Start**.</span></span>  
  
9. <span data-ttu-id="efe82-240">在**啟動 'RuleTestApp' 應用程式**對話方塊中，按一下 **啟動**，然後等到應用程式已成功啟動。</span><span class="sxs-lookup"><span data-stu-id="efe82-240">In the **Start 'RuleTestApp' Application** dialog box, click **Start**, and then wait until the application is started successfully.</span></span>  
  
10. <span data-ttu-id="efe82-241">開啟**SamplePO.xml**和**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="efe82-241">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
11. <span data-ttu-id="efe82-242">複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。</span><span class="sxs-lookup"><span data-stu-id="efe82-242">Copy the **SamplePO.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
12. <span data-ttu-id="efe82-243">您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="efe82-243">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="efe82-244">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="efe82-244">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
13. <span data-ttu-id="efe82-245">重複步驟 11 和 12 **SamplePO2.xml**，並注意值**狀態**輸出文件中的欄位會與輸入文件中的相同 (**xyz**)。</span><span class="sxs-lookup"><span data-stu-id="efe82-245">Repeat steps 11 and 12 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**xyz**).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="efe82-246">註解</span><span class="sxs-lookup"><span data-stu-id="efe82-246">Comments</span></span>  
  
-   <span data-ttu-id="efe82-247">在此逐步解說中，將圖形新增至協調流程時，您並未使用 [工具箱] 中的圖形，</span><span class="sxs-lookup"><span data-stu-id="efe82-247">In this walkthrough, to add the shapes to the orchestration, you did not use the shapes from the Toolbox.</span></span> <span data-ttu-id="efe82-248">而是按一下滑鼠右鍵，並選取想要插入的圖形。</span><span class="sxs-lookup"><span data-stu-id="efe82-248">Instead, you clicked the right mouse button and selected the shape that you wanted to insert.</span></span>  
  
-   <span data-ttu-id="efe82-249">組態**呼叫規則**圖形會決定使用的型別時查看儲存的最新版本。</span><span class="sxs-lookup"><span data-stu-id="efe82-249">The configuration for the **Call Rules** shape looks at the latest saved version when determining the types used.</span></span> <span data-ttu-id="efe82-250">在執行階段，則將使用最新的已部署版本。</span><span class="sxs-lookup"><span data-stu-id="efe82-250">At run time, the latest deployed version will be used.</span></span>  
  
-   <span data-ttu-id="efe82-251">如果您打算使用最新的部署版本以外的原則版本，您應該使用**運算式**圖形，並叫用規則引擎以程式設計方式來執行該特定版本的原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-251">If you plan to use a policy version other than the latest deployed version, you should use an **Expression** shape, and invoke the rule engine programmatically to execute the policy of that specific version.</span></span> <span data-ttu-id="efe82-252">如需詳細資訊，請參閱[如何執行原則來](../core/how-to-execute-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="efe82-252">For more information, see [How to Execute Policies](../core/how-to-execute-policies.md).</span></span>  
  
-   <span data-ttu-id="efe82-253">**呼叫規則**圖形重新建構訊息，如同使用**建構訊息**圖形，這可能造成遺失訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="efe82-253">The **Call Rules** shape reconstructs the message, as if using a **Construct Message** shape, which in turn may cause context properties of the message to be lost.</span></span>  
  
-   <span data-ttu-id="efe82-254">您無法修改已發佈的原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-254">A policy cannot be modified after it is published.</span></span>  
  
-   <span data-ttu-id="efe82-255">用戶端應用程式只能存取已部署的原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-255">The client applications can access only the deployed policies.</span></span> <span data-ttu-id="efe82-256">如果用戶端應用程式會叫用未部署的原則，規則引擎就會產生**RuleEngineDeploymentNotDeployedException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="efe82-256">If a client application invokes a policy that is not deployed, the rule engine generates a **RuleEngineDeploymentNotDeployedException** exception.</span></span> <span data-ttu-id="efe82-257">您可以在應用程式事件日誌中查看詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="efe82-257">You can see the detailed error message in the application event log.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="efe82-258">後續步驟</span><span class="sxs-lookup"><span data-stu-id="efe82-258">Next Steps</span></span>  
 <span data-ttu-id="efe82-259">現在您已完成此逐步解說中，執行[逐步解說： 建立和使用詞彙的原則中](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md)逐步解說，它可讓您建立詞彙和使用詞彙的逐步指示**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="efe82-259">Now that you have completed this walkthrough, perform the [Walkthrough: Creating and Using a Vocabulary in the Policy](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) walkthrough, which gives you step-by-step instructions for creating a vocabulary and using the vocabulary in the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe82-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe82-260">See Also</span></span>  
 <span data-ttu-id="efe82-261">[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="efe82-261">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 <span data-ttu-id="efe82-262">[議程與優先順序](../core/agenda-and-priority.md) </span><span class="sxs-lookup"><span data-stu-id="efe82-262">[Agenda and Priority](../core/agenda-and-priority.md) </span></span>  
 [<span data-ttu-id="efe82-263">叫用協調流程中的商務規則</span><span class="sxs-lookup"><span data-stu-id="efe82-263">Invoking Business Rules in Orchestrations</span></span>](../core/invoking-business-rules-in-orchestrations.md)