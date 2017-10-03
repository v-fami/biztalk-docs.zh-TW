---
title: "回應者公開程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow
- messages, public processes
- public processes, message flow
- public processes, responder
ms.assetid: 78d83954-2998-44ac-a527-5e5858c61009
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c89c246bca80fdb648df909cd4f01fca4e2691dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="responder-public-process"></a><span data-ttu-id="3a339-102">回應者公開程序</span><span class="sxs-lookup"><span data-stu-id="3a339-102">Responder Public Process</span></span>
<span data-ttu-id="3a339-103">回應者的這個公開程序會接收來自啟動者的 RosettaNet 實作架構 (RNIF) 訊息並依此回應。</span><span class="sxs-lookup"><span data-stu-id="3a339-103">This public process on the responder receives the RosettaNet Implementation Framework (RNIF) message from the initiator, and responds accordingly.</span></span>  
  
## <a name="message-flow-in-the-responder-public-process"></a><span data-ttu-id="3a339-104">回應者公開程序中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="3a339-104">Message Flow in the Responder Public Process</span></span>  
 <span data-ttu-id="3a339-105">透過回應者公開程序的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="3a339-105">The message flow through the responder public process is as follows:</span></span>  
  
1.  <span data-ttu-id="3a339-106">回應者公開程序從回應者 MessageBox 資料庫接收 RNIF 訊息。</span><span class="sxs-lookup"><span data-stu-id="3a339-106">The responder public process receives the RNIF message from the responder MessageBox database.</span></span>  
  
2.  <span data-ttu-id="3a339-107">公開程序從動作訊息擷取服務內容和標頭，然後傳送至私用程序。</span><span class="sxs-lookup"><span data-stu-id="3a339-107">The public process extracts the service content and headers from the action message, and sends them to the private process.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a339-108">回應者公開程序針對內送訊息執行標準驗證 (以及包含在驗證配接器中的任何其他驗證)。</span><span class="sxs-lookup"><span data-stu-id="3a339-108">The responder public process performs standard validation on the incoming message (and any additional validation included in a validation adapter, if applicable).</span></span> <span data-ttu-id="3a339-109">如果驗證成功，公開程序將會初始化應用程式配接器，依照特定的實作方式來執行通知。</span><span class="sxs-lookup"><span data-stu-id="3a339-109">If validation is successful, then the public process will initiate the application adapter to perform notification in accordance with the specific implementation.</span></span> <span data-ttu-id="3a339-110">回應者公開程序會將訊息儲存在 MessageBox 資料庫中，並通知已經將訊息儲存至 MessageBox 的回應者私用程序 (使用 `BeginNotify` 類別中的 `ApplicationAdapter` 方法)。</span><span class="sxs-lookup"><span data-stu-id="3a339-110">The responder public process will save the message in the MessageBox database, and will notify the responder private process that it has saved the message in the MessageBox (using the `BeginNotify` method in the `ApplicationAdapter` class).</span></span> <span data-ttu-id="3a339-111">如需有關驗證配接器和應用程式配接器的詳細資訊，請參閱[ValidationAdapter &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)和[ApplicationAdapter &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md).</span><span class="sxs-lookup"><span data-stu-id="3a339-111">For more information about the validation adapter and application adapter, see [ValidationAdapter &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md) and [ApplicationAdapter &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md).</span></span>  
  
3.  <span data-ttu-id="3a339-112">如果活動是非同步且為單向動作，公開程序便會將服務內容訊息部分與前序、服務標頭及傳遞標頭 (僅針對 RNIF 2.01) 包裝起來以建構 RNIF 信號訊息 (通知接受)。</span><span class="sxs-lookup"><span data-stu-id="3a339-112">If the activity is asynchronous and single-action, the public process constructs an RNIF signal message (Acknowledgment Acceptance) by wrapping the service-content message part with the preamble, the service header, and (for RNIF 2.01 only) the delivery header.</span></span> <span data-ttu-id="3a339-113">公開程序建構前序、 服務標頭和傳遞標頭使用儲存在合作對象之間交易夥伴協議的資訊： 程序組態設定、 設定來源的相關資訊，目的地合作對象，以及交易夥伴介面程序 (PIP) 變數。</span><span class="sxs-lookup"><span data-stu-id="3a339-113">The public process constructs the preamble, the service header, and the delivery header using information stored in the trading partner agreement between the parties: the process configuration settings, configuration information about the source and destination parties, and the Partner Interface Process (PIP) variables.</span></span> <span data-ttu-id="3a339-114">接著，程序會傳送信號訊息至啟動者。</span><span class="sxs-lookup"><span data-stu-id="3a339-114">The process then sends the signal message to the initiator.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a339-115">如果訊息是單向動作訊息，訊息流程就完成了。</span><span class="sxs-lookup"><span data-stu-id="3a339-115">If the message is a single-action message, the message flow is complete.</span></span>  
  
