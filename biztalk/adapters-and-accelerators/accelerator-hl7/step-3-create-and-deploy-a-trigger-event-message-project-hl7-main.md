---
title: "步驟 3： 建立及部署觸發程序事件 （訊息） Project_hl7_main |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, trigger events
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ba388eef1f5dbfb885e33c6263c4e0f8ef4be29
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-projecthl7main"></a><span data-ttu-id="047b0-102">步驟 3： 建立及部署觸發程序事件 （訊息） Project_hl7_main</span><span class="sxs-lookup"><span data-stu-id="047b0-102">Step 3: Create and Deploy a Trigger Event (Message) Project_hl7_main</span></span>
<span data-ttu-id="047b0-103">在此步驟中，您可以建立使用觸發程序事件訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="047b0-103">In this step, you create the schema used by a trigger event message.</span></span> <span data-ttu-id="047b0-104">例如，許可放電和傳輸系統 (ADT)，傳送訊息醫院資訊系統 (HIS)。</span><span class="sxs-lookup"><span data-stu-id="047b0-104">For example, the Admissions Discharge and Transfer system (ADT) that sends a message to the Hospital Information System (HIS).</span></span> <span data-ttu-id="047b0-105">您可以使用此結構描述來定義訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="047b0-105">You use this schema to define the format of your message.</span></span>  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a><span data-ttu-id="047b0-106">若要建立觸發程序事件訊息的專案</span><span class="sxs-lookup"><span data-stu-id="047b0-106">To create the project for the trigger event message</span></span>  
  
1.  <span data-ttu-id="047b0-107">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="047b0-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="047b0-108">在 新增專案 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後按一下  **BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="047b0-108">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="047b0-109">在**範本**清單中，按一下**空白 BTAHL7 專案**。</span><span class="sxs-lookup"><span data-stu-id="047b0-109">In the **Templates** list, click **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="047b0-110">在**名稱**欄位中，輸入**BTAHL7V24Body 專案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="047b0-110">In the **Name** field, type **BTAHL7V24Body Project**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="047b0-111">在 方案總管 中，您的新節點下方**BTAHL7V24Body**專案中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="047b0-111">In Solution Explorer, under the node for your new **BTAHL7V24Body** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="047b0-112">在 加入參考 對話方塊中，按一下**專案**索引標籤上，選取**Interrogative_24Schemas**，按一下**新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="047b0-112">In the Add Reference dialog box, click the **Projects** tab, select **Interrogative_24Schemas**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="step-3a-add-the-schemas"></a><span data-ttu-id="047b0-113">步驟 3A： 新增結構描述</span><span class="sxs-lookup"><span data-stu-id="047b0-113">Step 3A: Add the Schemas</span></span>  
 <span data-ttu-id="047b0-114">使用下列程序，將新的結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="047b0-114">Use the following procedure to add the new schemas to the project.</span></span>  
  
#### <a name="to-add-the-schemas-to-the-project"></a><span data-ttu-id="047b0-115">將結構描述加入至專案</span><span class="sxs-lookup"><span data-stu-id="047b0-115">To add the schemas to the project</span></span>  
  
1.  <span data-ttu-id="047b0-116">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V24Body 專案**，指向 **新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="047b0-116">In Solution Explorer, right-click **BTAHL7V24Body Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="047b0-117">在 [加入新項目] 對話方塊中，依序展開**BizTalk 專案項目**，然後按兩下**BTAHL7 結構描述**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="047b0-117">In the Add New Item dialog box, expand **BizTalk Project Items**, and then double-click **BTAHL7 Schemas** in the right pane.</span></span>  
  
3.  <span data-ttu-id="047b0-118">在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="047b0-118">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="047b0-119">使用</span><span class="sxs-lookup"><span data-stu-id="047b0-119">Use this</span></span>|<span data-ttu-id="047b0-120">動作</span><span class="sxs-lookup"><span data-stu-id="047b0-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="047b0-121">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="047b0-121">**Message Class**</span></span>|<span data-ttu-id="047b0-122">保留**V2.X**選取。</span><span class="sxs-lookup"><span data-stu-id="047b0-122">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="047b0-123">**版本**</span><span class="sxs-lookup"><span data-stu-id="047b0-123">**Version**</span></span>|<span data-ttu-id="047b0-124">選取**2.4**。</span><span class="sxs-lookup"><span data-stu-id="047b0-124">Select **2.4**.</span></span>|  
    |<span data-ttu-id="047b0-125">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="047b0-125">**Message Type**</span></span>|<span data-ttu-id="047b0-126">選取**QRY**。</span><span class="sxs-lookup"><span data-stu-id="047b0-126">Select **QRY**.</span></span>|  
    |<span data-ttu-id="047b0-127">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="047b0-127">**Trigger Event**</span></span>|<span data-ttu-id="047b0-128">選取**Q01**。</span><span class="sxs-lookup"><span data-stu-id="047b0-128">Select **Q01**.</span></span>|  
  
