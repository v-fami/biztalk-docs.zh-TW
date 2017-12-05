---
title: "資料如何儲存輸出 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e576fc-37fd-417d-ae68-607a0a8bcc0a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f98d5113c63e29f3f4b85834b7ca1aa0836d0a5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-data-is-stored-for-outbound-edi-messages"></a><span data-ttu-id="3796f-102">如何儲存輸出 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-102">How Data Is Stored for Outbound EDI Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3796f-103"> 會針對輸出交換，進行下列作業以產生狀態報告項目：</span><span class="sxs-lookup"><span data-stu-id="3796f-103"> does the following to generate a status report entry for an outbound interchange:</span></span>  
  
1.  <span data-ttu-id="3796f-104">輸出訊息 XML 傳送到 EDI 傳送管線時，傳送管線便會以下列的值，在狀態報告資料存放區中建立項目：</span><span class="sxs-lookup"><span data-stu-id="3796f-104">When outbound message XML is sent to the EDI send pipeline, the send pipeline creates an entry in the status reporting data store with the following values:</span></span>  
  
    -   <span data-ttu-id="3796f-105">交換狀態項目已設定為「已處理」</span><span class="sxs-lookup"><span data-stu-id="3796f-105">Interchange status entry is set to Processed</span></span>  
  
    -   <span data-ttu-id="3796f-106">交換通知狀態項目 (每個交換一個) 已設定為「預期」</span><span class="sxs-lookup"><span data-stu-id="3796f-106">Interchange ACK status entry (one per interchange) is set to Expected</span></span>  
  
    -   <span data-ttu-id="3796f-107">功能通知狀態項目 (X12 中每個群組一個，EDIFACT 中所有群組共用一個) 已設定為「預期」</span><span class="sxs-lookup"><span data-stu-id="3796f-107">Functional ACK status entries (one per group in X12, one for all groups in EDIFACT) are set to Expected</span></span>  
  
2.  <span data-ttu-id="3796f-108">在 EDI 訊息傳送至交易夥伴，且已從交易夥伴傳回通知後，接收通知的 EDI 接收管線就會視情況將交換狀態、交換通知狀態和功能通知狀態項目，更新為「已接受」/「已部分接受」/「已拒絕」。</span><span class="sxs-lookup"><span data-stu-id="3796f-108">After the EDI message has been sent to the trading partner, and the acknowledgment has been returned from the trading partner, the EDI receive pipeline that receives the acknowledgment updates the Interchange status, the Interchange ACK status, and the Functional ACK status entries to Accepted/Partially Accepted/Rejected, as appropriate.</span></span>  
  
## <a name="data-stored-by-the-send-pipeline-for-outbound-interchanges"></a><span data-ttu-id="3796f-109">傳送管線所儲存的輸出交換資料</span><span class="sxs-lookup"><span data-stu-id="3796f-109">Data Stored by the Send Pipeline for Outbound Interchanges</span></span>  
 <span data-ttu-id="3796f-110">傳送管線會在狀態報告資料存放區中，針對其所傳送的每個交換建立記錄。</span><span class="sxs-lookup"><span data-stu-id="3796f-110">The send pipeline creates a record in the status report data store for each interchange that it sends.</span></span> <span data-ttu-id="3796f-111">此項目所需要的多數資料，都會在交換的標頭/結尾區段中 (ISA/IEA 或 UNB/UNZ) 提供。</span><span class="sxs-lookup"><span data-stu-id="3796f-111">Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ).</span></span> <span data-ttu-id="3796f-112">其他資料則由傳送埠屬性提供。</span><span class="sxs-lookup"><span data-stu-id="3796f-112">Other data is available from send port properties.</span></span> <span data-ttu-id="3796f-113">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="3796f-113">The data stored includes:</span></span>  
  
-   <span data-ttu-id="3796f-114">記錄類型 = 交換狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-114">Record Type = Interchange Status</span></span>  
  
-   <span data-ttu-id="3796f-115">交換方向 = 更新資料 = 傳送</span><span class="sxs-lookup"><span data-stu-id="3796f-115">Interchange Direction = Update Data = Send</span></span>  
  
-   <span data-ttu-id="3796f-116">交換接收者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-116">Interchange Receiver = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-117">交換傳送者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-117">Interchange Sender = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-118">交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-118">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-119">交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-119">Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-120">交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-120">Interchange Control ID = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-121">交換狀態：已處理/傳送。</span><span class="sxs-lookup"><span data-stu-id="3796f-121">Interchange Status: Processed/Sent.</span></span> <span data-ttu-id="3796f-122">「已處理」的狀態表示傳送管線已成功處理交換，並將它傳送至傳送配接器等候傳遞。</span><span class="sxs-lookup"><span data-stu-id="3796f-122">A status of Processed indicates that the send pipeline has successfully processed the interchange and handed it over to the send adapter for delivery.</span></span>  
  
-   <span data-ttu-id="3796f-123">交換控制計數 (在 X12 中分別為群組/訊息) = 資料</span><span class="sxs-lookup"><span data-stu-id="3796f-123">Interchange Control Count (Groups/Messages in X12 respectively) = Data</span></span>  
  
-   <span data-ttu-id="3796f-124">交換傳送埠識別碼 = 資料</span><span class="sxs-lookup"><span data-stu-id="3796f-124">Interchange Send Port ID = Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a><span data-ttu-id="3796f-125">由接收管線針對回應輸出交換而接收之每個技術通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-125">Data Stored by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange</span></span>  
 <span data-ttu-id="3796f-126">接收管線會在狀態報告資料存放區中，針對其所接收的每個技術通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="3796f-126">The receive pipeline creates a record in the status report data store for each technical acknowledgment that it receives.</span></span> <span data-ttu-id="3796f-127">接收管線就會建立每個交換狀態報告資料存放區中收到的記錄。</span><span class="sxs-lookup"><span data-stu-id="3796f-127">The receive pipeline creates a record of each interchange received in the status report data store.</span></span> <span data-ttu-id="3796f-128">每個技術通知以回應傳送給交易夥伴交換接收的資料存放區中建立一個技術通知狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="3796f-128">creates one technical acknowledgment status report entry in the data store for each technical ACK received as a response to an interchange sent to a trading partner.</span></span> <span data-ttu-id="3796f-129">X12 類型的技術通知是 TA1，EDIFACT 類型的技術通知為僅包含 UCI 區段的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="3796f-129">The technical acknowledge is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT.</span></span> <span data-ttu-id="3796f-130">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="3796f-130">The data stored includes:</span></span>  
  
-   <span data-ttu-id="3796f-131">記錄類型 = 交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-131">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="3796f-132">交換通知方向 = 傳送 – 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-132">Interchange ACK Direction = Send – Update Data</span></span>  
  
-   <span data-ttu-id="3796f-133">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-133">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-134">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-134">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-135">交換日期 = 更新資料 (X12 相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-135">Interchange Date = Update Data (required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="3796f-136">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-136">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-137">交換通知狀態 = 已產生或不適用\<參閱說明 0\> -更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-137">Interchange ACK Status = Generated or Not Applicable \<Refer Note 0\> - Update Data</span></span>  
  
-   <span data-ttu-id="3796f-138">交換通知控制識別碼= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-138">Interchange ACK Control ID= Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-139">交換通知日期= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-139">Interchange ACK Date = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-140">交換通知時間= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-140">Interchange ACK Time = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-141">通知/動作代碼 = 更新資料\<附註 1，請參閱\>（從 X12 TA104 或 edifact-uci4） *</span><span class="sxs-lookup"><span data-stu-id="3796f-141">ACK/Action Code = Update Data  \<refer note 1\> (from X12-TA104 or EDIFACT-UCI4)*</span></span>  
  
-   <span data-ttu-id="3796f-142">通知說明碼 = 更新資料\<，請參閱註 2\> （從 X12-TA105，EDIFACT 不適用) *</span><span class="sxs-lookup"><span data-stu-id="3796f-142">ACK Note Code = Update Data \<Refer Note 2\> (from X12-TA105, not applicable for EDIFACT)*</span></span>  
  
 <span data-ttu-id="3796f-143">使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-143">The following ACK/Action Codes are used:</span></span>  
  
|<span data-ttu-id="3796f-144">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-144">Data in ACK/Action Code</span></span>|<span data-ttu-id="3796f-145">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-145">Error description for Reporting</span></span>|<span data-ttu-id="3796f-146">註解 (適用性)</span><span class="sxs-lookup"><span data-stu-id="3796f-146">Comment (applicability)</span></span>|  
|------------------------------|-------------------------------------|-------------------------------|  
|<span data-ttu-id="3796f-147">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="3796f-147">A</span></span>|<span data-ttu-id="3796f-148">已接受</span><span class="sxs-lookup"><span data-stu-id="3796f-148">Accepted</span></span>|<span data-ttu-id="3796f-149">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-149">X12</span></span>|  
|<span data-ttu-id="3796f-150">E</span><span class="sxs-lookup"><span data-stu-id="3796f-150">E</span></span>|<span data-ttu-id="3796f-151">已接受，但已記錄錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-151">Accepted, errors noted</span></span>|<span data-ttu-id="3796f-152">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-152">X12</span></span>|  
|<span data-ttu-id="3796f-153">P</span><span class="sxs-lookup"><span data-stu-id="3796f-153">P</span></span>|<span data-ttu-id="3796f-154">已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-154">Partially Accepted</span></span>|<span data-ttu-id="3796f-155">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-155">X12</span></span>|  
|<span data-ttu-id="3796f-156">R</span><span class="sxs-lookup"><span data-stu-id="3796f-156">R</span></span>|<span data-ttu-id="3796f-157">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-157">Rejected</span></span>|<span data-ttu-id="3796f-158">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-158">X12</span></span>|  
|<span data-ttu-id="3796f-159">4</span><span class="sxs-lookup"><span data-stu-id="3796f-159">4</span></span>|<span data-ttu-id="3796f-160">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-160">Rejected</span></span>|<span data-ttu-id="3796f-161">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-161">EDIFACT</span></span>|  
|<span data-ttu-id="3796f-162">8</span><span class="sxs-lookup"><span data-stu-id="3796f-162">8</span></span>|<span data-ttu-id="3796f-163">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-163">Accepted/Partially Accepted</span></span>|<span data-ttu-id="3796f-164">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-164">EDIFACT</span></span>|  
  
 <span data-ttu-id="3796f-165">使用的通知說明碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-165">The following ACK Note Codes are used:</span></span>  
  
