---
title: Windows SharePoint Services 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41583fde-530a-4070-9647-f1ab6273aadf
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1af70299f5e308d1fc40fa6206f0ebfabff22a06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973284"
---
# <a name="windows-sharepoint-services-adapter-performance-counters"></a><span data-ttu-id="e4e8f-102">Windows SharePoint Services 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="e4e8f-102">Windows SharePoint Services Adapter Performance Counters</span></span>
<span data-ttu-id="e4e8f-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="e4e8f-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="e4e8f-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Windows Sharepoint Services 配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="e4e8f-105">The following performance counters are accessible for each host instance under the **BizTalk:Windows Sharepoint Services Adapter** performance object category:</span></span>  
  
|<span data-ttu-id="e4e8f-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="e4e8f-106">**Category**</span></span>|<span data-ttu-id="e4e8f-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="e4e8f-107">**Counter**</span></span>|<span data-ttu-id="e4e8f-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="e4e8f-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="e4e8f-109">BizTalk:Windows Sharepoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="e4e8f-109">BizTalk:Windows Sharepoint Services Adapter</span></span>|<span data-ttu-id="e4e8f-110">% 接收訊息失敗</span><span class="sxs-lookup"><span data-stu-id="e4e8f-110">% Receive Message Failures</span></span>|<span data-ttu-id="e4e8f-111">BizTalk Server 因為接收發生錯誤而尚未處理的 Windows SharePoint Services 檔案百分比。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-111">The percentage of Windows SharePoint Services files that have not been processed by BizTalk Server due to receive errors.</span></span>|  
||<span data-ttu-id="e4e8f-112">% 傳送訊息失敗</span><span class="sxs-lookup"><span data-stu-id="e4e8f-112">% Send Message Failures</span></span>|<span data-ttu-id="e4e8f-113">BizTalk Server 嘗試傳送至 Windows SharePoint Services 的失敗訊息百分比。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-113">The percentage of failed messages BizTalk Server attempted to send to Windows SharePoint Services.</span></span>|  
||<span data-ttu-id="e4e8f-114">% Web 服務呼叫失敗</span><span class="sxs-lookup"><span data-stu-id="e4e8f-114">% Web Service Call Failures</span></span>|<span data-ttu-id="e4e8f-115">已經失敗的 Windows SharePoint Services 配接器 Web 服務呼叫百分比。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-115">The percentage of Windows SharePoint Services adapter Web service calls that have failed.</span></span>|  
||<span data-ttu-id="e4e8f-116">接收認可失敗總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-116">Total Receive Commit Failures</span></span>|<span data-ttu-id="e4e8f-117">更新 SharePoint 文件的狀態時，發生的 Windows SharePoint Services 錯誤的總數。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-117">The total number of Windows SharePoint Services errors that were raised when updating the status of the SharePoint documents.</span></span>|  
||<span data-ttu-id="e4e8f-118">接收訊息失敗總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-118">Total Receive Message Failures</span></span>|<span data-ttu-id="e4e8f-119">BizTalk Server 已收到但因為錯誤而尚未處理的 Windows SharePoint Services 檔案總數。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-119">The total number of Windows SharePoint Services files received that have not been processed by BizTalk Server due to errors.</span></span>|  
||<span data-ttu-id="e4e8f-120">已接收訊息總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-120">Total Received Messages</span></span>|<span data-ttu-id="e4e8f-121">Windows SharePoint Services 配接器接收的 Windows SharePoint Services 檔案總數，包括無法處理的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-121">The total number of Windows SharePoint Services files received by the Windows SharePoint Services adapter, including files that failed to process.</span></span>|  
||<span data-ttu-id="e4e8f-122">傳送訊息失敗總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-122">Total Send Message Failures</span></span>|<span data-ttu-id="e4e8f-123">BizTalk Server 嘗試傳送到 Windows SharePoint Services 的失敗訊息總數。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-123">The total number of failed messages BizTalk Server attempted to send to Windows SharePoint Services.</span></span>|  
||<span data-ttu-id="e4e8f-124">已傳送訊息總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-124">Total Sent Messages</span></span>|<span data-ttu-id="e4e8f-125">BizTalk Server 傳送到 Windows SharePoint Services 的訊息總數，包括無法處理的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-125">The total number of messages BizTalk Server sent to Windows SharePoint Services, including files that failed to process.</span></span>|  
||<span data-ttu-id="e4e8f-126">Web 服務呼叫失敗總數</span><span class="sxs-lookup"><span data-stu-id="e4e8f-126">Total Web Service Call Failures</span></span>|<span data-ttu-id="e4e8f-127">已經失敗的 Windows SharePoint Services 配接器 Web 服務呼叫總數。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-127">The total number of Windows SharePoint Services adapter Web service calls that have failed.</span></span>|  
||<span data-ttu-id="e4e8f-128">每秒 Web 服務呼叫數目</span><span class="sxs-lookup"><span data-stu-id="e4e8f-128">Web Service Calls per Second</span></span>|<span data-ttu-id="e4e8f-129">每秒的 Windows SharePoint Services 配接器 Web 服務呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-129">The number of Windows SharePoint Services adapter Web service calls per second.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="e4e8f-130">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="e4e8f-130">To access performance counters</span></span>  
 <span data-ttu-id="e4e8f-131">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-131">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="e4e8f-132">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="e4e8f-132">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="e4e8f-133">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-133">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="e4e8f-134">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-134">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="e4e8f-135">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Windows Sharepoint Services 配接器**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="e4e8f-135">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:Windows Sharepoint Services Adapter** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="e4e8f-136">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-136">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="e4e8f-137">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-137">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="e4e8f-138">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-138">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="e4e8f-139">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="e4e8f-139">The selected performance counters appear on the **Performance Monitor** screen.</span></span>