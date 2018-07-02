---
title: 若要重新啟動服務，或關閉的步驟 |Microsoft Docs
description: 啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務，或關閉 BizTalk Server 電腦
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d6449ba-2892-49c6-a697-847608d10ec5
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b83e7573117749ce78789de0ba21ef63ebed217
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987887"
---
# <a name="restart-biztalk-services-or-shut-down-the-biztalk-server"></a><span data-ttu-id="6386e-103">重新啟動 BizTalk 服務，或關閉 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6386e-103">Restart BizTalk services, or shut down the BizTalk Server</span></span>

<span data-ttu-id="6386e-104">您可啟動、停止、暫停、繼續或重新啟動下表列出的 BizTalk Server 服務：</span><span class="sxs-lookup"><span data-stu-id="6386e-104">The following table lists the BizTalk Server services that you can start, stop, pause, resume, or restart:</span></span>  
  
|<span data-ttu-id="6386e-105">[屬性]</span><span class="sxs-lookup"><span data-stu-id="6386e-105">Name</span></span>|<span data-ttu-id="6386e-106">描述</span><span class="sxs-lookup"><span data-stu-id="6386e-106">Description</span></span>|<span data-ttu-id="6386e-107">啟動類型</span><span class="sxs-lookup"><span data-stu-id="6386e-107">Startup Type</span></span>|<span data-ttu-id="6386e-108">相依性</span><span class="sxs-lookup"><span data-stu-id="6386e-108">Dependencies</span></span>|  
|----------|-----------------|------------------|------------------|  
|<span data-ttu-id="6386e-109">BizTalk 服務 BizTalk 群組：  *\<BizTalkServerApplication\>*</span><span class="sxs-lookup"><span data-stu-id="6386e-109">BizTalk Service BizTalk Group: *\<BizTalkServerApplication\>*</span></span>|<span data-ttu-id="6386e-110">提供 BizTalk Server 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="6386e-110">Provides the BizTalk Server application service.</span></span>|<span data-ttu-id="6386e-111">Automatic</span><span class="sxs-lookup"><span data-stu-id="6386e-111">Automatic</span></span>|<span data-ttu-id="6386e-112">企業單一登入 (SSO) 服務</span><span class="sxs-lookup"><span data-stu-id="6386e-112">-   Enterprise Single Sign-On (SSO) Service</span></span><br /><span data-ttu-id="6386e-113">-事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="6386e-113">-   Event Log</span></span><br /><span data-ttu-id="6386e-114">-遠端程序呼叫 (RPC)</span><span class="sxs-lookup"><span data-stu-id="6386e-114">-   Remote Procedure Call (RPC)</span></span>|  
|<span data-ttu-id="6386e-115">企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="6386e-115">Enterprise Single Sign-On Service</span></span>|<span data-ttu-id="6386e-116">提供單一登入服務給企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="6386e-116">Provides single sign-on services to enterprise applications.</span></span>|<span data-ttu-id="6386e-117">Automatic</span><span class="sxs-lookup"><span data-stu-id="6386e-117">Automatic</span></span>|<span data-ttu-id="6386e-118">SQL Server 在本機安裝：</span><span class="sxs-lookup"><span data-stu-id="6386e-118">With SQL Server installed locally:</span></span><br /><br /> <span data-ttu-id="6386e-119">-COM + 系統應用程式</span><span class="sxs-lookup"><span data-stu-id="6386e-119">-   COM+ System Application</span></span><br /><span data-ttu-id="6386e-120">-遠端程序呼叫 (RPC)</span><span class="sxs-lookup"><span data-stu-id="6386e-120">-   Remote Procedure Call (RPC)</span></span><br /><span data-ttu-id="6386e-121">SQL Server (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="6386e-121">-   SQL Server (MSSQLSERVER)</span></span><br /><br /> <span data-ttu-id="6386e-122">SQL Server 在遠端安裝：</span><span class="sxs-lookup"><span data-stu-id="6386e-122">With SQL Server installed remotely:</span></span><br /><br /> <span data-ttu-id="6386e-123">-COM + 系統應用程式</span><span class="sxs-lookup"><span data-stu-id="6386e-123">-   COM+ System Application</span></span><br /><span data-ttu-id="6386e-124">-遠端程序呼叫 (RPC) 無</span><span class="sxs-lookup"><span data-stu-id="6386e-124">-   Remote Procedure Call (RPC)None</span></span>|  
|<span data-ttu-id="6386e-125">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="6386e-125">Rule Engine Update Service</span></span>|<span data-ttu-id="6386e-126">通知使用者有關原則的部署或解除部署。</span><span class="sxs-lookup"><span data-stu-id="6386e-126">Notifies users about the deployment or undeployment of policies.</span></span>|<span data-ttu-id="6386e-127">Automatic</span><span class="sxs-lookup"><span data-stu-id="6386e-127">Automatic</span></span>|<span data-ttu-id="6386e-128">無</span><span class="sxs-lookup"><span data-stu-id="6386e-128">None</span></span>|  
  
 
## <a name="start-stop-pause-resume-or-restart-a-biztalk-server-service"></a><span data-ttu-id="6386e-129">啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務</span><span class="sxs-lookup"><span data-stu-id="6386e-129">Start, stop, pause, resume, or restart a BizTalk Server service</span></span>  
 <span data-ttu-id="6386e-130">您可以啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務，使用 Services.msc，或使用命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6386e-130">You can start, stop, pause, resume, or restart a BizTalk Server service by using Services.msc, or using the command prompt.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6386e-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="6386e-131">Prerequisites</span></span>  
 <span data-ttu-id="6386e-132">若要執行此程序，您必須是本機電腦的系統管理員群組的成員，或者必須已經被委派適當的授權。</span><span class="sxs-lookup"><span data-stu-id="6386e-132">To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority.</span></span> <span data-ttu-id="6386e-133">若電腦已加入網域中，則 Domain Admins 群組的成員將可執行此程序。</span><span class="sxs-lookup"><span data-stu-id="6386e-133">If the computer is joined to a domain, members of the Domain Admins group might be able to perform this procedure.</span></span> <span data-ttu-id="6386e-134">最佳的安全作法是考慮使用 [執行身分] 來執行此程序。</span><span class="sxs-lookup"><span data-stu-id="6386e-134">As a security best practice, consider using Run as to perform this procedure.</span></span> 
  
### <a name="use-services-in-control-panel"></a><span data-ttu-id="6386e-135">使用控制台中的服務</span><span class="sxs-lookup"><span data-stu-id="6386e-135">Use Services in Control Panel</span></span>  
  
1.  <span data-ttu-id="6386e-136">開啟 [服務]。</span><span class="sxs-lookup"><span data-stu-id="6386e-136">Open Services.</span></span> <span data-ttu-id="6386e-137">按一下 **開始**，按一下**執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="6386e-137">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
2.  <span data-ttu-id="6386e-138">以滑鼠右鍵按一下適當的 BizTalk Server 服務，然後按一下 **開始**，**停止**，**暫停**，**繼續**，或**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="6386e-138">Right-click the appropriate BizTalk Server service and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
### <a name="use-a-command-prompt"></a><span data-ttu-id="6386e-139">使用命令提示字元</span><span class="sxs-lookup"><span data-stu-id="6386e-139">Use a command prompt</span></span>  
  
1.  <span data-ttu-id="6386e-140">從 [開始] 功能表中，以滑鼠右鍵按一下**命令提示字元**，選取**詳細**，然後選取**系統管理員身分執行**</span><span class="sxs-lookup"><span data-stu-id="6386e-140">From the start menu, right-click **Command prompt**, select **More**, and select **Run as Administrator**</span></span>
  
2.  <span data-ttu-id="6386e-141">輸入下列命令，其中何處*ServiceName*是您想要啟動、 停止、 暫停或繼續的 BizTalk Server 服務名稱：</span><span class="sxs-lookup"><span data-stu-id="6386e-141">Type one of the following, where *ServiceName* is the name of the BizTalk Server service you want to start, stop, pause, or resume:</span></span>  
  
    -   <span data-ttu-id="6386e-142">若要啟動服務，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6386e-142">To start a service, type:</span></span>  
  
         <span data-ttu-id="6386e-143">**net start** *ServiceName*</span><span class="sxs-lookup"><span data-stu-id="6386e-143">**net start** *ServiceName*</span></span>  
  
    -   <span data-ttu-id="6386e-144">若要停止服務，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6386e-144">To stop a service, type:</span></span>  
  
         <span data-ttu-id="6386e-145">**net stop** *ServiceName*</span><span class="sxs-lookup"><span data-stu-id="6386e-145">**net stop** *ServiceName*</span></span>  
  
    -   <span data-ttu-id="6386e-146">若要暫停服務，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6386e-146">To pause a service, type:</span></span>  
  
         <span data-ttu-id="6386e-147">**net pause** *ServiceName*</span><span class="sxs-lookup"><span data-stu-id="6386e-147">**net pause** *ServiceName*</span></span>  
  
    -   <span data-ttu-id="6386e-148">若要繼續服務，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6386e-148">To resume a service, type:</span></span>  
  
         <span data-ttu-id="6386e-149">**net 繼續** *ServiceName*</span><span class="sxs-lookup"><span data-stu-id="6386e-149">**net continue** *ServiceName*</span></span>  

    |<span data-ttu-id="6386e-150">BizTalk 服務</span><span class="sxs-lookup"><span data-stu-id="6386e-150">BizTalk service</span></span>|<span data-ttu-id="6386e-151">ServiceName</span><span class="sxs-lookup"><span data-stu-id="6386e-151">ServiceName</span></span>|  
    |---|---|  
    |<span data-ttu-id="6386e-152">BizTalk 服務 BizTalk 群組：BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="6386e-152">BizTalk Service BizTalk Group: BizTalkServerApplication</span></span>|<span data-ttu-id="6386e-153">btssvc$biztalkserverapplication</span><span class="sxs-lookup"><span data-stu-id="6386e-153">btssvc$biztalkserverapplication</span></span>|  
    |<span data-ttu-id="6386e-154">企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="6386e-154">Enterprise Single Sign-On Service</span></span>|<span data-ttu-id="6386e-155">Entsso</span><span class="sxs-lookup"><span data-stu-id="6386e-155">Entsso</span></span>|  
    |<span data-ttu-id="6386e-156">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="6386e-156">Rule Engine Update Service</span></span>|<span data-ttu-id="6386e-157">ruleengineupdateservice</span><span class="sxs-lookup"><span data-stu-id="6386e-157">ruleengineupdateservice</span></span>|
  
## <a name="shut-down-biztalk-server"></a><span data-ttu-id="6386e-158">關閉 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6386e-158">Shut down BizTalk Server</span></span>  

### <a name="prerequisites"></a><span data-ttu-id="6386e-159">必要條件</span><span class="sxs-lookup"><span data-stu-id="6386e-159">Prerequisites</span></span>  
-   <span data-ttu-id="6386e-160">是您想要關閉的 BizTalk server 上的本機 administrators 群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6386e-160">Sign in with an account that is a member of the local administrators group on the BizTalk server that you want to shut down.</span></span> <span data-ttu-id="6386e-161">這是必要的因此您可以停止服務。</span><span class="sxs-lookup"><span data-stu-id="6386e-161">This is necessary so you can stop services.</span></span>  
-   <span data-ttu-id="6386e-162">使用 BizTalk Server 系統管理員群組或 BizTalk Server 操作員群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6386e-162">Sign in with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> 

### <a name="task-overview"></a><span data-ttu-id="6386e-163">工作概觀</span><span class="sxs-lookup"><span data-stu-id="6386e-163">Task overview</span></span>
1. <span data-ttu-id="6386e-164">停用接收位置，並停止協調流程，並且透過對每個作用中的應用程式中執行部分停止傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6386e-164">Disable receive locations, and stop orchestrations and send ports by performing a partial stop on every active application.</span></span> <span data-ttu-id="6386e-165">只有當您想要移除或重新部署應用程式，您應該執行完全停止。</span><span class="sxs-lookup"><span data-stu-id="6386e-165">You should perform a full stop only if you intend to remove or redeploy an application.</span></span> <span data-ttu-id="6386e-166">如需詳細資訊，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6386e-166">For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
2. <span data-ttu-id="6386e-167">停止主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="6386e-167">Stop host instances.</span></span> <span data-ttu-id="6386e-168">如需詳細資訊，請參閱 <<c0> [ 如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="6386e-168">For more information, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
3. <span data-ttu-id="6386e-169">關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="6386e-169">Shut down [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="6386e-170">請參閱**如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services** （在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="6386e-170">See **How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services** (in this topic).</span></span>
  
4. <span data-ttu-id="6386e-171">關閉向下網際網路資訊服務 (IIS)，或停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式集區和網站。</span><span class="sxs-lookup"><span data-stu-id="6386e-171">Shut down Internet Information Services (IIS), or stop [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application pools and Web sites.</span></span> <span data-ttu-id="6386e-172">如果您要關閉伺服器完全您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="6386e-172">If you are going to shut down the server entirely you can skip this step.</span></span> <span data-ttu-id="6386e-173">如果您停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]進行維護，或以部署或解除部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中，您應該執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="6386e-173">If you are stopping [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for maintenance or to deploy or undeploy a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, you should perform this step.</span></span> <span data-ttu-id="6386e-174">當您停止 Web 站台和應用程式集區相關聯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，其他與 IIS 相關處理程序將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="6386e-174">When you stop only the Web sites and application pools associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], other IIS-related processes will continue to run.</span></span>  
  
    <span data-ttu-id="6386e-175">進行此步驟取決於您所使用的 IIS 版本某種程度。</span><span class="sxs-lookup"><span data-stu-id="6386e-175">How you proceed with this step depends to some extent on which version of IIS you are using.</span></span> <span data-ttu-id="6386e-176">IIS 6 可讓您停止應用程式集區和網站。</span><span class="sxs-lookup"><span data-stu-id="6386e-176">IIS 6 permits you to stop application pools and Web sites.</span></span> <span data-ttu-id="6386e-177">您也可以使用 IIS 6 停止 IIS 管理服務，關閉所有的 IIS 活動，包括應用程式集區和網站。</span><span class="sxs-lookup"><span data-stu-id="6386e-177">With IIS 6 you can also stop the IIS Admin Service to shut down all IIS activity including application pools and Web sites.</span></span> <span data-ttu-id="6386e-178">IIS 7.0 與 IIS 6.0 中，更接近模組化而且沒有任何可用來停止所有 IIS 7.0 的活動，因此您必須個別都停止網站和應用程式集區的單一參數。</span><span class="sxs-lookup"><span data-stu-id="6386e-178">IIS 7.0 is more modular than IIS 6.0, and there is no single switch you can use to stop all IIS 7.0 activities, so you will need to stop Web sites and application pools separately.</span></span>  
  
    <span data-ttu-id="6386e-179">如需應用程式集區和虛擬應用程式 （網站和 Web 服務） BizTalk Server 所使用的清單，請參閱 <<c0> [ 設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6386e-179">For a list of application pools and virtual applications (Web sites and Web services) used by BizTalk Server, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>  
  
   <span data-ttu-id="6386e-180">如需啟動和停止應用程式集區，在 IIS 中的資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=140513 ](http://go.microsoft.com/fwlink/?LinkID=140513)。</span><span class="sxs-lookup"><span data-stu-id="6386e-180">For information about starting and stopping application pools in IIS, see [http://go.microsoft.com/fwlink/?LinkID=140513](http://go.microsoft.com/fwlink/?LinkID=140513).</span></span>  
  
   <span data-ttu-id="6386e-181">啟動和停止中 IIS Web 伺服器的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=140695 ](http://go.microsoft.com/fwlink/?LinkId=140695)。</span><span class="sxs-lookup"><span data-stu-id="6386e-181">For information about starting and stopping the Web Server in IIS, see [http://go.microsoft.com/fwlink/?LinkId=140695](http://go.microsoft.com/fwlink/?LinkId=140695).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6386e-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6386e-182">See Also</span></span>  
 <span data-ttu-id="6386e-183">[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="6386e-183">[How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="6386e-184">如何停止主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6386e-184">How to Stop a Host Instance</span></span>](../core/how-to-stop-a-host-instance.md)   