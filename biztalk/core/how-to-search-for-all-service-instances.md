---
title: 如何搜尋所有服務執行個體 |Microsoft 文件
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
ms.openlocfilehash: e96622fad23c28c0d4147f64a11cc540e88e7f97
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22255118"
---
# <a name="how-to-search-for-all-service-instances"></a><span data-ttu-id="0a28b-102">如何搜尋所有服務執行個體</span><span class="sxs-lookup"><span data-stu-id="0a28b-102">How to Search for All Service Instances</span></span>
<span data-ttu-id="0a28b-103">您可以使用 **查詢** 在 BizTalk Server 管理主控台，來搜尋所有服務執行個體 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a28b-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for all service instances.</span></span> <span data-ttu-id="0a28b-104">若有任何執行中或擱置的執行個體，就無法取消登錄特定服務類型。</span><span class="sxs-lookup"><span data-stu-id="0a28b-104">You cannot unenlist a specific service type if there are any running or suspended instances.</span></span> <span data-ttu-id="0a28b-105">例如，取消登錄特定服務類型之前，可以搜尋所有的服務執行個體，以確保沒有執行中或擱置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-105">For example, before you can unenlist a specific service type, you can search for all service instances to ensure that there are no running or suspended instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a28b-106">URI 建立群組和篩選時，結果中僅會顯示傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="0a28b-106">When Grouping and Filtering by URI, only send and receive ports are displayed in the results.</span></span> <span data-ttu-id="0a28b-107">URI 建立群組和篩選並不適用協調流程，因為協調流程不包含在顯示的結果內。</span><span class="sxs-lookup"><span data-stu-id="0a28b-107">Grouping and Filtering by URI is not possible for orchestrations, which are not included in the displayed results.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a28b-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="0a28b-108">Prerequisites</span></span>  
 <span data-ttu-id="0a28b-109">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="0a28b-109">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-all-service-instances"></a><span data-ttu-id="0a28b-110">搜尋所有服務執行個體</span><span class="sxs-lookup"><span data-stu-id="0a28b-110">To search for all service instances</span></span>  
  
1.  <span data-ttu-id="0a28b-111">按一下  **啟動**, ，按一下  **所有程式**, ，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], ，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0a28b-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0a28b-112">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="0a28b-112">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="0a28b-113">在詳細資料窗格中，按一下 [ **新查詢** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a28b-113">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="0a28b-114">在 **查詢運算式** 群組 **值** 欄中，選取 **所有進行中的服務執行個體** 從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="0a28b-114">In the **Query Expression** group, in the **Value** column, select **All In-Progress Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="0a28b-115">在 **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，選取一或多個項目︰</span><span class="sxs-lookup"><span data-stu-id="0a28b-115">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="0a28b-116">使用</span><span class="sxs-lookup"><span data-stu-id="0a28b-116">Use this</span></span>|<span data-ttu-id="0a28b-117">動作</span><span class="sxs-lookup"><span data-stu-id="0a28b-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0a28b-118">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="0a28b-118">**Application Name**</span></span>|<span data-ttu-id="0a28b-119">BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a28b-119">The BizTalk Server application.</span></span>|  
    |<span data-ttu-id="0a28b-120">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="0a28b-120">**Creation Time**</span></span>|<span data-ttu-id="0a28b-121">尋找指定日期前後建立的所有服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-121">Find all service instances created before or after the specified date.</span></span>|  
    |<span data-ttu-id="0a28b-122">**群組結果依據**</span><span class="sxs-lookup"><span data-stu-id="0a28b-122">**Group Results By**</span></span>|<span data-ttu-id="0a28b-123">您可以依據應用程式、主控件名稱、服務類別、服務執行個體狀態或服務名稱來群組結果。</span><span class="sxs-lookup"><span data-stu-id="0a28b-123">You can group results by application, host name, service class, service instance status, or service name.</span></span>|  
    |<span data-ttu-id="0a28b-124">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="0a28b-124">**Host Name**</span></span>|<span data-ttu-id="0a28b-125">BizTalk 主控件的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a28b-125">The name of the BizTalk Host.</span></span>|  
    |<span data-ttu-id="0a28b-126">**執行個體狀態**</span><span class="sxs-lookup"><span data-stu-id="0a28b-126">**Instance Status**</span></span>|<span data-ttu-id="0a28b-127">您可以搜尋所有正在執行的執行個體、所有擱置的執行個體、作用中的執行個體、凍結的執行個體、準備執行的執行個體、已排程的執行個體、已擱置但不可繼續的執行個體，或是已擱置但可以繼續的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-127">You can search for all running instances, all suspended instances, active instances, dehydrated instances, ready to run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances.</span></span>|  
    |<span data-ttu-id="0a28b-128">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="0a28b-128">**Maximum Matches**</span></span>|<span data-ttu-id="0a28b-129">要顯示的相符記錄數目 (必要)。</span><span class="sxs-lookup"><span data-stu-id="0a28b-129">The number of matches to display (required).</span></span> <span data-ttu-id="0a28b-130">依預設，通常設定為 50。</span><span class="sxs-lookup"><span data-stu-id="0a28b-130">This is usually set to 50, the default.</span></span><br /><br /> <span data-ttu-id="0a28b-131">當您也使用 [群組結果依據] 時，會顯示群組的數目而非記錄的總數。</span><span class="sxs-lookup"><span data-stu-id="0a28b-131">When you include Group Results By, this displays the number of groups, not the total number of records.</span></span>|  
    |<span data-ttu-id="0a28b-132">**服務類別**</span><span class="sxs-lookup"><span data-stu-id="0a28b-132">**Service Class**</span></span>|<span data-ttu-id="0a28b-133">您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。</span><span class="sxs-lookup"><span data-stu-id="0a28b-133">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>|  
    |<span data-ttu-id="0a28b-134">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="0a28b-134">**Service Instance ID**</span></span>|<span data-ttu-id="0a28b-135">您可以依據服務執行個體識別碼來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-135">You can group or filter service instances by service instance ID.</span></span>|  
    |<span data-ttu-id="0a28b-136">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="0a28b-136">**Service Name**</span></span>|<span data-ttu-id="0a28b-137">您可以依據服務名稱來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-137">You can group or filter service instances by service name.</span></span>|  
    |<span data-ttu-id="0a28b-138">**服務類型識別碼**</span><span class="sxs-lookup"><span data-stu-id="0a28b-138">**Service Type ID**</span></span>|<span data-ttu-id="0a28b-139">您可以依據服務類型識別碼來群組或篩選服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a28b-139">You can group or filter service instances by service type ID.</span></span>|  
  
6.  <span data-ttu-id="0a28b-140">完成 **值** 適用於選取您所做的資料行 **欄位名稱** 資料行。</span><span class="sxs-lookup"><span data-stu-id="0a28b-140">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="0a28b-141">繼續新增其他行至視需要查詢，藉由完成 **欄位名稱**, ，**運算子**, ，和 **值** 資料行，然後再按一下 **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="0a28b-141">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a28b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a28b-142">See Also</span></span>  
 [<span data-ttu-id="0a28b-143">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="0a28b-143">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)