4.  <span data-ttu-id="047b0-129">按一下**完成**將結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="047b0-129">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="047b0-130">這會建立查詢的結構描述檔案 QRY_Q01_24_GLO_DEF.xsd。</span><span class="sxs-lookup"><span data-stu-id="047b0-130">This creates the query schema file QRY_Q01_24_GLO_DEF.xsd.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="047b0-131">請勿關閉 [HL7 結構描述選取器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="047b0-131">Do not close the HL7 Schema Selector dialog box.</span></span>  
  
5.  <span data-ttu-id="047b0-132">在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="047b0-132">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="047b0-133">使用</span><span class="sxs-lookup"><span data-stu-id="047b0-133">Use this</span></span>|<span data-ttu-id="047b0-134">動作</span><span class="sxs-lookup"><span data-stu-id="047b0-134">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="047b0-135">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="047b0-135">**Message Class**</span></span>|<span data-ttu-id="047b0-136">保留**V2.X**選取。</span><span class="sxs-lookup"><span data-stu-id="047b0-136">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="047b0-137">**版本**</span><span class="sxs-lookup"><span data-stu-id="047b0-137">**Version**</span></span>|<span data-ttu-id="047b0-138">選取**2.4**。</span><span class="sxs-lookup"><span data-stu-id="047b0-138">Select **2.4**.</span></span>|  
    |<span data-ttu-id="047b0-139">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="047b0-139">**Message Type**</span></span>|<span data-ttu-id="047b0-140">選取**DSR**。</span><span class="sxs-lookup"><span data-stu-id="047b0-140">Select **DSR**.</span></span>|  
    |<span data-ttu-id="047b0-141">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="047b0-141">**Trigger Event**</span></span>|<span data-ttu-id="047b0-142">選取**Q01**。</span><span class="sxs-lookup"><span data-stu-id="047b0-142">Select **Q01**.</span></span>|  
  
6.  <span data-ttu-id="047b0-143">按一下**完成**將結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="047b0-143">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="047b0-144">這會建立回應結構描述檔 DSR_Q01_24_GLO_DEF.xsd。</span><span class="sxs-lookup"><span data-stu-id="047b0-144">This creates the response schema file DSR_Q01_24_GLO_DEF.xsd.</span></span>  
  
7.  <span data-ttu-id="047b0-145">按一下**取消**關閉**HL7 結構描述選取器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="047b0-145">Click **Cancel** to close the **HL7 Schema Selector** dialog box.</span></span>  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="047b0-146">步驟 3B： 指派強式金鑰組件和部署</span><span class="sxs-lookup"><span data-stu-id="047b0-146">Step 3B: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="047b0-147">若要將組件的強式金鑰，然後再部署組件使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="047b0-147">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="047b0-148">指派強式金鑰，並部署組件</span><span class="sxs-lookup"><span data-stu-id="047b0-148">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="047b0-149">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V24Body**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="047b0-149">In Solution Explorer, right-click **BTAHL7V24Body** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="047b0-150">在**BTAHL7V24Body 屬性頁**對話方塊中，按一下 **組件**。</span><span class="sxs-lookup"><span data-stu-id="047b0-150">In the **BTAHL7V24Body Property Pages** dialog box, click **Assembly**.</span></span>  
  
3.  <span data-ttu-id="047b0-151">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="047b0-151">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
4.  <span data-ttu-id="047b0-152">在**組件金鑰檔案**對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative 教學課程中，按一下**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="047b0-152">In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="047b0-153">在**BTAHL7V24Body 屬性頁**對話方塊中，按一下 **確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="047b0-153">In the **BTAHL7V24Body Property Pages** dialog box, click **OK** to save your changes.</span></span>  
  
6.  <span data-ttu-id="047b0-154">在 方案總管 中以滑鼠右鍵按一下**BTAHL7V24Body 專案**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="047b0-154">In Solution Explorer right-click **BTAHL7V24Body Project**, and then click **Deploy**.</span></span> <span data-ttu-id="047b0-155">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="047b0-155">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="047b0-156">如果不成功的部署訊息，請使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="047b0-156">If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="047b0-157">若要繼續[步驟 4： 建立接收埠，以便接受 ADT 查詢訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="047b0-157">Proceed to [Step 4: Create the Receive Port for Accepting ADT Query Messages](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).</span></span>