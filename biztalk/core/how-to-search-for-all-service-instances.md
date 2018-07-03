---
title: 如何搜尋所有服務執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- instances, services
ms.assetid: 48cb885c-aaf1-44e8-9810-2e70cf63db81
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2a9193633b111d9a75e2c695017c880e924058e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013751"
---
# <a name="how-to-search-for-all-service-instances"></a><span data-ttu-id="ae1db-102">如何搜尋所有服務執行個體</span><span class="sxs-lookup"><span data-stu-id="ae1db-102">How to Search for All Service Instances</span></span>
<span data-ttu-id="ae1db-103">您可以使用**查詢** 索引標籤，在 BizTalk Server 管理主控台，來搜尋所有服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for all service instances.</span></span> <span data-ttu-id="ae1db-104">若有任何執行中或擱置的執行個體，就無法取消登錄特定服務類型。</span><span class="sxs-lookup"><span data-stu-id="ae1db-104">You cannot unenlist a specific service type if there are any running or suspended instances.</span></span> <span data-ttu-id="ae1db-105">例如，取消登錄特定服務類型之前，可以搜尋所有的服務執行個體，以確保沒有執行中或擱置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-105">For example, before you can unenlist a specific service type, you can search for all service instances to ensure that there are no running or suspended instances.</span></span>  

> [!NOTE]
>  <span data-ttu-id="ae1db-106">URI 建立群組和篩選時，結果中僅會顯示傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="ae1db-106">When Grouping and Filtering by URI, only send and receive ports are displayed in the results.</span></span> <span data-ttu-id="ae1db-107">URI 建立群組和篩選並不適用協調流程，因為協調流程不包含在顯示的結果內。</span><span class="sxs-lookup"><span data-stu-id="ae1db-107">Grouping and Filtering by URI is not possible for orchestrations, which are not included in the displayed results.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="ae1db-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="ae1db-108">Prerequisites</span></span>  
 <span data-ttu-id="ae1db-109">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="ae1db-109">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  

### <a name="to-search-for-all-service-instances"></a><span data-ttu-id="ae1db-110">搜尋所有服務執行個體</span><span class="sxs-lookup"><span data-stu-id="ae1db-110">To search for all service instances</span></span>  

1. <span data-ttu-id="ae1db-111">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ae1db-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="ae1db-112">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="ae1db-112">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  

3. <span data-ttu-id="ae1db-113">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ae1db-113">In the details pane, click the **New Query** tab.</span></span>  

4. <span data-ttu-id="ae1db-114">在 **查詢運算式**群組中**值**欄中，選取**所有進行中服務執行個體**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="ae1db-114">In the **Query Expression** group, in the **Value** column, select **All In-Progress Service Instances** from the drop-down list box.</span></span>  

