---
title: EDI 通知的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a769a78e-8a49-4aa4-899e-e9f54fdd5f37
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f02ef54ed8786f8ead12e16fad880040dbcadc8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262238"
---
# <a name="known-issues-with-edi-acknowledgments"></a><span data-ttu-id="e912e-102">EDI 通知的已知問題</span><span class="sxs-lookup"><span data-stu-id="e912e-102">Known Issues with EDI Acknowledgments</span></span>
<span data-ttu-id="e912e-103">本主題說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中有關 EDI 通知的已知問題。</span><span class="sxs-lookup"><span data-stu-id="e912e-103">This topic describes known issues with EDI acknowledgments in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="ak102-in-a-997-acknowledgment-can-be-negative"></a><span data-ttu-id="e912e-104">997 通知中的 AK102 可能為負值</span><span class="sxs-lookup"><span data-stu-id="e912e-104">AK102 in a 997 Acknowledgment Can Be Negative</span></span>  
 <span data-ttu-id="e912e-105">X12 997 通知中的 AK102 資料元素 (群組控制編號) 可能為負值。</span><span class="sxs-lookup"><span data-stu-id="e912e-105">The AK102 data element (group control number) in an X12 997 acknowledgment can be a negative value.</span></span> <span data-ttu-id="e912e-106">即使負值的群組控制編號沒有意義，含負 AK102 資料元素的通知仍然會通過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="e912e-106">An acknowledgment with a negative AK102 data element will pass the validation performed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], even though a negative group control number is not meaningful.</span></span>  
  
## <a name="a-contrl-receipt-may-report-a-status-of-accepted-when-part-of-the-message-is-rejected"></a><span data-ttu-id="e912e-107">CONTRL 回條可能在部分訊息遭拒時報告已接受狀態</span><span class="sxs-lookup"><span data-stu-id="e912e-107">A CONTRL Receipt May Report a Status of Accepted when Part of the Message Is Rejected</span></span>  
 <span data-ttu-id="e912e-108">CONTRL 回條 (EDIFACT 技術通知) 只會在內送 EDIFACT 訊息發生重複或是信封中發生錯誤 (例如，字元集發生問題) 時報告「已拒絕」狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-108">A CONTRL receipt (EDIFACT technical acknowledgment) reports a status of “Rejected” only when the incoming EDIFACT message is a duplicate or there are errors in the envelope (for example, an issue with the character set).</span></span> <span data-ttu-id="e912e-109">不同於 X12 在 TA1 通知中 TA104 欄位，EDIFACT 不會在 CONTRL 技術通知中報告「交換已接受，發生錯誤」狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-109">EDIFACT does not report a state of “Interchange accepted with errors” in the CONTRL technical acknowledgment, as X12 does in the TA104 field in a TA1 acknowledgment.</span></span> <span data-ttu-id="e912e-110">若已接受部分 EDIFACT 訊息，CONTRL 技術通知將會報告「已接受」。</span><span class="sxs-lookup"><span data-stu-id="e912e-110">If part of the EDIFACT message is accepted, the CONTRL technical acknowledgment will report “Accepted”.</span></span> <span data-ttu-id="e912e-111">在一些情況下，部分訊息雖然將遭到拒絕，但是 CONTRL 通知仍會報告「已接受」狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-111">In some scenarios, part of the message will be rejected, but the CONTRL acknowledgment will still report a status of “Accepted”.</span></span> <span data-ttu-id="e912e-112">在這種情況下，UCI5 元素可能會報告此等錯誤。</span><span class="sxs-lookup"><span data-stu-id="e912e-112">In such scenarios, the UCI5 element may report the error.</span></span>  
  
