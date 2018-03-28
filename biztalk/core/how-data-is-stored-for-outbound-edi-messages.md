---
title: 資料如何儲存輸出 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6e576fc-37fd-417d-ae68-607a0a8bcc0a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f98d5113c63e29f3f4b85834b7ca1aa0836d0a5d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-data-is-stored-for-outbound-edi-messages"></a><span data-ttu-id="29213-102">如何儲存輸出 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="29213-102">How Data Is Stored for Outbound EDI Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="29213-103"> 會針對輸出交換，進行下列作業以產生狀態報告項目：</span><span class="sxs-lookup"><span data-stu-id="29213-103"> does the following to generate a status report entry for an outbound interchange:</span></span>  
  
1.  <span data-ttu-id="29213-104">輸出訊息 XML 傳送到 EDI 傳送管線時，傳送管線便會以下列的值，在狀態報告資料存放區中建立項目：</span><span class="sxs-lookup"><span data-stu-id="29213-104">When outbound message XML is sent to the EDI send pipeline, the send pipeline creates an entry in the status reporting data store with the following values:</span></span>  
  
    -   <span data-ttu-id="29213-105">交換狀態項目已設定為「已處理」</span><span class="sxs-lookup"><span data-stu-id="29213-105">Interchange status entry is set to Processed</span></span>  
  
    -   <span data-ttu-id="29213-106">交換通知狀態項目 (每個交換一個) 已設定為「預期」</span><span class="sxs-lookup"><span data-stu-id="29213-106">Interchange ACK status entry (one per interchange) is set to Expected</span></span>  
  
    -   <span data-ttu-id="29213-107">功能通知狀態項目 (X12 中每個群組一個，EDIFACT 中所有群組共用一個) 已設定為「預期」</span><span class="sxs-lookup"><span data-stu-id="29213-107">Functional ACK status entries (one per group in X12, one for all groups in EDIFACT) are set to Expected</span></span>  
  
2.  <span data-ttu-id="29213-108">在 EDI 訊息傳送至交易夥伴，且已從交易夥伴傳回通知後，接收通知的 EDI 接收管線就會視情況將交換狀態、交換通知狀態和功能通知狀態項目，更新為「已接受」/「已部分接受」/「已拒絕」。</span><span class="sxs-lookup"><span data-stu-id="29213-108">After the EDI message has been sent to the trading partner, and the acknowledgment has been returned from the trading partner, the EDI receive pipeline that receives the acknowledgment updates the Interchange status, the Interchange ACK status, and the Functional ACK status entries to Accepted/Partially Accepted/Rejected, as appropriate.</span></span>  
  
## <a name="data-stored-by-the-send-pipeline-for-outbound-interchanges"></a><span data-ttu-id="29213-109">傳送管線所儲存的輸出交換資料</span><span class="sxs-lookup"><span data-stu-id="29213-109">Data Stored by the Send Pipeline for Outbound Interchanges</span></span>  
 <span data-ttu-id="29213-110">傳送管線會在狀態報告資料存放區中，針對其所傳送的每個交換建立記錄。</span><span class="sxs-lookup"><span data-stu-id="29213-110">The send pipeline creates a record in the status report data store for each interchange that it sends.</span></span> <span data-ttu-id="29213-111">此項目所需要的多數資料，都會在交換的標頭/結尾區段中 (ISA/IEA 或 UNB/UNZ) 提供。</span><span class="sxs-lookup"><span data-stu-id="29213-111">Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ).</span></span> <span data-ttu-id="29213-112">其他資料則由傳送埠屬性提供。</span><span class="sxs-lookup"><span data-stu-id="29213-112">Other data is available from send port properties.</span></span> <span data-ttu-id="29213-113">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="29213-113">The data stored includes:</span></span>  
  
-   <span data-ttu-id="29213-114">記錄類型 = 交換狀態</span><span class="sxs-lookup"><span data-stu-id="29213-114">Record Type = Interchange Status</span></span>  
  
-   <span data-ttu-id="29213-115">交換方向 = 更新資料 = 傳送</span><span class="sxs-lookup"><span data-stu-id="29213-115">Interchange Direction = Update Data = Send</span></span>  
  
-   <span data-ttu-id="29213-116">交換接收者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-116">Interchange Receiver = Update Data</span></span>  
  
-   <span data-ttu-id="29213-117">交換傳送者 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-117">Interchange Sender = Update Data</span></span>  
  
-   <span data-ttu-id="29213-118">交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-118">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="29213-119">交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-119">Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="29213-120">交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-120">Interchange Control ID = Update Data</span></span>  
  
-   <span data-ttu-id="29213-121">交換狀態：已處理/傳送。</span><span class="sxs-lookup"><span data-stu-id="29213-121">Interchange Status: Processed/Sent.</span></span> <span data-ttu-id="29213-122">「已處理」的狀態表示傳送管線已成功處理交換，並將它傳送至傳送配接器等候傳遞。</span><span class="sxs-lookup"><span data-stu-id="29213-122">A status of Processed indicates that the send pipeline has successfully processed the interchange and handed it over to the send adapter for delivery.</span></span>  
  
-   <span data-ttu-id="29213-123">交換控制計數 (在 X12 中分別為群組/訊息) = 資料</span><span class="sxs-lookup"><span data-stu-id="29213-123">Interchange Control Count (Groups/Messages in X12 respectively) = Data</span></span>  
  
-   <span data-ttu-id="29213-124">交換傳送埠識別碼 = 資料</span><span class="sxs-lookup"><span data-stu-id="29213-124">Interchange Send Port ID = Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a><span data-ttu-id="29213-125">由接收管線針對回應輸出交換而接收之每個技術通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="29213-125">Data Stored by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange</span></span>  
 <span data-ttu-id="29213-126">接收管線會在狀態報告資料存放區中，針對其所接收的每個技術通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="29213-126">The receive pipeline creates a record in the status report data store for each technical acknowledgment that it receives.</span></span> <span data-ttu-id="29213-127">接收管線會建立每個交換狀態報告資料存放區中所收到的記錄。</span><span class="sxs-lookup"><span data-stu-id="29213-127">The receive pipeline creates a record of each interchange received in the status report data store.</span></span> <span data-ttu-id="29213-128">每個技術通知以回應傳送給交易夥伴交換接收的資料存放區中建立一個技術通知狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="29213-128">creates one technical acknowledgment status report entry in the data store for each technical ACK received as a response to an interchange sent to a trading partner.</span></span> <span data-ttu-id="29213-129">X12 類型的技術通知是 TA1，EDIFACT 類型的技術通知為僅包含 UCI 區段的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="29213-129">The technical acknowledge is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT.</span></span> <span data-ttu-id="29213-130">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="29213-130">The data stored includes:</span></span>  
  
-   <span data-ttu-id="29213-131">記錄類型 = 交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="29213-131">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="29213-132">交換通知方向 = 傳送 – 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-132">Interchange ACK Direction = Send – Update Data</span></span>  
  
-   <span data-ttu-id="29213-133">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-133">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-134">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-134">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-135">交換日期 = 更新資料 (X12 相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-135">Interchange Date = Update Data (required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="29213-136">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-136">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-137">交換通知狀態 = 已產生或不適用\<參閱說明 0\> -更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-137">Interchange ACK Status = Generated or Not Applicable \<Refer Note 0\> - Update Data</span></span>  
  
-   <span data-ttu-id="29213-138">交換通知控制識別碼= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-138">Interchange ACK Control ID= Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-139">交換通知日期= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-139">Interchange ACK Date = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-140">交換通知時間= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-140">Interchange ACK Time = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-141">通知/動作代碼 = 更新資料\<附註 1，請參閱\>（從 X12 TA104 或 edifact-uci4） \*</span><span class="sxs-lookup"><span data-stu-id="29213-141">ACK/Action Code = Update Data  \<refer note 1\> (from X12-TA104 or EDIFACT-UCI4)\*</span></span>  
  
-   <span data-ttu-id="29213-142">通知說明碼 = 更新資料\<，請參閱註 2\> （從 X12-TA105，EDIFACT 不適用) \*</span><span class="sxs-lookup"><span data-stu-id="29213-142">ACK Note Code = Update Data \<Refer Note 2\> (from X12-TA105, not applicable for EDIFACT)\*</span></span>  
  
 <span data-ttu-id="29213-143">使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-143">The following ACK/Action Codes are used:</span></span>  
  
|<span data-ttu-id="29213-144">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-144">Data in ACK/Action Code</span></span>|<span data-ttu-id="29213-145">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-145">Error description for Reporting</span></span>|<span data-ttu-id="29213-146">註解 (適用性)</span><span class="sxs-lookup"><span data-stu-id="29213-146">Comment (applicability)</span></span>|  
|------------------------------|-------------------------------------|-------------------------------|  
|<span data-ttu-id="29213-147">A</span><span class="sxs-lookup"><span data-stu-id="29213-147">A</span></span>|<span data-ttu-id="29213-148">已接受</span><span class="sxs-lookup"><span data-stu-id="29213-148">Accepted</span></span>|<span data-ttu-id="29213-149">X12</span><span class="sxs-lookup"><span data-stu-id="29213-149">X12</span></span>|  
|<span data-ttu-id="29213-150">E</span><span class="sxs-lookup"><span data-stu-id="29213-150">E</span></span>|<span data-ttu-id="29213-151">已接受，但已記錄錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-151">Accepted, errors noted</span></span>|<span data-ttu-id="29213-152">X12</span><span class="sxs-lookup"><span data-stu-id="29213-152">X12</span></span>|  
|<span data-ttu-id="29213-153">P</span><span class="sxs-lookup"><span data-stu-id="29213-153">P</span></span>|<span data-ttu-id="29213-154">已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-154">Partially Accepted</span></span>|<span data-ttu-id="29213-155">X12</span><span class="sxs-lookup"><span data-stu-id="29213-155">X12</span></span>|  
|<span data-ttu-id="29213-156">R</span><span class="sxs-lookup"><span data-stu-id="29213-156">R</span></span>|<span data-ttu-id="29213-157">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-157">Rejected</span></span>|<span data-ttu-id="29213-158">X12</span><span class="sxs-lookup"><span data-stu-id="29213-158">X12</span></span>|  
|<span data-ttu-id="29213-159">4</span><span class="sxs-lookup"><span data-stu-id="29213-159">4</span></span>|<span data-ttu-id="29213-160">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-160">Rejected</span></span>|<span data-ttu-id="29213-161">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-161">EDIFACT</span></span>|  
|<span data-ttu-id="29213-162">8</span><span class="sxs-lookup"><span data-stu-id="29213-162">8</span></span>|<span data-ttu-id="29213-163">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-163">Accepted/Partially Accepted</span></span>|<span data-ttu-id="29213-164">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-164">EDIFACT</span></span>|  
  
 <span data-ttu-id="29213-165">使用的通知說明碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-165">The following ACK Note Codes are used:</span></span>  
  
