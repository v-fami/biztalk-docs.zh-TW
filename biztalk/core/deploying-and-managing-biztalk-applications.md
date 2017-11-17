---
title: "部署和管理 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, managing
- Administration Console [BizTalk Server], applications
- bts06.deployment.application
- managing, applications
ms.assetid: d933ad2b-702b-48df-8ef6-a5702d0521e2
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355c66f7550f5e4cf2b04cfc8bb1f705cc6ade7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-managing-biztalk-applications"></a><span data-ttu-id="02327-102">部署和管理 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-102">Deploying and Managing BizTalk Applications</span></span>
<span data-ttu-id="02327-103">本節提供有關管理 BizTalk 應用程式的資訊，包括如何部署、修改、更新及解除部署組件。</span><span class="sxs-lookup"><span data-stu-id="02327-103">This section provides information about managing BizTalk applications, including how to deploy, modify, update, and undeploy them.</span></span> <span data-ttu-id="02327-104">BizTalk 應用程式提供檢視和管理項目 (稱為「成品」) 的方式，這些成品組成 BizTalk 商務方案。</span><span class="sxs-lookup"><span data-stu-id="02327-104">BizTalk applications provide a way to view and manage the items, called "artifacts," that make up a BizTalk business solution.</span></span> <span data-ttu-id="02327-105">成品的範例包括 BizTalk 組件、.NET 組件、結構描述、對應、繫結和憑證等。</span><span class="sxs-lookup"><span data-stu-id="02327-105">Examples of artifacts are BizTalk assemblies, .NET assemblies, schemas, maps, bindings, and certificates.</span></span>  
  
 <span data-ttu-id="02327-106">您可以建立 BizTalk 應用程式，並將成品新增到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="02327-106">You can create a BizTalk application and add artifacts to it.</span></span> <span data-ttu-id="02327-107">接著，您可以從 BizTalk Server 管理主控台，或是使用 BTSTask 命令列工具，將應用程式及其成品當做單一實體來檢視、封裝、部署及管理。</span><span class="sxs-lookup"><span data-stu-id="02327-107">You can then view, package, deploy, and manage the application and its artifacts as a single entity from within the BizTalk Administration console or by using the BTSTask command-line tool.</span></span>  
  
 <span data-ttu-id="02327-108">如需 BizTalk 應用程式部署和維護的背景資訊，請參閱[瞭解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)。</span><span class="sxs-lookup"><span data-stu-id="02327-108">For background information about BizTalk application deployment and maintenance, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="02327-109">如需部署簡單的應用程式的逐步指示，這會讓您熟悉的應用程式部署功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="02327-109">For step-by-step instructions on deploying a simple application, which will familiarize you with the application deployment features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02327-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="02327-110">In This Section</span></span>  
  
-   [<span data-ttu-id="02327-111">部署 BizTalk 應用程式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="02327-111">Best Practices for Deploying a BizTalk Application</span></span>](../core/best-practices-for-deploying-a-biztalk-application.md)  
  
-   [<span data-ttu-id="02327-112">BizTalk 應用程式部署和管理檢查清單</span><span class="sxs-lookup"><span data-stu-id="02327-112">BizTalk Application Deployment and Management Checklists</span></span>](../core/biztalk-application-deployment-and-management-checklists.md)  
  
-   [<span data-ttu-id="02327-113">逐步解說： 部署基本 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-113">Walkthrough: Deploying a Basic BizTalk Application</span></span>](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md) 
  
-   [<span data-ttu-id="02327-114">了解 BizTalk 應用程式部署和管理</span><span class="sxs-lookup"><span data-stu-id="02327-114">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)  
  
-   [<span data-ttu-id="02327-115">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-115">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)  
  
-   [<span data-ttu-id="02327-116">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-116">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)  
  
-   [<span data-ttu-id="02327-117">管理成品</span><span class="sxs-lookup"><span data-stu-id="02327-117">Managing Artifacts</span></span>](../core/managing-artifacts.md)  
  
-   [<span data-ttu-id="02327-118">自訂繫結檔案</span><span class="sxs-lookup"><span data-stu-id="02327-118">Customizing Binding Files</span></span>](../core/customizing-binding-files.md)  
  
-   [<span data-ttu-id="02327-119">使用前置和後置處理指令碼自訂應用程式部署</span><span class="sxs-lookup"><span data-stu-id="02327-119">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)  
  
-   [<span data-ttu-id="02327-120">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-120">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)  
  
-   [<span data-ttu-id="02327-121">更新 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-121">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)  
  
-   [<span data-ttu-id="02327-122">解除部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02327-122">Undeploying BizTalk Applications</span></span>](../core/undeploying-biztalk-applications.md)