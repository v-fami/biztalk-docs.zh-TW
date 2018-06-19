---
title: 步驟 1： 將 EAIOrchestration 專案加入方案 |Microsoft 文件
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
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276862"
---
# <a name="step-1-add-eaiorchestration-project-to-the-solution"></a><span data-ttu-id="17b7d-102">步驟 1：將 EAIOrchestration 專案加入解決方案中</span><span class="sxs-lookup"><span data-stu-id="17b7d-102">Step 1: Add EAIOrchestration Project to the Solution</span></span>
<span data-ttu-id="17b7d-103">![步驟 4 之 1](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="17b7d-103">![Step 1 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="17b7d-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="17b7d-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="17b7d-105">**目標：** 在此步驟中，您必須加入第二個專案到 EAI 方案。</span><span class="sxs-lookup"><span data-stu-id="17b7d-105">**Objective:** In this step, you add a second project to the EAI solution.</span></span> <span data-ttu-id="17b7d-106">然後新增協調流程至新專案。</span><span class="sxs-lookup"><span data-stu-id="17b7d-106">Then you add an orchestration to the new project.</span></span>  
  
 <span data-ttu-id="17b7d-107">**用途：** 建立協調流程的個別專案。</span><span class="sxs-lookup"><span data-stu-id="17b7d-107">**Purpose:** You create a separate project for the orchestration.</span></span> <span data-ttu-id="17b7d-108">當有幾個不同的人在處理方案時，這是有所助益的。</span><span class="sxs-lookup"><span data-stu-id="17b7d-108">This is helpful when you have several different people working on one solution.</span></span> <span data-ttu-id="17b7d-109">您使用新協調流程自動化本課程的商務程序。</span><span class="sxs-lookup"><span data-stu-id="17b7d-109">You use the new orchestration to automate the business process in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="17b7d-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="17b7d-110">Prerequisites</span></span>  
 <span data-ttu-id="17b7d-111">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="17b7d-111">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="17b7d-112">在開始此步驟之前必須先完成[第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="17b7d-112">Before you begin this step you must complete [Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="17b7d-113">程序</span><span class="sxs-lookup"><span data-stu-id="17b7d-113">Procedures</span></span>  
 <span data-ttu-id="17b7d-114">如果您關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]視窗中，請遵循 「 若要開啟 Visual Studio 專案 」 程序中[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)加以開啟。</span><span class="sxs-lookup"><span data-stu-id="17b7d-114">If you have closed the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window, follow the procedure “To open the Visual Studio project” in [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) to open it.</span></span>  
  
#### <a name="to-add-another-project-to-your-solution"></a><span data-ttu-id="17b7d-115">新增另一個專案到您的方案</span><span class="sxs-lookup"><span data-stu-id="17b7d-115">To add another project to your solution</span></span>  
  
1.  <span data-ttu-id="17b7d-116">Visual Studio 中，從上**檔案**功能表上，指向**新增**，然後按一下 **新專案**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-116">From Visual Studio, on the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="17b7d-117">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="17b7d-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="17b7d-118">使用</span><span class="sxs-lookup"><span data-stu-id="17b7d-118">Use this</span></span>|<span data-ttu-id="17b7d-119">動作</span><span class="sxs-lookup"><span data-stu-id="17b7d-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="17b7d-120">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="17b7d-120">**Installed Templates**</span></span>|<span data-ttu-id="17b7d-121">按一下**BizTalk 專案**，然後按一下 **空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-121">Click **BizTalk Projects**, and then click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="17b7d-122">**名稱**</span><span class="sxs-lookup"><span data-stu-id="17b7d-122">**Name**</span></span>|<span data-ttu-id="17b7d-123">輸入 `EAIOrchestration`。</span><span class="sxs-lookup"><span data-stu-id="17b7d-123">Type `EAIOrchestration`.</span></span>|  
    |<span data-ttu-id="17b7d-124">**位置**</span><span class="sxs-lookup"><span data-stu-id="17b7d-124">**Location**</span></span>|<span data-ttu-id="17b7d-125">輸入 `C:\BTSTutorials\EAISolution`。</span><span class="sxs-lookup"><span data-stu-id="17b7d-125">Type `C:\BTSTutorials\EAISolution`.</span></span>|  
  
3.  <span data-ttu-id="17b7d-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-126">Click **OK**.</span></span>  
  
#### <a name="to-add-an-orchestration"></a><span data-ttu-id="17b7d-127">若要新增協調流程</span><span class="sxs-lookup"><span data-stu-id="17b7d-127">To add an orchestration</span></span>  
  
1.  <span data-ttu-id="17b7d-128">在 方案總管 中，以滑鼠右鍵按一下**EAIOrchestration**，指向 **新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-128">In Solution Explorer, right-click **EAIOrchestration**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="17b7d-129">在**加入新項目-EAIOrchestration**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="17b7d-129">In the **Add New Item - EAIOrchestration** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="17b7d-130">使用</span><span class="sxs-lookup"><span data-stu-id="17b7d-130">Use this</span></span>|<span data-ttu-id="17b7d-131">動作</span><span class="sxs-lookup"><span data-stu-id="17b7d-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="17b7d-132">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="17b7d-132">**Installed Templates**</span></span>|<span data-ttu-id="17b7d-133">按一下**協調流程檔案**，然後按一下  **BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-133">Click **Orchestration Files**, and then click **BizTalk Orchestration**.</span></span>|  
    |<span data-ttu-id="17b7d-134">**名稱**</span><span class="sxs-lookup"><span data-stu-id="17b7d-134">**Name**</span></span>|<span data-ttu-id="17b7d-135">型別**EAIProcess.odx**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-135">Type **EAIProcess.odx**.</span></span>|  
  
3.  <span data-ttu-id="17b7d-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="17b7d-136">Click **Add**.</span></span>  
  
     <span data-ttu-id="17b7d-137">就會開啟「協調流程設計師」。</span><span class="sxs-lookup"><span data-stu-id="17b7d-137">Orchestration Designer opens.</span></span> <span data-ttu-id="17b7d-138">下圖顯示含有 EAIProcess 協調流程的「協調流程設計師」。</span><span class="sxs-lookup"><span data-stu-id="17b7d-138">The following figure shows Orchestration Designer with the EAIProcess orchestration.</span></span>  
  
     <span data-ttu-id="17b7d-139">![新的協調流程](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="17b7d-139">![New orchestration](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="17b7d-140">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="17b7d-140">What did I just do?</span></span>  
 <span data-ttu-id="17b7d-141">在此步驟中，您已將第二個專案新增至 EAI 方案中。</span><span class="sxs-lookup"><span data-stu-id="17b7d-141">In this step, you added a second project to the EAI solution.</span></span> <span data-ttu-id="17b7d-142">然後在新專案中新增了協調流程。</span><span class="sxs-lookup"><span data-stu-id="17b7d-142">Then you added an orchestration to the new project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="17b7d-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="17b7d-143">Next Steps</span></span>  
 <span data-ttu-id="17b7d-144">定義商務程序中的[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="17b7d-144">You define the business process in [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b7d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17b7d-145">See Also</span></span>  
 <span data-ttu-id="17b7d-146">[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="17b7d-146">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 <span data-ttu-id="17b7d-147">[步驟 3： 新增至協調流程連接埠](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="17b7d-147">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="17b7d-148">步驟 4： 建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="17b7d-148">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)