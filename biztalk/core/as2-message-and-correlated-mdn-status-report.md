---
title: "AS2 訊息和相互關聯的 MDN 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48ed0ee3-c844-4cb9-a84d-32b719ab8fab
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ce4aed138f4e32e87cb1d428050999cc2b764a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-message-and-correlated-mdn-status-report"></a><span data-ttu-id="0b96b-102">AS2 訊息和相互關聯的 MDN 狀態報告</span><span class="sxs-lookup"><span data-stu-id="0b96b-102">AS2 Message and Correlated MDN Status Report</span></span>
<span data-ttu-id="0b96b-103">此報告會顯示 AS2 傳送和接收管線處理的所有 AS2 訊息，以及與這些交換相互關聯的 MDN。</span><span class="sxs-lookup"><span data-stu-id="0b96b-103">This report shows all AS2 messages that are processed by the AS2 send and receive pipelines, and the MDNs correlated to those interchanges.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="0b96b-104">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="0b96b-104">Fields in the Status Report</span></span>  
 <span data-ttu-id="0b96b-105">「AS2 訊息和相互關聯的通知狀態報告」會針對已接收或已傳送的交換及其相互關聯的通知，顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="0b96b-105">The AS2 Message and Correlated ACK Status Report displays the following information for the received or sent interchanges and the acknowledgments that are correlated to them:</span></span>  
  
-   <span data-ttu-id="0b96b-106">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-106">Sender Party Name</span></span>  
  
-   <span data-ttu-id="0b96b-107">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-107">Receiver Party Name</span></span>  
  
-   <span data-ttu-id="0b96b-108">AS2 來源</span><span class="sxs-lookup"><span data-stu-id="0b96b-108">AS2 From</span></span>  
  
-   <span data-ttu-id="0b96b-109">AS2 目標</span><span class="sxs-lookup"><span data-stu-id="0b96b-109">AS2 To</span></span>  
  
-   <span data-ttu-id="0b96b-110">AS2 訊息識別碼</span><span class="sxs-lookup"><span data-stu-id="0b96b-110">AS2 Message ID</span></span>  
  
-   <span data-ttu-id="0b96b-111">AS2 訊息日期時間</span><span class="sxs-lookup"><span data-stu-id="0b96b-111">AS2 Message Date Time</span></span>  
  
-   <span data-ttu-id="0b96b-112">接收日期時間</span><span class="sxs-lookup"><span data-stu-id="0b96b-112">Received Date Time</span></span>  
  
-   <span data-ttu-id="0b96b-113">合作對象角色</span><span class="sxs-lookup"><span data-stu-id="0b96b-113">Party Role</span></span>  
  
-   <span data-ttu-id="0b96b-114">MDN 狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-114">MDN Status</span></span>  
  
-   <span data-ttu-id="0b96b-115">加密狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-115">Encryption Status</span></span>  
  
-   <span data-ttu-id="0b96b-116">簽章狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-116">Signature Status</span></span>  
  
-   <span data-ttu-id="0b96b-117">Edi 交換狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-117">Edi Interchange Status</span></span>  
  
-   <span data-ttu-id="0b96b-118">是重複的 AS2 訊息嗎</span><span class="sxs-lookup"><span data-stu-id="0b96b-118">Is AS2 Message duplicate</span></span>  
  
-   <span data-ttu-id="0b96b-119">若要檢查有重複的天數</span><span class="sxs-lookup"><span data-stu-id="0b96b-119">Days to check for duplicate</span></span>  
  
-   <span data-ttu-id="0b96b-120">檔名</span><span class="sxs-lookup"><span data-stu-id="0b96b-120">Filename</span></span>  
  
