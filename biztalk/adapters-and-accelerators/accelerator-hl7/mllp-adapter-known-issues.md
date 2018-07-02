---
title: MLLP 配接器的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MLLP adapters, known issues
- known issues, MLLP adapters
ms.assetid: 66af8fcc-981a-4a77-80b7-84824bfae608
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb90c62baebb8fc73b939c0a3ea20eb85e9b0e28
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970831"
---
# <a name="mllp-adapter-known-issues"></a><span data-ttu-id="cf5ba-102">MLLP 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="cf5ba-102">MLLP Adapter Known Issues</span></span>
<span data-ttu-id="cf5ba-103">本節包含可協助您避免最少的較低層通訊協定 (MLLP) 配接器錯誤的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-103">This section contains useful information that may help you avoid Minimal Lower Layer Protocol (MLLP) adapter errors.</span></span>  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a><span data-ttu-id="cf5ba-104">雙向 MLLP 配接器可能無法偵測出問題與通知</span><span class="sxs-lookup"><span data-stu-id="cf5ba-104">Two-way MLLP adapter might not detect a problem with an ACK</span></span>  
 <span data-ttu-id="cf5ba-105">當 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]) 接收通知 (ACK) 上的雙向的 MLLP 配接器，配接器會執行輕量型驗證上的認可，以判斷其有效性。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-105">When Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]) receives an acknowledgment (ACK) on a two-way MLLP adapter, the adapter performs a lightweight validation on the ACK to determine its validity.</span></span> <span data-ttu-id="cf5ba-106">如果找到有效，擷取 MSA1 欄位時，並根據其值，配接器會重試、 暫止，或刪除原始訊息的 ACK 已回應。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-106">If it is found to be valid, the MSA1 field is extracted, and depending on its value, the adapter retries, suspends, or deletes the original message to which the ACK was responding.</span></span> <span data-ttu-id="cf5ba-107">不過，由於配接器所執行的驗證不是完整的驗證，就可以配接器不會偵測到問題的通知。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-107">However, since the validation performed by the adapter is not a complete validation, it is possible that the adapter will not detect a problem with the ACK.</span></span> <span data-ttu-id="cf5ba-108">比方說，配接器無法判斷通知是有效的並刪除原始的訊息，而管線會判斷通知不是語式正確，並擱置的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-108">For instance, the adapter could determine that the ACK is valid, and delete the original message, whereas the pipeline would determine that the ACK was not well-formed, and suspend the ACK message.</span></span>  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a><span data-ttu-id="cf5ba-109">MLLP 效能計數器不算 Ack</span><span class="sxs-lookup"><span data-stu-id="cf5ba-109">MLLP performance counters do not count ACKs</span></span>  
 <span data-ttu-id="cf5ba-110">MLLP 效能計數器所示，效能的一個量值會是處理 MLLP 配接器的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-110">One measure of performance is the number of messages processed by an MLLP adapter, as indicated by MLLP performance counters.</span></span> <span data-ttu-id="cf5ba-111">這個計數會測量已接收或傳送的訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-111">This count measures the number of messages received or transmitted.</span></span> <span data-ttu-id="cf5ba-112">不過，計數不會衡量接收或傳送的通知數目。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-112">However, the count does not measure the number of ACKs either received or sent.</span></span>  
  