|<span data-ttu-id="29213-166">通知說明碼中的資料 (在 X12 中)</span><span class="sxs-lookup"><span data-stu-id="29213-166">Data in ACK Note Code (in X12)</span></span>|<span data-ttu-id="29213-167">Description</span><span class="sxs-lookup"><span data-stu-id="29213-167">Description</span></span>|  
|--------------------------------------|-----------------|  
|<span data-ttu-id="29213-168">000</span><span class="sxs-lookup"><span data-stu-id="29213-168">000</span></span>|<span data-ttu-id="29213-169">成功</span><span class="sxs-lookup"><span data-stu-id="29213-169">Success</span></span>|  
|<span data-ttu-id="29213-170">001</span><span class="sxs-lookup"><span data-stu-id="29213-170">001</span></span>|<span data-ttu-id="29213-171">交換控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="29213-171">Interchange Control Number mismatch</span></span>|  
|<span data-ttu-id="29213-172">002</span><span class="sxs-lookup"><span data-stu-id="29213-172">002</span></span>|<span data-ttu-id="29213-173">不支援標準</span><span class="sxs-lookup"><span data-stu-id="29213-173">Standard not supported</span></span>|  
|<span data-ttu-id="29213-174">003</span><span class="sxs-lookup"><span data-stu-id="29213-174">003</span></span>|<span data-ttu-id="29213-175">不支援控制項版本</span><span class="sxs-lookup"><span data-stu-id="29213-175">Version of the Controls Not Supported</span></span>|  
|<span data-ttu-id="29213-176">004</span><span class="sxs-lookup"><span data-stu-id="29213-176">004</span></span>|<span data-ttu-id="29213-177">區段結束字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-177">Segment Terminator is Invalid</span></span>|  
|<span data-ttu-id="29213-178">005</span><span class="sxs-lookup"><span data-stu-id="29213-178">005</span></span>|<span data-ttu-id="29213-179">無效的傳送者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="29213-179">Invalid Interchange ID Qualifier for Sender</span></span>|  
|<span data-ttu-id="29213-180">006</span><span class="sxs-lookup"><span data-stu-id="29213-180">006</span></span>|<span data-ttu-id="29213-181">無效的交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-181">Invalid Interchange Sender ID</span></span>|  
|<span data-ttu-id="29213-182">007</span><span class="sxs-lookup"><span data-stu-id="29213-182">007</span></span>|<span data-ttu-id="29213-183">無效的接收者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="29213-183">Invalid Interchange ID Qualifier for Receiver</span></span>|  
|<span data-ttu-id="29213-184">008</span><span class="sxs-lookup"><span data-stu-id="29213-184">008</span></span>|<span data-ttu-id="29213-185">無效的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-185">Invalid Interchange Receiver ID</span></span>|  
|<span data-ttu-id="29213-186">009</span><span class="sxs-lookup"><span data-stu-id="29213-186">009</span></span>|<span data-ttu-id="29213-187">未知的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-187">Unknown Interchange Receiver ID</span></span>|  
|<span data-ttu-id="29213-188">010</span><span class="sxs-lookup"><span data-stu-id="29213-188">010</span></span>|<span data-ttu-id="29213-189">無效的授權資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="29213-189">Invalid Authorization Information Qualifier Value</span></span>|  
|<span data-ttu-id="29213-190">011</span><span class="sxs-lookup"><span data-stu-id="29213-190">011</span></span>|<span data-ttu-id="29213-191">無效的授權資訊值</span><span class="sxs-lookup"><span data-stu-id="29213-191">Invalid Authorization Information Value</span></span>|  
|<span data-ttu-id="29213-192">012</span><span class="sxs-lookup"><span data-stu-id="29213-192">012</span></span>|<span data-ttu-id="29213-193">無效的安全性資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="29213-193">Invalid Security Information Qualifier Value</span></span>|  
|<span data-ttu-id="29213-194">013</span><span class="sxs-lookup"><span data-stu-id="29213-194">013</span></span>|<span data-ttu-id="29213-195">無效的安全性資訊值</span><span class="sxs-lookup"><span data-stu-id="29213-195">Invalid Security Information Value</span></span>|  
|<span data-ttu-id="29213-196">014</span><span class="sxs-lookup"><span data-stu-id="29213-196">014</span></span>|<span data-ttu-id="29213-197">無效的交換日期值</span><span class="sxs-lookup"><span data-stu-id="29213-197">Invalid Interchange Date Value</span></span>|  
|<span data-ttu-id="29213-198">015</span><span class="sxs-lookup"><span data-stu-id="29213-198">015</span></span>|<span data-ttu-id="29213-199">無效的交換時間值</span><span class="sxs-lookup"><span data-stu-id="29213-199">Invalid Interchange Time Value</span></span>|  
|<span data-ttu-id="29213-200">016</span><span class="sxs-lookup"><span data-stu-id="29213-200">016</span></span>|<span data-ttu-id="29213-201">無效的交換標準識別碼值</span><span class="sxs-lookup"><span data-stu-id="29213-201">Invalid Interchange Standards Identifier Value</span></span>|  
|<span data-ttu-id="29213-202">017</span><span class="sxs-lookup"><span data-stu-id="29213-202">017</span></span>|<span data-ttu-id="29213-203">無效的交換版本識別碼值</span><span class="sxs-lookup"><span data-stu-id="29213-203">Invalid Interchange Version ID Value</span></span>|  
|<span data-ttu-id="29213-204">018</span><span class="sxs-lookup"><span data-stu-id="29213-204">018</span></span>|<span data-ttu-id="29213-205">無效的交換控制編號值</span><span class="sxs-lookup"><span data-stu-id="29213-205">Invalid Interchange Control Number Value</span></span>|  
|<span data-ttu-id="29213-206">019</span><span class="sxs-lookup"><span data-stu-id="29213-206">019</span></span>|<span data-ttu-id="29213-207">無效的通知要求值</span><span class="sxs-lookup"><span data-stu-id="29213-207">Invalid Acknowledgment Requested Value</span></span>|  
|<span data-ttu-id="29213-208">020</span><span class="sxs-lookup"><span data-stu-id="29213-208">020</span></span>|<span data-ttu-id="29213-209">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="29213-209">Invalid Test Indicator Value</span></span>|  
|<span data-ttu-id="29213-210">021</span><span class="sxs-lookup"><span data-stu-id="29213-210">021</span></span>|<span data-ttu-id="29213-211">無效之包括的群組數目值</span><span class="sxs-lookup"><span data-stu-id="29213-211">Invalid Number of Included Groups Value</span></span>|  
|<span data-ttu-id="29213-212">022</span><span class="sxs-lookup"><span data-stu-id="29213-212">022</span></span>|<span data-ttu-id="29213-213">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="29213-213">Invalid Control Structure</span></span>|  
|<span data-ttu-id="29213-214">023</span><span class="sxs-lookup"><span data-stu-id="29213-214">023</span></span>|<span data-ttu-id="29213-215">不適當的檔案結尾</span><span class="sxs-lookup"><span data-stu-id="29213-215">Improper End-of-File</span></span>|  
|<span data-ttu-id="29213-216">024</span><span class="sxs-lookup"><span data-stu-id="29213-216">024</span></span>|<span data-ttu-id="29213-217">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="29213-217">Invalid Interchange Content</span></span>|  
|<span data-ttu-id="29213-218">025</span><span class="sxs-lookup"><span data-stu-id="29213-218">025</span></span>|<span data-ttu-id="29213-219">重複的交換控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-219">Duplicate Interchange Control Number</span></span>|  
|<span data-ttu-id="29213-220">026</span><span class="sxs-lookup"><span data-stu-id="29213-220">026</span></span>|<span data-ttu-id="29213-221">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-221">Invalid Data Element Separator</span></span>|  
|<span data-ttu-id="29213-222">027</span><span class="sxs-lookup"><span data-stu-id="29213-222">027</span></span>|<span data-ttu-id="29213-223">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-223">Invalid Component Element Separator</span></span>|  
|<span data-ttu-id="29213-224">028</span><span class="sxs-lookup"><span data-stu-id="29213-224">028</span></span>|<span data-ttu-id="29213-225">延遲傳遞要求中無效的傳遞日期</span><span class="sxs-lookup"><span data-stu-id="29213-225">Invalid Delivery Date in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="29213-226">029</span><span class="sxs-lookup"><span data-stu-id="29213-226">029</span></span>|<span data-ttu-id="29213-227">延遲傳遞要求中無效的傳遞時間</span><span class="sxs-lookup"><span data-stu-id="29213-227">Invalid Delivery Time in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="29213-228">030</span><span class="sxs-lookup"><span data-stu-id="29213-228">030</span></span>|<span data-ttu-id="29213-229">延遲的傳遞要求中無效的傳遞時間碼</span><span class="sxs-lookup"><span data-stu-id="29213-229">Invalid Delivery Time Code in Deferred Delivery  Request</span></span>|  
|<span data-ttu-id="29213-230">031</span><span class="sxs-lookup"><span data-stu-id="29213-230">031</span></span>|<span data-ttu-id="29213-231">無效的服務等級</span><span class="sxs-lookup"><span data-stu-id="29213-231">Invalid Grade of Service</span></span>|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a><span data-ttu-id="29213-232">由接收管線針對回應輸出交換而接收之每個技術通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="29213-232">Data Updated by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange</span></span>  
 <span data-ttu-id="29213-233">對於接收管線所接收的每個技術通知，接收管線都會更新相互關聯之傳送交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="29213-233">For each technical acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.</span></span>  
  
 <span data-ttu-id="29213-234">EDI 解譯器會使用內送通知中 UCI 和 TA1 區段內的資料，找出資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29213-234">The EDI Disassembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="29213-235">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="29213-235">Fields in ACK</span></span>|<span data-ttu-id="29213-236">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="29213-236">Fields in Data store</span></span>|<span data-ttu-id="29213-237">註解</span><span class="sxs-lookup"><span data-stu-id="29213-237">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="29213-238">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-238">Interchange Sender ID</span></span>|<span data-ttu-id="29213-239">交換接收方</span><span class="sxs-lookup"><span data-stu-id="29213-239">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="29213-240">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-240">Interchange Receiver ID</span></span>|<span data-ttu-id="29213-241">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="29213-241">Interchange Sender</span></span>|-|  
