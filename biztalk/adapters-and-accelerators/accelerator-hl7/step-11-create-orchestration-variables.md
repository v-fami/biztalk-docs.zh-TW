---
title: 步驟 11： 建立協調流程變數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
- message enrichment tutorial, orchestrations
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfe49f533989e339e6eb4318460a444ed0d8b741
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991159"
---
# <a name="step-11-create-orchestration-variables"></a><span data-ttu-id="49487-102">步驟 11： 建立協調流程變數</span><span class="sxs-lookup"><span data-stu-id="49487-102">Step 11: Create Orchestration Variables</span></span>
<span data-ttu-id="49487-103">在此步驟中，您會建立訊息執行個體傳送和接收的協調流程的協調流程變數。</span><span class="sxs-lookup"><span data-stu-id="49487-103">In this step, you create the orchestration variables for the message instances sent and received by the orchestration.</span></span>  
  
 <span data-ttu-id="49487-104">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 序列化程式需要下列部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="49487-104">The BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) serializer expects the following part names.</span></span> <span data-ttu-id="49487-105">如果您建立多部分訊息與任何其他組件名稱時，序列化程式會拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="49487-105">If you create a multipart message with any other part names, the serializer rejects the message.</span></span> <span data-ttu-id="49487-106">訊息部分的名稱是：</span><span class="sxs-lookup"><span data-stu-id="49487-106">The message part names are:</span></span>  
  
- <span data-ttu-id="49487-107">MSHSegment</span><span class="sxs-lookup"><span data-stu-id="49487-107">MSHSegment</span></span>  
  
- <span data-ttu-id="49487-108">BodySegments</span><span class="sxs-lookup"><span data-stu-id="49487-108">BodySegments</span></span>  
  
- <span data-ttu-id="49487-109">Z 區段</span><span class="sxs-lookup"><span data-stu-id="49487-109">Z segments</span></span>  
  
  <span data-ttu-id="49487-110">以下是有關 Z 區段組件的重要資訊：</span><span class="sxs-lookup"><span data-stu-id="49487-110">The following is important information about Z segment parts:</span></span>  
  
- <span data-ttu-id="49487-111">上面所述，不論 Z 區段是否存在，所有的訊息會包含三個部分。</span><span class="sxs-lookup"><span data-stu-id="49487-111">All messages contain three parts as described above, regardless of whether a Z segment is present or not.</span></span>  
  
- <span data-ttu-id="49487-112">您可以使用 Z 區段組件，包含訊息執行個體，它是句尾且未定義 （這也表示它未宣告） 的結構描述中的資料。</span><span class="sxs-lookup"><span data-stu-id="49487-112">You use a Z segment part to contain data from the message instance, which is trailing and not defined in the schema (which also means that it is undeclared).</span></span>  
  
- <span data-ttu-id="49487-113">如果沒有任何未宣告的資料，是空白的 Z 區段組件。</span><span class="sxs-lookup"><span data-stu-id="49487-113">If there is no undeclared data, the Z segment part is blank.</span></span> <span data-ttu-id="49487-114">您看不見的 Z 區段部分檢視的中繼 XML 內 BizTalk 對應工具; 時不過，在 BizTalk 狀況與活動追蹤 (HAT) 工具中，您會看到每個訊息的三個部分。</span><span class="sxs-lookup"><span data-stu-id="49487-114">You do not see the Z segment parts when viewing the intermediate XML within BizTalk Mapper; however, in the BizTalk Health and Activity Tracking (HAT) tool, you see three parts to each message.</span></span>  
  
### <a name="to-create-orchestration-variables"></a><span data-ttu-id="49487-115">若要建立協調流程變數</span><span class="sxs-lookup"><span data-stu-id="49487-115">To create orchestration variables</span></span>  
  
1. <span data-ttu-id="49487-116">按一下 [**協調流程檢視**索引標籤旁**方案總管] 中**下方 [方案總管] 中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="49487-116">Click the **Orchestration View** tab next to the **Solution Explorer** tab beneath the Solutions Explorer.</span></span>  
  
2. <span data-ttu-id="49487-117">在 **協調流程檢視** 窗格中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="49487-117">In the **Orchestration View** pane, right-click **Messages**, and then click **New Message**.</span></span>  
  
