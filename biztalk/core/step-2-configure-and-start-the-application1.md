---
title: "步驟 2： 設定並啟動 Application1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc9c3c027126d3a461bf99329b70fda57b9be647
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-and-start-the-application"></a><span data-ttu-id="d1cbd-102">步驟 2： 設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="d1cbd-102">Step 2: Configure and Start the Application</span></span>
<span data-ttu-id="d1cbd-103">![步驟 3 之 2](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="d1cbd-103">![Step 2 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="d1cbd-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="d1cbd-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="d1cbd-105">**目標：**在此步驟中，設定並啟動 EAISolution 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-105">**Objective:** In this step, you configure and start the EAISolution application.</span></span>  
  
 <span data-ttu-id="d1cbd-106">**用途：**是多半關於繫結的組態。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-106">**Purpose:** The configuration is mostly about binding.</span></span>  <span data-ttu-id="d1cbd-107">繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-107">A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party.</span></span> <span data-ttu-id="d1cbd-108">這讓通訊能在不同的 BizTalk 商務方案元件之間進行。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-108">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="d1cbd-109">您可以使用 [BizTalk Server 管理主控台] 建立繫結。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-109">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d1cbd-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="d1cbd-110">Prerequisites</span></span>  
 <span data-ttu-id="d1cbd-111">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-111">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="d1cbd-112">在開始此步驟之前必須先完成[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-112">Before you begin this step you must complete [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md).</span></span>  
  
-   <span data-ttu-id="d1cbd-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分來登入。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-113">You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d1cbd-114">程序</span><span class="sxs-lookup"><span data-stu-id="d1cbd-114">Procedures</span></span>  
 <span data-ttu-id="d1cbd-115">BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-115">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="d1cbd-116">BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-116">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span>  <span data-ttu-id="d1cbd-117">如需詳細資訊，請參閱[什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-117">For more information, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md).</span></span>  <span data-ttu-id="d1cbd-118">在[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)，我們設定的應用程式名稱是"EAISolution"，然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-118">In [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md), we configure the application name to be “EAISolution” before we deploy the projects.</span></span>  <span data-ttu-id="d1cbd-119">因此，EAISolution 應用程式包含協調流程、兩個結構描述以及對應。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-119">So the EAISolution application contains the orchestration, the two schema, and the map.</span></span>  
  
#### <a name="to-open-the-eaisolution-application-from-biztalk-server-administration-console"></a><span data-ttu-id="d1cbd-120">若要從 BizTalk Server 管理主控台開啟 EAISolution 應用程式</span><span class="sxs-lookup"><span data-stu-id="d1cbd-120">To open the EAISolution application from BizTalk Server Administration Console</span></span>  
  
1.  <span data-ttu-id="d1cbd-121">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-121">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="d1cbd-122">左邊的主控台樹狀目錄中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-122">In the console tree on the left side of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="d1cbd-123">展開**BizTalk 群組**，依序展開**應用程式**，然後按一下  **EAISolution**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-123">Expand **BizTalk Group**, expand **Applications**, and then click **EAISolution**.</span></span>  
  
 <span data-ttu-id="d1cbd-124">在[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)，我們建立了協調流程。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-124">In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), we created an orchestration.</span></span>  <span data-ttu-id="d1cbd-125">在協調流程中，我們定義了邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-125">In the orchestration, we defined the logical ports.</span></span>  <span data-ttu-id="d1cbd-126">在下列程序中，您將會定義實體連接埠，並將實體連接埠繫結至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-126">In the following procedures, you will define the physical ports and bind the physical ports to the logical ports.</span></span>  
  
#### <a name="to-create-the-receiverequest-port"></a><span data-ttu-id="d1cbd-127">若要建立 ReceiveRequest 連接埠</span><span class="sxs-lookup"><span data-stu-id="d1cbd-127">To create the ReceiveRequest port</span></span>  
  
1.  <span data-ttu-id="d1cbd-128">BizTalk Server 管理主控台，從下**EAISolution** ] 節點，以滑鼠右鍵按一下**接收埠**，指向 [**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-128">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="d1cbd-129">在 [一般] 索引標籤上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-129">On the General tab,  do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-130">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-130">Use this</span></span>|<span data-ttu-id="d1cbd-131">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-132">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-132">**Name**</span></span>|<span data-ttu-id="d1cbd-133">型別**EAISolutionReceiveRequestPort**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-133">Type **EAISolutionReceiveRequestPort**.</span></span>|  
    |<span data-ttu-id="d1cbd-134">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-134">**Enable routing for failed messages**</span></span>|<span data-ttu-id="d1cbd-135">(清除)</span><span class="sxs-lookup"><span data-stu-id="d1cbd-135">(clear)</span></span>|  
  
3.  <span data-ttu-id="d1cbd-136">按一下**接收位置**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-136">Click **Receive Locations**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="d1cbd-137">從 [Receive Location1 - 接收位置屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-137">From Receive Location1 – Receive Location Properties, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-138">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-138">Use this</span></span>|<span data-ttu-id="d1cbd-139">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-140">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-140">**Name**</span></span>|<span data-ttu-id="d1cbd-141">型別**EAISolutionReceiveRequestLocation**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-141">Type **EAISolutionReceiveRequestLocation**.</span></span>|  
    |<span data-ttu-id="d1cbd-142">**型別**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-142">**Type**</span></span>|<span data-ttu-id="d1cbd-143">選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-143">Select **File**.</span></span>|  
    |<span data-ttu-id="d1cbd-144">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-144">**Receive handler**</span></span>|<span data-ttu-id="d1cbd-145">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-145">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="d1cbd-146">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-146">**Receive pipeline**</span></span>|<span data-ttu-id="d1cbd-147">選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-147">Select **XMLReceive**.</span></span>|  
  
5.  <span data-ttu-id="d1cbd-148">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-148">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="d1cbd-149">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-149">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-150">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-150">Use this</span></span>|<span data-ttu-id="d1cbd-151">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-151">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-152">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-152">**Receive folder**</span></span>|<span data-ttu-id="d1cbd-153">型別**C:\BTSTutorials\WareHouse\Request**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-153">Type **C:\BTSTutorials\WareHouse\Request**.</span></span>|  
  
7.  <span data-ttu-id="d1cbd-154">按一下**確定**三次。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-154">Click **OK** three times.</span></span>  
  
#### <a name="to-create-the-senddecline-port"></a><span data-ttu-id="d1cbd-155">若要建立 SendDecline 連接埠</span><span class="sxs-lookup"><span data-stu-id="d1cbd-155">To create the SendDecline port</span></span>  
  
1.  <span data-ttu-id="d1cbd-156">從 BizTalk Server 管理主控台，在**EAISolution** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-156">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="d1cbd-157">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-157">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-158">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-158">Use this</span></span>|<span data-ttu-id="d1cbd-159">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-159">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-160">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-160">**Name**</span></span>|<span data-ttu-id="d1cbd-161">型別**EAISolutionSendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-161">Type **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="d1cbd-162">**型別**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-162">**Type**</span></span>|<span data-ttu-id="d1cbd-163">選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-163">Select **File**.</span></span>|  
    |<span data-ttu-id="d1cbd-164">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-164">**Send handler**</span></span>|<span data-ttu-id="d1cbd-165">選取**BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-165">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="d1cbd-166">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-166">**Send pipeline**</span></span>|<span data-ttu-id="d1cbd-167">選取**XML 傳輸**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-167">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="d1cbd-168">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-168">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="d1cbd-169">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-169">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-170">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-170">Use this</span></span>|<span data-ttu-id="d1cbd-171">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-171">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-172">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-172">**Receive folder**</span></span>|<span data-ttu-id="d1cbd-173">型別**C:\BTSTutorials\WareHouse\RequestDecline**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-173">Type **C:\BTSTutorials\WareHouse\RequestDecline**.</span></span>|  
    |<span data-ttu-id="d1cbd-174">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-174">**File name**</span></span>|<span data-ttu-id="d1cbd-175">型別**RequestDecline_%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-175">Type **RequestDecline_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="d1cbd-176">按兩次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-176">Click **OK** twice.</span></span>  
  
#### <a name="to-create-the-sendtoerp-port"></a><span data-ttu-id="d1cbd-177">若要建立 SendToERP 連接埠</span><span class="sxs-lookup"><span data-stu-id="d1cbd-177">To create the SendToERP port</span></span>  
  
1.  <span data-ttu-id="d1cbd-178">從 BizTalk Server 管理主控台，在**EAISolution** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-178">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="d1cbd-179">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-179">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-180">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-180">Use this</span></span>|<span data-ttu-id="d1cbd-181">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-181">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-182">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-182">**Name**</span></span>|<span data-ttu-id="d1cbd-183">型別**EAISolutionSendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-183">Type **EAISolutionSendToERPPort**.</span></span>|  
    |<span data-ttu-id="d1cbd-184">**型別**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-184">**Type**</span></span>|<span data-ttu-id="d1cbd-185">選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-185">Select **File**.</span></span>|  
    |<span data-ttu-id="d1cbd-186">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-186">**Send handler**</span></span>|<span data-ttu-id="d1cbd-187">選取**BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-187">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="d1cbd-188">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-188">**Send pipeline**</span></span>|<span data-ttu-id="d1cbd-189">選取**XML 傳輸**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-189">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="d1cbd-190">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-190">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="d1cbd-191">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-191">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-192">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-192">Use this</span></span>|<span data-ttu-id="d1cbd-193">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-193">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-194">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-194">**Receive folder**</span></span>|<span data-ttu-id="d1cbd-195">型別**C:\BTSTutorials\ERP\Request**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-195">Type **C:\BTSTutorials\ERP\Request**.</span></span>|  
    |<span data-ttu-id="d1cbd-196">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-196">**File name**</span></span>|<span data-ttu-id="d1cbd-197">型別**Request_%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-197">Type **Request_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="d1cbd-198">按兩次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-198">Click **OK** twice.</span></span>  
  
#### <a name="to-bind-the-ports"></a><span data-ttu-id="d1cbd-199">若要繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="d1cbd-199">To bind the ports</span></span>  
  
1.  <span data-ttu-id="d1cbd-200">從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-200">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="d1cbd-201">設定應用程式，從左窗格中，按一下**EAIProcess**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-201">From Configure Application, in the left pane, click **EAIProcess**.</span></span>  <span data-ttu-id="d1cbd-202">這是我們建立的協調流程。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-202">This is the orchestration we created.</span></span>  
  
3.  <span data-ttu-id="d1cbd-203">從右窗格中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d1cbd-203">From the right pane, do the following:</span></span>  
  
    |<span data-ttu-id="d1cbd-204">使用</span><span class="sxs-lookup"><span data-stu-id="d1cbd-204">Use this</span></span>|<span data-ttu-id="d1cbd-205">動作</span><span class="sxs-lookup"><span data-stu-id="d1cbd-205">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d1cbd-206">**Host**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-206">**Host**</span></span>|<span data-ttu-id="d1cbd-207">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-207">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="d1cbd-208">**接收埠**如**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-208">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="d1cbd-209">選取**[eaisolutionreceivereqeustport]**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-209">Select **EAISolutionReceiveReqeustPort**.</span></span>|  
    |<span data-ttu-id="d1cbd-210">**傳送埠與傳送埠群組**如**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-210">**Send PortsSend Port Groups** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="d1cbd-211">選取**EAISolutionSendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-211">Select **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="d1cbd-212">**接收埠**如**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="d1cbd-212">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="d1cbd-213">選取**EAISolutionSendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-213">Select **EAISolutionSendToERPPort**.</span></span>|  
  
4.  <span data-ttu-id="d1cbd-214">按一下**確定**儲存設定。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-214">Click **OK** to save the configuration.</span></span>  
  
#### <a name="to-start-the-application"></a><span data-ttu-id="d1cbd-215">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="d1cbd-215">To start the application</span></span>  
  
1.  <span data-ttu-id="d1cbd-216">從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-216">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Start**.</span></span>  
  
2.  <span data-ttu-id="d1cbd-217">從對話方塊中，按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-217">From the dialog, click **Start**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d1cbd-218">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="d1cbd-218">What did I just do?</span></span>  
 <span data-ttu-id="d1cbd-219">在此步驟中，您設定和啟動了 EAIApplication 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-219">In this step, you configured and started the EAIApplication application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d1cbd-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d1cbd-220">Next Steps</span></span>  
 <span data-ttu-id="d1cbd-221">您可以測試 EAI 方案處理訊息中的方式[步驟 3： 測試方案](../core/step-3-test-the-solution2.md)。</span><span class="sxs-lookup"><span data-stu-id="d1cbd-221">You test how the EAI solution processes messages in [Step 3: Test the Solution](../core/step-3-test-the-solution2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1cbd-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1cbd-222">See Also</span></span>  
 <span data-ttu-id="d1cbd-223">[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md) </span><span class="sxs-lookup"><span data-stu-id="d1cbd-223">[Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md) </span></span>  
 [<span data-ttu-id="d1cbd-224">步驟 3： 測試方案</span><span class="sxs-lookup"><span data-stu-id="d1cbd-224">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)