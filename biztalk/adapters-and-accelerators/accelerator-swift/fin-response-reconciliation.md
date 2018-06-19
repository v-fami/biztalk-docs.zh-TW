---
title: FIN 回應對帳 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ACKs
- FRR
- FIN Response Reconciliation
- SAA
- NAKs
- FRR, about FRR
- acknowledgements
- FIN Response Reconciliation, about FIN Response Reconciliation
- FIN Response Reconciliation, acknowledgements
ms.assetid: 987b932b-e487-4ca8-acd0-410d71df8e6d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5452dbacb8a9a20c8d2e62d62f6043aaea2d18da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22208254"
---
# <a name="fin-response-reconciliation"></a><span data-ttu-id="ee747-102">FIN 回應對帳</span><span class="sxs-lookup"><span data-stu-id="ee747-102">FIN Response Reconciliation</span></span>
<span data-ttu-id="ee747-103">FIN 回應對帳 (FRR) 功能[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]調解 FIN 回應與對應的原始訊息傳送的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ee747-103">The FIN Response Reconciliation (FRR) feature of [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reconciles a FIN response with the corresponding original message sent by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="ee747-104">這會建立原始訊息的狀態，並讓[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]才能根據該狀態的步驟。</span><span class="sxs-lookup"><span data-stu-id="ee747-104">This establishes the status of the original message, and enables [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to take steps based upon that status.</span></span> <span data-ttu-id="ee747-105">不重新調整，這就不可能。</span><span class="sxs-lookup"><span data-stu-id="ee747-105">Without reconciliation, this would not be possible.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="ee747-106">就會知道它成功 （或不成功） 傳送原始訊息至 SAA，，和就會從 SAA，指出狀態的傳輸，收到的回應，但是它會不能使兩者之間的連線。</span><span class="sxs-lookup"><span data-stu-id="ee747-106"> would know that it successfully (or unsuccessfully) sent the original message to SAA, and it would have the response that it received from SAA, indicating the status of the transmission, but it would not be able to make the connection between the two.</span></span> <span data-ttu-id="ee747-107">FRR 建立該連接。</span><span class="sxs-lookup"><span data-stu-id="ee747-107">FRR establishes that connection.</span></span>  
  
 <span data-ttu-id="ee747-108">FIN 回應的通知 (Ack) 或負值通知 (NAKs) 傳送至 SAA [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，或由 SWIFT 網路傳送至 SAA 並再轉送到 SAA [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ee747-108">FIN responses are acknowledgments (ACKs) or negative acknowledgments (NAKs) sent by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], or sent by the SWIFT network to SAA and then forwarded by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="ee747-109">這些通知與否定義商務的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="ee747-109">The presence or absence of these acknowledgments defines the business status of the message.</span></span> <span data-ttu-id="ee747-110">您可以監視此透過商務活動監控 (BAM) 報告的狀態。</span><span class="sxs-lookup"><span data-stu-id="ee747-110">You can monitor this status through Business Activity Monitoring (BAM) reporting.</span></span>  
  
 <span data-ttu-id="ee747-111">您也可以實作 FRR 周圍的自訂應用程式行為。</span><span class="sxs-lookup"><span data-stu-id="ee747-111">You can also implement custom application behavior around FRR.</span></span> <span data-ttu-id="ee747-112">自訂處理常式可以實作您自己的邏輯來處理和一致的 FIN 回應的設定。</span><span class="sxs-lookup"><span data-stu-id="ee747-112">A custom handler can implement your own logic for handling reconciled sets of FIN responses.</span></span> <span data-ttu-id="ee747-113">如需處理的訊息有相互關聯的 FRR MTS21_FIN_ACKNAK NAK 訊息的自訂處理常式的範例，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ee747-113">For an example of a custom handler that processes messages that FRR has correlated with a MTS21_FIN_ACKNAK NAK message, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span></span>  
  
 <span data-ttu-id="ee747-114">依預設會安裝 FRR 協調流程[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="ee747-114">The FRR orchestration is installed by default by the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program.</span></span> <span data-ttu-id="ee747-115">您需要設定 FRR 系統藉由建立一個接收管線，接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ee747-115">You need to configure the FRR system by creating a receive pipeline, receive locations, and send ports.</span></span> <span data-ttu-id="ee747-116">您也需要設定來指定它應該等候多久延遲 NAKs，以及回應一般 FRR。</span><span class="sxs-lookup"><span data-stu-id="ee747-116">You also need to configure FRR to specify how long it should wait for delayed NAKs, and for responses in general.</span></span> <span data-ttu-id="ee747-117">如需 FRR 設定和管理的詳細資訊，請參閱[設定 FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md)和[管理 FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md)。</span><span class="sxs-lookup"><span data-stu-id="ee747-117">For more information about FRR configuration and administration, see [Configuring FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md) and [Administering FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md).</span></span>  
  
 <span data-ttu-id="ee747-118">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="ee747-118">This section contains:</span></span>  
  
-   [<span data-ttu-id="ee747-119">FIN 回應類型</span><span class="sxs-lookup"><span data-stu-id="ee747-119">FIN Response Types</span></span>](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)  
  
-   [<span data-ttu-id="ee747-120">FRR 處理</span><span class="sxs-lookup"><span data-stu-id="ee747-120">FRR Processing</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-processing.md)  
  
-   [<span data-ttu-id="ee747-121">FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="ee747-121">FRR Orchestration</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-orchestration.md)  
  
-   [<span data-ttu-id="ee747-122">FRR 接收訊息的位置從後端應用程式</span><span class="sxs-lookup"><span data-stu-id="ee747-122">FRR Receive Location for Messages from the Back-End Application</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-the-back-end-application.md)  
  
-   [<span data-ttu-id="ee747-123">FRR SWIFT 的訊息的傳送埠</span><span class="sxs-lookup"><span data-stu-id="ee747-123">FRR Send Port for Messages to SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-send-port-for-messages-to-swift.md)  
  
-   [<span data-ttu-id="ee747-124">FRR 來自 SWIFT 接收訊息的位置</span><span class="sxs-lookup"><span data-stu-id="ee747-124">FRR Receive Location for Messages from SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-swift.md)  
  
-   [<span data-ttu-id="ee747-125">訊息的自訂處理常式的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="ee747-125">FRR Send Ports for Messages to the Custom Handlers</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-send-ports-for-messages-to-the-custom-handlers.md)  
  
-   [<span data-ttu-id="ee747-126">處理調節訊息設定</span><span class="sxs-lookup"><span data-stu-id="ee747-126">Handling Reconciled Message Sets</span></span>](../../adapters-and-accelerators/accelerator-swift/handling-reconciled-message-sets.md)