-   <span data-ttu-id="0b96b-121">啟用可信賴傳訊</span><span class="sxs-lookup"><span data-stu-id="0b96b-121">Reliable messaging enabled</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="0b96b-122">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="0b96b-122">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="0b96b-123">您可以自訂「AS2 訊息和相互關聯的通知狀態報告」，藉由變更查詢運算式中的欄位，決定要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="0b96b-123">You can customize the AS2 Message and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="0b96b-124">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="0b96b-124">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="0b96b-125">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="0b96b-125">Query Expression Field</span></span>|<span data-ttu-id="0b96b-126">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="0b96b-126">Potential Operators</span></span>|<span data-ttu-id="0b96b-127">可能的值</span><span class="sxs-lookup"><span data-stu-id="0b96b-127">Potential Values</span></span>|<span data-ttu-id="0b96b-128">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="0b96b-128">Included By Default?</span></span>|  
|<span data-ttu-id="0b96b-129">搜尋</span><span class="sxs-lookup"><span data-stu-id="0b96b-129">Search for</span></span>|<span data-ttu-id="0b96b-130">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-130">Equals</span></span>|<span data-ttu-id="0b96b-131">AS2/MDN 狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-131">AS2/MDN Status</span></span>|<span data-ttu-id="0b96b-132">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="0b96b-132">Yes (required)</span></span>|  
|<span data-ttu-id="0b96b-133">訊息狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-133">Message Status</span></span>|<span data-ttu-id="0b96b-134">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-134">Equals</span></span><br /><br /> <span data-ttu-id="0b96b-135">不等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-135">Not Equals</span></span>|<span data-ttu-id="0b96b-136">全部</span><span class="sxs-lookup"><span data-stu-id="0b96b-136">All</span></span><br /><br /> <span data-ttu-id="0b96b-137">認可-處理</span><span class="sxs-lookup"><span data-stu-id="0b96b-137">Acknowledged - Processed</span></span><br /><br /> <span data-ttu-id="0b96b-138">認可-失敗</span><span class="sxs-lookup"><span data-stu-id="0b96b-138">Acknowledged - Failed</span></span><br /><br /> <span data-ttu-id="0b96b-139">已處理-暫止的 MDN</span><span class="sxs-lookup"><span data-stu-id="0b96b-139">Processed - MDN pending</span></span><br /><br /> <span data-ttu-id="0b96b-140">已處理-未預期 MDN</span><span class="sxs-lookup"><span data-stu-id="0b96b-140">Processed - MDN not expected</span></span><br /><br /> <span data-ttu-id="0b96b-141">尚未認可 – 重新傳送嘗試超過</span><span class="sxs-lookup"><span data-stu-id="0b96b-141">Not acknowledged – Resend attempts exceeded</span></span><br /><br /> <span data-ttu-id="0b96b-142">尚未認可 – 重新傳送的時間長度超過</span><span class="sxs-lookup"><span data-stu-id="0b96b-142">Not acknowledged – Resend duration exceeded</span></span>|<span data-ttu-id="0b96b-143">是</span><span class="sxs-lookup"><span data-stu-id="0b96b-143">Yes</span></span>|  
|<span data-ttu-id="0b96b-144">AS2 訊息日期時間</span><span class="sxs-lookup"><span data-stu-id="0b96b-144">AS2 Message Date Time</span></span>|<span data-ttu-id="0b96b-145">小於或等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-145">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="0b96b-146">大於或等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-146">Greater Than or Equals</span></span>|<span data-ttu-id="0b96b-147">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="0b96b-147">Specific Date Time</span></span><br /><br /> <span data-ttu-id="0b96b-148">今天</span><span class="sxs-lookup"><span data-stu-id="0b96b-148">Today</span></span><br /><br /> <span data-ttu-id="0b96b-149">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="0b96b-149">Today - 1</span></span>|<span data-ttu-id="0b96b-150">是</span><span class="sxs-lookup"><span data-stu-id="0b96b-150">Yes</span></span><br /><br /> <span data-ttu-id="0b96b-151">附註： 可以包含超過一次在查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="0b96b-151">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="0b96b-152">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="0b96b-152">Maximum Matches</span></span>|<span data-ttu-id="0b96b-153">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-153">Equals</span></span>|<span data-ttu-id="0b96b-154">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="0b96b-154">Integer (default of 50)</span></span>|<span data-ttu-id="0b96b-155">是</span><span class="sxs-lookup"><span data-stu-id="0b96b-155">Yes</span></span>|  
|<span data-ttu-id="0b96b-156">AS2 訊息識別碼</span><span class="sxs-lookup"><span data-stu-id="0b96b-156">AS2 Message ID</span></span>|<span data-ttu-id="0b96b-157">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-157">Equals</span></span>|<span data-ttu-id="0b96b-158">全部</span><span class="sxs-lookup"><span data-stu-id="0b96b-158">All</span></span><br /><br /> <span data-ttu-id="0b96b-159">特定 AS2 訊息識別碼</span><span class="sxs-lookup"><span data-stu-id="0b96b-159">Specific AS2 Message ID</span></span>|<span data-ttu-id="0b96b-160">否</span><span class="sxs-lookup"><span data-stu-id="0b96b-160">No</span></span>|  
|<span data-ttu-id="0b96b-161">方向</span><span class="sxs-lookup"><span data-stu-id="0b96b-161">Direction</span></span>|<span data-ttu-id="0b96b-162">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-162">Equals</span></span>|<span data-ttu-id="0b96b-163">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="0b96b-163">All (default)</span></span><br /><br /> <span data-ttu-id="0b96b-164">Receive</span><span class="sxs-lookup"><span data-stu-id="0b96b-164">Receive</span></span><br /><br /> <span data-ttu-id="0b96b-165">Send</span><span class="sxs-lookup"><span data-stu-id="0b96b-165">Send</span></span>|<span data-ttu-id="0b96b-166">否</span><span class="sxs-lookup"><span data-stu-id="0b96b-166">No</span></span>|  
|<span data-ttu-id="0b96b-167">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-167">Receiver Party Name</span></span>|<span data-ttu-id="0b96b-168">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-168">Equals</span></span>|<span data-ttu-id="0b96b-169">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="0b96b-169">All (default)</span></span><br /><br /> <span data-ttu-id="0b96b-170">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-170">Specific party name</span></span>|<span data-ttu-id="0b96b-171">否</span><span class="sxs-lookup"><span data-stu-id="0b96b-171">No</span></span>|  
|<span data-ttu-id="0b96b-172">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-172">Sender Party Name</span></span>|<span data-ttu-id="0b96b-173">等於</span><span class="sxs-lookup"><span data-stu-id="0b96b-173">Equals</span></span>|<span data-ttu-id="0b96b-174">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="0b96b-174">All (default)</span></span><br /><br /> <span data-ttu-id="0b96b-175">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="0b96b-175">Specific party name</span></span>|<span data-ttu-id="0b96b-176">否</span><span class="sxs-lookup"><span data-stu-id="0b96b-176">No</span></span>|  
  
