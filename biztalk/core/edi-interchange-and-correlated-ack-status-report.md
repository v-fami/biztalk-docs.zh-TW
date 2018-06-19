---
title: EDI 交換和相互關聯的 ACK 狀態報表 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a112cc3d-d34c-4652-a8ee-3355a31d4a03
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5f4268badf9907eb90b090abe34a8355b3ab8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242366"
---
# <a name="edi-interchange-and-correlated-ack-status-report"></a><span data-ttu-id="19566-102">EDI 交換和相互關聯的 ACK 狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-102">EDI Interchange and Correlated ACK Status Report</span></span>
<span data-ttu-id="19566-103">此報告會顯示 EDI 傳送和接收管線處理的所有 EDI 交換，以及與這些交換相互關聯的通知。</span><span class="sxs-lookup"><span data-stu-id="19566-103">This report shows all EDI interchanges that are processed by the EDI send and receive pipelines, and the acknowledgment correlated to those interchanges.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="19566-104">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="19566-104">Fields in the Status Report</span></span>  
 <span data-ttu-id="19566-105">[EDI 交換和相互關聯的 ACK 狀態] 報告會針對接收或傳送交換以及其相互關聯的通知，顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="19566-105">The EDI Interchange and Correlated ACK Status Report displays the following information for the received or sent interchanges and the acknowledgments that are correlated to them:</span></span>  
  
-   <span data-ttu-id="19566-106">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="19566-106">Sender Party</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19566-107">傳送者合作對象將會依照以下方式決定：</span><span class="sxs-lookup"><span data-stu-id="19566-107">The sender party will be determined as follows:</span></span>  
    >   
    >  -   <span data-ttu-id="19566-108">如果交換中的合作對象名稱符合合作對象之 EDI 屬性中所設定的名稱，則會顯示設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="19566-108">If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.</span></span>  
    > -   <span data-ttu-id="19566-109">如果交換中的合作對象名稱不符合任何已設定 EDI 屬性的現有合作對象，則會顯示指定交換中的合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="19566-109">If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.</span></span>  
  
-   <span data-ttu-id="19566-110">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="19566-110">Receiver Party</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19566-111">接收者合作對象名稱將會依照以下方式決定：</span><span class="sxs-lookup"><span data-stu-id="19566-111">The receiver party name will be determined as follows:</span></span>  
    >   
    >  -   <span data-ttu-id="19566-112">如果交換中的合作對象名稱符合合作對象之 EDI 屬性中所設定的名稱，則會顯示設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="19566-112">If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.</span></span>  
    > -   <span data-ttu-id="19566-113">如果交換中的合作對象名稱不符合任何已設定 EDI 屬性的現有合作對象，則會顯示指定交換中的合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="19566-113">If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.</span></span>  
  
-   <span data-ttu-id="19566-114">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="19566-114">Control ID</span></span>  
  
-   <span data-ttu-id="19566-115">方向</span><span class="sxs-lookup"><span data-stu-id="19566-115">Direction</span></span>  
  
-   <span data-ttu-id="19566-116">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="19566-116">Interchange Date Time</span></span>  
  
-   <span data-ttu-id="19566-117">EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="19566-117">EDI encoding type</span></span>  
  
-   <span data-ttu-id="19566-118">交換狀態</span><span class="sxs-lookup"><span data-stu-id="19566-118">Interchange Status</span></span>  
  
-   <span data-ttu-id="19566-119">群組計數</span><span class="sxs-lookup"><span data-stu-id="19566-119">Group Count</span></span>  
  
-   <span data-ttu-id="19566-120">連接埠識別碼</span><span class="sxs-lookup"><span data-stu-id="19566-120">Port ID</span></span>  
  
-   <span data-ttu-id="19566-121">傳送者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="19566-121">Sender Party Alias</span></span>  
  
-   <span data-ttu-id="19566-122">接收者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="19566-122">Receiver Party Alias</span></span>  
  
