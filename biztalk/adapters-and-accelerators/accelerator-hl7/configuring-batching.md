---
title: 設定批次處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, configuring
- configuring, batching
ms.assetid: 33c72d5e-31dd-44a8-8418-1faab3239e8e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ea79c4b96ac54e6b2d1eed281b60a261ca5cc1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976327"
---
# <a name="configuring-batching"></a><span data-ttu-id="a85cb-102">設定批次處理</span><span class="sxs-lookup"><span data-stu-id="a85cb-102">Configuring Batching</span></span>
<span data-ttu-id="a85cb-103">您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]組態總管來建立批次，批次中 / 出批次處理，，和選取可用的結構描述的輸出批次的批次。</span><span class="sxs-lookup"><span data-stu-id="a85cb-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to create batch, batch in/batch out batching, and to select available schemas for outbound batching.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a85cb-104">您必須設定使用 BizTalk 總管 中，您可設定訊息批次處理的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="a85cb-104">You must configure trading partners using BizTalk Explorer before you can configure message batching.</span></span>  
  
 <span data-ttu-id="a85cb-105">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管**批次定義** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a85cb-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Definition** tab.</span></span>  
  
 <span data-ttu-id="a85cb-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")</span><span class="sxs-lookup"><span data-stu-id="a85cb-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")</span></span>  
  
 <span data-ttu-id="a85cb-107">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，並設定批次。</span><span class="sxs-lookup"><span data-stu-id="a85cb-107">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure batching.</span></span>  
  
### <a name="to-enable-message-batching-for-outbound-batching-create-batch"></a><span data-ttu-id="a85cb-108">若要啟用輸出批次處理 （建立批次） 的訊息批次處理</span><span class="sxs-lookup"><span data-stu-id="a85cb-108">To enable message batching for outbound batching (Create Batch)</span></span>  
  
1.  <span data-ttu-id="a85cb-109">在 **開始**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-109">In the **Start** menu, open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a85cb-110">在管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-110">In the Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="a85cb-111">按一下 **協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-111">Click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="a85cb-112">在 [協調流程屬性] 對話方塊中，按一下**繫結**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="a85cb-112">In the Orchestration Properties dialog box, click **Bindings** in the console tree.</span></span>  
  
5.  <span data-ttu-id="a85cb-113">在 **繫結**窗格中，選取適當的主機，如**主機**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-113">In the **Bindings** pane, select the appropriate host for **Host**.</span></span> <span data-ttu-id="a85cb-114">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="a85cb-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="a85cb-115">以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**登錄**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-115">Right-click **BatchOrchestration.Orchestration_1**, and then select **Enlist**.</span></span>  
  
7.  <span data-ttu-id="a85cb-116">以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**開始**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-116">Right-click **BatchOrchestration.Orchestration_1**, and then select **Start**.</span></span>  
  
### <a name="to-run-btahl7-configuration-explorer"></a><span data-ttu-id="a85cb-117">若要執行 BTAHL7 設定總管</span><span class="sxs-lookup"><span data-stu-id="a85cb-117">To run BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="a85cb-118">在 **開始**功能表中，開啟**Microsoft BizTalk Accelerator for HL7** ，然後按一下**BTAHL7 設定總管**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-118">In the **Start** menu, open **Microsoft BizTalk Accelerator for HL7** , and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-configure-batching"></a><span data-ttu-id="a85cb-119">若要設定批次處理</span><span class="sxs-lookup"><span data-stu-id="a85cb-119">To configure batching</span></span>  
  
- <span data-ttu-id="a85cb-120">在 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，請在**BTAHL7 設定總管**對話方塊的 **合作對象**索引標籤上，選取您想要設定合作對的象，然後在**批次定義**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a85cb-120">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Definition** tab, do the following:</span></span>  
  
  |<span data-ttu-id="a85cb-121">使用</span><span class="sxs-lookup"><span data-stu-id="a85cb-121">Use this</span></span>|<span data-ttu-id="a85cb-122">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a85cb-122">To do this</span></span>|  
  |--------------|----------------|  
  |<span data-ttu-id="a85cb-123">**需要的片段**</span><span class="sxs-lookup"><span data-stu-id="a85cb-123">**Fragmentation required**</span></span>|<span data-ttu-id="a85cb-124">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="a85cb-124">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="a85cb-125">-   **是**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-125">-   **Yes**.</span></span> <span data-ttu-id="a85cb-126">若要啟用片段。</span><span class="sxs-lookup"><span data-stu-id="a85cb-126">To enable fragmentation.</span></span><br /><span data-ttu-id="a85cb-127">-   **否**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-127">-   **No**.</span></span> <span data-ttu-id="a85cb-128">若要停用片段。</span><span class="sxs-lookup"><span data-stu-id="a85cb-128">To disable fragmentation.</span></span> <span data-ttu-id="a85cb-129">**附註：** 新的合作對象**所需的分散程度**預設為**否**。</span><span class="sxs-lookup"><span data-stu-id="a85cb-129">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>|  
  |<span data-ttu-id="a85cb-130">**選取訊息**</span><span class="sxs-lookup"><span data-stu-id="a85cb-130">**Select Messages**</span></span>|<span data-ttu-id="a85cb-131">選取您想要從以批次傳送的訊息類型**可用的訊息** 視窗中，然後按一下 移至 向右箭號 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="a85cb-131">Select the message types you want to send as a batch from the **Available Messages** window, and then click the Move to the right arrow (**>>**).</span></span>|  
  |<span data-ttu-id="a85cb-132">**選取訊息通知**</span><span class="sxs-lookup"><span data-stu-id="a85cb-132">**Select Message Acknowledgments**</span></span>|<span data-ttu-id="a85cb-133">選取您想要從以批次傳送通知的訊息類型**可用的訊息 Ack** ] 視窗中，然後按一下 [向右移動 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="a85cb-133">Select the message types for which you want the acknowledgments to send as a batch from the **Available Message Acks** window, and then click the Move to the right (**>>**).</span></span>|  
  
  > [!NOTE]
  >  <span data-ttu-id="a85cb-134">您可能不會看到您加入的結構描述您在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]專案中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管正在執行。</span><span class="sxs-lookup"><span data-stu-id="a85cb-134">You may not see schemas that you add to your In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] project while In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer is running.</span></span> <span data-ttu-id="a85cb-135">若要檢視這些檔案，您可能需要重新啟動[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="a85cb-135">In order to view these files, you may need to restart In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85cb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a85cb-136">See Also</span></span>  
 [<span data-ttu-id="a85cb-137">排程批次處理</span><span class="sxs-lookup"><span data-stu-id="a85cb-137">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)