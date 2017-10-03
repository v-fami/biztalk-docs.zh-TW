---
title: "升級 BizTalk Server 中的 RosettaNet 加速器 (BTARN) |Microsoft 文件 」"
description: "請依照下列升級步驟來更新到 BizTalk Server 中的目前版本的 BTARN"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 16e6083f3e5fb1778d77536cd602ee2208c0005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="upgrade-the-rosettanet-accelerator"></a><span data-ttu-id="50eef-103">升級 RosettaNet 加速器</span><span class="sxs-lookup"><span data-stu-id="50eef-103">Upgrade the RosettaNet accelerator</span></span>

## <a name="upgrade-overview"></a><span data-ttu-id="50eef-104">升級概觀</span><span class="sxs-lookup"><span data-stu-id="50eef-104">Upgrade overview</span></span>
<span data-ttu-id="50eef-105">您可以升級舊版安裝 BizTalk Accelerator for RosettaNet (BTARN) 的目前版本。</span><span class="sxs-lookup"><span data-stu-id="50eef-105">You can upgrade the previous version of the BizTalk Accelerator for RosettaNet (BTARN) installation to the current version.</span></span> <span data-ttu-id="50eef-106">升級程序包括升級 BizTalk Server，然後升級 BTARN。</span><span class="sxs-lookup"><span data-stu-id="50eef-106">The upgrade process involves upgrading BizTalk Server, and then upgrading BTARN.</span></span>  
  
 <span data-ttu-id="50eef-107">您可以從舊版的 BTARN 以升級執行 BTARN 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="50eef-107">You can upgrade from the previous version of BTARN to a by running the BTARN installation program.</span></span> <span data-ttu-id="50eef-108">安裝程式會將 BTRAN 組態資訊移轉到最新版本。</span><span class="sxs-lookup"><span data-stu-id="50eef-108">The setup migrates the BTRAN configuration information to the current version.</span></span>  
  
 <span data-ttu-id="50eef-109">在多伺服器 BTARN 環境中，您應升級所有 BizTalk 伺服器，然後再到 BTARN。</span><span class="sxs-lookup"><span data-stu-id="50eef-109">In a multi-server BTARN environment, you should upgrade all BizTalk Servers first, and then to BTARN.</span></span> <span data-ttu-id="50eef-110">請依下列順序移轉您的伺服器：</span><span class="sxs-lookup"><span data-stu-id="50eef-110">Migrate your servers in the following order:</span></span>  
  
-   <span data-ttu-id="50eef-111">裝載 BizTalk 群組的伺服器</span><span class="sxs-lookup"><span data-stu-id="50eef-111">The server hosting the BizTalk Group</span></span>  
  
-   <span data-ttu-id="50eef-112">每個處理節點</span><span class="sxs-lookup"><span data-stu-id="50eef-112">Each processing node</span></span>  
  
-   <span data-ttu-id="50eef-113">BAM 入口網站伺服器</span><span class="sxs-lookup"><span data-stu-id="50eef-113">The BAM portal server</span></span>  
  
 <span data-ttu-id="50eef-114">BTARN 中升級程序，請確定您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="50eef-114">In the BTARN upgrade process, ensure you do the following:</span></span>  
  
-   <span data-ttu-id="50eef-115">檢查 SQL Server (MSSQLSERVER) 服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="50eef-115">Check if the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="50eef-116">請勿執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="50eef-116">Do not run a silent installation.</span></span>  
  
## <a name="upgrade-steps"></a><span data-ttu-id="50eef-117">升級步驟</span><span class="sxs-lookup"><span data-stu-id="50eef-117">Upgrade steps</span></span>  
  
