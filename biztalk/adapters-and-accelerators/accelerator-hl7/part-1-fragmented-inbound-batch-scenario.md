---
title: 第 1 部分： 分散的傳入批次案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- batching tutorial, fragmenting messages
- fragmenting messages
ms.assetid: 8adf2c17-5f66-408d-b30b-51b22d8e71fa
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8891bd09c803c77e1878b304f5db5b71a26ab9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206214"
---
# <a name="part-1-fragmented-inbound-batch-scenario"></a><span data-ttu-id="ec151-102">第 1 部分： 分散的傳入批次的案例</span><span class="sxs-lookup"><span data-stu-id="ec151-102">Part 1: Fragmented Inbound Batch Scenario</span></span>
<span data-ttu-id="ec151-103">在本教學課程的這個部分，您可以接收 HL7 編碼的批次、 分割成個別的訊息，以及個別的訊息傳送至目的地。</span><span class="sxs-lookup"><span data-stu-id="ec151-103">In this part of the tutorial, you receive an HL7-encoded batch, fragment it into individual messages, and send the individual messages to a destination.</span></span> <span data-ttu-id="ec151-104">下圖顯示此程序的流程。</span><span class="sxs-lookup"><span data-stu-id="ec151-104">The following figure shows the flow of this process.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-fragmented-inbound-batching-scenario.gif "hl7_fragmented_inbound_batching_scenario")  
  
 <span data-ttu-id="ec151-105">此案例包含下列工作流程：</span><span class="sxs-lookup"><span data-stu-id="ec151-105">This scenario includes the following workflow:</span></span>  
  
