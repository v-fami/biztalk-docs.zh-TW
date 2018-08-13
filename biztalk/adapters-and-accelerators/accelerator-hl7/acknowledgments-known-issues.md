---
title: 通知的已知的問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, acknowledgements
- acknowledgements, known issues
ms.assetid: cb45f80e-ba89-4b3f-a770-4b1cf9b8e220
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f585c9f0b147f50bd915bb757a3ed3c09a56ee8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966151"
---
# <a name="acknowledgments-known-issues"></a><span data-ttu-id="c5076-102">通知的已知的問題</span><span class="sxs-lookup"><span data-stu-id="c5076-102">Acknowledgments Known Issues</span></span>
<span data-ttu-id="c5076-103">本節包含可協助您避免通知 (ACK) 錯誤的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="c5076-103">This section contains useful information that may help you avoid acknowledgment (ACK) errors.</span></span>  
  
## <a name="hl7-v21-acknowledgment-message-accepted-even-if-it-contains-msa6-field"></a><span data-ttu-id="c5076-104">HL7 V2.1 通知訊息，即使它包含 MSA6 欄位接受</span><span class="sxs-lookup"><span data-stu-id="c5076-104">HL7 V2.1 acknowledgment message accepted even if it contains MSA6 field</span></span>  
 <span data-ttu-id="c5076-105">Microsoft [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會接受 HL7 V2.1 通知訊息，即使包含 MSA6 欄位。</span><span class="sxs-lookup"><span data-stu-id="c5076-105">Microsoft [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will accept a HL7 V2.1 acknowledgment message even if contains the MSA6 field.</span></span>  
  
## <a name="msa-01-value-not-generated-for-commit-acknowledgment-errors"></a><span data-ttu-id="c5076-106">不產生認可通知錯誤的 MSA-01 值</span><span class="sxs-lookup"><span data-stu-id="c5076-106">MSA-01 value not generated for commit acknowledgment errors</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="c5076-107"> 不會產生認可通知錯誤 (CE) 的 MSA-01 通知程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5076-107"> does not generate an MSA-01 acknowledgment code for commit acknowledgments errors (CE).</span></span>  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a><span data-ttu-id="c5076-108">雙向 MLLP 配接器可能無法偵測出問題與通知</span><span class="sxs-lookup"><span data-stu-id="c5076-108">Two-way MLLP adapter might not detect a problem with an ACK</span></span>  
 <span data-ttu-id="c5076-109">當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]收到 ACK 在雙向的 MLLP 配接器，配接器會執行輕量型驗證上的認可，以判斷其有效性。</span><span class="sxs-lookup"><span data-stu-id="c5076-109">When [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives an ACK on a two-way MLLP adapter, the adapter performs a lightweight validation on the ACK to determine its validity.</span></span> <span data-ttu-id="c5076-110">如果找到有效，擷取 MSA1 欄位時，並根據其值，配接器會重試、 暫止，或刪除原始訊息的 ACK 已回應。</span><span class="sxs-lookup"><span data-stu-id="c5076-110">If it is found to be valid, the MSA1 field is extracted, and depending on its value, the adapter retries, suspends, or deletes the original message to which the ACK was responding.</span></span> <span data-ttu-id="c5076-111">不過，由於配接器所執行的驗證不是完整的驗證，就可以配接器不會偵測到問題的通知。</span><span class="sxs-lookup"><span data-stu-id="c5076-111">However, since the validation performed by the adapter is not a complete validation, it is possible that the adapter will not detect a problem with the ACK.</span></span> <span data-ttu-id="c5076-112">比方說，配接器無法判斷通知是有效的並刪除原始的訊息，而管線會判斷通知不是語式正確，並擱置的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="c5076-112">For instance, the adapter could determine that the ACK is valid, and delete the original message, whereas the pipeline would determine that the ACK was not well-formed, and suspend the ACK message.</span></span>  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a><span data-ttu-id="c5076-113">V2。有多個錯誤的 XML 通知將無法通過驗證</span><span class="sxs-lookup"><span data-stu-id="c5076-113">V2.XML ACKs with multiple errors will fail validation</span></span>  
 <span data-ttu-id="c5076-114">如果內送的 V2。XML 訊息包含多個錯誤，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器可能會產生 V2。在 [錯誤] 欄位中的多個錯誤的 XML 通知。</span><span class="sxs-lookup"><span data-stu-id="c5076-114">If an incoming V2.XML message contains more than one error, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser may generate a V2.XML ACK with more than one error in the error field.</span></span> <span data-ttu-id="c5076-115">V2。XML 通知將無法通過驗證，因為 HL7 標準可讓您指定剖析器可以報告在 V2 中的一個錯誤。XML 通知錯誤的欄位。</span><span class="sxs-lookup"><span data-stu-id="c5076-115">Such a V2.XML ACK will fail validation, because the HL7 standard specifies that the parser can report only one error in a V2.XML ACK error field.</span></span>  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a><span data-ttu-id="c5076-116">MLLP 效能計數器不算 Ack</span><span class="sxs-lookup"><span data-stu-id="c5076-116">MLLP performance counters do not count ACKs</span></span>  
 <span data-ttu-id="c5076-117">一種測量[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]MLLP 效能計數器所示，效能是 MLLP 配接器所處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="c5076-117">One measure of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performance is the number of messages processed by an MLLP adapter, as indicated by MLLP performance counters.</span></span> <span data-ttu-id="c5076-118">這個計數會測量已接收或傳送的訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="c5076-118">This count measures the number of messages received or transmitted.</span></span> <span data-ttu-id="c5076-119">不過，計數不會衡量接收或傳送的通知數目。</span><span class="sxs-lookup"><span data-stu-id="c5076-119">However, the count does not measure the number of ACKs either received or sent.</span></span>  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a><span data-ttu-id="c5076-120">雙向 MLLP 配接器所產生的 NAK</span><span class="sxs-lookup"><span data-stu-id="c5076-120">NAK generated by two-way MLLP adapter</span></span>  
 <span data-ttu-id="c5076-121">雙向的 MLLP 配接器會擱置訊息，當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生 NAK （負值通知），並將它放置在 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5076-121">When a two-way MLLP adapter suspends a message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a NAK (negative acknowledgment) and places it in the MessageBox database.</span></span> <span data-ttu-id="c5076-122">這可能是未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="c5076-122">This may be unexpected behavior.</span></span> <span data-ttu-id="c5076-123">您可能想要移除 NAK 從 MessageBox 資料庫，或將它對應到另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="c5076-123">You may want to remove the NAK from the MessageBox database or map it into another message.</span></span>  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a><span data-ttu-id="c5076-124">資料類型的通知設定為批次訊息</span><span class="sxs-lookup"><span data-stu-id="c5076-124">Data type of an ACK to a batch message</span></span>  
 <span data-ttu-id="c5076-125">在產生回應的批次訊息的 ACK 訊息，GUID，而不是根據批次訊息中的 [MSH10] 欄位的資料類型，將會 MSH10 欄位 (訊息控制項 ID)。</span><span class="sxs-lookup"><span data-stu-id="c5076-125">In an ACK message generated in response to a batch message, the MSH10 field (message control ID) will be a GUID, rather than being based on the data type of the MSH10 field in the batch message.</span></span>  
  
## <a name="generated-acknowledgments-doc-type"></a><span data-ttu-id="c5076-126">產生的通知文件類型</span><span class="sxs-lookup"><span data-stu-id="c5076-126">Generated acknowledgments DOC type</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="c5076-127"> 產生使用文件類型的通知 http://Microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF 或 http://Microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF 。</span><span class="sxs-lookup"><span data-stu-id="c5076-127"> generates acknowledgments using the DOC type http://Microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF or http://Microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.</span></span> <span data-ttu-id="c5076-128">如果您的目的合作對象使用不同的命名空間，您必須套用本文中對應的傳送埠;否則，您可能會發生序列化錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5076-128">If your destination party uses a different namespace, you must apply a body map in the send port; otherwise, you may encounter serialization errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5076-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5076-129">See Also</span></span>  
 [<span data-ttu-id="c5076-130">已知問題</span><span class="sxs-lookup"><span data-stu-id="c5076-130">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)