1.  <span data-ttu-id="50eef-118">升級 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="50eef-118">Upgrade BizTalk Server.</span></span> <span data-ttu-id="50eef-119">請參閱[BizTalk Server 新安裝、 設定及升級](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="50eef-119">See [BizTalk Server What's New, Installation, Configuration, and Upgrade](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
  
2.  <span data-ttu-id="50eef-120">備份 BTARN 資料庫和 BTARN 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="50eef-120">Back up the BTARN database and BTARN message schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50eef-121">您應該備份基於安全理由 BTARN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="50eef-121">You should back up the BTARN database for safety reasons.</span></span> <span data-ttu-id="50eef-122">安裝程式會將 BTRAN 資料庫移轉到較新版本。</span><span class="sxs-lookup"><span data-stu-id="50eef-122">The installation program migrates the BTRAN database to the newer version.</span></span>  
  
3.  <span data-ttu-id="50eef-123">備份之下任何檔案*< 磁碟機\>*: \Program Files\\Microsoft BizTalk Accelerator for RosettaNet 資料夾，您所做的變更，例如 SDK 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="50eef-123">Back up any files under the *<drive\>*:\Program Files\\Microsoft BizTalk Accelerator for RosettaNet folder that you have made changes to, for example, files in the SDK.</span></span>  
  
4.  <span data-ttu-id="50eef-124">解除部署會參考所列之一或多個舊版 BTARN 組件的任何專案或組件。</span><span class="sxs-lookup"><span data-stu-id="50eef-124">Undeploy any projects or assemblies that have references to one or more of the previous versions of BTARN assemblies.</span></span>  
  
5.  <span data-ttu-id="50eef-125">在 Visual Studio 中，您必須手動解除部署所有的 BTARN 組件，以下列順序：</span><span class="sxs-lookup"><span data-stu-id="50eef-125">In Visual Studio, manually undeploy all BTARN assemblies, in the following order:</span></span>  
  
    -   <span data-ttu-id="50eef-126">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="50eef-126">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="50eef-127">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="50eef-127">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="50eef-128">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="50eef-128">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="50eef-129">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="50eef-129">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="50eef-130">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="50eef-130">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="50eef-131">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="50eef-131">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="50eef-132">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="50eef-132">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="50eef-133">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="50eef-133">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="50eef-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="50eef-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="50eef-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="50eef-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="50eef-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="50eef-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
6.  <span data-ttu-id="50eef-137">執行 BTARN 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="50eef-137">Run the BTARN installation.</span></span> <span data-ttu-id="50eef-138">請參閱[安裝及設定 RosettaNet 加速器](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="50eef-138">See [Install and configure the RosettaNet accelerator](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>
  
7.  <span data-ttu-id="50eef-139">使用**BTSTask.exe**手動重新部署 BTARN 組件，以下列順序的 (\Program Files\Microsoft BizTalk Server):</span><span class="sxs-lookup"><span data-stu-id="50eef-139">Use **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) to manually redeploy the BTARN assemblies in the following order:</span></span>  
  
    -   <span data-ttu-id="50eef-140">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="50eef-140">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="50eef-141">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="50eef-141">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="50eef-142">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="50eef-142">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="50eef-143">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="50eef-143">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="50eef-144">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="50eef-144">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="50eef-145">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="50eef-145">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="50eef-146">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="50eef-146">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="50eef-147">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="50eef-147">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="50eef-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="50eef-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="50eef-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="50eef-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="50eef-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="50eef-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50eef-151">如需有關**BTSTask.exe**，請參閱 BizTalk Server 說明中的 < BTSTask 命令列參考 > 主題。</span><span class="sxs-lookup"><span data-stu-id="50eef-151">For more information about **BTSTask.exe**, see the "BTSTask Command-line Reference" topic in BizTalk Server Help.</span></span>  
  
8.  <span data-ttu-id="50eef-152">重建任何專案或組件的參考一或多個 [BTARN 組件。</span><span class="sxs-lookup"><span data-stu-id="50eef-152">Rebuild any projects or assemblies that have a reference to one or more of the [BTARN assemblies.</span></span> <span data-ttu-id="50eef-153">使用**BTSTask.exe**手動重新部署這些專案。</span><span class="sxs-lookup"><span data-stu-id="50eef-153">Use **BTSTask.exe** to manually redeploy these projects.</span></span>  
  
9. <span data-ttu-id="50eef-154">請將下列項目之 IIS 中的虛擬資料夾從 ASP.NET 2.0 升級到 ASP.NET 4.0：</span><span class="sxs-lookup"><span data-stu-id="50eef-154">Upgrade the virtual folders in IIS from ASP.NET 2.0 to ASP.NET 4.0 for the following:</span></span>  
  
    -   <span data-ttu-id="50eef-155">BTARNApp</span><span class="sxs-lookup"><span data-stu-id="50eef-155">BTARNApp</span></span>  
  
    -   <span data-ttu-id="50eef-156">BTARNHttpReceive</span><span class="sxs-lookup"><span data-stu-id="50eef-156">BTARNHttpReceive</span></span>  
  
10. <span data-ttu-id="50eef-157">重新啟動電腦，以套用所有修改。</span><span class="sxs-lookup"><span data-stu-id="50eef-157">Restart the computer to apply any modifications done.</span></span>  
  