## <a name="x12-acknowledgments-will-show-accepted-for-a-preserved-interchange-suspend-interchange-on-error-when-a-group-header-or-trailer-is-in-error"></a><span data-ttu-id="e912e-113">群組標題或結尾發生錯誤時，X12 通知會顯示已接受保留的交換 (發生錯誤時暫停交換)</span><span class="sxs-lookup"><span data-stu-id="e912e-113">X12 Acknowledgments Will Show Accepted for a Preserved Interchange (Suspend Interchange on Error) When a Group Header or Trailer is in Error</span></span>  
 <span data-ttu-id="e912e-114">如果 X12 訊息的輸入批次處理選項設定為「保留交換 - 發生錯誤時暫停交換」，而且群組標題或結尾內有一個欄位無效，則 TA1 和 997 通知中將報告「已接受」狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-114">If the inbound batch processing option for an X12 message is set to “Preserve Interchange – suspend interchange on error”, and a field in the group header or trailer is invalid, the status will be reported as Accepted in both TA1 and 997 acknowledgments.</span></span> <span data-ttu-id="e912e-115">EDI 狀態報告和交易集詳細資料也會指出「已接受」的狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-115">The EDI status report and transaction set details will also indicate a status of Accepted.</span></span> <span data-ttu-id="e912e-116">即使交換將遭擱置，也會出現這種情形，而且「事件檢視器」中的錯誤會指出交換已經遭擱置。</span><span class="sxs-lookup"><span data-stu-id="e912e-116">This occurs even though the interchange will be suspended, and an error in the Event Viewer will indicate that the interchange was suspended.</span></span>  
  
 <span data-ttu-id="e912e-117">TA1 通知會顯示「已接受」的狀態，因為它的目的在於驗證 ISA 標頭和 ISA 結尾的正確性，不是 GS 標頭和 GE 結尾的正確性。</span><span class="sxs-lookup"><span data-stu-id="e912e-117">The TA1 acknowledgment will show a status of Accepted because it is intended to verify the correctness of the ISA header and IEA trailer, but not the correctness of the GS header and GE trailer.</span></span> <span data-ttu-id="e912e-118">然而，997 通知還是會顯示「已接受」的狀態。</span><span class="sxs-lookup"><span data-stu-id="e912e-118">However, the 997 acknowledgment will also show a status of Accepted.</span></span>  
  
## <a name="if-groups-in-an-interchange-have-the-same-name-the-status-report-will-show-twice-as-many-acknowledgments"></a><span data-ttu-id="e912e-119">若交換中的群組有相同名稱，則狀態報告會顯示兩倍的通知。</span><span class="sxs-lookup"><span data-stu-id="e912e-119">If groups in an interchange have the same name, the status report will show twice as many acknowledgments</span></span>  
 <span data-ttu-id="e912e-120">若 BizTalk Server 處理的 EDI 交換有多個群組名稱相同，EDI 交換和相互關聯的 ACK 狀態報表，會列出比預期多一倍的功能通知。</span><span class="sxs-lookup"><span data-stu-id="e912e-120">If BizTalk Server processes an EDI interchange with multiple groups that have the same name, the EDI Interchange and Correlated ACK status report will list twice as many functional acknowledgments as expected.</span></span> <span data-ttu-id="e912e-121">例如，若某個交換中有兩個群組的名稱相同，則狀態報告會列出四則通知而不是兩則通知。</span><span class="sxs-lookup"><span data-stu-id="e912e-121">For example, if two groups in an interchange have the same name, the status report will list four acknowledgments, rather than two.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e912e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e912e-122">See Also</span></span>  
 <span data-ttu-id="e912e-123">[EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md) </span><span class="sxs-lookup"><span data-stu-id="e912e-123">[Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md) </span></span>  
 <span data-ttu-id="e912e-124">[傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="e912e-124">[Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md) </span></span>  
 <span data-ttu-id="e912e-125">[處理接收的通知](../core/processing-a-received-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="e912e-125">[Processing a Received Acknowledgment](../core/processing-a-received-acknowledgment.md) </span></span>  
 [<span data-ttu-id="e912e-126">設定 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="e912e-126">Configuring EDI Acknowledgments</span></span>](../core/configuring-edi-acknowledgments.md)