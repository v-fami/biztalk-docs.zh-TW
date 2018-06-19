---
title: 步驟 4： 建置 EAIOrchestration 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66e4b161-c5ac-404c-9ee5-4c0322fc40f3
caps.latest.revision: 34
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 992d903fc64740cb9ec4bda762ee5ac032e51a77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276670"
---
# <a name="step-4-build-the-eaiorchestration-project"></a><span data-ttu-id="fbc5e-102">步驟 4：建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="fbc5e-102">Step 4: Build the EAIOrchestration Project</span></span>
<span data-ttu-id="fbc5e-103">![步驟 4 之 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="fbc5e-103">![Step 4 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="fbc5e-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="fbc5e-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="fbc5e-105">**目標：** 在此步驟中，您將 EAIOrchestration 專案編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="fbc5e-105">**Objective:** In this step, you compile the EAIOrchestration project into an assembly.</span></span>  
  
 <span data-ttu-id="fbc5e-106">**用途：** BizTalk Server 需要的所有成品編譯到.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="fbc5e-106">**Purpose:** BizTalk Server requires all the artifacts to be compiled into .NET assemblies.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fbc5e-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="fbc5e-107">Prerequisites</span></span>  
 <span data-ttu-id="fbc5e-108">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="fbc5e-108">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="fbc5e-109">在開始此步驟之前，您必須先完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fbc5e-109">Before you begin this step you must complete the following steps:</span></span>  
  
    -   [<span data-ttu-id="fbc5e-110">步驟 1： 將 EAIOrchestration 專案加入方案</span><span class="sxs-lookup"><span data-stu-id="fbc5e-110">Step 1: Add EAIOrchestration Project to the Solution</span></span>](../core/step-1-add-eaiorchestration-project-to-the-solution.md)  
  
    -   [<span data-ttu-id="fbc5e-111">步驟 2： 定義商務程序</span><span class="sxs-lookup"><span data-stu-id="fbc5e-111">Step 2: Define the Business Process</span></span>](../core/step-2-define-the-business-process.md)  
  
    -   [<span data-ttu-id="fbc5e-112">步驟 3： 新增至協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="fbc5e-112">Step 3: Add Ports to the Orchestration</span></span>](../core/step-3-add-ports-to-the-orchestration.md)  
  
## <a name="procedures"></a><span data-ttu-id="fbc5e-113">程序</span><span class="sxs-lookup"><span data-stu-id="fbc5e-113">Procedures</span></span>  
  
#### <a name="to-build-the-eaiorchestration-project"></a><span data-ttu-id="fbc5e-114">若要建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="fbc5e-114">To build the EAIOrchestration project</span></span>  
  
-   <span data-ttu-id="fbc5e-115">在 方案總管 中，以滑鼠右鍵按一下**EAIOrchestration**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="fbc5e-115">In Solution Explorer, right-click **EAIOrchestration**, and then click **Build**.</span></span>  
  
     <span data-ttu-id="fbc5e-116">畫面底部應會顯示：</span><span class="sxs-lookup"><span data-stu-id="fbc5e-116">The bottom of the screen should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="fbc5e-117">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="fbc5e-117">What did I just do?</span></span>  
 <span data-ttu-id="fbc5e-118">在此步驟中，您編譯 EAIOrchestration 專案。</span><span class="sxs-lookup"><span data-stu-id="fbc5e-118">In this step, you compiled the EAIOrchestration project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fbc5e-119">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="fbc5e-119">Next steps</span></span>  
 <span data-ttu-id="fbc5e-120">您會部署 EAISolution 方案中的[第 3 課： 部署方案](../core/lesson-3-deploy-the-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc5e-120">You deploy the EAISolution solution in [Lesson 3: Deploy the Solution](../core/lesson-3-deploy-the-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc5e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc5e-121">See Also</span></span>  
 <span data-ttu-id="fbc5e-122">[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="fbc5e-122">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="fbc5e-123">[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="fbc5e-123">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="fbc5e-124">步驟 3： 新增至協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="fbc5e-124">Step 3: Add Ports to the Orchestration</span></span>](../core/step-3-add-ports-to-the-orchestration.md)