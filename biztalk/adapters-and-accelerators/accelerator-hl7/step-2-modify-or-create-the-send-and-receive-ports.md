---
title: 步驟 2： 修改或建立傳送和接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42c40652d334fd2c7dec2475edca81b9fc9b1b14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996519"
---
# <a name="step-2-modify-or-create-the-send-and-receive-ports"></a><span data-ttu-id="8f69c-102">步驟 2： 修改或建立傳送和接收埠</span><span class="sxs-lookup"><span data-stu-id="8f69c-102">Step 2: Modify or Create the Send and Receive Ports</span></span>
<span data-ttu-id="8f69c-103">FILE 傳送和接收埠以進行批次，您需要在 / 批次出教學課程。</span><span class="sxs-lookup"><span data-stu-id="8f69c-103">You need FILE send and receive ports for the Batch In/Batch Out tutorial.</span></span> <span data-ttu-id="8f69c-104">如果您按下**啟動的教學課程**結尾的安裝 Enterprise Edition 的按鈕[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]為您建立這些連接埠： 名為 Tutorial_BTAHL7Drop，傳送埠和接收埠命名為 Tutorial_BTAHL7PickUp。</span><span class="sxs-lookup"><span data-stu-id="8f69c-104">If you clicked the **Launch Tutorial** button at the end of installing the Enterprise Edition of [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] created these ports for you: a send port named Tutorial_BTAHL7Drop, and a receive port named Tutorial_BTAHL7PickUp.</span></span> <span data-ttu-id="8f69c-105">如果您有這些連接埠，您仍然需要修改傳送埠 Tutorial_BTAHL7Drop。</span><span class="sxs-lookup"><span data-stu-id="8f69c-105">If you have these ports, you still need to modify the send port Tutorial_BTAHL7Drop.</span></span>  

 <span data-ttu-id="8f69c-106">如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式建立傳送和接收埠以進行您，請參閱本主題中，「 建立 BIBOTutorialPickup 接收連接埠 」 程序，且然後請參閱 「 建立 BIBOTutorialDrop 傳送連接埠 」 也是本主題中的程序。</span><span class="sxs-lookup"><span data-stu-id="8f69c-106">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup did not create the send and receive ports for you, see "To create the BIBOTutorialPickup receive port" procedure in this topic, and then see "To create the BIBOTutorialDrop send port" procedure also in this topic.</span></span>  

### <a name="to-modify-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="8f69c-107">若要修改 Tutorial_BTAHL7Drop 傳送埠</span><span class="sxs-lookup"><span data-stu-id="8f69c-107">To modify the Tutorial_BTAHL7Drop send port</span></span>  

1. <span data-ttu-id="8f69c-108">按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-108">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="8f69c-109">在管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk 應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-109">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  

3. <span data-ttu-id="8f69c-110">按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_BTAHL7Drop**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-110">Click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Properties**.</span></span>  

4. <span data-ttu-id="8f69c-111">在主控台樹狀目錄中，按一下**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-111">In the console tree, click **Filters**.</span></span>  

5. <span data-ttu-id="8f69c-112">在 **篩選器**窗格中的，第二個資料列中，選取**BTAHL7Schemas.MessageClass**的**屬性**，選取**==** 的**運算子**，然後輸入**MessageClass2X** for**值**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-112">In the **Filters** pane, in the second row, select **BTAHL7Schemas.MessageClass** for **Properties**, select **==** for **Operator**, and type **MessageClass2X** for **Value**.</span></span> <span data-ttu-id="8f69c-113">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-113">Click **Enter**.</span></span>  

6. <span data-ttu-id="8f69c-114">設定**分組**上**BTS。ReceivePortName**列**或是**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-114">Set **Group By** on the **BTS.ReceivePortName** line to **Or**, and then click **OK**.</span></span>  

