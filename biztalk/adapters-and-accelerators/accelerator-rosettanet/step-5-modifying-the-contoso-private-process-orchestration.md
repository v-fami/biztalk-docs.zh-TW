---
title: 步驟 5： 修改 Contoso 私用程序協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private processes, orchestrations
- private process tutorial, modifying private process orchestration
ms.assetid: a5430db8-e5f0-48a6-abb9-e268d8ec2ec4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a222ee518cf0555de60094411df73bf5a5d486a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967756"
---
# <a name="step-5-modifying-the-contoso-private-process-orchestration"></a><span data-ttu-id="c3ad9-102">步驟 5： 修改 Contoso 私用程序協調流程</span><span class="sxs-lookup"><span data-stu-id="c3ad9-102">Step 5: Modifying the Contoso Private Process Orchestration</span></span>
<span data-ttu-id="c3ad9-103">在此步驟中，您將修改私用程序協調流程，以便與 Contoso 的「企業資源規劃」(Enterprise Resource Planning，ERP) 系統進行整合。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-103">In this step, you modify the private process orchestration to integrate with the Enterprise Resource Planning (ERP) system for Contoso.</span></span> <span data-ttu-id="c3ad9-104">Contoso 的 ERP 系統使用內部定義的產品價格與可用性結構描述。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-104">The ERP system for Contoso uses internally defined schemas for product price and availability.</span></span> <span data-ttu-id="c3ad9-105">自訂「3A2 - 價格與可用性交易夥伴介面程序 (PIP)」的私用程序之後，您就能夠使用結構描述對應資訊與 ERP 系統進行整合。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-105">By customizing the private process for the 3A2 - Price and Availability Partner Interface Process (PIP), you will be able to integrate with the ERP system by using schema-mapping information.</span></span>  
  
### <a name="to-add-a-reference-to-the-contoso-priceandavailability-and-rnpips-assemblies"></a><span data-ttu-id="c3ad9-106">加入 Contoso PriceAndAvailability 及 RNPIPs 組件的參考</span><span class="sxs-lookup"><span data-stu-id="c3ad9-106">To add a reference to the Contoso PriceAndAvailability and RNPIPs assemblies</span></span>  
  
1.  <span data-ttu-id="c3ad9-107">Contoso 方案顯示在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-107">With the Contoso solution displayed in Solution Explorer, right-click the **PrivateResponder** project, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="c3ad9-108">在 [加入參考] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-108">In the Add Reference dialog box, click **Browse**.</span></span> <span data-ttu-id="c3ad9-109">移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin 資料夾，然後再選取下列組件 **:**</span><span class="sxs-lookup"><span data-stu-id="c3ad9-109">Move to *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin folder, and then select the following assemblies **:**</span></span>  
  
    -   <span data-ttu-id="c3ad9-110">Microsoft.Solutions.BTARN.CommonTypes.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-110">Microsoft.Solutions.BTARN.CommonTypes.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-111">Microsoft.Solutions.BTARN.ConfigurationManager.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-111">Microsoft.Solutions.BTARN.ConfigurationManager.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-112">Microsoft.Solutions.BTARN.GlobalSchemas.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-112">Microsoft.Solutions.BTARN.GlobalSchemas.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-113">Microsoft.Solutions.BTARN.PublicResponder.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-113">Microsoft.Solutions.BTARN.PublicResponder.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-114">Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-114">Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-115">Microsoft.Solutions.BTARN.Shared.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-115">Microsoft.Solutions.BTARN.Shared.dll</span></span>  
  
    -   <span data-ttu-id="c3ad9-116">Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll</span><span class="sxs-lookup"><span data-stu-id="c3ad9-116">Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll</span></span>  
  
3.  <span data-ttu-id="c3ad9-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-117">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="c3ad9-118">在 [加入參考] 對話方塊中，按一下**專案**索引標籤上，選取**ContosoPriceAndAvailability**和**HeaderHelper**專案，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-118">In the Add Reference dialog box, click the **Projects** tab, select the **ContosoPriceAndAvailability** and **HeaderHelper** projects, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="c3ad9-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-119">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c3ad9-120">在 Microsoft 開發環境] 對話方塊中，按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-120">In the Microsoft Development Environment dialog box, click **OK**.</span></span>  
  
### <a name="to-create-new-message-types"></a><span data-ttu-id="c3ad9-121">建立新訊息類型</span><span class="sxs-lookup"><span data-stu-id="c3ad9-121">To create new message types</span></span>  
  
1.  <span data-ttu-id="c3ad9-122">在 [方案總管] 中，按兩下**PrivateResponder**協調流程加以開啟。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-122">In Solution Explorer, double-click the **PrivateResponder** orchestration to open it.</span></span>  
  
