---
title: "部署及管理 BizTalk 應用程式所需的權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], security
- permissions, EDI adapters
- deploying, security
- security, applications
- security, EDI adapters
- assemblies, permissions
- permissions, deploying
- EDI adapters, security
- permissions, assemblies
- security, assemblies
- permissions, applications
- deploying, permissions
- applications, importing
- applications, exporting
- permissions, exporting
- installing, permissions
- applications, security
- security, permissions
- applications, installing
- assemblies, security
- managing, security
ms.assetid: 4a459ff1-661d-403a-99e0-d54b82e008d0
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 608da93cd1960d26304f4dcebe239367de2404e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="permissions-required-for-deploying-and-managing-a-biztalk-application"></a><span data-ttu-id="d9c1b-102">部署和管理 BizTalk 應用程式所需的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-102">Permissions Required for Deploying and Managing a BizTalk Application</span></span>
<span data-ttu-id="d9c1b-103">應用程式部署包括從 Visual Studio 部署 BizTalk 組件，以及匯入、匯出和安裝 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-103">Application deployment includes deploying BizTalk assemblies from Visual Studio as well as importing, exporting, and installing BizTalk applications.</span></span> <span data-ttu-id="d9c1b-104">執行這些工作所需的基本權限如下：</span><span class="sxs-lookup"><span data-stu-id="d9c1b-104">The basic permissions you need to perform these tasks are as follows:</span></span>  
  
-   <span data-ttu-id="d9c1b-105">身為「BizTalk Server 系統管理員」群組的成員，您將被授與從 Visual Studio 部署 BizTalk 組件所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-105">As a member of the BizTalk Server Administrators group, you are granted the permissions required to deploy BizTalk assemblies from Visual Studio.</span></span>  
  
-   <span data-ttu-id="d9c1b-106">身為「BizTalk Server 系統管理員」群組的成員，您將被授與將 BizTalk 應用程式匯入 BizTalk 群組所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-106">As a member of the BizTalk Server Administrators group, you are granted the permissions required to import BizTalk applications into a BizTalk group.</span></span> <span data-ttu-id="d9c1b-107">如果已指定在匯入時將應用程式中包含的組件新增到全域組件快取 (GAC) 的選項，您也必須擁有組件資料夾的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-107">If the option to add an assembly included in the application to the global assembly cache (GAC) on import has been specified, you must also have Write permissions on the assembly folder.</span></span> <span data-ttu-id="d9c1b-108">身為本機「系統管理員」群組的成員，您將擁有此權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-108">As a member of the local Administrators group, you have this permission.</span></span>  
  
-   <span data-ttu-id="d9c1b-109">身為「BizTalk Server 系統管理員」或「BizTalk 操作員」群組的成員，您將被授與執行以下動作所需的權限：</span><span class="sxs-lookup"><span data-stu-id="d9c1b-109">As a member of the BizTalk Server Administrators or BizTalk Server Operators group, you are granted the permissions required to:</span></span>  
  
    -   <span data-ttu-id="d9c1b-110">匯出 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="d9c1b-110">Export BizTalk applications</span></span>  
  
    -   <span data-ttu-id="d9c1b-111">啟動和停止傳送埠、傳送埠群組和協調流程</span><span class="sxs-lookup"><span data-stu-id="d9c1b-111">Start and stop send ports, send port groups, and orchestrations</span></span>  
  
    -   <span data-ttu-id="d9c1b-112">啟用和停用接收位置</span><span class="sxs-lookup"><span data-stu-id="d9c1b-112">Enable and disable receive locations</span></span>  
  
    -   <span data-ttu-id="d9c1b-113">擱置、繼續和終止執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-113">Suspend, resume, and terminate instances</span></span>  
  
    -   <span data-ttu-id="d9c1b-114">啟動和停止應用程式</span><span class="sxs-lookup"><span data-stu-id="d9c1b-114">Start and stop applications</span></span>  
  
-   <span data-ttu-id="d9c1b-115">身為本機「系統管理員」群組的成員，您將被授與在本機電腦上安裝 BizTalk 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-115">As a member of the local Administrators group you are granted permissions to install BizTalk applications on the local computer.</span></span>  
  
 <span data-ttu-id="d9c1b-116">您可能會想要為使用者提供執行這些工作最嚴格的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-116">You may want to provide the most restrictive permissions for users to perform these tasks.</span></span> <span data-ttu-id="d9c1b-117">本主題接下來將為所需的權限提供更詳盡的說明，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-117">The remainder of this topic provides more details on the required permissions, as follows.</span></span>  
  
