---
title: "資料儲存輸入的 EDI 訊息的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8cbcb96-c0af-4f41-b844-f0e684a4af7c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9a395e691835f3e21622ebf5f29c2845361fb36
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-data-is-stored-for-inbound-edi-messages"></a><span data-ttu-id="cc163-102">如何儲存輸入 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-102">How Data Is Stored for Inbound EDI Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cc163-103">會執行下列命令來產生輸入的交換而傳送給它的回應的通知狀態報告項目：</span><span class="sxs-lookup"><span data-stu-id="cc163-103"> does the following to generate a status report entry for an inbound interchange and the acknowledgment sent in response to it:</span></span>  
  
1.  <span data-ttu-id="cc163-104">當輸入訊息 XML 由 EDI 接收管線傳送到 MessageBox 時，接收管線便會以下列值，在狀態報告資料存放區中建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="cc163-104">When inbound message XML is sent by the EDI receive pipeline to the MessageBox, the receive pipeline creates the following entries in the status reporting data store with the following values:</span></span>  
  
    -   <span data-ttu-id="cc163-105">針對每個接收之交換的一個狀態報告項目，其「狀態」會設定為「已接受」、「已部分接受」或「已拒絕」</span><span class="sxs-lookup"><span data-stu-id="cc163-105">One status report entry for each interchange received, with Status set to Accepted/Partially Accepted/Rejected</span></span>  
  
    -   <span data-ttu-id="cc163-106">針對每個技術 (交換) 通知 (每個交換一個) 的一個狀態報告項目，其「狀態」會設定為「已產生」</span><span class="sxs-lookup"><span data-stu-id="cc163-106">One status report entry for each technical (interchange) acknowledgment, one per interchange, with Status set to Generated</span></span>  
  
    -   <span data-ttu-id="cc163-107">針對每個功能通知 (若是 X12 則為每個群組一個，若是 EDIFACT 則為全部群組共一個) 的一個狀態報告項目，其「狀態」會設定為「已產生」</span><span class="sxs-lookup"><span data-stu-id="cc163-107">One status report entry for each functional acknowledgment, one per group in X12 and one for all groups in EDIFACT, with Status set to Generated.</span></span>  
  
2.  <span data-ttu-id="cc163-108">在傳送管線將通知傳送給交易夥伴後，EDI 傳送管線便會將「交換通知狀態」和「功能通知狀態」項目適當地更新為「已傳送」。</span><span class="sxs-lookup"><span data-stu-id="cc163-108">After the send pipeline has sent the acknowledgments to the trading partner, the EDI send pipeline updates the Interchange ACK status and Functional ACK status entries to Sent, as appropriate.</span></span> <span data-ttu-id="cc163-109">交換狀態項目不會進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="cc163-109">No changes are made to the Interchange status entry.</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-inbound-interchanges"></a><span data-ttu-id="cc163-110">接收管線為輸入交換所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-110">Data Stored by the Receive Pipeline for Inbound Interchanges</span></span>  
 <span data-ttu-id="cc163-111">接收管線會在狀態報告資料存放區中，針對其所接收的每個交換建立記錄。</span><span class="sxs-lookup"><span data-stu-id="cc163-111">The receive pipeline creates a record in the status report data store for each interchange that it receives.</span></span> <span data-ttu-id="cc163-112">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="cc163-112">The data stored includes:</span></span>  
  
-   <span data-ttu-id="cc163-113">記錄類型 = 交換狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-113">Record Type = Interchange Status</span></span>  
  
-   <span data-ttu-id="cc163-114">交換方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="cc163-114">Interchange Direction = Receive</span></span>  
  
-   <span data-ttu-id="cc163-115">交換接收者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-115">Interchange Receiver = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-116">交換傳送者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-116">Interchange Sender = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-117">交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-117">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-118">交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-118">Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-119">交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-119">Interchange Control ID = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-120">交換狀態： 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-120">Interchange Status: Update Data</span></span>  
  
-   <span data-ttu-id="cc163-121">交換中群組的計數 = 更新資料 (在 EDIFACT 群組中為選擇性，而且如果不存在，其值會是「不適用」)</span><span class="sxs-lookup"><span data-stu-id="cc163-121">Count of Groups in Interchange = Update Data (In EDIFACT Groups are optional and if not present, valued as ‘Not Applicable’)</span></span>  
  