-   <span data-ttu-id="19566-123">交易集合相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="19566-123">Transaction Set Correlation ID</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="19566-124">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="19566-124">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="19566-125">您可以自訂 [EDI 交換和相互關聯的 ACK 狀態] 報告，方法是變更查詢運算式中負責決定所顯示之資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="19566-125">You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="19566-126">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="19566-126">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="19566-127">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="19566-127">Query Expression Field</span></span>|<span data-ttu-id="19566-128">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="19566-128">Potential Operators</span></span>|<span data-ttu-id="19566-129">可能的值</span><span class="sxs-lookup"><span data-stu-id="19566-129">Potential Values</span></span>|<span data-ttu-id="19566-130">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="19566-130">Included By Default?</span></span>|  
|<span data-ttu-id="19566-131">搜尋</span><span class="sxs-lookup"><span data-stu-id="19566-131">Search for</span></span>|<span data-ttu-id="19566-132">等於</span><span class="sxs-lookup"><span data-stu-id="19566-132">Equals</span></span>|<span data-ttu-id="19566-133">交換/通知狀態</span><span class="sxs-lookup"><span data-stu-id="19566-133">Interchange/ACK Status</span></span>|<span data-ttu-id="19566-134">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="19566-134">Yes (required)</span></span>|  
|<span data-ttu-id="19566-135">狀態</span><span class="sxs-lookup"><span data-stu-id="19566-135">Status</span></span>|<span data-ttu-id="19566-136">等於</span><span class="sxs-lookup"><span data-stu-id="19566-136">Equals</span></span><br /><br /> <span data-ttu-id="19566-137">不等於</span><span class="sxs-lookup"><span data-stu-id="19566-137">Not Equals</span></span>|<span data-ttu-id="19566-138">已接受</span><span class="sxs-lookup"><span data-stu-id="19566-138">Accepted</span></span><br /><br /> <span data-ttu-id="19566-139">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="19566-139">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="19566-140">已傳送</span><span class="sxs-lookup"><span data-stu-id="19566-140">Sent</span></span><br /><br /> <span data-ttu-id="19566-141">全部</span><span class="sxs-lookup"><span data-stu-id="19566-141">All</span></span><br /><br /> <span data-ttu-id="19566-142">預期通知</span><span class="sxs-lookup"><span data-stu-id="19566-142">Ack Expected</span></span><br /><br /> <span data-ttu-id="19566-143">未預期通知</span><span class="sxs-lookup"><span data-stu-id="19566-143">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="19566-144">已拒絕</span><span class="sxs-lookup"><span data-stu-id="19566-144">Rejected</span></span><br /><br /> <span data-ttu-id="19566-145">(這些值定義如下)。</span><span class="sxs-lookup"><span data-stu-id="19566-145">(These values are defined below.)</span></span>|<span data-ttu-id="19566-146">是</span><span class="sxs-lookup"><span data-stu-id="19566-146">Yes</span></span>|  
|<span data-ttu-id="19566-147">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="19566-147">Interchange Date Time</span></span>|<span data-ttu-id="19566-148">小於或等於</span><span class="sxs-lookup"><span data-stu-id="19566-148">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="19566-149">大於或等於</span><span class="sxs-lookup"><span data-stu-id="19566-149">Greater Than or Equals</span></span>|<span data-ttu-id="19566-150">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="19566-150">Specific Date Time</span></span><br /><br /> <span data-ttu-id="19566-151">今天</span><span class="sxs-lookup"><span data-stu-id="19566-151">Today</span></span><br /><br /> <span data-ttu-id="19566-152">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="19566-152">Today - 1</span></span>|<span data-ttu-id="19566-153">是</span><span class="sxs-lookup"><span data-stu-id="19566-153">Yes</span></span><br /><br /> <span data-ttu-id="19566-154">附註： 可以包含超過一次在查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="19566-154">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="19566-155">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="19566-155">Maximum Matches</span></span>|<span data-ttu-id="19566-156">等於</span><span class="sxs-lookup"><span data-stu-id="19566-156">Equals</span></span>|<span data-ttu-id="19566-157">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="19566-157">Integer (default of 50)</span></span>|<span data-ttu-id="19566-158">是</span><span class="sxs-lookup"><span data-stu-id="19566-158">Yes</span></span>|  
|<span data-ttu-id="19566-159">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="19566-159">Control ID</span></span>|<span data-ttu-id="19566-160">等於</span><span class="sxs-lookup"><span data-stu-id="19566-160">Equals</span></span>|<span data-ttu-id="19566-161">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="19566-161">Interchange Control ID</span></span>|<span data-ttu-id="19566-162">否</span><span class="sxs-lookup"><span data-stu-id="19566-162">No</span></span>|  
|<span data-ttu-id="19566-163">方向</span><span class="sxs-lookup"><span data-stu-id="19566-163">Direction</span></span>|<span data-ttu-id="19566-164">等於</span><span class="sxs-lookup"><span data-stu-id="19566-164">Equals</span></span>|<span data-ttu-id="19566-165">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="19566-165">All (default)</span></span><br /><br /> <span data-ttu-id="19566-166">Receive</span><span class="sxs-lookup"><span data-stu-id="19566-166">Receive</span></span><br /><br /> <span data-ttu-id="19566-167">Send</span><span class="sxs-lookup"><span data-stu-id="19566-167">Send</span></span>|<span data-ttu-id="19566-168">否</span><span class="sxs-lookup"><span data-stu-id="19566-168">No</span></span>|  
|<span data-ttu-id="19566-169">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="19566-169">Receiver Party</span></span>|<span data-ttu-id="19566-170">等於</span><span class="sxs-lookup"><span data-stu-id="19566-170">Equals</span></span>|<span data-ttu-id="19566-171">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="19566-171">All (default)</span></span><br /><br /> <span data-ttu-id="19566-172">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="19566-172">Specific party name</span></span>|<span data-ttu-id="19566-173">否</span><span class="sxs-lookup"><span data-stu-id="19566-173">No</span></span>|  
|<span data-ttu-id="19566-174">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="19566-174">Sender Party</span></span>|<span data-ttu-id="19566-175">等於</span><span class="sxs-lookup"><span data-stu-id="19566-175">Equals</span></span>|<span data-ttu-id="19566-176">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="19566-176">All (default)</span></span><br /><br /> <span data-ttu-id="19566-177">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="19566-177">Specific party name</span></span>|<span data-ttu-id="19566-178">否</span><span class="sxs-lookup"><span data-stu-id="19566-178">No</span></span>|  
  