## <a name="additional-as2-message-and-correlated-mdn-status-reports"></a><span data-ttu-id="0b96b-177">其他 AS2 訊息和相互關聯的 MDN 狀態報告</span><span class="sxs-lookup"><span data-stu-id="0b96b-177">Additional AS2 Message and Correlated MDN Status Reports</span></span>  
 <span data-ttu-id="0b96b-178">如果您以滑鼠右鍵按一下 [AS2 訊息和相互關聯的 MDN 狀態] 報告中所列的 AS2 訊息，可以顯示下列其中一個詳細狀態報告：</span><span class="sxs-lookup"><span data-stu-id="0b96b-178">If you right-click an AS2 message listed in the AS2 Message and Correlated MDN status report, you can display one of the following more detailed status reports:</span></span>  
  
|<span data-ttu-id="0b96b-179">狀態報告</span><span class="sxs-lookup"><span data-stu-id="0b96b-179">Status Report</span></span>|<span data-ttu-id="0b96b-180">顯示的狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-180">Status Displayed</span></span>|  
|-------------------|----------------------|  
|<span data-ttu-id="0b96b-181">交換/通知狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-181">Interchange/ACK Status</span></span>|<span data-ttu-id="0b96b-182">AS2 訊息之 EDI 內容的狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-182">The status of the EDI payload of the AS2 message</span></span>|  
|<span data-ttu-id="0b96b-183">重新傳送狀態詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b96b-183">Resend Status Details</span></span>|<span data-ttu-id="0b96b-184">重新傳送訊息的狀態</span><span class="sxs-lookup"><span data-stu-id="0b96b-184">The resend status of the message</span></span>|  
|<span data-ttu-id="0b96b-185">訊息電傳格式</span><span class="sxs-lookup"><span data-stu-id="0b96b-185">Message Wire Format</span></span>|<span data-ttu-id="0b96b-186">AS2 訊息的電傳格式</span><span class="sxs-lookup"><span data-stu-id="0b96b-186">The wire format of the AS2 message</span></span>|  
|<span data-ttu-id="0b96b-187">訊息解碼</span><span class="sxs-lookup"><span data-stu-id="0b96b-187">Message Decoded</span></span>|<span data-ttu-id="0b96b-188">AS2 訊息的解碼格式</span><span class="sxs-lookup"><span data-stu-id="0b96b-188">The decoded format of the AS2 message</span></span>|  
|<span data-ttu-id="0b96b-189">MDN 訊息</span><span class="sxs-lookup"><span data-stu-id="0b96b-189">MDN Message</span></span>|<span data-ttu-id="0b96b-190">AS2 訊息相互關聯的 MDN 訊息</span><span class="sxs-lookup"><span data-stu-id="0b96b-190">The MDN message correlated to the AS2 message</span></span>|  
  
 <span data-ttu-id="0b96b-191">每個最後三個訊息的格式是相同的。</span><span class="sxs-lookup"><span data-stu-id="0b96b-191">The format of each of the final three messages is the same.</span></span> <span data-ttu-id="0b96b-192">如需詳細資訊，請參閱[AS2 訊息內容狀態報告](../core/as2-message-content-status-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="0b96b-192">For more information, see [AS2 Message Content Status Reports](../core/as2-message-content-status-reports.md).</span></span>  
  
## <a name="correlate-an-as2-message-with-its-edi-payload"></a><span data-ttu-id="0b96b-193">AS2 訊息與其 EDI 內容相互關聯</span><span class="sxs-lookup"><span data-stu-id="0b96b-193">Correlate an AS2 Message with its EDI Payload</span></span>  
 <span data-ttu-id="0b96b-194">AS2 和 EDI 狀態報告，可讓您將相互關聯的 AS2 訊息與其 EDI 內容的狀態項目。</span><span class="sxs-lookup"><span data-stu-id="0b96b-194">AS2 and EDI status reporting enables you to correlate status entries for an AS2 message and its EDI payload.</span></span> <span data-ttu-id="0b96b-195">如果您同時啟用 AS2 和 EDI 狀態報告，會在 AS2 狀態報告中建立 AS2 訊息的狀態項目，並在 EDI 狀態報告中建立該 AS2 訊息之 EDI 內容的狀態項目。</span><span class="sxs-lookup"><span data-stu-id="0b96b-195">If you have enabled both AS2 and EDI status reporting, a status entry is made in the AS2 status report for the AS2 message and a status entry is made in the EDI status report for the EDI payload of that AS2 message.</span></span> <span data-ttu-id="0b96b-196">如果您有顯示 AS2 狀態報告，您可以以滑鼠右鍵按一下 AS2 訊息狀態項目，然後按一下 顯示 AS2 訊息的 EDI 內容狀態**交換/通知狀態**。</span><span class="sxs-lookup"><span data-stu-id="0b96b-196">If you have the AS2 status report displayed, you can display the status of the EDI payload for an AS2 message by right-clicking the AS2 message status entry, and then clicking **Interchange/ACK Status**.</span></span> <span data-ttu-id="0b96b-197">如果 AS2 訊息中只有一個 EDI 交換，此動作將會顯示該 EDI 交換的狀態項目。</span><span class="sxs-lookup"><span data-stu-id="0b96b-197">If there is only one EDI interchange in the AS2 message, this action will bring up the status entry for that one interchange.</span></span>  
  
 <span data-ttu-id="0b96b-198">如果 AS2 訊息包含多個 EDI 交換，而您嘗試顯示 AS2 訊息中多個 EDI 交換的狀態，則只有最後一個 EDI 交換會在 [交換/通知狀態] 報告中顯示。</span><span class="sxs-lookup"><span data-stu-id="0b96b-198">If the AS2 message contains multiple EDI interchanges, and you attempt to display the status of the multiple EDI interchanges in the AS2 message, only the last EDI interchange will be displayed in the Interchange/ACK status report.</span></span> <span data-ttu-id="0b96b-199">此外， **EDI 交易控制編號**欄位在 [AS2/MDN 狀態] 報告中的只會顯示最後一個交換控制編號。</span><span class="sxs-lookup"><span data-stu-id="0b96b-199">In addition, the **EDI Interchange Control No** field in the AS2/MDN Status report will only show the last interchange control number.</span></span> <span data-ttu-id="0b96b-200">(交換控制編號可使 AS2 訊息與其 EDI 交換內容相互關聯)。</span><span class="sxs-lookup"><span data-stu-id="0b96b-200">(The interchange control number correlates the AS2 message and its EDI interchange payload.)</span></span>  
  
 <span data-ttu-id="0b96b-201">AS2 訊息中所有 EDI 交換的資料都會儲存在狀態報告資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b96b-201">The data for all EDI interchanges in an AS2 message is saved in the status report database.</span></span> <span data-ttu-id="0b96b-202">如果，您可以在 [交換/通知狀態] 報告中的 AS2 訊息中顯示的所有交換**Control ID Equals All**子句會在狀態報告查詢。</span><span class="sxs-lookup"><span data-stu-id="0b96b-202">You can display all interchanges in an AS2 message in the Interchange/ACK Status report if the **Control ID Equals All** clause is in the status report query.</span></span> <span data-ttu-id="0b96b-203">這也可能會顯示出其他不在 AS2 訊息中的交換，不過，您可以查看其他欄位 (如 [傳送者合作對象]、[接收者合作對象] 和 [交換日期時間]) 判斷哪些 EDI 交換是在某個單一的 AS2 訊息中。</span><span class="sxs-lookup"><span data-stu-id="0b96b-203">This will also potentially display other interchanges that are not in the AS2 message; however, you can determine which EDI interchanges are in a single AS2 message by looking at other fields, such as the Sender party, Receiver party, and Interchange Date Time.</span></span>  
  
 <span data-ttu-id="0b96b-204">**合作對象角色**欄位在 AS2 狀態報告和**方向**EDI 狀態報告中的欄位在意義上的是相反。</span><span class="sxs-lookup"><span data-stu-id="0b96b-204">The **Party role** field in the AS2 status report and the **Direction** field in the EDI status report are opposite in their meaning.</span></span> <span data-ttu-id="0b96b-205">針對內送 AS2 訊息含有 EDI 內容，**合作對象角色**欄位 AS2 訊息會是**寄件者**，雖然**方向**欄位會是 EDI 交換**接收**。</span><span class="sxs-lookup"><span data-stu-id="0b96b-205">For an incoming AS2 message with an EDI payload, the **Party role** field for the AS2 message would be **Sender**, while the **Direction** field for the EDI interchange would be **Receive**.</span></span> <span data-ttu-id="0b96b-206">這是因為對於從合作對象收到的內送訊息來說，該合作對象的角色就是傳送者。</span><span class="sxs-lookup"><span data-stu-id="0b96b-206">The reason for this is that for an incoming message received from a party, the role of that party is a sender.</span></span> <span data-ttu-id="0b96b-207">與所傳送 AS2 訊息相關之合作對象的屬性，就是做為 AS2 訊息傳送者之合作對象的屬性，即如 [夥伴協議管理] 的 [AS2 屬性] 對話方塊中所定義。</span><span class="sxs-lookup"><span data-stu-id="0b96b-207">The properties of that party related to an AS2 message that it sends are that of party as AS2 message sender, as defined in the AS2 Properties dialog box in the Partner Agreement Management.</span></span> <span data-ttu-id="0b96b-208">因此，AS2 合作對象角色與 EDI 方向相反。</span><span class="sxs-lookup"><span data-stu-id="0b96b-208">As a result, the AS2 party role is opposite to the EDI direction.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0b96b-209">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="0b96b-209">Next steps</span></span>
  
-   [<span data-ttu-id="0b96b-210">AS2 訊息內容狀態報告</span><span class="sxs-lookup"><span data-stu-id="0b96b-210">AS2 Message Content Status Reports</span></span>](../core/as2-message-content-status-reports.md)  
  
-   [<span data-ttu-id="0b96b-211">重新傳送狀態詳細資料報表</span><span class="sxs-lookup"><span data-stu-id="0b96b-211">Resend Status Details Report</span></span>](../core/resend-status-details-report.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b96b-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b96b-212">See Also</span></span>  
 [<span data-ttu-id="0b96b-213">AS2 訊息和相互關聯的 MDN 狀態報告</span><span class="sxs-lookup"><span data-stu-id="0b96b-213">AS2 Message and Correlated MDN Status Report</span></span>](../core/as2-message-and-correlated-mdn-status-report.md)   