|<span data-ttu-id="3796f-166">通知說明碼中的資料 (在 X12 中)</span><span class="sxs-lookup"><span data-stu-id="3796f-166">Data in ACK Note Code (in X12)</span></span>|<span data-ttu-id="3796f-167">Description</span><span class="sxs-lookup"><span data-stu-id="3796f-167">Description</span></span>|  
|--------------------------------------|-----------------|  
|<span data-ttu-id="3796f-168">000</span><span class="sxs-lookup"><span data-stu-id="3796f-168">000</span></span>|<span data-ttu-id="3796f-169">成功</span><span class="sxs-lookup"><span data-stu-id="3796f-169">Success</span></span>|  
|<span data-ttu-id="3796f-170">001</span><span class="sxs-lookup"><span data-stu-id="3796f-170">001</span></span>|<span data-ttu-id="3796f-171">交換控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-171">Interchange Control Number mismatch</span></span>|  
|<span data-ttu-id="3796f-172">002</span><span class="sxs-lookup"><span data-stu-id="3796f-172">002</span></span>|<span data-ttu-id="3796f-173">不支援標準</span><span class="sxs-lookup"><span data-stu-id="3796f-173">Standard not supported</span></span>|  
|<span data-ttu-id="3796f-174">003</span><span class="sxs-lookup"><span data-stu-id="3796f-174">003</span></span>|<span data-ttu-id="3796f-175">不支援控制項版本</span><span class="sxs-lookup"><span data-stu-id="3796f-175">Version of the Controls Not Supported</span></span>|  
|<span data-ttu-id="3796f-176">004</span><span class="sxs-lookup"><span data-stu-id="3796f-176">004</span></span>|<span data-ttu-id="3796f-177">區段結束字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-177">Segment Terminator is Invalid</span></span>|  
|<span data-ttu-id="3796f-178">005</span><span class="sxs-lookup"><span data-stu-id="3796f-178">005</span></span>|<span data-ttu-id="3796f-179">無效的傳送者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="3796f-179">Invalid Interchange ID Qualifier for Sender</span></span>|  
|<span data-ttu-id="3796f-180">006</span><span class="sxs-lookup"><span data-stu-id="3796f-180">006</span></span>|<span data-ttu-id="3796f-181">無效的交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-181">Invalid Interchange Sender ID</span></span>|  
|<span data-ttu-id="3796f-182">007</span><span class="sxs-lookup"><span data-stu-id="3796f-182">007</span></span>|<span data-ttu-id="3796f-183">無效的接收者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="3796f-183">Invalid Interchange ID Qualifier for Receiver</span></span>|  
|<span data-ttu-id="3796f-184">008</span><span class="sxs-lookup"><span data-stu-id="3796f-184">008</span></span>|<span data-ttu-id="3796f-185">無效的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-185">Invalid Interchange Receiver ID</span></span>|  
|<span data-ttu-id="3796f-186">009</span><span class="sxs-lookup"><span data-stu-id="3796f-186">009</span></span>|<span data-ttu-id="3796f-187">未知的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-187">Unknown Interchange Receiver ID</span></span>|  
|<span data-ttu-id="3796f-188">010</span><span class="sxs-lookup"><span data-stu-id="3796f-188">010</span></span>|<span data-ttu-id="3796f-189">無效的授權資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-189">Invalid Authorization Information Qualifier Value</span></span>|  
|<span data-ttu-id="3796f-190">011</span><span class="sxs-lookup"><span data-stu-id="3796f-190">011</span></span>|<span data-ttu-id="3796f-191">無效的授權資訊值</span><span class="sxs-lookup"><span data-stu-id="3796f-191">Invalid Authorization Information Value</span></span>|  
|<span data-ttu-id="3796f-192">012</span><span class="sxs-lookup"><span data-stu-id="3796f-192">012</span></span>|<span data-ttu-id="3796f-193">無效的安全性資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-193">Invalid Security Information Qualifier Value</span></span>|  
|<span data-ttu-id="3796f-194">013</span><span class="sxs-lookup"><span data-stu-id="3796f-194">013</span></span>|<span data-ttu-id="3796f-195">無效的安全性資訊值</span><span class="sxs-lookup"><span data-stu-id="3796f-195">Invalid Security Information Value</span></span>|  
|<span data-ttu-id="3796f-196">014</span><span class="sxs-lookup"><span data-stu-id="3796f-196">014</span></span>|<span data-ttu-id="3796f-197">無效的交換日期值</span><span class="sxs-lookup"><span data-stu-id="3796f-197">Invalid Interchange Date Value</span></span>|  
|<span data-ttu-id="3796f-198">015</span><span class="sxs-lookup"><span data-stu-id="3796f-198">015</span></span>|<span data-ttu-id="3796f-199">無效的交換時間值</span><span class="sxs-lookup"><span data-stu-id="3796f-199">Invalid Interchange Time Value</span></span>|  
|<span data-ttu-id="3796f-200">016</span><span class="sxs-lookup"><span data-stu-id="3796f-200">016</span></span>|<span data-ttu-id="3796f-201">無效的交換標準識別碼值</span><span class="sxs-lookup"><span data-stu-id="3796f-201">Invalid Interchange Standards Identifier Value</span></span>|  
|<span data-ttu-id="3796f-202">017</span><span class="sxs-lookup"><span data-stu-id="3796f-202">017</span></span>|<span data-ttu-id="3796f-203">無效的交換版本識別碼值</span><span class="sxs-lookup"><span data-stu-id="3796f-203">Invalid Interchange Version ID Value</span></span>|  
|<span data-ttu-id="3796f-204">018</span><span class="sxs-lookup"><span data-stu-id="3796f-204">018</span></span>|<span data-ttu-id="3796f-205">無效的交換控制編號值</span><span class="sxs-lookup"><span data-stu-id="3796f-205">Invalid Interchange Control Number Value</span></span>|  
|<span data-ttu-id="3796f-206">019</span><span class="sxs-lookup"><span data-stu-id="3796f-206">019</span></span>|<span data-ttu-id="3796f-207">無效的通知要求值</span><span class="sxs-lookup"><span data-stu-id="3796f-207">Invalid Acknowledgment Requested Value</span></span>|  
|<span data-ttu-id="3796f-208">020</span><span class="sxs-lookup"><span data-stu-id="3796f-208">020</span></span>|<span data-ttu-id="3796f-209">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-209">Invalid Test Indicator Value</span></span>|  
|<span data-ttu-id="3796f-210">021</span><span class="sxs-lookup"><span data-stu-id="3796f-210">021</span></span>|<span data-ttu-id="3796f-211">無效之包括的群組數目值</span><span class="sxs-lookup"><span data-stu-id="3796f-211">Invalid Number of Included Groups Value</span></span>|  
|<span data-ttu-id="3796f-212">022</span><span class="sxs-lookup"><span data-stu-id="3796f-212">022</span></span>|<span data-ttu-id="3796f-213">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="3796f-213">Invalid Control Structure</span></span>|  
|<span data-ttu-id="3796f-214">023</span><span class="sxs-lookup"><span data-stu-id="3796f-214">023</span></span>|<span data-ttu-id="3796f-215">不適當的檔案結尾</span><span class="sxs-lookup"><span data-stu-id="3796f-215">Improper End-of-File</span></span>|  
|<span data-ttu-id="3796f-216">024</span><span class="sxs-lookup"><span data-stu-id="3796f-216">024</span></span>|<span data-ttu-id="3796f-217">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="3796f-217">Invalid Interchange Content</span></span>|  
|<span data-ttu-id="3796f-218">025</span><span class="sxs-lookup"><span data-stu-id="3796f-218">025</span></span>|<span data-ttu-id="3796f-219">重複的交換控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-219">Duplicate Interchange Control Number</span></span>|  
|<span data-ttu-id="3796f-220">026</span><span class="sxs-lookup"><span data-stu-id="3796f-220">026</span></span>|<span data-ttu-id="3796f-221">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-221">Invalid Data Element Separator</span></span>|  
|<span data-ttu-id="3796f-222">027</span><span class="sxs-lookup"><span data-stu-id="3796f-222">027</span></span>|<span data-ttu-id="3796f-223">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-223">Invalid Component Element Separator</span></span>|  
|<span data-ttu-id="3796f-224">028</span><span class="sxs-lookup"><span data-stu-id="3796f-224">028</span></span>|<span data-ttu-id="3796f-225">延遲傳遞要求中無效的傳遞日期</span><span class="sxs-lookup"><span data-stu-id="3796f-225">Invalid Delivery Date in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="3796f-226">029</span><span class="sxs-lookup"><span data-stu-id="3796f-226">029</span></span>|<span data-ttu-id="3796f-227">延遲傳遞要求中無效的傳遞時間</span><span class="sxs-lookup"><span data-stu-id="3796f-227">Invalid Delivery Time in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="3796f-228">030</span><span class="sxs-lookup"><span data-stu-id="3796f-228">030</span></span>|<span data-ttu-id="3796f-229">延遲的傳遞要求中無效的傳遞時間碼</span><span class="sxs-lookup"><span data-stu-id="3796f-229">Invalid Delivery Time Code in Deferred Delivery  Request</span></span>|  
|<span data-ttu-id="3796f-230">031</span><span class="sxs-lookup"><span data-stu-id="3796f-230">031</span></span>|<span data-ttu-id="3796f-231">無效的服務等級</span><span class="sxs-lookup"><span data-stu-id="3796f-231">Invalid Grade of Service</span></span>|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a><span data-ttu-id="3796f-232">由接收管線針對回應輸出交換而接收之每個技術通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-232">Data Updated by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange</span></span>  
 <span data-ttu-id="3796f-233">對於接收管線所接收的每個技術通知，接收管線都會更新相互關聯之傳送交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="3796f-233">For each technical acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.</span></span>  
  
 <span data-ttu-id="3796f-234">EDI 解譯器會使用內送通知中 UCI 和 TA1 區段內的資料，找出資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3796f-234">The EDI Disassembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="3796f-235">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="3796f-235">Fields in ACK</span></span>|<span data-ttu-id="3796f-236">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="3796f-236">Fields in Data store</span></span>|<span data-ttu-id="3796f-237">註解</span><span class="sxs-lookup"><span data-stu-id="3796f-237">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="3796f-238">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-238">Interchange Sender ID</span></span>|<span data-ttu-id="3796f-239">交換接收方</span><span class="sxs-lookup"><span data-stu-id="3796f-239">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="3796f-240">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-240">Interchange Receiver ID</span></span>|<span data-ttu-id="3796f-241">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="3796f-241">Interchange Sender</span></span>|-|  
