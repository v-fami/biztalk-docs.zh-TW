---
title: 步驟 1： 建立 EAISchemas 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a14ee61-fa27-4f03-997e-42c34a77afee
caps.latest.revision: 55
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb51c936edfcc20009048abcb90bb8ead72fd11c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974455"
---
# <a name="step-1-create-eaischemas-project"></a><span data-ttu-id="29e5d-102">步驟 1：建立 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="29e5d-102">Step 1: Create EAISchemas Project</span></span>
<span data-ttu-id="29e5d-103">![步驟 1，共 5](../core/media/step-1of5.gif "Step_1of5")</span><span class="sxs-lookup"><span data-stu-id="29e5d-103">![Step 1 of 5](../core/media/step-1of5.gif "Step_1of5")</span></span>  

 <span data-ttu-id="29e5d-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="29e5d-104">**Time to complete:** 5 minutes</span></span>  

 <span data-ttu-id="29e5d-105">**目標：** 在此步驟中，您建立新[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案和專案。</span><span class="sxs-lookup"><span data-stu-id="29e5d-105">**Objective:** In this step, you create a new [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution and a project.</span></span>  

 <span data-ttu-id="29e5d-106">**用途：** 您可以使用 BizTalk 專案系統以建立部分或所有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]應用程式或商務方案。</span><span class="sxs-lookup"><span data-stu-id="29e5d-106">**Purpose:** You use the BizTalk project system to create part or all of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] application or business solution.</span></span> <span data-ttu-id="29e5d-107">任何這類方案的核心項目為 BizTalk 專案—為部署之前建置和產生至組件的結構描述、協調流程、Web 訊息類型、類別、管線、對應和參考等項目的集合。</span><span class="sxs-lookup"><span data-stu-id="29e5d-107">The core element of any such solution is a BizTalk project—a collection of items, such as schemas, orchestrations, Web message types, classes, pipelines, maps, and references that you can build and generate into an assembly before deploying it.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="29e5d-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="29e5d-108">Prerequisites</span></span>  
 <span data-ttu-id="29e5d-109">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="29e5d-109">Note the following requirements before you begin this step:</span></span>  

-   <span data-ttu-id="29e5d-110">在開始此步驟之前，您就必須完成中的步驟[在您開始本教學課程之前](../core/before-you-begin-the-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="29e5d-110">Before you begin this step you must complete the steps in [Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md).</span></span>  

## <a name="procedures"></a><span data-ttu-id="29e5d-111">程序</span><span class="sxs-lookup"><span data-stu-id="29e5d-111">Procedures</span></span>  

#### <a name="to-create-a-new-visual-studio-solutionproject"></a><span data-ttu-id="29e5d-112">若要建立新的 Visual Studio 方案/專案</span><span class="sxs-lookup"><span data-stu-id="29e5d-112">To create a new Visual Studio solution/project</span></span>  

1. <span data-ttu-id="29e5d-113">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-113">Start **Microsoft Visual Studio**.</span></span>  

2. <span data-ttu-id="29e5d-114">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-114">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  

3. <span data-ttu-id="29e5d-115">在 **新的專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="29e5d-115">In the **New Project** dialog box, do the following:</span></span>  


   |             <span data-ttu-id="29e5d-116">使用</span><span class="sxs-lookup"><span data-stu-id="29e5d-116">Use this</span></span>              |                                <span data-ttu-id="29e5d-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="29e5d-117">To do this</span></span>                                |
   |-----------------------------------|--------------------------------------------------------------------------|
   |      <span data-ttu-id="29e5d-118">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="29e5d-118">**Installed Templates**</span></span>      | <span data-ttu-id="29e5d-119">按一下  **BizTalk 專案**，然後按一下**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-119">Click **BizTalk Projects**, then click **Empty BizTalk Server Project**.</span></span> |
   |             <span data-ttu-id="29e5d-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="29e5d-120">**Name**</span></span>              |                           <span data-ttu-id="29e5d-121">型別**EAISchemas**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-121">Type **EAISchemas**.</span></span>                           |
   |           <span data-ttu-id="29e5d-122">**位置**</span><span class="sxs-lookup"><span data-stu-id="29e5d-122">**Location**</span></span>            |                      <span data-ttu-id="29e5d-123">型別**C:\tutorial\Lessons**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-123">Type **C:\tutorial\Lessons**.</span></span>                       |
   |         <span data-ttu-id="29e5d-124">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="29e5d-124">**Solution Name**</span></span>         |                          <span data-ttu-id="29e5d-125">型別**EAISolution**。</span><span class="sxs-lookup"><span data-stu-id="29e5d-125">Type **EAISolution**.</span></span>                           |
   | <span data-ttu-id="29e5d-126">**為解決方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="29e5d-126">**Create directory for solution**</span></span> |                                <span data-ttu-id="29e5d-127">(已選取)</span><span class="sxs-lookup"><span data-stu-id="29e5d-127">(selected)</span></span>                                |


4. <span data-ttu-id="29e5d-128">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="29e5d-128">Click **OK**.</span></span>  

5. <span data-ttu-id="29e5d-129">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="29e5d-129">On the **File** menu, click **Save All**.</span></span>  

## <a name="what-did-i-just-do"></a><span data-ttu-id="29e5d-130">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="29e5d-130">What did I just do?</span></span>  
 <span data-ttu-id="29e5d-131">在此步驟中，您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中開啟了新專案和 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="29e5d-131">In this step, you opened a new project and a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  

## <a name="next-steps"></a><span data-ttu-id="29e5d-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="29e5d-132">Next Steps</span></span>  
 <span data-ttu-id="29e5d-133">您會建立庫存補充要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="29e5d-133">You create the schema for the inventory replenishment request message.</span></span>  

## <a name="see-also"></a><span data-ttu-id="29e5d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29e5d-134">See Also</span></span>  
 <span data-ttu-id="29e5d-135">[開始本教學課程之前](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-135">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="29e5d-136">[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-136">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="29e5d-137">[步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-137">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="29e5d-138">[步驟 4： 建立對應](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-138">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="29e5d-139">[步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-139">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 <span data-ttu-id="29e5d-140">[開發人員工具](../core/developer-tools.md) </span><span class="sxs-lookup"><span data-stu-id="29e5d-140">[Developer Tools](../core/developer-tools.md) </span></span>  
 [<span data-ttu-id="29e5d-141">使用 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="29e5d-141">Working with BizTalk Projects</span></span>](../core/working-with-biztalk-projects.md)