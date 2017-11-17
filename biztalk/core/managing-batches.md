---
title: "管理批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82755840-4e00-4fed-80e0-1a22b248c0bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4903cf2722f1938ceb1df92c2a3ac2a88fe6d61e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-batches"></a><span data-ttu-id="b7779-102">管理批次</span><span class="sxs-lookup"><span data-stu-id="b7779-102">Managing Batches</span></span>
<span data-ttu-id="b7779-103">如何手動控制版本的批次交換，在頂端使用的控制項**批次組態**單向協議索引標籤的頁面**協議屬性**對話方塊 (在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台) X12 和 EDIFACT 編碼的。</span><span class="sxs-lookup"><span data-stu-id="b7779-103">How to control manually the release of batched interchanges, using the controls at the top of the **Batch Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box (in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console) for both X12 and EDIFACT encoding.</span></span> <span data-ttu-id="b7779-104">這項控制與下列控制項有關：</span><span class="sxs-lookup"><span data-stu-id="b7779-104">This involves the following controls:</span></span>  
  
-   <span data-ttu-id="b7779-105">**啟動批次**。</span><span class="sxs-lookup"><span data-stu-id="b7779-105">**Starting a batch**.</span></span> <span data-ttu-id="b7779-106">啟動批次處理協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7779-106">Activates an instance of the batching orchestration.</span></span> <span data-ttu-id="b7779-107">選取後**啟動**批次處理項目 按鈕，在啟動範圍內的執行個體時所收集。</span><span class="sxs-lookup"><span data-stu-id="b7779-107">After you select the **Start** button, batching elements are collected when the instance is within the activation range.</span></span>  
  
-   <span data-ttu-id="b7779-108">**覆寫批次**。</span><span class="sxs-lookup"><span data-stu-id="b7779-108">**Overriding a batch**.</span></span> <span data-ttu-id="b7779-109">建立批次使用現有的項目，並立即傳送。</span><span class="sxs-lookup"><span data-stu-id="b7779-109">Creates a batch using existing elements and immediately sends it.</span></span> <span data-ttu-id="b7779-110">在批次完成傳送之後，批次處理協調流程就會依據已建立的設定，繼續進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="b7779-110">After the batch is sent, the batching orchestration resumes batch processing according to the established settings.</span></span>  
  
-   <span data-ttu-id="b7779-111">**停止批次**。</span><span class="sxs-lookup"><span data-stu-id="b7779-111">**Stopping a batch**.</span></span> <span data-ttu-id="b7779-112">停用批次處理協調流程已啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7779-112">Deactivates an activated instance of the batching orchestration.</span></span> <span data-ttu-id="b7779-113">選取後**停止** 按鈕，協調流程從現有的批次元素建立批次，將交換傳遞給 EDI 傳送管線，而會結束。</span><span class="sxs-lookup"><span data-stu-id="b7779-113">After you select the **Stop** button, the orchestration creates a batch from existing batch elements, delivers the interchange to the EDI send pipeline, and terminates.</span></span>  
  
 <span data-ttu-id="b7779-114">控制項作用於單一批次組態。</span><span class="sxs-lookup"><span data-stu-id="b7779-114">The controls act upon a single batch configuration.</span></span>  
  
 <span data-ttu-id="b7779-115">當您按下，BizTalk 所採取的動作**啟動**取決於按鈕**篩選**準則，**發行**準則，並**啟用**範圍上設定**批次組態**頁面。</span><span class="sxs-lookup"><span data-stu-id="b7779-115">The actions that BizTalk takes when you press the **Start** button depend upon the **Filter** criteria, **Release** criteria, and **Activation** range settings on the **Batch Configuration** page.</span></span> <span data-ttu-id="b7779-116">篩選準則決定哪些訊息要批次處理。</span><span class="sxs-lookup"><span data-stu-id="b7779-116">The filter criteria determine which messages are batched.</span></span> <span data-ttu-id="b7779-117">釋放準則決定何時要釋放批次。</span><span class="sxs-lookup"><span data-stu-id="b7779-117">The release criteria determine when batches are released.</span></span> <span data-ttu-id="b7779-118">啟動範圍屬性則決定已啟動的批次處理協調流程執行個體是否會收集批次處理項目。</span><span class="sxs-lookup"><span data-stu-id="b7779-118">The activation range properties determine whether an activated instance of the batching orchestration will collect elements for batching.</span></span> <span data-ttu-id="b7779-119">如需有關這些設定的詳細資訊，請參閱[設定外寄批次](../core/configuring-an-outgoing-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="b7779-119">For more information about these settings, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).</span></span>  

