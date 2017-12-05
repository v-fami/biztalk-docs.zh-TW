---
title: "步驟 6： 建立傳送埠認可批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 958746634776e9b01c32ff2425122312bc7a841c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-6-create-the-send-port-for-the-acknowledgment-batch"></a><span data-ttu-id="e2b25-102">步驟 6： 建立通知批次的傳送埠</span><span class="sxs-lookup"><span data-stu-id="e2b25-102">Step 6: Create the Send Port for the Acknowledgment Batch</span></span>
<span data-ttu-id="e2b25-103">在此步驟中，您可以建立傳送埠以將您建立的認可批次傳送到來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="e2b25-103">In this step, you create a send port to deliver the acknowledgment batch that you create to the source party.</span></span> <span data-ttu-id="e2b25-104">這是靜態單向連接埠與 FILE 配接器類型。</span><span class="sxs-lookup"><span data-stu-id="e2b25-104">This is a static one-way port with a FILE adapter type.</span></span> <span data-ttu-id="e2b25-105">您指定檔案資料夾的來源 (\Tutorial_BatchACKDrop)，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將卸除認可批次檔。</span><span class="sxs-lookup"><span data-stu-id="e2b25-105">You designate a file folder for the source (\Tutorial_BatchACKDrop), where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the acknowledgment batch file.</span></span> <span data-ttu-id="e2b25-106">您定義指出哪種類型的通知批次傳送連接埠的連接埠的篩選。</span><span class="sxs-lookup"><span data-stu-id="e2b25-106">You define a filter for the port indicating what type of acknowledgment batches the ports will send.</span></span> <span data-ttu-id="e2b25-107">篩選器會指定來源 Tutorial_BatchSource 和 OutboundBatch 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="e2b25-107">The filter specifies the source of Tutorial_BatchSource and the message type of OutboundBatch.</span></span>  
  
### <a name="to-create-the-send-port-for-the-acknowledgment-batch"></a><span data-ttu-id="e2b25-108">若要建立通知批次的傳送埠</span><span class="sxs-lookup"><span data-stu-id="e2b25-108">To create the send port for the acknowledgment batch</span></span>  
  
1.  <span data-ttu-id="e2b25-109">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-109">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="e2b25-110">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e2b25-110">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="e2b25-111">使用</span><span class="sxs-lookup"><span data-stu-id="e2b25-111">Use this</span></span>|<span data-ttu-id="e2b25-112">動作</span><span class="sxs-lookup"><span data-stu-id="e2b25-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e2b25-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e2b25-113">**Name**</span></span>|<span data-ttu-id="e2b25-114">型別**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-114">Type **Tutorial_BatchSource**.</span></span>|  
    |<span data-ttu-id="e2b25-115">**型別**</span><span class="sxs-lookup"><span data-stu-id="e2b25-115">**Type**</span></span>|<span data-ttu-id="e2b25-116">選取**檔案**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e2b25-116">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="e2b25-117">**設定**</span><span class="sxs-lookup"><span data-stu-id="e2b25-117">**Configure**</span></span>|<span data-ttu-id="e2b25-118">按一下**設定**以開啟 [FILE 傳輸屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e2b25-118">Click **Configure** to open the FILE Transport Properties dialog box.</span></span>|  
  
