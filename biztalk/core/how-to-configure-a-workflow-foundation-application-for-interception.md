---
title: 如何設定用於攔截的 Workflow Foundation 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c82e83f-9dbd-4325-9f30-778eba892296
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6929161360b2b3af1bfe221e9fa3583d93b566
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967801"
---
# <a name="how-to-configure-a-workflow-foundation-application-for-interception"></a><span data-ttu-id="69519-102">如何設定用於攔截的 Workflow Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="69519-102">How to Configure a Workflow Foundation Application for Interception</span></span>
<span data-ttu-id="69519-103">您必須安裝 BAM 攔截器軟體，並設定應用程式使用 [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] 攔截器服務，才能開始收集 BAM 活動資料。</span><span class="sxs-lookup"><span data-stu-id="69519-103">You must install the BAM interceptor software and configure your application to use the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor service before you can begin collecting BAM activity data.</span></span> <span data-ttu-id="69519-104">假設您已成功安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及其相依性，而且至少已建立一個 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="69519-104">It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.</span></span>  
  
## <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="69519-105">安裝 BAM-Eventing 軟體</span><span class="sxs-lookup"><span data-stu-id="69519-105">Installing the BAM-Eventing Software</span></span>  
 <span data-ttu-id="69519-106">您必須使用 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 安裝程式安裝 BAM-Eventing 軟體，才能將 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式設定為使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BAM 攔截器。</span><span class="sxs-lookup"><span data-stu-id="69519-106">Before you can configure your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="69519-107">如需有關安裝 Bam-eventing 軟體和註冊效能計數器的詳細資訊，請參閱 <<c0> [ 安裝 Bam-eventing 軟體](../core/installing-the-bam-eventing-software.md)。</span><span class="sxs-lookup"><span data-stu-id="69519-107">For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).</span></span>  
  
