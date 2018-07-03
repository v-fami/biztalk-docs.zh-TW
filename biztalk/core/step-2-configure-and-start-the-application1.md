---
title: 步驟 2： 設定並啟動應用程式 1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8edeb1cdb1f24774ec7c1e615377d81e4393c9dc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024548"
---
# <a name="step-2-configure-and-start-the-application"></a><span data-ttu-id="0311a-102">步驟 2： 設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="0311a-102">Step 2: Configure and Start the Application</span></span>
<span data-ttu-id="0311a-103">![步驟 3 之 2](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="0311a-103">![Step 2 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="0311a-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="0311a-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="0311a-105">**目標：** 在此步驟中，您需要設定並啟動 EAISolution 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0311a-105">**Objective:** In this step, you configure and start the EAISolution application.</span></span>  
  
 <span data-ttu-id="0311a-106">**用途：** 組態是多半關於繫結。</span><span class="sxs-lookup"><span data-stu-id="0311a-106">**Purpose:** The configuration is mostly about binding.</span></span>  <span data-ttu-id="0311a-107">繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。</span><span class="sxs-lookup"><span data-stu-id="0311a-107">A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party.</span></span> <span data-ttu-id="0311a-108">這讓通訊能在不同的 BizTalk 商務方案元件之間進行。</span><span class="sxs-lookup"><span data-stu-id="0311a-108">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="0311a-109">您可以使用 [BizTalk Server 管理主控台] 建立繫結。</span><span class="sxs-lookup"><span data-stu-id="0311a-109">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0311a-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="0311a-110">Prerequisites</span></span>  
 <span data-ttu-id="0311a-111">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="0311a-111">Note the following requirements before you begin this step:</span></span>  
  
- <span data-ttu-id="0311a-112">在開始此步驟之前必須先完成[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="0311a-112">Before you begin this step you must complete [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md).</span></span>  
  
- <span data-ttu-id="0311a-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0311a-113">You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0311a-114">程序</span><span class="sxs-lookup"><span data-stu-id="0311a-114">Procedures</span></span>  
 <span data-ttu-id="0311a-115">BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。</span><span class="sxs-lookup"><span data-stu-id="0311a-115">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="0311a-116">BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="0311a-116">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span>  <span data-ttu-id="0311a-117">如需詳細資訊，請參閱 <<c0> [ 什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0311a-117">For more information, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md).</span></span>  <span data-ttu-id="0311a-118">在 [步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)，我們設定應用程式名稱是"EAISolution"，然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="0311a-118">In [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md), we configure the application name to be “EAISolution” before we deploy the projects.</span></span>  <span data-ttu-id="0311a-119">因此，EAISolution 應用程式包含協調流程、兩個結構描述以及對應。</span><span class="sxs-lookup"><span data-stu-id="0311a-119">So the EAISolution application contains the orchestration, the two schema, and the map.</span></span>  
  
#### <a name="to-open-the-eaisolution-application-from-biztalk-server-administration-console"></a><span data-ttu-id="0311a-120">若要從 BizTalk Server 管理主控台開啟 EAISolution 應用程式</span><span class="sxs-lookup"><span data-stu-id="0311a-120">To open the EAISolution application from BizTalk Server Administration Console</span></span>  
  
1. <span data-ttu-id="0311a-121">按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0311a-121">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2. <span data-ttu-id="0311a-122">在主控台樹狀目錄中的左邊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="0311a-122">In the console tree on the left side of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3. <span data-ttu-id="0311a-123">依序展開**BizTalk 群組**，展開**應用程式**，然後按一下**EAISolution**。</span><span class="sxs-lookup"><span data-stu-id="0311a-123">Expand **BizTalk Group**, expand **Applications**, and then click **EAISolution**.</span></span>  
  
   <span data-ttu-id="0311a-124">在 [第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)，我們建立了協調流程。</span><span class="sxs-lookup"><span data-stu-id="0311a-124">In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), we created an orchestration.</span></span>  <span data-ttu-id="0311a-125">在協調流程中，我們定義了邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="0311a-125">In the orchestration, we defined the logical ports.</span></span>  <span data-ttu-id="0311a-126">在下列程序中，您將會定義實體連接埠，並將實體連接埠繫結至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="0311a-126">In the following procedures, you will define the physical ports and bind the physical ports to the logical ports.</span></span>  
  
#### <a name="to-create-the-receiverequest-port"></a><span data-ttu-id="0311a-127">若要建立 ReceiveRequest 連接埠</span><span class="sxs-lookup"><span data-stu-id="0311a-127">To create the ReceiveRequest port</span></span>  
  
1.  <span data-ttu-id="0311a-128">BizTalk Server 管理主控台，從下**EAISolution**節點，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0311a-128">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="0311a-129">在 [一般] 索引標籤中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0311a-129">On the General tab,  do the following:</span></span>  
  
    |<span data-ttu-id="0311a-130">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-130">Use this</span></span>|<span data-ttu-id="0311a-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-132">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-132">**Name**</span></span>|<span data-ttu-id="0311a-133">型別**EAISolutionReceiveRequestPort**。</span><span class="sxs-lookup"><span data-stu-id="0311a-133">Type **EAISolutionReceiveRequestPort**.</span></span>|  
    |<span data-ttu-id="0311a-134">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="0311a-134">**Enable routing for failed messages**</span></span>|<span data-ttu-id="0311a-135">(清除)</span><span class="sxs-lookup"><span data-stu-id="0311a-135">(clear)</span></span>|  
  
3.  <span data-ttu-id="0311a-136">按一下 **接收位置**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0311a-136">Click **Receive Locations**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="0311a-137">從 [Receive Location1 - 接收位置屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-137">From Receive Location1 – Receive Location Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-138">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-138">Use this</span></span>|<span data-ttu-id="0311a-139">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-140">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-140">**Name**</span></span>|<span data-ttu-id="0311a-141">型別**EAISolutionReceiveRequestLocation**。</span><span class="sxs-lookup"><span data-stu-id="0311a-141">Type **EAISolutionReceiveRequestLocation**.</span></span>|  
    |<span data-ttu-id="0311a-142">**型別**</span><span class="sxs-lookup"><span data-stu-id="0311a-142">**Type**</span></span>|<span data-ttu-id="0311a-143">選取 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="0311a-143">Select **File**.</span></span>|  
    |<span data-ttu-id="0311a-144">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="0311a-144">**Receive handler**</span></span>|<span data-ttu-id="0311a-145">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="0311a-145">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="0311a-146">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="0311a-146">**Receive pipeline**</span></span>|<span data-ttu-id="0311a-147">選取  **XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="0311a-147">Select **XMLReceive**.</span></span>|  
  
5.  <span data-ttu-id="0311a-148">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0311a-148">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="0311a-149">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-149">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-150">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-150">Use this</span></span>|<span data-ttu-id="0311a-151">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-151">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-152">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="0311a-152">**Receive folder**</span></span>|<span data-ttu-id="0311a-153">型別**C:\BTSTutorials\WareHouse\Request**。</span><span class="sxs-lookup"><span data-stu-id="0311a-153">Type **C:\BTSTutorials\WareHouse\Request**.</span></span>|  
  
7.  <span data-ttu-id="0311a-154">按一下 **確定**三次。</span><span class="sxs-lookup"><span data-stu-id="0311a-154">Click **OK** three times.</span></span>  
  
#### <a name="to-create-the-senddecline-port"></a><span data-ttu-id="0311a-155">若要建立 SendDecline 連接埠</span><span class="sxs-lookup"><span data-stu-id="0311a-155">To create the SendDecline port</span></span>  
  
1.  <span data-ttu-id="0311a-156">BizTalk Server 管理主控台，從下**EAISolution**節點，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0311a-156">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="0311a-157">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-157">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-158">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-158">Use this</span></span>|<span data-ttu-id="0311a-159">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-159">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-160">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-160">**Name**</span></span>|<span data-ttu-id="0311a-161">型別**EAISolutionSendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="0311a-161">Type **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="0311a-162">**型別**</span><span class="sxs-lookup"><span data-stu-id="0311a-162">**Type**</span></span>|<span data-ttu-id="0311a-163">選取 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="0311a-163">Select **File**.</span></span>|  
    |<span data-ttu-id="0311a-164">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="0311a-164">**Send handler**</span></span>|<span data-ttu-id="0311a-165">選取  **BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0311a-165">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="0311a-166">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="0311a-166">**Send pipeline**</span></span>|<span data-ttu-id="0311a-167">選取  **XML 傳輸**。</span><span class="sxs-lookup"><span data-stu-id="0311a-167">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="0311a-168">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0311a-168">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="0311a-169">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-169">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-170">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-170">Use this</span></span>|<span data-ttu-id="0311a-171">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-171">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-172">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="0311a-172">**Receive folder**</span></span>|<span data-ttu-id="0311a-173">型別**C:\BTSTutorials\WareHouse\RequestDecline**。</span><span class="sxs-lookup"><span data-stu-id="0311a-173">Type **C:\BTSTutorials\WareHouse\RequestDecline**.</span></span>|  
    |<span data-ttu-id="0311a-174">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-174">**File name**</span></span>|<span data-ttu-id="0311a-175">型別**RequestDecline_%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="0311a-175">Type **RequestDecline_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="0311a-176">按兩次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0311a-176">Click **OK** twice.</span></span>  
  
#### <a name="to-create-the-sendtoerp-port"></a><span data-ttu-id="0311a-177">若要建立 SendToERP 連接埠</span><span class="sxs-lookup"><span data-stu-id="0311a-177">To create the SendToERP port</span></span>  
  
1.  <span data-ttu-id="0311a-178">BizTalk Server 管理主控台，從下**EAISolution**節點，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0311a-178">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="0311a-179">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-179">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-180">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-180">Use this</span></span>|<span data-ttu-id="0311a-181">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-181">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-182">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-182">**Name**</span></span>|<span data-ttu-id="0311a-183">型別**EAISolutionSendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="0311a-183">Type **EAISolutionSendToERPPort**.</span></span>|  
    |<span data-ttu-id="0311a-184">**型別**</span><span class="sxs-lookup"><span data-stu-id="0311a-184">**Type**</span></span>|<span data-ttu-id="0311a-185">選取 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="0311a-185">Select **File**.</span></span>|  
    |<span data-ttu-id="0311a-186">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="0311a-186">**Send handler**</span></span>|<span data-ttu-id="0311a-187">選取  **BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0311a-187">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="0311a-188">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="0311a-188">**Send pipeline**</span></span>|<span data-ttu-id="0311a-189">選取  **XML 傳輸**。</span><span class="sxs-lookup"><span data-stu-id="0311a-189">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="0311a-190">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0311a-190">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="0311a-191">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0311a-191">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-192">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-192">Use this</span></span>|<span data-ttu-id="0311a-193">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-193">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-194">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="0311a-194">**Receive folder**</span></span>|<span data-ttu-id="0311a-195">型別**C:\BTSTutorials\ERP\Request**。</span><span class="sxs-lookup"><span data-stu-id="0311a-195">Type **C:\BTSTutorials\ERP\Request**.</span></span>|  
    |<span data-ttu-id="0311a-196">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="0311a-196">**File name**</span></span>|<span data-ttu-id="0311a-197">型別**Request_%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="0311a-197">Type **Request_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="0311a-198">按兩次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0311a-198">Click **OK** twice.</span></span>  
  
#### <a name="to-bind-the-ports"></a><span data-ttu-id="0311a-199">若要繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="0311a-199">To bind the ports</span></span>  
  
1.  <span data-ttu-id="0311a-200">從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0311a-200">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="0311a-201">從 設定應用程式，在左窗格中，按一下**EAIProcess**。</span><span class="sxs-lookup"><span data-stu-id="0311a-201">From Configure Application, in the left pane, click **EAIProcess**.</span></span>  <span data-ttu-id="0311a-202">這是我們建立的協調流程。</span><span class="sxs-lookup"><span data-stu-id="0311a-202">This is the orchestration we created.</span></span>  
  
3.  <span data-ttu-id="0311a-203">從右窗格中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0311a-203">From the right pane, do the following:</span></span>  
  
    |<span data-ttu-id="0311a-204">使用</span><span class="sxs-lookup"><span data-stu-id="0311a-204">Use this</span></span>|<span data-ttu-id="0311a-205">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0311a-205">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0311a-206">**主控件**</span><span class="sxs-lookup"><span data-stu-id="0311a-206">**Host**</span></span>|<span data-ttu-id="0311a-207">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="0311a-207">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="0311a-208">**接收埠**針對**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="0311a-208">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="0311a-209">選取  **eaisolutionreceivereqeustport**。</span><span class="sxs-lookup"><span data-stu-id="0311a-209">Select **EAISolutionReceiveReqeustPort**.</span></span>|  
    |<span data-ttu-id="0311a-210">**傳送埠與傳送埠群組**針對**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="0311a-210">**Send PortsSend Port Groups** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="0311a-211">選取  **EAISolutionSendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="0311a-211">Select **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="0311a-212">**接收埠**針對**ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="0311a-212">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="0311a-213">選取  **EAISolutionSendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="0311a-213">Select **EAISolutionSendToERPPort**.</span></span>|  
  
4.  <span data-ttu-id="0311a-214">按一下 **確定**儲存設定。</span><span class="sxs-lookup"><span data-stu-id="0311a-214">Click **OK** to save the configuration.</span></span>  
  
#### <a name="to-start-the-application"></a><span data-ttu-id="0311a-215">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="0311a-215">To start the application</span></span>  
  
1.  <span data-ttu-id="0311a-216">從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="0311a-216">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Start**.</span></span>  
  
2.  <span data-ttu-id="0311a-217">在對話方塊中，按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0311a-217">From the dialog, click **Start**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="0311a-218">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="0311a-218">What did I just do?</span></span>  
 <span data-ttu-id="0311a-219">在此步驟中，您設定和啟動了 EAIApplication 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0311a-219">In this step, you configured and started the EAIApplication application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0311a-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0311a-220">Next Steps</span></span>  
 <span data-ttu-id="0311a-221">您可以測試 EAI 方案處理訊息的方式[步驟 3： 測試方案](../core/step-3-test-the-solution2.md)。</span><span class="sxs-lookup"><span data-stu-id="0311a-221">You test how the EAI solution processes messages in [Step 3: Test the Solution](../core/step-3-test-the-solution2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0311a-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0311a-222">See Also</span></span>  
 <span data-ttu-id="0311a-223">[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md) </span><span class="sxs-lookup"><span data-stu-id="0311a-223">[Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md) </span></span>  
 [<span data-ttu-id="0311a-224">步驟 3：測試解決方案</span><span class="sxs-lookup"><span data-stu-id="0311a-224">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)