---
title: "處理和一致的訊息集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fc9f35f9381f82df90acb92e9536bbd967901a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-reconciled-message-sets"></a><span data-ttu-id="80751-102">處理調節訊息設定</span><span class="sxs-lookup"><span data-stu-id="80751-102">Handling Reconciled Message Sets</span></span>
<span data-ttu-id="80751-103">當 SAA 傳回的回應[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]位於 MessageBox 中記錄的回應，而且符合回應或原始訊息的回應。</span><span class="sxs-lookup"><span data-stu-id="80751-103">When SAA returns a response to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] records the response in the MessageBox, and matches the response or responses to the original message.</span></span> <span data-ttu-id="80751-104">您可以實作自訂的應用程式的行為，使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="80751-104">You can implement custom application behavior using this information.</span></span> <span data-ttu-id="80751-105">若要這樣做，請開發實作特定客戶的反應，來調解的訊息/回應設定的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="80751-105">To do so, develop custom handlers that implement customer-specific reactions to reconciled message/response sets.</span></span> <span data-ttu-id="80751-106">您可以建立自訂的處理常式，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="80751-106">You can create custom handlers that do the following:</span></span>  
  
-   <span data-ttu-id="80751-107">處理的訊息有相互關聯的 FRR MTS21_FIN_ACKNAK 負值通知訊息，這表示，SWIFT 未順利收到來自訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80751-107">Process messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="80751-108">這可以讓 repairer 修正訊息並重新將它傳送到 SAA 和 SWIFT 網路，在修復後將會希望能夠成功接收訊息。</span><span class="sxs-lookup"><span data-stu-id="80751-108">This can enable a repairer to fix the message and re-send it to SAA and the SWIFT network, which after the repair will hopefully be able to receive the message successfully.</span></span> <span data-ttu-id="80751-109">如需此解決方案的詳細資訊，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="80751-109">For more information about this solution, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span></span>  
  
-   <span data-ttu-id="80751-110">卸除具有唯一的檔名表示的關聯性在集合中的訊息檔案資料夾到協調流程所發行的訊息回應設定。</span><span class="sxs-lookup"><span data-stu-id="80751-110">Drop message-response sets published by the orchestration into a file folder with unique file names indicating the relationships of the messages in the set.</span></span> <span data-ttu-id="80751-111">然後，您可以在這些訊息上執行商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="80751-111">You can then perform business logic on these messages.</span></span>  
  
-   <span data-ttu-id="80751-112">處理序逾時訊息。</span><span class="sxs-lookup"><span data-stu-id="80751-112">Process timed-out messages.</span></span>  
  
-   <span data-ttu-id="80751-113">記錄訊息傳輸的結果，然後捨棄真正的訊息。</span><span class="sxs-lookup"><span data-stu-id="80751-113">Log the results of message transmission and then discard the actual messages.</span></span>