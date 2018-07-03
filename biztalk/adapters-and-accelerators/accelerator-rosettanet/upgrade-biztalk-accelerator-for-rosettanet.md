---
title: 升級 BizTalk Server 中的 RosettaNet Accelerator (BTARN) |Microsoft Docs 」
description: 遵循升級步驟來更新至 BizTalk Server 中的目前版本的 BTARN
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
ms.author: mandia
ms.openlocfilehash: 80e813ced767cdd56910027b655060e1db9f91fe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011297"
---
# <a name="upgrade-the-rosettanet-accelerator"></a><span data-ttu-id="f6caf-103">升級 RosettaNet 加速器</span><span class="sxs-lookup"><span data-stu-id="f6caf-103">Upgrade the RosettaNet accelerator</span></span>

## <a name="upgrade-overview"></a><span data-ttu-id="f6caf-104">升級概觀</span><span class="sxs-lookup"><span data-stu-id="f6caf-104">Upgrade overview</span></span>
<span data-ttu-id="f6caf-105">您可以升級舊版的 BizTalk Accelerator for RosettaNet (BTARN) 安裝到目前的版本。</span><span class="sxs-lookup"><span data-stu-id="f6caf-105">You can upgrade the previous version of the BizTalk Accelerator for RosettaNet (BTARN) installation to the current version.</span></span> <span data-ttu-id="f6caf-106">升級程序包括升級 BizTalk Server，然後升級 BTARN。</span><span class="sxs-lookup"><span data-stu-id="f6caf-106">The upgrade process involves upgrading BizTalk Server, and then upgrading BTARN.</span></span>  
  
 <span data-ttu-id="f6caf-107">您可以從舊版的 BTARN 以升級執行 BTARN 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f6caf-107">You can upgrade from the previous version of BTARN to a by running the BTARN installation program.</span></span> <span data-ttu-id="f6caf-108">安裝程式會將 BTRAN 組態資訊移轉到最新版本。</span><span class="sxs-lookup"><span data-stu-id="f6caf-108">The setup migrates the BTRAN configuration information to the current version.</span></span>  
  
 <span data-ttu-id="f6caf-109">在多伺服器 BTARN 環境中，您應升級所有的 BizTalk Server，然後再到 BTARN。</span><span class="sxs-lookup"><span data-stu-id="f6caf-109">In a multi-server BTARN environment, you should upgrade all BizTalk Servers first, and then to BTARN.</span></span> <span data-ttu-id="f6caf-110">請依下列順序移轉您的伺服器：</span><span class="sxs-lookup"><span data-stu-id="f6caf-110">Migrate your servers in the following order:</span></span>  
  
- <span data-ttu-id="f6caf-111">裝載 BizTalk 群組的伺服器</span><span class="sxs-lookup"><span data-stu-id="f6caf-111">The server hosting the BizTalk Group</span></span>  
  
- <span data-ttu-id="f6caf-112">每個處理節點</span><span class="sxs-lookup"><span data-stu-id="f6caf-112">Each processing node</span></span>  
  
- <span data-ttu-id="f6caf-113">BAM 入口網站伺服器</span><span class="sxs-lookup"><span data-stu-id="f6caf-113">The BAM portal server</span></span>  
  
  <span data-ttu-id="f6caf-114">BTARN 中升級程序，請確定您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f6caf-114">In the BTARN upgrade process, ensure you do the following:</span></span>  
  
- <span data-ttu-id="f6caf-115">檢查 SQL Server (MSSQLSERVER) 服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="f6caf-115">Check if the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
- <span data-ttu-id="f6caf-116">請勿執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="f6caf-116">Do not run a silent installation.</span></span>  
  
## <a name="upgrade-steps"></a><span data-ttu-id="f6caf-117">升級步驟</span><span class="sxs-lookup"><span data-stu-id="f6caf-117">Upgrade steps</span></span>  
  