2.  <span data-ttu-id="c3ad9-123">在 方案總管 中，按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-123">In Solution Explorer, click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="c3ad9-124">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-124">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="c3ad9-125">在 [屬性] 視窗中**識別碼**方塊中，輸入**PIP3A2RequestMessage**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-125">In the Properties window, in the **Identifier** box, type **PIP3A2RequestMessage**.</span></span>  
  
5.  <span data-ttu-id="c3ad9-126">在**訊息類型**方塊中，按一下下拉箭號，展開 **結構描述**，然後選取**\<從參考組件選取\>**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-126">In the **Message Type** box, click the drop-down arrow, expand **Schemas**, and then select **\<Select from referenced assembly\>**.</span></span>  
  
6.  <span data-ttu-id="c3ad9-127">在 選取成品 Typedialog 方塊中，選取  **Microsoft.Solutions.BTARN.Schemas.RNPIPs**在左窗格中，選取 **_3a2priceandavailabilityquerymessageguideline_v1_3**在右窗格中，並然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-127">In the Select Artifact Typedialog box, select **Microsoft.Solutions.BTARN.Schemas.RNPIPs** in the left pane, select **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3** in the right pane, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="c3ad9-128">重複執行步驟 3 至 6，使用下列資訊建立方案的所有訊息類型：</span><span class="sxs-lookup"><span data-stu-id="c3ad9-128">Repeat steps 3 through 6 to create all the message types for the solution using the following information:</span></span>  
  
    |<span data-ttu-id="c3ad9-129">識別碼</span><span class="sxs-lookup"><span data-stu-id="c3ad9-129">Identifier</span></span>|<span data-ttu-id="c3ad9-130">組件</span><span class="sxs-lookup"><span data-stu-id="c3ad9-130">Assembly</span></span>|<span data-ttu-id="c3ad9-131">訊息類型</span><span class="sxs-lookup"><span data-stu-id="c3ad9-131">Message Type</span></span>|  
    |----------------|--------------|------------------|  
    |<span data-ttu-id="c3ad9-132">PIP3A2ResponseMessage</span><span class="sxs-lookup"><span data-stu-id="c3ad9-132">PIP3A2ResponseMessage</span></span>|<span data-ttu-id="c3ad9-133">Microsoft.Solutions.BTARN。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-133">Microsoft.Solutions.BTARN.</span></span><br /><span data-ttu-id="c3ad9-134">Schemas.RNPips</span><span class="sxs-lookup"><span data-stu-id="c3ad9-134">Schemas.RNPips</span></span>|<span data-ttu-id="c3ad9-135">_3A2PriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="c3ad9-135">_3A2PriceAndAvailability</span></span><br /><span data-ttu-id="c3ad9-136">ResponseMessageGuideline_v1_3</span><span class="sxs-lookup"><span data-stu-id="c3ad9-136">ResponseMessageGuideline_v1_3</span></span>|  
    |<span data-ttu-id="c3ad9-137">Contoso3A2ResponseMessage</span><span class="sxs-lookup"><span data-stu-id="c3ad9-137">Contoso3A2ResponseMessage</span></span>|<span data-ttu-id="c3ad9-138">ContosoPriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="c3ad9-138">ContosoPriceAndAvailability</span></span>|<span data-ttu-id="c3ad9-139">rootPriceResponse</span><span class="sxs-lookup"><span data-stu-id="c3ad9-139">rootPriceResponse</span></span>|  
    |<span data-ttu-id="c3ad9-140">Contoso3A2RequestMessage</span><span class="sxs-lookup"><span data-stu-id="c3ad9-140">Contoso3A2RequestMessage</span></span>|<span data-ttu-id="c3ad9-141">ContosoPriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="c3ad9-141">ContosoPriceAndAvailability</span></span>|<span data-ttu-id="c3ad9-142">rootPriceRequest</span><span class="sxs-lookup"><span data-stu-id="c3ad9-142">rootPriceRequest</span></span>|  
  
8.  <span data-ttu-id="c3ad9-143">您已經完成建立方案的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-143">You have finished creating the message types for the solution.</span></span>  
  
### <a name="to-create-new-variables"></a><span data-ttu-id="c3ad9-144">建立新變數</span><span class="sxs-lookup"><span data-stu-id="c3ad9-144">To create new variables</span></span>  
  
1.  <span data-ttu-id="c3ad9-145">在協調流程檢視中，以滑鼠右鍵按一下**變數**，然後按一下 **新變數**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-145">In Orchestration View, right-click **Variables,** and then click **New Variable**.</span></span>  
  
