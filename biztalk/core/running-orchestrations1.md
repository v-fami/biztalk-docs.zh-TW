---
title: 執行 Orchestrations1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- host instances, stopping and restarting
- orchestrations, compiling
- orchestrations, deploying
ms.assetid: b992bdba-630d-4f28-aca8-c568f3c27968
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe1645ecaff4cea4f153c988188fa7f47e94959c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969119"
---
# <a name="running-orchestrations"></a><span data-ttu-id="ddfe0-102">執行協調流程</span><span class="sxs-lookup"><span data-stu-id="ddfe0-102">Running Orchestrations</span></span>
<span data-ttu-id="ddfe0-103">下列程序說明如何建置、部署、繫結和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-103">The following procedures describe how to build, deploy, bind, and start an orchestration.</span></span>  
  
## <a name="creating-a-strong-name-key"></a><span data-ttu-id="ddfe0-104">建立強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="ddfe0-104">Creating a Strong Name Key</span></span>  
  
#### <a name="to-create-a-strong-name-key"></a><span data-ttu-id="ddfe0-105">若要建立強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="ddfe0-105">To create a strong name key</span></span>  
  
1. <span data-ttu-id="ddfe0-106">啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-106">Start a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.</span></span>  
  
2. <span data-ttu-id="ddfe0-107">例如，將目錄變更為現有的專案中，\<磁碟機\>: \Adapter_Install\biztalk2010\my_project。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-107">Change directories to an existing project, for example, \<drive\>:\Adapter_Install\biztalk2010\my_project.</span></span>  
  
3. <span data-ttu-id="ddfe0-108">在命令提示字元中輸入下列文字，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="ddfe0-108">Type the following in the command prompt and press ENTER:</span></span>  
  
    `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a><span data-ttu-id="ddfe0-109">編譯和部署協調流程</span><span class="sxs-lookup"><span data-stu-id="ddfe0-109">Compiling and Deploying an Orchestration</span></span>  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a><span data-ttu-id="ddfe0-110">若要編譯和部署協調流程</span><span class="sxs-lookup"><span data-stu-id="ddfe0-110">To compile and deploy an orchestration</span></span>  
  
1. <span data-ttu-id="ddfe0-111">在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下 SSOSchedule 專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-111">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the SSOSchedule project, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="ddfe0-112">按一下 **通用屬性**，展開**組件**節點。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-112">Click **Common Properties**, and expand the **Assembly** node.</span></span>  
  
3. <span data-ttu-id="ddfe0-113">輸入的路徑中輸入 ssoschedule.snk**組件金鑰檔案**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-113">Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.</span></span>  
  
4. <span data-ttu-id="ddfe0-114">確認 Configuration properties\deployment\server 中包含點 （.） 或您的電腦名稱，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-114">Verify that Configuration Properties\Deployment\Server contains a dot (.) or your computer name, and click **OK**.</span></span>  
  
5. <span data-ttu-id="ddfe0-115">在 [方案總管] 中，以滑鼠右鍵按一下**SSOSchedule**，然後按一下**重建**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-115">In Solution Explorer, right-click **SSOSchedule**, and click **Rebuild**.</span></span>  
  
6. <span data-ttu-id="ddfe0-116">以滑鼠右鍵按一下**SSOSchedule**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-116">Right-click the **SSOSchedule**, and click **Deploy**.</span></span>  
  
## <a name="starting-the-orchestration"></a><span data-ttu-id="ddfe0-117">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="ddfe0-117">Starting the Orchestration</span></span>  
  
#### <a name="to-start-the-orchestration"></a><span data-ttu-id="ddfe0-118">若要啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="ddfe0-118">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="ddfe0-119">在 BizTalk 管理主控台中，選取您想要啟動的協調流程。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-119">In the BizTalk Administration console, select the orchestration you want to start.</span></span>  
  
2.  <span data-ttu-id="ddfe0-120">以滑鼠右鍵按一下協調流程，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-120">Right-click the orchestration and click **Start**.</span></span>  
  
## <a name="stopping-and-restarting-a-host-instance"></a><span data-ttu-id="ddfe0-121">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="ddfe0-121">Stopping and Restarting a Host Instance</span></span>  
 <span data-ttu-id="ddfe0-122">部署範例之後，您必須重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-122">After deploying the sample, you must restart the host instance.</span></span>  
  
#### <a name="to-stop-and-restart-a-host-instance"></a><span data-ttu-id="ddfe0-123">若要停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="ddfe0-123">To stop and restart a host instance</span></span>  
  
1. <span data-ttu-id="ddfe0-124">按一下 [**開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後選取**BizTalk Server 管理]。**</span><span class="sxs-lookup"><span data-stu-id="ddfe0-124">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and select **BizTalk Server Administration.**</span></span>  
  
2. <span data-ttu-id="ddfe0-125">在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**Microsoft BizTalk Server （本機）** ] 節點，展開**主機**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-125">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the **Microsoft BizTalk Server (local)** node, and expand **Hosts**.</span></span>  
  
3. <span data-ttu-id="ddfe0-126">在左窗格中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-126">In the left pane, select the **BizTalkServerApplication**.</span></span>  
  
4. <span data-ttu-id="ddfe0-127">在右窗格中，請以滑鼠右鍵按一下主控件執行個體 （例如，電腦名稱），然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-127">In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.</span></span>  
  
    <span data-ttu-id="ddfe0-128">主控件執行個體狀態會變更為**已停止**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-128">The status of the host instance changes to **Stopped**.</span></span>  
  
5. <span data-ttu-id="ddfe0-129">在右窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-129">In the right pane, right-click the host instance and click **Start**.</span></span>  
  
    <span data-ttu-id="ddfe0-130">主控件執行個體狀態會變更為**開始擱置**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-130">The status of the host instance changes to **Start pending**.</span></span>  
  
    <span data-ttu-id="ddfe0-131">若要將狀態變更為**執行**，按一下**重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="ddfe0-131">To change the status to **Running**, click **Refresh**, or right-click the host instance and then click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfe0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddfe0-132">See Also</span></span>  
 [<span data-ttu-id="ddfe0-133">配接器中的安全性</span><span class="sxs-lookup"><span data-stu-id="ddfe0-133">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)