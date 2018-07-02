---
title: 交換彙總報告 |Microsoft Docs
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
ms.openlocfilehash: 578747267c73c4428e28eefd8b07ba51e8196fed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977951"
---
# <a name="interchange-aggregation-report"></a><span data-ttu-id="fa2b8-102">交換彙總報告</span><span class="sxs-lookup"><span data-stu-id="fa2b8-102">Interchange Aggregation Report</span></span>
<span data-ttu-id="fa2b8-103">此報告可提供一份記錄，指出共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的 EDI 交換數目。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-103">This report provides one record that indicates the number of EDI interchanges that share the same EDI encoding type, sender party, receiver party, and direction.</span></span> <span data-ttu-id="fa2b8-104">此報告不提供個別交換的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-104">This report does not provide details about the individual interchanges.</span></span>  
  
 <span data-ttu-id="fa2b8-105">按一下底部的 [群組中樞] 頁面中的 [交換彙總報告] 連結會顯示此狀態報告[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-105">This status report is displayed by clicking the Interchange Aggregation Report link at the bottom of the Group Hub page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="fa2b8-106">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="fa2b8-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="fa2b8-107">交換彙總報告會顯示每份記錄的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="fa2b8-107">The Interchange Aggregation Report displays the following information for each record:</span></span>  
  
- <span data-ttu-id="fa2b8-108">有多少交換共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的統計數目</span><span class="sxs-lookup"><span data-stu-id="fa2b8-108">A count of how many interchanges share the same EDI encoding type, sender party, receiver party, and direction</span></span>  
  
- <span data-ttu-id="fa2b8-109">記錄中每個交換的傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="fa2b8-109">The Sender Party for each interchange in the record</span></span>  
  
- <span data-ttu-id="fa2b8-110">記錄中每個交換的接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="fa2b8-110">The Receiver Party for each interchange in the record</span></span>  
  
- <span data-ttu-id="fa2b8-111">記錄中每個交換的方向 (接收或傳送)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-111">The Direction (receive or send) of each interchange in the record</span></span>  
  
- <span data-ttu-id="fa2b8-112">在傳送或接收的時間範圍內，最早交換的日期和時間 (最早開始日期/時間)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-112">The date and time at which the earliest interchange in the time range was sent or received (Earliest Started Date/Time)</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="fa2b8-113">接收文件，如果交換中所指定的日期是 YYMMDD 格式，而且 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示為 19YY。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-113">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="fa2b8-114">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-114">If the date is less than 75, it will be displayed as 20YY.</span></span>  
  > 
  >  <span data-ttu-id="fa2b8-115">比方說，如果您收到的交換包含值 991113 中 isa09-，最早開始日期/時間將會列在 1999 年 11/13/報表。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-115">For example, if you receive an interchange that contains the value 991113 in ISA09, the Earliest Started Date/time will be listed in the report as 11/13/1999.</span></span>  
  
- <span data-ttu-id="fa2b8-116">在傳送或接收的時間範圍內，最晚交換的日期和時間 (最新結束日期/時間)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-116">The date and time at which the latest interchange in the time range was sent or received (Latest Ended Date/Time)</span></span>  
  
- <span data-ttu-id="fa2b8-117">記錄中每個交換的 EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="fa2b8-117">The EDI encoding type for each interchange in the record</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="fa2b8-118">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="fa2b8-118">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="fa2b8-119">您可以自訂 [交換彙總報告]，只要變更會決定所顯示資料之查詢運算式中的欄位即可。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-119">You can customize the Interchange Aggregation Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="fa2b8-120">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="fa2b8-120">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="fa2b8-121">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="fa2b8-121">Query Expression Field</span></span>|<span data-ttu-id="fa2b8-122">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="fa2b8-122">Potential Operators</span></span>|<span data-ttu-id="fa2b8-123">可能的值</span><span class="sxs-lookup"><span data-stu-id="fa2b8-123">Potential Values</span></span>|<span data-ttu-id="fa2b8-124">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="fa2b8-124">Included By Default?</span></span>|  
|<span data-ttu-id="fa2b8-125">搜尋</span><span class="sxs-lookup"><span data-stu-id="fa2b8-125">Search for</span></span>|<span data-ttu-id="fa2b8-126">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-126">Equals</span></span>|<span data-ttu-id="fa2b8-127">交換彙總報告</span><span class="sxs-lookup"><span data-stu-id="fa2b8-127">Interchange Aggregation Report</span></span>|<span data-ttu-id="fa2b8-128">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-128">Yes (required)</span></span>|  
|<span data-ttu-id="fa2b8-129">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="fa2b8-129">Interchange Date Time</span></span>|<span data-ttu-id="fa2b8-130">小於或等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-130">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="fa2b8-131">大於或等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-131">Greater Than or Equals</span></span>|<span data-ttu-id="fa2b8-132">特定日期時間</span><span class="sxs-lookup"><span data-stu-id="fa2b8-132">Specific Date Time</span></span><br /><br /> <span data-ttu-id="fa2b8-133">今天</span><span class="sxs-lookup"><span data-stu-id="fa2b8-133">Today</span></span><br /><br /> <span data-ttu-id="fa2b8-134">今日 - 1</span><span class="sxs-lookup"><span data-stu-id="fa2b8-134">Today - 1</span></span>|<span data-ttu-id="fa2b8-135">是</span><span class="sxs-lookup"><span data-stu-id="fa2b8-135">Yes</span></span><br /><br /> <span data-ttu-id="fa2b8-136">附註： 可以包含兩次在查詢運算式中，一次使用較低的運算子，另一次加入大於-運算子，以便提供範圍。</span><span class="sxs-lookup"><span data-stu-id="fa2b8-136">Note: Can be included twice in the query expression, once with a less-than operator and once with a greater-than operator, to provide a range.</span></span>|  
|<span data-ttu-id="fa2b8-137">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="fa2b8-137">Maximum Matches</span></span>|<span data-ttu-id="fa2b8-138">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-138">Equals</span></span>|<span data-ttu-id="fa2b8-139">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-139">Integer (default of 50)</span></span>|<span data-ttu-id="fa2b8-140">是</span><span class="sxs-lookup"><span data-stu-id="fa2b8-140">Yes</span></span>|  
|<span data-ttu-id="fa2b8-141">方向</span><span class="sxs-lookup"><span data-stu-id="fa2b8-141">Direction</span></span>|<span data-ttu-id="fa2b8-142">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-142">Equals</span></span>|<span data-ttu-id="fa2b8-143">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-143">All (default)</span></span><br /><br /> <span data-ttu-id="fa2b8-144">Receive</span><span class="sxs-lookup"><span data-stu-id="fa2b8-144">Receive</span></span><br /><br /> <span data-ttu-id="fa2b8-145">Send</span><span class="sxs-lookup"><span data-stu-id="fa2b8-145">Send</span></span>|<span data-ttu-id="fa2b8-146">否</span><span class="sxs-lookup"><span data-stu-id="fa2b8-146">No</span></span>|  
|<span data-ttu-id="fa2b8-147">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="fa2b8-147">Receiver Party Name</span></span>|<span data-ttu-id="fa2b8-148">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-148">Equals</span></span>|<span data-ttu-id="fa2b8-149">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-149">All (default)</span></span><br /><br /> <span data-ttu-id="fa2b8-150">特定合作對象名稱 (AN 字串)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-150">Specific party name (AN string)</span></span>|<span data-ttu-id="fa2b8-151">否</span><span class="sxs-lookup"><span data-stu-id="fa2b8-151">No</span></span>|  
|<span data-ttu-id="fa2b8-152">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="fa2b8-152">Sender Party Name</span></span>|<span data-ttu-id="fa2b8-153">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-153">Equals</span></span>|<span data-ttu-id="fa2b8-154">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-154">All (default)</span></span><br /><br /> <span data-ttu-id="fa2b8-155">特定合作對象名稱 (AN 字串)</span><span class="sxs-lookup"><span data-stu-id="fa2b8-155">Specific party name (AN string)</span></span>|<span data-ttu-id="fa2b8-156">否</span><span class="sxs-lookup"><span data-stu-id="fa2b8-156">No</span></span>|  
|<span data-ttu-id="fa2b8-157">[狀態]</span><span class="sxs-lookup"><span data-stu-id="fa2b8-157">Status</span></span>|<span data-ttu-id="fa2b8-158">等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-158">Equals</span></span><br /><br /> <span data-ttu-id="fa2b8-159">不等於</span><span class="sxs-lookup"><span data-stu-id="fa2b8-159">Not Equals</span></span>|<span data-ttu-id="fa2b8-160">已接受</span><span class="sxs-lookup"><span data-stu-id="fa2b8-160">Accepted</span></span><br /><br /> <span data-ttu-id="fa2b8-161">已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="fa2b8-161">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="fa2b8-162">已傳送</span><span class="sxs-lookup"><span data-stu-id="fa2b8-162">Sent</span></span><br /><br /> <span data-ttu-id="fa2b8-163">All</span><span class="sxs-lookup"><span data-stu-id="fa2b8-163">All</span></span><br /><br /> <span data-ttu-id="fa2b8-164">預期通知</span><span class="sxs-lookup"><span data-stu-id="fa2b8-164">Ack Expected</span></span><br /><br /> <span data-ttu-id="fa2b8-165">未預期通知</span><span class="sxs-lookup"><span data-stu-id="fa2b8-165">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="fa2b8-166">已拒絕</span><span class="sxs-lookup"><span data-stu-id="fa2b8-166">Rejected</span></span>|<span data-ttu-id="fa2b8-167">否</span><span class="sxs-lookup"><span data-stu-id="fa2b8-167">No</span></span>|