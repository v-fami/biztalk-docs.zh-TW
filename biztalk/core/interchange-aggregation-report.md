---
title: 交換彙總報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4619e8d0-9e9e-4d19-a67a-ac1058a0579b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac86a43bc74d862aa856a18f1564b03bc7f4e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257878"
---
# <a name="interchange-aggregation-report"></a><span data-ttu-id="139df-102">交換彙總報告</span><span class="sxs-lookup"><span data-stu-id="139df-102">Interchange Aggregation Report</span></span>
<span data-ttu-id="139df-103">此報告可提供一份記錄，指出共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的 EDI 交換數目。</span><span class="sxs-lookup"><span data-stu-id="139df-103">This report provides one record that indicates the number of EDI interchanges that share the same EDI encoding type, sender party, receiver party, and direction.</span></span> <span data-ttu-id="139df-104">此報告不提供個別交換的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="139df-104">This report does not provide details about the individual interchanges.</span></span>  
  
 <span data-ttu-id="139df-105">此狀態報告中的 [群組中樞] 頁面底部的 [交換彙總報告] 連結，即可顯示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="139df-105">This status report is displayed by clicking the Interchange Aggregation Report link at the bottom of the Group Hub page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="139df-106">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="139df-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="139df-107">交換彙總報告會顯示每份記錄的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="139df-107">The Interchange Aggregation Report displays the following information for each record:</span></span>  
  
-   <span data-ttu-id="139df-108">有多少交換共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的統計數目</span><span class="sxs-lookup"><span data-stu-id="139df-108">A count of how many interchanges share the same EDI encoding type, sender party, receiver party, and direction</span></span>  
  
-   <span data-ttu-id="139df-109">記錄中每個交換的傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="139df-109">The Sender Party for each interchange in the record</span></span>  
  
-   <span data-ttu-id="139df-110">記錄中每個交換的接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="139df-110">The Receiver Party for each interchange in the record</span></span>  
  
-   <span data-ttu-id="139df-111">記錄中每個交換的方向 (接收或傳送)</span><span class="sxs-lookup"><span data-stu-id="139df-111">The Direction (receive or send) of each interchange in the record</span></span>  
  
-   <span data-ttu-id="139df-112">在傳送或接收的時間範圍內，最早交換的日期和時間 (最早開始日期/時間)</span><span class="sxs-lookup"><span data-stu-id="139df-112">The date and time at which the earliest interchange in the time range was sent or received (Earliest Started Date/Time)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="139df-113">接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。</span><span class="sxs-lookup"><span data-stu-id="139df-113">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="139df-114">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="139df-114">If the date is less than 75, it will be displayed as 20YY.</span></span>  
    >   
    >  <span data-ttu-id="139df-115">比方說，如果您收到的交換包含值 991113 中 ISA09，最早啟動日期/時間會列出為 11/13/1999年報表中。</span><span class="sxs-lookup"><span data-stu-id="139df-115">For example, if you receive an interchange that contains the value 991113 in ISA09, the Earliest Started Date/time will be listed in the report as 11/13/1999.</span></span>  
  
-   <span data-ttu-id="139df-116">在傳送或接收的時間範圍內，最晚交換的日期和時間 (最新結束日期/時間)</span><span class="sxs-lookup"><span data-stu-id="139df-116">The date and time at which the latest interchange in the time range was sent or received (Latest Ended Date/Time)</span></span>  
  
