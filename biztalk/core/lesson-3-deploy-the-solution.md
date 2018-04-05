---
title: 第 3 課： 部署方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial, deploying solutions
ms.assetid: b2f50fe7-7636-45bf-a09b-776065dd8a33
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1f8c565a55bf59c49ccda9f1c521ebadc60aac5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-deploy-the-solution"></a><span data-ttu-id="24d58-102">課程 3：部署方案</span><span class="sxs-lookup"><span data-stu-id="24d58-102">Lesson 3: Deploy the Solution</span></span>
<span data-ttu-id="24d58-103">部署 EAISolution 的第一步是將組件加入至 BizTalk 管理資料庫和全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="24d58-103">The first step in deploying EAISolution is to add assemblies to the BizTalk Management database and the global assembly cache.</span></span>  
  
 <span data-ttu-id="24d58-104">第二步是設定及啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="24d58-104">The second step is to configure and start the application.</span></span>  
  
 <span data-ttu-id="24d58-105">在[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)，邏輯連接埠加入 EAIProcess 協調流程。</span><span class="sxs-lookup"><span data-stu-id="24d58-105">In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), you added logical ports to the EAIProcess orchestration.</span></span> <span data-ttu-id="24d58-106">在這一課，您會定義實體連接埠，並將實體連接埠繫結至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="24d58-106">In this lesson, you define the physical ports, and bind the physical ports to the logical ports.</span></span> <span data-ttu-id="24d58-107">您也必須將協調流程、接收埠和傳送埠指派給主控件。</span><span class="sxs-lookup"><span data-stu-id="24d58-107">You must also assign orchestration, receive port and send ports to hosts.</span></span>  <span data-ttu-id="24d58-108">主控件是 BizTalk 成品的虛擬容器。</span><span class="sxs-lookup"><span data-stu-id="24d58-108">A host is a virtual container for BizTalk artifacts.</span></span>  <span data-ttu-id="24d58-109">每一個主控件都有指派的主控件執行個體來處理成品。</span><span class="sxs-lookup"><span data-stu-id="24d58-109">Each host has designated host instances to process the artifacts.</span></span>  
  
 <span data-ttu-id="24d58-110">在這一課，您將學習使用 [BizTalk Server 管理主控台] 來管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 成品。</span><span class="sxs-lookup"><span data-stu-id="24d58-110">In this lesson, you learn about administering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts by using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="24d58-111">使用 BizTalk Server 管理主控台的相關資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="24d58-111">For information about using the BizTalk Server Administration Console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24d58-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="24d58-112">In This Section</span></span>  
  
-   [<span data-ttu-id="24d58-113">步驟 1： 部署專案</span><span class="sxs-lookup"><span data-stu-id="24d58-113">Step 1: Deploy the Projects</span></span>](../core/step-1-deploy-the-projects.md)  
  
-   [<span data-ttu-id="24d58-114">步驟 2： 設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="24d58-114">Step 2: Configure and Start the Application</span></span>](../core/step-2-configure-and-start-the-application1.md)  
  
-   [<span data-ttu-id="24d58-115">步驟 3： 測試方案</span><span class="sxs-lookup"><span data-stu-id="24d58-115">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)  
  
## <a name="see-also"></a><span data-ttu-id="24d58-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24d58-116">See Also</span></span>  
 <span data-ttu-id="24d58-117">[開始本教學課程之前](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="24d58-117">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="24d58-118">[第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="24d58-118">[Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md) </span></span>  
 [<span data-ttu-id="24d58-119">第 2 課： 定義商務程序</span><span class="sxs-lookup"><span data-stu-id="24d58-119">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)