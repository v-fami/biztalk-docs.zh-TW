---
title: 啟動者公開程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- public processes, initiator
- CIDX, 0A1 messages
- messages, 0A1 messages
- messages, message flow
- messages, public processes
- 0A1 messages
- public processes, message flow
ms.assetid: 371d0792-d346-405b-a8f4-2dfa64dd1566
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fa1cd2fc73e37590e25fb381f509c2ad74cd9e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968439"
---
# <a name="initiator-public-process"></a><span data-ttu-id="9b188-102">啟動者公開程序</span><span class="sxs-lookup"><span data-stu-id="9b188-102">Initiator Public Process</span></span>
<span data-ttu-id="9b188-103">此程序會建立並傳送初始 RNIF 商務訊息，以在啟動者系統上初始 RosettaNet 實作架構 (RNIF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-103">This process initiates RosettaNet Implementation Framework (RNIF) messaging on the initiator system by creating and sending the initial RNIF business message.</span></span>  
  
## <a name="message-flow-in-the-initiator-public-process"></a><span data-ttu-id="9b188-104">啟動者公開程序中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="9b188-104">Message Flow in the Initiator Public Process</span></span>  
 <span data-ttu-id="9b188-105">通過啟動者公開程序的訊息流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b188-105">The message flow through the initiator public process is as follows:</span></span>  
  
1. <span data-ttu-id="9b188-106">啟動者公開程序透過服務內容傳輸埠，從私用程序接收服務內容以及附件。</span><span class="sxs-lookup"><span data-stu-id="9b188-106">The initiator public process receives the service content and attachments from the private process through the service-content port.</span></span>  
  
2. <span data-ttu-id="9b188-107">公開程序傳送回應至私用程序，但不會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="9b188-107">The public process sends the response to the private process, and does no further processing.</span></span>  
  
3. <span data-ttu-id="9b188-108">如果公開程序就會收到通知，Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]未能成功傳送訊息，公開程序會將該狀態回到啟動者私用程序，然後結束。</span><span class="sxs-lookup"><span data-stu-id="9b188-108">If the public process receives notification that Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] did not successfully send the message, the public process sends that status back to the initiator private process, and then ends.</span></span>  
  
4. <span data-ttu-id="9b188-109">如果公開程序收到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 成功傳送訊息的通知，程序便會進入等候狀態 (等候回應者的動作)。</span><span class="sxs-lookup"><span data-stu-id="9b188-109">If the public process receives notification that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] successfully sent the message, the process enters a wait state (waiting for action by the responder).</span></span>  
  
