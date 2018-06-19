---
title: 部署組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65f8ee21-0e52-4a74-b114-864a3069659c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73112fd9efb536452b8641faa976f42bb892b67c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297862"
---
# <a name="deploying-an-assembly"></a><span data-ttu-id="c2624-102">部署組件</span><span class="sxs-lookup"><span data-stu-id="c2624-102">Deploying an Assembly</span></span>
<span data-ttu-id="c2624-103">部署組件會建置組件並匯入，以及協調流程、 管線、 結構描述和對應 （成品），它包含到本機 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c2624-103">Deploying an assembly builds the assembly and imports it, along with the orchestrations, pipelines, schemas, and maps (artifacts) that it contains into the local BizTalk Management database.</span></span> <span data-ttu-id="c2624-104">一開始，這是在開發環境中。</span><span class="sxs-lookup"><span data-stu-id="c2624-104">Initially, this is done in the development environment.</span></span>  
  
 <span data-ttu-id="c2624-105">部署也會將組件與您在 Visual Studio 中的專案屬性中所指定的 BizTalk 應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c2624-105">Deployment also associates the assembly with the BizTalk application that you have specified in project properties within Visual Studio.</span></span> <span data-ttu-id="c2624-106">在部署解決方案以後，您便能夠從 [BizTalk Server 管理主控台] 內，或是使用 BTSTask 命令列工具，來檢視和管理已部署的組件及其成品。</span><span class="sxs-lookup"><span data-stu-id="c2624-106">After you deploy a solution, you can view and manage the deployed assemblies and their artifacts from within the BizTalk Server Administration console or by using the BTSTask command-line tool.</span></span> <span data-ttu-id="c2624-107">您可以管理成品可以個別或應用程式中予以分組。</span><span class="sxs-lookup"><span data-stu-id="c2624-107">You can manage the artifacts either individually or grouped within the application.</span></span>  
  
## <a name="deploying-an-assembly"></a><span data-ttu-id="c2624-108">部署組件</span><span class="sxs-lookup"><span data-stu-id="c2624-108">Deploying an Assembly</span></span>  
 <span data-ttu-id="c2624-109">您可以下列方式加入應用程式組件：</span><span class="sxs-lookup"><span data-stu-id="c2624-109">You can add assemblies to applications in the following ways:</span></span>  
  
-   <span data-ttu-id="c2624-110">將組件部署到應用程式的 Visual Studio 環境中</span><span class="sxs-lookup"><span data-stu-id="c2624-110">Deploy an assembly to an application from within the Visual Studio environment</span></span>  
  
-   <span data-ttu-id="c2624-111">手動新增到應用程式的 BizTalk Server 管理主控台中的 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="c2624-111">Manually add BizTalk Server assemblies to the application from within the BizTalk Server Administration console</span></span>  
  
-   <span data-ttu-id="c2624-112">使用從命令列指令碼，將 BizTalk 組件加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="c2624-112">Add a BizTalk assembly to an application by using script from the command line</span></span>  
  
-   <span data-ttu-id="c2624-113">從 BizTalk Server 管理主控台從其他應用程式移動 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="c2624-113">Move BizTalk Server assemblies from other applications from within the BizTalk Server Administration console</span></span>  
  
 <span data-ttu-id="c2624-114">如需將組件加入至應用程式的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。</span><span class="sxs-lookup"><span data-stu-id="c2624-114">For more information about adding assemblies to applications, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).</span></span>  
  
