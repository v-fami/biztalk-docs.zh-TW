---
title: "步驟 5： 建置 EAISchemas 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c20cd368-7446-4861-8d71-5bc25ce408a2
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394d9df78f7064df8501ed43149bd26793533c47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-build-the-eaischemas-project"></a><span data-ttu-id="6ca49-102">步驟 5：建置 EAISchema 專案</span><span class="sxs-lookup"><span data-stu-id="6ca49-102">Step 5: Build the EAISchemas Project</span></span>
<span data-ttu-id="6ca49-103">![步驟 5 之 5](../core/media/step-5of5.gif "Step_5of5")</span><span class="sxs-lookup"><span data-stu-id="6ca49-103">![Step 5 of 5](../core/media/step-5of5.gif "Step_5of5")</span></span>  
  
 <span data-ttu-id="6ca49-104">**若要完成的時間：** 6 分鐘</span><span class="sxs-lookup"><span data-stu-id="6ca49-104">**Time to complete:** 6 minutes</span></span>  
  
 <span data-ttu-id="6ca49-105">**目標：**在此步驟中，您會編譯 EAISchemas 專案。</span><span class="sxs-lookup"><span data-stu-id="6ca49-105">**Objective:** In this step, you compile the EAISchemas project.</span></span>  
  
 <span data-ttu-id="6ca49-106">**用途：** Microsoft BizTalk Server 與.NET Framework 的最重要的部分是所有 BizTalk Server 成品、 對應、 結構描述、 協調流程和管線都會編譯為.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="6ca49-106">**Purpose:** The most important aspect of Microsoft BizTalk Server and the .NET Framework is that all BizTalk Server artifacts; maps, schemas, orchestrations, and pipelines, get compiled into .NET assemblies.</span></span> <span data-ttu-id="6ca49-107">此設計的兩個最重要含意是這些組件必須具有強式名稱，因此它們也遵循 .NET 版本管理規則。</span><span class="sxs-lookup"><span data-stu-id="6ca49-107">The two most important implications of this design are that these assemblies must have strong names, and because of that, they also follow .NET versioning rules.</span></span> <span data-ttu-id="6ca49-108">其主要含意為，一旦針對另一個 .NET 專案或組件 (包括 BizTalk 專案) 的特定版本建置 BizTalk 專案，該專案會繼續使用此版本，直到再針對較新的版本重新建置它為止。</span><span class="sxs-lookup"><span data-stu-id="6ca49-108">The main implication of this is that a BizTalk project, once built against a particular version of another .NET project or assembly (including BizTalk projects), continues to use that version until it has been rebuilt against a newer version.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ca49-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="6ca49-109">Prerequisites</span></span>  
 <span data-ttu-id="6ca49-110">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="6ca49-110">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="6ca49-111">在開始此步驟之前，您必須先完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6ca49-111">Before you begin this step you must complete the following steps:</span></span>  
  
    -   [<span data-ttu-id="6ca49-112">步驟 1： 建立 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="6ca49-112">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
  
    -   [<span data-ttu-id="6ca49-113">步驟 2： 建立庫存要求結構描述</span><span class="sxs-lookup"><span data-stu-id="6ca49-113">Step 2: Create the Inventory Request Schema</span></span>](../core/step-2-create-the-inventory-request-schema.md) 
  
    -   [<span data-ttu-id="6ca49-114">步驟 3： 建立拒絕要求結構描述</span><span class="sxs-lookup"><span data-stu-id="6ca49-114">Step 3: Create the Request Decline Schema</span></span>](../core/step-3-create-the-request-decline-schema.md)  
  
    -   [<span data-ttu-id="6ca49-115">步驟 4： 建立地圖</span><span class="sxs-lookup"><span data-stu-id="6ca49-115">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)  
  
## <a name="procedures"></a><span data-ttu-id="6ca49-116">程序</span><span class="sxs-lookup"><span data-stu-id="6ca49-116">Procedures</span></span>  
  
#### <a name="to-build-the-eaischemas-project"></a><span data-ttu-id="6ca49-117">若要建置 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="6ca49-117">To build the EAISchemas project</span></span>  
  
1.  <span data-ttu-id="6ca49-118">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6ca49-118">In Solution Explorer, right-click **EAISchemas**, and then click **Build**.</span></span>  
  
     <span data-ttu-id="6ca49-119">畫面底部應會顯示：</span><span class="sxs-lookup"><span data-stu-id="6ca49-119">The bottom of the screen should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="6ca49-120">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="6ca49-120">What did I just do?</span></span>  
 <span data-ttu-id="6ca49-121">在此步驟中，您已經建置 EAISchemas 專案來產生組件檔案 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="6ca49-121">In this step, you built the EAISchemas project to generate an assembly file (DLL).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6ca49-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6ca49-122">Next Steps</span></span>  
 <span data-ttu-id="6ca49-123">建立評估庫存補充要求訊息，依據核准準則中的內容的商務程序[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca49-123">You create the business process that evaluates the contents of the inventory replenishment request message against approval criteria in [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca49-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca49-124">See Also</span></span>  
 <span data-ttu-id="6ca49-125">[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="6ca49-125">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="6ca49-126">[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="6ca49-126">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="6ca49-127">[步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="6ca49-127">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 [<span data-ttu-id="6ca49-128">步驟 4： 建立地圖</span><span class="sxs-lookup"><span data-stu-id="6ca49-128">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)