3. <span data-ttu-id="49487-118">變更**識別碼**中的屬性**屬性**窗格，即可**DoorbellInputMessage**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-118">Change the **Identifier** property in the **Properties** pane to **DoorbellInputMessage**, and then press **Enter**.</span></span>  
  
4. <span data-ttu-id="49487-119">在 **屬性** 窗格的下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**。</span><span class="sxs-lookup"><span data-stu-id="49487-119">In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.</span></span>  
  
5. <span data-ttu-id="49487-120">重複步驟 2 和 3 來建立名為另一則訊息**DoorbellOutputMessage**。</span><span class="sxs-lookup"><span data-stu-id="49487-120">Repeat steps 2 and 3 to create another message named **DoorbellOutputMessage**.</span></span>  
  
6. <span data-ttu-id="49487-121">在 **屬性** 窗格的下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="49487-121">In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.</span></span>  
  
7. <span data-ttu-id="49487-122">在 **協調流程檢視**窗格中，展開**型別**節點。</span><span class="sxs-lookup"><span data-stu-id="49487-122">In the **Orchestration View** pane, expand the **Types** node.</span></span> <span data-ttu-id="49487-123">以滑鼠右鍵按一下**多部分訊息類型**，然後按一下**新的多部分訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="49487-123">Right-click **Multi-part Message Types**, and then click **New Multi-part Message Type**.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="49487-124"> 建立新的訊息類型，名為**MultipartType_1**以及名為的新訊息**MessagePart_1**。</span><span class="sxs-lookup"><span data-stu-id="49487-124"> creates a new message type named **MultipartType_1** along with a new message named **MessagePart_1**.</span></span>  
  
8. <span data-ttu-id="49487-125">按一下  **MultipartType_1**，然後在**屬性**視窗中，按一下 **識別碼**，輸入新名稱**DoorbellFinalMessageType**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-125">Click **MultipartType_1**, and in the **Properties** window, click **Identifier** and type the new name **DoorbellFinalMessageType**, and then press **Enter**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="49487-126">在步驟 9 至 15 中，您將建立多部分訊息的部分。</span><span class="sxs-lookup"><span data-stu-id="49487-126">In steps 9 through 15, you will create the parts of the multipart message.</span></span> <span data-ttu-id="49487-127">您可以在其中建立多部分訊息的部分順序很重要。</span><span class="sxs-lookup"><span data-stu-id="49487-127">The order in which you create the parts of a multipart message is important.</span></span> <span data-ttu-id="49487-128">一律會建立標頭，則主體中，則 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="49487-128">Always create the header, then the body, then the Z segment.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="49487-129">一旦您已建立並命名為訊息部分，請勿重新命名它們。</span><span class="sxs-lookup"><span data-stu-id="49487-129">Once you have created and named the message parts, do not rename them.</span></span> <span data-ttu-id="49487-130">如有需要，刪除舊的內文部分，並使用新的名稱建立新的內文部分。</span><span class="sxs-lookup"><span data-stu-id="49487-130">If necessary, delete the old body part, and create a new body part with a new name.</span></span>  
  
9. <span data-ttu-id="49487-131">中**型別** 視窗底下**多部分訊息類型**，展開**DoorbellFinalMessageType**，然後按一下**MessagePart_1**。</span><span class="sxs-lookup"><span data-stu-id="49487-131">In the **Types** window, under **Multi-part Message Types**, expand **DoorbellFinalMessageType**, and then click **MessagePart_1**.</span></span> <span data-ttu-id="49487-132">在 [**屬性**] 窗格中，輸入**MSHSegment**的**識別碼**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-132">In the **Properties** pane, enter **MSHSegment** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="49487-133">中的下拉式清單**型別**，展開 **.NET 類別**，然後按一下\<**從參考組件中選取\>**。</span><span class="sxs-lookup"><span data-stu-id="49487-133">In the drop-down list for **Type**, expand **.NET Classes**, and then click \<**Select from referenced assemblies\>**.</span></span>  
  
10. <span data-ttu-id="49487-134">在 **選取成品類型**對話方塊中，在左窗格中，按一下**System.Xml**。</span><span class="sxs-lookup"><span data-stu-id="49487-134">In the **Select Artifact Type** dialog box, in the left pane, click **System.Xml**.</span></span> <span data-ttu-id="49487-135">在右窗格中，按一下**XmlDocument**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="49487-135">In the right pane, click **XmlDocument**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="49487-136">在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下**新訊息部分**建立 MessagePart_1。</span><span class="sxs-lookup"><span data-stu-id="49487-136">In the Orchestration View window, right-click **DoorbellFinalMessageType**, and then click **New Message Part** to create MessagePart_1.</span></span>  
  