## <a name="mllp-adapter-connection-names-are-not-guaranteed-to-be-unique"></a><span data-ttu-id="cf5ba-113">不保證是唯一的 MLLP 配接器連接名稱</span><span class="sxs-lookup"><span data-stu-id="cf5ba-113">MLLP adapter connection names are not guaranteed to be unique</span></span>  
 [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]<span data-ttu-id="cf5ba-114"> 不保證唯一性的 MLLP 配接器的屬性頁面中輸入的連接名稱。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-114"> does not guarantee the uniqueness of the connection name entered in the property pages of an MLLP adapter.</span></span> <span data-ttu-id="cf5ba-115">確定該描述性及相關連接此必要欄位中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-115">Ensure that descriptive and relevant connection names are entered in this required field.</span></span> <span data-ttu-id="cf5ba-116">使用代表特定業務應用程式的連接名稱可能會很有用，嘗試了解連接的行為時。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-116">Using connection names that represent line-of-business applications can be useful when trying to understand the behavior of the connection.</span></span> <span data-ttu-id="cf5ba-117">比方說，PerfMon 計數器使用的連接名稱。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-117">For example, PerfMon counters use the connection name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf5ba-118">BTAHL7 並確保唯一性的接收位置或傳送埠名稱。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-118">BTAHL7 does ensure the uniqueness of receive locations or send port names.</span></span>  
  
## <a name="two-way-mllp-adapters-do-not-send-commit-acks-for-all-messages-in-a-batch"></a><span data-ttu-id="cf5ba-119">雙向 MLLP 配接器不會傳送認可的認可的批次中的所有訊息</span><span class="sxs-lookup"><span data-stu-id="cf5ba-119">Two-way MLLP adapters do not send Commit ACKs for all messages in a batch</span></span>  
 <span data-ttu-id="cf5ba-120">當您設定每個訊息批次處理，以產生認可的通知，並在系統傳送的批次雙向 MLLP 接收配接器，配接器只會傳送對應至第一個訊息批次中認可的通知。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-120">When you configure each message in a batch to generate a Commit ACK, and the system sends the batch to a two-way MLLP receive adapter, the adapter will only send the Commit ACK corresponding to the first message in the batch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf5ba-121">建議您，使用單向的 MLLP 配接器傳輸批次。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-121">It is recommended that you use a one-way MLLP adapter to transport batches.</span></span>  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a><span data-ttu-id="cf5ba-122">雙向 MLLP 配接器所產生的 NAK</span><span class="sxs-lookup"><span data-stu-id="cf5ba-122">NAK generated by two-way MLLP adapter</span></span>  
 <span data-ttu-id="cf5ba-123">雙向的 MLLP 配接器會擱置任何訊息，當 MLLP 配接器就會產生 NAK （負值通知），並將它放在 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-123">When a two-way MLLP adapter suspends any message, the MLLP adapter generates a NAK (negative acknowledgment) and places it in the MessageBox database.</span></span> <span data-ttu-id="cf5ba-124">這可能是未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-124">This may be unexpected behavior.</span></span> <span data-ttu-id="cf5ba-125">您可能想要移除 NAK 從 MessageBox 資料庫，或將它對應到另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-125">You may want to remove the NAK from the MessageBox database or map it into another message.</span></span>  
  
## <a name="two-way-mllp-adapter-only-supports-the-2x-message-format"></a><span data-ttu-id="cf5ba-126">雙向 MLLP 配接器只支援 2.X 訊息格式</span><span class="sxs-lookup"><span data-stu-id="cf5ba-126">Two-way MLLP adapter only supports the 2.X message format</span></span>  
 <span data-ttu-id="cf5ba-127">雙向的 MLLP 配接器目前支援僅 2.X 訊息格式。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-127">The two-way MLLP adapter currently supports only the 2.X message format.</span></span>  
  
## <a name="two-way-mllp-adapter-does-not-support-static-acknowledgments"></a><span data-ttu-id="cf5ba-128">雙向 MLLP 配接器不支援靜態通知</span><span class="sxs-lookup"><span data-stu-id="cf5ba-128">Two-way MLLP adapter does not support static acknowledgments</span></span>  
 <span data-ttu-id="cf5ba-129">雙向傳送配接器不支援處理靜態的通知。</span><span class="sxs-lookup"><span data-stu-id="cf5ba-129">The two-way send adapter does not support processing static acknowledgments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5ba-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf5ba-130">See Also</span></span>  
 [<span data-ttu-id="cf5ba-131">已知問題</span><span class="sxs-lookup"><span data-stu-id="cf5ba-131">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)