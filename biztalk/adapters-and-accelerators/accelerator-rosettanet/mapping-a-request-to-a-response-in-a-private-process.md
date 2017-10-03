---
title: "將要求對應至私用程序中回應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, maps
- private processes, mapping requests
- private processes, customizing
- orchestrations, adding maps
- maps, adding to orchestrations
- maps, creating
- customizing private processes
- requests, mapping
- requests, private processes
ms.assetid: 5452c0a2-3a9b-43e7-bfa7-713eef0eab3b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bd67be0bbe70794f6fe6f77d388b69660e2d1ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-a-request-to-a-response-in-a-private-process"></a><span data-ttu-id="c0426-102">將要求對應至私用程序中回應時間</span><span class="sxs-lookup"><span data-stu-id="c0426-102">Mapping a Request to a Response in a Private Process</span></span>
<span data-ttu-id="c0426-103">本主題描述如何將私用回應者程序所接收的要求訊息對應 — 從[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]公用回應者程序，來回應訊息傳送給[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]公用回應者程序。</span><span class="sxs-lookup"><span data-stu-id="c0426-103">This topic describes how to map a request message received by the private responder process—from the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] public responder process, to a response message that can be sent to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public responder process.</span></span>  
  
 <span data-ttu-id="c0426-104">當回應者收到要求訊息時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會藉由從公開程序協調流程到私用程序協調流程的方式，路由這個要求訊息至商務營運系統 (LOB) 程式。</span><span class="sxs-lookup"><span data-stu-id="c0426-104">When a responder receives a request message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] routes the request message from the public-process orchestration, to the private-process orchestration, to the line-of-business (LOB) program.</span></span> <span data-ttu-id="c0426-105">這個回應者需要從 LOB 程式取得回應服務內容，並產生 RosettaNet 回應訊息傳回給啟動者。</span><span class="sxs-lookup"><span data-stu-id="c0426-105">The responder requires the response service content from the LOB program to generate a RosettaNet response message back to the initiator.</span></span> <span data-ttu-id="c0426-106">回應訊息中的許多項目都是使用要求訊息的值加以填入。</span><span class="sxs-lookup"><span data-stu-id="c0426-106">Many of the elements in the response message are populated using the values from the request message.</span></span> <span data-ttu-id="c0426-107">因此，您可以在回應者私用程序協調流程中整合出一套對應方式，幫助 LOB 程式以所需的格式產生回應服務內容訊息。</span><span class="sxs-lookup"><span data-stu-id="c0426-107">As a result, you can incorporate a map in the responder private-process orchestration to help the LOB program generate the response service-content message in the required format.</span></span>  
  
 <span data-ttu-id="c0426-108">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含下列範例，讓您可以在將對應加入回應者私用程序時加以使用：</span><span class="sxs-lookup"><span data-stu-id="c0426-108">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK contains the following samples that you can use when you add a map to a responder private-process:</span></span>  
  
-   [<span data-ttu-id="c0426-109">3A2 要求至 3A2 回應的對應範例</span><span class="sxs-lookup"><span data-stu-id="c0426-109">3A2 Request to 3A2 Response Map Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)  
  
-   [<span data-ttu-id="c0426-110">3A4 要求至 3A4 回應的對應範例</span><span class="sxs-lookup"><span data-stu-id="c0426-110">3A4 Request to 3A4 Response Map Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)  
  
-   [<span data-ttu-id="c0426-111">Double 動作 PIPAutomation 協調流程</span><span class="sxs-lookup"><span data-stu-id="c0426-111">Double Action PIPAutomation Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)  
  
-   [<span data-ttu-id="c0426-112">使用商務規則的 3A4 私用回應者協調流程</span><span class="sxs-lookup"><span data-stu-id="c0426-112">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)  
  
### <a name="to-create-the-map"></a><span data-ttu-id="c0426-113">若要建立對應</span><span class="sxs-lookup"><span data-stu-id="c0426-113">To create the map</span></span>  
  
