---
title: 監視應用程式 |Microsoft 文件
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
ms.openlocfilehash: 67c937ae0edb1698991ad111622a582ebfc64d76
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008979"
---
# <a name="monitoring-applications"></a><span data-ttu-id="cd083-102">監視應用程式</span><span class="sxs-lookup"><span data-stu-id="cd083-102">Monitoring Applications</span></span>
<span data-ttu-id="cd083-103">設定 Microsoft System Center Operations Manager 來監視 BizTalk 應用程式通常可以分成漸進式的四個步驟程序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd083-103">Setting up Microsoft System Center Operations Manager to monitor BizTalk applications typically can be broken down into a progressive four-step process as follows:</span></span>  
  
1.  <span data-ttu-id="cd083-104">**修改現有的規則和/或複製的規則，以自訂的管理組件來監視自訂 BizTalk 應用程式**</span><span class="sxs-lookup"><span data-stu-id="cd083-104">**Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application**</span></span>  
  
     <span data-ttu-id="cd083-105">您必須將複製其中許多規則多次。</span><span class="sxs-lookup"><span data-stu-id="cd083-105">You will need to copy many of these rules multiple times.</span></span> <span data-ttu-id="cd083-106">如果您要監視的數字的檔案共用，例如，這是大小寫。</span><span class="sxs-lookup"><span data-stu-id="cd083-106">This is the case if you are monitoring a number of file shares, for example.</span></span> <span data-ttu-id="cd083-107">在此案例中，您會複製基底規則一次的每個檔案共用上的描述欄位中加入的檔案共用位址**準則**規則 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cd083-107">In this scenario, you would copy the base rule once for each file share with the file share address added in the description field on the **Criteria** tab of the rule.</span></span> <span data-ttu-id="cd083-108">藉由新增地址，Operations Manager 將會引發警示的每個個別的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="cd083-108">By adding the address, Operations Manager will raise an alert for each individual file share.</span></span> <span data-ttu-id="cd083-109">當您複製現有的規則時，請確定您選取**啟用**規則停用覆寫此規則，或您會收到重複的警示。</span><span class="sxs-lookup"><span data-stu-id="cd083-109">When you copy an existing rule, ensure that you select **Enable** rule-disable overrides for this rule or you will receive duplicate alerts.</span></span>  
  
     <span data-ttu-id="cd083-110">您應該將它加入至您所建立的每個規則的另一個項目位於知識資訊**知識庫**規則屬性 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cd083-110">Another item that you should add to each rule that you create is Knowledge information on the **Knowledge Base** tab of the rule property.</span></span> <span data-ttu-id="cd083-111">這項資料會附加至 Operations Manager 會送出警示時，會引發通知。</span><span class="sxs-lookup"><span data-stu-id="cd083-111">This data is attached to the notification that is raised when Operations Manager sends out an alert.</span></span> <span data-ttu-id="cd083-112">包含可協助解決此錯誤的步驟，這項功能的能力會變得清楚。</span><span class="sxs-lookup"><span data-stu-id="cd083-112">The power of this feature becomes clear when you include steps that may help resolve the error.</span></span>  
  
2.  <span data-ttu-id="cd083-113">**建立每個已定義的規則動作**</span><span class="sxs-lookup"><span data-stu-id="cd083-113">**Create actions for each defined rule**</span></span>  
  
     <span data-ttu-id="cd083-114">在建立或修改規則實際上是程序的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="cd083-114">Creating or copying a rule is really the first step in the process.</span></span> <span data-ttu-id="cd083-115">下一個步驟是要採取某些動作，根據該規則。</span><span class="sxs-lookup"><span data-stu-id="cd083-115">The next step is to take some action based on that rule.</span></span> <span data-ttu-id="cd083-116">如果沒有採取任何動作不以規則然後其實並沒有差別曾經監視事件。</span><span class="sxs-lookup"><span data-stu-id="cd083-116">If there is no action based on a rule then it doesn’t really matter that the event was ever monitored.</span></span> <span data-ttu-id="cd083-117">最常執行的動作是要警示的操作員或系統管理員發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd083-117">The action most frequently taken is to alert an operator or administrator that an error has occurred.</span></span> <span data-ttu-id="cd083-118">Operations Manager 也提供數個其他的事件觸發時，可以使用的動作。</span><span class="sxs-lookup"><span data-stu-id="cd083-118">Operations Manager also provides a number of other actions that can be used when an event is triggered.</span></span> <span data-ttu-id="cd083-119">這些動作包括：</span><span class="sxs-lookup"><span data-stu-id="cd083-119">These actions include:</span></span>  
  
    -   <span data-ttu-id="cd083-120">啟動指令碼</span><span class="sxs-lookup"><span data-stu-id="cd083-120">Starting a script</span></span>  
  
    -   <span data-ttu-id="cd083-121">傳送簡易網路管理通訊協定 (SNMP) 陷阱 （在 SNMP 代理程式監視的各種裝置上的網路和網路主控台工作站的報表中的活動）</span><span class="sxs-lookup"><span data-stu-id="cd083-121">Sending a Simple Network Management Protocol (SNMP) trap (in SNMP, agents monitor the activity in the various devices on the network and report to the network console workstation)</span></span>  
  
    -   <span data-ttu-id="cd083-122">傳送通知給通知群組</span><span class="sxs-lookup"><span data-stu-id="cd083-122">Sending a notification to a Notification group</span></span>  
  
    -   <span data-ttu-id="cd083-123">執行命令或批次檔</span><span class="sxs-lookup"><span data-stu-id="cd083-123">Executing a command or batch file</span></span>  
  
    -   <span data-ttu-id="cd083-124">更新狀態變數</span><span class="sxs-lookup"><span data-stu-id="cd083-124">Updating a state variable</span></span>  
  
    -   <span data-ttu-id="cd083-125">檔案傳輸</span><span class="sxs-lookup"><span data-stu-id="cd083-125">Transferring a file</span></span>  
  
    -   <span data-ttu-id="cd083-126">Managed 程式碼組件上呼叫方法</span><span class="sxs-lookup"><span data-stu-id="cd083-126">Calling a method on a managed code assembly</span></span>  
  