-   <span data-ttu-id="cc163-122">交換接收連接埠識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-122">Interchange Receive Port ID = Update Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-generated-in-response-to-an-inbound-interchange"></a><span data-ttu-id="cc163-123">由接收管線針對回應輸入交換而產生之每個技術通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-123">Data Stored by the Receive Pipeline for Each Technical Acknowledgment Generated in Response to an Inbound Interchange</span></span>  
 <span data-ttu-id="cc163-124">傳送管線會在狀態報告資料存放區中，針對其所傳送的每個技術通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="cc163-124">The send pipeline creates a record in the status report data store for each technical acknowledgment that it sends.</span></span> <span data-ttu-id="cc163-125">X12 類型的技術通知是 TA1，EDIFACT 類型的技術通知則是只有 UCI 區段的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="cc163-125">The technical acknowledgement is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT.</span></span> <span data-ttu-id="cc163-126">此項目所需要的多數資料，都會在交換的標頭/結尾區段中 (ISA/IEA 或 UNB/UNZ) 提供。</span><span class="sxs-lookup"><span data-stu-id="cc163-126">Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ).</span></span> <span data-ttu-id="cc163-127">其他資料則由傳送埠屬性提供。</span><span class="sxs-lookup"><span data-stu-id="cc163-127">Other data is available from send port properties.</span></span> <span data-ttu-id="cc163-128">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="cc163-128">The data stored includes:</span></span>  
  
-   <span data-ttu-id="cc163-129">記錄類型 = 交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-129">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="cc163-130">交換通知方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="cc163-130">Interchange ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="cc163-131">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-131">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-132">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-132">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-133">交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-133">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-134">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-134">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-135">交換通知狀態 =\<預期或不適用\>。</span><span class="sxs-lookup"><span data-stu-id="cc163-135">Interchange ACK Status = \< Expected or Not Applicable\>.</span></span> <span data-ttu-id="cc163-136">如果技術通知經過設定，或是在內送交換中有指定值，狀態 = 預期。</span><span class="sxs-lookup"><span data-stu-id="cc163-136">If the technical ACK is configured or valued in the incoming interchange, status = Expected.</span></span> <span data-ttu-id="cc163-137">否則，狀態 = 不適用。</span><span class="sxs-lookup"><span data-stu-id="cc163-137">Otherwise, status = Not Applicable.</span></span>  
  
-   <span data-ttu-id="cc163-138">交換通知控制識別碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-138">Interchange ACK Control ID= \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-139">交換通知日期 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-139">Interchange ACK Date = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-140">交換通知時間 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-140">Interchange ACK Time = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-141">通知/動作代碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-141">ACK/Action Code = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-142">通知說明碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-142">ACK Note Code = \<not valued\></span></span>  
  
## <a name="data-updated-by-the-send-pipeline-for-each-technical-acknowledgment-generated-in-response-to-inbound-interchanges"></a><span data-ttu-id="cc163-143">由傳送管線針對回應輸入交換而產生之每個技術通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-143">Data Updated by the Send Pipeline for Each Technical Acknowledgment Generated in Response to Inbound Interchanges</span></span>  
 <span data-ttu-id="cc163-144">對於傳送管線所傳送的每個技術通知，傳送管線都會更新相互關聯之接收交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="cc163-144">For each technical acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange.</span></span> <span data-ttu-id="cc163-145">資料的來源會是由「傳送管線」建立的交換信封。</span><span class="sxs-lookup"><span data-stu-id="cc163-145">The source for the data will be the Interchange envelopes created by the Send Pipeline.</span></span>  
  
 <span data-ttu-id="cc163-146">「EDI 組合器」會使用內送通知中 UCI 和 TA1 區段內的資料，來找到資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc163-146">The EDI Assembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="cc163-147">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="cc163-147">Fields in ACK</span></span>|<span data-ttu-id="cc163-148">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="cc163-148">Fields in Data store</span></span>|<span data-ttu-id="cc163-149">註解</span><span class="sxs-lookup"><span data-stu-id="cc163-149">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="cc163-150">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-150">Interchange Sender ID</span></span>|<span data-ttu-id="cc163-151">交換接收方</span><span class="sxs-lookup"><span data-stu-id="cc163-151">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="cc163-152">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-152">Interchange Receiver ID</span></span>|<span data-ttu-id="cc163-153">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="cc163-153">Interchange Sender</span></span>|-|  
