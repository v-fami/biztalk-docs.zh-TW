---
title: 如何搜尋受到追蹤的服務執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6337df9-8c2e-4d4a-a64b-cc040f83bd91
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08e5a7fa563e175d6a1d784e546bd399e20d3c21
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-tracked-service-instances"></a><span data-ttu-id="4e73e-102">如何搜尋受到追蹤的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="4e73e-102">How to Search for Tracked Service Instances</span></span>
<span data-ttu-id="4e73e-103">您可以使用**查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來搜尋所有受到追蹤的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e73e-103">You can use the **Query** tab in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to search for all tracked service instances.</span></span> <span data-ttu-id="4e73e-104">若要尋找服務執行個體，您可以根據組件的名稱與版本、執行個體存留期的開始與結束時間、服務類別的名稱或執行個體識別碼、主控件名稱、錯誤碼以及服務執行個體的狀態，來進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="4e73e-104">To locate service instances, you can search on the name and version of the assembly, the start and end times of its lifetime, the name or instance ID of the service class, host name, error code, and the state of the service instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e73e-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="4e73e-105">Prerequisites</span></span>  
 <span data-ttu-id="4e73e-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="4e73e-106">To perform this procedure, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.</span></span>  
  
### <a name="to-search-for-tracked-service-instances"></a><span data-ttu-id="4e73e-107">若要搜尋受到追蹤的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="4e73e-107">To search for tracked service instances</span></span>  
  
1.  <span data-ttu-id="4e73e-108">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4e73e-108">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="4e73e-109">在主控台樹狀目錄中，依序展開 **BizTalk Server 管理**, ，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="4e73e-109">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="4e73e-110">在詳細資料窗格中，按一下 [ **新查詢** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4e73e-110">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="4e73e-111">在 **查詢運算式** 群組 **值** 欄中，選取 **追蹤服務執行個體** 從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="4e73e-111">In the **Query Expression** group, in the **Value** column, select **Tracked Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="4e73e-112">在 **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，選取一或多個項目︰</span><span class="sxs-lookup"><span data-stu-id="4e73e-112">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="4e73e-113">項目</span><span class="sxs-lookup"><span data-stu-id="4e73e-113">Item</span></span>|<span data-ttu-id="4e73e-114">Description</span><span class="sxs-lookup"><span data-stu-id="4e73e-114">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="4e73e-115">**組件名稱**</span><span class="sxs-lookup"><span data-stu-id="4e73e-115">**Assembly Name**</span></span>|<span data-ttu-id="4e73e-116">服務執行個體的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="4e73e-116">Name of the assembly for the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-117">**組件版本**</span><span class="sxs-lookup"><span data-stu-id="4e73e-117">**Assembly Version**</span></span>|<span data-ttu-id="4e73e-118">服務執行個體的 版本。</span><span class="sxs-lookup"><span data-stu-id="4e73e-118">Version of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-119">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="4e73e-119">**End Time**</span></span>|<span data-ttu-id="4e73e-120">服務執行個體的 結束時間。</span><span class="sxs-lookup"><span data-stu-id="4e73e-120">End time of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-121">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="4e73e-121">**Error Code**</span></span>|<span data-ttu-id="4e73e-122">任何 與服務執行個體相關聯的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4e73e-122">Any error code associated with the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-123">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="4e73e-123">**Host Name**</span></span>|<span data-ttu-id="4e73e-124">服務執行個體的 主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="4e73e-124">The host name of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-125">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="4e73e-125">**Maximum Matches**</span></span>|<span data-ttu-id="4e73e-126">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="4e73e-126">The number of matches to display.</span></span>|  
    |<span data-ttu-id="4e73e-127">**服務類別**</span><span class="sxs-lookup"><span data-stu-id="4e73e-127">**Service Class**</span></span>|<span data-ttu-id="4e73e-128">服務執行個體的 類別。</span><span class="sxs-lookup"><span data-stu-id="4e73e-128">The class of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-129">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="4e73e-129">**Service Instance ID**</span></span>|<span data-ttu-id="4e73e-130">服務執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="4e73e-130">The service instance ID.</span></span>|  
    |<span data-ttu-id="4e73e-131">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="4e73e-131">**Service Name**</span></span>|<span data-ttu-id="4e73e-132">服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e73e-132">The name of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-133">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="4e73e-133">**Start Time**</span></span>|<span data-ttu-id="4e73e-134">服務執行個體的開始時間。</span><span class="sxs-lookup"><span data-stu-id="4e73e-134">The start time of the service instance.</span></span>|  
    |<span data-ttu-id="4e73e-135">**狀態**</span><span class="sxs-lookup"><span data-stu-id="4e73e-135">**State**</span></span>|<span data-ttu-id="4e73e-136">服務執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="4e73e-136">The state of the service instance.</span></span>|  
  
6.  <span data-ttu-id="4e73e-137">完成 **值** 適用於選取您所做的資料行 **欄位名稱** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4e73e-137">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="4e73e-138">繼續新增其他行至查詢中，藉由完成 **欄位名稱**, ，**運算子**, ，和 **值** 資料行，然後再按一下 **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="4e73e-138">Continue adding additional lines to the query as appropriate by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e73e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e73e-139">See Also</span></span>  
 [<span data-ttu-id="4e73e-140">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="4e73e-140">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)