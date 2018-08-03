---
title: 如何搜尋執行中服務執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, viewing
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- service instances, running
ms.assetid: fc65bf33-c013-4e6a-b9fd-b4536811e7b4
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c61b94b440810fc948ae7e9e51c1897204d28c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023932"
---
# <a name="how-to-search-for-running-service-instances"></a><span data-ttu-id="a44d3-102">如何搜尋執行中的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="a44d3-102">How to Search for Running Service Instances</span></span>
<span data-ttu-id="a44d3-103">您可以使用**查詢** 索引標籤來搜尋特定 BizTalk Server 管理主控台中的已凍結、 作用中、 在中斷點、 已排程，以及重試服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44d3-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific dehydrated, active, in breakpoint, scheduled, and retrying service instance.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="a44d3-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="a44d3-104">Prerequisites</span></span>  
 <span data-ttu-id="a44d3-105">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="a44d3-105">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  

### <a name="to-search-for-running-service-instances"></a><span data-ttu-id="a44d3-106">搜尋執行中的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="a44d3-106">To search for running service instances</span></span>  

1. <span data-ttu-id="a44d3-107">按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a44d3-107">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="a44d3-108">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="a44d3-108">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  

3. <span data-ttu-id="a44d3-109">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a44d3-109">In the details pane, click the **New Query** tab.</span></span>  

4. <span data-ttu-id="a44d3-110">在 **查詢運算式**群組中**值**欄中，選取**執行的服務執行個體**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="a44d3-110">In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.</span></span>  

5. <span data-ttu-id="a44d3-111">在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (\* *\\* \* \*)，選取一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="a44d3-111">In the **Field Name** column, in the empty drop-down list box next to the asterisk (\*\*\\*\*\*), select one or more of the following:</span></span>  


   |          <span data-ttu-id="a44d3-112">項目</span><span class="sxs-lookup"><span data-stu-id="a44d3-112">Item</span></span>          |                                                             <span data-ttu-id="a44d3-113">描述</span><span class="sxs-lookup"><span data-stu-id="a44d3-113">Description</span></span>                                                             |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
   |  <span data-ttu-id="a44d3-114">**Application Name**</span><span class="sxs-lookup"><span data-stu-id="a44d3-114">**Application Name**</span></span>  |                                                   <span data-ttu-id="a44d3-115">BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a44d3-115">The BizTalk Server application.</span></span>                                                   |
   |   <span data-ttu-id="a44d3-116">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="a44d3-116">**Creation Time**</span></span>    |                             <span data-ttu-id="a44d3-117">尋找指定日期前後建立的執行中服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44d3-117">Find running service instances created before or after the specified date.</span></span>                              |
   |  <span data-ttu-id="a44d3-118">**將結果分組**</span><span class="sxs-lookup"><span data-stu-id="a44d3-118">**Group Results By**</span></span>  |  <span data-ttu-id="a44d3-119">您可以依據應用程式、主控件名稱、擱置作業的類型、服務類別、服務執行個體狀態或服務名稱來群組結果。</span><span class="sxs-lookup"><span data-stu-id="a44d3-119">You can group results by application, host name, pending operation type, service class, service instance status, or service name.</span></span>  |
   |     <span data-ttu-id="a44d3-120">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="a44d3-120">**Host Name**</span></span>      |                                                    <span data-ttu-id="a44d3-121">BizTalk 主控件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a44d3-121">The name of the BizTalk Host.</span></span>                                                    |
   |  <span data-ttu-id="a44d3-122">**執行個體狀態**</span><span class="sxs-lookup"><span data-stu-id="a44d3-122">**Instance Status**</span></span>   |             <span data-ttu-id="a44d3-123">您可以搜尋作用中的執行個體、已凍結的執行個體、準備執行的執行個體、已排程的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44d3-123">You can search for active instances, dehydrated instances, ready to run instances, and scheduled instances.</span></span>             |
   |  <span data-ttu-id="a44d3-124">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="a44d3-124">**Maximum Matches**</span></span>   |                                                  <span data-ttu-id="a44d3-125">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="a44d3-125">The number of matches to display.</span></span>                                                  |
   | <span data-ttu-id="a44d3-126">**暫止的作業**</span><span class="sxs-lookup"><span data-stu-id="a44d3-126">**Pending Operations**</span></span> |                      <span data-ttu-id="a44d3-127">您可以搜尋目前擱置或終止的執行中服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44d3-127">You can search for running service instances that are pending suspension or termination.</span></span>                       |
   |   <span data-ttu-id="a44d3-128">**服務類別**</span><span class="sxs-lookup"><span data-stu-id="a44d3-128">**Service Class**</span></span>    | <span data-ttu-id="a44d3-129">您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。</span><span class="sxs-lookup"><span data-stu-id="a44d3-129">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span> |
   |    <span data-ttu-id="a44d3-130">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="a44d3-130">**Service Name**</span></span>    |                                 <span data-ttu-id="a44d3-131">您可以依服務名稱來群組或篩選執行中的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44d3-131">You can group or filter running service instances by service name.</span></span>                                  |
   |  <span data-ttu-id="a44d3-132">**服務類型識別碼**</span><span class="sxs-lookup"><span data-stu-id="a44d3-132">**Service Type ID**</span></span>   |                                        <span data-ttu-id="a44d3-133">您可以使用服務類型識別碼來分組或篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="a44d3-133">You can group or filter messages by service type ID.</span></span>                                         |


6. <span data-ttu-id="a44d3-134">完成**值**適當選取您在中所做的資料行**欄位名**資料行。</span><span class="sxs-lookup"><span data-stu-id="a44d3-134">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  

7. <span data-ttu-id="a44d3-135">繼續新增其他行至視需要查詢中，藉由完成**欄位名**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="a44d3-135">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a44d3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a44d3-136">See Also</span></span>  
 [<span data-ttu-id="a44d3-137">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="a44d3-137">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)