---
title: 監視工作的常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2f9f56a-c839-4108-933d-69b00a1e3817
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d500e79cdf20c6a1914708976101715c2f00ae69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001655"
---
# <a name="routine-monitoring-tasks"></a><span data-ttu-id="725d5-102">例行性監視工作</span><span class="sxs-lookup"><span data-stu-id="725d5-102">Routine Monitoring Tasks</span></span>
<span data-ttu-id="725d5-103">執行下列監視工作依定期排程將會協助您保留您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構，操作。</span><span class="sxs-lookup"><span data-stu-id="725d5-103">Performing the following monitoring tasks on a regularly scheduled basis will assist you in keeping your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure operationally ready.</span></span>  
  
## <a name="daily-monitoring-tasks"></a><span data-ttu-id="725d5-104">每日監視工作</span><span class="sxs-lookup"><span data-stu-id="725d5-104">Daily Monitoring Tasks</span></span>  
  
- <span data-ttu-id="725d5-105">檢閱所有未解決的警示。</span><span class="sxs-lookup"><span data-stu-id="725d5-105">Review all open alerts.</span></span>  
  
- <span data-ttu-id="725d5-106">使用**群組中樞**頁面中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]調查協調流程、 連接埠和訊息失敗的管理主控台。</span><span class="sxs-lookup"><span data-stu-id="725d5-106">Use the **Group Hub** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console to investigate orchestration, port, and message failures.</span></span> <span data-ttu-id="725d5-107">**群組中樞**頁面會提供即時的目前狀態，系統中，在 MessageBox 資料庫中存取資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="725d5-107">The **Group Hub** page provides access to the current real-time state of the system, accessing data in the MessageBox database.</span></span> <span data-ttu-id="725d5-108">您可檢視所有服務執行個體 (如協調流程、連接埠和傳訊)，及其關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="725d5-108">You can view all service instances such as orchestrations, ports, and messaging, along with their associated messages.</span></span> <span data-ttu-id="725d5-109">使用**群組中樞**頁面，您可以執行下列活動：</span><span class="sxs-lookup"><span data-stu-id="725d5-109">Using the **Group Hub** page you can perform the following activities:</span></span>  
  
  - <span data-ttu-id="725d5-110">請參閱目前正在執行的服務執行個體，例如協調流程和傳訊，以及相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="725d5-110">See currently running service instances, such as orchestrations and messaging, and their associated messages.</span></span>  
  
  - <span data-ttu-id="725d5-111">查看 MessageBox 資料庫中的目前資料與系統即時狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="725d5-111">Look into the MessageBox database for a view of the current data and the real-time state of the system.</span></span>  
  
  - <span data-ttu-id="725d5-112">擱置、終止與繼續服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="725d5-112">Suspend, terminate, and resume service instances.</span></span>  
  
    <span data-ttu-id="725d5-113">如需使用詳細資訊**群組中樞**頁面上，請參閱[ http://go.microsoft.com/fwlink/?LinkId=155281 ](http://go.microsoft.com/fwlink/?LinkId=155281)。</span><span class="sxs-lookup"><span data-stu-id="725d5-113">For more information about using the **Group Hub** page, see [http://go.microsoft.com/fwlink/?LinkId=155281](http://go.microsoft.com/fwlink/?LinkId=155281).</span></span>  
  
- <span data-ttu-id="725d5-114">檢視警告 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="725d5-114">Review warnings (optional).</span></span>  
  
  <span data-ttu-id="725d5-115">如需詳細資訊，請參閱 <<c0> [ 檢查清單： 執行每日維護檢查](../technical-guides/checklist-performing-daily-maintenance-checks.md)。</span><span class="sxs-lookup"><span data-stu-id="725d5-115">For more information, see [Checklist: Performing Daily Maintenance Checks](../technical-guides/checklist-performing-daily-maintenance-checks.md).</span></span>  
  
## <a name="weekly-monitoring-tasks"></a><span data-ttu-id="725d5-116">每週的監視工作</span><span class="sxs-lookup"><span data-stu-id="725d5-116">Weekly Monitoring Tasks</span></span>  
  
- <span data-ttu-id="725d5-117">檢閱事件記錄檔，每週至少一次。</span><span class="sxs-lookup"><span data-stu-id="725d5-117">Review the event logs at least once per week.</span></span> <span data-ttu-id="725d5-118">這項工作的原因是為了防止問題，例如讓未偵測到的 DBNetLib 錯誤。</span><span class="sxs-lookup"><span data-stu-id="725d5-118">The reason for this task is to prevent issues, such as DBNetLib errors going undetected.</span></span> <span data-ttu-id="725d5-119">服務中斷可能會被忽視除非您有非常低的延遲系統。</span><span class="sxs-lookup"><span data-stu-id="725d5-119">Service interruption might go unnoticed unless you have a very low latency system.</span></span> <span data-ttu-id="725d5-120">不過，某些錯誤可能表示更大的問題 （例如太多主機或 BizTalk Server 伺服器，訊息方塊中，SQL 方塊等的效能問題的數目）。</span><span class="sxs-lookup"><span data-stu-id="725d5-120">However, some of these errors can indicate a bigger issue (for example, too many hosts or BizTalk Server servers for the number of message boxes, performance issues on the SQL box, etc).</span></span>  
  
  <span data-ttu-id="725d5-121">如需詳細資訊，請參閱 <<c0> [ 檢查清單： 執行每週維護檢查](../technical-guides/checklist-performing-weekly-maintenance-checks.md)。</span><span class="sxs-lookup"><span data-stu-id="725d5-121">For more information, see [Checklist: Performing Weekly Maintenance Checks](../technical-guides/checklist-performing-weekly-maintenance-checks.md).</span></span>  
  
## <a name="as-needed-tasks"></a><span data-ttu-id="725d5-122">視需要的工作</span><span class="sxs-lookup"><span data-stu-id="725d5-122">As-Needed Tasks</span></span>  
  
- <span data-ttu-id="725d5-123">修改規則，以自訂的監視您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="725d5-123">Modify the rules to customize the monitoring of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure.</span></span>  
  
- <span data-ttu-id="725d5-124">執行記錄檔的效能分析工具 (PAL)。</span><span class="sxs-lookup"><span data-stu-id="725d5-124">Run the Performance Analysis of Logs tool (PAL).</span></span> <span data-ttu-id="725d5-125">如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署是很頻繁 （比方說，新的交易夥伴未定期，加入新的程式碼未部署），您可能會執行效能監視器及 PAL 一季一次，或甚至是每隔六個月。</span><span class="sxs-lookup"><span data-stu-id="725d5-125">If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment is fairly constant (for example, new trading partners aren't added routinely, new code is not deployed), you might run Perfmon and PAL once a quarter or even every six months.</span></span> <span data-ttu-id="725d5-126">如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署的變更頻率，您可能要執行 Perfmon PAL 每隔幾個月的時間相比較的基準。</span><span class="sxs-lookup"><span data-stu-id="725d5-126">If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment changes more frequently, you may want to run Perfmon and PAL every couple of months to compare against a baseline.</span></span> <span data-ttu-id="725d5-127">如需有關 PAL 的詳細資訊，請參閱 <<c0> [ 使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="725d5-127">For more information on PAL, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).</span></span>  
  
- <span data-ttu-id="725d5-128">執行效能監視器中發生的變更數目而定的一季一次，或甚至是每隔六個月來每幾個月您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="725d5-128">Run Perfmon every few months, to once a quarter or even every six months depending on the number of changes occur in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
- <span data-ttu-id="725d5-129">執行 BizTalk Server Best Practices Analyzer 時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署的變更 （例如，新增新的應用程式） 或建立新的主機。</span><span class="sxs-lookup"><span data-stu-id="725d5-129">Run BizTalk Server Best Practices Analyzer when the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment changes (for example, the addition of new applications or creation of new hosts).</span></span> <span data-ttu-id="725d5-130">您可以下載 BizTalk Server Best Practices Analyzer 在[ http://go.microsoft.com/fwlink/?LinkId=83317 ](http://go.microsoft.com/fwlink/?LinkId=83317)。</span><span class="sxs-lookup"><span data-stu-id="725d5-130">You can download the BizTalk Server Best Practices Analyzer at [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317).</span></span>  
  
- <span data-ttu-id="725d5-131">執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)(http://go.microsoft.com/fwlink/?LinkId=151930)。</span><span class="sxs-lookup"><span data-stu-id="725d5-131">Run the [BizTalk MsgBoxViewer tool](http://go.microsoft.com/fwlink/?LinkId=151930) (http://go.microsoft.com/fwlink/?LinkId=151930).</span></span> <span data-ttu-id="725d5-132">這項工具會分析 BizTalk MessageBox 和其他資料庫，並產生包含警告的 HTML 報告與資料庫相關的任何，和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="725d5-132">This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any, and other information related to the databases.</span></span>  
  
  > [!TIP]  
  >  <span data-ttu-id="725d5-133">您也可以儲存供稍後使用的報表。</span><span class="sxs-lookup"><span data-stu-id="725d5-133">You can also save the reports for later use.</span></span> <span data-ttu-id="725d5-134">與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="725d5-134">These reports might be useful when troubleshooting issues with the BizTalk application.</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="725d5-135">Microsoft 不支援使用這個工具，Microsoft 不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="725d5-135">Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs.</span></span> <span data-ttu-id="725d5-136">請自行承擔使用這個程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="725d5-136">Use of this program is entirely at your own risk.</span></span>  
  
- <span data-ttu-id="725d5-137">執行[結束字元 工具](http://go.microsoft.com/fwlink/?LinkId=151931)(http://go.microsoft.com/fwlink/?LinkId=151931)。</span><span class="sxs-lookup"><span data-stu-id="725d5-137">Run the [Terminator tool](http://go.microsoft.com/fwlink/?LinkId=151931) (http://go.microsoft.com/fwlink/?LinkId=151931).</span></span> <span data-ttu-id="725d5-138">這項工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。</span><span class="sxs-lookup"><span data-stu-id="725d5-138">This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.</span></span> <span data-ttu-id="725d5-139">如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[若要解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。</span><span class="sxs-lookup"><span data-stu-id="725d5-139">For more information about how the Terminator tool integrates with the BizTalk MsgBoxViewer tool, see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932).</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="725d5-140">Microsoft 不支援使用這個工具，Microsoft 不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="725d5-140">Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs.</span></span> <span data-ttu-id="725d5-141">請自行承擔使用這個程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="725d5-141">Use of this program is entirely at your own risk.</span></span>  
  
## <a name="annual-monitoring-tasks"></a><span data-ttu-id="725d5-142">每年的監視工作</span><span class="sxs-lookup"><span data-stu-id="725d5-142">Annual Monitoring Tasks</span></span>  
  
- <span data-ttu-id="725d5-143">檢閱監視的有效性您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="725d5-143">Review the effectiveness of the monitoring of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure.</span></span>  
  
- <span data-ttu-id="725d5-144">建立計畫以監視進行任何所需的變更。</span><span class="sxs-lookup"><span data-stu-id="725d5-144">Create a plan to make any needed changes in monitoring.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725d5-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="725d5-145">See Also</span></span>  
 [<span data-ttu-id="725d5-146">例行性維護工作檢查清單</span><span class="sxs-lookup"><span data-stu-id="725d5-146">Routine Maintenance Checklists</span></span>](../technical-guides/routine-maintenance-checklists.md)