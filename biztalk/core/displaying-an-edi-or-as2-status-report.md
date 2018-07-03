---
title: 顯示 EDI 或 AS2 狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60968c3d-6329-411f-9f10-1dd4a6cc9d79
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a729e089c3d833d7bf8d8b87ebabeec0743b358a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018632"
---
# <a name="displaying-an-edi-or-as2-status-report"></a><span data-ttu-id="9c951-102">顯示 EDI 或 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="9c951-102">Displaying an EDI or AS2 Status Report</span></span>
<span data-ttu-id="9c951-103">啟用 EDI 和 AS2 狀態報告時，您可以存取下列狀態報告：</span><span class="sxs-lookup"><span data-stu-id="9c951-103">When EDI and AS2 status reports are enabled, you will have access to the following status reports:</span></span>  
  
|<span data-ttu-id="9c951-104">報告類型</span><span class="sxs-lookup"><span data-stu-id="9c951-104">Type of Report</span></span>|<span data-ttu-id="9c951-105">上層狀態報告</span><span class="sxs-lookup"><span data-stu-id="9c951-105">Higher-level status report</span></span>|<span data-ttu-id="9c951-106">下層狀態報告</span><span class="sxs-lookup"><span data-stu-id="9c951-106">Lower-level status report</span></span>|  
|--------------------|---------------------------------|--------------------------------|  
|<span data-ttu-id="9c951-107">EDI</span><span class="sxs-lookup"><span data-stu-id="9c951-107">EDI</span></span>|<span data-ttu-id="9c951-108">EDI 交換和相互關聯的 ACK 狀態</span><span class="sxs-lookup"><span data-stu-id="9c951-108">EDI Interchange and Correlated ACK Status</span></span>|<span data-ttu-id="9c951-109">-交換狀態和通知詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c951-109">- Interchange Status and ACK Details</span></span><br /><br /> <span data-ttu-id="9c951-110">交易集詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c951-110">- Transaction Set Details</span></span><br /><br /> <span data-ttu-id="9c951-111">EDI 訊息內容</span><span class="sxs-lookup"><span data-stu-id="9c951-111">- EDI Message Content</span></span>|  
|<span data-ttu-id="9c951-112">EDI</span><span class="sxs-lookup"><span data-stu-id="9c951-112">EDI</span></span>|<span data-ttu-id="9c951-113">批次狀態</span><span class="sxs-lookup"><span data-stu-id="9c951-113">Batch Status</span></span>|-|  
|<span data-ttu-id="9c951-114">EDI</span><span class="sxs-lookup"><span data-stu-id="9c951-114">EDI</span></span>|<span data-ttu-id="9c951-115">交換彙總報告</span><span class="sxs-lookup"><span data-stu-id="9c951-115">Interchange Aggregation Report</span></span>|-|  
|<span data-ttu-id="9c951-116">EDI</span><span class="sxs-lookup"><span data-stu-id="9c951-116">EDI</span></span>|<span data-ttu-id="9c951-117">交易集彙總報告</span><span class="sxs-lookup"><span data-stu-id="9c951-117">Transaction Set Aggregation Report</span></span>|-|  
|<span data-ttu-id="9c951-118">AS2</span><span class="sxs-lookup"><span data-stu-id="9c951-118">AS2</span></span>|<span data-ttu-id="9c951-119">AS2 訊息和相互關聯的 MDN 狀態</span><span class="sxs-lookup"><span data-stu-id="9c951-119">AS2 Message and Correlated MDN Status</span></span>|<span data-ttu-id="9c951-120">AS2 訊息內容</span><span class="sxs-lookup"><span data-stu-id="9c951-120">AS2 Message Content</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="9c951-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="9c951-121">Prerequisites</span></span>  
 <span data-ttu-id="9c951-122">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="9c951-122">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
- <span data-ttu-id="9c951-123">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員群組的成員身分登入，才能自訂任何狀態報告。</span><span class="sxs-lookup"><span data-stu-id="9c951-123">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to customize any of the status reports.</span></span>  
  
- <span data-ttu-id="9c951-124">如果以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組的成員身分登入，則只能顯示唯讀狀態報告。</span><span class="sxs-lookup"><span data-stu-id="9c951-124">If you are logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, you can display read-only status reports.</span></span>  
  
## <a name="display-an-edi-or-as2-status-report"></a><span data-ttu-id="9c951-125">顯示 EDI 或 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="9c951-125">Display an EDI or AS2 status report</span></span>  
  
