---
title: 交易集詳細資料狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d81367c7-c74e-42cb-b856-748962b727ec
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef31f7216eb011d95ab62ebf361dfcde8374ddd2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009951"
---
# <a name="transaction-set-details-status-report"></a><span data-ttu-id="d316f-102">交易集詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="d316f-102">Transaction Set Details Status Report</span></span>
<span data-ttu-id="d316f-103">這個報告會針對選自「交換/通知狀態」報告其中之特定 EDI 交換的交易集，顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d316f-103">This report shows the details for transaction sets in a specific EDI interchange selected from within the Interchange/ACK Status report.</span></span> <span data-ttu-id="d316f-104">若要顯示此狀態報告，以滑鼠右鍵按一下 交換/通知狀態 報告中，查詢結果窗格中所列的交換，然後按一下 **交易集詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="d316f-104">To display this status report, right-click an interchange listed in the Query results pane of the Interchange/ACK Status report, and then click **Transaction Set Details**.</span></span>  
  
 <span data-ttu-id="d316f-105">此報表可供您已選取時，才**儲存交易集/內容報告**相關合作對象 [EDI 屬性] 對話方塊的 [一般] 頁面中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d316f-105">This report is available only if you have selected the **Store transaction set/payload for reporting** property in the General Page of the EDI Properties dialog box for the related party.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="d316f-106">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="d316f-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="d316f-107">「交易集詳細資料狀態報告」會針對已接收或已傳送交換的交易集顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d316f-107">The Transaction Set Details Status Report displays the following information for transaction sets in received or sent interchanges:</span></span>  
  
- <span data-ttu-id="d316f-108">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-108">Transaction Set ID</span></span>  
  
- <span data-ttu-id="d316f-109">文件類型</span><span class="sxs-lookup"><span data-stu-id="d316f-109">Document type</span></span>  
  
- <span data-ttu-id="d316f-110">傳送者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="d316f-110">Sender party alias</span></span>  
  
- <span data-ttu-id="d316f-111">應用程式傳送者</span><span class="sxs-lookup"><span data-stu-id="d316f-111">Application Sender</span></span>  
  
- <span data-ttu-id="d316f-112">接收者合作對象別名</span><span class="sxs-lookup"><span data-stu-id="d316f-112">Receiver party alias</span></span>  
  
- <span data-ttu-id="d316f-113">應用程式接收者</span><span class="sxs-lookup"><span data-stu-id="d316f-113">Application Receiver</span></span>  
  
- <span data-ttu-id="d316f-114">方向</span><span class="sxs-lookup"><span data-stu-id="d316f-114">Direction</span></span>  
  
- <span data-ttu-id="d316f-115">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="d316f-115">Interchange Control Number</span></span>  
  
- <span data-ttu-id="d316f-116">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="d316f-116">Group Control Number</span></span>  
  
- <span data-ttu-id="d316f-117">交易集合控制編號</span><span class="sxs-lookup"><span data-stu-id="d316f-117">Transaction Set Control Number</span></span>  
  
- <span data-ttu-id="d316f-118">交易集合狀態</span><span class="sxs-lookup"><span data-stu-id="d316f-118">Transaction Set Status</span></span>  
  
- <span data-ttu-id="d316f-119">交換日期時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="d316f-119">Interchange Date Time (not displayed by default)</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d316f-120">接收文件，如果交換中所指定的日期是 YYMMDD 格式，而且 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示為 19YY。</span><span class="sxs-lookup"><span data-stu-id="d316f-120">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="d316f-121">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="d316f-121">If the date is less than 75, it will be displayed as 20YY.</span></span>  
  > 
  >  <span data-ttu-id="d316f-122">比方說，如果您收到包含值 991113 中 isa09-交換，交換日期時間將會列出在報表中為 11/13/1999年。</span><span class="sxs-lookup"><span data-stu-id="d316f-122">For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date Time will be listed in the report as 11/13/1999.</span></span>  
  
- <span data-ttu-id="d316f-123">處理日期/時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="d316f-123">Processing Date/Time (not displayed by default)</span></span>  
  