3.  <span data-ttu-id="e2b25-119">在 [FILE 傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e2b25-119">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="e2b25-120">使用</span><span class="sxs-lookup"><span data-stu-id="e2b25-120">Use this</span></span>|<span data-ttu-id="e2b25-121">動作</span><span class="sxs-lookup"><span data-stu-id="e2b25-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e2b25-122">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="e2b25-122">**Destination folder**</span></span>|<span data-ttu-id="e2b25-123">瀏覽至  **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchACKDrop * *。</span><span class="sxs-lookup"><span data-stu-id="e2b25-123">Browse to **\<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchACKDrop**.</span></span> <span data-ttu-id="e2b25-124">這是在檔案系統或公用共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將撰寫包含認可批次的檔案。</span><span class="sxs-lookup"><span data-stu-id="e2b25-124">This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file containing the acknowledgment batch.</span></span>|  
    |<span data-ttu-id="e2b25-125">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="e2b25-125">**File name**</span></span>|<span data-ttu-id="e2b25-126">型別**%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。</span><span class="sxs-lookup"><span data-stu-id="e2b25-126">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
    |<span data-ttu-id="e2b25-127">**複製模式**</span><span class="sxs-lookup"><span data-stu-id="e2b25-127">**Copy mode**</span></span>|<span data-ttu-id="e2b25-128">選取**建立新**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-128">Select **Create New**.</span></span>|  
  
4.  <span data-ttu-id="e2b25-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-129">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e2b25-130">在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-130">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="e2b25-131">在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e2b25-131">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="e2b25-132">使用</span><span class="sxs-lookup"><span data-stu-id="e2b25-132">Use this</span></span>|<span data-ttu-id="e2b25-133">動作</span><span class="sxs-lookup"><span data-stu-id="e2b25-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e2b25-134">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e2b25-134">**Property**</span></span>|<span data-ttu-id="e2b25-135">按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e2b25-135">Click the field under **Property**, and then select **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** from the drop-down list.</span></span>|  
    |<span data-ttu-id="e2b25-136">**運算子**</span><span class="sxs-lookup"><span data-stu-id="e2b25-136">**Operator**</span></span>|<span data-ttu-id="e2b25-137">保留 **==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="e2b25-137">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="e2b25-138">**值**</span><span class="sxs-lookup"><span data-stu-id="e2b25-138">**Value**</span></span>|<span data-ttu-id="e2b25-139">型別**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-139">Type **Tutorial_BatchSource**.</span></span>|  
    |<span data-ttu-id="e2b25-140">**Group By**</span><span class="sxs-lookup"><span data-stu-id="e2b25-140">**Group By**</span></span>|<span data-ttu-id="e2b25-141">選取**和**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e2b25-141">Select **And** from the drop-down list.</span></span>|  
    |<span data-ttu-id="e2b25-142">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e2b25-142">**Property**</span></span>|<span data-ttu-id="e2b25-143">選取**BTAHL7Schemas.BTAHL7MessageType**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-143">Select **BTAHL7Schemas.BTAHL7MessageType**.</span></span>|  
    |<span data-ttu-id="e2b25-144">**運算子**</span><span class="sxs-lookup"><span data-stu-id="e2b25-144">**Operator**</span></span>|<span data-ttu-id="e2b25-145">保留 **==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="e2b25-145">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="e2b25-146">**值**</span><span class="sxs-lookup"><span data-stu-id="e2b25-146">**Value**</span></span>|<span data-ttu-id="e2b25-147">型別**OutboundBatch**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-147">Type **OutboundBatch**.</span></span>|  
  
7.  <span data-ttu-id="e2b25-148">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e2b25-148">Press **Enter**.</span></span> <span data-ttu-id="e2b25-149">在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-149">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e2b25-150">在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-150">In the BizTalk Administration Console, select **Send Ports**, right-click **Tutorial_BatchSource**, and then click **Start**.</span></span>  
  
### <a name="to-associate-the-send-port-with-the-source-party"></a><span data-ttu-id="e2b25-151">要與來源合作對象產生關聯的傳送埠</span><span class="sxs-lookup"><span data-stu-id="e2b25-151">To associate the send port with the source party</span></span>  
  
1.  <span data-ttu-id="e2b25-152">在 BizTalk 管理主控台中，按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-152">In the BizTalk Administration Console, click **Parties**.</span></span> <span data-ttu-id="e2b25-153">以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-153">Right-click **Tutorial_BatchSource**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e2b25-154">在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="e2b25-154">In the Party Properties dialog box, click **Send Ports** in the console tree.</span></span> <span data-ttu-id="e2b25-155">如**傳送埠**，選取**Tutorial_BatchSource**從下拉式清單，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e2b25-155">For **Send Ports**, select **Tutorial_BatchSource** from the drop-down list, and then click **OK**.</span></span>  
  
 <span data-ttu-id="e2b25-156">若要繼續[步驟 7： 啟動協調流程，然後重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b25-156">Proceed to [Step 7: Start the Orchestration and Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md).</span></span>