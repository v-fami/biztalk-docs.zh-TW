---
title: 了解 BizTalk 應用程式部署和管理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying [applications]
- managing [applications], deploying
- applications, deploying
- deploying, what's new
- applications, managing
- what's new, deploying
- deploying [applications], what's new
- managing [applications], what's new
- applications, what's new
- what's new, applications
- managing, applications
ms.assetid: 4bc1677d-24a2-4f55-83b2-6dfc39767072
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82d9596f2f8261b35035ead291f2a7d1bb859a5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286622"
---
# <a name="understanding-biztalk-application-deployment-and-management"></a><span data-ttu-id="424d4-102">瞭解 BizTalk 應用程式部署和管理</span><span class="sxs-lookup"><span data-stu-id="424d4-102">Understanding BizTalk Application Deployment and Management</span></span>
<span data-ttu-id="424d4-103">本節簡介 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的新應用程式部署和管理功能，並提供背景資訊以協助您瞭解如何使用這些功能來部署和管理 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="424d4-103">This section introduces the new application deployment and management features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and provides background information that will help you understand how to use these features to deploy and manage BizTalk applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="424d4-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="424d4-104">In This Section</span></span>  
  
-   [<span data-ttu-id="424d4-105">什麼是 BizTalk 應用程式？</span><span class="sxs-lookup"><span data-stu-id="424d4-105">What Is a BizTalk Application?</span></span>](../core/what-is-a-biztalk-application.md)  
  
-   [<span data-ttu-id="424d4-106">應用程式部署程序</span><span class="sxs-lookup"><span data-stu-id="424d4-106">The Application Deployment Process</span></span>](../core/the-application-deployment-process.md)  
  
-   [<span data-ttu-id="424d4-107">應用程式部署和管理功能</span><span class="sxs-lookup"><span data-stu-id="424d4-107">Application Deployment and Management Features</span></span>](../core/application-deployment-and-management-features.md)  
  
-   [<span data-ttu-id="424d4-108">應用程式部署和管理工具</span><span class="sxs-lookup"><span data-stu-id="424d4-108">Application Deployment and Management Tools</span></span>](../core/application-deployment-and-management-tools.md)  
  
-   [<span data-ttu-id="424d4-109">應用程式部署和管理案例</span><span class="sxs-lookup"><span data-stu-id="424d4-109">Application Deployment and Management Scenarios</span></span>](../core/application-deployment-and-management-scenarios.md)  
  
-   [<span data-ttu-id="424d4-110">會發生什麼事成品至應用程式部署期間</span><span class="sxs-lookup"><span data-stu-id="424d4-110">What Happens to Artifacts During Application Deployment</span></span>](../core/what-happens-to-artifacts-during-application-deployment.md)  
  
-   [<span data-ttu-id="424d4-111">應用程式部署工作</span><span class="sxs-lookup"><span data-stu-id="424d4-111">Application Deployment Tasks</span></span>](../core/application-deployment-tasks.md)  
  
-   [<span data-ttu-id="424d4-112">應用程式部署的安全性考量</span><span class="sxs-lookup"><span data-stu-id="424d4-112">Security Considerations for Application Deployment</span></span>](../core/security-considerations-for-application-deployment.md)  
  
-   [<span data-ttu-id="424d4-113">相依性和應用程式部署</span><span class="sxs-lookup"><span data-stu-id="424d4-113">Dependencies and Application Deployment</span></span>](../core/dependencies-and-application-deployment.md)  
  
-   [<span data-ttu-id="424d4-114">繫結檔案和應用程式部署</span><span class="sxs-lookup"><span data-stu-id="424d4-114">Binding Files and Application Deployment</span></span>](../core/binding-files-and-application-deployment.md)  
  
-   [<span data-ttu-id="424d4-115">中的應用程式或群組必須是唯一的成品</span><span class="sxs-lookup"><span data-stu-id="424d4-115">Artifacts That Must Be Unique in an Application or Group</span></span>](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)  
  
-   [<span data-ttu-id="424d4-116">組件安裝在 GAC 中</span><span class="sxs-lookup"><span data-stu-id="424d4-116">Assembly Installation in the GAC</span></span>](../core/assembly-installation-in-the-gac.md)