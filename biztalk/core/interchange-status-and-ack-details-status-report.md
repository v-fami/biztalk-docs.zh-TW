---
title: 交換狀態和通知詳細資料狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebba4af5-6dff-4bb8-9c63-739ef49bbbb8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3201bc969bc053e9a128cbb0e65a42a2714480c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999023"
---
# <a name="interchange-status-and-ack-details-status-report"></a><span data-ttu-id="f0535-102">交換狀態和通知詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="f0535-102">Interchange Status and ACK Details Status Report</span></span>
<span data-ttu-id="f0535-103">這份狀態報告會顯示交換的詳細資料，以及與其相關的交換 (技術) 通知和功能通知。</span><span class="sxs-lookup"><span data-stu-id="f0535-103">This status report displays details of an interchange and its correlated interchange (technical) acknowledgment and functional acknowledgments.</span></span> <span data-ttu-id="f0535-104">顯示此報表的交換內 [交換/通知狀態] 報告中，以滑鼠右鍵按一下，然後按一下**交換狀態和通知詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="f0535-104">You display this report for right-clicking an interchange within the Interchange/ACK status report, and then clicking **Interchange status and ack details**.</span></span>  
  
 <span data-ttu-id="f0535-105">這份報告會提供下列針對交換和相關通知的個別檢視：</span><span class="sxs-lookup"><span data-stu-id="f0535-105">This report provides the following separate views for the interchange and the correlated acknowledgments:</span></span>  
  
## <a name="interchange-status"></a><span data-ttu-id="f0535-106">交換狀態</span><span class="sxs-lookup"><span data-stu-id="f0535-106">Interchange Status</span></span>  
 <span data-ttu-id="f0535-107">這個檢視提供顯示下列欄位之值的表格：</span><span class="sxs-lookup"><span data-stu-id="f0535-107">This view provides a table showing the values for the following fields:</span></span>  
  
- <span data-ttu-id="f0535-108">傳送者合作對象識別碼</span><span class="sxs-lookup"><span data-stu-id="f0535-108">Sender party ID</span></span>  
  
- <span data-ttu-id="f0535-109">接收者合作對象識別碼</span><span class="sxs-lookup"><span data-stu-id="f0535-109">Receiver party ID</span></span>  
  
- <span data-ttu-id="f0535-110">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="f0535-110">Control ID</span></span>  
  
- <span data-ttu-id="f0535-111">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="f0535-111">Receiver party name</span></span>  
  
- <span data-ttu-id="f0535-112">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="f0535-112">Sender party name</span></span>  
  
- <span data-ttu-id="f0535-113">方向</span><span class="sxs-lookup"><span data-stu-id="f0535-113">Direction</span></span>  
  
- <span data-ttu-id="f0535-114">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="f0535-114">Interchange Date Time</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="f0535-115">接收文件，如果交換中所指定的日期是 YYMMDD 格式，而且 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示為 19YY。</span><span class="sxs-lookup"><span data-stu-id="f0535-115">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="f0535-116">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="f0535-116">If the date is less than 75, it will be displayed as 20YY.</span></span>  
  > 
  >  <span data-ttu-id="f0535-117">比方說，如果您收到包含值 991113 中 isa09-交換，交換日期將會列出在報表中為 11/13/1999年。</span><span class="sxs-lookup"><span data-stu-id="f0535-117">For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date will be listed in the report as 11/13/1999.</span></span>  
  
- <span data-ttu-id="f0535-118">群組計數</span><span class="sxs-lookup"><span data-stu-id="f0535-118">Group count</span></span>  
  
- <span data-ttu-id="f0535-119">連接埠識別碼</span><span class="sxs-lookup"><span data-stu-id="f0535-119">Port ID</span></span>  
  
- <span data-ttu-id="f0535-120">交換狀態</span><span class="sxs-lookup"><span data-stu-id="f0535-120">Interchange Status</span></span>  
  
- <span data-ttu-id="f0535-121">EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="f0535-121">EDI encoding type</span></span>  
  
- <span data-ttu-id="f0535-122">交易集合相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="f0535-122">Transaction Set Correlation Id</span></span>  
  
  <span data-ttu-id="f0535-123">如果做為交換接收者的合作對象已經啟用技術通知 (在 [EDI 屬性] 對話方塊的 [通知處理和驗證設定] 頁面中)，BizTalk Server 便會期待收到可回應其傳送之交換而傳回的技術 (交換) 通知。</span><span class="sxs-lookup"><span data-stu-id="f0535-123">If a technical acknowledgment is enabled for a party as an interchange receiver (in the ACK Processing and Validation Settings page of the EDI Properties dialog box), BizTalk Server expects a technical (interchange) acknowledgment to be returned in response to an interchange that it sends.</span></span> <span data-ttu-id="f0535-124">一開始在建立輸出交換的交換狀態項目時，BizTalk Server 會在 [交換狀態] 欄位中輸入「預期通知」。</span><span class="sxs-lookup"><span data-stu-id="f0535-124">When it initially creates an interchange status entry for an outbound interchange, it will enter ACK Expected in the Interchange Status field.</span></span> <span data-ttu-id="f0535-125">當它收到技術通知，並使其與原始的交換相互關聯時，便會更新 [交換狀態] 欄位，以表示它已經收到通知。</span><span class="sxs-lookup"><span data-stu-id="f0535-125">When it receives a technical acknowledgment and correlates it to the original interchange, it will update the Interchange Status field to indicate that it has received the acknowledgment.</span></span>  
  