1.  <span data-ttu-id="f6caf-118">升級 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="f6caf-118">Upgrade BizTalk Server.</span></span> <span data-ttu-id="f6caf-119">請參閱[BizTalk Server 新功能、 安裝、 設定和升級](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="f6caf-119">See [BizTalk Server What's New, Installation, Configuration, and Upgrade](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
  
2.  <span data-ttu-id="f6caf-120">備份的 BTARN 資料庫和 BTARN 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="f6caf-120">Back up the BTARN database and BTARN message schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6caf-121">您應該備份基於安全理由的 BTARN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f6caf-121">You should back up the BTARN database for safety reasons.</span></span> <span data-ttu-id="f6caf-122">安裝程式會將 BTRAN 資料庫移轉至較新版本。</span><span class="sxs-lookup"><span data-stu-id="f6caf-122">The installation program migrates the BTRAN database to the newer version.</span></span>  
  
3.  <span data-ttu-id="f6caf-123">在任何檔案備份 *< 磁碟機\>*: \Program Files\\Microsoft BizTalk Accelerator for RosettaNet 資料夾，您所做的變更，例如，SDK 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f6caf-123">Back up any files under the *<drive\>*:\Program Files\\Microsoft BizTalk Accelerator for RosettaNet folder that you have made changes to, for example, files in the SDK.</span></span>  
  
4.  <span data-ttu-id="f6caf-124">解除部署會參考所列之一或多個舊版 BTARN 組件的任何專案或組件。</span><span class="sxs-lookup"><span data-stu-id="f6caf-124">Undeploy any projects or assemblies that have references to one or more of the previous versions of BTARN assemblies.</span></span>  
  
5.  <span data-ttu-id="f6caf-125">在 Visual Studio 中，您必須手動解除部署所有的 BTARN 組件，以下列順序：</span><span class="sxs-lookup"><span data-stu-id="f6caf-125">In Visual Studio, manually undeploy all BTARN assemblies, in the following order:</span></span>  
  
    -   <span data-ttu-id="f6caf-126">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="f6caf-126">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="f6caf-127">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="f6caf-127">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="f6caf-128">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="f6caf-128">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="f6caf-129">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="f6caf-129">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="f6caf-130">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="f6caf-130">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="f6caf-131">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="f6caf-131">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="f6caf-132">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="f6caf-132">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="f6caf-133">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="f6caf-133">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="f6caf-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="f6caf-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="f6caf-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="f6caf-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="f6caf-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="f6caf-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
6.  <span data-ttu-id="f6caf-137">執行 BTARN 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f6caf-137">Run the BTARN installation.</span></span> <span data-ttu-id="f6caf-138">請參閱[安裝和設定 RosettaNet accelerator](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="f6caf-138">See [Install and configure the RosettaNet accelerator](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>
  
7.  <span data-ttu-id="f6caf-139">使用**BTSTask.exe**手動重新部署 BTARN 組件，以下列順序的 (\Program Files\Microsoft BizTalk Server):</span><span class="sxs-lookup"><span data-stu-id="f6caf-139">Use **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) to manually redeploy the BTARN assemblies in the following order:</span></span>  
  
    -   <span data-ttu-id="f6caf-140">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="f6caf-140">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="f6caf-141">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="f6caf-141">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="f6caf-142">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="f6caf-142">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="f6caf-143">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="f6caf-143">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="f6caf-144">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="f6caf-144">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="f6caf-145">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="f6caf-145">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="f6caf-146">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="f6caf-146">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="f6caf-147">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="f6caf-147">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="f6caf-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="f6caf-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="f6caf-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="f6caf-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="f6caf-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="f6caf-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6caf-151">如需詳細資訊**BTSTask.exe**，請參閱 BizTalk Server 說明中的 < BTSTask 命令列參考 > 主題。</span><span class="sxs-lookup"><span data-stu-id="f6caf-151">For more information about **BTSTask.exe**, see the "BTSTask Command-line Reference" topic in BizTalk Server Help.</span></span>  
  
8.  <span data-ttu-id="f6caf-152">重建任何專案或有一或多個 [BTARN 組件參考組件。</span><span class="sxs-lookup"><span data-stu-id="f6caf-152">Rebuild any projects or assemblies that have a reference to one or more of the [BTARN assemblies.</span></span> <span data-ttu-id="f6caf-153">使用**BTSTask.exe**手動重新部署這些專案。</span><span class="sxs-lookup"><span data-stu-id="f6caf-153">Use **BTSTask.exe** to manually redeploy these projects.</span></span>  
  
9. <span data-ttu-id="f6caf-154">請將下列項目之 IIS 中的虛擬資料夾從 ASP.NET 2.0 升級到 ASP.NET 4.0：</span><span class="sxs-lookup"><span data-stu-id="f6caf-154">Upgrade the virtual folders in IIS from ASP.NET 2.0 to ASP.NET 4.0 for the following:</span></span>  
  
    -   <span data-ttu-id="f6caf-155">BTARNApp</span><span class="sxs-lookup"><span data-stu-id="f6caf-155">BTARNApp</span></span>  
  
    -   <span data-ttu-id="f6caf-156">BTARNHttpReceive</span><span class="sxs-lookup"><span data-stu-id="f6caf-156">BTARNHttpReceive</span></span>  
  
10. <span data-ttu-id="f6caf-157">重新啟動電腦，以套用所有修改。</span><span class="sxs-lookup"><span data-stu-id="f6caf-157">Restart the computer to apply any modifications done.</span></span>  
  