7. <span data-ttu-id="8f69c-115">在 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理 視窗中，展開**平台設定**，然後展開**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-115">In the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration window, expand **Platform Settings**, and expand **Host Instances**.</span></span> <span data-ttu-id="8f69c-116">以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-116">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f69c-117">只能使用下列程序，如果您已安裝 Standard Edition [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]，或如果您沒有按一下**啟動的教學課程**按鈕，當您設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f69c-117">Only use the following procedures if you installed the Standard Edition of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], or if you did not click the **Launch Tutorial** button when you set up [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span>  

### <a name="to-create-the-tutorialbtahl7pickup-receive-port-and-location"></a><span data-ttu-id="8f69c-118">若要建立 Tutorial_BTAHL7Pickup 接收埠和位置</span><span class="sxs-lookup"><span data-stu-id="8f69c-118">To create the Tutorial_BTAHL7Pickup receive port and location</span></span>  

1. <span data-ttu-id="8f69c-119">按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-119">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="8f69c-120">在管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk 應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-120">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  

3. <span data-ttu-id="8f69c-121">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  

4. <span data-ttu-id="8f69c-122">在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入**Tutorial_BTAHL7PickUp**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-122">In the Receive Port Properties dialog box, in the **Name** box, type **Tutorial_BTAHL7PickUp**.</span></span>  

5. <span data-ttu-id="8f69c-123">按一下 **套用**要繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  

6. <span data-ttu-id="8f69c-124">以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-124">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  

7. <span data-ttu-id="8f69c-125">在 [選取接收埠] 對話方塊中，按一下**Tutorial_BTAHL7PickUp**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-125">In the Select a Receive Port dialog box, click **Tutorial_BTAHL7PickUp**, and then click **OK**.</span></span>  

8. <span data-ttu-id="8f69c-126">在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_FileReceiveLoc**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-126">In the Receive Location Properties dialog box, in the **Name** box, type **Tutorial_FileReceiveLoc**.</span></span>  

9. <span data-ttu-id="8f69c-127">在**傳輸**區段中，如**型別**文字方塊中，按一下下拉式清單中，然後按**檔案**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-127">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  

10. <span data-ttu-id="8f69c-128">按一下 **設定**按鈕右邊的 類型 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f69c-128">Click the **Configure** button to the right of the Type drop-down list.</span></span>  

11. <span data-ttu-id="8f69c-129">在 [FILE 傳輸屬性] 對話方塊中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8f69c-129">In the FILE Transport Properties dialog box, do the following:</span></span>  


    |      <span data-ttu-id="8f69c-130">使用</span><span class="sxs-lookup"><span data-stu-id="8f69c-130">Use this</span></span>      |                                                                                                                                                                         <span data-ttu-id="8f69c-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f69c-131">To do this</span></span>                                                                                                                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | <span data-ttu-id="8f69c-132">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="8f69c-132">**Receive Folder**</span></span> | <span data-ttu-id="8f69c-133">瀏覽至**\<**<em>磁碟機</em>**\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7PickUp**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-133">Browse to **\<**<em>drive</em>**\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp**.</span></span> <span data-ttu-id="8f69c-134">**注意︰** 這是在檔案系統或公用的共用位置的路徑從何處[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會收取檔案。</span><span class="sxs-lookup"><span data-stu-id="8f69c-134">**Note:**  This is the path to the location on the file system or public share from where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will pick up the file.</span></span> |
    |   <span data-ttu-id="8f69c-135">**檔案遮罩**</span><span class="sxs-lookup"><span data-stu-id="8f69c-135">**File mask**</span></span>    |                                                                                                                                                                      <span data-ttu-id="8f69c-136">型別 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-136">Type **\*.txt**.</span></span>                                                                                                                                                                       |


12. <span data-ttu-id="8f69c-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f69c-137">Click **OK**.</span></span>  

13. <span data-ttu-id="8f69c-138">在 [接收位置屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f69c-138">In the Receive Location Properties dialog box, do the following:</span></span>  


    |       <span data-ttu-id="8f69c-139">使用</span><span class="sxs-lookup"><span data-stu-id="8f69c-139">Use this</span></span>       |                      <span data-ttu-id="8f69c-140">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f69c-140">To do this</span></span>                       |
    |----------------------|-------------------------------------------------------|
    | <span data-ttu-id="8f69c-141">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="8f69c-141">**Receive Handler**</span></span>  |    <span data-ttu-id="8f69c-142">保持**BizTalkServerApplication**為選取狀態。</span><span class="sxs-lookup"><span data-stu-id="8f69c-142">Keep **BizTalkServerApplication** as selected.</span></span>     |
    | <span data-ttu-id="8f69c-143">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="8f69c-143">**Receive Pipeline**</span></span> | <span data-ttu-id="8f69c-144">選取  **BTAHL72XPipelines.BTAHL72XReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-144">Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span></span> |


14. <span data-ttu-id="8f69c-145">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f69c-145">Click **OK**.</span></span>  

15. <span data-ttu-id="8f69c-146">在 [BizTalk 總管] 中，以滑鼠右鍵按一下**Tutorial_FileReceiveLoc**，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-146">In BizTalk Explorer, right-click **Tutorial_FileReceiveLoc**, and then click **Enable**.</span></span>  

### <a name="to-create-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="8f69c-147">若要建立 Tutorial_BTAHL7Drop 傳送埠</span><span class="sxs-lookup"><span data-stu-id="8f69c-147">To create the Tutorial_BTAHL7Drop send port</span></span>  

1. <span data-ttu-id="8f69c-148">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-148">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="8f69c-149">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f69c-149">In the Send Port Properties dialog box, do the following:</span></span>  


   |   <span data-ttu-id="8f69c-150">使用</span><span class="sxs-lookup"><span data-stu-id="8f69c-150">Use this</span></span>    |                                <span data-ttu-id="8f69c-151">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f69c-151">To do this</span></span>                                 |
   |---------------|---------------------------------------------------------------------------|
   |   <span data-ttu-id="8f69c-152">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8f69c-152">**Name**</span></span>    |                       <span data-ttu-id="8f69c-153">型別**Tutorial_BTAHL7Drop**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-153">Type **Tutorial_BTAHL7Drop**.</span></span>                       |
   |   <span data-ttu-id="8f69c-154">**型別**</span><span class="sxs-lookup"><span data-stu-id="8f69c-154">**Type**</span></span>    |                 <span data-ttu-id="8f69c-155">選取 **檔案**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f69c-155">Select **FILE** from the drop-down list.</span></span>                  |
   | <span data-ttu-id="8f69c-156">**設定**</span><span class="sxs-lookup"><span data-stu-id="8f69c-156">**Configure**</span></span> | <span data-ttu-id="8f69c-157">按一下 [**設定**來開啟**FILE 傳輸屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8f69c-157">Click **Configure** to open the **FILE Transport Properties** dialog box.</span></span> |


3. <span data-ttu-id="8f69c-158">在 [FILE 傳輸屬性] 對話方塊中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8f69c-158">In the FILE Transport Properties dialog box, do the following:</span></span>  


   |        <span data-ttu-id="8f69c-159">使用</span><span class="sxs-lookup"><span data-stu-id="8f69c-159">Use this</span></span>        |                                                                                                                                                                      <span data-ttu-id="8f69c-160">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f69c-160">To do this</span></span>                                                                                                                                                                       |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="8f69c-161">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="8f69c-161">**Destination folder**</span></span> | <span data-ttu-id="8f69c-162">瀏覽至**\<**<em>磁碟機</em>**:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7Drop**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-162">Browse to **\<**<em>drive</em>**:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop**.</span></span> <span data-ttu-id="8f69c-163">**注意︰** 這是在檔案系統或公開共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="8f69c-163">**Note:**  This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file.</span></span> |
   |     <span data-ttu-id="8f69c-164">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="8f69c-164">**File name**</span></span>      |                                                                                                                                          <span data-ttu-id="8f69c-165">型別 **%MessageID%.txt** （請注意，副檔名為 txt，不是 xml）。</span><span class="sxs-lookup"><span data-stu-id="8f69c-165">Type **%MessageID%.txt** (note that the extension is txt, not xml).</span></span>                                                                                                                                          |


4. <span data-ttu-id="8f69c-166">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f69c-166">Click **OK**.</span></span>  

5. <span data-ttu-id="8f69c-167">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f69c-167">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline** from the drop-down list.</span></span>  

6. <span data-ttu-id="8f69c-168">在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8f69c-168">In the console tree, click **Filters**, and then do the following:</span></span>  


   |   <span data-ttu-id="8f69c-169">使用</span><span class="sxs-lookup"><span data-stu-id="8f69c-169">Use this</span></span>   |                       <span data-ttu-id="8f69c-170">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f69c-170">To do this</span></span>                        |
   |--------------|---------------------------------------------------------|
   | <span data-ttu-id="8f69c-171">**屬性**</span><span class="sxs-lookup"><span data-stu-id="8f69c-171">**Property**</span></span> | <span data-ttu-id="8f69c-172">選取**BTS。ReceivePortName**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f69c-172">Select **BTS.ReceivePortName** from the drop-down list.</span></span> |
   | <span data-ttu-id="8f69c-173">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="8f69c-173">**Operator**</span></span> |              <span data-ttu-id="8f69c-174">離開**==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="8f69c-174">Leave **==** as the operator.</span></span>              |
   |  <span data-ttu-id="8f69c-175">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="8f69c-175">**Value**</span></span>   |             <span data-ttu-id="8f69c-176">型別**Tutorial_BTAHL7PickUp**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-176">Type **Tutorial_BTAHL7PickUp**.</span></span>             |
   | <span data-ttu-id="8f69c-177">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="8f69c-177">**Group By**</span></span> |         <span data-ttu-id="8f69c-178">選取 **或**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f69c-178">Select **Or** from the drop-down list.</span></span>          |
   | <span data-ttu-id="8f69c-179">**屬性**</span><span class="sxs-lookup"><span data-stu-id="8f69c-179">**Property**</span></span> |         <span data-ttu-id="8f69c-180">選取  **BTAHL7Schemas.MessageClass**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-180">Select **BTAHL7Schemas.MessageClass**.</span></span>          |
   | <span data-ttu-id="8f69c-181">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="8f69c-181">**Operator**</span></span> |              <span data-ttu-id="8f69c-182">離開**==** 做為運算子。</span><span class="sxs-lookup"><span data-stu-id="8f69c-182">Leave **==** as the operator.</span></span>              |
   |  <span data-ttu-id="8f69c-183">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="8f69c-183">**Value**</span></span>   |                <span data-ttu-id="8f69c-184">型別**MessageClass2X**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-184">Type **MessageClass2X**.</span></span>                 |


7. <span data-ttu-id="8f69c-185">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-185">Click **Enter**.</span></span> <span data-ttu-id="8f69c-186">確認在對話方塊底部窗格中的篩選條件運算式正確。</span><span class="sxs-lookup"><span data-stu-id="8f69c-186">Verify in the pane at the bottom of the dialog box that the filter expression is correct.</span></span>  

8. <span data-ttu-id="8f69c-187">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f69c-187">Click **OK**.</span></span>  

9. <span data-ttu-id="8f69c-188">在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_BTAHL7Drop**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-188">In the Administration Console, click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Start**.</span></span>  

10. <span data-ttu-id="8f69c-189">依序展開**平台設定**，然後按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-189">Expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="8f69c-190">以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="8f69c-190">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  

    <span data-ttu-id="8f69c-191">請繼續進行[步驟 3： 測試中的批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="8f69c-191">Proceed to [Step 3: Test the Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).</span></span>