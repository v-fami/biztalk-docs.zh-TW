---
title: "部署 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.deployment.application
helpviewer_keywords:
- deploying [applications]
- managing [applications], deploying
- applications, deploying
ms.assetid: eef12d8a-6f5c-4eb2-b85b-df9281c0b88e
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56417fa7e9c4aef40a6c76144a8e2d9e5bae548f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-biztalk-applications"></a><span data-ttu-id="26835-102">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="26835-102">Deploying BizTalk Applications</span></span>
<span data-ttu-id="26835-103">本節提供下列有關部署 BizTalk 應用程式的資訊：</span><span class="sxs-lookup"><span data-stu-id="26835-103">This section provides the following information about deploying BizTalk applications:</span></span>  
  
-   <span data-ttu-id="26835-104">將應用程式及其成品匯出至 Windows Installer (.msi) 檔案</span><span class="sxs-lookup"><span data-stu-id="26835-104">Exporting an application and its artifacts to a Windows Installer (.msi) file</span></span>  
  
-   <span data-ttu-id="26835-105">將 .msi 檔案匯入其他 BizTalk 群組，以便在新群組中建立應用程式及其成品</span><span class="sxs-lookup"><span data-stu-id="26835-105">Importing the .msi file into another BizTalk group to create the application and its artifacts in the new group</span></span>  
  
-   <span data-ttu-id="26835-106">將應用程式安裝在將會予以執行的電腦上</span><span class="sxs-lookup"><span data-stu-id="26835-106">Installing the application on the computers that will run it</span></span>  
  
-   <span data-ttu-id="26835-107">將 BizTalk 組件安裝到全域組件快取 (GAC)</span><span class="sxs-lookup"><span data-stu-id="26835-107">Installing BizTalk assemblies to the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="26835-108">監控應用程式的部署及測試的進度</span><span class="sxs-lookup"><span data-stu-id="26835-108">Monitoring the progress of the deployment and testing the application</span></span>  
  
-   <span data-ttu-id="26835-109">將應用程式部署到商務夥伴</span><span class="sxs-lookup"><span data-stu-id="26835-109">Deploying an application to a business partner</span></span>  
  
-   <span data-ttu-id="26835-110">編輯繫結檔案以自訂不同部署環境的繫結</span><span class="sxs-lookup"><span data-stu-id="26835-110">Editing a binding file to customize the bindings for different deployment environments</span></span>  
  
 <span data-ttu-id="26835-111">您必須在不同的應用程式部署案例中執行的工作檢查清單，請參閱[BizTalk 應用程式部署和管理檢查清單](../core/biztalk-application-deployment-and-management-checklists.md)。</span><span class="sxs-lookup"><span data-stu-id="26835-111">For checklists of tasks that you need to perform in different application deployment scenarios, see [BizTalk Application Deployment and Management Checklists](../core/biztalk-application-deployment-and-management-checklists.md).</span></span> <span data-ttu-id="26835-112">如需 BizTalk 應用程式和其部署的背景資訊，請參閱[瞭解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)。</span><span class="sxs-lookup"><span data-stu-id="26835-112">For background information on BizTalk applications and their deployment, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="26835-113">如需建立應用程式，並修改藉由新增或移除成品或加入另一個應用程式的參考資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="26835-113">For information about creating an application and modifying it by adding or removing artifacts or adding a reference to another application, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).</span></span> <span data-ttu-id="26835-114">如需部署 BizTalk 組件的相關資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="26835-114">For information about deploying BizTalk assemblies, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26835-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="26835-115">In This Section</span></span>  
  
-   [<span data-ttu-id="26835-116">匯出 BizTalk 應用程式、 繫結和原則</span><span class="sxs-lookup"><span data-stu-id="26835-116">Exporting BizTalk Applications, Bindings, and Policies</span></span>](../core/exporting-biztalk-applications-bindings-and-policies.md)  
  
-   [<span data-ttu-id="26835-117">匯入 BizTalk 應用程式、 繫結和原則</span><span class="sxs-lookup"><span data-stu-id="26835-117">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)  
  
-   [<span data-ttu-id="26835-118">如何安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="26835-118">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)  
  
-   [<span data-ttu-id="26835-119">監控 BizTalk 應用程式部署的進度</span><span class="sxs-lookup"><span data-stu-id="26835-119">Monitoring the Progress of Your BizTalk Application Deployment</span></span>](../core/monitoring-the-progress-of-your-biztalk-application-deployment.md)