1.  <span data-ttu-id="ec151-106">工作流程開始的特定業務應用程式傳送訊息批次時[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Integration 引擎使用最少的較低層通訊協定 (MLLP) 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ec151-106">The workflow begins when a line-of-business application sends a message batch to the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Integration Engine using the Minimal Lower Layer Protocol (MLLP) protocol.</span></span> <span data-ttu-id="ec151-107">批次包含兩個版本 ADT ^ A03 訊息。</span><span class="sxs-lookup"><span data-stu-id="ec151-107">The batch contains two versions of an ADT^A03 message.</span></span> <span data-ttu-id="ec151-108">原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。</span><span class="sxs-lookup"><span data-stu-id="ec151-108">The source application belongs to the Tutorial_BatchSource party.</span></span>  
  
2.  <span data-ttu-id="ec151-109">介面引擎接收批次 MLLP 的接收埠，並驗證的訊息批次。</span><span class="sxs-lookup"><span data-stu-id="ec151-109">The Interface Engine receives the batch on an MLLP receive port, and validates the message batch.</span></span> <span data-ttu-id="ec151-110">（驗證層級取決於選取的來源合作對象 BTAHL7 組態總管 中設定）。</span><span class="sxs-lookup"><span data-stu-id="ec151-110">(The level of validation depends on settings selected for the source party in BTAHL7 Configuration Explorer.)</span></span>  
  
3.  <span data-ttu-id="ec151-111">根據 BTAHL7 Configuration 總管，可讓批次片段中的設定，介面引擎會剖析批次到兩個個別 ADT ^ A03 訊息。</span><span class="sxs-lookup"><span data-stu-id="ec151-111">Based on a setting in BTAHL7 Configuration Explorer that enables batch fragmentation, the Interface Engine parses the batch into two individual ADT^A03 messages.</span></span> <span data-ttu-id="ec151-112">它會驗證個別訊息，再根據 BTAHL7 組態總管 中的來源合作對象為選取的設定。</span><span class="sxs-lookup"><span data-stu-id="ec151-112">It validates the individual messages, again based on settings selected for the source party in BTAHL7 Configuration Explorer.</span></span>  
  
4.  <span data-ttu-id="ec151-113">介面引擎會產生每個訊息，取決於 BTAHL7 組態總管 中的通知定義設定的通知。</span><span class="sxs-lookup"><span data-stu-id="ec151-113">The Interface Engine generates an acknowledgment for each message, based on the acknowledgment definition settings in BTAHL7 Configuration Explorer.</span></span> <span data-ttu-id="ec151-114">在本教學課程中，您將選取原始的認可模式中，因此介面引擎產生單一應用程式接受通知，每個訊息驗證的訊息標頭和本文之後。</span><span class="sxs-lookup"><span data-stu-id="ec151-114">In this tutorial, you will select Original Acknowledgment mode, so the Interface Engine generates a single Application Accept acknowledgment for each message after validating both the message header and body.</span></span> <span data-ttu-id="ec151-115">引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 目的合作對象進入 MSH3，並進入 MSH5 來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="ec151-115">The engine builds the acknowledgment based on the ACK_024_GLO_DEF schema, enters "AA" in field MSA2 of the acknowledgment, enters the destination party in MSH3, and enters the source party in MSH5.</span></span>  
  
5.  <span data-ttu-id="ec151-116">介面引擎將每個通知，MLLP 包裝函式，並透過 MLLP 傳送配接器的通知到來源合作對象的路由設定處理通知。</span><span class="sxs-lookup"><span data-stu-id="ec151-116">The Interface Engine places MLLP wrappers around each acknowledgment, and routes the acknowledgments to the source party through an MLLP send adapter set up to process acknowledgments.</span></span>  
  
6.  <span data-ttu-id="ec151-117">介面引擎會將每個訊息，以及個別 MLLP 每個訊息的傳送埠設定來處理非通知訊息的路由 MLLP 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="ec151-117">The Interface Engine places MLLP wrappers around each message, and routes each message individually to an MLLP send port set up to process non-acknowledgment messages.</span></span>  
  
7.  <span data-ttu-id="ec151-118">BTAHL7 會透過另一個 MLLP 傳送埠中每個訊息傳送到其 MSH5 欄位中指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="ec151-118">BTAHL7 sends each message through another MLLP send port to the destination specified in its MSH5 field.</span></span>  
  
8.  <span data-ttu-id="ec151-119">目的合作對象會傳送至 BTAHL7 應用程式接受它接收到每個訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="ec151-119">The destination party sends to BTAHL7 an application-accept acknowledgment for each message that it received.</span></span>  
  
9. <span data-ttu-id="ec151-120">介面引擎接收每個通知。</span><span class="sxs-lookup"><span data-stu-id="ec151-120">The Interface Engine receives each acknowledgment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec151-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="ec151-121">In This Section</span></span>  
  
-   [<span data-ttu-id="ec151-122">步驟 1： 加入標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="ec151-122">Step 1: Add Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="ec151-123">步驟 2： 新增 v2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="ec151-123">Step 2: Add Common Schemas for v2.3.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)  
  
-   [<span data-ttu-id="ec151-124">步驟 3： 新增觸發程序事件 （訊息） 結構描述</span><span class="sxs-lookup"><span data-stu-id="ec151-124">Step 3: Add a Trigger Event (Message) Schema</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)  
  
-   [<span data-ttu-id="ec151-125">步驟 4： 建立接收埠，以便接受批次訊息</span><span class="sxs-lookup"><span data-stu-id="ec151-125">Step 4: Create a Receive Port for Accepting the Batch Message</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)  
  
-   [<span data-ttu-id="ec151-126">步驟 5： 建立傳送埠將訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="ec151-126">Step 5: Create a Send Port to Deliver Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)  
  
-   [<span data-ttu-id="ec151-127">步驟 6： 建立傳送埠以傳送通知</span><span class="sxs-lookup"><span data-stu-id="ec151-127">Step 6: Create a Send Port to Deliver Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)  
  
-   [<span data-ttu-id="ec151-128">步驟 7： 建立及設定來源合作對象</span><span class="sxs-lookup"><span data-stu-id="ec151-128">Step 7: Create and Configure a Source Party</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)  
  
-   [<span data-ttu-id="ec151-129">步驟 8： 重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ec151-129">Step 8: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="ec151-130">步驟 9： 驗證的分散輸入批次案例</span><span class="sxs-lookup"><span data-stu-id="ec151-130">Step 9: Verify the Fragmented Inbound Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-verify-the-fragmented-inbound-batch-scenario.md)