|-|<span data-ttu-id="cc163-154">交換日期</span><span class="sxs-lookup"><span data-stu-id="cc163-154">Interchange Date</span></span>|-|  
|<span data-ttu-id="cc163-155">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="cc163-155">Interchange Control Number</span></span>|<span data-ttu-id="cc163-156">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-156">Interchange Control ID</span></span>|-|  
|-|<span data-ttu-id="cc163-157">交換方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="cc163-157">Interchange Direction = Receive</span></span>|<span data-ttu-id="cc163-158">確保唯一性而保留之交換實例的必要項</span><span class="sxs-lookup"><span data-stu-id="cc163-158">Required in preserved interchange scenario for uniqueness</span></span>|  
|<span data-ttu-id="cc163-159">記錄類型</span><span class="sxs-lookup"><span data-stu-id="cc163-159">Record Type</span></span>|<span data-ttu-id="cc163-160">交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-160">Interchange ACK Status</span></span>|-|  
  
 <span data-ttu-id="cc163-161">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="cc163-161">The data stored includes:</span></span>  
  
-   <span data-ttu-id="cc163-162">記錄類型 = 交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-162">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="cc163-163">交換通知方向 = 傳送 - 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-163">Interchange ACK Direction = Send- Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-164">交換通知狀態 = 已處理或已傳送 - 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-164">Interchange ACK Status = Processed or Sent – Update Data</span></span>  
  
-   <span data-ttu-id="cc163-165">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-165">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-166">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-166">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-167">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="cc163-167">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-168">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-168">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-169">交換通知控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-169">Interchange ACK Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="cc163-170">交換通知日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-170">Interchange ACK Date = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-171">交換通知時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-171">Interchange ACK Time = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-172">通知/動作代碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-172">ACK/Action Code = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-173">通知說明碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-173">ACK Note Code = Existing Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-generated-in-response-to-an-inbound-interchange"></a><span data-ttu-id="cc163-174">由接收管線針對回應輸入交換而產生之每個功能通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-174">Data Stored by the Receive Pipeline for Each Functional Acknowledgment Generated in Response to an Inbound Interchange</span></span>  
 <span data-ttu-id="cc163-175">傳送管線會在狀態報告資料存放區中，針對其所傳送的每個功能通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="cc163-175">The send pipeline creates a record in the status report data store for each functional acknowledgment that it sends.</span></span> <span data-ttu-id="cc163-176">傳送管線會在狀態報告資料存放區中，針對其所傳送的每個功能通知 (為了回應於接收的交換) 建立記錄。</span><span class="sxs-lookup"><span data-stu-id="cc163-176">The send pipeline creates a record of each functional acknowledgment sent (in response to an interchange received) in the status report data store.</span></span> <span data-ttu-id="cc163-177">如果 EDIFACT 中不存在任何群組，這時依然會建立一個功能通知。</span><span class="sxs-lookup"><span data-stu-id="cc163-177">If no group is present in EDIFACT, one functional ACK will still be created.</span></span> <span data-ttu-id="cc163-178">功能通知狀態報告項目中將會填入功能群組標頭/結尾 (GS/GE 或 UNG/UNE)。</span><span class="sxs-lookup"><span data-stu-id="cc163-178">The functional ACK status report entry will be populated from the functional group header/trailer (GS/GE or UNG/UNE).</span></span> <span data-ttu-id="cc163-179">X12 類型的技術通知是 997，EDIFACT 類型的技術通知為完整的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="cc163-179">The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT.</span></span> <span data-ttu-id="cc163-180">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="cc163-180">The data stored includes:</span></span>  
  
