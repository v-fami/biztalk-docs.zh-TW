---
title: "執行 Orchestrations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- creating strong name keys
- compiling orchestrations
- host instances, stopping and restarting
- deployment, orchestrations
- orchestrations, compiling
- orchestrations, deploying
- stopping host instances
- restarting host instances
ms.assetid: a098d552-d302-44f6-9af9-d77d16549fd3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a2d6ef6752965c1f20c695dacb06ff348089054
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="running-orchestrations"></a><span data-ttu-id="7cc37-102">執行協調流程</span><span class="sxs-lookup"><span data-stu-id="7cc37-102">Running Orchestrations</span></span>
<span data-ttu-id="7cc37-103">下列程序說明如何建置、部署、繫結和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="7cc37-103">The following procedures describe how to build, deploy, bind, and start an orchestration.</span></span>  
  
## <a name="creating-a-strong-name-key"></a><span data-ttu-id="7cc37-104">建立強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="7cc37-104">Creating a Strong Name Key</span></span>  
  
#### <a name="to-create-a-strong-name-key"></a><span data-ttu-id="7cc37-105">若要建立強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="7cc37-105">To create a strong name key</span></span>  
  
1.  <span data-ttu-id="7cc37-106">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7cc37-106">Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="7cc37-107">將目錄變更為現有的專案，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7cc37-107">Change directories to an existing project and press ENTER.</span></span>  
  
     <span data-ttu-id="7cc37-108">例如：</span><span class="sxs-lookup"><span data-stu-id="7cc37-108">For example:</span></span>  
  
     <span data-ttu-id="7cc37-109">**\<磁碟機 >: \Adapter_Install\biztalk\my_project**</span><span class="sxs-lookup"><span data-stu-id="7cc37-109">**\<drive>:\Adapter_Install\biztalk\my_project**</span></span>  
  
3.  <span data-ttu-id="7cc37-110">在命令提示字元中輸入下列文字，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="7cc37-110">Type the following at the command prompt and press ENTER:</span></span>  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a><span data-ttu-id="7cc37-111">編譯和部署協調流程</span><span class="sxs-lookup"><span data-stu-id="7cc37-111">Compiling and Deploying an Orchestration</span></span>  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a><span data-ttu-id="7cc37-112">若要編譯和部署協調流程</span><span class="sxs-lookup"><span data-stu-id="7cc37-112">To compile and deploy an orchestration</span></span>  
  
1.  <span data-ttu-id="7cc37-113">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下**SSOSchedule**專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-113">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the **SSOSchedule** project, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="7cc37-114">按一下**通用屬性**，然後展開**組件**節點。</span><span class="sxs-lookup"><span data-stu-id="7cc37-114">Click **Common Properties**, and expand the **Assembly** node.</span></span>  
  
3.  <span data-ttu-id="7cc37-115">輸入的路徑中輸入 ssoschedule.snk**組件金鑰檔案**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7cc37-115">Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.</span></span>  
  
4.  <span data-ttu-id="7cc37-116">確認 Configuration Properties\Deployment\Server 是一個點 （.） 或您的電腦名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-116">Verify that Configuration Properties\Deployment\Server is a dot (.) or your computer name, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="7cc37-117">在 方案總管 中，以滑鼠右鍵按一下**SSOSchedule**，然後按一下 **重建**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-117">In Solution Explorer, right-click **SSOSchedule**, and then click **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="7cc37-118">以滑鼠右鍵按一下**SSOSchedule**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-118">Right-click **SSOSchedule**, and then click **Deploy**.</span></span>  
  
## <a name="starting-the-orchestration"></a><span data-ttu-id="7cc37-119">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="7cc37-119">Starting the Orchestration</span></span>  
  
#### <a name="to-start-the-orchestration"></a><span data-ttu-id="7cc37-120">若要啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="7cc37-120">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="7cc37-121">按一下**啟動**，指向**所有程式**，指向 **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 [ **BizTalk Server 管理]。**</span><span class="sxs-lookup"><span data-stu-id="7cc37-121">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="7cc37-122">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開所需應用程式，，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-122">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand the desired application, and then click **Orchestrations**.</span></span>  
  
3.  <span data-ttu-id="7cc37-123">在詳細資料窗格中，以滑鼠右鍵按一下協調流程，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-123">In the details pane, right-click the orchestration and click **Start**.</span></span>  
  
## <a name="stopping-and-restarting-a-host-instance"></a><span data-ttu-id="7cc37-124">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="7cc37-124">Stopping and Restarting a Host Instance</span></span>  
 <span data-ttu-id="7cc37-125">部署範例之後，您必須重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cc37-125">After you deploy the sample, you must restart the host instance.</span></span>  
  
#### <a name="to-stop-and-restart-a-host-instance"></a><span data-ttu-id="7cc37-126">若要停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="7cc37-126">To stop and restart a host instance</span></span>  
  
1.  <span data-ttu-id="7cc37-127">按一下**啟動**，指向**所有程式**，指向 **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 [ **BizTalk Server 管理]。**</span><span class="sxs-lookup"><span data-stu-id="7cc37-127">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="7cc37-128">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-128">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="7cc37-129">在右窗格中，以滑鼠右鍵按一下主控件執行個體 （例如，電腦名稱），然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-129">In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.</span></span>  
  
     <span data-ttu-id="7cc37-130">主控件執行個體狀態會變更為**已停止**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-130">The status of the host instance changes to **Stopped**.</span></span>  
  
4.  <span data-ttu-id="7cc37-131">在右窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-131">In the right pane, right-click the host instance and click **Start**.</span></span>  
  
     <span data-ttu-id="7cc37-132">主控件執行個體狀態會變更為**開始擱置**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-132">The status of the host instance changes to **Start pending**.</span></span>  
  
     <span data-ttu-id="7cc37-133">若要將狀態變更為**執行**按一下**重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="7cc37-133">To change the status to **Running** and click **Refresh**, or right-click the host instance and then click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc37-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cc37-134">See Also</span></span>  
 [<span data-ttu-id="7cc37-135">保護配接器</span><span class="sxs-lookup"><span data-stu-id="7cc37-135">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)