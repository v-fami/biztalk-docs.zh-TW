---
title: 逐步解說： 叫用的協調流程的原則 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb2d2974-8a36-4d36-905c-799e4236ef99
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33bef51b2c702e71fcf6ef0ea0c4fd63b28fbde8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976553"
---
# <a name="walkthrough-invoking-the-policy-from-an-orchestration"></a><span data-ttu-id="6629c-102">逐步解說： 叫用原則與協調流程</span><span class="sxs-lookup"><span data-stu-id="6629c-102">Walkthrough: Invoking the Policy from an Orchestration</span></span>
<span data-ttu-id="6629c-103">您可以使用下列其中一種方式，從協調流程叫用原則：</span><span class="sxs-lookup"><span data-stu-id="6629c-103">You can invoke a policy from an orchestration in one of the following ways:</span></span>  

- <span data-ttu-id="6629c-104">藉由使用**呼叫規則**圖形</span><span class="sxs-lookup"><span data-stu-id="6629c-104">By using the **Call Rules** shape</span></span>  

- <span data-ttu-id="6629c-105">藉由使用**運算式**圖形，並以程式設計方式叫用規則引擎來執行原則 (**Policy.Execute**方法)</span><span class="sxs-lookup"><span data-stu-id="6629c-105">By using the **Expression** shape, and programmatically invoking the rule engine to execute the policy (**Policy.Execute** method)</span></span>  

  <span data-ttu-id="6629c-106">使用**呼叫規則**圖案是最常見的方式，而叫用原則，以從協調流程的建議的方式。</span><span class="sxs-lookup"><span data-stu-id="6629c-106">Using the **Call Rules** shape is the most common way and also the recommended way to invoke a policy from an orchestration.</span></span> <span data-ttu-id="6629c-107">本逐步解說提供逐步程序使用**呼叫規則**圖形來叫用**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-107">This walkthrough provides step-by-step procedures for using the **Call Rules** shape to invoke the **ProcessPurchaseOrder** policy.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="6629c-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="6629c-108">Prerequisites</span></span>  
 <span data-ttu-id="6629c-109">您必須先完成[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="6629c-109">You must complete the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough before performing this walkthrough.</span></span>  

## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="6629c-110">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="6629c-110">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="6629c-111">此逐步解說包含七個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="6629c-111">This walkthrough contains seven procedures, as described in the following table.</span></span>  

|<span data-ttu-id="6629c-112">程序標題</span><span class="sxs-lookup"><span data-stu-id="6629c-112">Procedure title</span></span>|<span data-ttu-id="6629c-113">程序說明</span><span class="sxs-lookup"><span data-stu-id="6629c-113">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="6629c-114">使用結構描述和協調流程建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6629c-114">To create a BizTalk project with a schema and an orchestration</span></span>|<span data-ttu-id="6629c-115">提供逐步指示來建立結構描述和協調流程叫用**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-115">Provides step-by-step instructions for creating a schema and an orchestration that invokes the **ProcessPurchaseOrder** policy.</span></span>|  
|<span data-ttu-id="6629c-116">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="6629c-116">To create message variables</span></span>|<span data-ttu-id="6629c-117">提供逐步指示，說明如何建立協調流程中所使用的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="6629c-117">Provides step-by-step instructions for creating message variables used in the orchestration.</span></span>|  
|<span data-ttu-id="6629c-118">設定圖形</span><span class="sxs-lookup"><span data-stu-id="6629c-118">To configure shapes</span></span>|<span data-ttu-id="6629c-119">提供逐步指示，說明如何在協調流程中設定圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-119">Provides step-by-step instructions for configuring shapes in the orchestration.</span></span>|  
|<span data-ttu-id="6629c-120">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="6629c-120">To create ports</span></span>|<span data-ttu-id="6629c-121">提供逐步指示，說明如何在協調流程中建立連接埠。</span><span class="sxs-lookup"><span data-stu-id="6629c-121">Provides step-by-step instructions for creating ports in the orchestration.</span></span>|  
|<span data-ttu-id="6629c-122">連接連接埠與圖形</span><span class="sxs-lookup"><span data-stu-id="6629c-122">To connect ports with the shapes</span></span>|<span data-ttu-id="6629c-123">提供逐步指示，說明如何連接連接埠與圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-123">Provides step-by-step instructions for connecting ports with the shapes.</span></span>|  
|<span data-ttu-id="6629c-124">建置和部署解決方案</span><span class="sxs-lookup"><span data-stu-id="6629c-124">To build and deploy the solution</span></span>|<span data-ttu-id="6629c-125">提供逐步指示，說明如何建置和測試解決方案。</span><span class="sxs-lookup"><span data-stu-id="6629c-125">Provides step-by-step instructions for building and deploying the solution.</span></span>|  
|<span data-ttu-id="6629c-126">測試方案</span><span class="sxs-lookup"><span data-stu-id="6629c-126">To test the solution</span></span>|<span data-ttu-id="6629c-127">提供測試方案的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="6629c-127">Provides step-by-step instructions for testing the solution.</span></span>|  

### <a name="to-create-a-biztalk-project-with-a-schema-and-an-orchestration"></a><span data-ttu-id="6629c-128">使用結構描述和協調流程建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6629c-128">To create a BizTalk project with a schema and an orchestration</span></span>  

1. <span data-ttu-id="6629c-129">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6629c-129">Start **Microsoft Visual Studio**.</span></span>  

2. <span data-ttu-id="6629c-130">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6629c-130">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  

3. <span data-ttu-id="6629c-131">在 **新的專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6629c-131">In the **New Project** dialog box, do the following:</span></span>  


   |             <span data-ttu-id="6629c-132">使用</span><span class="sxs-lookup"><span data-stu-id="6629c-132">Use this</span></span>              |                             <span data-ttu-id="6629c-133">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="6629c-133">To do this</span></span>                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         <span data-ttu-id="6629c-134">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="6629c-134">**Project types**</span></span>         |                     <span data-ttu-id="6629c-135">按一下  **BizTalk 專案**。</span><span class="sxs-lookup"><span data-stu-id="6629c-135">Click **BizTalk Projects**.</span></span>                     |
   |           <span data-ttu-id="6629c-136">**範本**</span><span class="sxs-lookup"><span data-stu-id="6629c-136">**Templates**</span></span>           |               <span data-ttu-id="6629c-137">按一下 **空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="6629c-137">Click **Empty BizTalk Server Project**.</span></span>               |
   |             <span data-ttu-id="6629c-138">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6629c-138">**Name**</span></span>              |                         <span data-ttu-id="6629c-139">型別**RuleTest**。</span><span class="sxs-lookup"><span data-stu-id="6629c-139">Type **RuleTest**.</span></span>                          |
   |           <span data-ttu-id="6629c-140">**位置**</span><span class="sxs-lookup"><span data-stu-id="6629c-140">**Location**</span></span>            |                  <span data-ttu-id="6629c-141">指定**C:\BRE-Walkthroughs**。</span><span class="sxs-lookup"><span data-stu-id="6629c-141">Specify **C:\BRE-Walkthroughs**.</span></span>                   |
   |         <span data-ttu-id="6629c-142">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="6629c-142">**Solution Name**</span></span>         |                        <span data-ttu-id="6629c-143">型別**RuleTestSol**。</span><span class="sxs-lookup"><span data-stu-id="6629c-143">Type **RuleTestSol**.</span></span>                        |
   | <span data-ttu-id="6629c-144">**為解決方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="6629c-144">**Create directory for solution**</span></span> | <span data-ttu-id="6629c-145">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="6629c-145">Select this check box to create a directory for the solution files.</span></span> |


4. <span data-ttu-id="6629c-146">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-146">Click **OK**.</span></span> <span data-ttu-id="6629c-147">**RuleTest**專案應該會出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="6629c-147">The **RuleTest** project should appear in Solution Explorer.</span></span> <span data-ttu-id="6629c-148">如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="6629c-148">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  

5. <span data-ttu-id="6629c-149">在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="6629c-149">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **Existing Item**.</span></span>  

6. <span data-ttu-id="6629c-150">瀏覽並新增**PO.xsd**您在建立的結構描述檔案[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="6629c-150">Browse and add the **PO.xsd** schema file you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough.</span></span> <span data-ttu-id="6629c-151">Visual Studio 會建立一份**PO.xsd**檔案，並將它新增至專案。</span><span class="sxs-lookup"><span data-stu-id="6629c-151">Visual Studio makes a copy of the **PO.xsd** file and adds it to the project.</span></span>  

7. <span data-ttu-id="6629c-152">在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="6629c-152">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **New Item**.</span></span>  

8. <span data-ttu-id="6629c-153">在 **加入新項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6629c-153">In the **Add New Item** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="6629c-154">使用</span><span class="sxs-lookup"><span data-stu-id="6629c-154">Use this</span></span>    |            <span data-ttu-id="6629c-155">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="6629c-155">To do this</span></span>            |
   |----------------|----------------------------------|
   | <span data-ttu-id="6629c-156">**類別**</span><span class="sxs-lookup"><span data-stu-id="6629c-156">**Categories**</span></span> |  <span data-ttu-id="6629c-157">按一下 **協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="6629c-157">Click **Orchestration Files**.</span></span>  |
   | <span data-ttu-id="6629c-158">**範本**</span><span class="sxs-lookup"><span data-stu-id="6629c-158">**Templates**</span></span>  | <span data-ttu-id="6629c-159">按一下  **BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="6629c-159">Click **BizTalk Orchestration**.</span></span> |
   |    <span data-ttu-id="6629c-160">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6629c-160">**Name**</span></span>    |      <span data-ttu-id="6629c-161">型別**RuleTest.odx**。</span><span class="sxs-lookup"><span data-stu-id="6629c-161">Type **RuleTest.odx**.</span></span>      |


9. <span data-ttu-id="6629c-162">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="6629c-162">Click **Add**.</span></span>  

10. <span data-ttu-id="6629c-163">以滑鼠右鍵按一下**從 [工具箱] 拖曳圖形**，指向**插入圖形**，然後按一下**接收**。</span><span class="sxs-lookup"><span data-stu-id="6629c-163">Right-click **Drop a shape from the toolbox here**, point to **Insert Shape**, and then click **Receive**.</span></span>  

11. <span data-ttu-id="6629c-164">在 [屬性] 視窗中，變更名稱**接收**圖形至**ReceivePO**，並將值**啟動**屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="6629c-164">In the Properties window, change the name of the **Receive** shape to **ReceivePO**, and set the value of the **Activate** property to `true`.</span></span>  

12. <span data-ttu-id="6629c-165">在工具箱中，在**BizTalk 協調流程**索引標籤，拖曳**呼叫規則**圖形下方的連接線到**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-165">In the Toolbox, on the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line below the **Receive** shape.</span></span>  

13. <span data-ttu-id="6629c-166">在 [屬性] 視窗中，變更名稱**呼叫規則**圖形至**CallProcessPOPolicy**。</span><span class="sxs-lookup"><span data-stu-id="6629c-166">In the Properties window, change the name of the **Call Rules** shape to **CallProcessPOPolicy**.</span></span>  

14. <span data-ttu-id="6629c-167">以滑鼠右鍵按一下下面的**呼叫規則**圖形中，指向**插入圖形**，然後按一下**傳送**。</span><span class="sxs-lookup"><span data-stu-id="6629c-167">Right-click below the **Call Rules** shape, point to **Insert Shape**, and then click **Send**.</span></span>  

15. <span data-ttu-id="6629c-168">在 [屬性] 視窗中，變更名稱**傳送**圖形至**SendPO**。</span><span class="sxs-lookup"><span data-stu-id="6629c-168">In the Properties window, change the name of the **Send** shape to **SendPO**.</span></span> <span data-ttu-id="6629c-169">協調流程的外觀應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="6629c-169">The orchestration should look like the following figure.</span></span>  

     <span data-ttu-id="6629c-170">![BRE&#45;逐步解說&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span><span class="sxs-lookup"><span data-stu-id="6629c-170">![BRE&#45;Walkthrough&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span></span>  

### <a name="to-create-message-variables"></a><span data-ttu-id="6629c-171">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="6629c-171">To create message variables</span></span>  

1.  <span data-ttu-id="6629c-172">在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="6629c-172">In the Orchestration View window, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="6629c-173">如果看不到協調流程檢視 視窗中，按一下**檢視**功能表上，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="6629c-173">If you do not see the Orchestration View window, click the **View** menu, point to **Other Windows**, and then click **Orchestration View**.</span></span> <span data-ttu-id="6629c-174">[協調流程檢視] 視窗通常是顯示在 [方案總管] 索引標籤旁邊的索引標籤上。根據預設，新的訊息會命名為**Message_1**。</span><span class="sxs-lookup"><span data-stu-id="6629c-174">Typically, the Orchestration View window is on the tab next to the Solution Explorer tab. By default, the new message is named **Message_1**.</span></span>  

     <span data-ttu-id="6629c-175">![BRE&#45;逐步解說&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span><span class="sxs-lookup"><span data-stu-id="6629c-175">![BRE&#45;Walkthrough&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span></span>  

2.  <span data-ttu-id="6629c-176">在 [協調流程檢視] 視窗中，按一下**Message_1**。</span><span class="sxs-lookup"><span data-stu-id="6629c-176">In the Orchestration View window, click **Message_1**.</span></span>  

3.  <span data-ttu-id="6629c-177">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6629c-177">In the Properties window, do the following:</span></span>  

    |<span data-ttu-id="6629c-178">使用</span><span class="sxs-lookup"><span data-stu-id="6629c-178">Use this</span></span>|<span data-ttu-id="6629c-179">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="6629c-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6629c-180">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="6629c-180">**Identifier**</span></span>|<span data-ttu-id="6629c-181">型別 **[poinst]**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="6629c-181">Type **POInst**, and then press ENTER.</span></span>|  
    |<span data-ttu-id="6629c-182">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="6629c-182">**Message Type**</span></span>|<span data-ttu-id="6629c-183">從下拉式清單中，依序展開**結構描述**，然後選取**RuleTest.PO**。</span><span class="sxs-lookup"><span data-stu-id="6629c-183">From the drop-down list, expand **Schemas**, and then select **RuleTest.PO**.</span></span>|  

     <span data-ttu-id="6629c-184">![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span><span class="sxs-lookup"><span data-stu-id="6629c-184">![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span></span>  

### <a name="to-configure-shapes"></a><span data-ttu-id="6629c-185">設定圖形</span><span class="sxs-lookup"><span data-stu-id="6629c-185">To configure shapes</span></span>  

1. <span data-ttu-id="6629c-186">選取 **接收**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-186">Select the **Receive** shape in Orchestration Designer.</span></span>  

2. <span data-ttu-id="6629c-187">在 [屬性] 視窗中，選取 **[poinst]** for**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="6629c-187">In the Properties window, select **POInst** for the **Message** property.</span></span>  

3. <span data-ttu-id="6629c-188">按兩下**呼叫規則**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-188">Double-click the **Call Rules** shape in Orchestration Designer.</span></span>  

4. <span data-ttu-id="6629c-189">在 **呼叫規則原則組態**對話方塊中，選取**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-189">In the **Call Rules policy configuration** dialog box, select **ProcessPurchaseOrder** for the policy.</span></span>  

5. <span data-ttu-id="6629c-190">按一下 下一步**\\**<em>下面的 \* \* 參數名稱</em><em>，然後選取 \**poinst</em>* 做為原則的參數。</span><span class="sxs-lookup"><span data-stu-id="6629c-190">Click next to **\\**<em>, below \*\*Parameter Name</em><em>, and select \**POInst</em>* as a parameter to the policy.</span></span>  

    <span data-ttu-id="6629c-191">![BRE&#45;逐步解說&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span><span class="sxs-lookup"><span data-stu-id="6629c-191">![BRE&#45;Walkthrough&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span></span>  

6. <span data-ttu-id="6629c-192">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-192">Click **OK**.</span></span>  

7. <span data-ttu-id="6629c-193">選取 **傳送**協調流程中的圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-193">Select the **Send** shape in the orchestration.</span></span>  

8. <span data-ttu-id="6629c-194">在 [屬性] 視窗中設定的值**訊息類型**屬性設 **[poinst]**。</span><span class="sxs-lookup"><span data-stu-id="6629c-194">In the Properties window, set the value of the **Message Type** property to **POInst**.</span></span>  

### <a name="to-create-ports"></a><span data-ttu-id="6629c-195">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="6629c-195">To create ports</span></span>  

1.  <span data-ttu-id="6629c-196">建立兩個資料夾**輸入**並**輸出**，在 C:\BRE-Walkthroughs\RuleTestSol 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6629c-196">Create two folders, **Input** and **Output**, in the C:\BRE-Walkthroughs\RuleTestSol folder.</span></span>  

2.  <span data-ttu-id="6629c-197">以滑鼠右鍵按一下協調流程，在左側連接埠介面，然後按一下**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="6629c-197">Right-click the left port surface of the orchestration, and then click **New Configured Port**.</span></span>  

3.  <span data-ttu-id="6629c-198">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-198">Click **Next**.</span></span> <span data-ttu-id="6629c-199">型別 **[receivepoprt]** 連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="6629c-199">Type **ReceivePOPrt** for the port name.</span></span>  

4.  <span data-ttu-id="6629c-200">按一下 [**下一步]** 兩次。</span><span class="sxs-lookup"><span data-stu-id="6629c-200">Click **Next** twice.</span></span>  

5.  <span data-ttu-id="6629c-201">選取 **立即指定**for**連接埠繫結**。</span><span class="sxs-lookup"><span data-stu-id="6629c-201">Select **Specify Now** for the **port binding**.</span></span>  

6.  <span data-ttu-id="6629c-202">指定**檔案**for**傳輸**，然後輸入做為輸入的目錄名稱**C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml**與檔案遮罩 (**\*.xml**) uri。</span><span class="sxs-lookup"><span data-stu-id="6629c-202">Specify **FILE** for the **transport**, and type the name of the input directory as **C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml** along with the file mask (**\*.xml**) for the URI.</span></span>  

7.  <span data-ttu-id="6629c-203">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="6629c-203">Click **Next**, and then click **Finish**.</span></span>  

8.  <span data-ttu-id="6629c-204">以滑鼠右鍵按一下協調流程，在右側連接埠介面，然後按一下**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="6629c-204">Right-click the right port surface of the orchestration, and then click **New Configuration Port**.</span></span>  

9. <span data-ttu-id="6629c-205">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-205">Click **Next**.</span></span> <span data-ttu-id="6629c-206">型別**SendPOPort**連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="6629c-206">Type **SendPOPort** for the port name.</span></span>  

10. <span data-ttu-id="6629c-207">按一下 [**下一步]** 兩次。</span><span class="sxs-lookup"><span data-stu-id="6629c-207">Click **Next** twice.</span></span>  

11. <span data-ttu-id="6629c-208">變更**連接埠通訊方向**要**我將總是傳送的訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="6629c-208">Change the **Port direction of communication** to **I'll always be sending messages on this port**.</span></span>  

12. <span data-ttu-id="6629c-209">選取 **立即指定**for**連接埠繫結**。</span><span class="sxs-lookup"><span data-stu-id="6629c-209">Select **Specify Now** for the **port binding**.</span></span>  

13. <span data-ttu-id="6629c-210">指定**檔案**for**傳輸**，並輸入與輸出目錄的名稱**C:\BRE-Walkthroughs\RuleTestSol\Output**，和 %MessageID%.xml 與輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6629c-210">Specify **FILE** for the **transport**, and type the name of the output directory as **C:\BRE-Walkthroughs\RuleTestSol\Output**,and %MessageID%.xml as the output file name.</span></span>  

14. <span data-ttu-id="6629c-211">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="6629c-211">Click **Next**, and then click **Finish**.</span></span>  

### <a name="to-connect-ports-with-the-shapes"></a><span data-ttu-id="6629c-212">連接連接埠與圖形</span><span class="sxs-lookup"><span data-stu-id="6629c-212">To connect ports with the shapes</span></span>  

1.  <span data-ttu-id="6629c-213">連接 **[receivepoprt]** 連接埠連接到**ReceivePO**圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-213">Connect the **ReceivePOPrt** port to the **ReceivePO** shape.</span></span> <span data-ttu-id="6629c-214">(將連接埠介面上 [ReceivePOPrt] 連接埠右邊的箭號，拖曳到 [ReceivePO] 上的方塊)。</span><span class="sxs-lookup"><span data-stu-id="6629c-214">(Drag the arrow to the right of ReceivePOPrt port on the port surface to the box on the ReceivePO shape.)</span></span>  

     <span data-ttu-id="6629c-215">![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span><span class="sxs-lookup"><span data-stu-id="6629c-215">![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span></span>  

2.  <span data-ttu-id="6629c-216">連接**SendPO**圖形至 **[sendpoprt]** 連接埠。</span><span class="sxs-lookup"><span data-stu-id="6629c-216">Connect the **SendPO** shape to the **SendPOPrt** port.</span></span>  

     <span data-ttu-id="6629c-217">![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span><span class="sxs-lookup"><span data-stu-id="6629c-217">![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span></span>  

### <a name="to-build-and-deploy-the-solution"></a><span data-ttu-id="6629c-218">建置和部署解決方案</span><span class="sxs-lookup"><span data-stu-id="6629c-218">To build and deploy the solution</span></span>  

1. <span data-ttu-id="6629c-219">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6629c-219">Start **Microsoft Visual Studio**.</span></span>  

2. <span data-ttu-id="6629c-220">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6629c-220">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the **RuleTest** project, and then click **Properties**.</span></span>  

3. <span data-ttu-id="6629c-221">在 專案設計工具 （在中間窗格） 中，按一下**簽署**。</span><span class="sxs-lookup"><span data-stu-id="6629c-221">In Project Designer (in the center pane), click **Signing**.</span></span>  

4. <span data-ttu-id="6629c-222">在 簽署 索引標籤，核取**簽署組件**核取方塊;在下拉式清單**選擇強式名稱金鑰檔**，按一下**新增**;在 **金鑰檔案名稱**欄位中，輸入規則測試;在 **密碼**欄位 （選擇性），設定密碼，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6629c-222">In Signing tab, Check **Sign the assembly** checkbox; In the dropdown list **Choose a strong name key file**, click **New**; In the **Key File name** field, enter Rule Test; In the **Password** field (Optional),  set Password, and then click **OK**.</span></span>  

5. <span data-ttu-id="6629c-223">在 專案設計工具中，按一下**部署**切換至 部署 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6629c-223">In Project Designer, click **Deployment** to switch to the Deployment tab.</span></span>  

6. <span data-ttu-id="6629c-224">指定**RuleTestApp**做為應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="6629c-224">Specify **RuleTestApp** as the application name.</span></span>  

    <span data-ttu-id="6629c-225">![BRE&#45;逐步解說&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span><span class="sxs-lookup"><span data-stu-id="6629c-225">![BRE&#45;Walkthrough&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span></span>  

7. <span data-ttu-id="6629c-226">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-226">Click **OK**.</span></span>  

8. <span data-ttu-id="6629c-227">以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="6629c-227">Right-click the **RuleTest** project, and then click **Build**.</span></span>  

9. <span data-ttu-id="6629c-228">以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="6629c-228">Right-click the **RuleTest** project, and then click **Deploy**.</span></span>  

### <a name="to-test-the-solution"></a><span data-ttu-id="6629c-229">測試方案</span><span class="sxs-lookup"><span data-stu-id="6629c-229">To test the solution</span></span>  

1. <span data-ttu-id="6629c-230">在 商務規則編輯器 中，展開**原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**.</span><span class="sxs-lookup"><span data-stu-id="6629c-230">In Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Publish**.</span></span>  

2. <span data-ttu-id="6629c-231">以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="6629c-231">Right-click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  

3. <span data-ttu-id="6629c-232">在 **開始**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="6629c-232">In the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="6629c-233">如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。</span><span class="sxs-lookup"><span data-stu-id="6629c-233">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  

4. <span data-ttu-id="6629c-234">依序展開**主控台根目錄**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6629c-234">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  

5. <span data-ttu-id="6629c-235">以滑鼠右鍵按一下**RuleTestApp**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="6629c-235">Right-click **RuleTestApp**, and then click **Configure**.</span></span>  

6. <span data-ttu-id="6629c-236">按一下  **Orchestration_1**，並指定**BizTalkServerApplication**為主機。</span><span class="sxs-lookup"><span data-stu-id="6629c-236">Click **Orchestration_1**, and specify **BizTalkServerApplication** as the host.</span></span>  

    <span data-ttu-id="6629c-237">![BRE&#45;逐步解說&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span><span class="sxs-lookup"><span data-stu-id="6629c-237">![BRE&#45;Walkthrough&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span></span>  

7. <span data-ttu-id="6629c-238">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6629c-238">Click **OK**.</span></span>  

8. <span data-ttu-id="6629c-239">以滑鼠右鍵按一下**RuleTestApp**，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="6629c-239">Right-click **RuleTestApp**, and then click **Start**.</span></span>  

9. <span data-ttu-id="6629c-240">在 [**啟動 'RuleTestApp' 應用程式**] 對話方塊中，按一下**開始**，應用程式已成功啟動，然後等到。</span><span class="sxs-lookup"><span data-stu-id="6629c-240">In the **Start 'RuleTestApp' Application** dialog box, click **Start**, and then wait until the application is started successfully.</span></span>  

10. <span data-ttu-id="6629c-241">開啟**SamplePO.xml**並**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。</span><span class="sxs-lookup"><span data-stu-id="6629c-241">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  

11. <span data-ttu-id="6629c-242">複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。</span><span class="sxs-lookup"><span data-stu-id="6629c-242">Copy the **SamplePO.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  

12. <span data-ttu-id="6629c-243">您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="6629c-243">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="6629c-244">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="6629c-244">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  

13. <span data-ttu-id="6629c-245">重複步驟 11 和 12 與**SamplePO2.xml**，並請注意，值**狀態**輸出文件中的欄位是相同的輸入文件 (**xyz**)。</span><span class="sxs-lookup"><span data-stu-id="6629c-245">Repeat steps 11 and 12 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**xyz**).</span></span>  

## <a name="comments"></a><span data-ttu-id="6629c-246">註解</span><span class="sxs-lookup"><span data-stu-id="6629c-246">Comments</span></span>  

-   <span data-ttu-id="6629c-247">在此逐步解說中，將圖形新增至協調流程時，您並未使用 [工具箱] 中的圖形，</span><span class="sxs-lookup"><span data-stu-id="6629c-247">In this walkthrough, to add the shapes to the orchestration, you did not use the shapes from the Toolbox.</span></span> <span data-ttu-id="6629c-248">而是按一下滑鼠右鍵，並選取想要插入的圖形。</span><span class="sxs-lookup"><span data-stu-id="6629c-248">Instead, you clicked the right mouse button and selected the shape that you wanted to insert.</span></span>  

-   <span data-ttu-id="6629c-249">組態**呼叫規則**圖形會判斷使用的型別時查看最新的儲存版本。</span><span class="sxs-lookup"><span data-stu-id="6629c-249">The configuration for the **Call Rules** shape looks at the latest saved version when determining the types used.</span></span> <span data-ttu-id="6629c-250">在執行階段，則將使用最新的已部署版本。</span><span class="sxs-lookup"><span data-stu-id="6629c-250">At run time, the latest deployed version will be used.</span></span>  

-   <span data-ttu-id="6629c-251">如果您打算使用最新的部署版本以外的原則版本，您應該使用**運算式**圖形，並叫用規則引擎以程式設計方式來執行該特定版本的原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-251">If you plan to use a policy version other than the latest deployed version, you should use an **Expression** shape, and invoke the rule engine programmatically to execute the policy of that specific version.</span></span> <span data-ttu-id="6629c-252">如需詳細資訊，請參閱 <<c0> [ 如何執行原則來](../core/how-to-execute-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="6629c-252">For more information, see [How to Execute Policies](../core/how-to-execute-policies.md).</span></span>  

-   <span data-ttu-id="6629c-253">**呼叫規則**圖形會使用一樣，重新建構訊息**建構訊息**圖形，接著可能會導致遺失訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="6629c-253">The **Call Rules** shape reconstructs the message, as if using a **Construct Message** shape, which in turn may cause context properties of the message to be lost.</span></span>  

-   <span data-ttu-id="6629c-254">您無法修改已發佈的原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-254">A policy cannot be modified after it is published.</span></span>  

-   <span data-ttu-id="6629c-255">用戶端應用程式只能存取已部署的原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-255">The client applications can access only the deployed policies.</span></span> <span data-ttu-id="6629c-256">如果用戶端應用程式會叫用未部署的原則，就會產生 「 規則引擎**RuleEngineDeploymentNotDeployedException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6629c-256">If a client application invokes a policy that is not deployed, the rule engine generates a **RuleEngineDeploymentNotDeployedException** exception.</span></span> <span data-ttu-id="6629c-257">您可以在應用程式事件日誌中查看詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="6629c-257">You can see the detailed error message in the application event log.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="6629c-258">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6629c-258">Next Steps</span></span>  
 <span data-ttu-id="6629c-259">既然您已完成本逐步解說中，執行[逐步解說： 建立和使用詞彙的原則中](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md)逐步解說，它可讓您建立的詞彙和使用詞彙的逐步指示**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="6629c-259">Now that you have completed this walkthrough, perform the [Walkthrough: Creating and Using a Vocabulary in the Policy](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) walkthrough, which gives you step-by-step instructions for creating a vocabulary and using the vocabulary in the **ProcessPurchaseOrder** policy.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6629c-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6629c-260">See Also</span></span>  
 <span data-ttu-id="6629c-261">[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="6629c-261">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 <span data-ttu-id="6629c-262">[議程與優先順序](../core/agenda-and-priority.md) </span><span class="sxs-lookup"><span data-stu-id="6629c-262">[Agenda and Priority](../core/agenda-and-priority.md) </span></span>  
 [<span data-ttu-id="6629c-263">在協調流程中叫用商務規則</span><span class="sxs-lookup"><span data-stu-id="6629c-263">Invoking Business Rules in Orchestrations</span></span>](../core/invoking-business-rules-in-orchestrations.md)