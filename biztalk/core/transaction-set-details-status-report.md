---
title: "交易集詳細資料狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d81367c7-c74e-42cb-b856-748962b727ec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6da167ea995fa05d8e35807d8cf26f23b5444a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-details-status-report"></a><span data-ttu-id="ebf7b-102">交易集詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="ebf7b-102">Transaction Set Details Status Report</span></span>
<span data-ttu-id="ebf7b-103">這個報告會針對選自「交換/通知狀態」報告其中之特定 EDI 交換的交易集，顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-103">This report shows the details for transaction sets in a specific EDI interchange selected from within the Interchange/ACK Status report.</span></span> <span data-ttu-id="ebf7b-104">若要顯示此狀態報告，以滑鼠右鍵按一下 [交換/通知狀態] 報告中，查詢結果] 窗格中所列的交換，然後按一下 [**交易集詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-104">To display this status report, right-click an interchange listed in the Query results pane of the Interchange/ACK Status report, and then click **Transaction Set Details**.</span></span>  
  
 <span data-ttu-id="ebf7b-105">此報表是您已選取時，才可以使用**儲存交易集/內容 reporting**相關合作對象 [EDI 屬性] 對話方塊的 [一般] 頁面中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-105">This report is available only if you have selected the **Store transaction set/payload for reporting** property in the General Page of the EDI Properties dialog box for the related party.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="ebf7b-106">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="ebf7b-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="ebf7b-107">「交易集詳細資料狀態報告」會針對已接收或已傳送交換的交易集顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ebf7b-107">The Transaction Set Details Status Report displays the following information for transaction sets in received or sent interchanges:</span></span>  
  
-   <span data-ttu-id="ebf7b-108">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-108">Transaction Set ID</span></span>  
  
-   <span data-ttu-id="ebf7b-109">文件類型</span><span class="sxs-lookup"><span data-stu-id="ebf7b-109">Document type</span></span>  
  
-   <span data-ttu-id="ebf7b-110">傳送者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="ebf7b-110">Sender party alias</span></span>  
  
-   <span data-ttu-id="ebf7b-111">應用程式傳送者</span><span class="sxs-lookup"><span data-stu-id="ebf7b-111">Application Sender</span></span>  
  
-   <span data-ttu-id="ebf7b-112">接收者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="ebf7b-112">Receiver party alias</span></span>  
  
-   <span data-ttu-id="ebf7b-113">應用程式接收者</span><span class="sxs-lookup"><span data-stu-id="ebf7b-113">Application Receiver</span></span>  
  
-   <span data-ttu-id="ebf7b-114">方向</span><span class="sxs-lookup"><span data-stu-id="ebf7b-114">Direction</span></span>  
  
-   <span data-ttu-id="ebf7b-115">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="ebf7b-115">Interchange Control Number</span></span>  
  
-   <span data-ttu-id="ebf7b-116">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="ebf7b-116">Group Control Number</span></span>  
  
-   <span data-ttu-id="ebf7b-117">交易集合控制編號</span><span class="sxs-lookup"><span data-stu-id="ebf7b-117">Transaction Set Control Number</span></span>  
  
-   <span data-ttu-id="ebf7b-118">交易集合狀態</span><span class="sxs-lookup"><span data-stu-id="ebf7b-118">Transaction Set Status</span></span>  
  
-   <span data-ttu-id="ebf7b-119">交換日期時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="ebf7b-119">Interchange Date Time (not displayed by default)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebf7b-120">接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-120">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="ebf7b-121">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-121">If the date is less than 75, it will be displayed as 20YY.</span></span>  
    >   
    >  <span data-ttu-id="ebf7b-122">例如，如果您收到包含值 991113 中 isa09-交換，交換日期時間會列入報表中為 11/13/1999年。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-122">For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date Time will be listed in the report as 11/13/1999.</span></span>  
  
-   <span data-ttu-id="ebf7b-123">處理日期/時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="ebf7b-123">Processing Date/Time (not displayed by default)</span></span>  
  