1. <span data-ttu-id="9c951-126">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**BizTalk 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="9c951-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node.</span></span>  
  
2. <span data-ttu-id="9c951-127">在 **群組中樞**索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，移至頁面底部。</span><span class="sxs-lookup"><span data-stu-id="9c951-127">In the **Group Hub** tab of the **Group Overview** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, move to the bottom of the page.</span></span>  
  
3. <span data-ttu-id="9c951-128">若要顯示**EDI 交換和相互關聯的 ACK 狀態**報告，請執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c951-128">To display the **EDI Interchange and Correlated ACK Status** report, proceed as follows:</span></span>  
  
   1.  <span data-ttu-id="9c951-129">按一下 [ **EDI 交換和相互關聯的 ACK 狀態**中**EDI 狀態報告**區域**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c951-129">Click **EDI Interchange and Correlated ACK Status** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
   2.  <span data-ttu-id="9c951-130">若要顯示某個交換及其相互關聯的通知的詳細資訊，請以滑鼠右鍵按一下查詢結果中的項目**EDI 交換和相互關聯的 ACK 狀態**報告，，然後按一下 **交換狀態和通知詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="9c951-130">To display details of an interchange and its correlated acknowledgments, right-click an entry in the query results of the **EDI Interchange and Correlated ACK Status** report, and then click **Interchange status and ack details**.</span></span>  
  
   3.  <span data-ttu-id="9c951-131">若要顯示交易集的詳細資訊，請關閉 交換狀態和通知詳細資料報告，回到**EDI 交換和相互關聯的 ACK 狀態**詳細資料報表。</span><span class="sxs-lookup"><span data-stu-id="9c951-131">To display details of a transaction set, close the Interchange status and ack details report, returning to the **EDI Interchange and Correlated ACK Status** details report.</span></span> <span data-ttu-id="9c951-132">以滑鼠右鍵按一下查詢結果中的項目，然後按一下**交易集詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="9c951-132">Right-click an entry in the query results, and then click **Transaction Set Details**.</span></span>  
  
   4.  <span data-ttu-id="9c951-133">若要顯示的標頭和承載的交易集的詳細資訊，請以滑鼠右鍵按一下中的項目**交易集詳細資料**報告，然後按一下**檢視交易集內容**。</span><span class="sxs-lookup"><span data-stu-id="9c951-133">To display details about the headers and payload of a transaction set, right-click an entry in the **Transaction Set Details** report, and then click **View Transaction Set Content**.</span></span>  
  
   5.  <span data-ttu-id="9c951-134">若要顯示包含交易集之交換的資料，請以滑鼠右鍵按一下中的項目**交易集詳細資料**報告，然後按一下**交換/通知狀態**。</span><span class="sxs-lookup"><span data-stu-id="9c951-134">To display data about the interchange containing the transaction set, right-click an entry in the **Transaction Set Details** report, and then click **Interchange/ACK Status**.</span></span> <span data-ttu-id="9c951-135">包含交易集的交換將會反白顯示在 [交換/通知狀態] 報告中。</span><span class="sxs-lookup"><span data-stu-id="9c951-135">The interchange containing the transaction set will be highlighted in the Interchange/ACK Status report.</span></span>  
  
4. <span data-ttu-id="9c951-136">若要顯示**批次狀態**報告，請執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c951-136">To display the **Batch Status** report, proceed as follows:</span></span>  
  
   1.  <span data-ttu-id="9c951-137">按一下 [**批次狀態**中**EDI 狀態報告**區域**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c951-137">Click **Batch Status** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
   2.  <span data-ttu-id="9c951-138">若要顯示完成的批次中的批次項目相關聯**批次狀態**報告，以滑鼠右鍵按一下項目，然後按一下**已完成批次**。</span><span class="sxs-lookup"><span data-stu-id="9c951-138">To display the completed batches associated with a batch entry in the **Batch Status** report, right-click the entry and then click **Completed Batches**.</span></span>  
  
   3.  <span data-ttu-id="9c951-139">若要顯示已完成的批次交換的資料，請以滑鼠右鍵按一下中的交換**已完成批次**報告，然後按一下**交換/通知狀態**。</span><span class="sxs-lookup"><span data-stu-id="9c951-139">To display data about a completed batched interchange, right-click the interchange in the **Completed Batch** report, and then click **Interchange/ACK Status**.</span></span> <span data-ttu-id="9c951-140">批次交換的項目將會反白顯示在 [交換/通知狀態] 報告中。</span><span class="sxs-lookup"><span data-stu-id="9c951-140">The entry for the batched interchange will be highlighted in the Interchange/ACK Status report.</span></span>  
  
5. <span data-ttu-id="9c951-141">若要顯示**交換彙總報告**，繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c951-141">To display the **Interchange Aggregation Report**, proceed as follows:</span></span>  
  
   -   <span data-ttu-id="9c951-142">按一下 [**交換彙總報告**中**EDI 狀態報告**區域**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c951-142">Click **Interchange Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
6. <span data-ttu-id="9c951-143">若要顯示**交易集彙總報告**，繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c951-143">To display the **Transaction Set Aggregation Report**, proceed as follows:</span></span>  
  
   -   <span data-ttu-id="9c951-144">按一下 [**交易集彙總報告**中**EDI 狀態報告**區域**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c951-144">Click **Transaction Set Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
7. <span data-ttu-id="9c951-145">若要顯示**AS2 訊息和相互關聯的 MDN 狀態**報告，請執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c951-145">To display the **AS2 Message and Correlated MDN Status** report, proceed as follows:</span></span>  
  
   1.  <span data-ttu-id="9c951-146">按一下 [ **AS2 訊息和相互關聯的 MDN 狀態**中**EDIINT 狀態報告**區域**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c951-146">Click **AS2 Message and Correlated MDN Status** in the **EDIINT Status Reports** area of the **Group Hub** tab.</span></span>  
  
   2.  <span data-ttu-id="9c951-147">若要顯示 AS2 訊息中的 EDI 交換的狀態，以滑鼠右鍵按一下中的項目**AS2 訊息和相互關聯的 MDN 狀態**報告，然後按一下**交換/通知狀態**。</span><span class="sxs-lookup"><span data-stu-id="9c951-147">To display the status of the EDI interchange in an AS2 message, right-click an entry in the **AS2 Message and Correlated MDN Status** report, and then click **Interchange/ACK Status**.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="9c951-148">如需有關 EDI 和 AS2 狀態如何相關的詳細資訊，請參閱 「 相互關聯的 AS2 訊息與其 EDI 內容 」 一節[AS2 訊息和相互關聯的 MDN 狀態報告](../core/as2-message-and-correlated-mdn-status-report.md)。</span><span class="sxs-lookup"><span data-stu-id="9c951-148">For more information on how EDI status and AS2 status are correlated, see the "Correlating an AS2 Message with its EDI Payload" section of [AS2 Message and Correlated MDN Status Report](../core/as2-message-and-correlated-mdn-status-report.md).</span></span>  
  
   3.  <span data-ttu-id="9c951-149">若要以電傳格式顯示 AS2 訊息，以滑鼠右鍵按一下 [AS2/MDN 狀態] 報告中中的項目，然後按一下**訊息電傳格式**。</span><span class="sxs-lookup"><span data-stu-id="9c951-149">To display an AS2 message in wire format, right-click an entry in the AS2/MDN Status report, and then click **Message Wire Format**.</span></span>  
  
   4.  <span data-ttu-id="9c951-150">解碼格式顯示 AS2 訊息，以滑鼠右鍵按一下 [AS2/MDN 狀態] 報告中中的項目，然後按一下**訊息解碼格式**。</span><span class="sxs-lookup"><span data-stu-id="9c951-150">To display an AS2 message in decoded format, right-click an entry in the AS2/MDN Status report, and then click **Message Decoded Format**.</span></span>  
  
   5.  <span data-ttu-id="9c951-151">若要顯示 MDN 訊息，以滑鼠右鍵按一下 AS2/MDN 狀態 報告中中的項目，然後按一下  **Mdn 訊息**。</span><span class="sxs-lookup"><span data-stu-id="9c951-151">To display an MDN message, right-click an entry in the AS2/MDN Status report, and then click **Mdn Message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c951-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c951-152">See Also</span></span>  
 <span data-ttu-id="9c951-153">[監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="9c951-153">[Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="9c951-154">[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md) </span><span class="sxs-lookup"><span data-stu-id="9c951-154">[EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md) </span></span>  
 <span data-ttu-id="9c951-155">[啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9c951-155">[Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="9c951-156">設定 EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="9c951-156">Configuring an EDI and AS2 Status Report</span></span>](../core/configuring-an-edi-and-as2-status-report.md)