2.  <span data-ttu-id="c3ad9-146">在 [屬性] 視窗中**識別碼**方塊中，輸入**contosoResponseXML**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-146">In the Properties window, in the **Identifier** box, type **contosoResponseXML**.</span></span>  
  
3.  <span data-ttu-id="c3ad9-147">在**類型**方塊中，選取 **\<.NET 類別\>** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-147">In the **Type** box, select **\<.NET Class\>** from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="c3ad9-148">在 [選取成品類型] 對話方塊，在左窗格中，在**目前專案**和**參考**節點下，選取**System.Xml**，選取**XmlDocument**從清單中的右窗格中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-148">In the Select Artifact Type dialog box, in the left pane, under the **Current Project** and **References** nodes, select **System.Xml**, select **XmlDocument** from the list in the right pane, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c3ad9-149">在**協調流程檢視**，按一下 **變數**，然後按一下 **新變數**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-149">In **Orchestration View**, click **Variables**,and then click **New Variable**.</span></span>  
  
6.  <span data-ttu-id="c3ad9-150">在 [屬性] 視窗中**識別碼**方塊中，輸入**submitMessage**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-150">In the Properties window, in the **Identifier** box, type **submitMessage**.</span></span>  
  
7.  <span data-ttu-id="c3ad9-151">在**類型**方塊中，選取 **\<.NET 類別\>** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-151">In the **Type** box, select **\<.NET Class\>** from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="c3ad9-152">在 [選取成品類型] 對話方塊的左窗格中，展開**目前專案**和**參考**節點下，選取**Microsoft.Solutions.BTARN.Shared**，選取**SubmitRNIF**從清單中的右窗格中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-152">In the Select Artifact Type dialog box, in the left pane, expand **Current Project** and **References** nodes, select **Microsoft.Solutions.BTARN.Shared**, select **SubmitRNIF** from the list in the right pane, and then click **OK**.</span></span>  
  
### <a name="to-change-the-orchestration-filter-expression"></a><span data-ttu-id="c3ad9-153">變更協調流程的篩選條件運算式</span><span class="sxs-lookup"><span data-stu-id="c3ad9-153">To change the orchestration filter expression</span></span>  
  
1.  <span data-ttu-id="c3ad9-154">在協調流程設計師中，選取**ReceiveFromPublicProcessResponder**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-154">In Orchestration Designer, select the **ReceiveFromPublicProcessResponder** shape.</span></span>  
  
2.  <span data-ttu-id="c3ad9-155">在 屬性 視窗中**篩選條件運算式**方塊中，按一下 值 方塊中，然後按一下 省略符號按鈕 (**...**) 若要開啟 篩選運算式 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-155">In the Properties window, in the **Filter Expression** box, click the value box, and then click the ellipsis button (**...**) to open the Filter Expression dialog box.</span></span>  
  
3.  <span data-ttu-id="c3ad9-156">在 篩選運算式 對話方塊中**Group By**區段中，按一下**或者**值在第一行，然後選取  **AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-156">In the Filter Expression dialog box, in the **Group By** section, click the **OR** value on the first line, and then select **AND** from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="c3ad9-157">在 [篩選運算式] 對話方塊中，按一下**按一下此處以加入新的資料列**，然後選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-157">In the Filter Expression dialog box, click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="c3ad9-158">在相同的資料列中，按一下**值**，然後鍵入 **"3A2"**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-158">In the same row, click **Value**, and then type in **"3A2"**.</span></span>  
  
6.  <span data-ttu-id="c3ad9-159">在相同的資料列中，按一下**AND**中**Group By**方塊，並選取**或**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-159">In the same row, click **AND** in the **Group By** box, and then select **OR** from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="c3ad9-160">在 [篩選條件運算式] 對話方塊中，選取剛才建立的那一列，然後按一下向上箭號按鈕，將該列上移一列。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-160">In the Filter Expression dialog box, select the row that you just created, and then click the up arrow button once to move the row up once.</span></span>  
  
8.  <span data-ttu-id="c3ad9-161">按一下**按一下此處以加入新的資料列**，然後選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-161">Click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="c3ad9-162">在相同的資料列中，按一下**值**，然後鍵入 **"3A2"**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-162">In the same row, click **Value**, and then type in **"3A2"**.</span></span>  
  
10. <span data-ttu-id="c3ad9-163">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-163">Click OK.</span></span>  
  
### <a name="to-modify-the-business-process-workflow"></a><span data-ttu-id="c3ad9-164">修改商務程序工作流程</span><span class="sxs-lookup"><span data-stu-id="c3ad9-164">To modify the business process workflow</span></span>  
  
