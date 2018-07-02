---
title: 第 3 部分： 建立批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, creating
- creating, batching
ms.assetid: 02247186-5b21-4738-9110-f0ca0304f0fd
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e487bfbe29ee2a34f2e50affa502d7f20592fe0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975951"
---
# <a name="part-3-create-batch-scenario"></a><span data-ttu-id="27485-102">第 3 部分： 建立批次案例</span><span class="sxs-lookup"><span data-stu-id="27485-102">Part 3: Create-Batch Scenario</span></span>
<span data-ttu-id="27485-103">在案例的這個部分，您可以收到兩個內送訊息、 將它們結合為批次的訊息，和批次傳送至目的地。</span><span class="sxs-lookup"><span data-stu-id="27485-103">In this part of the scenario, you receive two incoming messages, combine them into a batched message, and send the batch to a destination.</span></span> <span data-ttu-id="27485-104">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會傳回包含兩個通知產生來源來自目的地的訊息通知批次。</span><span class="sxs-lookup"><span data-stu-id="27485-104">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) returns an acknowledgment batch containing the two acknowledgments generated for the messages from the destination to the source.</span></span> <span data-ttu-id="27485-105">下圖顯示本教學課程的這個部分的處理流程。</span><span class="sxs-lookup"><span data-stu-id="27485-105">The following figure shows the process flow of this part of the tutorial.</span></span>  
  
 <span data-ttu-id="27485-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-create-batch-scenario.gif "hl7_create_batch_scenario")</span><span class="sxs-lookup"><span data-stu-id="27485-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-create-batch-scenario.gif "hl7_create_batch_scenario")</span></span>  
  
 <span data-ttu-id="27485-107">**在建立批次的案例中的訊息如何流動**</span><span class="sxs-lookup"><span data-stu-id="27485-107">**How messages flow in the Create-Batch scenario**</span></span>  
  
 <span data-ttu-id="27485-108">此案例包含下列工作流程：</span><span class="sxs-lookup"><span data-stu-id="27485-108">This scenario includes the following workflow:</span></span>  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="27485-109"> 設陷符合 MessageBox 資料庫中的批次定義的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="27485-109"> traps all messages conforming to the batch definition in the MessageBox database.</span></span> <span data-ttu-id="27485-110">您輸入在此定義**批次定義**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="27485-110">You enter this definition in the **Batch Definition** tab of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span> <span data-ttu-id="27485-111">在本教學課程中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會設陷，並會批次處理所有訊息傳送至 Tutorial_BatchDest ADT 的結構描述與 ^ 將 adt^a03，和所有通知傳送到 ADT 由於 Tutorial_BatchSource ^ adt^a03 訊息。</span><span class="sxs-lookup"><span data-stu-id="27485-111">In this tutorial, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will trap and batch all messages to be sent to Tutorial_BatchDest with a schema of ADT^A03, and all acknowledgments to be sent to Tutorial_BatchSource as a result of ADT^A03 messages.</span></span>  
  
- <span data-ttu-id="27485-112">排程批次傳送時間時，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次的控制訊息觸發輸出批次交易。</span><span class="sxs-lookup"><span data-stu-id="27485-112">When the scheduled batch send time occurs, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends a batch control message that triggers the outbound batch transaction.</span></span> <span data-ttu-id="27485-113">您定義排程**批次排程**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="27485-113">You define the schedule on the **Batch Schedule** tab of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span> <span data-ttu-id="27485-114">您也可以按一下 觸發程序**立即傳送**相同的索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="27485-114">You can also trigger the process by clicking **Send Now** on the same tab.</span></span>  
  
