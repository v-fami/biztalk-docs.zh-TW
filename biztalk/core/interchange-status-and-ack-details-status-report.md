---
title: 交換狀態和通知詳細資料狀態報告 |Microsoft 文件
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
ms.openlocfilehash: 7cc596a99d1a49b01ccc417abccb73d12ed34ad5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257638"
---
# <a name="interchange-status-and-ack-details-status-report"></a><span data-ttu-id="2115c-102">交換狀態和通知詳細資料狀態報告</span><span class="sxs-lookup"><span data-stu-id="2115c-102">Interchange Status and ACK Details Status Report</span></span>
<span data-ttu-id="2115c-103">這份狀態報告會顯示交換的詳細資料，以及與其相關的交換 (技術) 通知和功能通知。</span><span class="sxs-lookup"><span data-stu-id="2115c-103">This status report displays details of an interchange and its correlated interchange (technical) acknowledgment and functional acknowledgments.</span></span> <span data-ttu-id="2115c-104">顯示此報表的交換內 交換/通知狀態報告，以滑鼠右鍵按一下，然後按一下 **交換狀態和通知詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="2115c-104">You display this report for right-clicking an interchange within the Interchange/ACK status report, and then clicking **Interchange status and ack details**.</span></span>  
  
 <span data-ttu-id="2115c-105">這份報告會提供下列針對交換和相關通知的個別檢視：</span><span class="sxs-lookup"><span data-stu-id="2115c-105">This report provides the following separate views for the interchange and the correlated acknowledgments:</span></span>  
  
## <a name="interchange-status"></a><span data-ttu-id="2115c-106">交換狀態</span><span class="sxs-lookup"><span data-stu-id="2115c-106">Interchange Status</span></span>  
 <span data-ttu-id="2115c-107">這個檢視提供顯示下列欄位之值的表格：</span><span class="sxs-lookup"><span data-stu-id="2115c-107">This view provides a table showing the values for the following fields:</span></span>  
  
-   <span data-ttu-id="2115c-108">傳送者合作對象識別碼</span><span class="sxs-lookup"><span data-stu-id="2115c-108">Sender party ID</span></span>  
  
-   <span data-ttu-id="2115c-109">接收者合作對象識別碼</span><span class="sxs-lookup"><span data-stu-id="2115c-109">Receiver party ID</span></span>  
  
-   <span data-ttu-id="2115c-110">控制項 ID</span><span class="sxs-lookup"><span data-stu-id="2115c-110">Control ID</span></span>  
  
-   <span data-ttu-id="2115c-111">接收者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="2115c-111">Receiver party name</span></span>  
  
-   <span data-ttu-id="2115c-112">傳送者合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="2115c-112">Sender party name</span></span>  
  
-   <span data-ttu-id="2115c-113">方向</span><span class="sxs-lookup"><span data-stu-id="2115c-113">Direction</span></span>  
  
-   <span data-ttu-id="2115c-114">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="2115c-114">Interchange Date Time</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2115c-115">接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。</span><span class="sxs-lookup"><span data-stu-id="2115c-115">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="2115c-116">如果日期為少於 75 台，它會顯示為 20YY。</span><span class="sxs-lookup"><span data-stu-id="2115c-116">If the date is less than 75, it will be displayed as 20YY.</span></span>  
    >   
    >  <span data-ttu-id="2115c-117">例如，如果您收到包含值 991113 中 isa09-交換，交換日期會列入報表中為 11/13/1999年。</span><span class="sxs-lookup"><span data-stu-id="2115c-117">For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date will be listed in the report as 11/13/1999.</span></span>  
  
-   <span data-ttu-id="2115c-118">群組計數</span><span class="sxs-lookup"><span data-stu-id="2115c-118">Group count</span></span>  
  
-   <span data-ttu-id="2115c-119">連接埠識別碼</span><span class="sxs-lookup"><span data-stu-id="2115c-119">Port ID</span></span>  
  
-   <span data-ttu-id="2115c-120">交換狀態</span><span class="sxs-lookup"><span data-stu-id="2115c-120">Interchange Status</span></span>  
  
-   <span data-ttu-id="2115c-121">EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="2115c-121">EDI encoding type</span></span>  
  
-   <span data-ttu-id="2115c-122">交易集合相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="2115c-122">Transaction Set Correlation Id</span></span>  
  
 <span data-ttu-id="2115c-123">如果做為交換接收者的合作對象已經啟用技術通知 (在 [EDI 屬性] 對話方塊的 [通知處理和驗證設定] 頁面中)，BizTalk Server 便會期待收到可回應其傳送之交換而傳回的技術 (交換) 通知。</span><span class="sxs-lookup"><span data-stu-id="2115c-123">If a technical acknowledgment is enabled for a party as an interchange receiver (in the ACK Processing and Validation Settings page of the EDI Properties dialog box), BizTalk Server expects a technical (interchange) acknowledgment to be returned in response to an interchange that it sends.</span></span> <span data-ttu-id="2115c-124">一開始在建立輸出交換的交換狀態項目時，BizTalk Server 會在 [交換狀態] 欄位中輸入「預期通知」。</span><span class="sxs-lookup"><span data-stu-id="2115c-124">When it initially creates an interchange status entry for an outbound interchange, it will enter ACK Expected in the Interchange Status field.</span></span> <span data-ttu-id="2115c-125">當它收到技術通知，並使其與原始的交換相互關聯時，便會更新 [交換狀態] 欄位，以表示它已經收到通知。</span><span class="sxs-lookup"><span data-stu-id="2115c-125">When it receives a technical acknowledgment and correlates it to the original interchange, it will update the Interchange Status field to indicate that it has received the acknowledgment.</span></span>  
  
