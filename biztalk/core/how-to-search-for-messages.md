---
title: "如何搜尋訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, viewing
- messages, searching
- Query tab [Administration Console], searching
- Query tab [Administration Console], messages
ms.assetid: c751d23f-913a-4325-81da-a36d61c07e8b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5443cc021bd5f97621f44d295432c99834bdaed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-messages"></a><span data-ttu-id="9e1de-102">如何搜尋訊息</span><span class="sxs-lookup"><span data-stu-id="9e1de-102">How to Search for Messages</span></span>
<span data-ttu-id="9e1de-103">您可以使用**查詢**中要搜尋特定類別的訊息 [BizTalk Server 管理主控台] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9e1de-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific class of messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9e1de-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="9e1de-104">Prerequisites</span></span>  
 <span data-ttu-id="9e1de-105">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="9e1de-105">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-messages"></a><span data-ttu-id="9e1de-106">搜尋訊息</span><span class="sxs-lookup"><span data-stu-id="9e1de-106">To search for messages</span></span>  
  
1.  <span data-ttu-id="9e1de-107">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9e1de-107">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9e1de-108">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="9e1de-108">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="9e1de-109">在 詳細資料 窗格中，按一下**新查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9e1de-109">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="9e1de-110">在**查詢運算式**群組中**值**欄中，選取**訊息**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="9e1de-110">In the **Query Expression** group, in the **Value** column, select **Messages** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="9e1de-111">在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，選取一個或多個項目：</span><span class="sxs-lookup"><span data-stu-id="9e1de-111">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="9e1de-112">項目</span><span class="sxs-lookup"><span data-stu-id="9e1de-112">Item</span></span>|<span data-ttu-id="9e1de-113">Description</span><span class="sxs-lookup"><span data-stu-id="9e1de-113">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="9e1de-114">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="9e1de-114">**Creation Time**</span></span>|<span data-ttu-id="9e1de-115">尋找在指定的日期之前或之後建立的訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-115">Find messages created before or after the specified date.</span></span>|  
    |<span data-ttu-id="9e1de-116">**錯誤配接器**</span><span class="sxs-lookup"><span data-stu-id="9e1de-116">**Error Adapter**</span></span>|<span data-ttu-id="9e1de-117">您可以分組或篩選訊息，配接器類型： 檔案、 FTP、 HTTP、 MQSeries、 MSMQ、 POP3、 SMTP、 SOAP 或 Windows SharePoint Services。</span><span class="sxs-lookup"><span data-stu-id="9e1de-117">You can group or filter messages by adapter type: FILE, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP, or Windows SharePoint Services.</span></span>|  
    |<span data-ttu-id="9e1de-118">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="9e1de-118">**Error Code**</span></span>|<span data-ttu-id="9e1de-119">您可以使用錯誤碼來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-119">You can group or filter messages by error code.</span></span>|  
    |<span data-ttu-id="9e1de-120">**錯誤描述**</span><span class="sxs-lookup"><span data-stu-id="9e1de-120">**Error Description**</span></span>|<span data-ttu-id="9e1de-121">您可以使用錯誤描述來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-121">You can group or filter messages by error description.</span></span>|  
    |<span data-ttu-id="9e1de-122">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="9e1de-122">**Host Name**</span></span>|<span data-ttu-id="9e1de-123">您可以使用主控件名稱來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-123">You can group or filter messages by host name.</span></span>|  
    |<span data-ttu-id="9e1de-124">**執行個體狀態**</span><span class="sxs-lookup"><span data-stu-id="9e1de-124">**Instance Status**</span></span>|<span data-ttu-id="9e1de-125">參考訊息的服務執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e1de-125">The status of the service instance referencing the message.</span></span> <span data-ttu-id="9e1de-126">您可以搜尋下列所有類型的執行個體：所有執行中的執行個體、所有擱置的執行個體、作用中的執行個體、已凍結的執行個體、準備執行的執行個體、已排程的執行個體、已擱置但不可繼續的執行個體，或已擱置但可以繼續的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e1de-126">You can search for all of the following types of instances: all running instances, all suspended instances, active instances, dehydrated instances, ready-to-run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances.</span></span>|  
    |<span data-ttu-id="9e1de-127">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="9e1de-127">**Maximum Matches**</span></span>|<span data-ttu-id="9e1de-128">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="9e1de-128">The number of matches to display.</span></span>|  
    |<span data-ttu-id="9e1de-129">**訊息識別碼**</span><span class="sxs-lookup"><span data-stu-id="9e1de-129">**Message ID**</span></span>|<span data-ttu-id="9e1de-130">您可以使用訊息識別碼來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-130">You can group or filter messages by message ID.</span></span>|  
    |<span data-ttu-id="9e1de-131">**訊息狀態**</span><span class="sxs-lookup"><span data-stu-id="9e1de-131">**Message Status**</span></span>|<span data-ttu-id="9e1de-132">您可以搜尋狀態為已使用、進行中、已擱置、已擱置但不可繼續、已擱置且可以繼續、已佇列、已佇列但等候處理、已佇列但已排程稍後傳遞，以及已佇列但等候重試的訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-132">You can search for messages with consumed, in process, suspended, suspended but not resumable, suspended and resumable, queued, queued but awaiting processing, queued but scheduled for later delivery, and queued but waiting to retry.</span></span>|  
    |<span data-ttu-id="9e1de-133">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="9e1de-133">**Message Type**</span></span>|<span data-ttu-id="9e1de-134">您可以使用訊息類型來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-134">You can group or filter messages by message type.</span></span>|  
    |<span data-ttu-id="9e1de-135">**服務類別**</span><span class="sxs-lookup"><span data-stu-id="9e1de-135">**Service Class**</span></span>|<span data-ttu-id="9e1de-136">您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。</span><span class="sxs-lookup"><span data-stu-id="9e1de-136">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>|  
    |<span data-ttu-id="9e1de-137">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="9e1de-137">**Service Instance ID**</span></span>|<span data-ttu-id="9e1de-138">您可以使用服務執行個體識別碼來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-138">You can group or filter messages by service instance ID.</span></span>|  
    |<span data-ttu-id="9e1de-139">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="9e1de-139">**Service Name**</span></span>|<span data-ttu-id="9e1de-140">您可以使用服務名稱來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-140">You can group or filter messages by service name.</span></span>|  
    |<span data-ttu-id="9e1de-141">**服務類型識別碼**</span><span class="sxs-lookup"><span data-stu-id="9e1de-141">**Service Type ID**</span></span>|<span data-ttu-id="9e1de-142">您可以使用服務類型識別碼來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-142">You can group or filter messages by service type ID.</span></span>|  
    |<span data-ttu-id="9e1de-143">**URI**</span><span class="sxs-lookup"><span data-stu-id="9e1de-143">**URI**</span></span>|<span data-ttu-id="9e1de-144">您可以使用 URI 來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="9e1de-144">You can group or filter messages by URI.</span></span>|  
  
6.  <span data-ttu-id="9e1de-145">完成**值**適用於選取項目所做的資料行**欄位名稱**資料行。</span><span class="sxs-lookup"><span data-stu-id="9e1de-145">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="9e1de-146">繼續新增其他行至視需要查詢，藉由完成**欄位名稱**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="9e1de-146">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1de-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e1de-147">See Also</span></span>  
 [<span data-ttu-id="9e1de-148">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="9e1de-148">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)