- <span data-ttu-id="27485-115">批次協調流程會形成超出受困於 MessageBox 資料庫的訊息的訊息批次。</span><span class="sxs-lookup"><span data-stu-id="27485-115">The batch orchestration forms the message batch out of the messages trapped in the MessageBox database.</span></span> <span data-ttu-id="27485-116">協調流程也會包裝檔案標頭和結尾和批次標頭和結尾中的批次。</span><span class="sxs-lookup"><span data-stu-id="27485-116">The orchestration also wraps the batch in a file header and trailer, and a batch header and trailer.</span></span> <span data-ttu-id="27485-117">此協調流程就是原生[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]協調流程加入[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]到 BizTalk 協調流程，因此它會列在 [BizTalk 總管或 BizTalk Server 管理主控台中的協調流程] 節點下的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="27485-117">This orchestration is a native [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration added by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup to your set of BizTalk orchestrations, so it is listed under the Orchestrations node in BizTalk Explorer or the BizTalk Server Administration Console.</span></span>  
  
- <span data-ttu-id="27485-118">如果是針對來源合作對象所定義的通知 （如它們在此情況下是針對 Tutorial_BatchSource），BizTalk 會批次處理通知 （至 \Tutorial_BatchACKDrop 資料夾中） 將它們傳回批次中。</span><span class="sxs-lookup"><span data-stu-id="27485-118">If acknowledgments are defined for the source party (as they are in this case for Tutorial_BatchSource), BizTalk batches the acknowledgments and returns them in a batch (to the \Tutorial_BatchACKDrop folder).</span></span> <span data-ttu-id="27485-119">在本教學課程中，批次的通知會傳送在短暫延遲之後。</span><span class="sxs-lookup"><span data-stu-id="27485-119">In this tutorial, the batched acknowledgments are sent after a short delay.</span></span>  
  
- <span data-ttu-id="27485-120">協調流程會將訊息路由至傳送埠 (Tutorial_BatchDest)，以將批次的訊息傳送到目的地 （在此情況下，您硬碟機上的 [\Tutorial_BatchMsgDrop] 資料夾）。</span><span class="sxs-lookup"><span data-stu-id="27485-120">The orchestration routes the message to the send port (Tutorial_BatchDest), which sends the batched message to the destination (in this case, the \Tutorial_BatchMsgDrop folder on your hard drive).</span></span> <span data-ttu-id="27485-121">在本教學課程中，會在一小時後傳送批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="27485-121">In this tutorial, the batched messages are sent after one hour.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27485-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="27485-122">In This Section</span></span>  
  
-   [<span data-ttu-id="27485-123">步驟 1：設定和啟用 BatchControlPort 接收埠</span><span class="sxs-lookup"><span data-stu-id="27485-123">Step 1: Configure and Enable the BatchControlPort Receive Port</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-and-enable-the-batchcontrolport-receive-port.md)  
  
-   [<span data-ttu-id="27485-124">步驟 2：啟用批次協調流程</span><span class="sxs-lookup"><span data-stu-id="27485-124">Step 2: Enable the Batch Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)  
  
-   [<span data-ttu-id="27485-125">步驟 3：建立和設定目的合作對象</span><span class="sxs-lookup"><span data-stu-id="27485-125">Step 3: Create and Configure a Destination Party</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)  
  
-   [<span data-ttu-id="27485-126">步驟 4：設定建立批次案例的來源合作對象</span><span class="sxs-lookup"><span data-stu-id="27485-126">Step 4: Configure the Source Party for the Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)  
  
-   [<span data-ttu-id="27485-127">步驟 5：建立訊息批次的傳送埠</span><span class="sxs-lookup"><span data-stu-id="27485-127">Step 5: Create the Send Port for the Message Batch</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)  
  
-   [<span data-ttu-id="27485-128">步驟 6：建立通知批次的傳送埠</span><span class="sxs-lookup"><span data-stu-id="27485-128">Step 6: Create the Send Port for the Acknowledgment Batch</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)  
  
-   [<span data-ttu-id="27485-129">步驟 7：啟動協調流程，並重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="27485-129">Step 7: Start the Orchestration and Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="27485-130">步驟 8：測試建立批次案例</span><span class="sxs-lookup"><span data-stu-id="27485-130">Step 8: Test the Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md)