1.  <span data-ttu-id="c0426-114">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="c0426-114">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="c0426-115">在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="c0426-115">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="c0426-116">找到含有 BizTalk 專案的資料夾，這個資料夾需包含要將對應加入至其中的私用程序協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0426-116">Locate the folder that contains the BizTalk project that contains the private-process orchestration to which you want to add the map.</span></span>  
  
4.  <span data-ttu-id="c0426-117">在方案總管中，以滑鼠右鍵按一下專案，指向 [加入]，然後按一下 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="c0426-117">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
5.  <span data-ttu-id="c0426-118">在 [加入新項目] 視窗中**類別**] 窗格中，按一下 [**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="c0426-118">In the Add New Item window, in the **Categories** pane, click **Map Files**.</span></span> <span data-ttu-id="c0426-119">在 [範本] 窗格中，按一下**對應**。</span><span class="sxs-lookup"><span data-stu-id="c0426-119">In the Templates pane, click **Map**.</span></span> <span data-ttu-id="c0426-120">在**名稱**方塊、 輸入對應的名稱，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="c0426-120">In the **Name** box, type a name for the map, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="c0426-121">在 [來源結構描述] 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="c0426-121">In the Source Schema pane, click **Open Source Schema**.</span></span>  
  
7.  <span data-ttu-id="c0426-122">在 BizTalk 型別選擇器 視窗中，依序展開**結構描述**，選取您想要從，對應，然後按一下 要求訊息的 PIP 結構描述**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0426-122">In the BizTalk Type Picker window, expand **Schemas**, select the PIP schema for the request message that you want to map from, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c0426-123">在 [目的結構描述] 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="c0426-123">In the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
9. <span data-ttu-id="c0426-124">在 [BizTalk 型別選擇器] 視窗中，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，依序展開**結構描述**，選取的 PIP 結構描述您想要對應，然後按一下的回應訊息**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0426-124">In the BizTalk Type Picker window, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, expand **Schemas**, select the PIP schema for the response message to which you want to map, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="c0426-125">以滑鼠右鍵按一下\<*結構描述*> 節點來源結構描述，然後再按一下**展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="c0426-125">Right-click the \<*Schema*> node of the source schema, and then click **Expand Tree Node**.</span></span>  
  
11. <span data-ttu-id="c0426-126">重複步驟 10，完成目的結構描述的部分。</span><span class="sxs-lookup"><span data-stu-id="c0426-126">Repeat step 10 for the destination schema.</span></span>  
  
12. <span data-ttu-id="c0426-127">在 [來源結構描述] 窗格中，在您要與目的結構描述之欄位進行對應的欄位上按住不放。</span><span class="sxs-lookup"><span data-stu-id="c0426-127">In the Source Schema pane, click and hold on a field that you want to map to a field in the destination schema.</span></span> <span data-ttu-id="c0426-128">然後將該欄位拖曳至 [目的結構描述] 窗格中對應的節點。</span><span class="sxs-lookup"><span data-stu-id="c0426-128">Drag to the corresponding node in the Destination Schema pane.</span></span>  
  
13. <span data-ttu-id="c0426-129">重複步驟 12，將全部您要進行對應的欄位完成對應的動作。</span><span class="sxs-lookup"><span data-stu-id="c0426-129">Repeat step 12 for all fields that you have to map between the two schemas.</span></span>  
  
14. <span data-ttu-id="c0426-130">驗證並測試對應。</span><span class="sxs-lookup"><span data-stu-id="c0426-130">Validate and test the map.</span></span> <span data-ttu-id="c0426-131">如需詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜編譯與測試對應＞主題。</span><span class="sxs-lookup"><span data-stu-id="c0426-131">For more information, see the "Compiling and Testing Maps" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
### <a name="to-add-the-map-to-the-orchestration"></a><span data-ttu-id="c0426-132">將對應加入協調流程</span><span class="sxs-lookup"><span data-stu-id="c0426-132">To add the map to the orchestration</span></span>  
  
1.  <span data-ttu-id="c0426-133">在 [方案總管] 中，按兩下私用程序協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0426-133">In Solution Explorer, double-click the private-process orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0426-134">請確認協調流程含有包括這個結構描述之組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c0426-134">Make sure that the orchestration has references to the assemblies that contain the schemas.</span></span>  
  
2.  <span data-ttu-id="c0426-135">在工具箱中，按一下 **轉換**圖形，並將它拖曳至協調流程，您不必將要求訊息轉換成回應訊息中的點。</span><span class="sxs-lookup"><span data-stu-id="c0426-135">In the Toolbox, click the **Transform** shape, and drag it to the point in the orchestration at which you have to transform the request message into the response message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0426-136">如需範例的位置的**轉換**圖形，請參閱 PIP3A4PrivateResponder.odx 協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0426-136">For an example of the placement of the **Transform** shape, see the PIP3A4PrivateResponder.odx orchestration.</span></span> <span data-ttu-id="c0426-137">它位於\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR。</span><span class="sxs-lookup"><span data-stu-id="c0426-137">It is located in \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span></span> <span data-ttu-id="c0426-138">這個範例會將放**轉換**立即圖形下**IsActivityDoubleAction**圖形。</span><span class="sxs-lookup"><span data-stu-id="c0426-138">This sample puts the **Transform** shape immediately under the **IsActivityDoubleAction** shape.</span></span> <span data-ttu-id="c0426-139">如需詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。</span><span class="sxs-lookup"><span data-stu-id="c0426-139">For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0426-140">如需如何將多個對應合併多個 Pip 的範例，請參閱[雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="c0426-140">For an example of how you can incorporate multiple maps for multiple PIPs, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span></span>  
  
3.  <span data-ttu-id="c0426-141">協調流程設計介面上，按一下  **ConstructMessage1**。</span><span class="sxs-lookup"><span data-stu-id="c0426-141">On the orchestration design surface, click **ConstructMessage1**.</span></span> <span data-ttu-id="c0426-142">在 [屬性] 視窗中，輸入這個圖形的名稱，以及所要建構的訊息名稱。</span><span class="sxs-lookup"><span data-stu-id="c0426-142">In the Properties window, type a name for the shape, and a name for the message to be constructed.</span></span>  
  
4.  <span data-ttu-id="c0426-143">協調流程設計介面上，按一下 **轉換**。</span><span class="sxs-lookup"><span data-stu-id="c0426-143">On the orchestration design surface, click **Transform**.</span></span> <span data-ttu-id="c0426-144">在 屬性 視窗中，按一下 省略符號按鈕 (**...**) 旁邊**對應名稱**。</span><span class="sxs-lookup"><span data-stu-id="c0426-144">In the Properties window, click the ellipsis button (**...**) next to **Map Name**.</span></span>  
  
5.  <span data-ttu-id="c0426-145">在 轉換組態 視窗中，按一下 **現有對應**，然後在**完整格式對應名稱**，按一下您剛才建立的對應。</span><span class="sxs-lookup"><span data-stu-id="c0426-145">In the Transform Configuration window, click **Existing Map**, and in **Fully Qualified Map Name**, click the map that you just created.</span></span>  
  
6.  <span data-ttu-id="c0426-146">在下**轉換**，按一下 **來源**。</span><span class="sxs-lookup"><span data-stu-id="c0426-146">Under **Transform**, click **Source**.</span></span> <span data-ttu-id="c0426-147">按一下變數下方的空白方塊，並從下拉式清單中選取要求訊息的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0426-147">Click the empty box under variable, and select the name of the request message from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="c0426-148">在下**轉換**，按一下 **目的地**。</span><span class="sxs-lookup"><span data-stu-id="c0426-148">Under **Transform**, click **Destination**.</span></span> <span data-ttu-id="c0426-149">按一下變數下方的空白方塊，並從下拉式清單中選取回應訊息的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0426-149">Click the empty box under variable, and select the name of the response message from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="c0426-150">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c0426-150">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0426-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0426-151">See Also</span></span>  
 [<span data-ttu-id="c0426-152">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c0426-152">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)