## <a name="interchange-ack-status"></a><span data-ttu-id="2115c-126">交換通知狀態</span><span class="sxs-lookup"><span data-stu-id="2115c-126">Interchange Ack Status</span></span>  
 <span data-ttu-id="2115c-127">這個檢視會顯示交換 (技術) 通知的狀態值。</span><span class="sxs-lookup"><span data-stu-id="2115c-127">This view displays status values for an interchange (technical) acknowledgment:</span></span>  
  
-   <span data-ttu-id="2115c-128">通知交換控制項 ID</span><span class="sxs-lookup"><span data-stu-id="2115c-128">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="2115c-129">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="2115c-129">Receiver party</span></span>  
  
-   <span data-ttu-id="2115c-130">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="2115c-130">Sender party</span></span>  
  
-   <span data-ttu-id="2115c-131">方向</span><span class="sxs-lookup"><span data-stu-id="2115c-131">Direction</span></span>  
  
-   <span data-ttu-id="2115c-132">通知交換日期</span><span class="sxs-lookup"><span data-stu-id="2115c-132">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="2115c-133">通知交換時間</span><span class="sxs-lookup"><span data-stu-id="2115c-133">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="2115c-134">通知狀態</span><span class="sxs-lookup"><span data-stu-id="2115c-134">Ack Status</span></span>  
  
-   <span data-ttu-id="2115c-135">狀態碼</span><span class="sxs-lookup"><span data-stu-id="2115c-135">Status Code</span></span>  
  
-   <span data-ttu-id="2115c-136">通知說明碼 1</span><span class="sxs-lookup"><span data-stu-id="2115c-136">Ack Note Code1</span></span>  
  
-   <span data-ttu-id="2115c-137">通知說明碼 2</span><span class="sxs-lookup"><span data-stu-id="2115c-137">Ack Note Code2</span></span>  
  
## <a name="functional-acks"></a><span data-ttu-id="2115c-138">功能通知</span><span class="sxs-lookup"><span data-stu-id="2115c-138">Functional Ack(s)</span></span>  
 <span data-ttu-id="2115c-139">這個檢視會顯示功能通知的狀態值。</span><span class="sxs-lookup"><span data-stu-id="2115c-139">This view displays status values for an functional acknowledgment:</span></span>  
  
-   <span data-ttu-id="2115c-140">群組控制編號</span><span class="sxs-lookup"><span data-stu-id="2115c-140">Group Control Number</span></span>  
  
-   <span data-ttu-id="2115c-141">接收者合作對象</span><span class="sxs-lookup"><span data-stu-id="2115c-141">Receiver party</span></span>  
  
-   <span data-ttu-id="2115c-142">傳送者合作對象</span><span class="sxs-lookup"><span data-stu-id="2115c-142">Sender party</span></span>  
  
-   <span data-ttu-id="2115c-143">方向</span><span class="sxs-lookup"><span data-stu-id="2115c-143">Direction</span></span>  
  
-   <span data-ttu-id="2115c-144">狀態</span><span class="sxs-lookup"><span data-stu-id="2115c-144">Status</span></span>  
  
-   <span data-ttu-id="2115c-145">狀態碼</span><span class="sxs-lookup"><span data-stu-id="2115c-145">Status Code</span></span>  
  
-   <span data-ttu-id="2115c-146">功能識別項程式碼</span><span class="sxs-lookup"><span data-stu-id="2115c-146">Functional ID Code</span></span>  
  
-   <span data-ttu-id="2115c-147">TS 計數</span><span class="sxs-lookup"><span data-stu-id="2115c-147">TS Count</span></span>  
  
-   <span data-ttu-id="2115c-148">通知交換控制項 ID</span><span class="sxs-lookup"><span data-stu-id="2115c-148">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="2115c-149">通知交換日期</span><span class="sxs-lookup"><span data-stu-id="2115c-149">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="2115c-150">通知交換時間</span><span class="sxs-lookup"><span data-stu-id="2115c-150">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="2115c-151">已傳遞 TS 計數</span><span class="sxs-lookup"><span data-stu-id="2115c-151">Delivered TS Count</span></span>  
  
-   <span data-ttu-id="2115c-152">已接受 TS 計數</span><span class="sxs-lookup"><span data-stu-id="2115c-152">Accepted TS Count</span></span>  
  
-   <span data-ttu-id="2115c-153">ErrorCode 1</span><span class="sxs-lookup"><span data-stu-id="2115c-153">ErrorCode 1</span></span>  
  
-   <span data-ttu-id="2115c-154">ErrorCode 2</span><span class="sxs-lookup"><span data-stu-id="2115c-154">ErrorCode 2</span></span>  
  
-   <span data-ttu-id="2115c-155">ErrorCode 3</span><span class="sxs-lookup"><span data-stu-id="2115c-155">ErrorCode 3</span></span>  
  
-   <span data-ttu-id="2115c-156">ErrorCode 4</span><span class="sxs-lookup"><span data-stu-id="2115c-156">ErrorCode 4</span></span>  
  
-   <span data-ttu-id="2115c-157">錯誤碼 5</span><span class="sxs-lookup"><span data-stu-id="2115c-157">ErrorCode 5</span></span>  
  
-   <span data-ttu-id="2115c-158">接收時間</span><span class="sxs-lookup"><span data-stu-id="2115c-158">Time Received</span></span>