|-|<span data-ttu-id="29213-242">交換日期</span><span class="sxs-lookup"><span data-stu-id="29213-242">Interchange Date</span></span>|-|  
|<span data-ttu-id="29213-243">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-243">Interchange Control Number</span></span>|<span data-ttu-id="29213-244">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-244">Interchange Control ID</span></span>|-|  
|-|<span data-ttu-id="29213-245">交換方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="29213-245">Interchange Direction = Send</span></span>|<span data-ttu-id="29213-246">在為唯一性而保留的批次實例中是必要的</span><span class="sxs-lookup"><span data-stu-id="29213-246">Required in preserved batch scenario for uniqueness</span></span>|  
|<span data-ttu-id="29213-247">記錄類型</span><span class="sxs-lookup"><span data-stu-id="29213-247">Record Type</span></span>|<span data-ttu-id="29213-248">交換狀態和交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="29213-248">Interchange Status and Interchange ACK Status</span></span>|-|  
  
 <span data-ttu-id="29213-249">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="29213-249">The data stored includes:</span></span>  
  
-   <span data-ttu-id="29213-250">交換通知方向 = 接收 – 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-250">Interchange ACK Direction = Receive – Existing Data</span></span>  
  
-   <span data-ttu-id="29213-251">交換通知狀態 = 已收到</span><span class="sxs-lookup"><span data-stu-id="29213-251">Interchange ACK Status = Received</span></span>  
  
-   <span data-ttu-id="29213-252">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-252">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-253">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-253">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-254">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="29213-254">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-255">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-255">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-256">交換通知控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-256">Interchange ACK Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="29213-257">交換通知日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-257">Interchange ACK Date = Update Data</span></span>  
  
-   <span data-ttu-id="29213-258">交換通知時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-258">Interchange ACK Time = Update Data</span></span>  
  
-   <span data-ttu-id="29213-259">通知/動作代碼 = 更新資料 （從 X12 TA104 或 edifact-uci4） \*\<附註 1，請參閱\></span><span class="sxs-lookup"><span data-stu-id="29213-259">ACK/Action Code = Update Data (from X12-TA104 or EDIFACT-UCI4)\* \<Refer Note 1\></span></span>  
  
-   <span data-ttu-id="29213-260">通知說明碼 2 = 更新資料 (從 X12 TA105 和不 edifact 的值) \* \<，請參閱註 2\></span><span class="sxs-lookup"><span data-stu-id="29213-260">ACK Note Code 2 = Update Data (from X12-TA105 and not valued for EDIFACT)\* \<Refer Note 2\></span></span>  
  
 <span data-ttu-id="29213-261">來自 ACK X12:TA1-104 或 EDIFACT UCI4 的資料將會加以對應，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29213-261">The data from the ACK X12:TA1-104 or EDIFACT UCI4 is to be mapped as follows:</span></span>  
  
|<span data-ttu-id="29213-262">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-262">Data in ACK/Action Code</span></span>|<span data-ttu-id="29213-263">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="29213-263">Mapped for Status Reporting</span></span>|<span data-ttu-id="29213-264">註解</span><span class="sxs-lookup"><span data-stu-id="29213-264">Comment</span></span>|  
|------------------------------|---------------------------------|-------------|  
|<span data-ttu-id="29213-265">A</span><span class="sxs-lookup"><span data-stu-id="29213-265">A</span></span>|<span data-ttu-id="29213-266">已接受</span><span class="sxs-lookup"><span data-stu-id="29213-266">Accepted</span></span>|<span data-ttu-id="29213-267">X12</span><span class="sxs-lookup"><span data-stu-id="29213-267">X12</span></span>|  
|<span data-ttu-id="29213-268">P</span><span class="sxs-lookup"><span data-stu-id="29213-268">P</span></span>|<span data-ttu-id="29213-269">已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-269">Partially Accepted</span></span>|<span data-ttu-id="29213-270">X12</span><span class="sxs-lookup"><span data-stu-id="29213-270">X12</span></span>|  
|<span data-ttu-id="29213-271">R、M、W、X</span><span class="sxs-lookup"><span data-stu-id="29213-271">R, M, W, X</span></span>|<span data-ttu-id="29213-272">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-272">Rejected</span></span>|<span data-ttu-id="29213-273">X12</span><span class="sxs-lookup"><span data-stu-id="29213-273">X12</span></span>|  
|<span data-ttu-id="29213-274">E</span><span class="sxs-lookup"><span data-stu-id="29213-274">E</span></span>|<span data-ttu-id="29213-275">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-275">Accepted with errors</span></span>|<span data-ttu-id="29213-276">X12</span><span class="sxs-lookup"><span data-stu-id="29213-276">X12</span></span>|  
|<span data-ttu-id="29213-277">4</span><span class="sxs-lookup"><span data-stu-id="29213-277">4</span></span>|<span data-ttu-id="29213-278">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-278">Rejected</span></span>|<span data-ttu-id="29213-279">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-279">EDIFACT</span></span>|  
|<span data-ttu-id="29213-280">7, 8</span><span class="sxs-lookup"><span data-stu-id="29213-280">7, 8</span></span>|<span data-ttu-id="29213-281">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-281">Accepted/Partially Accepted</span></span>|<span data-ttu-id="29213-282">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-282">EDIFACT</span></span>|  
  
 <span data-ttu-id="29213-283">使用的通知說明碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-283">The following ACK Note Codes are used:</span></span>  
  
|<span data-ttu-id="29213-284">通知說明碼中的資料 (在 X12 中)</span><span class="sxs-lookup"><span data-stu-id="29213-284">Data in ACK Note Code (in X12)</span></span>|<span data-ttu-id="29213-285">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="29213-285">Mapped for Status Reporting</span></span>|  
|--------------------------------------|---------------------------------|  
|<span data-ttu-id="29213-286">000</span><span class="sxs-lookup"><span data-stu-id="29213-286">000</span></span>|<span data-ttu-id="29213-287">成功</span><span class="sxs-lookup"><span data-stu-id="29213-287">Success</span></span>|  
|<span data-ttu-id="29213-288">001</span><span class="sxs-lookup"><span data-stu-id="29213-288">001</span></span>|<span data-ttu-id="29213-289">交換控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="29213-289">Interchange Control Number mismatch</span></span>|  
|<span data-ttu-id="29213-290">002</span><span class="sxs-lookup"><span data-stu-id="29213-290">002</span></span>|<span data-ttu-id="29213-291">不支援標準</span><span class="sxs-lookup"><span data-stu-id="29213-291">Standard not supported</span></span>|  
|<span data-ttu-id="29213-292">003</span><span class="sxs-lookup"><span data-stu-id="29213-292">003</span></span>|<span data-ttu-id="29213-293">不支援控制項版本</span><span class="sxs-lookup"><span data-stu-id="29213-293">Version of the Controls Not Supported</span></span>|  
|<span data-ttu-id="29213-294">004</span><span class="sxs-lookup"><span data-stu-id="29213-294">004</span></span>|<span data-ttu-id="29213-295">區段結束字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-295">Segment Terminator is Invalid</span></span>|  
|<span data-ttu-id="29213-296">005</span><span class="sxs-lookup"><span data-stu-id="29213-296">005</span></span>|<span data-ttu-id="29213-297">無效的傳送者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="29213-297">Invalid Interchange ID Qualifier for Sender</span></span>|  
|<span data-ttu-id="29213-298">006</span><span class="sxs-lookup"><span data-stu-id="29213-298">006</span></span>|<span data-ttu-id="29213-299">無效的交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-299">Invalid Interchange Sender ID</span></span>|  
|<span data-ttu-id="29213-300">007</span><span class="sxs-lookup"><span data-stu-id="29213-300">007</span></span>|<span data-ttu-id="29213-301">無效的接收者交換識別碼辨識符號</span><span class="sxs-lookup"><span data-stu-id="29213-301">Invalid Interchange ID Qualifier for Receiver</span></span>|  
|<span data-ttu-id="29213-302">008</span><span class="sxs-lookup"><span data-stu-id="29213-302">008</span></span>|<span data-ttu-id="29213-303">無效的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-303">Invalid Interchange Receiver ID</span></span>|  
|<span data-ttu-id="29213-304">009</span><span class="sxs-lookup"><span data-stu-id="29213-304">009</span></span>|<span data-ttu-id="29213-305">未知的交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-305">Unknown Interchange Receiver ID</span></span>|  
|<span data-ttu-id="29213-306">010</span><span class="sxs-lookup"><span data-stu-id="29213-306">010</span></span>|<span data-ttu-id="29213-307">無效的授權資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="29213-307">Invalid Authorization Information Qualifier Value</span></span>|  
|<span data-ttu-id="29213-308">011</span><span class="sxs-lookup"><span data-stu-id="29213-308">011</span></span>|<span data-ttu-id="29213-309">無效的授權資訊值</span><span class="sxs-lookup"><span data-stu-id="29213-309">Invalid Authorization Information Value</span></span>|  
|<span data-ttu-id="29213-310">012</span><span class="sxs-lookup"><span data-stu-id="29213-310">012</span></span>|<span data-ttu-id="29213-311">無效的安全性資訊辨識符號值</span><span class="sxs-lookup"><span data-stu-id="29213-311">Invalid Security Information Qualifier Value</span></span>|  
|<span data-ttu-id="29213-312">013</span><span class="sxs-lookup"><span data-stu-id="29213-312">013</span></span>|<span data-ttu-id="29213-313">無效的安全性資訊值</span><span class="sxs-lookup"><span data-stu-id="29213-313">Invalid Security Information Value</span></span>|  
|<span data-ttu-id="29213-314">014</span><span class="sxs-lookup"><span data-stu-id="29213-314">014</span></span>|<span data-ttu-id="29213-315">無效的交換日期值</span><span class="sxs-lookup"><span data-stu-id="29213-315">Invalid Interchange Date Value</span></span>|  
|<span data-ttu-id="29213-316">015</span><span class="sxs-lookup"><span data-stu-id="29213-316">015</span></span>|<span data-ttu-id="29213-317">無效的交換時間值</span><span class="sxs-lookup"><span data-stu-id="29213-317">Invalid Interchange Time Value</span></span>|  
|<span data-ttu-id="29213-318">016</span><span class="sxs-lookup"><span data-stu-id="29213-318">016</span></span>|<span data-ttu-id="29213-319">無效的交換標準識別碼值</span><span class="sxs-lookup"><span data-stu-id="29213-319">Invalid Interchange Standards Identifier Value</span></span>|  
|<span data-ttu-id="29213-320">017</span><span class="sxs-lookup"><span data-stu-id="29213-320">017</span></span>|<span data-ttu-id="29213-321">無效的交換版本識別碼值</span><span class="sxs-lookup"><span data-stu-id="29213-321">Invalid Interchange Version ID Value</span></span>|  
|<span data-ttu-id="29213-322">018</span><span class="sxs-lookup"><span data-stu-id="29213-322">018</span></span>|<span data-ttu-id="29213-323">無效的交換控制編號值</span><span class="sxs-lookup"><span data-stu-id="29213-323">Invalid Interchange Control Number Value</span></span>|  
|<span data-ttu-id="29213-324">019</span><span class="sxs-lookup"><span data-stu-id="29213-324">019</span></span>|<span data-ttu-id="29213-325">無效的通知要求值</span><span class="sxs-lookup"><span data-stu-id="29213-325">Invalid Acknowledgment Requested Value</span></span>|  
|<span data-ttu-id="29213-326">020</span><span class="sxs-lookup"><span data-stu-id="29213-326">020</span></span>|<span data-ttu-id="29213-327">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="29213-327">Invalid Test Indicator Value</span></span>|  
|<span data-ttu-id="29213-328">021</span><span class="sxs-lookup"><span data-stu-id="29213-328">021</span></span>|<span data-ttu-id="29213-329">無效之包括的群組數目值</span><span class="sxs-lookup"><span data-stu-id="29213-329">Invalid Number of Included Groups Value</span></span>|  
|<span data-ttu-id="29213-330">022</span><span class="sxs-lookup"><span data-stu-id="29213-330">022</span></span>|<span data-ttu-id="29213-331">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="29213-331">Invalid Control Structure</span></span>|  
|<span data-ttu-id="29213-332">023</span><span class="sxs-lookup"><span data-stu-id="29213-332">023</span></span>|<span data-ttu-id="29213-333">不適當的檔案結尾</span><span class="sxs-lookup"><span data-stu-id="29213-333">Improper End-of-File</span></span>|  
|<span data-ttu-id="29213-334">024</span><span class="sxs-lookup"><span data-stu-id="29213-334">024</span></span>|<span data-ttu-id="29213-335">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="29213-335">Invalid Interchange Content</span></span>|  
|<span data-ttu-id="29213-336">025</span><span class="sxs-lookup"><span data-stu-id="29213-336">025</span></span>|<span data-ttu-id="29213-337">重複的交換控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-337">Duplicate Interchange Control Number</span></span>|  
|<span data-ttu-id="29213-338">026</span><span class="sxs-lookup"><span data-stu-id="29213-338">026</span></span>|<span data-ttu-id="29213-339">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-339">Invalid Data Element Separator</span></span>|  
|<span data-ttu-id="29213-340">027</span><span class="sxs-lookup"><span data-stu-id="29213-340">027</span></span>|<span data-ttu-id="29213-341">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-341">Invalid Component Element Separator</span></span>|  
|<span data-ttu-id="29213-342">028</span><span class="sxs-lookup"><span data-stu-id="29213-342">028</span></span>|<span data-ttu-id="29213-343">延遲傳遞要求中無效的傳遞日期</span><span class="sxs-lookup"><span data-stu-id="29213-343">Invalid Delivery Date in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="29213-344">029</span><span class="sxs-lookup"><span data-stu-id="29213-344">029</span></span>|<span data-ttu-id="29213-345">延遲傳遞要求中無效的傳遞時間</span><span class="sxs-lookup"><span data-stu-id="29213-345">Invalid Delivery Time in Deferred Delivery Request</span></span>|  
|<span data-ttu-id="29213-346">030</span><span class="sxs-lookup"><span data-stu-id="29213-346">030</span></span>|<span data-ttu-id="29213-347">延遲的傳遞要求中無效的傳遞時間碼</span><span class="sxs-lookup"><span data-stu-id="29213-347">Invalid Delivery Time Code in Deferred Delivery  Request</span></span>|  
|<span data-ttu-id="29213-348">031</span><span class="sxs-lookup"><span data-stu-id="29213-348">031</span></span>|<span data-ttu-id="29213-349">無效的服務等級</span><span class="sxs-lookup"><span data-stu-id="29213-349">Invalid Grade of Service</span></span>|  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outbound-interchanges"></a><span data-ttu-id="29213-350">由接收管線針對回應輸出交換而接收之每個功能通知所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="29213-350">Data Stored by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outbound Interchanges</span></span>  
 <span data-ttu-id="29213-351">接收管線會在狀態報告資料存放區中，針對其所接收的每個功能通知建立記錄。</span><span class="sxs-lookup"><span data-stu-id="29213-351">The receive pipeline creates a record in the status report data store for each functional acknowledgment that it receives.</span></span>  <span data-ttu-id="29213-352">X12 類型的技術通知是 997，EDIFACT 類型的技術通知為完整的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="29213-352">The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT.</span></span> <span data-ttu-id="29213-353">會為每個群組建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="29213-353">One entry per group will to be created.</span></span> <span data-ttu-id="29213-354">進行這項輸入時會使用交換和群組標頭內的資料。</span><span class="sxs-lookup"><span data-stu-id="29213-354">Data from the interchange and group headers is used while making this entry.</span></span> <span data-ttu-id="29213-355">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="29213-355">The data stored includes:</span></span>  
  
