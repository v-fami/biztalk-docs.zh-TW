---
title: 監視應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4be98ba2-6acd-4dee-b6ea-db71bbd368f0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d1a7e4e0d4cb0f4e6899159da6c6c06a83e9165
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010291"
---
# <a name="monitoring-applications"></a><span data-ttu-id="bb6cb-102">監視應用程式</span><span class="sxs-lookup"><span data-stu-id="bb6cb-102">Monitoring Applications</span></span>
<span data-ttu-id="bb6cb-103">設定 Microsoft System Center Operations Manager 來監視 BizTalk 應用程式通常可以分成往下漸進式的四個步驟程序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bb6cb-103">Setting up Microsoft System Center Operations Manager to monitor BizTalk applications typically can be broken down into a progressive four-step process as follows:</span></span>  
  
1. <span data-ttu-id="bb6cb-104">**修改現有的規則和/或複製的規則，以自訂的管理組件來監視自訂的 BizTalk 應用程式**</span><span class="sxs-lookup"><span data-stu-id="bb6cb-104">**Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application**</span></span>  
  
    <span data-ttu-id="bb6cb-105">您必須複製其中許多規則多次。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-105">You will need to copy many of these rules multiple times.</span></span> <span data-ttu-id="bb6cb-106">如果您要監視多個檔案共用，比方說，這會是大小寫。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-106">This is the case if you are monitoring a number of file shares, for example.</span></span> <span data-ttu-id="bb6cb-107">在此案例中，您會複製基底規則一次的每個檔案共用上的 描述 欄位中新增的檔案共用位址**準則**規則 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-107">In this scenario, you would copy the base rule once for each file share with the file share address added in the description field on the **Criteria** tab of the rule.</span></span> <span data-ttu-id="bb6cb-108">藉由新增地址，Operations Manager 將會引發每個個別的檔案共用的警示。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-108">By adding the address, Operations Manager will raise an alert for each individual file share.</span></span> <span data-ttu-id="bb6cb-109">當您複製現有的規則時，請確定您選取**啟用**停用的規則覆寫此規則，或您會收到重複的警示。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-109">When you copy an existing rule, ensure that you select **Enable** rule-disable overrides for this rule or you will receive duplicate alerts.</span></span>  
  
    <span data-ttu-id="bb6cb-110">您應該將它新增至您所建立的每個規則的另一個項目位於知識資訊**知識庫**規則屬性 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-110">Another item that you should add to each rule that you create is Knowledge information on the **Knowledge Base** tab of the rule property.</span></span> <span data-ttu-id="bb6cb-111">這項資料會附加至 Operations Manager 會傳送出警示時，會引發通知。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-111">This data is attached to the notification that is raised when Operations Manager sends out an alert.</span></span> <span data-ttu-id="bb6cb-112">當您加入可能有助於解決此錯誤的步驟時，便會清楚的這項功能強大。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-112">The power of this feature becomes clear when you include steps that may help resolve the error.</span></span>  
  
2. <span data-ttu-id="bb6cb-113">**建立針對每個已定義的規則動作**</span><span class="sxs-lookup"><span data-stu-id="bb6cb-113">**Create actions for each defined rule**</span></span>  
  
    <span data-ttu-id="bb6cb-114">建立或複製規則其實處理程序的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-114">Creating or copying a rule is really the first step in the process.</span></span> <span data-ttu-id="bb6cb-115">下一個步驟是採取某些動作，根據該規則。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-115">The next step is to take some action based on that rule.</span></span> <span data-ttu-id="bb6cb-116">如果沒有採取任何動作不根據規則則怪罪則不斷監視事件。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-116">If there is no action based on a rule then it doesn’t really matter that the event was ever monitored.</span></span> <span data-ttu-id="bb6cb-117">最常執行的動作為警示操作員或系統管理員所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-117">The action most frequently taken is to alert an operator or administrator that an error has occurred.</span></span> <span data-ttu-id="bb6cb-118">Operations Manager 也會提供數個觸發事件時，可以使用其他動作。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-118">Operations Manager also provides a number of other actions that can be used when an event is triggered.</span></span> <span data-ttu-id="bb6cb-119">這些動作包括：</span><span class="sxs-lookup"><span data-stu-id="bb6cb-119">These actions include:</span></span>  
  
   -   <span data-ttu-id="bb6cb-120">啟動指令碼</span><span class="sxs-lookup"><span data-stu-id="bb6cb-120">Starting a script</span></span>  
  
   -   <span data-ttu-id="bb6cb-121">傳送簡易網路管理通訊協定 (SNMP) 陷阱 （在 SNMP 代理程式來監視各種裝置上的網路和網路主控台工作站的報表中的活動）</span><span class="sxs-lookup"><span data-stu-id="bb6cb-121">Sending a Simple Network Management Protocol (SNMP) trap (in SNMP, agents monitor the activity in the various devices on the network and report to the network console workstation)</span></span>  
  
   -   <span data-ttu-id="bb6cb-122">傳送通知給通知群組</span><span class="sxs-lookup"><span data-stu-id="bb6cb-122">Sending a notification to a Notification group</span></span>  
  
   -   <span data-ttu-id="bb6cb-123">執行命令或批次檔</span><span class="sxs-lookup"><span data-stu-id="bb6cb-123">Executing a command or batch file</span></span>  
  
   -   <span data-ttu-id="bb6cb-124">更新狀態變數</span><span class="sxs-lookup"><span data-stu-id="bb6cb-124">Updating a state variable</span></span>  
  
   -   <span data-ttu-id="bb6cb-125">傳輸檔案</span><span class="sxs-lookup"><span data-stu-id="bb6cb-125">Transferring a file</span></span>  
  
   -   <span data-ttu-id="bb6cb-126">在 managed 程式碼組件上呼叫方法</span><span class="sxs-lookup"><span data-stu-id="bb6cb-126">Calling a method on a managed code assembly</span></span>  
  
