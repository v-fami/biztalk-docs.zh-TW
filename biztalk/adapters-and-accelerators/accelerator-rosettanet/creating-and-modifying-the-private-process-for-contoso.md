---
title: 建立與修改 Contoso 私用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private processes, creating
- configuring, private processes
- private processes, configuring
- private process tutorial, creating private processes
- creating, private processes
- private process tutorial, configuring private processes
ms.assetid: 0690aaef-cd9e-46aa-8bd5-22744d5aec4c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 544dce433b439cae937b1328690f099b5b6ca592
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012151"
---
# <a name="creating-and-modifying-the-private-process-for-contoso"></a><span data-ttu-id="09eea-102">建立與修改 Contoso 私用程序</span><span class="sxs-lookup"><span data-stu-id="09eea-102">Creating and Modifying the Private Process for Contoso</span></span>
<span data-ttu-id="09eea-103">藉由自訂私用程序，Microsoft® 內實作您的解決方案時，您可以執行與 RosettaNet 訊息的其他工作[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="09eea-103">You can perform additional tasks with RosettaNet-based messages when implementing your solution by customizing the private process within Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="09eea-104">本節會展示如何使用「商務規則引擎」(BRE) 建立原則，以及如何利用 BizTalk 編輯器自訂私用程序協調流程，藉此自訂私用程序。</span><span class="sxs-lookup"><span data-stu-id="09eea-104">This section demonstrates how to customize the private process by using the Business Rule Engine (BRE) to create policies and BizTalk Editor to customize the private process orchestration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09eea-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="09eea-105">In This Section</span></span>  
  
-   [<span data-ttu-id="09eea-106">步驟 1：將現有的 BizTalk 專案新增至現有的 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="09eea-106">Step 1: Adding an Existing BizTalk Project to the Existing Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-adding-an-existing-biztalk-project-to-the-existing-contoso-solution.md)  
  
-   [<span data-ttu-id="09eea-107">步驟 2：定義與發佈 Contoso 的詞彙</span><span class="sxs-lookup"><span data-stu-id="09eea-107">Step 2: Defining and Publishing the Vocabulary for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)  
  
-   [<span data-ttu-id="09eea-108">步驟 3：定義、發佈與部署 Contoso 的商務原則</span><span class="sxs-lookup"><span data-stu-id="09eea-108">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)  
  
-   [<span data-ttu-id="09eea-109">步驟 4：建立 HeaderHelper 專案</span><span class="sxs-lookup"><span data-stu-id="09eea-109">Step 4: Creating the HeaderHelper Project</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)  
  
-   [<span data-ttu-id="09eea-110">步驟 5：修改 Contoso 私用程序協調流程</span><span class="sxs-lookup"><span data-stu-id="09eea-110">Step 5: Modifying the Contoso Private Process Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)  
  
-   [<span data-ttu-id="09eea-111">步驟 6：設定協調流程圖形 (Contoso)</span><span class="sxs-lookup"><span data-stu-id="09eea-111">Step 6: Configuring Orchestration Shapes (Contoso)</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)  
  
-   [<span data-ttu-id="09eea-112">步驟 7：建立與設定連接埠</span><span class="sxs-lookup"><span data-stu-id="09eea-112">Step 7: Creating and Configuring Ports</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)  
  
-   [<span data-ttu-id="09eea-113">步驟 8：建立與部署 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="09eea-113">Step 8: Building and Deploying the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)  
  
-   [<span data-ttu-id="09eea-114">步驟 9：啟動 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="09eea-114">Step 9: Starting the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)