|-|<span data-ttu-id="3796f-242">交換日期</span><span class="sxs-lookup"><span data-stu-id="3796f-242">Interchange Date</span></span>|-|  
|<span data-ttu-id="3796f-243">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-243">Interchange Control Number</span></span>|<span data-ttu-id="3796f-244">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-244">Interchange Control ID</span></span>|-|  
|-|<span data-ttu-id="3796f-245">交換方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="3796f-245">Interchange Direction = Send</span></span>|<span data-ttu-id="3796f-246">在為唯一性而保留的批次實例中是必要的</span><span class="sxs-lookup"><span data-stu-id="3796f-246">Required in preserved batch scenario for uniqueness</span></span>|  
|<span data-ttu-id="3796f-247">記錄類型</span><span class="sxs-lookup"><span data-stu-id="3796f-247">Record Type</span></span>|<span data-ttu-id="3796f-248">交換狀態和交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-248">Interchange Status and Interchange ACK Status</span></span>|-|  
  
 <span data-ttu-id="3796f-249">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="3796f-249">The data stored includes:</span></span>  
  
-   <span data-ttu-id="3796f-250">交換通知方向 = 接收 – 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-250">Interchange ACK Direction = Receive – Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-251">交換通知狀態 = 已收到</span><span class="sxs-lookup"><span data-stu-id="3796f-251">Interchange ACK Status = Received</span></span>  
  
-   <span data-ttu-id="3796f-252">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-252">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-253">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-253">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-254">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="3796f-254">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-255">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-255">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-256">交換通知控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-256">Interchange ACK Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="3796f-257">交換通知日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-257">Interchange ACK Date = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-258">交換通知時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-258">Interchange ACK Time = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-259">通知/動作代碼 = 更新資料 （從 X12 TA104 或 edifact-uci4） *\<附註 1，請參閱\></span><span class="sxs-lookup"><span data-stu-id="3796f-259">ACK/Action Code = Update Data (from X12-TA104 or EDIFACT-UCI4)* \<Refer Note 1\></span></span>  
  
-   <span data-ttu-id="3796f-260">通知說明碼 2 = 更新資料 (從 X12 TA105 和不 edifact 的值) * \<，請參閱註 2\></span><span class="sxs-lookup"><span data-stu-id="3796f-260">ACK Note Code 2 = Update Data (from X12-TA105 and not valued for EDIFACT)* \<Refer Note 2\></span></span>  
  
 <span data-ttu-id="3796f-261">來自 ACK X12:TA1-104 或 EDIFACT UCI4 的資料將會加以對應，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3796f-261">The data from the ACK X12:TA1-104 or EDIFACT UCI4 is to be mapped as follows:</span></span>  
  
|<span data-ttu-id="3796f-262">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-262">Data in ACK/Action Code</span></span>|<span data-ttu-id="3796f-263">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="3796f-263">Mapped for Status Reporting</span></span>|<span data-ttu-id="3796f-264">註解</span><span class="sxs-lookup"><span data-stu-id="3796f-264">Comment</span></span>|  
|------------------------------|---------------------------------|-------------|  
|<span data-ttu-id="3796f-265">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="3796f-265">A</span></span>|<span data-ttu-id="3796f-266">已接受</span><span class="sxs-lookup"><span data-stu-id="3796f-266">Accepted</span></span>|<span data-ttu-id="3796f-267">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-267">X12</span></span>|  
|<span data-ttu-id="3796f-268">P</span><span class="sxs-lookup"><span data-stu-id="3796f-268">P</span></span>|<span data-ttu-id="3796f-269">已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-269">Partially Accepted</span></span>|<span data-ttu-id="3796f-270">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-270">X12</span></span>|  
|<span data-ttu-id="3796f-271">R、M、W、X</span><span class="sxs-lookup"><span data-stu-id="3796f-271">R, M, W, X</span></span>|<span data-ttu-id="3796f-272">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-272">Rejected</span></span>|<span data-ttu-id="3796f-273">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-273">X12</span></span>|  
|<span data-ttu-id="3796f-274">E</span><span class="sxs-lookup"><span data-stu-id="3796f-274">E</span></span>|<span data-ttu-id="3796f-275">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-275">Accepted with errors</span></span>|<span data-ttu-id="3796f-276">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-276">X12</span></span>|  
|<span data-ttu-id="3796f-277">4</span><span class="sxs-lookup"><span data-stu-id="3796f-277">4</span></span>|<span data-ttu-id="3796f-278">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-278">Rejected</span></span>|<span data-ttu-id="3796f-279">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-279">EDIFACT</span></span>|  
|<span data-ttu-id="3796f-280">7, 8</span><span class="sxs-lookup"><span data-stu-id="3796f-280">7, 8</span></span>|<span data-ttu-id="3796f-281">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-281">Accepted/Partially Accepted</span></span>|<span data-ttu-id="3796f-282">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-282">EDIFACT</span></span>|  
  
 <span data-ttu-id="3796f-283">使用的通知說明碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-283">The following ACK Note Codes are used:</span></span>  
  
|<span data-ttu-id="3796f-284">通知說明碼中的資料 (在 X12 中)</span><span class="sxs-lookup"><span data-stu-id="3796f-284">Data in ACK Note Code (in X12)</span></span>|<span data-ttu-id="3796f-285">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="3796f-285">Mapped for Status Reporting</span></span>|  
|--------------------------------------|---------------------------------|  
|<span data-ttu-id="3796f-286">000</span><span class="sxs-lookup"><span data-stu-id="3796f-286">000</span></span>|<span data-ttu-id="3796f-287">成功</span><span class="sxs-lookup"><span data-stu-id="3796f-287">Success</span></span>|  
|<span data-ttu-id="3796f-288">001</span><span class="sxs-lookup"><span data-stu-id="3796f-288">001</span></span>|<span data-ttu-id="3796f-289">交換控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-289">Interchange Control Number mismatch</span></span>|  
|<span data-ttu-id="3796f-290">002</span><span class="sxs-lookup"><span data-stu-id="3796f-290">002</span></span>|<span data-ttu-id="3796f-291">不支援標準</span><span class="sxs-lookup"><span data-stu-id="3796f-291">Standard not supported</span></span>|  
|<span data-ttu-id="3796f-292">003</span><span class="sxs-lookup"><span data-stu-id="3796f-292">003</span></span>|<span data-ttu-id="3796f-293">不支援控制項版本</span><span class="sxs-lookup"><span data-stu-id="3796f-293">Version of the Controls Not Supported</span></span>|  
|<span data-ttu-id="3796f-294">004</span><span class="sxs-lookup"><span data-stu-id="3796f-294">004</span></span>|<span data-ttu-id="3796f-295">區段結束字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-295">Segment Terminator is Invalid</span></span>|  
|<span data-ttu-id="3796f-296">005</span><span class="sxs-lookup"><span data-stu-id="3796f-296">005</span></span>|<span data-ttu-id="3796f-297">無效的傳送者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="3796f-297">Invalid Interchange ID Qualifier for Sender</span></span>|  
|<span data-ttu-id="3796f-298">006</span><span class="sxs-lookup"><span data-stu-id="3796f-298">006</span></span>|<span data-ttu-id="3796f-299">無效的交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-299">Invalid Interchange Sender ID</span></span>|  
|<span data-ttu-id="3796f-300">007</span><span class="sxs-lookup"><span data-stu-id="3796f-300">007</span></span>|<span data-ttu-id="3796f-301">無效的接收者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="3796f-301">Invalid Interchange ID Qualifier for Receiver</span></span>|  
|<span data-ttu-id="3796f-302">008</span><span class="sxs-lookup"><span data-stu-id="3796f-302">008</span></span>|<span data-ttu-id="3796f-303">無效的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-303">Invalid Interchange Receiver ID</span></span>|  
|<span data-ttu-id="3796f-304">009</span><span class="sxs-lookup"><span data-stu-id="3796f-304">009</span></span>|<span data-ttu-id="3796f-305">未知的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-305">Unknown Interchange Receiver ID</span></span>|  
|<span data-ttu-id="3796f-306">010</span><span class="sxs-lookup"><span data-stu-id="3796f-306">010</span></span>|<span data-ttu-id="3796f-307">無效的授權資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-307">Invalid Authorization Information Qualifier Value</span></span>|  
|<span data-ttu-id="3796f-308">011</span><span class="sxs-lookup"><span data-stu-id="3796f-308">011</span></span>|<span data-ttu-id="3796f-309">無效的授權資訊值</span><span class="sxs-lookup"><span data-stu-id="3796f-309">Invalid Authorization Information Value</span></span>|  
|<span data-ttu-id="3796f-310">012</span><span class="sxs-lookup"><span data-stu-id="3796f-310">012</span></span>|<span data-ttu-id="3796f-311">無效的安全性資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-311">Invalid Security Information Qualifier Value</span></span>|  
|<span data-ttu-id="3796f-312">013</span><span class="sxs-lookup"><span data-stu-id="3796f-312">013</span></span>|<span data-ttu-id="3796f-313">無效的安全性資訊值</span><span class="sxs-lookup"><span data-stu-id="3796f-313">Invalid Security Information Value</span></span>|  
|<span data-ttu-id="3796f-314">014</span><span class="sxs-lookup"><span data-stu-id="3796f-314">014</span></span>|<span data-ttu-id="3796f-315">無效的交換日期值</span><span class="sxs-lookup"><span data-stu-id="3796f-315">Invalid Interchange Date Value</span></span>|  
|<span data-ttu-id="3796f-316">015</span><span class="sxs-lookup"><span data-stu-id="3796f-316">015</span></span>|<span data-ttu-id="3796f-317">無效的交換時間值</span><span class="sxs-lookup"><span data-stu-id="3796f-317">Invalid Interchange Time Value</span></span>|  
|<span data-ttu-id="3796f-318">016</span><span class="sxs-lookup"><span data-stu-id="3796f-318">016</span></span>|<span data-ttu-id="3796f-319">無效的交換標準識別碼值</span><span class="sxs-lookup"><span data-stu-id="3796f-319">Invalid Interchange Standards Identifier Value</span></span>|  
|<span data-ttu-id="3796f-320">017</span><span class="sxs-lookup"><span data-stu-id="3796f-320">017</span></span>|<span data-ttu-id="3796f-321">無效的交換版本識別碼值</span><span class="sxs-lookup"><span data-stu-id="3796f-321">Invalid Interchange Version ID Value</span></span>|  
|<span data-ttu-id="3796f-322">018</span><span class="sxs-lookup"><span data-stu-id="3796f-322">018</span></span>|<span data-ttu-id="3796f-323">無效的交換控制編號值</span><span class="sxs-lookup"><span data-stu-id="3796f-323">Invalid Interchange Control Number Value</span></span>|  
|<span data-ttu-id="3796f-324">019</span><span class="sxs-lookup"><span data-stu-id="3796f-324">019</span></span>|<span data-ttu-id="3796f-325">無效的通知要求值</span><span class="sxs-lookup"><span data-stu-id="3796f-325">Invalid Acknowledgment Requested Value</span></span>|  
|<span data-ttu-id="3796f-326">020</span><span class="sxs-lookup"><span data-stu-id="3796f-326">020</span></span>|<span data-ttu-id="3796f-327">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="3796f-327">Invalid Test Indicator Value</span></span>|  
|<span data-ttu-id="3796f-328">021</span><span class="sxs-lookup"><span data-stu-id="3796f-328">021</span></span>|<span data-ttu-id="3796f-329">無效之包括的群組數目值</span><span class="sxs-lookup"><span data-stu-id="3796f-329">Invalid Number of Included Groups Value</span></span>|  
|<span data-ttu-id="3796f-330">022</span><span class="sxs-lookup"><span data-stu-id="3796f-330">022</span></span>|<span data-ttu-id="3796f-331">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="3796f-331">Invalid Control Structure</span></span>|  
|<span data-ttu-id="3796f-332">023</span><span class="sxs-lookup"><span data-stu-id="3796f-332">023</span></span>|<span data-ttu-id="3796f-333">不適當的檔案結尾</span><span class="sxs-lookup"><span data-stu-id="3796f-333">Improper End-of-File</span></span>|  
|<span data-ttu-id="3796f-334">024</span><span class="sxs-lookup"><span data-stu-id="3796f-334">024</span></span>|<span data-ttu-id="3796f-335">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="3796f-335">Invalid Interchange Content</span></span>|  
|<span data-ttu-id="3796f-336">025</span><span class="sxs-lookup"><span data-stu-id="3796f-336">025</span></span>|<span data-ttu-id="3796f-337">重複的交換控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-337">Duplicate Interchange Control Number</span></span>|  
|<span data-ttu-id="3796f-338">026</span><span class="sxs-lookup"><span data-stu-id="3796f-338">026</span></span>|<span data-ttu-id="3796f-339">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-339">Invalid Data Element Separator</span></span>|  
|<span data-ttu-id="3796f-340">027</span><span class="sxs-lookup"><span data-stu-id="3796f-340">027</span></span>|<span data-ttu-id="3796f-341">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-341">Invalid Component Element Separator</span></span>|  
|<span data-ttu-id="3796f-342">028</span><span class="sxs-lookup"><span data-stu-id="3796f-342">028</span></span>|<span data-ttu-id="3796f-343">延遲傳遞要求中無效的傳遞日期</span><span class="sxs-lookup"><span data-stu-id="3796f-343">Invalid Delivery Date in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="3796f-344">029</span><span class="sxs-lookup"><span data-stu-id="3796f-344">029</span></span>|<span data-ttu-id="3796f-345">延遲傳遞要求中無效的傳遞時間</span><span class="sxs-lookup"><span data-stu-id="3796f-345">Invalid Delivery Time in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="3796f-346">030</span><span class="sxs-lookup"><span data-stu-id="3796f-346">030</span></span>|<span data-ttu-id="3796f-347">延遲的傳遞要求中無效的傳遞時間碼</span><span class="sxs-lookup"><span data-stu-id="3796f-347">Invalid Delivery Time Code in Deferred Delivery  Request</span></span>|  
|<span data-ttu-id="3796f-348">031</span><span class="sxs-lookup"><span data-stu-id="3796f-348">031</span></span>|<span data-ttu-id="3796f-349">無效的服務等級</span><span class="sxs-lookup"><span data-stu-id="3796f-349">Invalid Grade of Service</span></span>|  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outbound-interchanges"></a><span data-ttu-id="3796f-350">由接收管線針對回應輸出交換而接收之每個功能通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-350">Data Stored by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outbound Interchanges</span></span>  
 <span data-ttu-id="3796f-351">接收管線會在狀態報告資料存放區中，針對其所接收的每個功能通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="3796f-351">The receive pipeline creates a record in the status report data store for each functional acknowledgment that it receives.</span></span>  <span data-ttu-id="3796f-352">X12 類型的技術通知是 997，EDIFACT 類型的技術通知為完整的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="3796f-352">The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT.</span></span> <span data-ttu-id="3796f-353">會為每個群組建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="3796f-353">One entry per group will to be created.</span></span> <span data-ttu-id="3796f-354">進行這項輸入時會使用交換和群組標頭內的資料。</span><span class="sxs-lookup"><span data-stu-id="3796f-354">Data from the interchange and group headers is used while making this entry.</span></span> <span data-ttu-id="3796f-355">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="3796f-355">The data stored includes:</span></span>  
  
