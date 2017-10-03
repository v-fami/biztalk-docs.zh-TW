---
title: "儲存的批次狀態報告資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d55aa0e1-095f-434e-8530-f1a946ad4430
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db9831aafce56845fe7b75e91f5369a8860d8996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-batching-status-reports"></a><span data-ttu-id="19e78-102">批次狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="19e78-102">Data Stored for Batching Status Reports</span></span>
<span data-ttu-id="19e78-103">當**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存每個批次的執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="19e78-103">When the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the status of each batching instance.</span></span> <span data-ttu-id="19e78-104">這個屬性是在用於**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="19e78-104">This property is in available in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="19e78-105">這個狀態可以是下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="19e78-105">The status can be any of the following:</span></span>  
  
-   <span data-ttu-id="19e78-106">**定義**： 批次的執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="19e78-106">**Defined**: The batch instance is configured.</span></span> <span data-ttu-id="19e78-107">批次啟動開始日期時間大於目前日期時間。</span><span class="sxs-lookup"><span data-stu-id="19e78-107">The batch activation start date time is greater than the current date time.</span></span> <span data-ttu-id="19e78-108">所有批次參數都已定義，但是批次未執行 (不接受文件)。</span><span class="sxs-lookup"><span data-stu-id="19e78-108">All batch parameters are defined, but the batch is not running (not accepting documents).</span></span>  
  
-   <span data-ttu-id="19e78-109">**Active**： 批次的執行個體已啟動且正在彙總交易集。</span><span class="sxs-lookup"><span data-stu-id="19e78-109">**Active**: The batch instance has been activated and is aggregating transaction sets.</span></span> <span data-ttu-id="19e78-110">您可以檢視已接受/已拒絕的交易集數目。</span><span class="sxs-lookup"><span data-stu-id="19e78-110">You can view the number of accepted/rejected transaction sets.</span></span>  
  
-   <span data-ttu-id="19e78-111">**釋放**： 批次符合釋放準則和已釋放至 MessageBox，但尚未由傳送管線，釋出或處理任何訊息之前，先停止批次。</span><span class="sxs-lookup"><span data-stu-id="19e78-111">**Released**: The batch met the release criteria and was released into the MessageBox, but has not been released by the send pipeline, or that the batch was stopped before processing any messages.</span></span>  
  
-   <span data-ttu-id="19e78-112">**完成**: 批次已由 EdiSend 管線傳送。</span><span class="sxs-lookup"><span data-stu-id="19e78-112">**Completed**: The batch was sent by the EdiSend pipeline.</span></span>  
  
 <span data-ttu-id="19e78-113">如果批次已由 EdiSend 管線傳送，您可以將 UI 中的批次記錄與所傳送 Edi 交換的記錄相互關聯，然後檢視交易集詳細資料。</span><span class="sxs-lookup"><span data-stu-id="19e78-113">If the batch was sent by the EdiSend pipeline, you can correlate the batch record in the UI with a record of the sent Edi interchange, and view transaction set details.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e78-114">批次組態可能有多個「已完成」狀態的批次執行個體。</span><span class="sxs-lookup"><span data-stu-id="19e78-114">There may be multiple batch instances with a status of Completed for a batch configuration.</span></span>  
  
 <span data-ttu-id="19e78-115">**與批次的交換相互關聯**</span><span class="sxs-lookup"><span data-stu-id="19e78-115">**Correlating an Interchange with a Batch**</span></span>  
  
 <span data-ttu-id="19e78-116">BusinessMessageJournal BAM 活動可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將包含交易集的已接收 EDI 交換，與包含同一個交易集的外寄批次交換產生相互關聯。</span><span class="sxs-lookup"><span data-stu-id="19e78-116">The BusinessMessageJournal BAM activity enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to correlate a received EDI interchange containing a transaction set with an outgoing batched interchange that contains the same transaction set.</span></span> <span data-ttu-id="19e78-117">如需如何實作及使用此相互關聯資訊，請參閱[相互關聯的內送交易集與外寄批次](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="19e78-117">For information about how to implement and use this correlation information, see [Correlating an Incoming Transaction Set with an Outgoing Batch](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e78-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19e78-118">See Also</span></span>  
 <span data-ttu-id="19e78-119">[EDI 和 AS2 狀態報告的儲存資料](../core/data-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="19e78-119">[Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md) </span></span>  
 <span data-ttu-id="19e78-120">[EDI 狀態報告的儲存資料](../core/data-stored-for-edi-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="19e78-120">[Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md) </span></span>  
 [<span data-ttu-id="19e78-121">AS2 狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="19e78-121">Data Stored for AS2 Status Reports</span></span>](../core/data-stored-for-as2-status-reports.md)