-   <span data-ttu-id="ebf7b-124">群組日期/時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="ebf7b-124">Group Date/Time (not displayed by default)</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="ebf7b-125">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="ebf7b-125">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="ebf7b-126">您可以自訂 [EDI 交換和相互關聯的 ACK 狀態] 報告，方法是變更查詢運算式中負責決定所顯示之資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-126">You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="ebf7b-127">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="ebf7b-127">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="ebf7b-128">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="ebf7b-128">Query Expression Field</span></span>|<span data-ttu-id="ebf7b-129">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="ebf7b-129">Potential Operators</span></span>|<span data-ttu-id="ebf7b-130">可能的值</span><span class="sxs-lookup"><span data-stu-id="ebf7b-130">Potential Values</span></span>|<span data-ttu-id="ebf7b-131">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="ebf7b-131">Included By Default?</span></span>|  
|<span data-ttu-id="ebf7b-132">搜尋</span><span class="sxs-lookup"><span data-stu-id="ebf7b-132">Search for</span></span>|<span data-ttu-id="ebf7b-133">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-133">Equals</span></span>|<span data-ttu-id="ebf7b-134">交易集詳細資料</span><span class="sxs-lookup"><span data-stu-id="ebf7b-134">Transaction Set Details</span></span>|<span data-ttu-id="ebf7b-135">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="ebf7b-135">Yes (required)</span></span>|  
|<span data-ttu-id="ebf7b-136">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="ebf7b-136">Interchange Date Time</span></span>|<span data-ttu-id="ebf7b-137">小於或等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-137">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="ebf7b-138">大於或等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-138">Greater Than or Equals</span></span>|<span data-ttu-id="ebf7b-139">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="ebf7b-139">Specific Date Time</span></span><br /><br /> <span data-ttu-id="ebf7b-140">今天</span><span class="sxs-lookup"><span data-stu-id="ebf7b-140">Today</span></span><br /><br /> <span data-ttu-id="ebf7b-141">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="ebf7b-141">Today - 1</span></span>|<span data-ttu-id="ebf7b-142">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-142">Yes</span></span><br /><br /> <span data-ttu-id="ebf7b-143">附註： 可以包含超過一次在查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-143">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="ebf7b-144">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="ebf7b-144">Receiver Party Name</span></span>|<span data-ttu-id="ebf7b-145">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-145">Equals</span></span>|<span data-ttu-id="ebf7b-146">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="ebf7b-146">All (default)</span></span><br /><br /> <span data-ttu-id="ebf7b-147">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="ebf7b-147">Specific party name</span></span>|<span data-ttu-id="ebf7b-148">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-148">Yes</span></span>|  
|<span data-ttu-id="ebf7b-149">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="ebf7b-149">Sender Party Name</span></span>|<span data-ttu-id="ebf7b-150">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-150">Equals</span></span>|<span data-ttu-id="ebf7b-151">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="ebf7b-151">All (default)</span></span><br /><br /> <span data-ttu-id="ebf7b-152">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="ebf7b-152">Specific party name</span></span>|<span data-ttu-id="ebf7b-153">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-153">Yes</span></span>|  
|<span data-ttu-id="ebf7b-154">方向</span><span class="sxs-lookup"><span data-stu-id="ebf7b-154">Direction</span></span>|<span data-ttu-id="ebf7b-155">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-155">Equals</span></span>|<span data-ttu-id="ebf7b-156">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="ebf7b-156">All (default)</span></span><br /><br /> <span data-ttu-id="ebf7b-157">Receive</span><span class="sxs-lookup"><span data-stu-id="ebf7b-157">Receive</span></span><br /><br /> <span data-ttu-id="ebf7b-158">Send</span><span class="sxs-lookup"><span data-stu-id="ebf7b-158">Send</span></span>|<span data-ttu-id="ebf7b-159">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-159">Yes</span></span>|  
|<span data-ttu-id="ebf7b-160">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="ebf7b-160">Control ID</span></span>|<span data-ttu-id="ebf7b-161">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-161">Equals</span></span>|<span data-ttu-id="ebf7b-162">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-162">Interchange Control ID</span></span>|<span data-ttu-id="ebf7b-163">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-163">Yes</span></span>|  
|<span data-ttu-id="ebf7b-164">交易集合相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-164">Transaction Set Correlation Id</span></span>|<span data-ttu-id="ebf7b-165">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-165">Equals</span></span>|<span data-ttu-id="ebf7b-166">相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-166">Correlation Id</span></span>|<span data-ttu-id="ebf7b-167">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-167">Yes</span></span>|  
|<span data-ttu-id="ebf7b-168">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="ebf7b-168">Maximum Matches</span></span>|<span data-ttu-id="ebf7b-169">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-169">Equals</span></span>|<span data-ttu-id="ebf7b-170">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="ebf7b-170">Integer (default of 50)</span></span>|<span data-ttu-id="ebf7b-171">是</span><span class="sxs-lookup"><span data-stu-id="ebf7b-171">Yes</span></span>|  
|<span data-ttu-id="ebf7b-172">狀態</span><span class="sxs-lookup"><span data-stu-id="ebf7b-172">Status</span></span>|<span data-ttu-id="ebf7b-173">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-173">Equals</span></span><br /><br /> <span data-ttu-id="ebf7b-174">不等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-174">Not Equals</span></span>|<span data-ttu-id="ebf7b-175">已接受</span><span class="sxs-lookup"><span data-stu-id="ebf7b-175">Accepted</span></span><br /><br /> <span data-ttu-id="ebf7b-176">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="ebf7b-176">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="ebf7b-177">已傳送</span><span class="sxs-lookup"><span data-stu-id="ebf7b-177">Sent</span></span><br /><br /> <span data-ttu-id="ebf7b-178">全部</span><span class="sxs-lookup"><span data-stu-id="ebf7b-178">All</span></span><br /><br /> <span data-ttu-id="ebf7b-179">預期通知</span><span class="sxs-lookup"><span data-stu-id="ebf7b-179">Ack Expected</span></span><br /><br /> <span data-ttu-id="ebf7b-180">未預期通知</span><span class="sxs-lookup"><span data-stu-id="ebf7b-180">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="ebf7b-181">已拒絕</span><span class="sxs-lookup"><span data-stu-id="ebf7b-181">Rejected</span></span>|<span data-ttu-id="ebf7b-182">否</span><span class="sxs-lookup"><span data-stu-id="ebf7b-182">No</span></span>|  
|<span data-ttu-id="ebf7b-183">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-183">Transaction Set Id</span></span>|<span data-ttu-id="ebf7b-184">等於</span><span class="sxs-lookup"><span data-stu-id="ebf7b-184">Equals</span></span>|<span data-ttu-id="ebf7b-185">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="ebf7b-185">Transaction Set Id</span></span>|<span data-ttu-id="ebf7b-186">否</span><span class="sxs-lookup"><span data-stu-id="ebf7b-186">No</span></span>|  
  
