---
title: 步驟 3： 測試 Solution2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30dbc7c9-3c5f-4953-b26f-5c41141c22ad
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c0e484a9f6af788775ec4ae7309965327378267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277270"
---
# <a name="step-3-test-the-solution"></a><span data-ttu-id="8fa14-102">步驟 3： 測試方案</span><span class="sxs-lookup"><span data-stu-id="8fa14-102">Step 3: Test the Solution</span></span>
<span data-ttu-id="8fa14-103">![步驟 3 之 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="8fa14-103">![Step 3 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="8fa14-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="8fa14-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="8fa14-105">**目標：** 在此步驟中，您會測試 EAI 方案處理訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="8fa14-105">**Objective:** In this step, you test how the EAI solution processes messages.</span></span>  
  
 <span data-ttu-id="8fa14-106">**用途：** 在此步驟中，您會檢查 EAIProcess 協調流程是否正確處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8fa14-106">**Purpose:** In this step, you check that the EAIProcess orchestration processes messages correctly.</span></span> <span data-ttu-id="8fa14-107">您必須將範例訊息放入 EAI 應用程式所指定的接收位置。</span><span class="sxs-lookup"><span data-stu-id="8fa14-107">You do this by dropping sample messages into the receive location specified for the EAI application.</span></span> <span data-ttu-id="8fa14-108">若 EAI 方案正確地運作，且 EAIProcess 協調流程接收到倉儲的訊息要求超過 500 個項目，協調流程會產生拒絕的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8fa14-108">If the EAI solution is working properly, if the EAIProcess orchestration receives a message from the warehouse requesting more than 500 items, the orchestration generates a decline request message.</span></span> <span data-ttu-id="8fa14-109">若 EAIProcess 協調流程接收到倉儲的訊息要求少於 500 個項目，協調流程會將訊息傳遞到 ERP 系統。</span><span class="sxs-lookup"><span data-stu-id="8fa14-109">If the EAIProcess orchestration receives a message from the warehouse requesting fewer than 500 items, the orchestration passes the message on to the ERP system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8fa14-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="8fa14-110">Prerequisites</span></span>  
 <span data-ttu-id="8fa14-111">在開始此步驟之前必須先完成[步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md)。</span><span class="sxs-lookup"><span data-stu-id="8fa14-111">Before you begin this step you must complete [Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8fa14-112">程序</span><span class="sxs-lookup"><span data-stu-id="8fa14-112">Procedures</span></span>  
  
#### <a name="to-test-the-eai-solution"></a><span data-ttu-id="8fa14-113">測試 EAI 方案</span><span class="sxs-lookup"><span data-stu-id="8fa14-113">To test the EAI solution</span></span>  
  
1.  <span data-ttu-id="8fa14-114">開啟 Windows 檔案總管並瀏覽至**C:\BTSTutorials\WareHouse**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-114">Open Windows Explorer, and navigate to **C:\BTSTutorials\WareHouse**.</span></span>  <span data-ttu-id="8fa14-115">這個資料夾會建立安裝教學課程檔案。</span><span class="sxs-lookup"><span data-stu-id="8fa14-115">This folder is created by installing the tutorial files.</span></span>  
  
2.  <span data-ttu-id="8fa14-116">複製**RequestInstance.XML**並將它貼入**C:\BTSTutorials\WareHouse\Request**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-116">Copy **RequestInstance.XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.</span></span>  
  
3.  <span data-ttu-id="8fa14-117">當檔案消失時，會檢查**C:\BTSTutorials\ERP\Request**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-117">When the file disappears, check **C:\BTSTutorials\ERP\Request**.</span></span>  
  
4.  <span data-ttu-id="8fa14-118">在 Windows 檔案總管，瀏覽至**C:\BTSTutorials\WareHouse**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-118">In Windows Explorer, navigate to **C:\BTSTutorials\WareHouse**.</span></span>  
  
5.  <span data-ttu-id="8fa14-119">複製**RequestInstance （透過限制）。XML**並將它貼入**C:\BTSTutorials\WareHouse\Request**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-119">Copy **RequestInstance(Over Limit).XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.</span></span>  
  
6.  <span data-ttu-id="8fa14-120">當檔案消失時，會檢查**C:\BTSTutorials\WareHouse\RequestDecline**。</span><span class="sxs-lookup"><span data-stu-id="8fa14-120">When the file disappears, check **C:\BTSTutorials\WareHouse\RequestDecline**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8fa14-121">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="8fa14-121">What did I just do?</span></span>  
 <span data-ttu-id="8fa14-122">您在 EAI 應用程式的接收位置中放置範例訊息以測試 EAI 方案。</span><span class="sxs-lookup"><span data-stu-id="8fa14-122">You tested the EAI solution by placing sample messages in the receive location for the EAI application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa14-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fa14-123">See Also</span></span>  
 <span data-ttu-id="8fa14-124">[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md) </span><span class="sxs-lookup"><span data-stu-id="8fa14-124">[Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md) </span></span>  
 [<span data-ttu-id="8fa14-125">步驟 2： 設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="8fa14-125">Step 2: Configure and Start the Application</span></span>](../core/step-2-configure-and-start-the-application1.md)