## <a name="redeploying-assemblies"></a><span data-ttu-id="c2624-115">重新部署組件</span><span class="sxs-lookup"><span data-stu-id="c2624-115">Redeploying Assemblies</span></span>  
 <span data-ttu-id="c2624-116">在開發和偵錯您的 BizTalk 組件，您可能需要將其重新佈署多次。</span><span class="sxs-lookup"><span data-stu-id="c2624-116">In the process of developing and debugging your BizTalk assemblies, you may need to redeploy them multiple times.</span></span> <span data-ttu-id="c2624-117">BizTalk Server 提供的簡易機制，重新部署。</span><span class="sxs-lookup"><span data-stu-id="c2624-117">BizTalk Server provides a simple mechanism for redeployment.</span></span> <span data-ttu-id="c2624-118">如果您重新部署組件，而不變更版本號碼，您可以使用重新部署屬性。</span><span class="sxs-lookup"><span data-stu-id="c2624-118">If you are redeploying an assembly without changing the version number, you can use the Redeploy property.</span></span> <span data-ttu-id="c2624-119">BizTalk Server 將會自動執行所有步驟，重新部署您的組件。</span><span class="sxs-lookup"><span data-stu-id="c2624-119">BizTalk Server will automatically perform all of the steps to redeploy the assembly for you.</span></span>  
  
 <span data-ttu-id="c2624-120">如需有關重新部署組件的詳細資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720)。</span><span class="sxs-lookup"><span data-stu-id="c2624-120">For more information about redeploying assemblies, see [How to Redeploy a BizTalk Assembly from Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720).</span></span>  
  
### <a name="best-practices-for-redeploying-an-assembly"></a><span data-ttu-id="c2624-121">重新部署組件的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c2624-121">Best Practices for Redeploying an Assembly</span></span>  
 <span data-ttu-id="c2624-122">**您必須在 GAC 中安裝新的組件**</span><span class="sxs-lookup"><span data-stu-id="c2624-122">**You must install the new assembly in the GAC**</span></span>  
  