-   <span data-ttu-id="29213-356">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="29213-356">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="29213-357">功能通知方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="29213-357">Functional ACK Direction = Send</span></span>  
  
-   <span data-ttu-id="29213-358">功能通知狀態 =\<產生或不適用，請參閱附註 1\></span><span class="sxs-lookup"><span data-stu-id="29213-358">Functional ACK Status = \<Generated or Not Applicable, refer note 1\></span></span>  
  
-   <span data-ttu-id="29213-359">交換接收者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-359">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-360">交換傳送者 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-360">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-361">交換日期 = 更新資料 (X12 相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-361">Interchange Date = Update Data (required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="29213-362">交換控制識別碼 = 更新資料 (相互關聯的必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-362">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="29213-363">群組控制編號 = 更新資料 (「對於 EDIFACT 是選擇項」，對於 X12 相互關聯是必要項)</span><span class="sxs-lookup"><span data-stu-id="29213-363">Group Control Number = Update Data (‘optional for EDIFACT’ and required for X12 correlation)</span></span>  
  
-   <span data-ttu-id="29213-364">功能識別代碼 = 更新資料 (GS01/UNG01)</span><span class="sxs-lookup"><span data-stu-id="29213-364">Functional ID Code = Update Data (GS01/UNG01)</span></span>  
  
-   <span data-ttu-id="29213-365">交易集的計數 = 更新資料 (UNE1/UNZ1)</span><span class="sxs-lookup"><span data-stu-id="29213-365">Count of Transaction Sets = Update Data (UNE1/UNZ1)</span></span>  
  
-   <span data-ttu-id="29213-366">功能通知交換控制識別碼= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-366">Functional ACK Interchange Control ID= Not value – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-367">功能通知交換日期= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-367">Functional ACK Interchange Date = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-368">功能通知交換時間= 未指定值 – 會由傳送端套用</span><span class="sxs-lookup"><span data-stu-id="29213-368">Functional ACK Interchange Time = Not valued – will be applied by send side</span></span>  
  
-   <span data-ttu-id="29213-369">已接收交易集的計數 = 更新資料 (X12-AK903，由 EDIFACT 編碼的引擎計算)</span><span class="sxs-lookup"><span data-stu-id="29213-369">Count of Transaction Sets Received = Update Data (X12-AK903 and computed by Engine for EDIFACT encoding)</span></span>  
  
-   <span data-ttu-id="29213-370">已接受交易集的計數 = 更新資料 (X12-AK904，由 EDIFACT 編碼的引擎計算)</span><span class="sxs-lookup"><span data-stu-id="29213-370">Count of Transaction Sets Accepted = Update Data (X12-AK904 and computed by Engine for EDIFACT engine)</span></span>  
  
-   <span data-ttu-id="29213-371">通知/動作代碼 = 更新資料\<附註 2，請參閱\>（從 X12 AK901 或 edifact-uci4） \*</span><span class="sxs-lookup"><span data-stu-id="29213-371">ACK/Action Code = Update Data  \<refer note 2\> (from X12-AK901 or EDIFACT-UCI4)\*</span></span>  
  
-   <span data-ttu-id="29213-372">錯誤/語法錯誤碼 = 更新資料 (X12-AK905、EDIFACT UCI5) 說明 3</span><span class="sxs-lookup"><span data-stu-id="29213-372">Error/Syntax Error Code  = Update Data (X12-AK905, EDIFACT UCI5) Note 3</span></span>  
  
-   <span data-ttu-id="29213-373">其他 X12 通知錯誤碼 2 = 更新資料 (X12-AK906)</span><span class="sxs-lookup"><span data-stu-id="29213-373">Additional X12 ACK Error Code 2 = Update Data (X12-AK906)</span></span>  
  
-   <span data-ttu-id="29213-374">其他 X12 通知錯誤碼 3 = 更新資料 (X12-AK907)</span><span class="sxs-lookup"><span data-stu-id="29213-374">Additional X12 ACK Error Code 3 = Update Data (X12-AK907)</span></span>  
  
-   <span data-ttu-id="29213-375">其他 X12 通知錯誤碼 4 = 更新資料 (X12-AK908)</span><span class="sxs-lookup"><span data-stu-id="29213-375">Additional X12 ACK Error Code 4 = Update Data (X12-AK908)</span></span>  
  
-   <span data-ttu-id="29213-376">其他 X12 通知錯誤碼 5 = 更新資料 (X12-AK909)</span><span class="sxs-lookup"><span data-stu-id="29213-376">Additional X12 ACK Error Code 5 = Update Data (X12-AK909)</span></span>  
  
 <span data-ttu-id="29213-377">將使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-377">The following ACK/Action Codes will be used:</span></span>  
  
|<span data-ttu-id="29213-378">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-378">Data in ACK/Action Code</span></span>|<span data-ttu-id="29213-379">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-379">Error description for Reporting</span></span>|<span data-ttu-id="29213-380">註解 (適用性)</span><span class="sxs-lookup"><span data-stu-id="29213-380">Comment (applicability)</span></span>|  
|------------------------------|-------------------------------------|-------------------------------|  
|<span data-ttu-id="29213-381">A</span><span class="sxs-lookup"><span data-stu-id="29213-381">A</span></span>|<span data-ttu-id="29213-382">已接受</span><span class="sxs-lookup"><span data-stu-id="29213-382">Accepted</span></span>|<span data-ttu-id="29213-383">X12</span><span class="sxs-lookup"><span data-stu-id="29213-383">X12</span></span>|  
|<span data-ttu-id="29213-384">E</span><span class="sxs-lookup"><span data-stu-id="29213-384">E</span></span>|<span data-ttu-id="29213-385">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-385">Accepted  with errors</span></span>|<span data-ttu-id="29213-386">X12</span><span class="sxs-lookup"><span data-stu-id="29213-386">X12</span></span>|  
|<span data-ttu-id="29213-387">P</span><span class="sxs-lookup"><span data-stu-id="29213-387">P</span></span>|<span data-ttu-id="29213-388">已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-388">Partially Accepted</span></span>|<span data-ttu-id="29213-389">X12</span><span class="sxs-lookup"><span data-stu-id="29213-389">X12</span></span>|  
|<span data-ttu-id="29213-390">R</span><span class="sxs-lookup"><span data-stu-id="29213-390">R</span></span>|<span data-ttu-id="29213-391">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-391">Rejected</span></span>|<span data-ttu-id="29213-392">X12</span><span class="sxs-lookup"><span data-stu-id="29213-392">X12</span></span>|  
|<span data-ttu-id="29213-393">4</span><span class="sxs-lookup"><span data-stu-id="29213-393">4</span></span>|<span data-ttu-id="29213-394">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-394">Rejected</span></span>|<span data-ttu-id="29213-395">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-395">EDIFACT</span></span>|  
|<span data-ttu-id="29213-396">7</span><span class="sxs-lookup"><span data-stu-id="29213-396">7</span></span>|<span data-ttu-id="29213-397">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-397">Accepted/Partially Accepted</span></span>|<span data-ttu-id="29213-398">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-398">EDIFACT</span></span>|  
  
 <span data-ttu-id="29213-399">EDIFACT 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-399">The following Error/Syntax Error Codes will be used for EDIFACT:</span></span>  
  
|<span data-ttu-id="29213-400">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-400">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="29213-401">(適用於 EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="29213-401">(applicable to EDIFACT)</span></span>|<span data-ttu-id="29213-402">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-402">Error Description for reporting</span></span>|  
|--------------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="29213-403">2</span><span class="sxs-lookup"><span data-stu-id="29213-403">2</span></span>|<span data-ttu-id="29213-404">語法版本或層級不支援</span><span class="sxs-lookup"><span data-stu-id="29213-404">Syntax version or level not supported</span></span>|  
|<span data-ttu-id="29213-405">7</span><span class="sxs-lookup"><span data-stu-id="29213-405">7</span></span>|<span data-ttu-id="29213-406">交換收件者不是實際收件者</span><span class="sxs-lookup"><span data-stu-id="29213-406">Interchange recipient not actual recipient</span></span>|  
|<span data-ttu-id="29213-407">12</span><span class="sxs-lookup"><span data-stu-id="29213-407">12</span></span>|<span data-ttu-id="29213-408">無效值</span><span class="sxs-lookup"><span data-stu-id="29213-408">Invalid value</span></span>|  
|<span data-ttu-id="29213-409">13</span><span class="sxs-lookup"><span data-stu-id="29213-409">13</span></span>|<span data-ttu-id="29213-410">遺漏</span><span class="sxs-lookup"><span data-stu-id="29213-410">Missing</span></span>|  
|<span data-ttu-id="29213-411">14</span><span class="sxs-lookup"><span data-stu-id="29213-411">14</span></span>|<span data-ttu-id="29213-412">在這個位置中不支援的值</span><span class="sxs-lookup"><span data-stu-id="29213-412">Value not supported in this position</span></span>|  
|<span data-ttu-id="29213-413">15</span><span class="sxs-lookup"><span data-stu-id="29213-413">15</span></span>|<span data-ttu-id="29213-414">在這個位置中不支援</span><span class="sxs-lookup"><span data-stu-id="29213-414">Not supported in this position</span></span>|  
|<span data-ttu-id="29213-415">16</span><span class="sxs-lookup"><span data-stu-id="29213-415">16</span></span>|<span data-ttu-id="29213-416">太多結構成分</span><span class="sxs-lookup"><span data-stu-id="29213-416">Too many constituents</span></span>|  
|<span data-ttu-id="29213-417">17</span><span class="sxs-lookup"><span data-stu-id="29213-417">17</span></span>|<span data-ttu-id="29213-418">沒有協議</span><span class="sxs-lookup"><span data-stu-id="29213-418">No agreement</span></span>|  
|<span data-ttu-id="29213-419">18</span><span class="sxs-lookup"><span data-stu-id="29213-419">18</span></span>|<span data-ttu-id="29213-420">未指定的錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-420">Unspecified error</span></span>|  
|<span data-ttu-id="29213-421">19</span><span class="sxs-lookup"><span data-stu-id="29213-421">19</span></span>|<span data-ttu-id="29213-422">無效的小數點標記</span><span class="sxs-lookup"><span data-stu-id="29213-422">Invalid decimal notation</span></span>|  
|<span data-ttu-id="29213-423">20</span><span class="sxs-lookup"><span data-stu-id="29213-423">20</span></span>|<span data-ttu-id="29213-424">字元做為服務字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-424">Character invalid as service character</span></span>|  
|<span data-ttu-id="29213-425">21</span><span class="sxs-lookup"><span data-stu-id="29213-425">21</span></span>|<span data-ttu-id="29213-426">無效字元</span><span class="sxs-lookup"><span data-stu-id="29213-426">Invalid character(s)</span></span>|  
|<span data-ttu-id="29213-427">22</span><span class="sxs-lookup"><span data-stu-id="29213-427">22</span></span>|<span data-ttu-id="29213-428">服務字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-428">Invalid service character(s)</span></span>|  
|<span data-ttu-id="29213-429">23</span><span class="sxs-lookup"><span data-stu-id="29213-429">23</span></span>|<span data-ttu-id="29213-430">未知的交換傳送者</span><span class="sxs-lookup"><span data-stu-id="29213-430">Unknown Interchange sender</span></span>|  
|<span data-ttu-id="29213-431">24</span><span class="sxs-lookup"><span data-stu-id="29213-431">24</span></span>|<span data-ttu-id="29213-432">太舊</span><span class="sxs-lookup"><span data-stu-id="29213-432">Too old</span></span>|  
|<span data-ttu-id="29213-433">25</span><span class="sxs-lookup"><span data-stu-id="29213-433">25</span></span>|<span data-ttu-id="29213-434">不支援測試指示符號</span><span class="sxs-lookup"><span data-stu-id="29213-434">Test indicator not supported</span></span>|  
|<span data-ttu-id="29213-435">26</span><span class="sxs-lookup"><span data-stu-id="29213-435">26</span></span>|<span data-ttu-id="29213-436">偵測到重複</span><span class="sxs-lookup"><span data-stu-id="29213-436">Duplicate detected</span></span>|  
|<span data-ttu-id="29213-437">27</span><span class="sxs-lookup"><span data-stu-id="29213-437">27</span></span>|<span data-ttu-id="29213-438">不支援安全性函式</span><span class="sxs-lookup"><span data-stu-id="29213-438">Security function not supported</span></span>|  
|<span data-ttu-id="29213-439">28</span><span class="sxs-lookup"><span data-stu-id="29213-439">28</span></span>|<span data-ttu-id="29213-440">參考不相符</span><span class="sxs-lookup"><span data-stu-id="29213-440">References do not match</span></span>|  
|<span data-ttu-id="29213-441">29</span><span class="sxs-lookup"><span data-stu-id="29213-441">29</span></span>|<span data-ttu-id="29213-442">控制計數不符合接收到的執行個體數目</span><span class="sxs-lookup"><span data-stu-id="29213-442">Control count does not match number of instances received</span></span>|  
|<span data-ttu-id="29213-443">30</span><span class="sxs-lookup"><span data-stu-id="29213-443">30</span></span>|<span data-ttu-id="29213-444">群組和訊息/封裝已混合</span><span class="sxs-lookup"><span data-stu-id="29213-444">Groups and messages/packages mixed</span></span>|  
|<span data-ttu-id="29213-445">31</span><span class="sxs-lookup"><span data-stu-id="29213-445">31</span></span>|<span data-ttu-id="29213-446">群組中有一種以上的訊息類型</span><span class="sxs-lookup"><span data-stu-id="29213-446">More than one message type in group</span></span>|  
|<span data-ttu-id="29213-447">32</span><span class="sxs-lookup"><span data-stu-id="29213-447">32</span></span>|<span data-ttu-id="29213-448">較低層級空白</span><span class="sxs-lookup"><span data-stu-id="29213-448">Lower level empty</span></span>|  
|<span data-ttu-id="29213-449">33</span><span class="sxs-lookup"><span data-stu-id="29213-449">33</span></span>|<span data-ttu-id="29213-450">在訊息、封裝或群組外部出現的項目無效</span><span class="sxs-lookup"><span data-stu-id="29213-450">Invalid occurrence outside message, package, or group</span></span>|  
|<span data-ttu-id="29213-451">34</span><span class="sxs-lookup"><span data-stu-id="29213-451">34</span></span>|<span data-ttu-id="29213-452">不允許巢狀指示符號</span><span class="sxs-lookup"><span data-stu-id="29213-452">Nesting indicator not allowed</span></span>|  
|<span data-ttu-id="29213-453">35</span><span class="sxs-lookup"><span data-stu-id="29213-453">35</span></span>|<span data-ttu-id="29213-454">太多資料元素或區段重複</span><span class="sxs-lookup"><span data-stu-id="29213-454">Too many data element or segment repetitions</span></span>|  
|<span data-ttu-id="29213-455">36</span><span class="sxs-lookup"><span data-stu-id="29213-455">36</span></span>|<span data-ttu-id="29213-456">太多區段群組重複</span><span class="sxs-lookup"><span data-stu-id="29213-456">Too many segment group repetitions</span></span>|  
|<span data-ttu-id="29213-457">37</span><span class="sxs-lookup"><span data-stu-id="29213-457">37</span></span>|<span data-ttu-id="29213-458">無效字元類型</span><span class="sxs-lookup"><span data-stu-id="29213-458">Invalid type of character(s)</span></span>|  
|<span data-ttu-id="29213-459">38</span><span class="sxs-lookup"><span data-stu-id="29213-459">38</span></span>|<span data-ttu-id="29213-460">在小數符號之前遺失數字</span><span class="sxs-lookup"><span data-stu-id="29213-460">Missing digit in front of decimal sign</span></span>|  
|<span data-ttu-id="29213-461">39</span><span class="sxs-lookup"><span data-stu-id="29213-461">39</span></span>|<span data-ttu-id="29213-462">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="29213-462">Data element too long</span></span>|  
|<span data-ttu-id="29213-463">40</span><span class="sxs-lookup"><span data-stu-id="29213-463">40</span></span>|<span data-ttu-id="29213-464">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="29213-464">Data element too short</span></span>|  
|<span data-ttu-id="29213-465">41</span><span class="sxs-lookup"><span data-stu-id="29213-465">41</span></span>|<span data-ttu-id="29213-466">永久通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-466">Permanent communication network error</span></span>|  
|<span data-ttu-id="29213-467">42</span><span class="sxs-lookup"><span data-stu-id="29213-467">42</span></span>|<span data-ttu-id="29213-468">暫時通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-468">Temporary communication network error</span></span>|  
|<span data-ttu-id="29213-469">43</span><span class="sxs-lookup"><span data-stu-id="29213-469">43</span></span>|<span data-ttu-id="29213-470">未知的交換收件者</span><span class="sxs-lookup"><span data-stu-id="29213-470">Unknown interchange recipient</span></span>|  
|<span data-ttu-id="29213-471">45</span><span class="sxs-lookup"><span data-stu-id="29213-471">45</span></span>|<span data-ttu-id="29213-472">尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-472">Trailing separator</span></span>|  
|<span data-ttu-id="29213-473">46</span><span class="sxs-lookup"><span data-stu-id="29213-473">46</span></span>|<span data-ttu-id="29213-474">不支援字元集</span><span class="sxs-lookup"><span data-stu-id="29213-474">Character set not supported</span></span>|  
|<span data-ttu-id="29213-475">47</span><span class="sxs-lookup"><span data-stu-id="29213-475">47</span></span>|<span data-ttu-id="29213-476">不支援信封功能</span><span class="sxs-lookup"><span data-stu-id="29213-476">Envelope functionality not supported</span></span>|  
|<span data-ttu-id="29213-477">48</span><span class="sxs-lookup"><span data-stu-id="29213-477">48</span></span>|<span data-ttu-id="29213-478">違反相依性條件</span><span class="sxs-lookup"><span data-stu-id="29213-478">Dependency condition violated</span></span>|  
|<span data-ttu-id="29213-479">70</span><span class="sxs-lookup"><span data-stu-id="29213-479">70</span></span>|<span data-ttu-id="29213-480">交易集遺失或是交易集識別碼無效</span><span class="sxs-lookup"><span data-stu-id="29213-480">Transaction set is missing or invalid transaction set Identifier</span></span>|  
|<span data-ttu-id="29213-481">71</span><span class="sxs-lookup"><span data-stu-id="29213-481">71</span></span>|<span data-ttu-id="29213-482">設定或群組控制編號不相符的交易</span><span class="sxs-lookup"><span data-stu-id="29213-482">Transaction set or group control number mismatch</span></span>|  
|<span data-ttu-id="29213-483">72</span><span class="sxs-lookup"><span data-stu-id="29213-483">72</span></span>|<span data-ttu-id="29213-484">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-484">Unrecognized segment ID</span></span>|  
|<span data-ttu-id="29213-485">73</span><span class="sxs-lookup"><span data-stu-id="29213-485">73</span></span>|<span data-ttu-id="29213-486">XML 不在正確的位置</span><span class="sxs-lookup"><span data-stu-id="29213-486">XML not at correct position</span></span>|  
|<span data-ttu-id="29213-487">74</span><span class="sxs-lookup"><span data-stu-id="29213-487">74</span></span>|<span data-ttu-id="29213-488">區段群組的重複太少</span><span class="sxs-lookup"><span data-stu-id="29213-488">Too few segment group repetitions</span></span>|  
|<span data-ttu-id="29213-489">75</span><span class="sxs-lookup"><span data-stu-id="29213-489">75</span></span>|<span data-ttu-id="29213-490">區段的重複太少</span><span class="sxs-lookup"><span data-stu-id="29213-490">Too few segment repetitions</span></span>|  
|<span data-ttu-id="29213-491">76</span><span class="sxs-lookup"><span data-stu-id="29213-491">76</span></span>|<span data-ttu-id="29213-492">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="29213-492">Too few data elements found</span></span>|  
  
 <span data-ttu-id="29213-493">X12 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-493">The following Error/Syntax Error Codes will be used for X12:</span></span>  
  
|<span data-ttu-id="29213-494">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-494">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="29213-495">(適用於 X12)</span><span class="sxs-lookup"><span data-stu-id="29213-495">(applicable to X12)</span></span>|<span data-ttu-id="29213-496">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-496">Error Description for reporting</span></span>|  
|----------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="29213-497">1</span><span class="sxs-lookup"><span data-stu-id="29213-497">1</span></span>|<span data-ttu-id="29213-498">不支援功能群組</span><span class="sxs-lookup"><span data-stu-id="29213-498">Functional group not supported</span></span>|  
|<span data-ttu-id="29213-499">2</span><span class="sxs-lookup"><span data-stu-id="29213-499">2</span></span>|<span data-ttu-id="29213-500">不支援功能群組版本</span><span class="sxs-lookup"><span data-stu-id="29213-500">Functional group version not supported</span></span>|  
|<span data-ttu-id="29213-501">3</span><span class="sxs-lookup"><span data-stu-id="29213-501">3</span></span>|<span data-ttu-id="29213-502">遺失功能群組結尾</span><span class="sxs-lookup"><span data-stu-id="29213-502">Functional group trailer missing</span></span>|  
|<span data-ttu-id="29213-503">4</span><span class="sxs-lookup"><span data-stu-id="29213-503">4</span></span>|<span data-ttu-id="29213-504">功能群組標頭與結尾中的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="29213-504">Group control number in the functional group header and trailer do not agree</span></span>|  
|<span data-ttu-id="29213-505">5</span><span class="sxs-lookup"><span data-stu-id="29213-505">5</span></span>|<span data-ttu-id="29213-506">包含的交易集數目不符合實際計數</span><span class="sxs-lookup"><span data-stu-id="29213-506">Number of included transaction sets does not match actual count</span></span>|  
|<span data-ttu-id="29213-507">6-26</span><span class="sxs-lookup"><span data-stu-id="29213-507">6-26</span></span>|<span data-ttu-id="29213-508">其他不支援的驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-508">Other unsupported validation errors</span></span>|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outgoing-interchanges"></a><span data-ttu-id="29213-509">由接收管線針對回應外寄交換而接收之每個功能通知所更新的資料</span><span class="sxs-lookup"><span data-stu-id="29213-509">Data Updated by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outgoing Interchanges</span></span>  
 <span data-ttu-id="29213-510">對於接收管線所接收的每個功能通知，接收管線會更新相互關聯之傳送交換的狀態報告項目。</span><span class="sxs-lookup"><span data-stu-id="29213-510">For each functional acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.</span></span>  
  
 <span data-ttu-id="29213-511">「EDI 解譯器」會使用內送通知中交換和群組標頭區段內的資料，找出資料存放區中的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29213-511">The EDI Disassembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="29213-512">通知中的欄位</span><span class="sxs-lookup"><span data-stu-id="29213-512">Fields in ACK</span></span>|<span data-ttu-id="29213-513">資料存放區中的欄位</span><span class="sxs-lookup"><span data-stu-id="29213-513">Fields in Data store</span></span>|<span data-ttu-id="29213-514">註解</span><span class="sxs-lookup"><span data-stu-id="29213-514">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="29213-515">交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-515">Interchange Sender ID</span></span>|<span data-ttu-id="29213-516">交換接收方</span><span class="sxs-lookup"><span data-stu-id="29213-516">Interchange Receiver</span></span>|<span data-ttu-id="29213-517">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-517">Applicable to both X12 and EDIFACT</span></span>|  
|<span data-ttu-id="29213-518">交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-518">Interchange Receiver ID</span></span>|<span data-ttu-id="29213-519">交換寄件者</span><span class="sxs-lookup"><span data-stu-id="29213-519">Interchange Sender</span></span>|<span data-ttu-id="29213-520">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-520">Applicable to both X12 and EDIFACT</span></span>|  
|-|<span data-ttu-id="29213-521">交換日期</span><span class="sxs-lookup"><span data-stu-id="29213-521">Interchange Date</span></span>|-|  
|<span data-ttu-id="29213-522">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-522">Interchange Control Number</span></span>|<span data-ttu-id="29213-523">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-523">Interchange Control ID</span></span>|<span data-ttu-id="29213-524">僅適用於 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-524">Applicable only to EDIFACT</span></span>|  
|<span data-ttu-id="29213-525">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-525">Group Control Number</span></span>|<span data-ttu-id="29213-526">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="29213-526">Group Control Number</span></span>|<span data-ttu-id="29213-527">僅適用於 X12</span><span class="sxs-lookup"><span data-stu-id="29213-527">Applicable only to X12</span></span>|  
|-|<span data-ttu-id="29213-528">交換方向 = 傳送</span><span class="sxs-lookup"><span data-stu-id="29213-528">Interchange Direction = Send</span></span>|<span data-ttu-id="29213-529">為確保唯一性，在 BIBO 實例中是必要項</span><span class="sxs-lookup"><span data-stu-id="29213-529">Required since in BIBO Scenario for uniqueness</span></span>|  
|<span data-ttu-id="29213-530">記錄類型</span><span class="sxs-lookup"><span data-stu-id="29213-530">Record Type</span></span>|<span data-ttu-id="29213-531">功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="29213-531">Functional ACK Status</span></span>|<span data-ttu-id="29213-532">適用於 X12 與 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-532">Applicable to both X12 and EDIFACT</span></span>|  
  
 <span data-ttu-id="29213-533">儲存的資料包括：</span><span class="sxs-lookup"><span data-stu-id="29213-533">The data stored includes:</span></span>  
  
-   <span data-ttu-id="29213-534">記錄類型 = 功能通知狀態</span><span class="sxs-lookup"><span data-stu-id="29213-534">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="29213-535">功能通知方向 = 接收</span><span class="sxs-lookup"><span data-stu-id="29213-535">Functional ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="29213-536">功能通知狀態 =更新資料為已接收</span><span class="sxs-lookup"><span data-stu-id="29213-536">Functional ACK Status =Update Data as Received</span></span>  
  
-   <span data-ttu-id="29213-537">交換接收者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-537">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-538">交換傳送者 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-538">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-539">交換日期 = 現有日期</span><span class="sxs-lookup"><span data-stu-id="29213-539">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-540">交換控制識別碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-540">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-541">群組控制編號 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-541">Group Control Number = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-542">功能識別代碼 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-542">Functional ID Code = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-543">交易集的計數 = 現有資料</span><span class="sxs-lookup"><span data-stu-id="29213-543">Count of Transaction Sets = Existing Data</span></span>  
  
-   <span data-ttu-id="29213-544">功能通知交換控制識別碼 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-544">Functional ACK Interchange Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="29213-545">功能通知交換日期 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-545">Functional ACK Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="29213-546">功能通知交換時間 = 更新資料</span><span class="sxs-lookup"><span data-stu-id="29213-546">Functional ACK Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="29213-547">已傳送交易集的計數 = 更新資料 (X12 AK903，EDIFACT 不適用)</span><span class="sxs-lookup"><span data-stu-id="29213-547">Count of Transaction Sets Delivered = Update Data (X12 AK903 and not applicable for EDIFACT)</span></span>  
  
-   <span data-ttu-id="29213-548">已接受的交易集計數 = 更新資料 (X12 AK904，EDIFACT 不適用)</span><span class="sxs-lookup"><span data-stu-id="29213-548">Count of Transaction Sets Accepted = Update Data (X12 AK904 and not applicable for EDIFACT)</span></span>  
  
-   <span data-ttu-id="29213-549">通知/動作代碼 = 更新資料 (X12 AK901 和 UCI4) 參閱說明 1</span><span class="sxs-lookup"><span data-stu-id="29213-549">ACK/Action Code = Update Data (X12 AK901 and UCI4) Refer Note 1</span></span>  
  
-   <span data-ttu-id="29213-550">錯誤/語法錯誤碼  = (X12 AK905 和 UCI5) 參閱說明 2</span><span class="sxs-lookup"><span data-stu-id="29213-550">Error/Syntax Error Code  = (X12 AK905 and UCI5) Refer Note 2</span></span>  
  
-   <span data-ttu-id="29213-551">其他 X12 通知錯誤碼 2 = 更新資料 (X12-AK906)</span><span class="sxs-lookup"><span data-stu-id="29213-551">Additional X12 ACK Error Code 2 = Update Data (X12-AK906)</span></span>  
  
-   <span data-ttu-id="29213-552">其他 X12 通知錯誤碼 3 = 更新資料 (X12-AK907)</span><span class="sxs-lookup"><span data-stu-id="29213-552">Additional X12 ACK Error Code 3 = Update Data (X12-AK907)</span></span>  
  
-   <span data-ttu-id="29213-553">其他 X12 通知錯誤碼 4 = 更新資料 (X12-AK908)</span><span class="sxs-lookup"><span data-stu-id="29213-553">Additional X12 ACK Error Code 4 = Update Data (X12-AK908)</span></span>  
  
-   <span data-ttu-id="29213-554">其他 X12 通知錯誤碼 5 = 更新資料 (X12-AK909)</span><span class="sxs-lookup"><span data-stu-id="29213-554">Additional X12 ACK Error Code 5 = Update Data (X12-AK909)</span></span>  
  
 <span data-ttu-id="29213-555">將使用的通知/動作代碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-555">The following ACK/Action Codes will be used:</span></span>  
  
|<span data-ttu-id="29213-556">通知/動作代碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-556">Data in ACK/Action Code</span></span>|<span data-ttu-id="29213-557">針對狀態報告對應</span><span class="sxs-lookup"><span data-stu-id="29213-557">Mapped for Status Reporting</span></span>|<span data-ttu-id="29213-558">註解</span><span class="sxs-lookup"><span data-stu-id="29213-558">Comment</span></span>|  
|------------------------------|---------------------------------|-------------|  
|<span data-ttu-id="29213-559">A</span><span class="sxs-lookup"><span data-stu-id="29213-559">A</span></span>|<span data-ttu-id="29213-560">已接受</span><span class="sxs-lookup"><span data-stu-id="29213-560">Accepted</span></span>|<span data-ttu-id="29213-561">X12</span><span class="sxs-lookup"><span data-stu-id="29213-561">X12</span></span>|  
|<span data-ttu-id="29213-562">P</span><span class="sxs-lookup"><span data-stu-id="29213-562">P</span></span>|<span data-ttu-id="29213-563">已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-563">Partially Accepted</span></span>|<span data-ttu-id="29213-564">X12</span><span class="sxs-lookup"><span data-stu-id="29213-564">X12</span></span>|  
|<span data-ttu-id="29213-565">R、M、W、X</span><span class="sxs-lookup"><span data-stu-id="29213-565">R, M, W, X</span></span>|<span data-ttu-id="29213-566">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-566">Rejected</span></span>|<span data-ttu-id="29213-567">X12</span><span class="sxs-lookup"><span data-stu-id="29213-567">X12</span></span>|  
|<span data-ttu-id="29213-568">E</span><span class="sxs-lookup"><span data-stu-id="29213-568">E</span></span>|<span data-ttu-id="29213-569">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-569">Accepted with errors</span></span>|<span data-ttu-id="29213-570">X12</span><span class="sxs-lookup"><span data-stu-id="29213-570">X12</span></span>|  
|<span data-ttu-id="29213-571">4</span><span class="sxs-lookup"><span data-stu-id="29213-571">4</span></span>|<span data-ttu-id="29213-572">已拒絕</span><span class="sxs-lookup"><span data-stu-id="29213-572">Rejected</span></span>|<span data-ttu-id="29213-573">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-573">EDIFACT</span></span>|  
|<span data-ttu-id="29213-574">7, 8</span><span class="sxs-lookup"><span data-stu-id="29213-574">7, 8</span></span>|<span data-ttu-id="29213-575">已接受/已部分接受</span><span class="sxs-lookup"><span data-stu-id="29213-575">Accepted/Partially Accepted</span></span>|<span data-ttu-id="29213-576">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="29213-576">EDIFACT</span></span>|  
  
 <span data-ttu-id="29213-577">EDIFACT 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-577">The following Error/Syntax Error Codes will be used for EDIFACT:</span></span>  
  
|<span data-ttu-id="29213-578">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-578">Data in Error/Syntax Error Cod</span></span><br /><br /> <span data-ttu-id="29213-579">(適用於 EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="29213-579">(applicable to EDIFACT)</span></span>|<span data-ttu-id="29213-580">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-580">Error Description for reporting</span></span>|  
|-------------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="29213-581">2</span><span class="sxs-lookup"><span data-stu-id="29213-581">2</span></span>|<span data-ttu-id="29213-582">語法版本或層級不支援</span><span class="sxs-lookup"><span data-stu-id="29213-582">Syntax version or level not supported</span></span>|  
|<span data-ttu-id="29213-583">7</span><span class="sxs-lookup"><span data-stu-id="29213-583">7</span></span>|<span data-ttu-id="29213-584">交換收件者不是實際收件者</span><span class="sxs-lookup"><span data-stu-id="29213-584">Interchange recipient not actual recipient</span></span>|  
|<span data-ttu-id="29213-585">12</span><span class="sxs-lookup"><span data-stu-id="29213-585">12</span></span>|<span data-ttu-id="29213-586">無效值</span><span class="sxs-lookup"><span data-stu-id="29213-586">Invalid value</span></span>|  
|<span data-ttu-id="29213-587">13</span><span class="sxs-lookup"><span data-stu-id="29213-587">13</span></span>|<span data-ttu-id="29213-588">遺漏</span><span class="sxs-lookup"><span data-stu-id="29213-588">Missing</span></span>|  
|<span data-ttu-id="29213-589">14</span><span class="sxs-lookup"><span data-stu-id="29213-589">14</span></span>|<span data-ttu-id="29213-590">在這個位置中不支援的值</span><span class="sxs-lookup"><span data-stu-id="29213-590">Value not supported in this position</span></span>|  
|<span data-ttu-id="29213-591">15</span><span class="sxs-lookup"><span data-stu-id="29213-591">15</span></span>|<span data-ttu-id="29213-592">在這個位置中不支援</span><span class="sxs-lookup"><span data-stu-id="29213-592">Not supported in this position</span></span>|  
|<span data-ttu-id="29213-593">16</span><span class="sxs-lookup"><span data-stu-id="29213-593">16</span></span>|<span data-ttu-id="29213-594">太多結構成分</span><span class="sxs-lookup"><span data-stu-id="29213-594">Too many constituents</span></span>|  
|<span data-ttu-id="29213-595">17</span><span class="sxs-lookup"><span data-stu-id="29213-595">17</span></span>|<span data-ttu-id="29213-596">沒有協議</span><span class="sxs-lookup"><span data-stu-id="29213-596">No agreement</span></span>|  
|<span data-ttu-id="29213-597">18</span><span class="sxs-lookup"><span data-stu-id="29213-597">18</span></span>|<span data-ttu-id="29213-598">未指定的錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-598">Unspecified error</span></span>|  
|<span data-ttu-id="29213-599">19</span><span class="sxs-lookup"><span data-stu-id="29213-599">19</span></span>|<span data-ttu-id="29213-600">無效的小數點標記</span><span class="sxs-lookup"><span data-stu-id="29213-600">Invalid decimal notation</span></span>|  
|<span data-ttu-id="29213-601">20</span><span class="sxs-lookup"><span data-stu-id="29213-601">20</span></span>|<span data-ttu-id="29213-602">字元做為服務字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-602">Character invalid as service character</span></span>|  
|<span data-ttu-id="29213-603">21</span><span class="sxs-lookup"><span data-stu-id="29213-603">21</span></span>|<span data-ttu-id="29213-604">無效字元</span><span class="sxs-lookup"><span data-stu-id="29213-604">Invalid character(s)</span></span>|  
|<span data-ttu-id="29213-605">22</span><span class="sxs-lookup"><span data-stu-id="29213-605">22</span></span>|<span data-ttu-id="29213-606">服務字元無效</span><span class="sxs-lookup"><span data-stu-id="29213-606">Invalid service character(s)</span></span>|  
|<span data-ttu-id="29213-607">23</span><span class="sxs-lookup"><span data-stu-id="29213-607">23</span></span>|<span data-ttu-id="29213-608">未知的交換傳送者</span><span class="sxs-lookup"><span data-stu-id="29213-608">Unknown Interchange sender</span></span>|  
|<span data-ttu-id="29213-609">24</span><span class="sxs-lookup"><span data-stu-id="29213-609">24</span></span>|<span data-ttu-id="29213-610">太舊</span><span class="sxs-lookup"><span data-stu-id="29213-610">Too old</span></span>|  
|<span data-ttu-id="29213-611">25</span><span class="sxs-lookup"><span data-stu-id="29213-611">25</span></span>|<span data-ttu-id="29213-612">不支援測試指示符號</span><span class="sxs-lookup"><span data-stu-id="29213-612">Test indicator not supported</span></span>|  
|<span data-ttu-id="29213-613">26</span><span class="sxs-lookup"><span data-stu-id="29213-613">26</span></span>|<span data-ttu-id="29213-614">偵測到重複</span><span class="sxs-lookup"><span data-stu-id="29213-614">Duplicate detected</span></span>|  
|<span data-ttu-id="29213-615">27</span><span class="sxs-lookup"><span data-stu-id="29213-615">27</span></span>|<span data-ttu-id="29213-616">不支援安全性函式</span><span class="sxs-lookup"><span data-stu-id="29213-616">Security function not supported</span></span>|  
|<span data-ttu-id="29213-617">28</span><span class="sxs-lookup"><span data-stu-id="29213-617">28</span></span>|<span data-ttu-id="29213-618">參考不相符</span><span class="sxs-lookup"><span data-stu-id="29213-618">References do not match</span></span>|  
|<span data-ttu-id="29213-619">29</span><span class="sxs-lookup"><span data-stu-id="29213-619">29</span></span>|<span data-ttu-id="29213-620">控制計數不符合接收到的執行個體數目</span><span class="sxs-lookup"><span data-stu-id="29213-620">Control count does not match number of instances received</span></span>|  
|<span data-ttu-id="29213-621">30</span><span class="sxs-lookup"><span data-stu-id="29213-621">30</span></span>|<span data-ttu-id="29213-622">群組和訊息/封裝已混合</span><span class="sxs-lookup"><span data-stu-id="29213-622">Groups and messages/packages mixed</span></span>|  
|<span data-ttu-id="29213-623">31</span><span class="sxs-lookup"><span data-stu-id="29213-623">31</span></span>|<span data-ttu-id="29213-624">群組中有一種以上的訊息類型</span><span class="sxs-lookup"><span data-stu-id="29213-624">More than one message type in group</span></span>|  
|<span data-ttu-id="29213-625">32</span><span class="sxs-lookup"><span data-stu-id="29213-625">32</span></span>|<span data-ttu-id="29213-626">較低層級空白</span><span class="sxs-lookup"><span data-stu-id="29213-626">Lower level empty</span></span>|  
|<span data-ttu-id="29213-627">33</span><span class="sxs-lookup"><span data-stu-id="29213-627">33</span></span>|<span data-ttu-id="29213-628">在訊息、封裝或群組外部出現的項目無效</span><span class="sxs-lookup"><span data-stu-id="29213-628">Invalid occurrence outside message, package, or group</span></span>|  
|<span data-ttu-id="29213-629">34</span><span class="sxs-lookup"><span data-stu-id="29213-629">34</span></span>|<span data-ttu-id="29213-630">不允許巢狀指示符號</span><span class="sxs-lookup"><span data-stu-id="29213-630">Nesting indicator not allowed</span></span>|  
|<span data-ttu-id="29213-631">35</span><span class="sxs-lookup"><span data-stu-id="29213-631">35</span></span>|<span data-ttu-id="29213-632">太多資料元素或區段重複</span><span class="sxs-lookup"><span data-stu-id="29213-632">Too many data element or segment repetitions</span></span>|  
|<span data-ttu-id="29213-633">36</span><span class="sxs-lookup"><span data-stu-id="29213-633">36</span></span>|<span data-ttu-id="29213-634">太多區段群組重複</span><span class="sxs-lookup"><span data-stu-id="29213-634">Too many segment group repetitions</span></span>|  
|<span data-ttu-id="29213-635">37</span><span class="sxs-lookup"><span data-stu-id="29213-635">37</span></span>|<span data-ttu-id="29213-636">無效字元類型</span><span class="sxs-lookup"><span data-stu-id="29213-636">Invalid type of character(s)</span></span>|  
|<span data-ttu-id="29213-637">38</span><span class="sxs-lookup"><span data-stu-id="29213-637">38</span></span>|<span data-ttu-id="29213-638">在小數符號之前遺失數字</span><span class="sxs-lookup"><span data-stu-id="29213-638">Missing digit in front of decimal sign</span></span>|  
|<span data-ttu-id="29213-639">39</span><span class="sxs-lookup"><span data-stu-id="29213-639">39</span></span>|<span data-ttu-id="29213-640">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="29213-640">Data element too long</span></span>|  
|<span data-ttu-id="29213-641">40</span><span class="sxs-lookup"><span data-stu-id="29213-641">40</span></span>|<span data-ttu-id="29213-642">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="29213-642">Data element too short</span></span>|  
|<span data-ttu-id="29213-643">41</span><span class="sxs-lookup"><span data-stu-id="29213-643">41</span></span>|<span data-ttu-id="29213-644">永久通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-644">Permanent communication network error</span></span>|  
|<span data-ttu-id="29213-645">42</span><span class="sxs-lookup"><span data-stu-id="29213-645">42</span></span>|<span data-ttu-id="29213-646">暫時通訊網路錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-646">Temporary communication network error</span></span>|  
|<span data-ttu-id="29213-647">43</span><span class="sxs-lookup"><span data-stu-id="29213-647">43</span></span>|<span data-ttu-id="29213-648">未知的交換收件者</span><span class="sxs-lookup"><span data-stu-id="29213-648">Unknown interchange recipient</span></span>|  
|<span data-ttu-id="29213-649">45</span><span class="sxs-lookup"><span data-stu-id="29213-649">45</span></span>|<span data-ttu-id="29213-650">尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="29213-650">Trailing separator</span></span>|  
|<span data-ttu-id="29213-651">46</span><span class="sxs-lookup"><span data-stu-id="29213-651">46</span></span>|<span data-ttu-id="29213-652">不支援字元集</span><span class="sxs-lookup"><span data-stu-id="29213-652">Character set not supported</span></span>|  
|<span data-ttu-id="29213-653">47</span><span class="sxs-lookup"><span data-stu-id="29213-653">47</span></span>|<span data-ttu-id="29213-654">不支援信封功能</span><span class="sxs-lookup"><span data-stu-id="29213-654">Envelope functionality not supported</span></span>|  
|<span data-ttu-id="29213-655">48</span><span class="sxs-lookup"><span data-stu-id="29213-655">48</span></span>|<span data-ttu-id="29213-656">違反相依性條件</span><span class="sxs-lookup"><span data-stu-id="29213-656">Dependency condition violated</span></span>|  
|<span data-ttu-id="29213-657">70</span><span class="sxs-lookup"><span data-stu-id="29213-657">70</span></span>|<span data-ttu-id="29213-658">交易集遺失或是交易集識別碼無效</span><span class="sxs-lookup"><span data-stu-id="29213-658">Transaction set is missing or invalid transaction set Identifier</span></span>|  
|<span data-ttu-id="29213-659">71</span><span class="sxs-lookup"><span data-stu-id="29213-659">71</span></span>|<span data-ttu-id="29213-660">設定或群組控制編號不相符的交易</span><span class="sxs-lookup"><span data-stu-id="29213-660">Transaction set or group control number mismatch</span></span>|  
|<span data-ttu-id="29213-661">72</span><span class="sxs-lookup"><span data-stu-id="29213-661">72</span></span>|<span data-ttu-id="29213-662">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="29213-662">Unrecognized segment ID</span></span>|  
|<span data-ttu-id="29213-663">73</span><span class="sxs-lookup"><span data-stu-id="29213-663">73</span></span>|<span data-ttu-id="29213-664">XML 不在正確的位置</span><span class="sxs-lookup"><span data-stu-id="29213-664">XML not at correct position</span></span>|  
|<span data-ttu-id="29213-665">74</span><span class="sxs-lookup"><span data-stu-id="29213-665">74</span></span>|<span data-ttu-id="29213-666">區段群組的重複太少</span><span class="sxs-lookup"><span data-stu-id="29213-666">Too few segment group repetitions</span></span>|  
|<span data-ttu-id="29213-667">75</span><span class="sxs-lookup"><span data-stu-id="29213-667">75</span></span>|<span data-ttu-id="29213-668">區段的重複太少</span><span class="sxs-lookup"><span data-stu-id="29213-668">Too few segment repetitions</span></span>|  
|<span data-ttu-id="29213-669">76</span><span class="sxs-lookup"><span data-stu-id="29213-669">76</span></span>|<span data-ttu-id="29213-670">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="29213-670">Too few data elements found</span></span>|  
  
 <span data-ttu-id="29213-671">X12 將使用的錯誤/語法錯誤碼如下：</span><span class="sxs-lookup"><span data-stu-id="29213-671">The following Error/Syntax Error Codes will be used for X12:</span></span>  
  
|<span data-ttu-id="29213-672">錯誤/語法錯誤碼中的資料</span><span class="sxs-lookup"><span data-stu-id="29213-672">Data in Error/Syntax Error Code</span></span><br /><br /> <span data-ttu-id="29213-673">(適用於 X12)</span><span class="sxs-lookup"><span data-stu-id="29213-673">(applicable to X12)</span></span>|<span data-ttu-id="29213-674">報告的錯誤描述</span><span class="sxs-lookup"><span data-stu-id="29213-674">Error Description for reporting</span></span>|  
|----------------------------------------------------------------|-------------------------------------|  
|<span data-ttu-id="29213-675">1</span><span class="sxs-lookup"><span data-stu-id="29213-675">1</span></span>|<span data-ttu-id="29213-676">不支援功能群組</span><span class="sxs-lookup"><span data-stu-id="29213-676">Functional group not supported</span></span>|  
|<span data-ttu-id="29213-677">2</span><span class="sxs-lookup"><span data-stu-id="29213-677">2</span></span>|<span data-ttu-id="29213-678">不支援功能群組版本</span><span class="sxs-lookup"><span data-stu-id="29213-678">Functional group version not supported</span></span>|  
|<span data-ttu-id="29213-679">3</span><span class="sxs-lookup"><span data-stu-id="29213-679">3</span></span>|<span data-ttu-id="29213-680">遺失功能群組結尾</span><span class="sxs-lookup"><span data-stu-id="29213-680">Functional group trailer missing</span></span>|  
|<span data-ttu-id="29213-681">4</span><span class="sxs-lookup"><span data-stu-id="29213-681">4</span></span>|<span data-ttu-id="29213-682">功能群組標頭與結尾中的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="29213-682">Group control number in the functional group header and trailer do not agree</span></span>|  
|<span data-ttu-id="29213-683">5</span><span class="sxs-lookup"><span data-stu-id="29213-683">5</span></span>|<span data-ttu-id="29213-684">包含的交易集數目不符合實際計數</span><span class="sxs-lookup"><span data-stu-id="29213-684">Number of included transaction sets does not match actual count</span></span>|  
|<span data-ttu-id="29213-685">6-26</span><span class="sxs-lookup"><span data-stu-id="29213-685">6-26</span></span>|<span data-ttu-id="29213-686">其他不支援的驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="29213-686">Other unsupported validation errors</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29213-687">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29213-687">See Also</span></span>  
 <span data-ttu-id="29213-688">[資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="29213-688">[How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="29213-689">如何儲存輸入 EDI 訊息的資料</span><span class="sxs-lookup"><span data-stu-id="29213-689">How Data Is Stored for Inbound EDI Messages</span></span>](../core/how-data-is-stored-for-inbound-edi-messages.md)