- <span data-ttu-id="d316f-124">群組日期/時間 （依預設不顯示）</span><span class="sxs-lookup"><span data-stu-id="d316f-124">Group Date/Time (not displayed by default)</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="d316f-125">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="d316f-125">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="d316f-126">您可以自訂 [EDI 交換和相互關聯的 ACK 狀態] 報告，方法是變更查詢運算式中負責決定所顯示之資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="d316f-126">You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="d316f-127">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="d316f-127">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="d316f-128">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="d316f-128">Query Expression Field</span></span>|<span data-ttu-id="d316f-129">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="d316f-129">Potential Operators</span></span>|<span data-ttu-id="d316f-130">可能的值</span><span class="sxs-lookup"><span data-stu-id="d316f-130">Potential Values</span></span>|<span data-ttu-id="d316f-131">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="d316f-131">Included By Default?</span></span>|  
|<span data-ttu-id="d316f-132">搜尋</span><span class="sxs-lookup"><span data-stu-id="d316f-132">Search for</span></span>|<span data-ttu-id="d316f-133">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-133">Equals</span></span>|<span data-ttu-id="d316f-134">交易集詳細資料</span><span class="sxs-lookup"><span data-stu-id="d316f-134">Transaction Set Details</span></span>|<span data-ttu-id="d316f-135">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="d316f-135">Yes (required)</span></span>|  
|<span data-ttu-id="d316f-136">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="d316f-136">Interchange Date Time</span></span>|<span data-ttu-id="d316f-137">小於或等於</span><span class="sxs-lookup"><span data-stu-id="d316f-137">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="d316f-138">大於或等於</span><span class="sxs-lookup"><span data-stu-id="d316f-138">Greater Than or Equals</span></span>|<span data-ttu-id="d316f-139">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="d316f-139">Specific Date Time</span></span><br /><br /> <span data-ttu-id="d316f-140">今天</span><span class="sxs-lookup"><span data-stu-id="d316f-140">Today</span></span><br /><br /> <span data-ttu-id="d316f-141">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="d316f-141">Today - 1</span></span>|<span data-ttu-id="d316f-142">是</span><span class="sxs-lookup"><span data-stu-id="d316f-142">Yes</span></span><br /><br /> <span data-ttu-id="d316f-143">注意： 可包含超過一次在查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="d316f-143">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="d316f-144">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="d316f-144">Receiver Party Name</span></span>|<span data-ttu-id="d316f-145">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-145">Equals</span></span>|<span data-ttu-id="d316f-146">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="d316f-146">All (default)</span></span><br /><br /> <span data-ttu-id="d316f-147">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="d316f-147">Specific party name</span></span>|<span data-ttu-id="d316f-148">是</span><span class="sxs-lookup"><span data-stu-id="d316f-148">Yes</span></span>|  
|<span data-ttu-id="d316f-149">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="d316f-149">Sender Party Name</span></span>|<span data-ttu-id="d316f-150">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-150">Equals</span></span>|<span data-ttu-id="d316f-151">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="d316f-151">All (default)</span></span><br /><br /> <span data-ttu-id="d316f-152">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="d316f-152">Specific party name</span></span>|<span data-ttu-id="d316f-153">是</span><span class="sxs-lookup"><span data-stu-id="d316f-153">Yes</span></span>|  
|<span data-ttu-id="d316f-154">方向</span><span class="sxs-lookup"><span data-stu-id="d316f-154">Direction</span></span>|<span data-ttu-id="d316f-155">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-155">Equals</span></span>|<span data-ttu-id="d316f-156">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="d316f-156">All (default)</span></span><br /><br /> <span data-ttu-id="d316f-157">Receive</span><span class="sxs-lookup"><span data-stu-id="d316f-157">Receive</span></span><br /><br /> <span data-ttu-id="d316f-158">Send</span><span class="sxs-lookup"><span data-stu-id="d316f-158">Send</span></span>|<span data-ttu-id="d316f-159">是</span><span class="sxs-lookup"><span data-stu-id="d316f-159">Yes</span></span>|  
|<span data-ttu-id="d316f-160">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="d316f-160">Control ID</span></span>|<span data-ttu-id="d316f-161">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-161">Equals</span></span>|<span data-ttu-id="d316f-162">交換控制識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-162">Interchange Control ID</span></span>|<span data-ttu-id="d316f-163">是</span><span class="sxs-lookup"><span data-stu-id="d316f-163">Yes</span></span>|  
|<span data-ttu-id="d316f-164">交易集合相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-164">Transaction Set Correlation Id</span></span>|<span data-ttu-id="d316f-165">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-165">Equals</span></span>|<span data-ttu-id="d316f-166">相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-166">Correlation Id</span></span>|<span data-ttu-id="d316f-167">是</span><span class="sxs-lookup"><span data-stu-id="d316f-167">Yes</span></span>|  
|<span data-ttu-id="d316f-168">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="d316f-168">Maximum Matches</span></span>|<span data-ttu-id="d316f-169">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-169">Equals</span></span>|<span data-ttu-id="d316f-170">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="d316f-170">Integer (default of 50)</span></span>|<span data-ttu-id="d316f-171">是</span><span class="sxs-lookup"><span data-stu-id="d316f-171">Yes</span></span>|  
|<span data-ttu-id="d316f-172">[狀態]</span><span class="sxs-lookup"><span data-stu-id="d316f-172">Status</span></span>|<span data-ttu-id="d316f-173">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-173">Equals</span></span><br /><br /> <span data-ttu-id="d316f-174">不等於</span><span class="sxs-lookup"><span data-stu-id="d316f-174">Not Equals</span></span>|<span data-ttu-id="d316f-175">已接受</span><span class="sxs-lookup"><span data-stu-id="d316f-175">Accepted</span></span><br /><br /> <span data-ttu-id="d316f-176">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d316f-176">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="d316f-177">已傳送</span><span class="sxs-lookup"><span data-stu-id="d316f-177">Sent</span></span><br /><br /> <span data-ttu-id="d316f-178">All</span><span class="sxs-lookup"><span data-stu-id="d316f-178">All</span></span><br /><br /> <span data-ttu-id="d316f-179">預期通知</span><span class="sxs-lookup"><span data-stu-id="d316f-179">Ack Expected</span></span><br /><br /> <span data-ttu-id="d316f-180">未預期通知</span><span class="sxs-lookup"><span data-stu-id="d316f-180">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="d316f-181">已拒絕</span><span class="sxs-lookup"><span data-stu-id="d316f-181">Rejected</span></span>|<span data-ttu-id="d316f-182">否</span><span class="sxs-lookup"><span data-stu-id="d316f-182">No</span></span>|  
|<span data-ttu-id="d316f-183">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-183">Transaction Set Id</span></span>|<span data-ttu-id="d316f-184">等於</span><span class="sxs-lookup"><span data-stu-id="d316f-184">Equals</span></span>|<span data-ttu-id="d316f-185">交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="d316f-185">Transaction Set Id</span></span>|<span data-ttu-id="d316f-186">否</span><span class="sxs-lookup"><span data-stu-id="d316f-186">No</span></span>|  
  