-   [<span data-ttu-id="d9c1b-118">部署 BizTalk 組件從 Visual Studio 的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-118">Permissions for deploying BizTalk assemblies from Visual Studio</span></span>](#BKMK_Permissions_for_deploying)  
  
-   [<span data-ttu-id="d9c1b-119">匯入應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-119">Permissions for importing an application</span></span>](#BKMK_Permissions_for_importing)  
  
-   [<span data-ttu-id="d9c1b-120">匯出應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-120">Permissions for exporting an application</span></span>](#BKMK_Permissions_for_exporting)  
  
-   [<span data-ttu-id="d9c1b-121">安裝應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-121">Permissions for installing an application</span></span>](#BKMK_Permissions_for_installing_an_application)  
  
##  <span data-ttu-id="d9c1b-122"><a name="BKMK_Permissions_for_deploying"></a>部署 BizTalk 組件從 Visual Studio 的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-122"><a name="BKMK_Permissions_for_deploying"></a> Permissions for deploying BizTalk assemblies from Visual Studio</span></span>  
 <span data-ttu-id="d9c1b-123">若要從 Visual Studio 中部署 BizTalk 組件，您必須至少擁有 BizTalk 管理資料庫的「寫入」權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-123">To deploy BizTalk assemblies from within Visual Studio, you must have Write permission on the BizTalk Management database, at a minimum.</span></span> <span data-ttu-id="d9c1b-124">身為「BizTalk Server 系統管理員」群組的成員，您將被授與此權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-124">You are granted this permission as a member of the BizTalk Server Administrators group.</span></span>  
  
##  <span data-ttu-id="d9c1b-125"><a name="BKMK_Permissions_for_importing"></a>匯入應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-125"><a name="BKMK_Permissions_for_importing"></a> Permissions for importing an application</span></span>  
 <span data-ttu-id="d9c1b-126">若要匯入 BizTalk 應用程式，您至少必須擁有下列權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-126">To import a BizTalk application, you must have the following permissions, at a minimum.</span></span> <span data-ttu-id="d9c1b-127">身為「BizTalk Server 系統管理員」群組的成員，您將被授與所有需要的權限，但如果您想要將任何組件安裝到 GAC，您還必須擁有組件資料夾的「寫入」權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-127">You are granted all of the required permissions as a member of the BizTalk Server Administrators group, except that if you want to install any assemblies to the GAC, you must also have Write permissions on the assembly folder.</span></span>  
  
|<span data-ttu-id="d9c1b-128">項目</span><span class="sxs-lookup"><span data-stu-id="d9c1b-128">Item</span></span>|<span data-ttu-id="d9c1b-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="d9c1b-129">Permissions</span></span>|<span data-ttu-id="d9c1b-130">需要時</span><span class="sxs-lookup"><span data-stu-id="d9c1b-130">When Required</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="d9c1b-131">BizTalk 管理資料庫</span><span class="sxs-lookup"><span data-stu-id="d9c1b-131">BizTalk Management database</span></span>|<span data-ttu-id="d9c1b-132">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-132">Read/Write</span></span>|<span data-ttu-id="d9c1b-133">永遠需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-133">Always required.</span></span>|  
|<span data-ttu-id="d9c1b-134">BizTalk 規則引擎資料庫</span><span class="sxs-lookup"><span data-stu-id="d9c1b-134">BizTalk Rule Engine database</span></span>|<span data-ttu-id="d9c1b-135">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-135">Read/Write</span></span>|<span data-ttu-id="d9c1b-136">只有應用程式包括規則資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-136">Required only if the application includes rules resources.</span></span>|  
|<span data-ttu-id="d9c1b-137">BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="d9c1b-137">BAM database</span></span>|<span data-ttu-id="d9c1b-138">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-138">Read/Write</span></span>|<span data-ttu-id="d9c1b-139">只有應用程式包括 BAM 資源時才需要</span><span class="sxs-lookup"><span data-stu-id="d9c1b-139">Required only if the application includes BAM resources</span></span>|  
|<span data-ttu-id="d9c1b-140">全域組件快取 (GAC)</span><span class="sxs-lookup"><span data-stu-id="d9c1b-140">Global assembly cache (GAC)</span></span>|<span data-ttu-id="d9c1b-141">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-141">Read/Write</span></span>|<span data-ttu-id="d9c1b-142">只有當應用程式包括組件資源並且您指定在匯入時將組件加入 GAC 時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-142">Required only if the application includes assembly resources, and you specify that the assemblies are added to the GAC on import.</span></span> <span data-ttu-id="d9c1b-143">(請參閱注意。)</span><span class="sxs-lookup"><span data-stu-id="d9c1b-143">(See Note.)</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d9c1b-144">當使用「匯入精靈」匯入組件時，您可以指定此選項以新增組件至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-144">When importing an assembly by using the Import Wizard, you can specify the option to add the assembly to the global assembly cache (GAC).</span></span> <span data-ttu-id="d9c1b-145">在此情況下，您必須擁有組件資料夾的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-145">In this case, you must have write permission on the assembly folder.</span></span> <span data-ttu-id="d9c1b-146">如需組件資料夾的詳細資訊，請參閱[安裝應用程式的權限](#BKMK_Permissions_for_installing_an_application)。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-146">For more information about the assembly folder, see [Permissions for installing an application](#BKMK_Permissions_for_installing_an_application).</span></span>  
>   
>  <span data-ttu-id="d9c1b-147">如果您的應用程式包含的某個指令碼會部署除了所列以外的任何項目，您必須有適當的權限才能進行部署。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-147">If your application includes a script that deploys any items in addition to those listed, you must have appropriate permissions to deploy the additional items.</span></span>  
  
##  <span data-ttu-id="d9c1b-148"><a name="BKMK_Permissions_for_exporting"></a>匯出應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-148"><a name="BKMK_Permissions_for_exporting"></a> Permissions for exporting an application</span></span>  
 <span data-ttu-id="d9c1b-149">若要匯出 BizTalk 應用程式，您至少必須擁有下列權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-149">To export a BizTalk application, you must have the following permissions, at a minimum.</span></span> <span data-ttu-id="d9c1b-150">身為「BizTalk 作員」群組的成員，您將被授與所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-150">You are granted the required permissions as a member of the BizTalk Operators group.</span></span>  
  
|<span data-ttu-id="d9c1b-151">項目</span><span class="sxs-lookup"><span data-stu-id="d9c1b-151">Item</span></span>|<span data-ttu-id="d9c1b-152">Permissions</span><span class="sxs-lookup"><span data-stu-id="d9c1b-152">Permissions</span></span>|<span data-ttu-id="d9c1b-153">需要時</span><span class="sxs-lookup"><span data-stu-id="d9c1b-153">When Required</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="d9c1b-154">BizTalk 管理資料庫</span><span class="sxs-lookup"><span data-stu-id="d9c1b-154">BizTalk Management database</span></span>|<span data-ttu-id="d9c1b-155">讀取</span><span class="sxs-lookup"><span data-stu-id="d9c1b-155">Read</span></span>|<span data-ttu-id="d9c1b-156">永遠需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-156">Always required.</span></span>|  
|<span data-ttu-id="d9c1b-157">BizTalk 規則引擎資料庫</span><span class="sxs-lookup"><span data-stu-id="d9c1b-157">BizTalk Rule Engine database</span></span>|<span data-ttu-id="d9c1b-158">讀取</span><span class="sxs-lookup"><span data-stu-id="d9c1b-158">Read</span></span>|<span data-ttu-id="d9c1b-159">只有應用程式包括規則資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-159">Required only if the application includes rules resources.</span></span>|  
|<span data-ttu-id="d9c1b-160">憑證存放區</span><span class="sxs-lookup"><span data-stu-id="d9c1b-160">Certificate store</span></span>|<span data-ttu-id="d9c1b-161">讀取</span><span class="sxs-lookup"><span data-stu-id="d9c1b-161">Read</span></span>|<span data-ttu-id="d9c1b-162">只有應用程式包括憑證資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-162">Required only if the application includes certificate resources.</span></span>|  
|<span data-ttu-id="d9c1b-163">Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="d9c1b-163">Internet Information Services</span></span>|<span data-ttu-id="d9c1b-164">讀取</span><span class="sxs-lookup"><span data-stu-id="d9c1b-164">Read</span></span>|<span data-ttu-id="d9c1b-165">只有應用程式包括虛擬目錄資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-165">Required only if the application includes virtual directory resources.</span></span>|  
  
##  <span data-ttu-id="d9c1b-166"><a name="BKMK_Permissions_for_installing_an_application"></a>安裝應用程式的權限</span><span class="sxs-lookup"><span data-stu-id="d9c1b-166"><a name="BKMK_Permissions_for_installing_an_application"></a> Permissions for installing an application</span></span>  
 <span data-ttu-id="d9c1b-167">依照預設，身為本機「系統管理員」群組的成員會擁有在本機電腦上安裝 BizTalk 應用程式所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-167">By default, members of the local Administrators group have the permissions required to install BizTalk applications on the local computer.</span></span> <span data-ttu-id="d9c1b-168">如果您想要為需要安裝應用程式的使用者提供最嚴格的權限，下表提供您必須設定的最低權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-168">If you want to provide more restricted permissions to users who need to install applications, the following table provides the minimum permissions that you must configure.</span></span> <span data-ttu-id="d9c1b-169">除了這些權限以外，如果您的應用程式擁有需要其他權限才能安裝的資源，例如建立新資料庫或資料庫資料表，您還必須擁有這些權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-169">In addition to these permissions, if your application has resources that require additional permissions to install, such as to create a new database or database table, you must also have these permissions.</span></span>  
  
|<span data-ttu-id="d9c1b-170">項目</span><span class="sxs-lookup"><span data-stu-id="d9c1b-170">Item</span></span>|<span data-ttu-id="d9c1b-171">Permissions</span><span class="sxs-lookup"><span data-stu-id="d9c1b-171">Permissions</span></span>|<span data-ttu-id="d9c1b-172">需要時</span><span class="sxs-lookup"><span data-stu-id="d9c1b-172">When Required</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="d9c1b-173">憑證存放區</span><span class="sxs-lookup"><span data-stu-id="d9c1b-173">Certificate store</span></span>|<span data-ttu-id="d9c1b-174">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-174">Read/Write</span></span>|<span data-ttu-id="d9c1b-175">只有應用程式包括憑證資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-175">Required only if the application includes certificate resources.</span></span>|  
|<span data-ttu-id="d9c1b-176">Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="d9c1b-176">Internet Information Services</span></span>|<span data-ttu-id="d9c1b-177">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-177">Read/Write</span></span>|<span data-ttu-id="d9c1b-178">只有應用程式包括虛擬目錄資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-178">Required only if the application includes virtual directory resources.</span></span>|  
|<span data-ttu-id="d9c1b-179">GAC</span><span class="sxs-lookup"><span data-stu-id="d9c1b-179">GAC</span></span>|<span data-ttu-id="d9c1b-180">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-180">Read/Write</span></span>|<span data-ttu-id="d9c1b-181">只有當應用程式包括組件資源並且您指定在安裝時將組件加入 GAC 時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-181">Required only if the application includes assembly resources, and you specify that the assemblies are added to the GAC on install.</span></span> <span data-ttu-id="d9c1b-182">(參閱下方的注意。)</span><span class="sxs-lookup"><span data-stu-id="d9c1b-182">(See Note, below.)</span></span>|  
|<span data-ttu-id="d9c1b-183">檔案系統</span><span class="sxs-lookup"><span data-stu-id="d9c1b-183">File system</span></span>|<span data-ttu-id="d9c1b-184">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-184">Read/Write</span></span>|<span data-ttu-id="d9c1b-185">只有在資源已設定目的屬性時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-185">Required only if a destination property has been set for a resource.</span></span>|  
|<span data-ttu-id="d9c1b-186">登錄</span><span class="sxs-lookup"><span data-stu-id="d9c1b-186">Registry</span></span>|<span data-ttu-id="d9c1b-187">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-187">Read/Write</span></span>|<span data-ttu-id="d9c1b-188">若**regsvcs**或**regasm**屬性設為 True，適用於組件資源包含 managed COM 或 COM + 元件。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-188">Required if the **regsvcs** or **regasm**property is set to True for an assembly resource containing managed COM or COM+ components.</span></span>|  
|<span data-ttu-id="d9c1b-189">登錄</span><span class="sxs-lookup"><span data-stu-id="d9c1b-189">Registry</span></span>|<span data-ttu-id="d9c1b-190">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="d9c1b-190">Read/Write</span></span>|<span data-ttu-id="d9c1b-191">當應用程式包括 Unmanaged COM 資源時才需要。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-191">Required if the application includes unmanaged COM resources</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d9c1b-192">從 BizTalk Server 管理主控台，您可以指定在安裝時將組件加入 GAC (使用滑鼠右鍵按一下資源資料夾中的組件，然後按一下 [修改])。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-192">From the BizTalk Server Administration console, you can specify that an assembly be added to the GAC on installation (right-click the assembly in the resources folder and then click Modify).</span></span> <span data-ttu-id="d9c1b-193">如果指定此選項，則安裝 BizTalk 應用程式將需要組件資料夾 (包含 GAC) 的「寫入」權限。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-193">If this option is specified, then installing the BizTalk application requires Write permission on the assembly folder, which contains the GAC.</span></span> <span data-ttu-id="d9c1b-194">組件資料夾的路徑為 %SystemRoot%\assembly。</span><span class="sxs-lookup"><span data-stu-id="d9c1b-194">The path of the assembly folder is %SystemRoot%\assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c1b-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c1b-195">See Also</span></span>  
 [<span data-ttu-id="d9c1b-196">應用程式部署的安全性考量</span><span class="sxs-lookup"><span data-stu-id="d9c1b-196">Security Considerations for Application Deployment</span></span>](../core/security-considerations-for-application-deployment.md)