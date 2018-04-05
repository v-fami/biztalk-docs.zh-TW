---
title: 第 2 課： 定義商務程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial, defining business processes
ms.assetid: 644aa049-4dd7-4392-b97f-31b1f29e12bd
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a2a9512fe847fdf50957456ec3d3eeff087c33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-define-the-business-process"></a><span data-ttu-id="18554-102">課程 2：定義商務程序</span><span class="sxs-lookup"><span data-stu-id="18554-102">Lesson 2: Define the Business Process</span></span>
<span data-ttu-id="18554-103">在這一課，您要在「企業應用程式整合」(EAI) 方案中建立第二個專案。</span><span class="sxs-lookup"><span data-stu-id="18554-103">In this lesson, you create the second project in the Enterprise Application Integration(EAI) solution.</span></span> <span data-ttu-id="18554-104">此專案包含一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="18554-104">This project contains an orchestration.</span></span>  
  
 <span data-ttu-id="18554-105">在 EAI 實例中，倉儲應用程式會傳送庫存補充訊息要求給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]進行處理。</span><span class="sxs-lookup"><span data-stu-id="18554-105">In the EAI scenario, the warehouse application sends an inventory replenishment message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="18554-106">使用您建立來自動化商務程序的協調流程。</span><span class="sxs-lookup"><span data-stu-id="18554-106"> uses the orchestration you create to automate the business process.</span></span> <span data-ttu-id="18554-107">協調流程提供工作流程、動作和運算式在系統中移動訊息以及處理其內容。</span><span class="sxs-lookup"><span data-stu-id="18554-107">The orchestration provides the workflow, actions, and expressions to move messages through the system and process their contents.</span></span>  
  
 <span data-ttu-id="18554-108">最後您開始之前，會在建置專案時[第 3 課： 部署方案](../core/lesson-3-deploy-the-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="18554-108">Finally you build the project before starting [Lesson 3: Deploy the Solution](../core/lesson-3-deploy-the-solution.md).</span></span>  
  
 <span data-ttu-id="18554-109">如需詳細資訊，請參閱[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="18554-109">For more information, see [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18554-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="18554-110">In This Section</span></span>  
  
-   [<span data-ttu-id="18554-111">步驟 1： 將 EAIOrchestration 專案加入方案</span><span class="sxs-lookup"><span data-stu-id="18554-111">Step 1: Add EAIOrchestration Project to the Solution</span></span>](../core/step-1-add-eaiorchestration-project-to-the-solution.md)  
  
-   [<span data-ttu-id="18554-112">步驟 2： 定義商務程序</span><span class="sxs-lookup"><span data-stu-id="18554-112">Step 2: Define the Business Process</span></span>](../core/step-2-define-the-business-process.md)  
  
-   [<span data-ttu-id="18554-113">步驟 3： 新增至協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="18554-113">Step 3: Add Ports to the Orchestration</span></span>](../core/step-3-add-ports-to-the-orchestration.md)  
  
-   [<span data-ttu-id="18554-114">步驟 4： 建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="18554-114">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)  
  
## <a name="see-also"></a><span data-ttu-id="18554-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18554-115">See Also</span></span>  
 <span data-ttu-id="18554-116">[開始本教學課程之前](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="18554-116">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="18554-117">[第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="18554-117">[Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md) </span></span>  
 [<span data-ttu-id="18554-118">第 3 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="18554-118">Lesson 3: Deploy the Solution</span></span>](../core/lesson-3-deploy-the-solution.md)