12. <span data-ttu-id="49487-137">在 [**屬性**] 視窗中，輸入**BodySegments**的**識別碼**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-137">In the **Properties** window, enter **BodySegments** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="49487-138">中的下拉式清單**型別**，展開**結構描述**，然後選取**BTAHL7Schemas.ADT_A04_22_GLO_DEF**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="49487-138">In the drop-down list for **Type**, expand **Schemas**, and then select **BTAHL7Schemas.ADT_A04_22_GLO_DEF** from the drop-down list.</span></span>  
  
13. <span data-ttu-id="49487-139">設定**訊息內文部分**屬性設 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="49487-139">Set the **Message Body Part** property to **True**.</span></span>  
  
14. <span data-ttu-id="49487-140">在 [**協調流程檢視**] 視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下**新訊息部分**。</span><span class="sxs-lookup"><span data-stu-id="49487-140">In the **Orchestration View** window, right-click **DoorbellFinalMessageType**, and then click **New Message Part**.</span></span>  
  
15. <span data-ttu-id="49487-141">在 [**屬性**] 窗格中，輸入**ZSegments**的**識別碼**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-141">In the **Properties** pane, enter **ZSegments** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="49487-142">按一下 **型別**，展開 **.NET 類別**，然後按一下**System.String**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="49487-142">Click **Type**, expand **.NET Classes**, and then click **System.String** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49487-143">您使用**System.String** Z 區段的訊息部分，因為 Z 區段包含不需要符合結構描述的字串資料。</span><span class="sxs-lookup"><span data-stu-id="49487-143">You use **System.String** for the Z segments message part, because a Z segment contains string data that does not need to conform to a schema.</span></span>  
  
16. <span data-ttu-id="49487-144">在 **協調流程檢視** 視窗中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="49487-144">In the **Orchestration View** window, right-click **Messages**, and then click **New Message**.</span></span>  
  
17. <span data-ttu-id="49487-145">在 [**屬性**] 視窗中，輸入**DoorbellFinalMessage**的**識別碼**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-145">In the **Properties** window, enter **DoorbellFinalMessage** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="49487-146">中的下拉式清單**訊息類型**，展開**多部分訊息類型**，然後按一下**BTAHL7_Project.DoorbellFinalMessageType**。</span><span class="sxs-lookup"><span data-stu-id="49487-146">In the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.</span></span>  
  
18. <span data-ttu-id="49487-147">在 **協調流程檢視** 視窗中，以滑鼠右鍵按一下**變數**，然後按一下 **新變數**。</span><span class="sxs-lookup"><span data-stu-id="49487-147">In the **Orchestration View** window, right-click **Variables**, and then click **New Variable**.</span></span>  
  
19. <span data-ttu-id="49487-148">在 **屬性**窗格中，輸入**HeaderInfo**的**識別碼**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="49487-148">In the **Properties** pane, enter **HeaderInfo** for **Identifier**, then press **Enter**.</span></span> <span data-ttu-id="49487-149">中的下拉式清單**型別**，按兩下\< **.NET 類別\>**。</span><span class="sxs-lookup"><span data-stu-id="49487-149">In the drop-down list for **Type**, double-click \<**.NET Class\>**.</span></span>  
  
20. <span data-ttu-id="49487-150">在 **選取成品類型**視窗中的，在左窗格中，按一下**System.Xml**。</span><span class="sxs-lookup"><span data-stu-id="49487-150">In the **Select Artifact Type** window, in the left pane, click **System.Xml**.</span></span> <span data-ttu-id="49487-151">在右窗格中，按一下**XmlDocument**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="49487-151">In the right pane, click **XmlDocument**, and then click **OK**.</span></span>  
  
21. <span data-ttu-id="49487-152">在 **檔案**功能表上，按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="49487-152">In the **File** menu, click **Save All**.</span></span>  
  
    <span data-ttu-id="49487-153">請繼續進行[步驟 12： 設定協調流程圖形](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="49487-153">Proceed to [Step 12: Configure Orchestration Shapes](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49487-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49487-154">See Also</span></span>  
 [<span data-ttu-id="49487-155">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="49487-155">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)