-   <span data-ttu-id="139df-117">記錄中每個交換的 EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="139df-117">The EDI encoding type for each interchange in the record</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="139df-118">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="139df-118">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="139df-119">您可以自訂 [交換彙總報告]，只要變更會決定所顯示資料之查詢運算式中的欄位即可。</span><span class="sxs-lookup"><span data-stu-id="139df-119">You can customize the Interchange Aggregation Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="139df-120">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="139df-120">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="139df-121">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="139df-121">Query Expression Field</span></span>|<span data-ttu-id="139df-122">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="139df-122">Potential Operators</span></span>|<span data-ttu-id="139df-123">可能的值</span><span class="sxs-lookup"><span data-stu-id="139df-123">Potential Values</span></span>|<span data-ttu-id="139df-124">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="139df-124">Included By Default?</span></span>|  
|<span data-ttu-id="139df-125">搜尋</span><span class="sxs-lookup"><span data-stu-id="139df-125">Search for</span></span>|<span data-ttu-id="139df-126">等於</span><span class="sxs-lookup"><span data-stu-id="139df-126">Equals</span></span>|<span data-ttu-id="139df-127">交換彙總報告</span><span class="sxs-lookup"><span data-stu-id="139df-127">Interchange Aggregation Report</span></span>|<span data-ttu-id="139df-128">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="139df-128">Yes (required)</span></span>|  
|<span data-ttu-id="139df-129">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="139df-129">Interchange Date Time</span></span>|<span data-ttu-id="139df-130">小於或等於</span><span class="sxs-lookup"><span data-stu-id="139df-130">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="139df-131">大於或等於</span><span class="sxs-lookup"><span data-stu-id="139df-131">Greater Than or Equals</span></span>|<span data-ttu-id="139df-132">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="139df-132">Specific Date Time</span></span><br /><br /> <span data-ttu-id="139df-133">今天</span><span class="sxs-lookup"><span data-stu-id="139df-133">Today</span></span><br /><br /> <span data-ttu-id="139df-134">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="139df-134">Today - 1</span></span>|<span data-ttu-id="139df-135">是</span><span class="sxs-lookup"><span data-stu-id="139df-135">Yes</span></span><br /><br /> <span data-ttu-id="139df-136">附註： 可以包含在查詢運算式中，一次使用小於兩次-運算子，另一次加入大於位運算子，以便提供範圍。</span><span class="sxs-lookup"><span data-stu-id="139df-136">Note: Can be included twice in the query expression, once with a less-than operator and once with a greater-than operator, to provide a range.</span></span>|  
|<span data-ttu-id="139df-137">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="139df-137">Maximum Matches</span></span>|<span data-ttu-id="139df-138">等於</span><span class="sxs-lookup"><span data-stu-id="139df-138">Equals</span></span>|<span data-ttu-id="139df-139">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="139df-139">Integer (default of 50)</span></span>|<span data-ttu-id="139df-140">是</span><span class="sxs-lookup"><span data-stu-id="139df-140">Yes</span></span>|  
|<span data-ttu-id="139df-141">方向</span><span class="sxs-lookup"><span data-stu-id="139df-141">Direction</span></span>|<span data-ttu-id="139df-142">等於</span><span class="sxs-lookup"><span data-stu-id="139df-142">Equals</span></span>|<span data-ttu-id="139df-143">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="139df-143">All (default)</span></span><br /><br /> <span data-ttu-id="139df-144">Receive</span><span class="sxs-lookup"><span data-stu-id="139df-144">Receive</span></span><br /><br /> <span data-ttu-id="139df-145">Send</span><span class="sxs-lookup"><span data-stu-id="139df-145">Send</span></span>|<span data-ttu-id="139df-146">否</span><span class="sxs-lookup"><span data-stu-id="139df-146">No</span></span>|  
|<span data-ttu-id="139df-147">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="139df-147">Receiver Party Name</span></span>|<span data-ttu-id="139df-148">等於</span><span class="sxs-lookup"><span data-stu-id="139df-148">Equals</span></span>|<span data-ttu-id="139df-149">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="139df-149">All (default)</span></span><br /><br /> <span data-ttu-id="139df-150">特定合作對象名稱 (AN 字串)</span><span class="sxs-lookup"><span data-stu-id="139df-150">Specific party name (AN string)</span></span>|<span data-ttu-id="139df-151">否</span><span class="sxs-lookup"><span data-stu-id="139df-151">No</span></span>|  
|<span data-ttu-id="139df-152">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="139df-152">Sender Party Name</span></span>|<span data-ttu-id="139df-153">等於</span><span class="sxs-lookup"><span data-stu-id="139df-153">Equals</span></span>|<span data-ttu-id="139df-154">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="139df-154">All (default)</span></span><br /><br /> <span data-ttu-id="139df-155">特定合作對象名稱 (AN 字串)</span><span class="sxs-lookup"><span data-stu-id="139df-155">Specific party name (AN string)</span></span>|<span data-ttu-id="139df-156">否</span><span class="sxs-lookup"><span data-stu-id="139df-156">No</span></span>|  
|<span data-ttu-id="139df-157">狀態</span><span class="sxs-lookup"><span data-stu-id="139df-157">Status</span></span>|<span data-ttu-id="139df-158">等於</span><span class="sxs-lookup"><span data-stu-id="139df-158">Equals</span></span><br /><br /> <span data-ttu-id="139df-159">不等於</span><span class="sxs-lookup"><span data-stu-id="139df-159">Not Equals</span></span>|<span data-ttu-id="139df-160">已接受</span><span class="sxs-lookup"><span data-stu-id="139df-160">Accepted</span></span><br /><br /> <span data-ttu-id="139df-161">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="139df-161">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="139df-162">已傳送</span><span class="sxs-lookup"><span data-stu-id="139df-162">Sent</span></span><br /><br /> <span data-ttu-id="139df-163">全部</span><span class="sxs-lookup"><span data-stu-id="139df-163">All</span></span><br /><br /> <span data-ttu-id="139df-164">預期通知</span><span class="sxs-lookup"><span data-stu-id="139df-164">Ack Expected</span></span><br /><br /> <span data-ttu-id="139df-165">未預期通知</span><span class="sxs-lookup"><span data-stu-id="139df-165">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="139df-166">已拒絕</span><span class="sxs-lookup"><span data-stu-id="139df-166">Rejected</span></span>|<span data-ttu-id="139df-167">否</span><span class="sxs-lookup"><span data-stu-id="139df-167">No</span></span>|