1.  <span data-ttu-id="c3ad9-165">拖曳**訊息指派**圖形從工具箱拖曳至設計介面，然後放在**ReceiveFromPublicProcessResponder**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-165">Drag a **Message Assignment** shape from the Toolbox to the design surface and drop it under the **ReceiveFromPublicProcessResponder** shape.</span></span> <span data-ttu-id="c3ad9-166">選取 **[constructmessage_1]** 所建立的圖形和**屬性**視窗，請在**名稱**方塊中，輸入**ConstructPIP3A2RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-166">Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructPIP3A2RequestMessage**.</span></span>  
  
2.  <span data-ttu-id="c3ad9-167">拖曳**轉換**圖形至設計介面，然後放在**ConstructPIP3A2RequestMessage**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-167">Drag a **Transform** shape to the design surface and drop it under the **ConstructPIP3A2RequestMessage** shape.</span></span> <span data-ttu-id="c3ad9-168">選取 **[constructmessage_1]** 所建立的圖形和**屬性**視窗，請在**名稱**方塊中，輸入**ConstructContoso3A2RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-168">Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructContoso3A2RequestMessage**.</span></span>  
  
3.  <span data-ttu-id="c3ad9-169">拖曳**傳送**圖形至設計介面，然後放在**ConstructContoso3A2RequestMessage**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-169">Drag a **Send** shape to the design surface and drop it under the **ConstructContoso3A2RequestMessage** shape.</span></span>  
  
4.  <span data-ttu-id="c3ad9-170">拖曳**接收**圖形至設計介面，然後放在 **[send_1]** 圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-170">Drag a **Receive** shape to the design surface and drop it under the **Send_1** shape.</span></span>  
  
5.  <span data-ttu-id="c3ad9-171">按一下協調流程設計介面的空白區域。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-171">On the orchestration design surface, click an empty area.</span></span>  
  
6.  <span data-ttu-id="c3ad9-172">在 [屬性] 視窗中，選取**交易類型**屬性，，然後按一下**長時間執行**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-172">In the Properties window, select the **Transaction Type** property, and then click **Long Running**.</span></span>  
  
7.  <span data-ttu-id="c3ad9-173">拖曳**範圍**圖形至設計介面，然後放在**Receive_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-173">Drag a **Scope** shape to the design surface and drop it under the **Receive_1** shape.</span></span>  
  
8.  <span data-ttu-id="c3ad9-174">在 [屬性] 視窗中，從**交易類型**屬性下拉式清單中，選取**不可部分完成**如**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-174">In the Properties window, from the **Transaction Type** property drop-down list, select **Atomic** for the **Scope** shape.</span></span>  
  
9. <span data-ttu-id="c3ad9-175">拖曳**呼叫規則**圖形至設計介面並將它放的標籤上，該處會指示**從 [工具箱] 拖曳圖形**內**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-175">Drag a **Call Rules** shape to the design surface and drop it on the label that says **Drop a shape from the toolbox here** inside the **Scope** shape.</span></span> <span data-ttu-id="c3ad9-176">在 [屬性] 視窗中**呼叫規則**圖形，在**名稱**方塊中，輸入**Execute3A2Vocabulary**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-176">In the Properties window for the **Call Rules** shape, in the **Name** box, type **Execute3A2Vocabulary**.</span></span>  
  
10. <span data-ttu-id="c3ad9-177">拖曳**轉換**圖形至設計介面，然後放在**Scope_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-177">Drag a **Transform** shape to the design surface and drop it under the **Scope_1** shape.</span></span> <span data-ttu-id="c3ad9-178">按一下 **[constructmessage_1]** 圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-178">Click the **ConstructMessage_1** shape.</span></span> <span data-ttu-id="c3ad9-179">在 [屬性] 視窗中**名稱**方塊中，輸入**Construct3A2ResponseMessage**。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-179">In the Properties window, in the **Name** box, type **Construct3A2ResponseMessage**.</span></span>  
  
11. <span data-ttu-id="c3ad9-180">拖曳**運算式**圖形至設計介面，然後放在**Construct3A2ResponseMessageTransform**圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-180">Drag an **Expression** shape to the design surface and drop it under the **Construct3A2ResponseMessageTransform** shape.</span></span>  
  
12. <span data-ttu-id="c3ad9-181">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**，按一下 **全部儲存**儲存專案。</span><span class="sxs-lookup"><span data-stu-id="c3ad9-181">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File**, click **Save All** to save the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ad9-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ad9-182">See Also</span></span>  
 [<span data-ttu-id="c3ad9-183">步驟 6：設定協調流程圖形 (Contoso)</span><span class="sxs-lookup"><span data-stu-id="c3ad9-183">Step 6: Configuring Orchestration Shapes (Contoso)</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)