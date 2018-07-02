---
title: 第 2 部分： 批次中批次出案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, outbound batches
- batching, inbound batches
ms.assetid: 36b9d927-f5b7-4c1a-9163-9e79d17c3e9e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 593f1e57b12eb30f47db65bfacd34a988f701f07
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975415"
---
# <a name="part-2-batch-inbatch-out-scenario"></a><span data-ttu-id="f6901-102">第 2 部分： 中批次 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="f6901-102">Part 2: Batch In/Batch Out Scenario</span></span>
<span data-ttu-id="f6901-103">在本教學課程的這個部分，接收 HL7 編碼的批次檔、 將其傳遞[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]片段，並傳送到目的地的不變的批次檔。</span><span class="sxs-lookup"><span data-stu-id="f6901-103">In this part of the tutorial, you receive an HL7-encoded batch file, pass it through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without fragmentation, and send the intact batch file to the destination.</span></span> <span data-ttu-id="f6901-104">下圖顯示這項程序流程，並以下小節說明工作流程。</span><span class="sxs-lookup"><span data-stu-id="f6901-104">The following figure shows the flow of this process, and the subsection below describes the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6901-105">開始本教學課程的這個部分之前, 關閉 MllpReceive 和 MllpSend 工具用於第 1 部分，藉由關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6901-105">Before starting this part of the tutorial, turn off the MllpReceive and MllpSend tools that you used in Part 1, by closing the command prompts.</span></span>  
  
 <span data-ttu-id="f6901-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")</span><span class="sxs-lookup"><span data-stu-id="f6901-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")</span></span>  
  
 <span data-ttu-id="f6901-107">**如何將訊息傳送批次中在 / 批次出案例**</span><span class="sxs-lookup"><span data-stu-id="f6901-107">**How messages flow in the Batch In/Batch Out scenario**</span></span>  
  
 <span data-ttu-id="f6901-108">此案例包含下列工作流程：</span><span class="sxs-lookup"><span data-stu-id="f6901-108">This scenario includes the following workflow:</span></span>  
  
1. <span data-ttu-id="f6901-109">在工作流程開始時的特定業務應用程式將訊息批次傳送至 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 整合引擎使用 FILE 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f6901-109">The workflow begins when a line-of-business application sends a message batch to the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Integration Engine using the FILE protocol.</span></span> <span data-ttu-id="f6901-110">批次包含兩個版本 ADT ^ 將 adt^a03 訊息。</span><span class="sxs-lookup"><span data-stu-id="f6901-110">The batch contains two versions of an ADT^A03 message.</span></span> <span data-ttu-id="f6901-111">原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。</span><span class="sxs-lookup"><span data-stu-id="f6901-111">The source application belongs to the Tutorial_BatchSource party.</span></span>  
  
2. <span data-ttu-id="f6901-112">整合引擎接收的批次檔案接收埠，並驗證的訊息批次。</span><span class="sxs-lookup"><span data-stu-id="f6901-112">The Integration Engine receives the batch on a FILE receive port, and validates the message batch.</span></span> <span data-ttu-id="f6901-113">(取決於選取中的來源合作對象設定的驗證層級[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。)</span><span class="sxs-lookup"><span data-stu-id="f6901-113">(The level of validation depends on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.)</span></span>  
  
3. <span data-ttu-id="f6901-114">根據設定，以在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管來停用 合作對象、 介面引擎的批次片段不會剖析成個別的訊息批次，但會保留做為批次的批次。</span><span class="sxs-lookup"><span data-stu-id="f6901-114">Based on a setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer that disables batch fragmentation for the party, the Interface Engine does not parse the batch into individual messages, but leaves the batch as a batch.</span></span> <span data-ttu-id="f6901-115">它會驗證個別的訊息，再根據設定中的來源合作對象選取[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="f6901-115">It validates the individual messages, again based on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
4. <span data-ttu-id="f6901-116">介面引擎產生的批次訊息中的通知定義設定為基礎的通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]的合作對象的組態編輯器。</span><span class="sxs-lookup"><span data-stu-id="f6901-116">The Interface Engine generates an acknowledgment for the batch message, based on the acknowledgment definition settings in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Editor for the party.</span></span> <span data-ttu-id="f6901-117">在此情況下，選取原始通知模式讓介面引擎產生的訊息批次的單一應用程式接受通知之後驗證訊息標頭和主體。</span><span class="sxs-lookup"><span data-stu-id="f6901-117">In this case, you select Original Acknowledgment mode, so the Interface Engine generates a single Application Accept acknowledgment for the message batch after validating both the message header and body.</span></span> <span data-ttu-id="f6901-118">引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 在 MSH3，輸入目的合作對象和 MSH5 中輸入的來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="f6901-118">The engine builds the acknowledgment based on the ACK_024_GLO_DEF schema, enters "AA" in field MSA2 of the acknowledgment, enters the destination party in MSH3, and enters the source party in MSH5.</span></span>  
  
5. <span data-ttu-id="f6901-119">通知批次的來源合作對象，透過檔案介面引擎路由傳送配接器設定來處理通知。</span><span class="sxs-lookup"><span data-stu-id="f6901-119">The Interface Engine routes the acknowledgment batch to the source party through a FILE send adapter set up to process acknowledgments.</span></span> <span data-ttu-id="f6901-120">在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將批次傳送至 \Tutorial_BatchACKDrop 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f6901-120">In this case, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] routes the batch to the \Tutorial_BatchACKDrop folder.</span></span>  
  
6. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f6901-121"> 會傳送到目的地的訊息批次指定目的合作對象，在此情況下資料夾 \Tutorial_BTAHL7Drop。</span><span class="sxs-lookup"><span data-stu-id="f6901-121"> sends the message batch to the destination specified for the destination party, in this case the folder \Tutorial_BTAHL7Drop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6901-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6901-122">In This Section</span></span>  
  
-   [<span data-ttu-id="f6901-123">步驟 1：設定批次進/批次出的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="f6901-123">Step 1: Configure Party Information for Batch In/Batch Out</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [<span data-ttu-id="f6901-124">步驟 2：修改或建立傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="f6901-124">Step 2: Modify or Create the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="f6901-125">步驟 3：測試批次進/批次出案例</span><span class="sxs-lookup"><span data-stu-id="f6901-125">Step 3: Test the Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)