-   <span data-ttu-id="cc163-181">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-181">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="cc163-182">功能通知方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="cc163-182">Functional ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="cc163-183">功能通知狀態 =\<預期或不適用\>。</span><span class="sxs-lookup"><span data-stu-id="cc163-183">Functional ACK Status = \< Expected or Not Applicable\>.</span></span> <span data-ttu-id="cc163-184">如果有選取 PAM 中的 [功能通知] 索引標籤，狀態便會設定為「預期」。</span><span class="sxs-lookup"><span data-stu-id="cc163-184">If the functional acknowledgment tab in PAM is selected, status will set to Expected.</span></span> <span data-ttu-id="cc163-185">否則，狀態會設定為「不適用」。</span><span class="sxs-lookup"><span data-stu-id="cc163-185">Otherwise, status will be set to Not Applicable.</span></span>  
  
-   <span data-ttu-id="cc163-186">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-186">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-187">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-187">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-188">交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-188">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-189">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="cc163-189">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="cc163-190">群組控制編號 = 更新資料 (相互關聯的必要項。</span><span class="sxs-lookup"><span data-stu-id="cc163-190">Group Control Number = Update Data (required for correlation.</span></span> <span data-ttu-id="cc163-191">在 EDIFACT 中如果不存在任何群組區段，便會使用 UNH.1 指定這個欄位的值)。</span><span class="sxs-lookup"><span data-stu-id="cc163-191">In EDIFACT if no group segments present this field is valued using UNH.1)</span></span>  
  
-   <span data-ttu-id="cc163-192">功能識別代碼 = 更新資料 (如果不存在群組，就不會在 EDIFACT 中指定值)</span><span class="sxs-lookup"><span data-stu-id="cc163-192">Functional ID Code = Update Data (not valued in EDIFACT if group is not present)</span></span>  
  
-   <span data-ttu-id="cc163-193">交易集的計數 = 資料 (在 EDIFACT 中，如果存在 UNG/UNE，此項便會對應至 UNE.1，如果不存在群組區段，則會對應至 UNZ.1)</span><span class="sxs-lookup"><span data-stu-id="cc163-193">Count of Transaction Sets = Data (in EDIFACT this is mapped to UNE.1 while UNG/UNE are present or UNZ.1 if no group segments are present)</span></span>  
  
-   <span data-ttu-id="cc163-194">功能通知交換控制識別碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-194">Functional ACK Interchange Control ID= \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-195">功能通知交換日期 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-195">Functional ACK Interchange Date = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-196">功能通知交換時間 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-196">Functional ACK Interchange Time = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-197">計數傳送交易集的 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-197">Count of Transaction Sets Delivered = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-198">交易集已接受的計數 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-198">Count of Transaction Sets Accepted = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-199">通知/動作代碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-199">ACK/Action Code = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-200">錯誤/語法錯誤碼 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-200">Error/Syntax Error Code  = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-201">其他 X12 通知錯誤的程式碼 2 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-201">Additional X12 ACK Error Code 2 = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-202">其他 X12 通知錯誤碼 3 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-202">Additional X12 ACK Error Code 3 = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-203">其他 X12 通知錯誤的程式碼 4 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-203">Additional X12 ACK Error Code 4 = \<not valued\></span></span>  
  
-   <span data-ttu-id="cc163-204">其他 X12 通知錯誤碼 5 =\<不值\></span><span class="sxs-lookup"><span data-stu-id="cc163-204">Additional X12 ACK Error Code 5 = \<not valued\></span></span>  
  
## <a name="data-updated-by-the-send-pipeline-for-each-functional-acknowledgment-generated-in-response-to-inbound-interchanges"></a><span data-ttu-id="cc163-205">由傳送管線針對回應輸入交換而產生之每個功能通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-205">Data Updated by the Send Pipeline for Each Functional Acknowledgment Generated in Response to Inbound Interchanges</span></span>  
 <span data-ttu-id="cc163-206">對於每個傳送管線所傳送的功能通知，傳送管線都會更新相互關聯之接收交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="cc163-206">For each functional acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange.</span></span> <span data-ttu-id="cc163-207">資料的來源會是由「傳送管線」建立的交換信封。</span><span class="sxs-lookup"><span data-stu-id="cc163-207">The source for the data will be the Interchange envelopes created by the Send Pipeline.</span></span>  
  
 <span data-ttu-id="cc163-208">「EDI 組合器」會使用內送通知中交換和群組標頭區段內的資料，來找到資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc163-208">The EDI Assembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="cc163-209">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="cc163-209">Fields in ACK</span></span>|<span data-ttu-id="cc163-210">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="cc163-210">Fields in Data store</span></span>|<span data-ttu-id="cc163-211">註解</span><span class="sxs-lookup"><span data-stu-id="cc163-211">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="cc163-212">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-212">Interchange Sender ID</span></span>|<span data-ttu-id="cc163-213">交換接收方</span><span class="sxs-lookup"><span data-stu-id="cc163-213">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="cc163-214">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-214">Interchange Receiver ID</span></span>|<span data-ttu-id="cc163-215">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="cc163-215">Interchange Sender</span></span>|-|  
