---
title: 步驟 1： 將 EAIOrchestration 專案加入方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9aa0d9-2075-4c7e-8baf-1ecd2721859a
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3b8e2b9c197e01ed695311c67bc79cf5056c4d1
ms.sourcegitcommit: 9b93ee2a019bef8d482626cf5525a6b95509b135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2018
ms.locfileid: "22276862"
---
# <a name="step-1-add-eaiorchestration-project-to-the-solution"></a><span data-ttu-id="c2861-102">步驟 1：將 EAIOrchestration 專案加入解決方案中</span><span class="sxs-lookup"><span data-stu-id="c2861-102">Step 1: Add EAIOrchestration Project to the Solution</span></span>
<span data-ttu-id="c2861-103">![步驟 4 之 1](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="c2861-103">![Step 1 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="c2861-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="c2861-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="c2861-105">**目標：** 在此步驟中，您必須新增第二個專案到 EAI 方案。</span><span class="sxs-lookup"><span data-stu-id="c2861-105">**Objective:** In this step, you add a second project to the EAI solution.</span></span> <span data-ttu-id="c2861-106">然後新增協調流程至新專案。</span><span class="sxs-lookup"><span data-stu-id="c2861-106">Then you add an orchestration to the new project.</span></span>  
  
 <span data-ttu-id="c2861-107">**用途：** 建立個別的協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="c2861-107">**Purpose:** You create a separate project for the orchestration.</span></span> <span data-ttu-id="c2861-108">當有幾個不同的人在處理方案時，這是有所助益的。</span><span class="sxs-lookup"><span data-stu-id="c2861-108">This is helpful when you have several different people working on one solution.</span></span> <span data-ttu-id="c2861-109">您使用新協調流程自動化本課程的商務程序。</span><span class="sxs-lookup"><span data-stu-id="c2861-109">You use the new orchestration to automate the business process in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c2861-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="c2861-110">Prerequisites</span></span>  
 <span data-ttu-id="c2861-111">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="c2861-111">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="c2861-112">在開始此步驟之前必須先完成[第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-112">Before you begin this step you must complete [Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c2861-113">程序</span><span class="sxs-lookup"><span data-stu-id="c2861-113">Procedures</span></span>  
 <span data-ttu-id="c2861-114">如果您已關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]視窗中，遵循 「 若要開啟 Visual Studio 專案 」 的程序[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)加以開啟。</span><span class="sxs-lookup"><span data-stu-id="c2861-114">If you have closed the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window, follow the procedure “To open the Visual Studio project” in [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) to open it.</span></span>  
  
#### <a name="to-add-another-project-to-your-solution"></a><span data-ttu-id="c2861-115">新增另一個專案到您的方案</span><span class="sxs-lookup"><span data-stu-id="c2861-115">To add another project to your solution</span></span>  
  
1.  <span data-ttu-id="c2861-116">從 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下**新專案**。</span><span class="sxs-lookup"><span data-stu-id="c2861-116">From Visual Studio, on the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="c2861-117">在 **新的專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c2861-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c2861-118">使用</span><span class="sxs-lookup"><span data-stu-id="c2861-118">Use this</span></span>|<span data-ttu-id="c2861-119">動作</span><span class="sxs-lookup"><span data-stu-id="c2861-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c2861-120">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="c2861-120">**Installed Templates**</span></span>|<span data-ttu-id="c2861-121">按一下  **BizTalk 專案**，然後按一下**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="c2861-121">Click **BizTalk Projects**, and then click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="c2861-122">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c2861-122">**Name**</span></span>|<span data-ttu-id="c2861-123">輸入 `EAIOrchestration`。</span><span class="sxs-lookup"><span data-stu-id="c2861-123">Type `EAIOrchestration`.</span></span>|  
    |<span data-ttu-id="c2861-124">**位置**</span><span class="sxs-lookup"><span data-stu-id="c2861-124">**Location**</span></span>|<span data-ttu-id="c2861-125">輸入 `C:\BTSTutorials\EAISolution`。</span><span class="sxs-lookup"><span data-stu-id="c2861-125">Type `C:\BTSTutorials\EAISolution`.</span></span>|  
  
3.  <span data-ttu-id="c2861-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c2861-126">Click **OK**.</span></span>  
  
#### <a name="to-add-an-orchestration"></a><span data-ttu-id="c2861-127">若要新增協調流程</span><span class="sxs-lookup"><span data-stu-id="c2861-127">To add an orchestration</span></span>  
  
1.  <span data-ttu-id="c2861-128">在 [方案總管] 中，以滑鼠右鍵按一下**EAIOrchestration**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="c2861-128">In Solution Explorer, right-click **EAIOrchestration**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="c2861-129">在 **加入新項目-EAIOrchestration**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c2861-129">In the **Add New Item - EAIOrchestration** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c2861-130">使用</span><span class="sxs-lookup"><span data-stu-id="c2861-130">Use this</span></span>|<span data-ttu-id="c2861-131">動作</span><span class="sxs-lookup"><span data-stu-id="c2861-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c2861-132">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="c2861-132">**Installed Templates**</span></span>|<span data-ttu-id="c2861-133">按一下 **協調流程檔案**，然後按一下**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="c2861-133">Click **Orchestration Files**, and then click **BizTalk Orchestration**.</span></span>|  
    |<span data-ttu-id="c2861-134">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c2861-134">**Name**</span></span>|<span data-ttu-id="c2861-135">型別**EAIProcess.odx**。</span><span class="sxs-lookup"><span data-stu-id="c2861-135">Type **EAIProcess.odx**.</span></span>|  
  
3.  <span data-ttu-id="c2861-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="c2861-136">Click **Add**.</span></span>  
  
     <span data-ttu-id="c2861-137">就會開啟「協調流程設計師」。</span><span class="sxs-lookup"><span data-stu-id="c2861-137">Orchestration Designer opens.</span></span> <span data-ttu-id="c2861-138">下圖顯示含有 EAIProcess 協調流程的「協調流程設計師」。</span><span class="sxs-lookup"><span data-stu-id="c2861-138">The following figure shows Orchestration Designer with the EAIProcess orchestration.</span></span>  
  
     <span data-ttu-id="c2861-139">![新的協調流程](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="c2861-139">![New orchestration](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="c2861-140">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="c2861-140">What did I just do?</span></span>  
 <span data-ttu-id="c2861-141">在此步驟中，您已將第二個專案新增至 EAI 方案中。</span><span class="sxs-lookup"><span data-stu-id="c2861-141">In this step, you added a second project to the EAI solution.</span></span> <span data-ttu-id="c2861-142">然後在新專案中新增了協調流程。</span><span class="sxs-lookup"><span data-stu-id="c2861-142">Then you added an orchestration to the new project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c2861-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2861-143">Next Steps</span></span>  
 <span data-ttu-id="c2861-144">定義中的商務程序[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-144">You define the business process in [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2861-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2861-145">See Also</span></span>  
 <span data-ttu-id="c2861-146">[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="c2861-146">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 <span data-ttu-id="c2861-147">[步驟 3： 新增連接埠至協調流程](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="c2861-147">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="c2861-148">步驟 4：建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="c2861-148">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)