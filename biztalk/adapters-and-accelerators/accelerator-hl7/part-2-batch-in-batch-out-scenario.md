---
title: 第 2 部分： 批次的批次中分析藍本 |Microsoft 文件
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
ms.openlocfilehash: 56ffac38676fe6b163a39ff06be5fe0538800d2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206182"
---
# <a name="part-2-batch-inbatch-out-scenario"></a><span data-ttu-id="08423-102">第 2 部分： 中批次 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="08423-102">Part 2: Batch In/Batch Out Scenario</span></span>
<span data-ttu-id="08423-103">在本教學課程的這個部分，接收 HL7 編碼的批次檔、 將其傳遞[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]分散的片段，而傳送保持不變的批次檔的目的地。</span><span class="sxs-lookup"><span data-stu-id="08423-103">In this part of the tutorial, you receive an HL7-encoded batch file, pass it through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without fragmentation, and send the intact batch file to the destination.</span></span> <span data-ttu-id="08423-104">下圖顯示此程序，流量和下列小節描述工作流程。</span><span class="sxs-lookup"><span data-stu-id="08423-104">The following figure shows the flow of this process, and the subsection below describes the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08423-105">開始本教學課程的這個部分之前, 關閉 MllpReceive 和 MllpSend 工具用於第 1 部分，關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="08423-105">Before starting this part of the tutorial, turn off the MllpReceive and MllpSend tools that you used in Part 1, by closing the command prompts.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")  
  
 <span data-ttu-id="08423-106">**批次中的訊息流動方式中 / 批次出案例**</span><span class="sxs-lookup"><span data-stu-id="08423-106">**How messages flow in the Batch In/Batch Out scenario**</span></span>  
  
 <span data-ttu-id="08423-107">此案例包含下列工作流程：</span><span class="sxs-lookup"><span data-stu-id="08423-107">This scenario includes the following workflow:</span></span>  
  
1.  <span data-ttu-id="08423-108">工作流程開始的特定業務應用程式傳送訊息批次時[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Integration 引擎使用 FILE 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="08423-108">The workflow begins when a line-of-business application sends a message batch to the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Integration Engine using the FILE protocol.</span></span> <span data-ttu-id="08423-109">批次包含兩個版本 ADT ^ A03 訊息。</span><span class="sxs-lookup"><span data-stu-id="08423-109">The batch contains two versions of an ADT^A03 message.</span></span> <span data-ttu-id="08423-110">原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。</span><span class="sxs-lookup"><span data-stu-id="08423-110">The source application belongs to the Tutorial_BatchSource party.</span></span>  
  
2.  <span data-ttu-id="08423-111">整合引擎接收批次檔接收埠，並驗證的訊息批次。</span><span class="sxs-lookup"><span data-stu-id="08423-111">The Integration Engine receives the batch on a FILE receive port, and validates the message batch.</span></span> <span data-ttu-id="08423-112">(驗證層級取決於選取的來源合作對象中設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。)</span><span class="sxs-lookup"><span data-stu-id="08423-112">(The level of validation depends on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.)</span></span>  
  
3.  <span data-ttu-id="08423-113">根據在設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管停用批次片段的合作對象、 介面引擎不會剖析成個別的訊息批次，但會保留做為批次的批次。</span><span class="sxs-lookup"><span data-stu-id="08423-113">Based on a setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer that disables batch fragmentation for the party, the Interface Engine does not parse the batch into individual messages, but leaves the batch as a batch.</span></span> <span data-ttu-id="08423-114">它會驗證個別訊息，再根據選取的來源合作對象中設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="08423-114">It validates the individual messages, again based on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
4.  <span data-ttu-id="08423-115">介面引擎產生批次，根據訊息中的通知定義設定通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]的合作對象的組態編輯器。</span><span class="sxs-lookup"><span data-stu-id="08423-115">The Interface Engine generates an acknowledgment for the batch message, based on the acknowledgment definition settings in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Editor for the party.</span></span> <span data-ttu-id="08423-116">在此情況下，選取原始的認可模式，如此介面引擎驗證的訊息標頭和本文之後產生的訊息批次的單一應用程式接受通知。</span><span class="sxs-lookup"><span data-stu-id="08423-116">In this case, you select Original Acknowledgment mode, so the Interface Engine generates a single Application Accept acknowledgment for the message batch after validating both the message header and body.</span></span> <span data-ttu-id="08423-117">引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 目的合作對象進入 MSH3，並進入 MSH5 來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="08423-117">The engine builds the acknowledgment based on the ACK_024_GLO_DEF schema, enters "AA" in field MSA2 of the acknowledgment, enters the destination party in MSH3, and enters the source party in MSH5.</span></span>  
  
5.  <span data-ttu-id="08423-118">通知批次的來源合作對象，透過檔案介面引擎路由傳送配接器設定處理通知。</span><span class="sxs-lookup"><span data-stu-id="08423-118">The Interface Engine routes the acknowledgment batch to the source party through a FILE send adapter set up to process acknowledgments.</span></span> <span data-ttu-id="08423-119">在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將批次傳送至 \Tutorial_BatchACKDrop 資料夾。</span><span class="sxs-lookup"><span data-stu-id="08423-119">In this case, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] routes the batch to the \Tutorial_BatchACKDrop folder.</span></span>  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="08423-120">會傳送到目的地的訊息批次為指定的目的合作對象，在此情況下資料夾 \Tutorial_BTAHL7Drop。</span><span class="sxs-lookup"><span data-stu-id="08423-120"> sends the message batch to the destination specified for the destination party, in this case the folder \Tutorial_BTAHL7Drop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08423-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="08423-121">In This Section</span></span>  
  
-   [<span data-ttu-id="08423-122">步驟 1： 設定批次中的合作對象資訊/出批次</span><span class="sxs-lookup"><span data-stu-id="08423-122">Step 1: Configure Party Information for Batch In/Batch Out</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [<span data-ttu-id="08423-123">步驟 2： 修改或建立傳送和接收埠</span><span class="sxs-lookup"><span data-stu-id="08423-123">Step 2: Modify or Create the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="08423-124">步驟 3： 測試中的批次/批次出案例</span><span class="sxs-lookup"><span data-stu-id="08423-124">Step 3: Test the Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)