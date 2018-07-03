---
title: 監視 SQL Server Agent 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fb4026b95a5f368c265b49425ab1d3e1ec776cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015389"
---
# <a name="monitoring-sql-server-agent-jobs"></a><span data-ttu-id="efb85-102">監視 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="efb85-102">Monitoring SQL Server Agent Jobs</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="efb85-103"> 包含多項 SQL Server Agent 作業，可執行重要功能以維持伺服器運作正常且狀況良好。</span><span class="sxs-lookup"><span data-stu-id="efb85-103"> includes multiple SQL Server Agent jobs that perform important functions to keep your servers operational and healthy.</span></span> <span data-ttu-id="efb85-104">您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="efb85-104">You should monitor the health of these jobs and ensure that they are running without errors.</span></span>  

## <a name="guidelines-for-monitoring-the-sql-server-agent-jobs"></a><span data-ttu-id="efb85-105">監視 SQL Server Agent 作業的指導方針</span><span class="sxs-lookup"><span data-stu-id="efb85-105">Guidelines for Monitoring the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="efb85-106">以下是監視作業的指導方針：</span><span class="sxs-lookup"><span data-stu-id="efb85-106">Following are guidelines for monitoring the jobs:</span></span>  

- <span data-ttu-id="efb85-107">**確認 SQL Server Agent 服務正在執行**</span><span class="sxs-lookup"><span data-stu-id="efb85-107">**Verify that the SQL Server Agent service is running**</span></span>  

- <span data-ttu-id="efb85-108">**確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功**</span><span class="sxs-lookup"><span data-stu-id="efb85-108">**Verify that the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully**</span></span>  

   <span data-ttu-id="efb85-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent 作業而言十分重要： 如果它們並未執行，經過一段時間，會降低系統效能。</span><span class="sxs-lookup"><span data-stu-id="efb85-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent jobs are crucial: if they are not running, system performance will degrade over time.</span></span>  

- <span data-ttu-id="efb85-110">**確認 BizTalk Server SQL Server Agent 作業所完成及時**</span><span class="sxs-lookup"><span data-stu-id="efb85-110">**Verify that the BizTalk Server SQL Server Agent jobs are completing in a timely manner**</span></span>  

   <span data-ttu-id="efb85-111">設定 Microsoft System Center Operations Manager，以監視作業。</span><span class="sxs-lookup"><span data-stu-id="efb85-111">Set up Microsoft System Center Operations Manager to monitor the jobs.</span></span>  

   <span data-ttu-id="efb85-112">您應該注意的是專門針對特定工作的排程：</span><span class="sxs-lookup"><span data-stu-id="efb85-112">You should be aware of schedules that are particular to certain jobs:</span></span>  

  -   <span data-ttu-id="efb85-113">預設會持續 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作執行。</span><span class="sxs-lookup"><span data-stu-id="efb85-113">The MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job runs continuously by default.</span></span> <span data-ttu-id="efb85-114">監視軟體，請考量此排程，並不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="efb85-114">Monitoring software should take this schedule into account and not produce warnings.</span></span>  

  -   <span data-ttu-id="efb85-115">MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業未啟用或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作開始每隔 10 秒。</span><span class="sxs-lookup"><span data-stu-id="efb85-115">The MessageBox_Message_Cleanup_BizTalkMsgBoxDb job is not enabled or scheduled, but it is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job every 10 seconds.</span></span> <span data-ttu-id="efb85-116">因此，這項作業不應啟用、 排程，或以手動方式啟動。</span><span class="sxs-lookup"><span data-stu-id="efb85-116">Therefore, this job should not be enabled, scheduled, or manually started.</span></span>  

- <span data-ttu-id="efb85-117">**確認已正確設定 SQL Server Agent 服務的啟動類型**</span><span class="sxs-lookup"><span data-stu-id="efb85-117">**Verify that the Startup type of the SQL Server Agent service is configured correctly**</span></span>  

   <span data-ttu-id="efb85-118">確認 SQL Server Agent 服務已設有**Startuptype**的**自動**除非 SQL Server Agent 服務設定為 Windows Server 叢集上叢集資源。</span><span class="sxs-lookup"><span data-stu-id="efb85-118">Verify that the SQL Server Agent service is configured with a **Startuptype** of **Automatic** unless the SQL Server Agent service is configured as a cluster resource on a Windows Server cluster.</span></span> <span data-ttu-id="efb85-119">如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**Startuptype**作為**手動**因為服務將受叢集服務。</span><span class="sxs-lookup"><span data-stu-id="efb85-119">If the SQL Server Agent service is configured as a cluster resource, then you should configure the **Startuptype** as **Manual** since the service will be managed by the Cluster service.</span></span>  

## <a name="additional-resources"></a><span data-ttu-id="efb85-120">其他資源</span><span class="sxs-lookup"><span data-stu-id="efb85-120">Additional Resources</span></span>  

- <span data-ttu-id="efb85-121">如需監視的詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業，請參閱[監視 SQL Server Agent 作業和資料庫](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="efb85-121">For more information about monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent jobs, see [Monitoring SQL Server Agent Jobs and Databases](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md).</span></span>  

- <span data-ttu-id="efb85-122">如需隨附於 SQL Server Agent 作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]請參閱 < [[資料庫結構和作業]](http://go.microsoft.com/fwlink/?LinkID=153451) (<http://go.microsoft.com/fwlink/?LinkID=153451>)。</span><span class="sxs-lookup"><span data-stu-id="efb85-122">For more information about the SQL Server Agent jobs that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] see ["Database Structure and Jobs"](http://go.microsoft.com/fwlink/?LinkID=153451) (<http://go.microsoft.com/fwlink/?LinkID=153451>).</span></span>