## <a name="configuring-a-windows-workflow-foundation-application-for-tracking"></a><span data-ttu-id="69519-108">設定用於追蹤的 Windows Workflow Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="69519-108">Configuring a Windows Workflow Foundation Application for Tracking</span></span>  
 <span data-ttu-id="69519-109">[!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式可以開始寫入 BAM 事件資訊前，必須先完成四項工作：</span><span class="sxs-lookup"><span data-stu-id="69519-109">Four tasks must be completed before your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application can begin writing BAM event information:</span></span>  
  
- <span data-ttu-id="69519-110">必須利用建立觀察模型[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BAM 工具，並接著使用 「 BAM 管理員命令列工具 (bm.exe) 部署。</span><span class="sxs-lookup"><span data-stu-id="69519-110">An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command-line tool (bm.exe).</span></span>  
  
- <span data-ttu-id="69519-111">必須使用 BAM 管理員命令列工具 (bm.exe) 建立及部署攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="69519-111">An interceptor configuration file must be created and deployed by using the BAM Manager command line-tool (bm.exe).</span></span>  
  
- <span data-ttu-id="69519-112">執行主應用程式的使用者必須屬於適當 BAM 活動事件寫入器 (bam_\<活動\>_EventWriter) 讓應用程式來讀取攔截器組態資訊和寫入的 SQL Server 角色BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="69519-112">The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity\>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.</span></span>  
  
- <span data-ttu-id="69519-113">App.config 檔案或應用程式本身必須經過修改，才能載入 BAM 追蹤服務並接著重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="69519-113">The App.config file or the application itself must be modified to load the BAM tracking service and then restart the application.</span></span>  
  
  <span data-ttu-id="69519-114">唯有成功完成這些工作，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 資料庫內才會開始出現事件。</span><span class="sxs-lookup"><span data-stu-id="69519-114">Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.</span></span>  
  
### <a name="deploying-an-observation-model"></a><span data-ttu-id="69519-115">部署觀察模型</span><span class="sxs-lookup"><span data-stu-id="69519-115">Deploying an Observation Model</span></span>  
 <span data-ttu-id="69519-116">您必須部署觀察模型，才能部署攔截器組態檔或擷取您應用程式中的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="69519-116">You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.</span></span>  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a><span data-ttu-id="69519-117">若要使用 bm.exe 部署觀察模型</span><span class="sxs-lookup"><span data-stu-id="69519-117">To deploy an observation model by using bm.exe</span></span>  
  
1. <span data-ttu-id="69519-118">按一下 **開始**，然後按一下**執行**開啟 Windows 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="69519-118">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2. <span data-ttu-id="69519-119">型別**cmd**中**開放**欄位，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="69519-119">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="69519-120">使用變更目錄命令移至內含要部署之觀察模型的目錄。</span><span class="sxs-lookup"><span data-stu-id="69519-120">Use the change directory command to move to the directory containing the observation model to deploy.</span></span> <span data-ttu-id="69519-121">例如， **cd c:\businessprocess\Orders**。</span><span class="sxs-lookup"><span data-stu-id="69519-121">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4. <span data-ttu-id="69519-122">使用 bm.exe 部署觀察模型：</span><span class="sxs-lookup"><span data-stu-id="69519-122">Deploy the observation model by using bm.exe:</span></span>  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="69519-123">Tracking\BM.exe 部署所有-definitionfile:\<*definitionfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="69519-123">Tracking\BM.exe deploy-all -definitionfile:\<*definitionfile.xml*\></span></span>  
  
    <span data-ttu-id="69519-124">請確定您取代\< *definitionfile.xml* \>具有您想要部署的觀察檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="69519-124">Make sure you replace \<*definitionfile.xml*\> with the name of the observation file you want to deploy.</span></span> <span data-ttu-id="69519-125">如需其他選項請參閱[攔截器管理命令](../core/interceptor-management-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="69519-125">For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="69519-126">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="69519-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5. <span data-ttu-id="69519-127">型別**結束**，然後按 ENTER 關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="69519-127">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
### <a name="deploying-an-interceptor-configuration-file"></a><span data-ttu-id="69519-128">部署攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="69519-128">Deploying an Interceptor Configuration File</span></span>  
 <span data-ttu-id="69519-129">您必須部署攔截器組態檔，應用程式才能擷取 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="69519-129">You must deploy an interceptor configuration file before your application can capture BAM activities.</span></span>  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a><span data-ttu-id="69519-130">若要使用 bm.exe 部署攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="69519-130">To deploy an interceptor configuration file by using bm.exe</span></span>  
  
1. <span data-ttu-id="69519-131">按一下 **開始**，然後按一下**執行**開啟 Windows 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="69519-131">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2. <span data-ttu-id="69519-132">型別**cmd**中**開放**欄位，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="69519-132">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="69519-133">使用變更目錄命令移至內含要部署之攔截器組態檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="69519-133">Use the change directory command to move to the directory containing the interceptor configuration file to deploy.</span></span> <span data-ttu-id="69519-134">例如， **cd c:\businessprocess\Orders**。</span><span class="sxs-lookup"><span data-stu-id="69519-134">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4. <span data-ttu-id="69519-135">使用 bm.exe 部署攔截器組態檔：</span><span class="sxs-lookup"><span data-stu-id="69519-135">Deploy the interceptor configuration file by using bm.exe:</span></span>  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="69519-136">Tracking\BM.exe 部署攔截器-filename:\<*icfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="69519-136">Tracking\BM.exe deploy-interceptor -filename:\<*icfile.xml*\></span></span>  
  
    <span data-ttu-id="69519-137">請確定您取代\< *icfile.xml* \>您想要部署攔截器組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="69519-137">Make sure you replace \<*icfile.xml*\> with the name of the interceptor configuration file you want to deploy.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="69519-138">您可以使用 **-Force: True**旗標，以覆寫現有的事件來源的攔截器組態檔中的相同名稱。</span><span class="sxs-lookup"><span data-stu-id="69519-138">You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file.</span></span> <span data-ttu-id="69519-139">如果您這樣做，請務必先備份使用現有的組態**取得攔截器**命令。</span><span class="sxs-lookup"><span data-stu-id="69519-139">If you do so, make sure you back up the existing configuration by using the **get-interceptor** command.</span></span> <span data-ttu-id="69519-140">使用 -Force:True 旗標可能會刪除任何參考要覆寫之事件來源的攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="69519-140">Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="69519-141">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="69519-141">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5. <span data-ttu-id="69519-142">型別**結束**，然後按 ENTER 關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="69519-142">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
   <span data-ttu-id="69519-143">若您已經部署 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式，在下一個輪詢間隔前，不會載入新組態。</span><span class="sxs-lookup"><span data-stu-id="69519-143">If you have already deployed your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval.</span></span> <span data-ttu-id="69519-144">然而，您若設定並重新啟動應用程式，就會立即收取組態。</span><span class="sxs-lookup"><span data-stu-id="69519-144">However, if you configure your application and restart it, the configuration will be picked up immediately.</span></span>  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a><span data-ttu-id="69519-145">加入使用者至適合的 BAM 活動角色</span><span class="sxs-lookup"><span data-stu-id="69519-145">Adding the User to the Appropriate BAM Activity Role</span></span>  
 <span data-ttu-id="69519-146">BAM 攔截器架構會讓每個活動使用一個 SQL Server 角色，控制活動和組態資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="69519-146">The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information.</span></span> <span data-ttu-id="69519-147">您必須將執行 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式的使用者帳戶，加入至 BAM 主要匯入資料庫內的適當 BAM 活動角色。</span><span class="sxs-lookup"><span data-stu-id="69519-147">You must add the user account running your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to the appropriate BAM activity role(s) in the BAM Primary Import database.</span></span>  
  
### <a name="configuring-the-application-to-load-the-bam-tracking-service"></a><span data-ttu-id="69519-148">設定應用程式以載入 BAM 追蹤服務</span><span class="sxs-lookup"><span data-stu-id="69519-148">Configuring the Application to Load the BAM Tracking Service</span></span>  
 <span data-ttu-id="69519-149">在 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式載入 BAM 追蹤服務的實例有三種：</span><span class="sxs-lookup"><span data-stu-id="69519-149">There are three scenarios for loading the BAM tracking service in your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application:</span></span>  
  
- <span data-ttu-id="69519-150">若 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式已經使用 WorkflowRuntime 載入 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 組態區段，則您可以將 BAM 追蹤服務資訊加入至現有區段。</span><span class="sxs-lookup"><span data-stu-id="69519-150">If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application already uses WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you can added BAM tracking service information to the existing section.</span></span>  
  
- <span data-ttu-id="69519-151">若 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式並未使用 WorkflowRuntime 載入 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 組態區段，則您必須新增程式碼才能從應用程式組態檔載入自訂區段。</span><span class="sxs-lookup"><span data-stu-id="69519-151">If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application does not use WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you will have to add code to load a custom section from your application configuration file.</span></span> <span data-ttu-id="69519-152">您必須建立區段，並在該區段加入 BAM 追蹤服務資訊。</span><span class="sxs-lookup"><span data-stu-id="69519-152">You will have to create the section and add the BAM tracking service information to it.</span></span>  
  
- <span data-ttu-id="69519-153">若您想選擇以硬式編碼的方式寫入組態，可以使用 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] API 以程式設計的方式載入追蹤服務 (無須組態檔)，或從自訂來源載入組態。</span><span class="sxs-lookup"><span data-stu-id="69519-153">If you prefer to hard-code the configuration, you can use the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] API to programmatically load the tracking service without a configuration file, or to load the configuration from a custom source.</span></span>  
  
  <span data-ttu-id="69519-154">設定 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式時，請注意下列考量：</span><span class="sxs-lookup"><span data-stu-id="69519-154">When configuring the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, note the following considerations:</span></span>  
  
- <span data-ttu-id="69519-155">[!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 攔截器每一個 WorkflowRuntime 只支援一個 BamTrackingService。</span><span class="sxs-lookup"><span data-stu-id="69519-155">The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports only one BamTrackingService per one WorkflowRuntime.</span></span>  
  
- <span data-ttu-id="69519-156">[!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 攔截器的每個應用程式網域支援多個 BamTrackingService 執行個體。</span><span class="sxs-lookup"><span data-stu-id="69519-156">The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports multiple BamTrackingService instances per application domain.</span></span>  
  
  -   <span data-ttu-id="69519-157">N 個 WorkflowRuntime 就支援 N 個 BamTrackingService。</span><span class="sxs-lookup"><span data-stu-id="69519-157">N number of BamTrackingService is supported for N number of WorkflowRuntime.</span></span>  
  
- <span data-ttu-id="69519-158">若同一個應用程式網域中，不同的 BamTrackingService 執行個體使用不同的連線字串，攔截器就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69519-158">The interceptor raises an exception if different connection strings are used for separate BamTrackingService instances in the same application domain.</span></span>  
  
- <span data-ttu-id="69519-159">攔截器會從第一個啟動的 BamTrackingService 執行個體取得 IC 輪詢間隔值。</span><span class="sxs-lookup"><span data-stu-id="69519-159">The interceptor obtains the IC polling interval value from the first BamTrackingService instance that starts.</span></span>  
  
- <span data-ttu-id="69519-160">應用程式網域中的最後一個 BamTrackingService 停止時，攔截器就會停止 IC 輪詢執行緒。</span><span class="sxs-lookup"><span data-stu-id="69519-160">The interceptor stops the IC polling thread when last BamTrackingService in application domain is stopped</span></span>  
  
  <span data-ttu-id="69519-161">如需 WorkflowRuntime 和載入組態資訊的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=83314 ](http://go.microsoft.com/fwlink/?LinkId=83314)。</span><span class="sxs-lookup"><span data-stu-id="69519-161">For more information on WorkflowRuntime and loading configuration information, see [http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314).</span></span>  
  
##### <a name="to-configure-the-appconfig-file-for-the-bam-tracking-service"></a><span data-ttu-id="69519-162">若要設定 BAM 追蹤服務的 App.config 檔案</span><span class="sxs-lookup"><span data-stu-id="69519-162">To configure the App.config file for the BAM tracking service</span></span>  
  
1.  <span data-ttu-id="69519-163">開啟與應用程式關聯的 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="69519-163">Open the App.config file associated with your application.</span></span> <span data-ttu-id="69519-164">使用 Notepad.exe 或其他文字編輯器開啟即可。</span><span class="sxs-lookup"><span data-stu-id="69519-164">You can use Notepad.exe or another text editor for this task.</span></span>  
  
2.  <span data-ttu-id="69519-165">將下列組態資訊插入 App.config 檔案以新增 BAM 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="69519-165">Add the BAM Tracking service by inserting the following configuration information into the App.config file.</span></span> <span data-ttu-id="69519-166">請定位該資訊，讓它成為 `configuration` 元素的子系。</span><span class="sxs-lookup"><span data-stu-id="69519-166">It should be positioned so that it is a child of the `configuration` element.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69519-167">Section 項目應該對應至使用 WorkflowRuntime 類別時，您的應用程式程式碼所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="69519-167">The section element should correspond to the name used by your application code when using the WorkflowRuntime class.</span></span>  
  
    ```  
    <!-- The element name must match the one expected by WorkflowRuntime in your WF application -->  
    <WorkflowServiceContainer>  
      <Services>  
        <add type="Microsoft.BizTalk.Bam.Interceptors.Workflow.BamTrackingService, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
       ConnectionString="Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"   
          PollingIntervalSec="5"/>  
        </Services>  
    </WorkflowServiceContainer>  
    ```  
  
3.  <span data-ttu-id="69519-168">修改**ConnectionString**屬性，以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="69519-168">Modify the **ConnectionString** attribute to match your environment.</span></span>  
  
4.  <span data-ttu-id="69519-169">重新啟動您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69519-169">Restart your application.</span></span>  
  
##### <a name="to-modify-your-application-to-load-a-custom-configuration-section"></a><span data-ttu-id="69519-170">若要修改應用程式以載入自訂組態區段</span><span class="sxs-lookup"><span data-stu-id="69519-170">To modify your application to load a custom configuration section</span></span>  
  
1.  <span data-ttu-id="69519-171">在 Visual Studio 中開啟 Windows Workflow Foundation 專案。</span><span class="sxs-lookup"><span data-stu-id="69519-171">Open your Windows Workflow Foundation project in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="69519-172">將具有適合之參數的新 BamTrackingService 執行個體，加入至應用程式的 WorkflowRuntime 執行個體：</span><span class="sxs-lookup"><span data-stu-id="69519-172">Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:</span></span>  
  
    ```  
    // !! Replace "WorkflowServiceContainer" with the section name  
    // you used in your App.config file.  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime("WorkflowServiceContainer");  
    ```  
  
3.  <span data-ttu-id="69519-173">重新編譯並部署修改後的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69519-173">Recompile and deploy the modified application.</span></span>  
  
##### <a name="to-modify-your-application-to-programmatically-load-the-bam-tracking-service"></a><span data-ttu-id="69519-174">若要修改應用程式以透過程式設計的方式載入 BAM 追蹤服務</span><span class="sxs-lookup"><span data-stu-id="69519-174">To modify your application to programmatically load the BAM tracking service</span></span>  
  
1.  <span data-ttu-id="69519-175">在 Visual Studio 中開啟 Windows Workflow Foundation 專案。</span><span class="sxs-lookup"><span data-stu-id="69519-175">Open your Windows Workflow Foundation project in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="69519-176">將具有適合之參數的新 BamTrackingService 執行個體，加入至應用程式的 WorkflowRuntime 執行個體：</span><span class="sxs-lookup"><span data-stu-id="69519-176">Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:</span></span>  
  
    ```  
    string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"  
    int pollingInterval = 5;  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
    workflowRuntime.AddService(new BamTrackingService(connectionString, pollingInterval));  
    ```  
  
     <span data-ttu-id="69519-177">您可根據特定環境新增或移除參數。</span><span class="sxs-lookup"><span data-stu-id="69519-177">You can add or remove parameters based on your specific environment.</span></span>  
  
3.  <span data-ttu-id="69519-178">重新編譯並部署修改後的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69519-178">Recompile and deploy the modified application.</span></span>