## <a name="additional-reports-displayed-from-this-report"></a><span data-ttu-id="ebf7b-187">根據這份報告顯示的其他報告</span><span class="sxs-lookup"><span data-stu-id="ebf7b-187">Additional Reports Displayed from This Report</span></span>  
 <span data-ttu-id="ebf7b-188">您可針對 [交易集詳細資料] 報告所顯示的交易集，顯示下列其他狀態報告：</span><span class="sxs-lookup"><span data-stu-id="ebf7b-188">You can display the following additional status reports for a transaction set shown in the Transaction Set Details report:</span></span>  
  
-   <span data-ttu-id="ebf7b-189">訊息內容狀態報告：</span><span class="sxs-lookup"><span data-stu-id="ebf7b-189">Message Content status report.</span></span> <span data-ttu-id="ebf7b-190">您可以用滑鼠右鍵按一下詳細資料報告中的交易集，然後按一下 [檢視交易集內容] 來顯示報告。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-190">You access this report by right-clicking a transaction set in the details reports, and then clicking View Transaction Set Content.</span></span> <span data-ttu-id="ebf7b-191">如需詳細資訊，請參閱[EDI 訊息內容狀態報告](../core/edi-message-content-status-report.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-191">For more information, see [EDI Message Content Status Report](../core/edi-message-content-status-report.md).</span></span>  
  
-   <span data-ttu-id="ebf7b-192">交換/通知狀態報告：</span><span class="sxs-lookup"><span data-stu-id="ebf7b-192">Interchange/ACK Status report.</span></span> <span data-ttu-id="ebf7b-193">此報表會使用相同的使用者介面[EDI 交換和相互關聯的 ACK 狀態報告](../core/edi-interchange-and-correlated-ack-status-report.md)顯示多個交換。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-193">This report uses the same user interface as the [EDI Interchange and Correlated ACK Status Report](../core/edi-interchange-and-correlated-ack-status-report.md) that is displayed for multiple interchanges.</span></span> <span data-ttu-id="ebf7b-194">兩者間的差異，在於這份報告資料只涵蓋包含這個交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="ebf7b-194">The difference is that this report data for only the interchange that contains this transaction set.</span></span>  
  
