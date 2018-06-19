---
title: 步驟 5： 建立傳送埠的訊息批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5db815df-5b76-4ba4-99ab-c7766b0c301a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5749166c8a9b34d5e5a04849c4179ac4427201c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "26006007"
---
# <a name="step-5-create-the-send-port-for-the-message-batch"></a><span data-ttu-id="f93da-102">步驟 5： 建立傳送埠的訊息批次</span><span class="sxs-lookup"><span data-stu-id="f93da-102">Step 5: Create the Send Port for the Message Batch</span></span>
<span data-ttu-id="f93da-103">在此步驟中，您可以建立傳送埠以將您建立的訊息批次傳遞至目的合作對象。</span><span class="sxs-lookup"><span data-stu-id="f93da-103">In this step, you create a send port to deliver the message batch that you create to the destination party.</span></span> <span data-ttu-id="f93da-104">這是靜態單向連接埠與 FILE 配接器類型。</span><span class="sxs-lookup"><span data-stu-id="f93da-104">This is a static one-way port with a FILE adapter type.</span></span> <span data-ttu-id="f93da-105">您指定的目的地 (\Tutorial_BatchMsgDrop) 的檔案資料夾位置[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將卸除的訊息批次檔。</span><span class="sxs-lookup"><span data-stu-id="f93da-105">You designate a file folder for the destination (\Tutorial_BatchMsgDrop) where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the message batch file.</span></span> <span data-ttu-id="f93da-106">您定義指出哪種類型的訊息批次傳送連接埠的連接埠的篩選。</span><span class="sxs-lookup"><span data-stu-id="f93da-106">You define a filter for the port indicating what type of message batches the ports will send.</span></span> <span data-ttu-id="f93da-107">篩選器會指定 Tutorial_BatchDest 和 OutboundBatch 的訊息類型的目的地。</span><span class="sxs-lookup"><span data-stu-id="f93da-107">The filter specifies the destination of Tutorial_BatchDest and the message type of OutboundBatch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f93da-108">當執行本教學課程的這個部分，您可以簡化結果停止傳送埠用於本教學課程的第 2 部分： **Tutorial_BTAHL7Drop**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f93da-108">When running this part of the tutorial, you can simplify the results by stopping the send port used in Part 2 of the tutorial: the **Tutorial_BTAHL7Drop** send port.</span></span>  
  
### <a name="to-create-the-send-port-for-the-message-batch"></a><span data-ttu-id="f93da-109">若要建立的訊息批次的傳送埠</span><span class="sxs-lookup"><span data-stu-id="f93da-109">To create the send port for the message batch</span></span>  
  
1.  <span data-ttu-id="f93da-110">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f93da-110">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f93da-111">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f93da-111">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f93da-112">使用</span><span class="sxs-lookup"><span data-stu-id="f93da-112">Use this</span></span>|<span data-ttu-id="f93da-113">動作</span><span class="sxs-lookup"><span data-stu-id="f93da-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f93da-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f93da-114">**Name**</span></span>|<span data-ttu-id="f93da-115">型別**Tutorial_BatchDest**。</span><span class="sxs-lookup"><span data-stu-id="f93da-115">Type **Tutorial_BatchDest**.</span></span>|  
    |<span data-ttu-id="f93da-116">**型別**</span><span class="sxs-lookup"><span data-stu-id="f93da-116">**Type**</span></span>|<span data-ttu-id="f93da-117">選取**檔案**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f93da-117">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f93da-118">**設定**</span><span class="sxs-lookup"><span data-stu-id="f93da-118">**Configure**</span></span>|<span data-ttu-id="f93da-119">按一下**設定**以開啟 [FILE 傳輸屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f93da-119">Click **Configure** to open the FILE Transport Properties dialog box.</span></span>|  
  
3.  <span data-ttu-id="f93da-120">在**FILE 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f93da-120">In the **FILE Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f93da-121">使用</span><span class="sxs-lookup"><span data-stu-id="f93da-121">Use this</span></span>|<span data-ttu-id="f93da-122">動作</span><span class="sxs-lookup"><span data-stu-id="f93da-122">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f93da-123">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="f93da-123">**Destination folder**</span></span>|<span data-ttu-id="f93da-124">瀏覽至 **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchMsgDrop**.</span><span class="sxs-lookup"><span data-stu-id="f93da-124">Browse to **\<*drive*:\>\Program Files\Microsoft  BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchMsgDrop**.</span></span> <span data-ttu-id="f93da-125">這是在檔案系統或公用共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入含有訊息批次的檔案。</span><span class="sxs-lookup"><span data-stu-id="f93da-125">This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file containing the message batch.</span></span>|  
    |<span data-ttu-id="f93da-126">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="f93da-126">**File name**</span></span>|<span data-ttu-id="f93da-127">型別 **%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。</span><span class="sxs-lookup"><span data-stu-id="f93da-127">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
    |<span data-ttu-id="f93da-128">**複製模式**</span><span class="sxs-lookup"><span data-stu-id="f93da-128">**Copy mode**</span></span>|<span data-ttu-id="f93da-129">選取**建立新**。</span><span class="sxs-lookup"><span data-stu-id="f93da-129">Select **Create New**.</span></span>|  
  
4.  <span data-ttu-id="f93da-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f93da-130">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="f93da-131">在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="f93da-131">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="f93da-132">在主控台樹狀目錄中，按一下  **篩選**, ，然後執行下列一項︰</span><span class="sxs-lookup"><span data-stu-id="f93da-132">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="f93da-133">使用</span><span class="sxs-lookup"><span data-stu-id="f93da-133">Use this</span></span>|<span data-ttu-id="f93da-134">動作</span><span class="sxs-lookup"><span data-stu-id="f93da-134">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f93da-135">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f93da-135">**Property**</span></span>|<span data-ttu-id="f93da-136">按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f93da-136">Click the field under **Property**, and then select **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f93da-137">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f93da-137">**Operator**</span></span>|<span data-ttu-id="f93da-138">保留 **==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="f93da-138">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="f93da-139">**值**</span><span class="sxs-lookup"><span data-stu-id="f93da-139">**Value**</span></span>|<span data-ttu-id="f93da-140">型別**Tutorial_BatchDest**。</span><span class="sxs-lookup"><span data-stu-id="f93da-140">Type **Tutorial_BatchDest**.</span></span>|  
    |<span data-ttu-id="f93da-141">**分組方式**</span><span class="sxs-lookup"><span data-stu-id="f93da-141">**Group By**</span></span>|<span data-ttu-id="f93da-142">選取**和**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f93da-142">Select **And** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f93da-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f93da-143">**Property**</span></span>|<span data-ttu-id="f93da-144">選取**BTAHL7Schemas.BTAHL7MessageType**。</span><span class="sxs-lookup"><span data-stu-id="f93da-144">Select **BTAHL7Schemas.BTAHL7MessageType**.</span></span>|  
    |<span data-ttu-id="f93da-145">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f93da-145">**Operator**</span></span>|<span data-ttu-id="f93da-146">保留 **==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="f93da-146">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="f93da-147">**值**</span><span class="sxs-lookup"><span data-stu-id="f93da-147">**Value**</span></span>|<span data-ttu-id="f93da-148">型別**OutboundBatch**。</span><span class="sxs-lookup"><span data-stu-id="f93da-148">Type **OutboundBatch**.</span></span>|  
  
7.  <span data-ttu-id="f93da-149">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="f93da-149">Press **Enter**.</span></span> <span data-ttu-id="f93da-150">在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f93da-150">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f93da-151">在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchDest**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="f93da-151">In the BizTalk Administration Console, select **Send Ports**, right-click **Tutorial_BatchDest**, and then click **Start**.</span></span>  
  
### <a name="to-associate-the-send-port-with-the-destination-party"></a><span data-ttu-id="f93da-152">若要將傳送埠與目的合作對象產生關聯</span><span class="sxs-lookup"><span data-stu-id="f93da-152">To associate the send port with the destination party</span></span>  
  
1.  <span data-ttu-id="f93da-153">在 BizTalk Server 管理主控台中，展開**合作對象**，按一下  **Tutorial_BatchDest**，然後以滑鼠右鍵按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f93da-153">In the BizTalk Server Administration Console, expand **Parties**, click **Tutorial_BatchDest**, and then right-click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f93da-154">在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="f93da-154">In the Party Properties dialog box, click  **Send Ports** in the console tree.</span></span>  <span data-ttu-id="f93da-155">選取**Tutorial_BatchDest**從下拉式清單，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f93da-155">Select **Tutorial_BatchDest** from the drop-down list, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f93da-156">如果並行存取違規，就會發生時**Tutorial_DestBatch**更新合作對象，按一下**確定**並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f93da-156">If a concurrency violation occurs while the **Tutorial_DestBatch** party was being updated, click **OK** and close the dialog box.</span></span> <span data-ttu-id="f93da-157">在管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，按一下 **重新整理**，然後重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="f93da-157">In the Administration Console, right-click **BizTalk Group**, click **Refresh**, and then repeat steps 1 and 2.</span></span>  
  
 <span data-ttu-id="f93da-158">若要繼續[步驟 6： 建立通知批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="f93da-158">Proceed to [Step 6: Create the Send Port for the Acknowledgment Batch](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md).</span></span>