## <a name="additional-reports-displayed-from-this-report"></a><span data-ttu-id="d316f-187">根據這份報告顯示的其他報告</span><span class="sxs-lookup"><span data-stu-id="d316f-187">Additional Reports Displayed from This Report</span></span>  
 <span data-ttu-id="d316f-188">您可針對 [交易集詳細資料] 報告所顯示的交易集，顯示下列其他狀態報告：</span><span class="sxs-lookup"><span data-stu-id="d316f-188">You can display the following additional status reports for a transaction set shown in the Transaction Set Details report:</span></span>  
  
-   <span data-ttu-id="d316f-189">訊息內容狀態報告：</span><span class="sxs-lookup"><span data-stu-id="d316f-189">Message Content status report.</span></span> <span data-ttu-id="d316f-190">您可以用滑鼠右鍵按一下詳細資料報告中的交易集，然後按一下 [檢視交易集內容] 來顯示報告。</span><span class="sxs-lookup"><span data-stu-id="d316f-190">You access this report by right-clicking a transaction set in the details reports, and then clicking View Transaction Set Content.</span></span> <span data-ttu-id="d316f-191">如需詳細資訊，請參閱 < [EDI 訊息內容狀態報告](../core/edi-message-content-status-report.md)。</span><span class="sxs-lookup"><span data-stu-id="d316f-191">For more information, see [EDI Message Content Status Report](../core/edi-message-content-status-report.md).</span></span>  
  
-   <span data-ttu-id="d316f-192">交換/通知狀態報告：</span><span class="sxs-lookup"><span data-stu-id="d316f-192">Interchange/ACK Status report.</span></span> <span data-ttu-id="d316f-193">此報表會使用相同的使用者介面[EDI 交換和相互關聯的 ACK 狀態報告](../core/edi-interchange-and-correlated-ack-status-report.md)顯示多個交換。</span><span class="sxs-lookup"><span data-stu-id="d316f-193">This report uses the same user interface as the [EDI Interchange and Correlated ACK Status Report](../core/edi-interchange-and-correlated-ack-status-report.md) that is displayed for multiple interchanges.</span></span> <span data-ttu-id="d316f-194">兩者間的差異，在於這份報告資料只涵蓋包含這個交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="d316f-194">The difference is that this report data for only the interchange that contains this transaction set.</span></span>  
  
