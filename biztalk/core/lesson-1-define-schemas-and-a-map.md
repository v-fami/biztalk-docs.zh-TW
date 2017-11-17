---
title: "第 1 課： 定義結構描述和對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: enterprise application integration tutorial, creating solutions
ms.assetid: 4fe7720d-722e-4fa0-a556-477fc66ffa12
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce6411a7a4ffa80b72bad2d84766bf773bbfb42f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-define-schemas-and-a-map"></a><span data-ttu-id="302d9-102">課程 1：定義結構描述及對應</span><span class="sxs-lookup"><span data-stu-id="302d9-102">Lesson 1: Define Schemas and a Map</span></span>
<span data-ttu-id="302d9-103">在此課程中，您要在企業應用程式整合 (EAI) 方案中建立並建置第一個專案。</span><span class="sxs-lookup"><span data-stu-id="302d9-103">In this lesson, you create and build the first project in the enterprise application integration (EAI) solution.</span></span> <span data-ttu-id="302d9-104">專案包含兩個訊息結構描述和一個對應。</span><span class="sxs-lookup"><span data-stu-id="302d9-104">The project contains two message schemas, and a map.</span></span>  
  
 <span data-ttu-id="302d9-105">在 EAI 方案中，倉儲系統會傳送庫存補充的要求訊息給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理。</span><span class="sxs-lookup"><span data-stu-id="302d9-105">In the EAI solution, a warehouse system sends a request message for inventory replenishment to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing.</span></span> <span data-ttu-id="302d9-106">在此課程中，您要建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="302d9-106">In this lesson, you create the following items:</span></span>  
  
-   <span data-ttu-id="302d9-107">存放專案的 EAI 方案。</span><span class="sxs-lookup"><span data-stu-id="302d9-107">The EAI solution, to hold the project.</span></span>  
  
-   <span data-ttu-id="302d9-108">存放結構描述和對應的專案。</span><span class="sxs-lookup"><span data-stu-id="302d9-108">The project, to hold the schemas and the map.</span></span>  
  
-   <span data-ttu-id="302d9-109">倉儲傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 要求庫存補充之訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="302d9-109">The schema, for the message the warehouse sends to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to request inventory replenishment.</span></span>  
  
-   <span data-ttu-id="302d9-110">訊息的結構描述，就會拒絕要求時，所預期倉儲。</span><span class="sxs-lookup"><span data-stu-id="302d9-110">The schema, for the message that the warehouse is expecting when a request is rejected.</span></span>  
  
-   <span data-ttu-id="302d9-111">重新格式化要求訊息以建立要求拒絕訊息對應。</span><span class="sxs-lookup"><span data-stu-id="302d9-111">A map, for reformatting a request message to create a request decline message.</span></span>  
  
 <span data-ttu-id="302d9-112">最後您開始之前，會在建置專案時[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="302d9-112">Finally you build the project before starting [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md).</span></span> <span data-ttu-id="302d9-113">在第 2 課，您可以建立商務程序，將訊息路由，並評估庫存補充要求訊息，依據核准準則的內容。</span><span class="sxs-lookup"><span data-stu-id="302d9-113">In Lesson 2, you create the business process that routes the messages and evaluates the contents of the inventory replenishment request message against approval criteria.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="302d9-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="302d9-114">In This Section</span></span>  
  
-   [<span data-ttu-id="302d9-115">步驟 1： 建立 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="302d9-115">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
  
-   [<span data-ttu-id="302d9-116">步驟 2： 建立庫存要求結構描述</span><span class="sxs-lookup"><span data-stu-id="302d9-116">Step 2: Create the Inventory Request Schema</span></span>](../core/step-2-create-the-inventory-request-schema.md)  
  
-   [<span data-ttu-id="302d9-117">步驟 3： 建立拒絕要求結構描述</span><span class="sxs-lookup"><span data-stu-id="302d9-117">Step 3: Create the Request Decline Schema</span></span>](../core/step-3-create-the-request-decline-schema.md)  
  
-   [<span data-ttu-id="302d9-118">步驟 4： 建立地圖</span><span class="sxs-lookup"><span data-stu-id="302d9-118">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)  
  
-   [<span data-ttu-id="302d9-119">步驟 5： 建置 Eaischema 專案</span><span class="sxs-lookup"><span data-stu-id="302d9-119">Step 5: Build the EAISchemas Project</span></span>](../core/step-5-build-the-eaischemas-project.md)  
  
## <a name="see-also"></a><span data-ttu-id="302d9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="302d9-120">See Also</span></span>  
 <span data-ttu-id="302d9-121">[開始本教學課程之前](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="302d9-121">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="302d9-122">[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="302d9-122">[Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="302d9-123">第 3 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="302d9-123">Lesson 3: Deploy the Solution</span></span>](../core/lesson-3-deploy-the-solution.md)