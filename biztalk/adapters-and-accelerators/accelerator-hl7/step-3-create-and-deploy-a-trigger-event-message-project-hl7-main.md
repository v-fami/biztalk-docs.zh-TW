---
title: 步驟 3： 建立及部署觸發程序事件 （訊息） 專案 _hl7_main |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, trigger events
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 263d131fffbeec996904d303be3fecd1eacf40c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013167"
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-projecthl7main"></a><span data-ttu-id="2bd87-102">步驟 3： 建立及部署觸發程序事件 （訊息） 專案 _hl7_main</span><span class="sxs-lookup"><span data-stu-id="2bd87-102">Step 3: Create and Deploy a Trigger Event (Message) Project_hl7_main</span></span>
<span data-ttu-id="2bd87-103">在此步驟中，您可以建立使用觸發程序事件訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2bd87-103">In this step, you create the schema used by a trigger event message.</span></span> <span data-ttu-id="2bd87-104">比方說，門診出院和傳輸系統 (ADT)，傳送訊息至醫院資訊系統 (HIS)。</span><span class="sxs-lookup"><span data-stu-id="2bd87-104">For example, the Admissions Discharge and Transfer system (ADT) that sends a message to the Hospital Information System (HIS).</span></span> <span data-ttu-id="2bd87-105">您可以使用此結構描述來定義訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="2bd87-105">You use this schema to define the format of your message.</span></span>  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a><span data-ttu-id="2bd87-106">若要建立觸發程序事件訊息的專案</span><span class="sxs-lookup"><span data-stu-id="2bd87-106">To create the project for the trigger event message</span></span>  
  
1. <span data-ttu-id="2bd87-107">在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="2bd87-108">在 [新增專案] 對話方塊中，在**專案類型**清單中，展開**BizTalk 專案**，然後按一下**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-108">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3. <span data-ttu-id="2bd87-109">在 **範本**清單中，按一下**空白 BTAHL7 專案**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-109">In the **Templates** list, click **Empty BTAHL7 Project**.</span></span>  
  
4. <span data-ttu-id="2bd87-110">在 **名稱**欄位中，輸入**BTAHL7V24Body 專案**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-110">In the **Name** field, type **BTAHL7V24Body Project**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="2bd87-111">在 [方案總管] 中，您新之節點下**BTAHL7V24Body**專案中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-111">In Solution Explorer, under the node for your new **BTAHL7V24Body** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
6. <span data-ttu-id="2bd87-112">在 加入參考 對話方塊中，按一下 **專案**索引標籤上，選取**Interrogative_24Schemas**，按一下**新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-112">In the Add Reference dialog box, click the **Projects** tab, select **Interrogative_24Schemas**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="step-3a-add-the-schemas"></a><span data-ttu-id="2bd87-113">步驟 3A： 新增結構描述</span><span class="sxs-lookup"><span data-stu-id="2bd87-113">Step 3A: Add the Schemas</span></span>  
 <span data-ttu-id="2bd87-114">使用下列程序，將新的結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="2bd87-114">Use the following procedure to add the new schemas to the project.</span></span>  
  
#### <a name="to-add-the-schemas-to-the-project"></a><span data-ttu-id="2bd87-115">若要將結構描述新增至專案</span><span class="sxs-lookup"><span data-stu-id="2bd87-115">To add the schemas to the project</span></span>  
  
1.  <span data-ttu-id="2bd87-116">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V24Body 專案**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-116">In Solution Explorer, right-click **BTAHL7V24Body Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="2bd87-117">在 [加入新項目] 對話方塊中，依序展開**BizTalk 專案項目**，然後按兩下**BTAHL7 結構描述**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="2bd87-117">In the Add New Item dialog box, expand **BizTalk Project Items**, and then double-click **BTAHL7 Schemas** in the right pane.</span></span>  
  
3.  <span data-ttu-id="2bd87-118">在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2bd87-118">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2bd87-119">使用</span><span class="sxs-lookup"><span data-stu-id="2bd87-119">Use this</span></span>|<span data-ttu-id="2bd87-120">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="2bd87-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2bd87-121">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="2bd87-121">**Message Class**</span></span>|<span data-ttu-id="2bd87-122">保持**V2.X**選取。</span><span class="sxs-lookup"><span data-stu-id="2bd87-122">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="2bd87-123">**版本(Version)**</span><span class="sxs-lookup"><span data-stu-id="2bd87-123">**Version**</span></span>|<span data-ttu-id="2bd87-124">選取  **2.4**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-124">Select **2.4**.</span></span>|  
    |<span data-ttu-id="2bd87-125">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="2bd87-125">**Message Type**</span></span>|<span data-ttu-id="2bd87-126">選取  **QRY**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-126">Select **QRY**.</span></span>|  
    |<span data-ttu-id="2bd87-127">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="2bd87-127">**Trigger Event**</span></span>|<span data-ttu-id="2bd87-128">選取  **Q01**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-128">Select **Q01**.</span></span>|  
  
