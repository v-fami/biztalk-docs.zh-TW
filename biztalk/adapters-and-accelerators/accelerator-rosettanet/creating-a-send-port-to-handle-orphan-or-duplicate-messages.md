---
title: "建立傳送埠，以便處理遭遺棄或重複的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, duplicate messages
- messages, orphaned messages
- send ports, duplicate messages
- send ports, orphaned messages
- messages, send ports
ms.assetid: 61d51206-13e3-4d32-a184-866248db9b45
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9a5e52197c81e86bac69603e72d294cfbcd6faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-send-port-to-handle-orphan-or-duplicate-messages"></a><span data-ttu-id="406cd-102">建立傳送埠，以便處理遭遺棄或重複的訊息</span><span class="sxs-lookup"><span data-stu-id="406cd-102">Creating a Send Port to Handle Orphan or Duplicate Messages</span></span>
<span data-ttu-id="406cd-103">本主題說明如何設定傳送埠，讓您可以用來刪除遭遺棄或重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="406cd-103">This topic describes how to set up a send port that you can use to delete orphan or duplicate messages.</span></span>  
  
 <span data-ttu-id="406cd-104">遭遺棄或重複的訊息可能會產生問題如果[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]公開程序協調流程完成處理訊息的第一個複本之後，接收訊息的額外複本。</span><span class="sxs-lookup"><span data-stu-id="406cd-104">Orphan or duplicate messages can be a problem if [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receives additional copies of a message after the public-process orchestration has completed processing the first copy of the message.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="406cd-105">將這些訊息標示為重複項目，並加以擱置。</span><span class="sxs-lookup"><span data-stu-id="406cd-105"> marks those messages as duplicates and suspends them.</span></span> <span data-ttu-id="406cd-106">您可以在 BizTalk 管理主控台中檢視這些訊息。</span><span class="sxs-lookup"><span data-stu-id="406cd-106">You can view these messages in the BizTalk Administration Console.</span></span> <span data-ttu-id="406cd-107">如需有關 BizTalk 管理主控台的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜使用 BizTalk 管理主控台＞一節。</span><span class="sxs-lookup"><span data-stu-id="406cd-107">For more information about BizTalk Administration Console, see "Using the BizTalk Administration Console" in the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="406cd-108">除非您檢閱或刪除這些遭遺棄或重複的訊息，否則它們會持續存在於 BizTalk 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="406cd-108">Orphan or duplicate messages remain in the BizTalk Administration Console until you review or delete them.</span></span> <span data-ttu-id="406cd-109">刪除它們最有效的方式，就是設定具有篩選遭遺棄或重複訊息功能的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="406cd-109">The most effective way of deleting them is to set up a send port with filters set for orphan or duplicate messages.</span></span> <span data-ttu-id="406cd-110">您可以使用 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 中任何可用的傳輸方式，移動這些訊息。</span><span class="sxs-lookup"><span data-stu-id="406cd-110">You can move them using any transportation means available in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="406cd-111">例如，您可以移動它們使用的檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="406cd-111">For example, you can move them by using File transport.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="406cd-112">會以檔案遭遺棄或重複的訊息傳送到硬碟上的位置。</span><span class="sxs-lookup"><span data-stu-id="406cd-112"> sends the orphan or duplicate messages as files to a location on a hard disk.</span></span> <span data-ttu-id="406cd-113">如此便可以輕易將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="406cd-113">This lets you to delete them easily.</span></span> <span data-ttu-id="406cd-114">這個連接埠可以是登錄或停止的狀態，在這種情況下，所有傳送至這個連接埠的訊息都將會在這個傳送埠下方，顯示為遭擱置的狀態。</span><span class="sxs-lookup"><span data-stu-id="406cd-114">The port can be in the enlisted and stopped state, in which case all messages sent to it will show as suspended under that send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="406cd-115">您可以建立特殊的管線元件，從 MessageBox 資料庫刪除這些訊息，而不用建立傳送埠來處理重複/遭遺棄的訊息。</span><span class="sxs-lookup"><span data-stu-id="406cd-115">Instead of creating a send port to handle duplicate/orphan messages, you can create a special pipeline component to delete these messages from the MessageBox database.</span></span> <span data-ttu-id="406cd-116">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK 中的 FixMsg 元件做為範本。</span><span class="sxs-lookup"><span data-stu-id="406cd-116">You can use the FixMsg component in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK as a template.</span></span> <span data-ttu-id="406cd-117">但必須修改 `IComponent.Execute` 方法，才能傳回 null。</span><span class="sxs-lookup"><span data-stu-id="406cd-117">You have to modify the `IComponent.Execute` method to return null.</span></span> <span data-ttu-id="406cd-118">這便會導致 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 捨棄任何傳送至含有該元件之管線的訊息。</span><span class="sxs-lookup"><span data-stu-id="406cd-118">This causes [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to discard any message sent to a pipeline that contains the component.</span></span> <span data-ttu-id="406cd-119">因此必須要編譯這個管線元件，並將它加入傳送管線，然後再編譯、部署以及選取這個接受埠的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="406cd-119">You have to compile this pipeline component and add it to a send pipeline, and then compile, deploy, and select the send pipeline for the sink port.</span></span> <span data-ttu-id="406cd-120">如需詳細資訊，請參閱「[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 說明」中的＜CustomComponent ([!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 範例)＞一節。</span><span class="sxs-lookup"><span data-stu-id="406cd-120">For more information, see "CustomComponent ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Sample)" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
### <a name="to-create-a-send-port-to-handle-orphan-or-duplicate-messages"></a><span data-ttu-id="406cd-121">建立傳送埠，處理遭遺棄或重複的訊息</span><span class="sxs-lookup"><span data-stu-id="406cd-121">To create a send port to handle orphan or duplicate messages</span></span>  
  
1.  <span data-ttu-id="406cd-122">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="406cd-122">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **View** menu, click **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="406cd-123">在 [BizTalk 總管] 中，展開**BizTalk 管理資料庫**，然後展開**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="406cd-123">In BizTalk Explorer, expand **BizTalk Management Database**, and then expand **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="406cd-124">以滑鼠右鍵按一下**傳送埠**，然後按一下 **新增傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="406cd-124">Right-click **Send Ports**, and then click **Add Send Port**.</span></span>  
  
4.  <span data-ttu-id="406cd-125">在 建立新傳送埠 視窗中，選取**靜態單向連接埠**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="406cd-125">In the Create New Send Port window, select **Static One-Way Port**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="406cd-126">在 [靜態單向傳送埠屬性] 視窗中**名稱**方塊中，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="406cd-126">In the Static One-Way Send Port Properties window, in the **Name** box, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="406cd-127">在左窗格中，按一下 **傳輸**。</span><span class="sxs-lookup"><span data-stu-id="406cd-127">In the left pane, click **Transport**.</span></span> <span data-ttu-id="406cd-128">在右窗格中，按一下 **傳輸類型**，然後選取**檔案**做為傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="406cd-128">In the right pane, click **Transport Type**, and select **FILE** for the transport type.</span></span> <span data-ttu-id="406cd-129">按一下旁邊的省略符號按鈕 （...）**位址 (URI)**，輸入您的硬碟上的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="406cd-129">Click the ellipsis button (...) next to **Address (URI)**, type a location on your hard disk, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="406cd-130">在左窗格中，按一下 **傳送**，按一下 **傳送管線**，然後選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="406cd-130">In the left pane, click **Send**, click **Send Pipeline**, and then select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
8.  <span data-ttu-id="406cd-131">在左窗格中，按一下 **篩選，並將對應**，然後按一下 **篩選**。</span><span class="sxs-lookup"><span data-stu-id="406cd-131">In the left pane, click **Filters and Maps**, and then click **Filters**.</span></span>  
  
9. <span data-ttu-id="406cd-132">在右窗格中的第一行的**屬性**，選取**Microsoft.Solutions.BTARN.GlobalSchemas.IsDuplicateMessage**從下拉式清單中，保留**運算子**為 **==** ，輸入**True**的**值**，然後選取**或**的下拉式清單**群組**。</span><span class="sxs-lookup"><span data-stu-id="406cd-132">On the first line in the right pane, for **Property**, select **Microsoft.Solutions.BTARN.GlobalSchemas.IsDuplicateMessage** from the drop-down list, leave the **Operator** as **==**, enter **True** for **Value**, and then select **Or** from the drop-down list for **Group**.</span></span>  
  
10. <span data-ttu-id="406cd-133">在右窗格中，在第二行如**屬性**，選取**Microsoft.Solutions.BTARN.GlobalSchemas.IsOrphanMessage**從下拉式清單中，保留**運算子**為 **==** ，然後輸入**True**如**值**。</span><span class="sxs-lookup"><span data-stu-id="406cd-133">On the second line in the right pane, for **Property**, select **Microsoft.Solutions.BTARN.GlobalSchemas.IsOrphanMessage** from the drop-down list, leave the **Operator** as **==**, and then enter **True** for **Value**.</span></span>  
  
11. <span data-ttu-id="406cd-134">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="406cd-134">Click **OK**.</span></span>  
  
12. <span data-ttu-id="406cd-135">在 [BizTalk 總管] 中，以滑鼠右鍵按一下傳送埠的名稱，請按一下**登錄**。</span><span class="sxs-lookup"><span data-stu-id="406cd-135">In BizTalk Explorer, right-click the name of the send port, click **Enlist**.</span></span> <span data-ttu-id="406cd-136">已經登錄傳送埠之後，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="406cd-136">After the send port has been enlisted, right-click the send port, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406cd-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="406cd-137">See Also</span></span>  
 [<span data-ttu-id="406cd-138">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="406cd-138">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)