## <a name="interchange-ack-status"></a><span data-ttu-id="f0535-126">交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="f0535-126">Interchange Ack Status</span></span>  
 <span data-ttu-id="f0535-127">這個檢視會顯示交換 (技術) 通知的狀態值。</span><span class="sxs-lookup"><span data-stu-id="f0535-127">This view displays status values for an interchange (technical) acknowledgment:</span></span>  
  
-   <span data-ttu-id="f0535-128">通知交換控制項 ID</span><span class="sxs-lookup"><span data-stu-id="f0535-128">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="f0535-129">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="f0535-129">Receiver party</span></span>  
  
-   <span data-ttu-id="f0535-130">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="f0535-130">Sender party</span></span>  
  
-   <span data-ttu-id="f0535-131">方向</span><span class="sxs-lookup"><span data-stu-id="f0535-131">Direction</span></span>  
  
-   <span data-ttu-id="f0535-132">通知交換日期</span><span class="sxs-lookup"><span data-stu-id="f0535-132">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="f0535-133">通知交換時間</span><span class="sxs-lookup"><span data-stu-id="f0535-133">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="f0535-134">通知狀態</span><span class="sxs-lookup"><span data-stu-id="f0535-134">Ack Status</span></span>  
  
-   <span data-ttu-id="f0535-135">狀態碼</span><span class="sxs-lookup"><span data-stu-id="f0535-135">Status Code</span></span>  
  
-   <span data-ttu-id="f0535-136">通知說明碼 1</span><span class="sxs-lookup"><span data-stu-id="f0535-136">Ack Note Code1</span></span>  
  
-   <span data-ttu-id="f0535-137">通知說明碼 2</span><span class="sxs-lookup"><span data-stu-id="f0535-137">Ack Note Code2</span></span>  
  
## <a name="functional-acks"></a><span data-ttu-id="f0535-138">功能通知</span><span class="sxs-lookup"><span data-stu-id="f0535-138">Functional Ack(s)</span></span>  
 <span data-ttu-id="f0535-139">這個檢視會顯示功能通知的狀態值。</span><span class="sxs-lookup"><span data-stu-id="f0535-139">This view displays status values for an functional acknowledgment:</span></span>  
  
-   <span data-ttu-id="f0535-140">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="f0535-140">Group Control Number</span></span>  
  
-   <span data-ttu-id="f0535-141">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="f0535-141">Receiver party</span></span>  
  
-   <span data-ttu-id="f0535-142">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="f0535-142">Sender party</span></span>  
  
-   <span data-ttu-id="f0535-143">方向</span><span class="sxs-lookup"><span data-stu-id="f0535-143">Direction</span></span>  
  
-   <span data-ttu-id="f0535-144">[狀態]</span><span class="sxs-lookup"><span data-stu-id="f0535-144">Status</span></span>  
  
-   <span data-ttu-id="f0535-145">狀態碼</span><span class="sxs-lookup"><span data-stu-id="f0535-145">Status Code</span></span>  
  
-   <span data-ttu-id="f0535-146">功能識別項程式碼</span><span class="sxs-lookup"><span data-stu-id="f0535-146">Functional ID Code</span></span>  
  
-   <span data-ttu-id="f0535-147">TS 計數</span><span class="sxs-lookup"><span data-stu-id="f0535-147">TS Count</span></span>  
  
-   <span data-ttu-id="f0535-148">通知交換控制項 ID</span><span class="sxs-lookup"><span data-stu-id="f0535-148">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="f0535-149">通知交換日期</span><span class="sxs-lookup"><span data-stu-id="f0535-149">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="f0535-150">通知交換時間</span><span class="sxs-lookup"><span data-stu-id="f0535-150">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="f0535-151">已傳遞 TS 計數</span><span class="sxs-lookup"><span data-stu-id="f0535-151">Delivered TS Count</span></span>  
  
-   <span data-ttu-id="f0535-152">已接受 TS 計數</span><span class="sxs-lookup"><span data-stu-id="f0535-152">Accepted TS Count</span></span>  
  
-   <span data-ttu-id="f0535-153">ErrorCode 1</span><span class="sxs-lookup"><span data-stu-id="f0535-153">ErrorCode 1</span></span>  
  
-   <span data-ttu-id="f0535-154">ErrorCode 2</span><span class="sxs-lookup"><span data-stu-id="f0535-154">ErrorCode 2</span></span>  
  
-   <span data-ttu-id="f0535-155">錯誤碼 3</span><span class="sxs-lookup"><span data-stu-id="f0535-155">ErrorCode 3</span></span>  
  
-   <span data-ttu-id="f0535-156">錯誤碼 4</span><span class="sxs-lookup"><span data-stu-id="f0535-156">ErrorCode 4</span></span>  
  
-   <span data-ttu-id="f0535-157">錯誤碼 5</span><span class="sxs-lookup"><span data-stu-id="f0535-157">ErrorCode 5</span></span>  
  
-   <span data-ttu-id="f0535-158">接收時間</span><span class="sxs-lookup"><span data-stu-id="f0535-158">Time Received</span></span>