5. <span data-ttu-id="9b188-110">下列動作可以結束等候狀態：</span><span class="sxs-lookup"><span data-stu-id="9b188-110">The following actions can end the wait state:</span></span>  
  
   1.  <span data-ttu-id="9b188-111">公開程序接收來自回應者的確認信號。</span><span class="sxs-lookup"><span data-stu-id="9b188-111">The public process receives an acknowledgement signal from the responder.</span></span>  
  
        <span data-ttu-id="9b188-112">如果需要不可否認性信號 (在程序組態設定中設定)，程序便會讀取摘要，並設定信號中的摘要與原始動作訊息摘要的關聯，然後持續發出信號。</span><span class="sxs-lookup"><span data-stu-id="9b188-112">If non-repudiation for the signal is required (as set in the process configuration settings), the process reads the digest, correlates the digest in the signal with the digest in the original action message, and then persists the signal.</span></span>  
  
        <span data-ttu-id="9b188-113">公開程序傳送信號的標頭以及服務內容至私用程序。</span><span class="sxs-lookup"><span data-stu-id="9b188-113">The public process sends the headers and service content of the signal to the private process.</span></span>  
  
   2.  <span data-ttu-id="9b188-114">公開程序接收來自回應者的雙向動作回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-114">The public process receives a double-action response message from the responder.</span></span>  
  
        <span data-ttu-id="9b188-115">程序從回應訊息取出服務內容以及標頭，然後傳送至私用程序。</span><span class="sxs-lookup"><span data-stu-id="9b188-115">The process extracts the service content and headers from the response message, and sends them to the private process.</span></span>  
  
        <span data-ttu-id="9b188-116">如果活動是同步的，公開程序便會將服務內容訊息部分與前序、服務標頭及傳遞標頭 (僅針對 RNIF 2.01) 包裝起來以建構 RNIF 信號訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-116">If the activity is synchronous, the process constructs an RNIF signal message by wrapping the service-content message part with the preamble, service header, and delivery header (for RNIF 2.01).</span></span> <span data-ttu-id="9b188-117">程序使用關於來源和合作對象的組態資訊以建立前序和標頭，以及儲存在不同合作對象之間交易夥伴協議中的 PIP 變數。</span><span class="sxs-lookup"><span data-stu-id="9b188-117">The process creates the preamble and headers using configuration information about the source and destination parties, and the PIP variables stored in the trading partner agreement between the parties.</span></span> <span data-ttu-id="9b188-118">接著，程序傳送信號訊息至回應者。</span><span class="sxs-lookup"><span data-stu-id="9b188-118">The process then sends the signal message to the responder.</span></span>  
  
        <span data-ttu-id="9b188-119">如果活動為非同步，程序便會結束。</span><span class="sxs-lookup"><span data-stu-id="9b188-119">If the activity is asynchronous, the process ends.</span></span>  
  
   3.  <span data-ttu-id="9b188-120">公開程序接收來自回應者的「失敗通知」(NoF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-120">The public process receives a Notification of Failure (NoF) message from the responder.</span></span> <span data-ttu-id="9b188-121">公開程序傳送相對的狀態訊息至啟動者私用程序。</span><span class="sxs-lookup"><span data-stu-id="9b188-121">The public process sends a corresponding status message to the initiator private process.</span></span> <span data-ttu-id="9b188-122">接著，私用程序會處理錯誤且一併結束兩個程序。</span><span class="sxs-lookup"><span data-stu-id="9b188-122">The private process then handles the error and ends both processes.</span></span>  
  
   4.  <span data-ttu-id="9b188-123">公開程序在「通知時間」時段 (在程序組態設定中設定) 之內不會接收來自回應者的確認信號。</span><span class="sxs-lookup"><span data-stu-id="9b188-123">The public process does not receive an acknowledgement signal from the responder within the Time to Acknowledge period (as set in the process configuration settings).</span></span> <span data-ttu-id="9b188-124">若是如此，會發生下列其中一種狀況：</span><span class="sxs-lookup"><span data-stu-id="9b188-124">If so, one of the following occurs:</span></span>  
  
        <span data-ttu-id="9b188-125">如果重試次數 (在程序組態設定中設定) 未達到零，並且活動為非同步，公開程序便會再次傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-125">If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is asynchronous, the public process sends the message again.</span></span>  
  
        <span data-ttu-id="9b188-126">如果重試次數 (在程序組態設定中設定) 未達到零，並且活動是同步的，公開程序便會初始 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-126">If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is synchronous, the public process initiates a 0A1 message.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="9b188-127">CIDX 不支援 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-127">CIDX does not support 0A1 messages.</span></span>  
  
        <span data-ttu-id="9b188-128">如果重試次數在沒有成功傳送的情況下達到零，公開程序會張貼錯誤訊息，且如果不是 CIDX，公開程序便會傳送 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-128">If the number of retries reaches zero without a successful send, the public process posts an error message, and if this is not CIDX, the public process sends a 0A1 message.</span></span>  
  
        <span data-ttu-id="9b188-129">如果此活動為同步，而且這不是 CIDX，則公開程序會初始 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-129">If the activity is synchronous, and this is not CIDX, the public process initiates a 0A1 message.</span></span>  
  
   5.  <span data-ttu-id="9b188-130">如果在「執行時間」內未發生任何動作，而且這不是 CIDX，則公開程序會傳送 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b188-130">If no action occurs within the Time to Perform period, and this is not CIDX, the public process sends a 0A1 message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b188-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b188-131">See Also</span></span>  
 <span data-ttu-id="9b188-132">[公開程序](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span><span class="sxs-lookup"><span data-stu-id="9b188-132">[Public Processes](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span></span>  
 [<span data-ttu-id="9b188-133">回應者公開程序</span><span class="sxs-lookup"><span data-stu-id="9b188-133">Responder Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)