3.  <span data-ttu-id="cd083-127">**建立自動化手動工作的反覆程序**</span><span class="sxs-lookup"><span data-stu-id="cd083-127">**Create iterative processes to automate manual tasks**</span></span>  
  
     <span data-ttu-id="cd083-128">下一個步驟是反覆的程序，並移出基本警示機制。</span><span class="sxs-lookup"><span data-stu-id="cd083-128">The next step is an iterative process and moves beyond the basic alerting mechanism.</span></span> <span data-ttu-id="cd083-129">使用 Operations Manager 可以叫用指令碼和.NET 程式碼，自動化手動工作引發的事件為基礎的程序是功能強大且時間儲存功能。</span><span class="sxs-lookup"><span data-stu-id="cd083-129">With Operations Manager able to invoke both script and .NET code, the process of automating manual tasks based on raised events is a powerful and time saving feature.</span></span> <span data-ttu-id="cd083-130">這個範例是執行指令碼來自動啟動的通訊埠，如果記錄已停用 / 停止事件訊息。</span><span class="sxs-lookup"><span data-stu-id="cd083-130">An example of this is to run a script to automatically start a port if a disabled /stopped event message is logged.</span></span> <span data-ttu-id="cd083-131">此程序，因為可以自動化許多處理序。</span><span class="sxs-lookup"><span data-stu-id="cd083-131">This process is iterative since many processes can be automated.</span></span>  
  
4.  <span data-ttu-id="cd083-132">**使用來自動化手動工作的臨界值規則**</span><span class="sxs-lookup"><span data-stu-id="cd083-132">**Use threshold rules to automate manual tasks**</span></span>  
  
     <span data-ttu-id="cd083-133">在處理下一個步驟是超越反應靈敏的警示，並使用臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="cd083-133">The next step in processing is to move beyond the reactive alerting and use threshold rules.</span></span> <span data-ttu-id="cd083-134">BizTalk Server 管理組件預設不包含任何臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="cd083-134">The BizTalk Server Management Pack does not contain any threshold rules by default.</span></span> <span data-ttu-id="cd083-135">這是因為這類規則通常專用於自訂應用程式，以及每個應用程式不同。</span><span class="sxs-lookup"><span data-stu-id="cd083-135">This is because such rules are typically specific to the custom application and are different for every application.</span></span> <span data-ttu-id="cd083-136">臨界值意自訂應用程式的相關商務規則，並提供主動式方法來監視系統。</span><span class="sxs-lookup"><span data-stu-id="cd083-136">A threshold embodies a business rule regarding the custom application and provides a proactive means of monitoring a system.</span></span> <span data-ttu-id="cd083-137">您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供使用效能分析的記錄檔 (PAL) 工具來定義規則的臨界值範本。</span><span class="sxs-lookup"><span data-stu-id="cd083-137">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] threshold templates provided with the Performance Analysis of Logs (PAL) tool to define rules.</span></span>  
  
     <span data-ttu-id="cd083-138">臨界值規則的範例是在伺服器上的 Cpu 一致的方式執行時超過 75%一段特定時間量值。</span><span class="sxs-lookup"><span data-stu-id="cd083-138">An example of such a threshold rule is to measure when the CPUs on a server consistently run above 75 percent for a specific time period.</span></span> <span data-ttu-id="cd083-139">這可能表示您需要向外擴充系統。</span><span class="sxs-lookup"><span data-stu-id="cd083-139">This could indicate that you need to scale out the system.</span></span> <span data-ttu-id="cd083-140">尚未另一個範例是您用來建立一組唯一的計數器會監視的臨界值規則。</span><span class="sxs-lookup"><span data-stu-id="cd083-140">Yet another example is where you create a threshold rule that monitors a unique set of counters.</span></span> <span data-ttu-id="cd083-141">此規則無法再叫用先前設定的備份伺服器上的 BizTalk 主控件執行個體初始化期間需求較高的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd083-141">This rule could then invoke code to initialize BizTalk host instances on a previously configured backup server during periods of high demand.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd083-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd083-142">See Also</span></span>  
 [<span data-ttu-id="cd083-143">使用 System Center Operations Manager 2007 監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cd083-143">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)