4.  <span data-ttu-id="3a339-116">公開程序進入等候狀態 (等候回應者私用程序的動作)。</span><span class="sxs-lookup"><span data-stu-id="3a339-116">The public process enters a wait state (waiting for action by the responder private process).</span></span>  
  
5.  <span data-ttu-id="3a339-117">下列動作可以結束等候狀態 (等候回應者私用程序的動作)：</span><span class="sxs-lookup"><span data-stu-id="3a339-117">The following actions can end the wait state (waiting for action by the responder private process):</span></span>  
  
    1.  <span data-ttu-id="3a339-118">回應者私用程序傳回回應服務內容和標頭，以回應原始動作訊息 (此為雙向動作訊息)。</span><span class="sxs-lookup"><span data-stu-id="3a339-118">The responder private process returns a response service-content message and headers, in response to the original action message (that was a double-action message).</span></span>  
  
         <span data-ttu-id="3a339-119">如果公開程序會從私用程序接收回應服務內容，公開程序以建構 RNIF 訊息，其中包含服務內容。</span><span class="sxs-lookup"><span data-stu-id="3a339-119">If the public process receives response service content from the private process, the public process constructs an RNIF message that contains the service content.</span></span> <span data-ttu-id="3a339-120">它的做法是將服務內容訊息部分、包含來源合作對象和目的合作對象組態資訊的標頭，以及儲存於交易夥伴協議中的 PIP 變數包裝起來。</span><span class="sxs-lookup"><span data-stu-id="3a339-120">It does so by wrapping the service-content message part with headers that contain the configuration information about the source and destination parties, and the PIP variables stored in the agreement between the parties.</span></span>  
  
         <span data-ttu-id="3a339-121">公開程序使用「動作/信號角色」(Action/Signal Role) 連結埠，傳送 RNIF 訊息給啟動者。</span><span class="sxs-lookup"><span data-stu-id="3a339-121">The public process sends the RNIF message to the initiator using the Action/Signal Role link port.</span></span>  
  
         <span data-ttu-id="3a339-122">如果公開程序會收到通知， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]未能成功傳送訊息，公開程序會將該狀態回傳至私用程序，然後結束。</span><span class="sxs-lookup"><span data-stu-id="3a339-122">If the public process receives notification that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] did not successfully send the message, the public process sends that status back to the private process, and then ends.</span></span>  
  
         <span data-ttu-id="3a339-123">如果公開程序收到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 成功傳送訊息的通知，程序便會進入等候狀態 (等候啟動者的動作)。</span><span class="sxs-lookup"><span data-stu-id="3a339-123">If the public process receives notification that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] successfully sent the message, the process enters a wait state (waiting for action by the initiator).</span></span> <span data-ttu-id="3a339-124">此等候狀態與啟動者在等候回應者的動作時的等候狀態類似。</span><span class="sxs-lookup"><span data-stu-id="3a339-124">This wait state is similar to the wait state that the initiator enters when it is waiting for action by the responder.</span></span>  
  
    2.  <span data-ttu-id="3a339-125">公開程序接收來自啟動者的「失敗通知」(NoF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="3a339-125">The public process receives a Notification of Failure message (NoF) from the initiator.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a339-126">回應者私用程序將在成功處理內送訊息後，通知回應者公開程序。</span><span class="sxs-lookup"><span data-stu-id="3a339-126">The responder private process will notify the responder public process after it has successfully processed the incoming message.</span></span> <span data-ttu-id="3a339-127">只有在回應者公開程序接收到此通知之後 (透過 `EndNotify` 類別中的 `ApplicationAdapter` 方法)，回應者公開程序才算成功完成。</span><span class="sxs-lookup"><span data-stu-id="3a339-127">Only after the responder public process has received this notification (from the `EndNotify` method in the `ApplicationAdapter` class) will the responder public process be successfully completed.</span></span>  
  
6.  <span data-ttu-id="3a339-128">回應者公開程序進入等候狀態 (等候接收啟動者的信號，以對回應者公開程序所傳送的回應訊息發出回應)。</span><span class="sxs-lookup"><span data-stu-id="3a339-128">The responder public process enters a wait state (waiting to receive a signal from the initiator in response to the response message that the responder public process sent).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a339-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a339-129">See Also</span></span>  
 <span data-ttu-id="3a339-130">[公開程序](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span><span class="sxs-lookup"><span data-stu-id="3a339-130">[Public Processes](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span></span>  
 <span data-ttu-id="3a339-131">[啟動者公開程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md) </span><span class="sxs-lookup"><span data-stu-id="3a339-131">[Initiator Public Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md) </span></span>  
 <span data-ttu-id="3a339-132">[ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a339-132">[ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md) </span></span>  
 [<span data-ttu-id="3a339-133">ValidationAdapter</span><span class="sxs-lookup"><span data-stu-id="3a339-133">ValidationAdapter</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)