|<span data-ttu-id="cc163-216">交換日期</span><span class="sxs-lookup"><span data-stu-id="cc163-216">Interchange Date</span></span>|<span data-ttu-id="cc163-217">交換日期</span><span class="sxs-lookup"><span data-stu-id="cc163-217">Interchange Date</span></span>|-|  
|<span data-ttu-id="cc163-218">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="cc163-218">Interchange Control Number</span></span>|<span data-ttu-id="cc163-219">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="cc163-219">Interchange Control ID</span></span>|-|  
|<span data-ttu-id="cc163-220">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="cc163-220">Group Control Number</span></span>|<span data-ttu-id="cc163-221">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="cc163-221">Group Control Number</span></span>|<span data-ttu-id="cc163-222">在 EDIFACT 中為選擇項</span><span class="sxs-lookup"><span data-stu-id="cc163-222">Optional in EDIFACT</span></span>|  
|-|<span data-ttu-id="cc163-223">交換方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="cc163-223">Interchange Direction = Receive</span></span>|<span data-ttu-id="cc163-224">確保唯一性而保留之交換實例的必要項</span><span class="sxs-lookup"><span data-stu-id="cc163-224">Required in preserved interchange scenario for uniqueness</span></span>|  
|<span data-ttu-id="cc163-225">記錄類型</span><span class="sxs-lookup"><span data-stu-id="cc163-225">Record Type</span></span>|<span data-ttu-id="cc163-226">功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-226">Functional ACK Status</span></span>|-|  
  
 <span data-ttu-id="cc163-227">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="cc163-227">The data stored includes:</span></span>  
  
-   <span data-ttu-id="cc163-228">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="cc163-228">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="cc163-229">功能通知方向 = 傳送 - 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-229">Functional ACK Direction = Send – Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-230">功能通知狀態 = 已傳送/處理 - 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-230">Functional ACK Status = Sent/Processed – Update Data</span></span>  
  
-   <span data-ttu-id="cc163-231">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-231">Interchange Receiver =  Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-232">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-232">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-233">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="cc163-233">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-234">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-234">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-235">群組控制編號 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-235">Group Control Number = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-236">功能識別代碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-236">Functional ID Code = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-237">交易集的計數 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-237">Count of Transaction Sets = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-238">功能通知交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-238">Functional ACK Interchange Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="cc163-239">功能通知交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-239">Functional ACK Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-240">功能通知交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="cc163-240">Functional ACK Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="cc163-241">已接收交易集的計數 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-241">Count of Transaction Sets Received = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-242">已接受交易集的計數 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-242">Count of Transaction Sets Accepted = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-243">通知/動作代碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-243">ACK/Action Code = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-244">錯誤/語法錯誤碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-244">Error/Syntax Error Code  = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-245">其他 X12 通知錯誤碼 2 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-245">Additional X12 ACK Error Code 2 = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-246">其他 X12 通知錯誤碼 3 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-246">Additional X12 ACK Error Code 3 = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-247">其他 X12 通知錯誤碼 4 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-247">Additional X12 ACK Error Code 4 = Existing Data</span></span>  
  
-   <span data-ttu-id="cc163-248">其他 X12 通知錯誤碼 5 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="cc163-248">Additional X12 ACK Error Code 5 = Existing Data</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc163-249">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc163-249">See Also</span></span>  
 <span data-ttu-id="cc163-250">[資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="cc163-250">[How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="cc163-251">如何儲存輸出 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="cc163-251">How Data Is Stored for Outbound EDI Messages</span></span>](../core/how-data-is-stored-for-outbound-edi-messages.md)