3. <span data-ttu-id="bb6cb-127">**建立反覆的程序，以將手動工作自動化**</span><span class="sxs-lookup"><span data-stu-id="bb6cb-127">**Create iterative processes to automate manual tasks**</span></span>  
  
    <span data-ttu-id="bb6cb-128">下一個步驟是反覆的程序，並移出基本的警示機制。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-128">The next step is an iterative process and moves beyond the basic alerting mechanism.</span></span> <span data-ttu-id="bb6cb-129">使用 Operations Manager 能夠叫用指令碼和.NET 程式碼，以引發的事件為基礎的手動工作自動化的程序會是功能強大且時間的儲存功能。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-129">With Operations Manager able to invoke both script and .NET code, the process of automating manual tasks based on raised events is a powerful and time saving feature.</span></span> <span data-ttu-id="bb6cb-130">這個範例是執行指令碼來自動啟動連接埠，如果記錄已停用 / 停止事件訊息。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-130">An example of this is to run a script to automatically start a port if a disabled /stopped event message is logged.</span></span> <span data-ttu-id="bb6cb-131">此程序是反覆的因為可以自動化許多程序。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-131">This process is iterative since many processes can be automated.</span></span>  
  
4. <span data-ttu-id="bb6cb-132">**使用臨界值規則來將手動工作自動化**</span><span class="sxs-lookup"><span data-stu-id="bb6cb-132">**Use threshold rules to automate manual tasks**</span></span>  
  
    <span data-ttu-id="bb6cb-133">處理的下一個步驟是超越消極反應式的警示，並使用臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-133">The next step in processing is to move beyond the reactive alerting and use threshold rules.</span></span> <span data-ttu-id="bb6cb-134">根據預設，BizTalk Server 管理組件不包含任何臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-134">The BizTalk Server Management Pack does not contain any threshold rules by default.</span></span> <span data-ttu-id="bb6cb-135">這是因為這類規則通常專用於自訂的應用程式，並有不同的每個應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-135">This is because such rules are typically specific to the custom application and are different for every application.</span></span> <span data-ttu-id="bb6cb-136">臨界值包含自訂的應用程式的相關商務規則，並提供主動監視系統。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-136">A threshold embodies a business rule regarding the custom application and provides a proactive means of monitoring a system.</span></span> <span data-ttu-id="bb6cb-137">您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所提供的效能分析的記錄檔 (PAL) 工具，來定義規則的臨界值範本。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-137">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] threshold templates provided with the Performance Analysis of Logs (PAL) tool to define rules.</span></span>  
  
    <span data-ttu-id="bb6cb-138">測量在伺服器上的 Cpu 持續執行 75%以上一段特定時間時為這類的臨界值規則範例。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-138">An example of such a threshold rule is to measure when the CPUs on a server consistently run above 75 percent for a specific time period.</span></span> <span data-ttu-id="bb6cb-139">這可能表示您需要相應放大系統。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-139">This could indicate that you need to scale out the system.</span></span> <span data-ttu-id="bb6cb-140">還有另一個範例是您用來建立一組唯一的計數器會監視的臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-140">Yet another example is where you create a threshold rule that monitors a unique set of counters.</span></span> <span data-ttu-id="bb6cb-141">此規則能再叫用程式碼來初始化先前設定的備份伺服器上的 BizTalk 主控件執行個體的高需求期間。</span><span class="sxs-lookup"><span data-stu-id="bb6cb-141">This rule could then invoke code to initialize BizTalk host instances on a previously configured backup server during periods of high demand.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6cb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6cb-142">See Also</span></span>  
 [<span data-ttu-id="bb6cb-143">使用 System Center Operations Manager 2007 監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bb6cb-143">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)