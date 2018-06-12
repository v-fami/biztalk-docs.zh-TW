---
title: 訊息與執行個體資料追蹤的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HAT, best practices
- best practices, HAT
ms.assetid: 2ac5c87b-2059-4912-9cec-2ae4eaac56df
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 680958d2950edffeaa56c7c3b8d7f8da40967173
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34849014"
---
# <a name="best-practices-for-message-and-instance-data-tracking"></a><span data-ttu-id="a4987-102">訊息和執行個體資料追蹤的最佳作法</span><span class="sxs-lookup"><span data-stu-id="a4987-102">Best Practices for Message and Instance Data Tracking</span></span>
<span data-ttu-id="a4987-103">檢閱使用歷程記錄和追蹤資料的下列最佳作法。</span><span class="sxs-lookup"><span data-stu-id="a4987-103">Review the following best practices for using historical and tracked data.</span></span>  
  
-   <span data-ttu-id="a4987-104">**檢閱使用歷程記錄和追蹤資料的安全性考量**</span><span class="sxs-lookup"><span data-stu-id="a4987-104">**Review the security considerations for using historical and tracked data**</span></span>  
  
    -   <span data-ttu-id="a4987-105">如需歷程記錄和追蹤資料的安全性考量的詳細資訊，請參閱[訊息和執行個體資料追蹤的安全性考量](../core/security-considerations-for-message-and-instance-data-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="a4987-105">For more information about security considerations for historical and tracked data, see [Security Considerations for Message and Instance Data Tracking](../core/security-considerations-for-message-and-instance-data-tracking.md).</span></span>  
  
-   <span data-ttu-id="a4987-106">**確定 SQL Server Agent 服務正在所有的 MessageBox 資料庫上執行**</span><span class="sxs-lookup"><span data-stu-id="a4987-106">**Ensure that the SQL Server Agent service is running on all MessageBox databases**</span></span>  
  
    -   <span data-ttu-id="a4987-107">SQL Server Agent 讓訊息內文可供 WMI 和歷程記錄和追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="a4987-107">SQL Server Agent makes message bodies available to WMI, and historical and tracked data.</span></span> <span data-ttu-id="a4987-108">這可讓您執行作業來清除 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4987-108">This enables you to run jobs to clean up the MessageBox databases.</span></span> <span data-ttu-id="a4987-109">如需有關 SQL Server Agent 的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="a4987-109">For more information about SQL Server Agent, see SQL Server Books Online.</span></span>  
  
-   <span data-ttu-id="a4987-110">**啟用訊息內文追蹤**</span><span class="sxs-lookup"><span data-stu-id="a4987-110">**Enable message body tracking**</span></span>  
  
    -   <span data-ttu-id="a4987-111">在服務執行個體處理完成之後，必須要有訊息內文追蹤才能儲存訊息。</span><span class="sxs-lookup"><span data-stu-id="a4987-111">Message body tracking is required to save messages after service instances processing is complete.</span></span>  
  
-   <span data-ttu-id="a4987-112">**針對您的商務需求適當地設定追蹤**</span><span class="sxs-lookup"><span data-stu-id="a4987-112">**Configure tracking as appropriate for your business needs**</span></span>  
  
    -   <span data-ttu-id="a4987-113">您可以檢視歷程記錄和追蹤資料之前，您必須先設定使用 BizTalk Server 管理主控台的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a4987-113">Before you can view historical and tracked data, you must first configure tracking using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="a4987-114">在啟用或停用追蹤選項時，必須牢記多個考量。</span><span class="sxs-lookup"><span data-stu-id="a4987-114">There are multiple considerations to keep in mind when enabling or disabling tracking options.</span></span> <span data-ttu-id="a4987-115">您追蹤的資料越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小便會成長越快，這可能會對執行階段效能造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="a4987-115">The more data you track, the faster your BizTalk Tracking (BizTalkDTADb) database will grow in size, which can adversely affect your runtime performance.</span></span> <span data-ttu-id="a4987-116">如需詳細資訊，請參閱[設定追蹤使用 BizTalk Server 管理主控台](http://msdn.microsoft.com/49b7f9d3-60b5-41bd-ba8b-029253926bef)。</span><span class="sxs-lookup"><span data-stu-id="a4987-116">For more information, see [Configuring Tracking Using the BizTalk Server Administration Console](http://msdn.microsoft.com/49b7f9d3-60b5-41bd-ba8b-029253926bef).</span></span>  
  
-   <span data-ttu-id="a4987-117">**選取適當類型的追蹤，以進行疑難排解或稽核**</span><span class="sxs-lookup"><span data-stu-id="a4987-117">**Select the appropriate type of tracking for troubleshooting or auditing**</span></span>  
  
    -   <span data-ttu-id="a4987-118">在開發環境，或在臨時或生產環境中進行疑難排解時，應該啟用所有追蹤選項，以便您可以查看成品事件、訊息屬性、訊息內文和協調流程事件的細節。</span><span class="sxs-lookup"><span data-stu-id="a4987-118">For troubleshooting either in a development environment, or in a staging or production environment, you should enable all tracking options so that you can see artifact events, message properties, message bodies and orchestration events in detail.</span></span> <span data-ttu-id="a4987-119">這會提供豐富的追蹤資訊，可讓您在系統中重新建立事件序列並偵錯應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4987-119">This provides a rich set of tracked information that you can use to recreate the sequence of events in your system and debug your application.</span></span>  
  
    -   <span data-ttu-id="a4987-120">對於執行層級的稽核，請仔細選取您要稽核的事件，然後只啟用那些事件的稽核。</span><span class="sxs-lookup"><span data-stu-id="a4987-120">For production level auditing, carefully choose the events you want to audit and then enable tracking only for those events.</span></span> <span data-ttu-id="a4987-121">例如，許多企業想要能夠證實訊息已輸入且已離開系統。</span><span class="sxs-lookup"><span data-stu-id="a4987-121">For example, many enterprises want to be able to prove that a message entered and exited the system.</span></span> <span data-ttu-id="a4987-122">為達成此目的，您應該啟用對應接收埠上的輸入追蹤，並啟用對應傳送埠上的輸出追蹤。</span><span class="sxs-lookup"><span data-stu-id="a4987-122">To achieve this, you should enable inbound tracking on the corresponding receive port and enable outbound tracking on the corresponding send port.</span></span> <span data-ttu-id="a4987-123">如有必要，您可以新增訊息屬性和訊息內文追蹤。</span><span class="sxs-lookup"><span data-stu-id="a4987-123">If necessary, you can add message property and message body tracking.</span></span>  
  
    -   <span data-ttu-id="a4987-124">如需測量商務關鍵效能指標 (KPI) 或是由指定商務里程碑的達成度所測量的進度，您應該使用商務活動監控 (BAM) 追蹤。</span><span class="sxs-lookup"><span data-stu-id="a4987-124">For measuring business Key Performance Indicators (KPIs) or progress as measured by the achievement of specified business milestones, you should use Business Activity Monitoring (BAM) tracking.</span></span> <span data-ttu-id="a4987-125">BAM 追蹤的追蹤，以及將訊息內文，因此如果這是重要的是，您應該使用歷程記錄和追蹤的資料搭配 BAM 追蹤的能力有限。</span><span class="sxs-lookup"><span data-stu-id="a4987-125">BAM tracking has limited abilities to track and store message bodies, so if this is important, you should use historical and tracked data  in conjunction with BAM tracking.</span></span> <span data-ttu-id="a4987-126">如需有關 BAM 追蹤的詳細資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。</span><span class="sxs-lookup"><span data-stu-id="a4987-126">For more information about BAM tracking, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md).</span></span>  
  
-   <span data-ttu-id="a4987-127">**封存和清除 BizTalk 追蹤 (BizTalkDTADb) 資料庫以規則為基礎的資料**</span><span class="sxs-lookup"><span data-stu-id="a4987-127">**Archive and purge data from the BizTalk Tracking (BizTalkDTADb) database on a regular basis**</span></span>  
  
    -   <span data-ttu-id="a4987-128">如果已啟用追蹤，您應該定期從「BizTalk 追蹤」資料庫封存和清除資料，協助讓資料庫保持適當的大小，以利改善系統效能。</span><span class="sxs-lookup"><span data-stu-id="a4987-128">If you have enabled tracking, you should archive and purge data from the BizTalk Tracking database on a regular basis to help keep the database appropriately sized, which helps improve system performance.</span></span> <span data-ttu-id="a4987-129">如需詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a4987-129">For more information, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4987-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4987-130">See Also</span></span>  
 [<span data-ttu-id="a4987-131">檢視追蹤的訊息和執行個體資料</span><span class="sxs-lookup"><span data-stu-id="a4987-131">Viewing Tracked Message and Instance Data</span></span>](../core/viewing-tracked-message-and-instance-data.md)