5. <span data-ttu-id="ae1db-115">在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (\* *\\* \* \*)，選取一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="ae1db-115">In the **Field Name** column, in the empty drop-down list box next to the asterisk (\*\*\\*\*\*), select one or more of the following:</span></span>  


   |        <span data-ttu-id="ae1db-116">使用</span><span class="sxs-lookup"><span data-stu-id="ae1db-116">Use this</span></span>         |                                                                                                              <span data-ttu-id="ae1db-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="ae1db-117">To do this</span></span>                                                                                                              |
   |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  <span data-ttu-id="ae1db-118">**Application Name**</span><span class="sxs-lookup"><span data-stu-id="ae1db-118">**Application Name**</span></span>   |                                                                                                   <span data-ttu-id="ae1db-119">BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae1db-119">The BizTalk Server application.</span></span>                                                                                                    |
   |    <span data-ttu-id="ae1db-120">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="ae1db-120">**Creation Time**</span></span>    |                                                                                <span data-ttu-id="ae1db-121">尋找指定日期前後建立的所有服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-121">Find all service instances created before or after the specified date.</span></span>                                                                                |
   |  <span data-ttu-id="ae1db-122">**將結果分組**</span><span class="sxs-lookup"><span data-stu-id="ae1db-122">**Group Results By**</span></span>   |                                                              <span data-ttu-id="ae1db-123">您可以依據應用程式、主控件名稱、服務類別、服務執行個體狀態或服務名稱來群組結果。</span><span class="sxs-lookup"><span data-stu-id="ae1db-123">You can group results by application, host name, service class, service instance status, or service name.</span></span>                                                               |
   |      <span data-ttu-id="ae1db-124">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="ae1db-124">**Host Name**</span></span>      |                                                                                                    <span data-ttu-id="ae1db-125">BizTalk 主控件的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae1db-125">The name of the BizTalk Host.</span></span>                                                                                                     |
   |   <span data-ttu-id="ae1db-126">**執行個體狀態**</span><span class="sxs-lookup"><span data-stu-id="ae1db-126">**Instance Status**</span></span>   | <span data-ttu-id="ae1db-127">您可以搜尋所有正在執行的執行個體、所有擱置的執行個體、作用中的執行個體、凍結的執行個體、準備執行的執行個體、已排程的執行個體、已擱置但不可繼續的執行個體，或是已擱置但可以繼續的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-127">You can search for all running instances, all suspended instances, active instances, dehydrated instances, ready to run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances.</span></span> |
   |   <span data-ttu-id="ae1db-128">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="ae1db-128">**Maximum Matches**</span></span>   |               <span data-ttu-id="ae1db-129">要顯示的相符記錄數目 (必要)。</span><span class="sxs-lookup"><span data-stu-id="ae1db-129">The number of matches to display (required).</span></span> <span data-ttu-id="ae1db-130">依預設，通常設定為 50。</span><span class="sxs-lookup"><span data-stu-id="ae1db-130">This is usually set to 50, the default.</span></span><br /><br /> <span data-ttu-id="ae1db-131">當您也使用 [群組結果依據] 時，會顯示群組的數目而非記錄的總數。</span><span class="sxs-lookup"><span data-stu-id="ae1db-131">When you include Group Results By, this displays the number of groups, not the total number of records.</span></span>               |
   |    <span data-ttu-id="ae1db-132">**服務類別**</span><span class="sxs-lookup"><span data-stu-id="ae1db-132">**Service Class**</span></span>    |                                                 <span data-ttu-id="ae1db-133">您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。</span><span class="sxs-lookup"><span data-stu-id="ae1db-133">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>                                                  |
   | <span data-ttu-id="ae1db-134">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="ae1db-134">**Service Instance ID**</span></span> |                                                                                  <span data-ttu-id="ae1db-135">您可以依據服務執行個體識別碼來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-135">You can group or filter service instances by service instance ID.</span></span>                                                                                   |
   |    <span data-ttu-id="ae1db-136">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="ae1db-136">**Service Name**</span></span>     |                                                                                      <span data-ttu-id="ae1db-137">您可以依據服務名稱來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-137">You can group or filter service instances by service name.</span></span>                                                                                      |
   |   <span data-ttu-id="ae1db-138">**服務類型識別碼**</span><span class="sxs-lookup"><span data-stu-id="ae1db-138">**Service Type ID**</span></span>   |                                                                                    <span data-ttu-id="ae1db-139">您可以依據服務類型識別碼來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae1db-139">You can group or filter service instances by service type ID.</span></span>                                                                                     |


6. <span data-ttu-id="ae1db-140">完成**值**適當選取您在中所做的資料行**欄位名**資料行。</span><span class="sxs-lookup"><span data-stu-id="ae1db-140">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  

7. <span data-ttu-id="ae1db-141">繼續新增其他行至視需要查詢中，藉由完成**欄位名**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="ae1db-141">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ae1db-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1db-142">See Also</span></span>  
 [<span data-ttu-id="ae1db-143">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="ae1db-143">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)