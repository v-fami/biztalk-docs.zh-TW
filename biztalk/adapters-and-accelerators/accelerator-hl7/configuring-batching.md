---
title: "設定批次處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, configuring
- configuring, batching
ms.assetid: 33c72d5e-31dd-44a8-8418-1faab3239e8e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9ab9ead01273e54826db670e7e6d6a2e9af6200
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching"></a><span data-ttu-id="b639c-102">設定批次處理</span><span class="sxs-lookup"><span data-stu-id="b639c-102">Configuring Batching</span></span>
<span data-ttu-id="b639c-103">您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]Configuration 總管來建立批次，在批次 / 出批次處理，並選取可用的結構描述的輸出批次的批次。</span><span class="sxs-lookup"><span data-stu-id="b639c-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to create batch, batch in/batch out batching, and to select available schemas for outbound batching.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b639c-104">您必須設定交易夥伴使用 BizTalk 總管 中，才可以設定訊息批次。</span><span class="sxs-lookup"><span data-stu-id="b639c-104">You must configure trading partners using BizTalk Explorer before you can configure message batching.</span></span>  
  
 <span data-ttu-id="b639c-105">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**批次定義** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b639c-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Definition** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")  
  
 <span data-ttu-id="b639c-106">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管，並設定批次。</span><span class="sxs-lookup"><span data-stu-id="b639c-106">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure batching.</span></span>  
  
### <a name="to-enable-message-batching-for-outbound-batching-create-batch"></a><span data-ttu-id="b639c-107">若要啟用訊息批次處理為輸出批次處理 （建立批次）</span><span class="sxs-lookup"><span data-stu-id="b639c-107">To enable message batching for outbound batching (Create Batch)</span></span>  
  
1.  <span data-ttu-id="b639c-108">在**啟動**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b639c-108">In the **Start** menu, open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b639c-109">在管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="b639c-109">In the Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="b639c-110">按一下**協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b639c-110">Click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="b639c-111">在 [協調流程屬性] 對話方塊中，按一下**繫結**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="b639c-111">In the Orchestration Properties dialog box, click **Bindings** in the console tree.</span></span>  
  
5.  <span data-ttu-id="b639c-112">在**繫結** 窗格中，選取適當的主機，如**主機**。</span><span class="sxs-lookup"><span data-stu-id="b639c-112">In the **Bindings** pane, select the appropriate host for **Host**.</span></span> <span data-ttu-id="b639c-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b639c-113">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="b639c-114">以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**登錄**。</span><span class="sxs-lookup"><span data-stu-id="b639c-114">Right-click **BatchOrchestration.Orchestration_1**, and then select **Enlist**.</span></span>  
  
7.  <span data-ttu-id="b639c-115">以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="b639c-115">Right-click **BatchOrchestration.Orchestration_1**, and then select **Start**.</span></span>  
  
### <a name="to-run-btahl7-configuration-explorer"></a><span data-ttu-id="b639c-116">若要執行 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="b639c-116">To run BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="b639c-117">在**啟動**功能表中，開啟**Microsoft BizTalk Accelerator for HL7** ，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="b639c-117">In the **Start** menu, open **Microsoft BizTalk Accelerator for HL7** , and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-configure-batching"></a><span data-ttu-id="b639c-118">若要設定批次處理</span><span class="sxs-lookup"><span data-stu-id="b639c-118">To configure batching</span></span>  
  
-   <span data-ttu-id="b639c-119">在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管，請在**BTAHL7 Configuration 總管**對話方塊**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**批次定義**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b639c-119">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Definition** tab, do the following:</span></span>  
  
    |<span data-ttu-id="b639c-120">使用</span><span class="sxs-lookup"><span data-stu-id="b639c-120">Use this</span></span>|<span data-ttu-id="b639c-121">動作</span><span class="sxs-lookup"><span data-stu-id="b639c-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b639c-122">**所需的片段**</span><span class="sxs-lookup"><span data-stu-id="b639c-122">**Fragmentation required**</span></span>|<span data-ttu-id="b639c-123">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="b639c-123">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="b639c-124">-   **[是]**。</span><span class="sxs-lookup"><span data-stu-id="b639c-124">-   **Yes**.</span></span> <span data-ttu-id="b639c-125">若要啟用片段。</span><span class="sxs-lookup"><span data-stu-id="b639c-125">To enable fragmentation.</span></span><br /><span data-ttu-id="b639c-126">-   **否**。</span><span class="sxs-lookup"><span data-stu-id="b639c-126">-   **No**.</span></span> <span data-ttu-id="b639c-127">若要停用片段。</span><span class="sxs-lookup"><span data-stu-id="b639c-127">To disable fragmentation.</span></span> <span data-ttu-id="b639c-128">**注意：**新合作對象，**片段所需**預設為**否**。</span><span class="sxs-lookup"><span data-stu-id="b639c-128">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>|  
    |<span data-ttu-id="b639c-129">**選取訊息**</span><span class="sxs-lookup"><span data-stu-id="b639c-129">**Select Messages**</span></span>|<span data-ttu-id="b639c-130">選取您想要以從批次傳送的訊息類型**可用訊息**視窗中，然後按一下 向右箭號來移動 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="b639c-130">Select the message types you want to send as a batch from the **Available Messages** window, and then click the Move to the right arrow (**>>**).</span></span>|  
    |<span data-ttu-id="b639c-131">**選取訊息通知**</span><span class="sxs-lookup"><span data-stu-id="b639c-131">**Select Message Acknowledgments**</span></span>|<span data-ttu-id="b639c-132">選取您想要以從批次傳送通知的訊息類型**可用訊息 Ack**視窗中，然後按一下 向右移動 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="b639c-132">Select the message types for which you want the acknowledgments to send as a batch from the **Available Message Acks** window, and then click the Move to the right (**>>**).</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b639c-133">您可能不會看到您加入的結構描述您在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]專案中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管正在執行。</span><span class="sxs-lookup"><span data-stu-id="b639c-133">You may not see schemas that you add to your In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] project while In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer is running.</span></span> <span data-ttu-id="b639c-134">若要檢視這些檔案，您可能需要重新啟動在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="b639c-134">In order to view these files, you may need to restart In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b639c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b639c-135">See Also</span></span>  
 [<span data-ttu-id="b639c-136">排程批次</span><span class="sxs-lookup"><span data-stu-id="b639c-136">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)