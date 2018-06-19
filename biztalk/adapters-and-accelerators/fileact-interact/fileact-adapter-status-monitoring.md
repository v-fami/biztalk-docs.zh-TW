---
title: FileAct 配接器狀態監視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 15833004-4276-4975-a0e7-8fff3c82576b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5b717a02631d47b864cc9180cba2fba673c5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223038"
---
# <a name="fileact-adapter-status-monitoring"></a><span data-ttu-id="52dc8-102">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="52dc8-102">FileAct Adapter Status Monitoring</span></span>
<span data-ttu-id="52dc8-103">在下圖說明可能的檔案傳輸，而這些狀態之間轉換的狀態。</span><span class="sxs-lookup"><span data-stu-id="52dc8-103">The possible states of a file transfer and the transitions between those states are illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="52dc8-104">![FileAct 配接器檔案傳輸狀態](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")</span><span class="sxs-lookup"><span data-stu-id="52dc8-104">![FileAct adapter file transfer states](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")</span></span>  
  
 <span data-ttu-id="52dc8-105">檔案傳輸狀態是：</span><span class="sxs-lookup"><span data-stu-id="52dc8-105">The file transfer states are:</span></span>  
  
-   <span data-ttu-id="52dc8-106">**起始**– 用戶端交涉訊息傳送至伺服器，但是尚未收到回應。</span><span class="sxs-lookup"><span data-stu-id="52dc8-106">**Initiated** – The client has sent the negotiation message to the server, but has not yet received the response.</span></span> <span data-ttu-id="52dc8-107">伺服器收到的交涉要求，但尚未傳送回應。</span><span class="sxs-lookup"><span data-stu-id="52dc8-107">The server has received the negotiation request, but has not yet sent the response.</span></span>  
  
-   <span data-ttu-id="52dc8-108">**接受**： 伺服器已接受要求，並且可在回應訊息中傳送 TransferAnswer，並且傳送仍在進行中。</span><span class="sxs-lookup"><span data-stu-id="52dc8-108">**Accepted** – The server has accepted the request and has sent the TransferAnswer in the response message, and the transfer is still in progress.</span></span>  
  
-   <span data-ttu-id="52dc8-109">**拒絕**– 伺服器已拒絕要求，並在回應訊息中，擁有 TransferAnswer，且已終止傳輸。</span><span class="sxs-lookup"><span data-stu-id="52dc8-109">**Rejected** – The server has rejected the request and has the TransferAnswer in the response message, and has terminated the transfer.</span></span>  
  
-   <span data-ttu-id="52dc8-110">**持續**– 傳送正在進行中，正在進行 （上述的定期更新）。</span><span class="sxs-lookup"><span data-stu-id="52dc8-110">**Ongoing** – The transfer is in progress and is proceeding (renewed periodically as above).</span></span>  
  
-   <span data-ttu-id="52dc8-111">**完成**– 檔案傳輸的傳送該端而言，包括摘要值的比較已順利完成。</span><span class="sxs-lookup"><span data-stu-id="52dc8-111">**Completed** – The file transfer has completed successfully as far as that side of the transfer is concerned, including the comparison of the digest value.</span></span>  
  
-   <span data-ttu-id="52dc8-112">**無法**– 檔案傳輸失敗，因為資料存取，處理時，通訊或逾時例外狀況。</span><span class="sxs-lookup"><span data-stu-id="52dc8-112">**Failed** – The file transfer has failed because of a data access, processing, communications or timeout exception.</span></span> <span data-ttu-id="52dc8-113">(注意： SWIFTNet 連結會強制執行逾時和值取決於 SWIFT)。</span><span class="sxs-lookup"><span data-stu-id="52dc8-113">(Note: Timeout is enforced by SWIFTNet Link, and the value is determined by SWIFT).</span></span>  
  
-   <span data-ttu-id="52dc8-114">**中止**– 已中止檔案傳輸 （其中端我中止的問題）。</span><span class="sxs-lookup"><span data-stu-id="52dc8-114">**Aborted** – The file transfer has been aborted (either side my issue the abort).</span></span>  
  
-   <span data-ttu-id="52dc8-115">**未知及重複**– 此狀態發生於僅由於計時。</span><span class="sxs-lookup"><span data-stu-id="52dc8-115">**Unknown and Duplicated** – This state occurs only because of timing.</span></span> <span data-ttu-id="52dc8-116">寄件者，在檔案應重新傳送標記為可能重複 (PDIndicator)。</span><span class="sxs-lookup"><span data-stu-id="52dc8-116">In the case of a sender, the file should be re-sent marked as possibly duplicated (PDIndicator).</span></span> <span data-ttu-id="52dc8-117">在接收者，當 PDIndicator 意味著，檔案可能已傳送，FileAct 配接器會檢查是否重複，而且如果找到，會傳回 TransferAnswer 的重複，這將會終止目前的嘗試。</span><span class="sxs-lookup"><span data-stu-id="52dc8-117">In the case of a receiver, when the PDIndicator implies that the file might have already been sent, the FileAct Adapter will check for the duplication, and if found, will return a TransferAnswer of Duplicated, which will terminate the current attempt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dc8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52dc8-118">See Also</span></span>  
 <span data-ttu-id="52dc8-119">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-119">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="52dc8-120">[FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-120">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="52dc8-121">[FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-121">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="52dc8-122">[FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-122">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="52dc8-123">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-123">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="52dc8-124">[FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-124">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="52dc8-125">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="52dc8-125">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 [<span data-ttu-id="52dc8-126">FileAct 配接器傳遞通知</span><span class="sxs-lookup"><span data-stu-id="52dc8-126">FileAct Adapter Delivery Notification</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)