<span data-ttu-id="b7779-120">本主題說明如何啟動、 停止、 覆寫，以及刪除批次。</span><span class="sxs-lookup"><span data-stu-id="b7779-120">This topic shows you how to start, stop, override, and delete batches.</span></span>  

> [!NOTE]
>  <span data-ttu-id="b7779-121">如需如何設定批次的指示，請參閱[設定 X12 批次處理](../core/configuring-batching-x12.md)或[設定 EDIFACT 批次處理](../core/configuring-batching-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="b7779-121">For instructions on how to configure batches, see [Configuring X12 Batching](../core/configuring-batching-x12.md) or [Configuring EDIFACT Batching](../core/configuring-batching-edifact.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="b7779-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="b7779-122">Prerequisites</span></span>  
 <span data-ttu-id="b7779-123">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="b7779-123">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7779-124">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員群組的成員可以啟動、停止或覆寫批次，但無法變更任何與批次處理相關的組態設定。</span><span class="sxs-lookup"><span data-stu-id="b7779-124">A member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group can start, stop, or override a batch, but cannot change any configuration setting related to batching.</span></span> <span data-ttu-id="b7779-125">您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]變更批次組態的系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="b7779-125">You must be a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to change batch configuration.</span></span>  
  
## <a name="start-stop-and-override-batches"></a><span data-ttu-id="b7779-126">啟動、 停止及覆寫批次</span><span class="sxs-lookup"><span data-stu-id="b7779-126">Start, stop, and override batches</span></span>  
  
1.  <span data-ttu-id="b7779-127">開啟**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**，展開 [BizTalk 群組] 並選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="b7779-127">Open **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand the BizTalk group, and select **Parties**.</span></span>  
  
2.  <span data-ttu-id="b7779-128">在**合作對象與商務設定檔**頁面的 **協議**區段中，以滑鼠右鍵按一下您想要啟動、 停止或覆寫批次組態的協議。</span><span class="sxs-lookup"><span data-stu-id="b7779-128">In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to start, stop, or override.</span></span>  
  
3.  <span data-ttu-id="b7779-129">在單向協議索引標籤的**協議屬性**，選取**批次組態**頁面。</span><span class="sxs-lookup"><span data-stu-id="b7779-129">In the one-way agreement tab of the **Agreement Properties**, select the **Batch Configuration** page.</span></span>  
  
4.  <span data-ttu-id="b7779-130">在**批次組態**頁面上，選取您想要啟動、 停止或覆寫批次的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7779-130">On the **Batch Configuration** page, select the tab for the batch that you want to start, stop, or override.</span></span>  
  
5.  <span data-ttu-id="b7779-131">確認篩選準則、釋放準則和啟動範圍屬性符合所需要的設定。</span><span class="sxs-lookup"><span data-stu-id="b7779-131">Verify that the filter criteria, release criteria, and activation range properties are as they should be.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7779-132">如果您隸屬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作員群組，但不是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，您可以啟動、 停止或覆寫批次。</span><span class="sxs-lookup"><span data-stu-id="b7779-132">If you are a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, but not the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group, you can start, stop, or override batches.</span></span> <span data-ttu-id="b7779-133">但是，您無法變更批次組態設定。</span><span class="sxs-lookup"><span data-stu-id="b7779-133">But, you cannot change batch configuration settings.</span></span> <span data-ttu-id="b7779-134">設定為可見，但如果您變更設定，然後再選取**確定**，取得權限錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7779-134">The settings are visible to you, but if you change a setting, and then select **OK**, you get a permissions error.</span></span>  
  
6.  <span data-ttu-id="b7779-135">如果尚未啟動批次處理協調流程執行個體，請選取**啟動**來啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7779-135">If an instance of the batching orchestration has not been activated, select **Start** to activate an instance.</span></span>  
  
    > [!NOTE]
    >  - <span data-ttu-id="b7779-136">您所見，批次處理協調流程執行個體尚未啟動是否**啟動**啟用按鈕時，和**批次處理未啟動**下方顯示**啟動**控制項。</span><span class="sxs-lookup"><span data-stu-id="b7779-136">You can tell that an instance of the batching orchestration has not been activated if the **Start** button is enabled, and **Batching is not activated** is displayed just beneath the **Start** control.</span></span>  
    >  - <span data-ttu-id="b7779-137">如果您已按下**啟動**按鈕，並已啟動批次處理協調流程執行個體，但是批次收集任何項目，然後確認中的 datetime**啟用**發生文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b7779-137">If you have clicked the **Start** button, and an instance of the batching orchestration has been activated, but no elements are being collected for the batch, then verify that the datetime in the **Activation** text box has transpired.</span></span> <span data-ttu-id="b7779-138">如果沒有，則**啟用**日期必須設定為目前的日期或更早版本。</span><span class="sxs-lookup"><span data-stu-id="b7779-138">If not, the **Activation** date must be set to the current date or earlier.</span></span>  
  
7.  <span data-ttu-id="b7779-139">若要傳送的批次的交換，不符合釋放準則時，請選取**覆寫**。</span><span class="sxs-lookup"><span data-stu-id="b7779-139">To send a batched interchange when the release criteria have not been met, select **Override**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7779-140">選取**覆寫**會導致批次的交換進行傳送，但不會影響批次處理協調流程執行個體、 啟動準則或釋放準則的啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="b7779-140">Selecting **Override** results in a batched interchange being sent, but does not affect the activation status of the batching orchestration instance, the activation criteria, or the release criteria.</span></span>  
  
8.  <span data-ttu-id="b7779-141">若要停用批次處理協調流程的執行個體，請選取**停止**。</span><span class="sxs-lookup"><span data-stu-id="b7779-141">To deactivate the instance of the batching orchestration, select **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7779-142">選取**停止**導致批次的交換進行傳送，且正在終止批次處理協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7779-142">Selecting **Stop** results in a batched interchange being sent, and the batching orchestration instance being terminated.</span></span>  
  
9. <span data-ttu-id="b7779-143">選取**確定**或**取消**關閉**協議屬性**。</span><span class="sxs-lookup"><span data-stu-id="b7779-143">Select **OK** or **Cancel** to close the **Agreement Properties**.</span></span>  

## <a name="delete-batches"></a><span data-ttu-id="b7779-144">刪除批次</span><span class="sxs-lookup"><span data-stu-id="b7779-144">Delete batches</span></span>  
  
1.  <span data-ttu-id="b7779-145">在**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="b7779-145">In **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, select **Parties**.</span></span>  
  
2.  <span data-ttu-id="b7779-146">在**合作對象與商務設定檔**頁面的 **協議**區段中，以滑鼠右鍵按一下您想要刪除的批次組態的協議。</span><span class="sxs-lookup"><span data-stu-id="b7779-146">In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to delete.</span></span>  
  
3.  <span data-ttu-id="b7779-147">在單向協議索引標籤的**協議屬性**對話方塊中，選取**批次組態**頁面。</span><span class="sxs-lookup"><span data-stu-id="b7779-147">In the one-way agreement tab of the **Agreement Properties** dialog box, select the **Batch Configuration** page.</span></span>  
  
4.  <span data-ttu-id="b7779-148">在**批次組態**頁面上，選取您想要刪除的批次的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7779-148">On the **Batch Configuration** page, select the tab for the batch that you want to delete.</span></span>  
  
5.  <span data-ttu-id="b7779-149">在索引標籤頁面右上角，選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="b7779-149">On the right-hand corner of the tab page, select **Delete**.</span></span>  
  
6.  <span data-ttu-id="b7779-150">選取**確定**關閉**協議屬性**。</span><span class="sxs-lookup"><span data-stu-id="b7779-150">Select **OK** to close the **Agreement Properties**.</span></span>  

  
## <a name="see-also"></a><span data-ttu-id="b7779-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7779-151">See Also</span></span>  
 [<span data-ttu-id="b7779-152">設定外寄批次</span><span class="sxs-lookup"><span data-stu-id="b7779-152">Configuring an Outgoing Batch</span></span>](../core/configuring-an-outgoing-batch.md)  
 [<span data-ttu-id="b7779-153">管理 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="b7779-153">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)