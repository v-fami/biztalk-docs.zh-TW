---
title: "步驟 1： 部署專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: "44"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4262b2bb424a339f866f3b4a14ae03c2e507f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-projects"></a><span data-ttu-id="8c8ed-102">步驟 1：部署專案</span><span class="sxs-lookup"><span data-stu-id="8c8ed-102">Step 1: Deploy the Projects</span></span>
<span data-ttu-id="8c8ed-103">![步驟 3 之 1](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="8c8ed-103">![Step 1 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="8c8ed-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="8c8ed-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="8c8ed-105">**目標：**在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-105">**Objective:** In this step, you deploy the EAISchemas and EAIOrchestration projects.</span></span>  
  
 <span data-ttu-id="8c8ed-106">**用途：**當您部署專案或方案在 Visual Studio 中的時，自動建置並部署到指定的應用程式組件。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-106">**Purpose:** When you deploy a project or solution in Visual Studio, the assemblies are automatically built and deployed into the specified application.</span></span> <span data-ttu-id="8c8ed-107">做為此程序的一部分，組件連同協調流程、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-107">As part of this process, the assembly along with the orchestrations, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8c8ed-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="8c8ed-108">Prerequisites</span></span>  
 <span data-ttu-id="8c8ed-109">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="8c8ed-109">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="8c8ed-110">在開始此步驟之前，您必須先完成下列課程：</span><span class="sxs-lookup"><span data-stu-id="8c8ed-110">Before you begin this step you must complete the following lessons:</span></span>  
  
    -   [<span data-ttu-id="8c8ed-111">第 1 課： 定義結構描述和對應</span><span class="sxs-lookup"><span data-stu-id="8c8ed-111">Lesson 1: Define Schemas and a Map</span></span>](../core/lesson-1-define-schemas-and-a-map.md)  
  
    -   [<span data-ttu-id="8c8ed-112">第 2 課： 定義商務程序</span><span class="sxs-lookup"><span data-stu-id="8c8ed-112">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)  
  
-   <span data-ttu-id="8c8ed-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分來登入。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-113">You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
-   <span data-ttu-id="8c8ed-114">在支援使用者帳戶控制 (UAC) 的系統上，您必須使用系統管理權限來執行 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-114">On a system that supports User Account Control (UAC), you must run Visual Studio with Administrative privileges.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8c8ed-115">程序</span><span class="sxs-lookup"><span data-stu-id="8c8ed-115">Procedures</span></span>  
 <span data-ttu-id="8c8ed-116">若要使用 Visual Studio 來部署應用程式，您必須登入 Windows 成為 BizTalk Server 系統管理員群組的成員，然後以系統管理員的身分執行 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-116">To deploy the application using Visual Studio, you must log on Windows as a member of the BizTalk Server Administrators group and run Visual Studio as administrator.</span></span>  <span data-ttu-id="8c8ed-117">否則，您會收到「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-117">Otherwise you will get the “Access is denied” error.</span></span>  
  
#### <a name="to-open-the-solution-with-administrative-privileges"></a><span data-ttu-id="8c8ed-118">若要使用系統管理權限來開啟方案</span><span class="sxs-lookup"><span data-stu-id="8c8ed-118">To open the solution with administrative privileges</span></span>  
  
1.  <span data-ttu-id="8c8ed-119">登入 Windows 成為 BizTalk Server 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-119">Log on Windows as a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="8c8ed-120">啟動**Microsoft Visual Studio**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-120">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
3.  <span data-ttu-id="8c8ed-121">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-121">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="8c8ed-122">在**開啟專案**對話方塊中，瀏覽至**EAISolution.sln**專案方案檔，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-122">In the **Open Project** dialog box, browse to the **EAISolution.sln** project solution file, and then click **Open**.</span></span>  
  
 <span data-ttu-id="8c8ed-123">部署程序要求組件必須是以強式名稱簽署的。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-123">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="8c8ed-124">您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-124">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  <span data-ttu-id="8c8ed-125">此檔案是由教學課程檔案所提供。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-125">This file is provided by the tutorial files.</span></span>  
  
 <span data-ttu-id="8c8ed-126">BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-126">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="8c8ed-127">BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-127">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span> <span data-ttu-id="8c8ed-128">我們可以指定專案的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-128">We can specify an application name for a project.</span></span>  <span data-ttu-id="8c8ed-129">此部署程序會自動建立具有指定名稱的新應用程式 (如果它不存在的話)。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-129">The deployment process will automatically create a new application having the specified name if it doesn’t exist.</span></span>  
  
#### <a name="to-configure-and-deploy-the-projects"></a><span data-ttu-id="8c8ed-130">若要設定和部署專案</span><span class="sxs-lookup"><span data-stu-id="8c8ed-130">To configure and deploy the projects</span></span>  
  
1.  <span data-ttu-id="8c8ed-131">在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-131">In Solution Explorer, right-click the **EAISchemas** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8c8ed-132">按一下**簽署**索引標籤上，選取**簽署組件**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-132">Click the **Signing** tab, select **Sign the assembly**.</span></span>  
  
3.  <span data-ttu-id="8c8ed-133">從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<瀏覽 >**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-133">From the drop-down list in the **Choose a strong name key file** box, select **\<Browse…>**.</span></span>  
  
4.  <span data-ttu-id="8c8ed-134">在**選取檔案**對話方塊方塊中，瀏覽至**C:\BTStutorials**，按一下  **btsTutorials.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-134">In the **Select File** dialog box, navigate to **C:\BTStutorials**, click **btsTutorials.snk**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="8c8ed-135">按一下**部署** 索引標籤右邊的方塊**應用程式名稱**，型別`EAISolution`。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-135">Click the **Deployment** tab, in the box to the right of **Application Name**, type `EAISolution`.</span></span>  
  
6.  <span data-ttu-id="8c8ed-136">從下拉式清單中的清單右邊的方塊**重新部署**，選取**True**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-136">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  
  
7.  <span data-ttu-id="8c8ed-137">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-137">In Solution Explorer, right-click **EAISchemas**, and then click **Deploy**.</span></span>  <span data-ttu-id="8c8ed-138">此時，[輸出] 視窗應該會顯示：</span><span class="sxs-lookup"><span data-stu-id="8c8ed-138">The Output window should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  <span data-ttu-id="8c8ed-139">重複步驟 1 到 7 來部署 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-139">Repeat step 1 through 7 to deploy the EAIOrchestration project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8c8ed-140">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="8c8ed-140">What did I just do?</span></span>  
 <span data-ttu-id="8c8ed-141">在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-141">In this step, you deployed the EAISchemas and EAIOrchestration projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8c8ed-142">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8c8ed-142">Next Steps</span></span>  
 <span data-ttu-id="8c8ed-143">您會建立實體連接埠，並將它們繫結至協調流程的邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="8c8ed-143">You create the physical ports, and bind them to the logical ports of the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8ed-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c8ed-144">See Also</span></span>  
 <span data-ttu-id="8c8ed-145">[步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md) </span><span class="sxs-lookup"><span data-stu-id="8c8ed-145">[Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md) </span></span>  
 [<span data-ttu-id="8c8ed-146">步驟 3： 測試方案</span><span class="sxs-lookup"><span data-stu-id="8c8ed-146">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)