## <a name="status-definitions"></a><span data-ttu-id="19566-179">狀態定義</span><span class="sxs-lookup"><span data-stu-id="19566-179">Status Definitions</span></span>  
 <span data-ttu-id="19566-180">EDI 狀態報告中所用的狀態值定義如下：</span><span class="sxs-lookup"><span data-stu-id="19566-180">The status values used in EDI status reports have the following definitions:</span></span>  
  
-   <span data-ttu-id="19566-181">已接受：有效的交換</span><span class="sxs-lookup"><span data-stu-id="19566-181">Accepted: Valid interchange</span></span>  
  
-   <span data-ttu-id="19566-182">已接受，發生錯誤：區段中已註明錯誤</span><span class="sxs-lookup"><span data-stu-id="19566-182">Accepted with Errors: Errors were noted in segments</span></span>  
  
-   <span data-ttu-id="19566-183">已傳送：已成功傳送交換</span><span class="sxs-lookup"><span data-stu-id="19566-183">Sent: The interchange was sent successfully</span></span>  
  
-   <span data-ttu-id="19566-184">All： 顯示與任何其他值的訊息</span><span class="sxs-lookup"><span data-stu-id="19566-184">All: Display a message with any of the other values</span></span>  
  
-   <span data-ttu-id="19566-185">預期通知</span><span class="sxs-lookup"><span data-stu-id="19566-185">Ack Expected</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19566-186">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 預期會有技術通知，則當傳送輸出訊息時，[交換狀態和通知詳細資料] 狀態報告中的 [交換狀態] 欄位將會針對此訊息設定為 [預期通知]。</span><span class="sxs-lookup"><span data-stu-id="19566-186">The Interchange Status field in the Interchange Status and ACK Details status report will be set to "Ack Expected" for an outbound message when the message is sent if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] expects a technical acknowledgment.</span></span> <span data-ttu-id="19566-187">會發生這個錯誤**預期 TA1**屬性設定**通知**頁面的單向協議索引標籤。已接收及驗證技術通知時，狀態就會變更為 已接受。</span><span class="sxs-lookup"><span data-stu-id="19566-187">This occurs if the **TA1 Expected** property is set in **Acknowledgements** page for the one-way agreement tab. The status will be changed to “Accepted” when the technical acknowledgment has been received and validated.</span></span> <span data-ttu-id="19566-188">請注意，只有技術通知會發生這個情況，功能通知則不會。</span><span class="sxs-lookup"><span data-stu-id="19566-188">Note that this only occurs for a technical acknowledgment, not a functional acknowledgment.</span></span>  
  
-   <span data-ttu-id="19566-189">未預期通知</span><span class="sxs-lookup"><span data-stu-id="19566-189">Ack Not Expected</span></span>  
  
-   <span data-ttu-id="19566-190">已拒絕：交換無效，因為發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="19566-190">Rejected: The interchange was invalid due to errors.</span></span>  
  
## <a name="additional-reports-displayed-from-this-report"></a><span data-ttu-id="19566-191">根據這份報告顯示的其他報告</span><span class="sxs-lookup"><span data-stu-id="19566-191">Additional Reports Displayed from This Report</span></span>  
 <span data-ttu-id="19566-192">您可針對 [交易集詳細資料] 報告中所顯示的交易集，顯示下列其他狀態報告。</span><span class="sxs-lookup"><span data-stu-id="19566-192">You can display the following additional status reports for a transaction set shown in the Transaction Set Details report.</span></span> <span data-ttu-id="19566-193">以滑鼠右鍵按一下 [EDI 交換和相互關聯的 ACK 狀態] 報告中所列的交換或通知，然後按一下適當的命令，即可存取報告：</span><span class="sxs-lookup"><span data-stu-id="19566-193">You access the reports by right-clicking an interchange or acknowledgment listed in the EDI Interchange and Correlated ACK Status report, and then clicking the appropriate command:</span></span>  
  
-   [<span data-ttu-id="19566-194">交換狀態和通知詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-194">Interchange Status and ACK Details Status Report</span></span>](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [<span data-ttu-id="19566-195">交易集詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-195">Transaction Set Details Status Report</span></span>](../core/transaction-set-details-status-report.md)  
  
## <a name="next-steps"></a><span data-ttu-id="19566-196">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="19566-196">Next steps</span></span>
  
-   [<span data-ttu-id="19566-197">交換狀態和通知詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-197">Interchange Status and ACK Details Status Report</span></span>](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [<span data-ttu-id="19566-198">交易集詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-198">Transaction Set Details Status Report</span></span>](../core/transaction-set-details-status-report.md)  
  
-   [<span data-ttu-id="19566-199">EDI 訊息內容狀態報告</span><span class="sxs-lookup"><span data-stu-id="19566-199">EDI Message Content Status Report</span></span>](../core/edi-message-content-status-report.md)  
  