-   <span data-ttu-id="3796f-356">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-356">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="3796f-357">功能通知方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="3796f-357">Functional ACK Direction = Send</span></span>  
  
-   <span data-ttu-id="3796f-358">功能通知狀態 =\<產生或不適用，請參閱附註 1\></span><span class="sxs-lookup"><span data-stu-id="3796f-358">Functional ACK Status = \<Generated or Not Applicable, refer note 1\></span></span>  
  
-   <span data-ttu-id="3796f-359">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-359">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-360">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-360">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-361">交換日期 = 更新資料 (X12 相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-361">Interchange Date = Update Data (required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="3796f-362">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-362">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="3796f-363">群組控制編號 = 更新資料 (「對於 EDIFACT 是選擇項」，對於 X12 相互關聯是必要項)</span><span class="sxs-lookup"><span data-stu-id="3796f-363">Group Control Number = Update Data (‘optional for EDIFACT’ and required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="3796f-364">功能識別代碼 = 更新資料 (GS01/UNG01)</span><span class="sxs-lookup"><span data-stu-id="3796f-364">Functional ID Code = Update Data (GS01/UNG01)</span></span>  
  
-   <span data-ttu-id="3796f-365">交易集的計數 = 更新資料 (UNE1/UNZ1)</span><span class="sxs-lookup"><span data-stu-id="3796f-365">Count of Transaction Sets = Update Data (UNE1/UNZ1)</span></span>  
  
-   <span data-ttu-id="3796f-366">功能通知交換控制識別碼= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-366">Functional ACK Interchange Control ID= Not value – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-367">功能通知交換日期= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-367">Functional ACK Interchange Date = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-368">功能通知交換時間= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="3796f-368">Functional ACK Interchange Time = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="3796f-369">已接收交易集的計數 = 更新資料 (X12-AK903，由 EDIFACT 編碼的引擎計算)</span><span class="sxs-lookup"><span data-stu-id="3796f-369">Count of Transaction Sets Received = Update Data (X12-AK903 and computed by Engine for EDIFACT encoding)</span></span>  
  
-   <span data-ttu-id="3796f-370">已接受交易集的計數 = 更新資料 (X12-AK904，由 EDIFACT 編碼的引擎計算)</span><span class="sxs-lookup"><span data-stu-id="3796f-370">Count of Transaction Sets Accepted = Update Data (X12-AK904 and computed by Engine for EDIFACT engine)</span></span>  
  
-   <span data-ttu-id="3796f-371">通知/動作代碼 = 更新資料\<附註 2，請參閱\>（從 X12 AK901 或 edifact-uci4） *</span><span class="sxs-lookup"><span data-stu-id="3796f-371">ACK/Action Code = Update Data  \<refer note 2\> (from X12-AK901 or EDIFACT-UCI4)*</span></span>  
  
-   <span data-ttu-id="3796f-372">錯誤/語法錯誤碼 = 更新資料 (X12-AK905、EDIFACT UCI5) 說明 3</span><span class="sxs-lookup"><span data-stu-id="3796f-372">Error/Syntax Error Code  = Update Data (X12-AK905, EDIFACT UCI5) Note 3</span></span>  
  
-   <span data-ttu-id="3796f-373">其他 X12 通知錯誤碼 2 = 更新資料 (X12-AK906)</span><span class="sxs-lookup"><span data-stu-id="3796f-373">Additional X12 ACK Error Code 2 = Update Data (X12-AK906)</span></span>  
  
-   <span data-ttu-id="3796f-374">其他 X12 通知錯誤碼 3 = 更新資料 (X12-AK907)</span><span class="sxs-lookup"><span data-stu-id="3796f-374">Additional X12 ACK Error Code 3 = Update Data (X12-AK907)</span></span>  
  
-   <span data-ttu-id="3796f-375">其他 X12 通知錯誤碼 4 = 更新資料 (X12-AK908)</span><span class="sxs-lookup"><span data-stu-id="3796f-375">Additional X12 ACK Error Code 4 = Update Data (X12-AK908)</span></span>  
  
-   <span data-ttu-id="3796f-376">其他 X12 通知錯誤碼 5 = 更新資料 (X12-AK909)</span><span class="sxs-lookup"><span data-stu-id="3796f-376">Additional X12 ACK Error Code 5 = Update Data (X12-AK909)</span></span>  
  
 <span data-ttu-id="3796f-377">將使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-377">The following ACK/Action Codes will be used:</span></span>  
  
|<span data-ttu-id="3796f-378">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-378">Data in ACK/Action Code</span></span>|<span data-ttu-id="3796f-379">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-379">Error description for Reporting</span></span>|<span data-ttu-id="3796f-380">註解 (適用性)</span><span class="sxs-lookup"><span data-stu-id="3796f-380">Comment (applicability)</span></span>|  
|------------------------------|-------------------------------------|-------------------------------|  
|<span data-ttu-id="3796f-381">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="3796f-381">A</span></span>|<span data-ttu-id="3796f-382">已接受</span><span class="sxs-lookup"><span data-stu-id="3796f-382">Accepted</span></span>|<span data-ttu-id="3796f-383">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-383">X12</span></span>|  
|<span data-ttu-id="3796f-384">E</span><span class="sxs-lookup"><span data-stu-id="3796f-384">E</span></span>|<span data-ttu-id="3796f-385">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-385">Accepted  with errors</span></span>|<span data-ttu-id="3796f-386">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-386">X12</span></span>|  
|<span data-ttu-id="3796f-387">P</span><span class="sxs-lookup"><span data-stu-id="3796f-387">P</span></span>|<span data-ttu-id="3796f-388">已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-388">Partially Accepted</span></span>|<span data-ttu-id="3796f-389">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-389">X12</span></span>|  
|<span data-ttu-id="3796f-390">R</span><span class="sxs-lookup"><span data-stu-id="3796f-390">R</span></span>|<span data-ttu-id="3796f-391">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-391">Rejected</span></span>|<span data-ttu-id="3796f-392">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-392">X12</span></span>|  
|<span data-ttu-id="3796f-393">4</span><span class="sxs-lookup"><span data-stu-id="3796f-393">4</span></span>|<span data-ttu-id="3796f-394">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-394">Rejected</span></span>|<span data-ttu-id="3796f-395">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-395">EDIFACT</span></span>|  
|<span data-ttu-id="3796f-396">7</span><span class="sxs-lookup"><span data-stu-id="3796f-396">7</span></span>|<span data-ttu-id="3796f-397">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-397">Accepted/Partially Accepted</span></span>|<span data-ttu-id="3796f-398">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-398">EDIFACT</span></span>|  
  
 <span data-ttu-id="3796f-399">EDIFACT 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-399">The following Error/Syntax Error Codes will be used for EDIFACT:</span></span>  
  
|<span data-ttu-id="3796f-400">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-400">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="3796f-401">(適用於 EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="3796f-401">(applicable to EDIFACT)</span></span>|<span data-ttu-id="3796f-402">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-402">Error Description for reporting</span></span>|  
|--------------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="3796f-403">2</span><span class="sxs-lookup"><span data-stu-id="3796f-403">2</span></span>|<span data-ttu-id="3796f-404">語法版本或層級不支援</span><span class="sxs-lookup"><span data-stu-id="3796f-404">Syntax version or level not supported</span></span>|  
|<span data-ttu-id="3796f-405">7</span><span class="sxs-lookup"><span data-stu-id="3796f-405">7</span></span>|<span data-ttu-id="3796f-406">交換收件者不是實際收件者</span><span class="sxs-lookup"><span data-stu-id="3796f-406">Interchange recipient not actual recipient</span></span>|  
|<span data-ttu-id="3796f-407">12</span><span class="sxs-lookup"><span data-stu-id="3796f-407">12</span></span>|<span data-ttu-id="3796f-408">無效值</span><span class="sxs-lookup"><span data-stu-id="3796f-408">Invalid value</span></span>|  
|<span data-ttu-id="3796f-409">13</span><span class="sxs-lookup"><span data-stu-id="3796f-409">13</span></span>|<span data-ttu-id="3796f-410">Missing</span><span class="sxs-lookup"><span data-stu-id="3796f-410">Missing</span></span>|  
|<span data-ttu-id="3796f-411">14</span><span class="sxs-lookup"><span data-stu-id="3796f-411">14</span></span>|<span data-ttu-id="3796f-412">在這個位置中不支援的值</span><span class="sxs-lookup"><span data-stu-id="3796f-412">Value not supported in this position</span></span>|  
|<span data-ttu-id="3796f-413">15</span><span class="sxs-lookup"><span data-stu-id="3796f-413">15</span></span>|<span data-ttu-id="3796f-414">在這個位置中不支援</span><span class="sxs-lookup"><span data-stu-id="3796f-414">Not supported in this position</span></span>|  
|<span data-ttu-id="3796f-415">16</span><span class="sxs-lookup"><span data-stu-id="3796f-415">16</span></span>|<span data-ttu-id="3796f-416">太多結構成分</span><span class="sxs-lookup"><span data-stu-id="3796f-416">Too many constituents</span></span>|  
|<span data-ttu-id="3796f-417">17</span><span class="sxs-lookup"><span data-stu-id="3796f-417">17</span></span>|<span data-ttu-id="3796f-418">沒有協議</span><span class="sxs-lookup"><span data-stu-id="3796f-418">No agreement</span></span>|  
|<span data-ttu-id="3796f-419">18</span><span class="sxs-lookup"><span data-stu-id="3796f-419">18</span></span>|<span data-ttu-id="3796f-420">未指定的錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-420">Unspecified error</span></span>|  
|<span data-ttu-id="3796f-421">19</span><span class="sxs-lookup"><span data-stu-id="3796f-421">19</span></span>|<span data-ttu-id="3796f-422">無效的小數點標記</span><span class="sxs-lookup"><span data-stu-id="3796f-422">Invalid decimal notation</span></span>|  
|<span data-ttu-id="3796f-423">20</span><span class="sxs-lookup"><span data-stu-id="3796f-423">20</span></span>|<span data-ttu-id="3796f-424">字元做為服務字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-424">Character invalid as service character</span></span>|  
|<span data-ttu-id="3796f-425">21</span><span class="sxs-lookup"><span data-stu-id="3796f-425">21</span></span>|<span data-ttu-id="3796f-426">無效字元</span><span class="sxs-lookup"><span data-stu-id="3796f-426">Invalid character(s)</span></span>|  
|<span data-ttu-id="3796f-427">22</span><span class="sxs-lookup"><span data-stu-id="3796f-427">22</span></span>|<span data-ttu-id="3796f-428">服務字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-428">Invalid service character(s)</span></span>|  
|<span data-ttu-id="3796f-429">23</span><span class="sxs-lookup"><span data-stu-id="3796f-429">23</span></span>|<span data-ttu-id="3796f-430">未知的交換傳送者</span><span class="sxs-lookup"><span data-stu-id="3796f-430">Unknown Interchange sender</span></span>|  
|<span data-ttu-id="3796f-431">24</span><span class="sxs-lookup"><span data-stu-id="3796f-431">24</span></span>|<span data-ttu-id="3796f-432">太舊</span><span class="sxs-lookup"><span data-stu-id="3796f-432">Too old</span></span>|  
|<span data-ttu-id="3796f-433">25</span><span class="sxs-lookup"><span data-stu-id="3796f-433">25</span></span>|<span data-ttu-id="3796f-434">不支援測試指示符號</span><span class="sxs-lookup"><span data-stu-id="3796f-434">Test indicator not supported</span></span>|  
|<span data-ttu-id="3796f-435">26</span><span class="sxs-lookup"><span data-stu-id="3796f-435">26</span></span>|<span data-ttu-id="3796f-436">偵測到重複</span><span class="sxs-lookup"><span data-stu-id="3796f-436">Duplicate detected</span></span>|  
|<span data-ttu-id="3796f-437">27</span><span class="sxs-lookup"><span data-stu-id="3796f-437">27</span></span>|<span data-ttu-id="3796f-438">不支援安全性函式</span><span class="sxs-lookup"><span data-stu-id="3796f-438">Security function not supported</span></span>|  
|<span data-ttu-id="3796f-439">28</span><span class="sxs-lookup"><span data-stu-id="3796f-439">28</span></span>|<span data-ttu-id="3796f-440">參考不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-440">References do not match</span></span>|  
|<span data-ttu-id="3796f-441">29</span><span class="sxs-lookup"><span data-stu-id="3796f-441">29</span></span>|<span data-ttu-id="3796f-442">控制計數不符合接收到的執行個體數目</span><span class="sxs-lookup"><span data-stu-id="3796f-442">Control count does not match number of instances received</span></span>|  
|<span data-ttu-id="3796f-443">30</span><span class="sxs-lookup"><span data-stu-id="3796f-443">30</span></span>|<span data-ttu-id="3796f-444">群組和訊息/封裝已混合</span><span class="sxs-lookup"><span data-stu-id="3796f-444">Groups and messages/packages mixed</span></span>|  
|<span data-ttu-id="3796f-445">31</span><span class="sxs-lookup"><span data-stu-id="3796f-445">31</span></span>|<span data-ttu-id="3796f-446">群組中有一種以上的訊息類型</span><span class="sxs-lookup"><span data-stu-id="3796f-446">More than one message type in group</span></span>|  
|<span data-ttu-id="3796f-447">32</span><span class="sxs-lookup"><span data-stu-id="3796f-447">32</span></span>|<span data-ttu-id="3796f-448">較低層級空白</span><span class="sxs-lookup"><span data-stu-id="3796f-448">Lower level empty</span></span>|  
|<span data-ttu-id="3796f-449">33</span><span class="sxs-lookup"><span data-stu-id="3796f-449">33</span></span>|<span data-ttu-id="3796f-450">在訊息、封裝或群組外部出現的項目無效</span><span class="sxs-lookup"><span data-stu-id="3796f-450">Invalid occurrence outside message, package, or group</span></span>|  
|<span data-ttu-id="3796f-451">34</span><span class="sxs-lookup"><span data-stu-id="3796f-451">34</span></span>|<span data-ttu-id="3796f-452">不允許巢狀指示符號</span><span class="sxs-lookup"><span data-stu-id="3796f-452">Nesting indicator not allowed</span></span>|  
|<span data-ttu-id="3796f-453">35</span><span class="sxs-lookup"><span data-stu-id="3796f-453">35</span></span>|<span data-ttu-id="3796f-454">太多資料元素或區段重複</span><span class="sxs-lookup"><span data-stu-id="3796f-454">Too many data element or segment repetitions</span></span>|  
|<span data-ttu-id="3796f-455">36</span><span class="sxs-lookup"><span data-stu-id="3796f-455">36</span></span>|<span data-ttu-id="3796f-456">太多區段群組重複</span><span class="sxs-lookup"><span data-stu-id="3796f-456">Too many segment group repetitions</span></span>|  
|<span data-ttu-id="3796f-457">37</span><span class="sxs-lookup"><span data-stu-id="3796f-457">37</span></span>|<span data-ttu-id="3796f-458">無效字元類型</span><span class="sxs-lookup"><span data-stu-id="3796f-458">Invalid type of character(s)</span></span>|  
|<span data-ttu-id="3796f-459">38</span><span class="sxs-lookup"><span data-stu-id="3796f-459">38</span></span>|<span data-ttu-id="3796f-460">在小數符號之前遺失數字</span><span class="sxs-lookup"><span data-stu-id="3796f-460">Missing digit in front of decimal sign</span></span>|  
|<span data-ttu-id="3796f-461">39</span><span class="sxs-lookup"><span data-stu-id="3796f-461">39</span></span>|<span data-ttu-id="3796f-462">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="3796f-462">Data element too long</span></span>|  
|<span data-ttu-id="3796f-463">40</span><span class="sxs-lookup"><span data-stu-id="3796f-463">40</span></span>|<span data-ttu-id="3796f-464">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="3796f-464">Data element too short</span></span>|  
|<span data-ttu-id="3796f-465">41</span><span class="sxs-lookup"><span data-stu-id="3796f-465">41</span></span>|<span data-ttu-id="3796f-466">永久通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-466">Permanent communication network error</span></span>|  
|<span data-ttu-id="3796f-467">42</span><span class="sxs-lookup"><span data-stu-id="3796f-467">42</span></span>|<span data-ttu-id="3796f-468">暫時通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-468">Temporary communication network error</span></span>|  
|<span data-ttu-id="3796f-469">43</span><span class="sxs-lookup"><span data-stu-id="3796f-469">43</span></span>|<span data-ttu-id="3796f-470">未知的交換收件者</span><span class="sxs-lookup"><span data-stu-id="3796f-470">Unknown interchange recipient</span></span>|  
|<span data-ttu-id="3796f-471">45</span><span class="sxs-lookup"><span data-stu-id="3796f-471">45</span></span>|<span data-ttu-id="3796f-472">尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-472">Trailing separator</span></span>|  
|<span data-ttu-id="3796f-473">46</span><span class="sxs-lookup"><span data-stu-id="3796f-473">46</span></span>|<span data-ttu-id="3796f-474">不支援字元集</span><span class="sxs-lookup"><span data-stu-id="3796f-474">Character set not supported</span></span>|  
|<span data-ttu-id="3796f-475">47</span><span class="sxs-lookup"><span data-stu-id="3796f-475">47</span></span>|<span data-ttu-id="3796f-476">不支援信封功能</span><span class="sxs-lookup"><span data-stu-id="3796f-476">Envelope functionality not supported</span></span>|  
|<span data-ttu-id="3796f-477">48</span><span class="sxs-lookup"><span data-stu-id="3796f-477">48</span></span>|<span data-ttu-id="3796f-478">違反相依性條件</span><span class="sxs-lookup"><span data-stu-id="3796f-478">Dependency condition violated</span></span>|  
|<span data-ttu-id="3796f-479">70</span><span class="sxs-lookup"><span data-stu-id="3796f-479">70</span></span>|<span data-ttu-id="3796f-480">交易集遺失或是交易集識別碼無效</span><span class="sxs-lookup"><span data-stu-id="3796f-480">Transaction set is missing or invalid transaction set Identifier</span></span>|  
|<span data-ttu-id="3796f-481">71</span><span class="sxs-lookup"><span data-stu-id="3796f-481">71</span></span>|<span data-ttu-id="3796f-482">交易集或群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-482">Transaction set or group control number mismatch</span></span>|  
|<span data-ttu-id="3796f-483">72</span><span class="sxs-lookup"><span data-stu-id="3796f-483">72</span></span>|<span data-ttu-id="3796f-484">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-484">Unrecognized segment ID</span></span>|  
|<span data-ttu-id="3796f-485">73</span><span class="sxs-lookup"><span data-stu-id="3796f-485">73</span></span>|<span data-ttu-id="3796f-486">XML 不在正確的位置</span><span class="sxs-lookup"><span data-stu-id="3796f-486">XML not at correct position</span></span>|  
|<span data-ttu-id="3796f-487">74</span><span class="sxs-lookup"><span data-stu-id="3796f-487">74</span></span>|<span data-ttu-id="3796f-488">區段群組的重複太少</span><span class="sxs-lookup"><span data-stu-id="3796f-488">Too few segment group repetitions</span></span>|  
|<span data-ttu-id="3796f-489">75</span><span class="sxs-lookup"><span data-stu-id="3796f-489">75</span></span>|<span data-ttu-id="3796f-490">區段的重複太少</span><span class="sxs-lookup"><span data-stu-id="3796f-490">Too few segment repetitions</span></span>|  
|<span data-ttu-id="3796f-491">76</span><span class="sxs-lookup"><span data-stu-id="3796f-491">76</span></span>|<span data-ttu-id="3796f-492">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="3796f-492">Too few data elements found</span></span>|  
  
 <span data-ttu-id="3796f-493">X12 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-493">The following Error/Syntax Error Codes will be used for X12:</span></span>  
  
|<span data-ttu-id="3796f-494">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-494">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="3796f-495">(適用於 X12)</span><span class="sxs-lookup"><span data-stu-id="3796f-495">(applicable to X12)</span></span>|<span data-ttu-id="3796f-496">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-496">Error Description for reporting</span></span>|  
|----------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="3796f-497">1</span><span class="sxs-lookup"><span data-stu-id="3796f-497">1</span></span>|<span data-ttu-id="3796f-498">不支援功能群組</span><span class="sxs-lookup"><span data-stu-id="3796f-498">Functional group not supported</span></span>|  
|<span data-ttu-id="3796f-499">2</span><span class="sxs-lookup"><span data-stu-id="3796f-499">2</span></span>|<span data-ttu-id="3796f-500">不支援功能群組版本</span><span class="sxs-lookup"><span data-stu-id="3796f-500">Functional group version not supported</span></span>|  
|<span data-ttu-id="3796f-501">3</span><span class="sxs-lookup"><span data-stu-id="3796f-501">3</span></span>|<span data-ttu-id="3796f-502">遺失功能群組結尾</span><span class="sxs-lookup"><span data-stu-id="3796f-502">Functional group trailer missing</span></span>|  
|<span data-ttu-id="3796f-503">4</span><span class="sxs-lookup"><span data-stu-id="3796f-503">4</span></span>|<span data-ttu-id="3796f-504">功能群組標頭與結尾中的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-504">Group control number in the functional group header and trailer do not agree</span></span>|  
|<span data-ttu-id="3796f-505">5</span><span class="sxs-lookup"><span data-stu-id="3796f-505">5</span></span>|<span data-ttu-id="3796f-506">包含的交易集數目不符合實際計數</span><span class="sxs-lookup"><span data-stu-id="3796f-506">Number of included transaction sets does not match actual count</span></span>|  
|<span data-ttu-id="3796f-507">6-26</span><span class="sxs-lookup"><span data-stu-id="3796f-507">6-26</span></span>|<span data-ttu-id="3796f-508">其他不支援的驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-508">Other unsupported validation errors</span></span>|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outgoing-interchanges"></a><span data-ttu-id="3796f-509">由接收管線針對回應外寄交換而接收之每個功能通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-509">Data Updated by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outgoing Interchanges</span></span>  
 <span data-ttu-id="3796f-510">對於接收管線所接收的每個功能通知，接收管線會更新相互關聯之傳送交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="3796f-510">For each functional acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.</span></span>  
  
 <span data-ttu-id="3796f-511">「EDI 解譯器」會使用內送通知中交換和群組標頭區段內的資料，找出資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3796f-511">The EDI Disassembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="3796f-512">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="3796f-512">Fields in ACK</span></span>|<span data-ttu-id="3796f-513">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="3796f-513">Fields in Data store</span></span>|<span data-ttu-id="3796f-514">註解</span><span class="sxs-lookup"><span data-stu-id="3796f-514">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="3796f-515">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-515">Interchange Sender ID</span></span>|<span data-ttu-id="3796f-516">交換接收方</span><span class="sxs-lookup"><span data-stu-id="3796f-516">Interchange Receiver</span></span>|<span data-ttu-id="3796f-517">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-517">Applicable to both X12 and EDIFACT</span></span>|  
|<span data-ttu-id="3796f-518">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-518">Interchange Receiver ID</span></span>|<span data-ttu-id="3796f-519">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="3796f-519">Interchange Sender</span></span>|<span data-ttu-id="3796f-520">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-520">Applicable to both X12 and EDIFACT</span></span>|  
|-|<span data-ttu-id="3796f-521">交換日期</span><span class="sxs-lookup"><span data-stu-id="3796f-521">Interchange Date</span></span>|-|  
|<span data-ttu-id="3796f-522">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-522">Interchange Control Number</span></span>|<span data-ttu-id="3796f-523">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-523">Interchange Control ID</span></span>|<span data-ttu-id="3796f-524">僅適用於 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-524">Applicable only to EDIFACT</span></span>|  
|<span data-ttu-id="3796f-525">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-525">Group Control Number</span></span>|<span data-ttu-id="3796f-526">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="3796f-526">Group Control Number</span></span>|<span data-ttu-id="3796f-527">僅適用於 X12</span><span class="sxs-lookup"><span data-stu-id="3796f-527">Applicable only to X12</span></span>|  
|-|<span data-ttu-id="3796f-528">交換方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="3796f-528">Interchange Direction = Send</span></span>|<span data-ttu-id="3796f-529">為確保唯一性，在 BIBO 實例中是必要項</span><span class="sxs-lookup"><span data-stu-id="3796f-529">Required since in BIBO Scenario for uniqueness</span></span>|  
|<span data-ttu-id="3796f-530">記錄類型</span><span class="sxs-lookup"><span data-stu-id="3796f-530">Record Type</span></span>|<span data-ttu-id="3796f-531">功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-531">Functional ACK Status</span></span>|<span data-ttu-id="3796f-532">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-532">Applicable to both X12 and EDIFACT</span></span>|  
  
 <span data-ttu-id="3796f-533">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="3796f-533">The data stored includes:</span></span>  
  
-   <span data-ttu-id="3796f-534">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="3796f-534">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="3796f-535">功能通知方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="3796f-535">Functional ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="3796f-536">功能通知狀態 =更新資料為已接收</span><span class="sxs-lookup"><span data-stu-id="3796f-536">Functional ACK Status =Update Data as Received</span></span>  
  
-   <span data-ttu-id="3796f-537">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-537">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-538">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-538">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-539">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="3796f-539">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-540">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-540">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-541">群組控制編號 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-541">Group Control Number = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-542">功能識別代碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-542">Functional ID Code = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-543">交易集的計數 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="3796f-543">Count of Transaction Sets = Existing Data</span></span>  
  
-   <span data-ttu-id="3796f-544">功能通知交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-544">Functional ACK Interchange Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="3796f-545">功能通知交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-545">Functional ACK Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-546">功能通知交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="3796f-546">Functional ACK Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="3796f-547">已傳送交易集的計數 = 更新資料 (X12 AK903，EDIFACT 不適用)</span><span class="sxs-lookup"><span data-stu-id="3796f-547">Count of Transaction Sets Delivered = Update Data (X12 AK903 and not applicable for EDIFACT)</span></span>  
  
-   <span data-ttu-id="3796f-548">已接受的交易集計數 = 更新資料 (X12 AK904，EDIFACT 不適用)</span><span class="sxs-lookup"><span data-stu-id="3796f-548">Count of Transaction Sets Accepted = Update Data (X12 AK904 and not applicable for EDIFACT)</span></span>  
  
-   <span data-ttu-id="3796f-549">通知/動作代碼 = 更新資料 (X12 AK901 和 UCI4) 參閱說明 1</span><span class="sxs-lookup"><span data-stu-id="3796f-549">ACK/Action Code = Update Data (X12 AK901 and UCI4) Refer Note 1</span></span>  
  
-   <span data-ttu-id="3796f-550">錯誤/語法錯誤碼  = (X12 AK905 和 UCI5) 參閱說明 2</span><span class="sxs-lookup"><span data-stu-id="3796f-550">Error/Syntax Error Code  = (X12 AK905 and UCI5) Refer Note 2</span></span>  
  
-   <span data-ttu-id="3796f-551">其他 X12 通知錯誤碼 2 = 更新資料 (X12-AK906)</span><span class="sxs-lookup"><span data-stu-id="3796f-551">Additional X12 ACK Error Code 2 = Update Data (X12-AK906)</span></span>  
  
-   <span data-ttu-id="3796f-552">其他 X12 通知錯誤碼 3 = 更新資料 (X12-AK907)</span><span class="sxs-lookup"><span data-stu-id="3796f-552">Additional X12 ACK Error Code 3 = Update Data (X12-AK907)</span></span>  
  
-   <span data-ttu-id="3796f-553">其他 X12 通知錯誤碼 4 = 更新資料 (X12-AK908)</span><span class="sxs-lookup"><span data-stu-id="3796f-553">Additional X12 ACK Error Code 4 = Update Data (X12-AK908)</span></span>  
  
-   <span data-ttu-id="3796f-554">其他 X12 通知錯誤碼 5 = 更新資料 (X12-AK909)</span><span class="sxs-lookup"><span data-stu-id="3796f-554">Additional X12 ACK Error Code 5 = Update Data (X12-AK909)</span></span>  
  
 <span data-ttu-id="3796f-555">將使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-555">The following ACK/Action Codes will be used:</span></span>  
  
|<span data-ttu-id="3796f-556">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-556">Data in ACK/Action Code</span></span>|<span data-ttu-id="3796f-557">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="3796f-557">Mapped for Status Reporting</span></span>|<span data-ttu-id="3796f-558">註解</span><span class="sxs-lookup"><span data-stu-id="3796f-558">Comment</span></span>|  
|------------------------------|---------------------------------|-------------|  
|<span data-ttu-id="3796f-559">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="3796f-559">A</span></span>|<span data-ttu-id="3796f-560">已接受</span><span class="sxs-lookup"><span data-stu-id="3796f-560">Accepted</span></span>|<span data-ttu-id="3796f-561">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-561">X12</span></span>|  
|<span data-ttu-id="3796f-562">P</span><span class="sxs-lookup"><span data-stu-id="3796f-562">P</span></span>|<span data-ttu-id="3796f-563">已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-563">Partially Accepted</span></span>|<span data-ttu-id="3796f-564">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-564">X12</span></span>|  
|<span data-ttu-id="3796f-565">R、M、W、X</span><span class="sxs-lookup"><span data-stu-id="3796f-565">R, M, W, X</span></span>|<span data-ttu-id="3796f-566">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-566">Rejected</span></span>|<span data-ttu-id="3796f-567">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-567">X12</span></span>|  
|<span data-ttu-id="3796f-568">E</span><span class="sxs-lookup"><span data-stu-id="3796f-568">E</span></span>|<span data-ttu-id="3796f-569">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-569">Accepted with errors</span></span>|<span data-ttu-id="3796f-570">X12</span><span class="sxs-lookup"><span data-stu-id="3796f-570">X12</span></span>|  
|<span data-ttu-id="3796f-571">4</span><span class="sxs-lookup"><span data-stu-id="3796f-571">4</span></span>|<span data-ttu-id="3796f-572">已拒絕</span><span class="sxs-lookup"><span data-stu-id="3796f-572">Rejected</span></span>|<span data-ttu-id="3796f-573">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-573">EDIFACT</span></span>|  
|<span data-ttu-id="3796f-574">7, 8</span><span class="sxs-lookup"><span data-stu-id="3796f-574">7, 8</span></span>|<span data-ttu-id="3796f-575">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="3796f-575">Accepted/Partially Accepted</span></span>|<span data-ttu-id="3796f-576">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="3796f-576">EDIFACT</span></span>|  
  
 <span data-ttu-id="3796f-577">EDIFACT 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-577">The following Error/Syntax Error Codes will be used for EDIFACT:</span></span>  
  
|<span data-ttu-id="3796f-578">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-578">Data in Error/Syntax Error Cod</span></span><br /><br /> <span data-ttu-id="3796f-579">(適用於 EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="3796f-579">(applicable to EDIFACT)</span></span>|<span data-ttu-id="3796f-580">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-580">Error Description for reporting</span></span>|  
|-------------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="3796f-581">2</span><span class="sxs-lookup"><span data-stu-id="3796f-581">2</span></span>|<span data-ttu-id="3796f-582">語法版本或層級不支援</span><span class="sxs-lookup"><span data-stu-id="3796f-582">Syntax version or level not supported</span></span>|  
|<span data-ttu-id="3796f-583">7</span><span class="sxs-lookup"><span data-stu-id="3796f-583">7</span></span>|<span data-ttu-id="3796f-584">交換收件者不是實際收件者</span><span class="sxs-lookup"><span data-stu-id="3796f-584">Interchange recipient not actual recipient</span></span>|  
|<span data-ttu-id="3796f-585">12</span><span class="sxs-lookup"><span data-stu-id="3796f-585">12</span></span>|<span data-ttu-id="3796f-586">無效值</span><span class="sxs-lookup"><span data-stu-id="3796f-586">Invalid value</span></span>|  
|<span data-ttu-id="3796f-587">13</span><span class="sxs-lookup"><span data-stu-id="3796f-587">13</span></span>|<span data-ttu-id="3796f-588">Missing</span><span class="sxs-lookup"><span data-stu-id="3796f-588">Missing</span></span>|  
|<span data-ttu-id="3796f-589">14</span><span class="sxs-lookup"><span data-stu-id="3796f-589">14</span></span>|<span data-ttu-id="3796f-590">在這個位置中不支援的值</span><span class="sxs-lookup"><span data-stu-id="3796f-590">Value not supported in this position</span></span>|  
|<span data-ttu-id="3796f-591">15</span><span class="sxs-lookup"><span data-stu-id="3796f-591">15</span></span>|<span data-ttu-id="3796f-592">在這個位置中不支援</span><span class="sxs-lookup"><span data-stu-id="3796f-592">Not supported in this position</span></span>|  
|<span data-ttu-id="3796f-593">16</span><span class="sxs-lookup"><span data-stu-id="3796f-593">16</span></span>|<span data-ttu-id="3796f-594">太多結構成分</span><span class="sxs-lookup"><span data-stu-id="3796f-594">Too many constituents</span></span>|  
|<span data-ttu-id="3796f-595">17</span><span class="sxs-lookup"><span data-stu-id="3796f-595">17</span></span>|<span data-ttu-id="3796f-596">沒有協議</span><span class="sxs-lookup"><span data-stu-id="3796f-596">No agreement</span></span>|  
|<span data-ttu-id="3796f-597">18</span><span class="sxs-lookup"><span data-stu-id="3796f-597">18</span></span>|<span data-ttu-id="3796f-598">未指定的錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-598">Unspecified error</span></span>|  
|<span data-ttu-id="3796f-599">19</span><span class="sxs-lookup"><span data-stu-id="3796f-599">19</span></span>|<span data-ttu-id="3796f-600">無效的小數點標記</span><span class="sxs-lookup"><span data-stu-id="3796f-600">Invalid decimal notation</span></span>|  
|<span data-ttu-id="3796f-601">20</span><span class="sxs-lookup"><span data-stu-id="3796f-601">20</span></span>|<span data-ttu-id="3796f-602">字元做為服務字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-602">Character invalid as service character</span></span>|  
|<span data-ttu-id="3796f-603">21</span><span class="sxs-lookup"><span data-stu-id="3796f-603">21</span></span>|<span data-ttu-id="3796f-604">無效字元</span><span class="sxs-lookup"><span data-stu-id="3796f-604">Invalid character(s)</span></span>|  
|<span data-ttu-id="3796f-605">22</span><span class="sxs-lookup"><span data-stu-id="3796f-605">22</span></span>|<span data-ttu-id="3796f-606">服務字元無效</span><span class="sxs-lookup"><span data-stu-id="3796f-606">Invalid service character(s)</span></span>|  
|<span data-ttu-id="3796f-607">23</span><span class="sxs-lookup"><span data-stu-id="3796f-607">23</span></span>|<span data-ttu-id="3796f-608">未知的交換傳送者</span><span class="sxs-lookup"><span data-stu-id="3796f-608">Unknown Interchange sender</span></span>|  
|<span data-ttu-id="3796f-609">24</span><span class="sxs-lookup"><span data-stu-id="3796f-609">24</span></span>|<span data-ttu-id="3796f-610">太舊</span><span class="sxs-lookup"><span data-stu-id="3796f-610">Too old</span></span>|  
|<span data-ttu-id="3796f-611">25</span><span class="sxs-lookup"><span data-stu-id="3796f-611">25</span></span>|<span data-ttu-id="3796f-612">不支援測試指示符號</span><span class="sxs-lookup"><span data-stu-id="3796f-612">Test indicator not supported</span></span>|  
|<span data-ttu-id="3796f-613">26</span><span class="sxs-lookup"><span data-stu-id="3796f-613">26</span></span>|<span data-ttu-id="3796f-614">偵測到重複</span><span class="sxs-lookup"><span data-stu-id="3796f-614">Duplicate detected</span></span>|  
|<span data-ttu-id="3796f-615">27</span><span class="sxs-lookup"><span data-stu-id="3796f-615">27</span></span>|<span data-ttu-id="3796f-616">不支援安全性函式</span><span class="sxs-lookup"><span data-stu-id="3796f-616">Security function not supported</span></span>|  
|<span data-ttu-id="3796f-617">28</span><span class="sxs-lookup"><span data-stu-id="3796f-617">28</span></span>|<span data-ttu-id="3796f-618">參考不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-618">References do not match</span></span>|  
|<span data-ttu-id="3796f-619">29</span><span class="sxs-lookup"><span data-stu-id="3796f-619">29</span></span>|<span data-ttu-id="3796f-620">控制計數不符合接收到的執行個體數目</span><span class="sxs-lookup"><span data-stu-id="3796f-620">Control count does not match number of instances received</span></span>|  
|<span data-ttu-id="3796f-621">30</span><span class="sxs-lookup"><span data-stu-id="3796f-621">30</span></span>|<span data-ttu-id="3796f-622">群組和訊息/封裝已混合</span><span class="sxs-lookup"><span data-stu-id="3796f-622">Groups and messages/packages mixed</span></span>|  
|<span data-ttu-id="3796f-623">31</span><span class="sxs-lookup"><span data-stu-id="3796f-623">31</span></span>|<span data-ttu-id="3796f-624">群組中有一種以上的訊息類型</span><span class="sxs-lookup"><span data-stu-id="3796f-624">More than one message type in group</span></span>|  
|<span data-ttu-id="3796f-625">32</span><span class="sxs-lookup"><span data-stu-id="3796f-625">32</span></span>|<span data-ttu-id="3796f-626">較低層級空白</span><span class="sxs-lookup"><span data-stu-id="3796f-626">Lower level empty</span></span>|  
|<span data-ttu-id="3796f-627">33</span><span class="sxs-lookup"><span data-stu-id="3796f-627">33</span></span>|<span data-ttu-id="3796f-628">在訊息、封裝或群組外部出現的項目無效</span><span class="sxs-lookup"><span data-stu-id="3796f-628">Invalid occurrence outside message, package, or group</span></span>|  
|<span data-ttu-id="3796f-629">34</span><span class="sxs-lookup"><span data-stu-id="3796f-629">34</span></span>|<span data-ttu-id="3796f-630">不允許巢狀指示符號</span><span class="sxs-lookup"><span data-stu-id="3796f-630">Nesting indicator not allowed</span></span>|  
|<span data-ttu-id="3796f-631">35</span><span class="sxs-lookup"><span data-stu-id="3796f-631">35</span></span>|<span data-ttu-id="3796f-632">太多資料元素或區段重複</span><span class="sxs-lookup"><span data-stu-id="3796f-632">Too many data element or segment repetitions</span></span>|  
|<span data-ttu-id="3796f-633">36</span><span class="sxs-lookup"><span data-stu-id="3796f-633">36</span></span>|<span data-ttu-id="3796f-634">太多區段群組重複</span><span class="sxs-lookup"><span data-stu-id="3796f-634">Too many segment group repetitions</span></span>|  
|<span data-ttu-id="3796f-635">37</span><span class="sxs-lookup"><span data-stu-id="3796f-635">37</span></span>|<span data-ttu-id="3796f-636">無效字元類型</span><span class="sxs-lookup"><span data-stu-id="3796f-636">Invalid type of character(s)</span></span>|  
|<span data-ttu-id="3796f-637">38</span><span class="sxs-lookup"><span data-stu-id="3796f-637">38</span></span>|<span data-ttu-id="3796f-638">在小數符號之前遺失數字</span><span class="sxs-lookup"><span data-stu-id="3796f-638">Missing digit in front of decimal sign</span></span>|  
|<span data-ttu-id="3796f-639">39</span><span class="sxs-lookup"><span data-stu-id="3796f-639">39</span></span>|<span data-ttu-id="3796f-640">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="3796f-640">Data element too long</span></span>|  
|<span data-ttu-id="3796f-641">40</span><span class="sxs-lookup"><span data-stu-id="3796f-641">40</span></span>|<span data-ttu-id="3796f-642">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="3796f-642">Data element too short</span></span>|  
|<span data-ttu-id="3796f-643">41</span><span class="sxs-lookup"><span data-stu-id="3796f-643">41</span></span>|<span data-ttu-id="3796f-644">永久通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-644">Permanent communication network error</span></span>|  
|<span data-ttu-id="3796f-645">42</span><span class="sxs-lookup"><span data-stu-id="3796f-645">42</span></span>|<span data-ttu-id="3796f-646">暫時通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-646">Temporary communication network error</span></span>|  
|<span data-ttu-id="3796f-647">43</span><span class="sxs-lookup"><span data-stu-id="3796f-647">43</span></span>|<span data-ttu-id="3796f-648">未知的交換收件者</span><span class="sxs-lookup"><span data-stu-id="3796f-648">Unknown interchange recipient</span></span>|  
|<span data-ttu-id="3796f-649">45</span><span class="sxs-lookup"><span data-stu-id="3796f-649">45</span></span>|<span data-ttu-id="3796f-650">尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="3796f-650">Trailing separator</span></span>|  
|<span data-ttu-id="3796f-651">46</span><span class="sxs-lookup"><span data-stu-id="3796f-651">46</span></span>|<span data-ttu-id="3796f-652">不支援字元集</span><span class="sxs-lookup"><span data-stu-id="3796f-652">Character set not supported</span></span>|  
|<span data-ttu-id="3796f-653">47</span><span class="sxs-lookup"><span data-stu-id="3796f-653">47</span></span>|<span data-ttu-id="3796f-654">不支援信封功能</span><span class="sxs-lookup"><span data-stu-id="3796f-654">Envelope functionality not supported</span></span>|  
|<span data-ttu-id="3796f-655">48</span><span class="sxs-lookup"><span data-stu-id="3796f-655">48</span></span>|<span data-ttu-id="3796f-656">違反相依性條件</span><span class="sxs-lookup"><span data-stu-id="3796f-656">Dependency condition violated</span></span>|  
|<span data-ttu-id="3796f-657">70</span><span class="sxs-lookup"><span data-stu-id="3796f-657">70</span></span>|<span data-ttu-id="3796f-658">交易集遺失或是交易集識別碼無效</span><span class="sxs-lookup"><span data-stu-id="3796f-658">Transaction set is missing or invalid transaction set Identifier</span></span>|  
|<span data-ttu-id="3796f-659">71</span><span class="sxs-lookup"><span data-stu-id="3796f-659">71</span></span>|<span data-ttu-id="3796f-660">交易集或群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-660">Transaction set or group control number mismatch</span></span>|  
|<span data-ttu-id="3796f-661">72</span><span class="sxs-lookup"><span data-stu-id="3796f-661">72</span></span>|<span data-ttu-id="3796f-662">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="3796f-662">Unrecognized segment ID</span></span>|  
|<span data-ttu-id="3796f-663">73</span><span class="sxs-lookup"><span data-stu-id="3796f-663">73</span></span>|<span data-ttu-id="3796f-664">XML 不在正確的位置</span><span class="sxs-lookup"><span data-stu-id="3796f-664">XML not at correct position</span></span>|  
|<span data-ttu-id="3796f-665">74</span><span class="sxs-lookup"><span data-stu-id="3796f-665">74</span></span>|<span data-ttu-id="3796f-666">區段群組的重複太少</span><span class="sxs-lookup"><span data-stu-id="3796f-666">Too few segment group repetitions</span></span>|  
|<span data-ttu-id="3796f-667">75</span><span class="sxs-lookup"><span data-stu-id="3796f-667">75</span></span>|<span data-ttu-id="3796f-668">區段的重複太少</span><span class="sxs-lookup"><span data-stu-id="3796f-668">Too few segment repetitions</span></span>|  
|<span data-ttu-id="3796f-669">76</span><span class="sxs-lookup"><span data-stu-id="3796f-669">76</span></span>|<span data-ttu-id="3796f-670">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="3796f-670">Too few data elements found</span></span>|  
  
 <span data-ttu-id="3796f-671">X12 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="3796f-671">The following Error/Syntax Error Codes will be used for X12:</span></span>  
  
|<span data-ttu-id="3796f-672">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-672">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="3796f-673">(適用於 X12)</span><span class="sxs-lookup"><span data-stu-id="3796f-673">(applicable to X12)</span></span>|<span data-ttu-id="3796f-674">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="3796f-674">Error Description for reporting</span></span>|  
|----------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="3796f-675">1</span><span class="sxs-lookup"><span data-stu-id="3796f-675">1</span></span>|<span data-ttu-id="3796f-676">不支援功能群組</span><span class="sxs-lookup"><span data-stu-id="3796f-676">Functional group not supported</span></span>|  
|<span data-ttu-id="3796f-677">2</span><span class="sxs-lookup"><span data-stu-id="3796f-677">2</span></span>|<span data-ttu-id="3796f-678">不支援功能群組版本</span><span class="sxs-lookup"><span data-stu-id="3796f-678">Functional group version not supported</span></span>|  
|<span data-ttu-id="3796f-679">3</span><span class="sxs-lookup"><span data-stu-id="3796f-679">3</span></span>|<span data-ttu-id="3796f-680">遺失功能群組結尾</span><span class="sxs-lookup"><span data-stu-id="3796f-680">Functional group trailer missing</span></span>|  
|<span data-ttu-id="3796f-681">4</span><span class="sxs-lookup"><span data-stu-id="3796f-681">4</span></span>|<span data-ttu-id="3796f-682">功能群組標頭與結尾中的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="3796f-682">Group control number in the functional group header and trailer do not agree</span></span>|  
|<span data-ttu-id="3796f-683">5</span><span class="sxs-lookup"><span data-stu-id="3796f-683">5</span></span>|<span data-ttu-id="3796f-684">包含的交易集數目不符合實際計數</span><span class="sxs-lookup"><span data-stu-id="3796f-684">Number of included transaction sets does not match actual count</span></span>|  
|<span data-ttu-id="3796f-685">6-26</span><span class="sxs-lookup"><span data-stu-id="3796f-685">6-26</span></span>|<span data-ttu-id="3796f-686">其他不支援的驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="3796f-686">Other unsupported validation errors</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3796f-687">請參閱</span><span class="sxs-lookup"><span data-stu-id="3796f-687">See Also</span></span>  
 <span data-ttu-id="3796f-688">[資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="3796f-688">[How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="3796f-689">如何儲存輸入 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="3796f-689">How Data Is Stored for Inbound EDI Messages</span></span>](../core/how-data-is-stored-for-inbound-edi-messages.md)