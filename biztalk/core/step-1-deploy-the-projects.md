---
title: 步驟 1： 部署專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: 44
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b25af8ee1095a5365fabd955f7185acbc79254db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007551"
---
# <a name="step-1-deploy-the-projects"></a><span data-ttu-id="da831-102">步驟 1：部署專案</span><span class="sxs-lookup"><span data-stu-id="da831-102">Step 1: Deploy the Projects</span></span>
<span data-ttu-id="da831-103">![步驟 3 之 1](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="da831-103">![Step 1 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="da831-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="da831-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="da831-105">**目標：** 在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="da831-105">**Objective:** In this step, you deploy the EAISchemas and EAIOrchestration projects.</span></span>  
  
 <span data-ttu-id="da831-106">**用途：** 當您部署專案或方案在 Visual Studio 中的時，組件會自動建置和部署到指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="da831-106">**Purpose:** When you deploy a project or solution in Visual Studio, the assemblies are automatically built and deployed into the specified application.</span></span> <span data-ttu-id="da831-107">做為此程序的一部分，組件連同協調流程、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="da831-107">As part of this process, the assembly along with the orchestrations, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="da831-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="da831-108">Prerequisites</span></span>  
  
- [<span data-ttu-id="da831-109">課程 1：定義結構描述及對應</span><span class="sxs-lookup"><span data-stu-id="da831-109">Lesson 1: Define Schemas and a Map</span></span>](../core/lesson-1-define-schemas-and-a-map.md)  
  
- [<span data-ttu-id="da831-110">課程 2：定義商務程序</span><span class="sxs-lookup"><span data-stu-id="da831-110">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)  
  
- <span data-ttu-id="da831-111">成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組</span><span class="sxs-lookup"><span data-stu-id="da831-111">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group</span></span>

- <span data-ttu-id="da831-112">以系統管理權限執行 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da831-112">Run Visual Studio with Administrative privileges</span></span>

> [!TIP]
> <span data-ttu-id="da831-113">您可以下載必要的教學課程檔案，在[教學課程 1： 企業應用程式整合](https://www.microsoft.com/download/details.aspx?id=22793)。</span><span class="sxs-lookup"><span data-stu-id="da831-113">You can download the required tutorial files at [Tutorial 1: Enterprise Application Integration](https://www.microsoft.com/download/details.aspx?id=22793).</span></span>

## <a name="open-the-solution-with-administrative-rights"></a><span data-ttu-id="da831-114">以系統管理權限開啟的方案</span><span class="sxs-lookup"><span data-stu-id="da831-114">Open the solution with administrative rights</span></span>  
  
1. <span data-ttu-id="da831-115">BizTalk Server 系統管理員群組的成員身分登入 Windows。</span><span class="sxs-lookup"><span data-stu-id="da831-115">Sign in to Windows as a member of the BizTalk Server Administrators group.</span></span>  
  
2. <span data-ttu-id="da831-116">開始**Microsoft Visual Studio**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="da831-116">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
3. <span data-ttu-id="da831-117">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="da831-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
4. <span data-ttu-id="da831-118">在 [**開啟專案**] 對話方塊中，瀏覽至**EAISolution.sln**專案方案檔，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="da831-118">In the **Open Project** dialog box, browse to the **EAISolution.sln** project solution file, and then click **Open**.</span></span>  
  
   <span data-ttu-id="da831-119">部署程序要求組件必須是以強式名稱簽署的。</span><span class="sxs-lookup"><span data-stu-id="da831-119">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="da831-120">您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。</span><span class="sxs-lookup"><span data-stu-id="da831-120">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  <span data-ttu-id="da831-121">此檔案包含在教學課程檔案。</span><span class="sxs-lookup"><span data-stu-id="da831-121">This file is included in the tutorial files.</span></span>  
  
   <span data-ttu-id="da831-122">BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。</span><span class="sxs-lookup"><span data-stu-id="da831-122">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="da831-123">BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="da831-123">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span> <span data-ttu-id="da831-124">我們可以指定專案的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="da831-124">We can specify an application name for a project.</span></span>  <span data-ttu-id="da831-125">部署程序會自動建立新的應用程式，如果不存在具有指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="da831-125">The deployment process automatically creates a new application having the specified name if it doesn’t exist.</span></span>  
  
## <a name="configure-and-deploy-the-projects"></a><span data-ttu-id="da831-126">設定和部署專案</span><span class="sxs-lookup"><span data-stu-id="da831-126">Configure and deploy the projects</span></span>  
  
1.  <span data-ttu-id="da831-127">在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="da831-127">In Solution Explorer, right-click the **EAISchemas** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="da831-128">按一下  **Signing**索引標籤上，選取**簽署組件**。</span><span class="sxs-lookup"><span data-stu-id="da831-128">Click the **Signing** tab, select **Sign the assembly**.</span></span>  
  
3.  <span data-ttu-id="da831-129">從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<瀏覽...\>**.</span><span class="sxs-lookup"><span data-stu-id="da831-129">From the drop-down list in the **Choose a strong name key file** box, select **\<Browse…\>**.</span></span>  
  
4.  <span data-ttu-id="da831-130">在 **選取檔案**對話方塊方塊中，瀏覽至**C:\BTStutorials**，按一下**btsTutorials.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="da831-130">In the **Select File** dialog box, navigate to **C:\BTStutorials**, click **btsTutorials.snk**, and then click **Open**.</span></span> 
  
5.  <span data-ttu-id="da831-131">按一下 **部署**索引標籤上，在右邊的方塊**應用程式名稱**，型別`EAISolution`。</span><span class="sxs-lookup"><span data-stu-id="da831-131">Click the **Deployment** tab, in the box to the right of **Application Name**, type `EAISolution`.</span></span>  
  
6.  <span data-ttu-id="da831-132">從下拉式清單方塊的清單中的右邊**重新部署**，選取 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="da831-132">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  
  
7.  <span data-ttu-id="da831-133">在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="da831-133">In Solution Explorer, right-click **EAISchemas**, and then click **Deploy**.</span></span>  <span data-ttu-id="da831-134">此時，[輸出] 視窗應該會顯示：</span><span class="sxs-lookup"><span data-stu-id="da831-134">The Output window should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  <span data-ttu-id="da831-135">重複步驟 1 到 7 來部署 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="da831-135">Repeat steps 1 through 7 to deploy the EAIOrchestration project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="da831-136">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="da831-136">What did I just do?</span></span>  
 <span data-ttu-id="da831-137">在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="da831-137">In this step, you deployed the EAISchemas and EAIOrchestration projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="da831-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="da831-138">Next Steps</span></span>  
 <span data-ttu-id="da831-139">您會建立實體連接埠，並將它們繫結至協調流程的邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="da831-139">You create the physical ports, and bind them to the logical ports of the orchestration.</span></span>  
  
 <span data-ttu-id="da831-140">[步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md) </span><span class="sxs-lookup"><span data-stu-id="da831-140">[Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md) </span></span>  
 [<span data-ttu-id="da831-141">步驟 3：測試解決方案</span><span class="sxs-lookup"><span data-stu-id="da831-141">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)