-   <span data-ttu-id="c2624-123">當您重新部署組件時，所以您必須一律在全域組件快取 (GAC) 中安裝新版的組件。</span><span class="sxs-lookup"><span data-stu-id="c2624-123">When you redeploy an assembly, you must always install the new version of the assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="c2624-124">您可以在重新部署後執行此作業。</span><span class="sxs-lookup"><span data-stu-id="c2624-124">You can do this after you redeploy it.</span></span> <span data-ttu-id="c2624-125">如需詳細資訊，請參閱[如何在 GAC 中安裝組件](http://go.microsoft.com/fwlink/?LinkID=154828)(http://go.microsoft.com/fwlink/?LinkID=154828)。</span><span class="sxs-lookup"><span data-stu-id="c2624-125">For more information, see [How to Install an Assembly in the GAC](http://go.microsoft.com/fwlink/?LinkID=154828) (http://go.microsoft.com/fwlink/?LinkID=154828).</span></span>  
  
 <span data-ttu-id="c2624-126">**您應該永遠重新部署方案層級相依性存在時**</span><span class="sxs-lookup"><span data-stu-id="c2624-126">**You should always redeploy at the solution level when there are dependencies**</span></span>  
  
-   <span data-ttu-id="c2624-127">如果解決方案中有多個組件，而且此解決方案中的一或多個組件相依於要重新部署的組件，則您必須在解決方案層級重新部署組件。</span><span class="sxs-lookup"><span data-stu-id="c2624-127">If you have multiple assemblies in a solution, and one or more assemblies in the solution has a dependency on the assembly that you want to redeploy, you should redeploy your assemblies at the solution level.</span></span> <span data-ttu-id="c2624-128">這是因為 BizTalk Server 時重新部署組件在專案層級，將會停止、 取消登錄、 解除繫結，並移除這個組件所依存的任何相依或此組件上的所有組件中的所有成品。</span><span class="sxs-lookup"><span data-stu-id="c2624-128">This is because when you redeploy an assembly at the project level, BizTalk Server will stop, unenlist, unbind, and remove the artifacts in all assemblies that either depend on this assembly or on upon which this assembly depends.</span></span> <span data-ttu-id="c2624-129">BizTalk Server 不會執行部署、繫結、登錄和啟動成品的額外步驟。</span><span class="sxs-lookup"><span data-stu-id="c2624-129">BizTalk Server will not take the additional steps to deploy, bind, enlist, and start the artifacts.</span></span> <span data-ttu-id="c2624-130">不過，當您重新部署整個解決方案時，BizTalk Server 會自動執行必要步驟，根據成品的相依性，解除部署和重新部署解決方案中的所有成品。</span><span class="sxs-lookup"><span data-stu-id="c2624-130">When you redeploy the entire solution, however, BizTalk Server automatically takes the steps required to undeploy and redeploy all of the artifacts in the solution based on their dependencies.</span></span>  
  
 <span data-ttu-id="c2624-131">**您可能需要手動重新部署相依組件**</span><span class="sxs-lookup"><span data-stu-id="c2624-131">**You may need to manually redeploy dependent assemblies**</span></span>  
  
-   <span data-ttu-id="c2624-132">BizTalk Server 固定會解除部署相依組件時，它會解除部署組件，但在下列情況下，您必須採取其他步驟，部署、 繫結，並且登錄之後重新部署組件所在的每個相依組件中的成品組件而定：</span><span class="sxs-lookup"><span data-stu-id="c2624-132">BizTalk Server always undeploys dependent assemblies when it undeploys an assembly, but in the following cases, you must take the additional steps to deploy, bind, and enlist the artifacts in each dependent assembly after redeploying the assembly on which the assembly depends:</span></span>  
  
     <span data-ttu-id="c2624-133">如果您在專案層級重新部署組件，而且相同解決方案中的另一個組件相依於此組件。</span><span class="sxs-lookup"><span data-stu-id="c2624-133">If you redeploy an assembly at the project level and another assembly in the same solution depends on it.</span></span>  
  
     <span data-ttu-id="c2624-134">如果您在解決方案層級重新部署組件，但不同解決方案中存在相依組件。</span><span class="sxs-lookup"><span data-stu-id="c2624-134">If you redeploy an assembly at the solution level, but a dependent assembly exists in a different solution.</span></span>  
  
 <span data-ttu-id="c2624-135">**您必須重新啟動主控件執行個體**</span><span class="sxs-lookup"><span data-stu-id="c2624-135">**You must restart host instances**</span></span>  
  
-   <span data-ttu-id="c2624-136">當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="c2624-136">When you redeploy an assembly that contains an orchestration without changing the assembly version number, the existing assembly is overwritten in the BizTalk Management database.</span></span> <span data-ttu-id="c2624-137">不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2624-137">Before the change will take effect, however, you must restart each host instance of the host to which the orchestration is bound.</span></span> <span data-ttu-id="c2624-138">您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2624-138">You can specify the option that all host instances on the local computer restart automatically when you redeploy an assembly.</span></span>  
  
     <span data-ttu-id="c2624-139">當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="c2624-139">When you redeploy an assembly that contains an orchestration without changing the assembly version number, the existing assembly is overwritten in the BizTalk Management database.</span></span> <span data-ttu-id="c2624-140">不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2624-140">Before the change will take effect, however, you must restart each host instance of the host to which the orchestration is bound.</span></span> <span data-ttu-id="c2624-141">您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2624-141">You can specify the option that all host instances on the local computer restart automatically when you redeploy an assembly.</span></span> <span data-ttu-id="c2624-142">如需部署屬性的詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](http://go.microsoft.com/fwlink/?LinkID=154718)(http://go.microsoft.com/fwlink/?LinkID=154718)。</span><span class="sxs-lookup"><span data-stu-id="c2624-142">For more information about deployment properties, see [How to Set Deployment Properties in Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154718) (http://go.microsoft.com/fwlink/?LinkID=154718).</span></span>  
  
     <span data-ttu-id="c2624-143">您也可以手動即可停止和啟動每個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2624-143">You can also manually stop and start each host instance.</span></span> <span data-ttu-id="c2624-144">如需停止和啟動主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154829)(http://go.microsoft.com/fwlink/?LinkID = 154829) 和[如何啟動主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154830)(http://go.microsoft.com/fwlink/?LinkID = 154830)。</span><span class="sxs-lookup"><span data-stu-id="c2624-144">For more information about stopping and starting a host instance, see [How to Stop a Host Instance](http://go.microsoft.com/fwlink/?LinkID=154829) (http://go.microsoft.com/fwlink/?LinkID=154829) and [How to Start a Host Instance](http://go.microsoft.com/fwlink/?LinkID=154830) (http://go.microsoft.com/fwlink/?LinkID=154830).</span></span>