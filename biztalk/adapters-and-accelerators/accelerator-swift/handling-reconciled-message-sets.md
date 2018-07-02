---
title: 處理和一致的訊息集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d3a06955e0072348098ddd7f191bf4862fb119a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986087"
---
# <a name="handling-reconciled-message-sets"></a><span data-ttu-id="ed002-102">處理協調的訊息集</span><span class="sxs-lookup"><span data-stu-id="ed002-102">Handling Reconciled Message Sets</span></span>
<span data-ttu-id="ed002-103">當 SAA 將回應傳回給[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]記錄位於 MessageBox 中的回應，並比對回應或原始訊息的回應。</span><span class="sxs-lookup"><span data-stu-id="ed002-103">When SAA returns a response to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] records the response in the MessageBox, and matches the response or responses to the original message.</span></span> <span data-ttu-id="ed002-104">您可以實作自訂的應用程式的行為，使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="ed002-104">You can implement custom application behavior using this information.</span></span> <span data-ttu-id="ed002-105">若要這樣做，請開發實作特定客戶的反應和一致的訊息回應集的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="ed002-105">To do so, develop custom handlers that implement customer-specific reactions to reconciled message/response sets.</span></span> <span data-ttu-id="ed002-106">您可以建立自訂的處理常式，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ed002-106">You can create custom handlers that do the following:</span></span>  

- <span data-ttu-id="ed002-107">處理 MTS21_FIN_ACKNAK 負值通知訊息，這會指出 SWIFT 未成功接收來自訊息的 FRR 有相互關聯訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed002-107">Process messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="ed002-108">這可以讓 repairer 修正訊息，並重新傳送給 SAA 和 SWIFT 網路，在修復後將會希望能夠成功接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ed002-108">This can enable a repairer to fix the message and re-send it to SAA and the SWIFT network, which after the repair will hopefully be able to receive the message successfully.</span></span> <span data-ttu-id="ed002-109">如需有關此解決方案的詳細資訊，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ed002-109">For more information about this solution, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span></span>  

- <span data-ttu-id="ed002-110">拖放入檔案資料夾中的協調流程發佈其唯一的檔案名稱表示的關聯性集合中的訊息的訊息回應設定。</span><span class="sxs-lookup"><span data-stu-id="ed002-110">Drop message-response sets published by the orchestration into a file folder with unique file names indicating the relationships of the messages in the set.</span></span> <span data-ttu-id="ed002-111">然後，您就可以執行商務邏輯上這些訊息。</span><span class="sxs-lookup"><span data-stu-id="ed002-111">You can then perform business logic on these messages.</span></span>  

- <span data-ttu-id="ed002-112">處理逾時訊息。</span><span class="sxs-lookup"><span data-stu-id="ed002-112">Process timed-out messages.</span></span>  

- <span data-ttu-id="ed002-113">記錄訊息傳輸的結果，並捨棄實際的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed002-113">Log the results of message transmission and then discard the actual messages.</span></span>