4.  <span data-ttu-id="2bd87-129">按一下 **完成**將結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="2bd87-129">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="2bd87-130">這會建立查詢的結構描述檔案 QRY_Q01_24_GLO_DEF.xsd。</span><span class="sxs-lookup"><span data-stu-id="2bd87-130">This creates the query schema file QRY_Q01_24_GLO_DEF.xsd.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2bd87-131">請勿關閉 [HL7 結構描述選取器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2bd87-131">Do not close the HL7 Schema Selector dialog box.</span></span>  
  
5.  <span data-ttu-id="2bd87-132">在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2bd87-132">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2bd87-133">使用</span><span class="sxs-lookup"><span data-stu-id="2bd87-133">Use this</span></span>|<span data-ttu-id="2bd87-134">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="2bd87-134">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2bd87-135">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="2bd87-135">**Message Class**</span></span>|<span data-ttu-id="2bd87-136">保持**V2.X**選取。</span><span class="sxs-lookup"><span data-stu-id="2bd87-136">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="2bd87-137">**版本(Version)**</span><span class="sxs-lookup"><span data-stu-id="2bd87-137">**Version**</span></span>|<span data-ttu-id="2bd87-138">選取  **2.4**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-138">Select **2.4**.</span></span>|  
    |<span data-ttu-id="2bd87-139">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="2bd87-139">**Message Type**</span></span>|<span data-ttu-id="2bd87-140">選取  **DSR**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-140">Select **DSR**.</span></span>|  
    |<span data-ttu-id="2bd87-141">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="2bd87-141">**Trigger Event**</span></span>|<span data-ttu-id="2bd87-142">選取  **Q01**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-142">Select **Q01**.</span></span>|  
  
6.  <span data-ttu-id="2bd87-143">按一下 **完成**將結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="2bd87-143">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="2bd87-144">這會建立回應結構描述檔 DSR_Q01_24_GLO_DEF.xsd。</span><span class="sxs-lookup"><span data-stu-id="2bd87-144">This creates the response schema file DSR_Q01_24_GLO_DEF.xsd.</span></span>  
  
7.  <span data-ttu-id="2bd87-145">按一下 [**取消**以關閉**HL7 結構描述選取器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2bd87-145">Click **Cancel** to close the **HL7 Schema Selector** dialog box.</span></span>  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="2bd87-146">步驟 3B： 指派強式金鑰組件和部署</span><span class="sxs-lookup"><span data-stu-id="2bd87-146">Step 3B: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="2bd87-147">使用下列程序組件指派強式金鑰，然後再部署組件。</span><span class="sxs-lookup"><span data-stu-id="2bd87-147">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="2bd87-148">指派強式金鑰，並部署組件</span><span class="sxs-lookup"><span data-stu-id="2bd87-148">To assign a strong key and deploy the assembly</span></span>  
  
1. <span data-ttu-id="2bd87-149">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V24Body**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-149">In Solution Explorer, right-click **BTAHL7V24Body** project, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="2bd87-150">在 [ **BTAHL7V24Body 屬性頁**] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-150">In the **BTAHL7V24Body Property Pages** dialog box, click **Assembly**.</span></span>  
  
3. <span data-ttu-id="2bd87-151">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2bd87-151">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
4. <span data-ttu-id="2bd87-152">在 [**組件金鑰檔案**] 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>加速器 HL7\SDK\Interrogative 教學課程中，按一下**key.snk**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-152">In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="2bd87-153">在 [ **BTAHL7V24Body 屬性頁**] 對話方塊中，按一下 **[確定]** 以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="2bd87-153">In the **BTAHL7V24Body Property Pages** dialog box, click **OK** to save your changes.</span></span>  
  
6. <span data-ttu-id="2bd87-154">在 [方案總管] 中以滑鼠右鍵按一下**BTAHL7V24Body 專案**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="2bd87-154">In Solution Explorer right-click **BTAHL7V24Body Project**, and then click **Deploy**.</span></span> <span data-ttu-id="2bd87-155">請確定在 [輸出] 視窗中會出現成功訊息。</span><span class="sxs-lookup"><span data-stu-id="2bd87-155">Ensure a success message appears in the output window.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="2bd87-156">如果不成功的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2bd87-156">If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
   <span data-ttu-id="2bd87-157">請繼續進行[步驟 4： 建立接收埠，以接受 ADT 查詢訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd87-157">Proceed to [Step 4: Create the Receive Port for Accepting ADT Query Messages](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).</span></span>