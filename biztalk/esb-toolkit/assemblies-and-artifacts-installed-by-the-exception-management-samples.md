---
title: "組件和成品安裝例外狀況管理範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af580992-73d4-4b16-a1cc-fa819b441fca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65bcb2681cceb450995b18b7dc00d3d8f5a44d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assemblies-and-artifacts-installed-by-the-exception-management-samples"></a><span data-ttu-id="03a96-102">組件和成品安裝例外狀況管理範例</span><span class="sxs-lookup"><span data-stu-id="03a96-102">Assemblies and Artifacts Installed by the Exception Management Samples</span></span>
<span data-ttu-id="03a96-103">下表列出的組件和其他成品 ESB 例外狀況管理範例的安裝。</span><span class="sxs-lookup"><span data-stu-id="03a96-103">The following table lists the assemblies and other artifacts installed for the ESB Exception Management sample.</span></span>  
  
|<span data-ttu-id="03a96-104">位置</span><span class="sxs-lookup"><span data-stu-id="03a96-104">Location</span></span>|<span data-ttu-id="03a96-105">類別目錄</span><span class="sxs-lookup"><span data-stu-id="03a96-105">Category</span></span>|<span data-ttu-id="03a96-106">名稱和版本的元件</span><span class="sxs-lookup"><span data-stu-id="03a96-106">Name and version of the component</span></span>|  
|--------------|--------------|---------------------------------------|  
|<span data-ttu-id="03a96-107">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-107">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-108">協調流程</span><span class="sxs-lookup"><span data-stu-id="03a96-108">Orchestrations</span></span>|<span data-ttu-id="03a96-109">GlobalBank.ESB.ExceptionHandling.Processes.EAIProcess</span><span class="sxs-lookup"><span data-stu-id="03a96-109">GlobalBank.ESB.ExceptionHandling.Processes.EAIProcess</span></span>|  
|||<span data-ttu-id="03a96-110">GlobalBank.ESB.ExceptionHandling.Handlers.EAIGenericHandler</span><span class="sxs-lookup"><span data-stu-id="03a96-110">GlobalBank.ESB.ExceptionHandling.Handlers.EAIGenericHandler</span></span>|  
|||<span data-ttu-id="03a96-111">GlobalBank.ESB.ExceptionHandling.Handlers.EAIProcessHandler</span><span class="sxs-lookup"><span data-stu-id="03a96-111">GlobalBank.ESB.ExceptionHandling.Handlers.EAIProcessHandler</span></span>|  
|<span data-ttu-id="03a96-112">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-112">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-113">傳送埠</span><span class="sxs-lookup"><span data-stu-id="03a96-113">Send Ports</span></span>|<span data-ttu-id="03a96-114">EAIProcessHandler.RepairSubmit</span><span class="sxs-lookup"><span data-stu-id="03a96-114">EAIProcessHandler.RepairSubmit</span></span>|  
|||<span data-ttu-id="03a96-115">EAIGenericHandler.PostTmpMsg</span><span class="sxs-lookup"><span data-stu-id="03a96-115">EAIGenericHandler.PostTmpMsg</span></span>|  
|||<span data-ttu-id="03a96-116">EAIProcess.PostApproval</span><span class="sxs-lookup"><span data-stu-id="03a96-116">EAIProcess.PostApproval</span></span>|  
|||<span data-ttu-id="03a96-117">EAIProcessHandler.PostDecline</span><span class="sxs-lookup"><span data-stu-id="03a96-117">EAIProcessHandler.PostDecline</span></span>|  
|||<span data-ttu-id="03a96-118">所有。Exceptions_FILE （參考 GlobalFaultProcessor 管線）</span><span class="sxs-lookup"><span data-stu-id="03a96-118">ALL.Exceptions_FILE (references the GlobalFaultProcessor pipeline)</span></span>|  
|<span data-ttu-id="03a96-119">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-119">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-120">接收埠</span><span class="sxs-lookup"><span data-stu-id="03a96-120">Receive Ports</span></span>|<span data-ttu-id="03a96-121">EAIProcess.RequestPort</span><span class="sxs-lookup"><span data-stu-id="03a96-121">EAIProcess.RequestPort</span></span>|  
|<span data-ttu-id="03a96-122">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-122">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-123">接收位置</span><span class="sxs-lookup"><span data-stu-id="03a96-123">Receive Locations</span></span>|<span data-ttu-id="03a96-124">EAIProcess.RequestPort_FILE</span><span class="sxs-lookup"><span data-stu-id="03a96-124">EAIProcess.RequestPort_FILE</span></span>|  
|||<span data-ttu-id="03a96-125">EAIProcess.ReSubmit_HTTP</span><span class="sxs-lookup"><span data-stu-id="03a96-125">EAIProcess.ReSubmit_HTTP</span></span>|  
|<span data-ttu-id="03a96-126">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-126">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-127">結構描述</span><span class="sxs-lookup"><span data-stu-id="03a96-127">Schemas</span></span>|<span data-ttu-id="03a96-128">GlobalBank.ESB.ExceptionHandling.Schemas.System_Properties 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-128">GlobalBank.ESB.ExceptionHandling.Schemas.System_Properties Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-129">GlobalBank.ESB.ExceptionHandling.Schemas.Request 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-129">GlobalBank.ESB.ExceptionHandling.Schemas.Request Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-130">GlobalBank.ESB.ExceptionHandling.Schemas.RequestDenied 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-130">GlobalBank.ESB.ExceptionHandling.Schemas.RequestDenied Version 2.0.0.0</span></span>|  
|<span data-ttu-id="03a96-131">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-131">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-132">管線</span><span class="sxs-lookup"><span data-stu-id="03a96-132">Pipelines</span></span>|<span data-ttu-id="03a96-133">GlobalBank.ESB.ExceptionHandling.Pipelines.GlobalFaultProcessor 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-133">GlobalBank.ESB.ExceptionHandling.Pipelines.GlobalFaultProcessor Version 2.0.0.0</span></span>|  
|<span data-ttu-id="03a96-134">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-134">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-135">資源</span><span class="sxs-lookup"><span data-stu-id="03a96-135">Resources</span></span>|<span data-ttu-id="03a96-136">GlobalBank.ESB.ExceptionHandling.Handlers 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-136">GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-137">GlobalBank.ESB.ExceptionHandling.Processes 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-137">GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-138">GlobalBank.ESB.ExceptionHandling.Schemas 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-138">GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-139">GlobalBank.ESB.ExceptionHandling.Pipelines 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-139">GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0</span></span>|  
|<span data-ttu-id="03a96-140">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-140">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-141">原則</span><span class="sxs-lookup"><span data-stu-id="03a96-141">Policies</span></span>||  
|<span data-ttu-id="03a96-142">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="03a96-142">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="03a96-143">地圖</span><span class="sxs-lookup"><span data-stu-id="03a96-143">Maps</span></span>|<span data-ttu-id="03a96-144">GlobalBank.ESB.ExceptionHandling.Schemas.MapToReqDenied 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-144">GlobalBank.ESB.ExceptionHandling.Schemas.MapToReqDenied Version 2.0.0.0</span></span>|  
|<span data-ttu-id="03a96-145">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="03a96-145">Global assembly cache</span></span>|<span data-ttu-id="03a96-146">組件</span><span class="sxs-lookup"><span data-stu-id="03a96-146">Assemblies</span></span>|<span data-ttu-id="03a96-147">GlobalBank.ESB.ExceptionHandling.Handlers 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-147">GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-148">GlobalBank.ESB.ExceptionHandling.Processes 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-148">GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-149">GlobalBank.ESB.ExceptionHandling.Schemas 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-149">GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0</span></span>|  
|||<span data-ttu-id="03a96-150">GlobalBank.ESB.ExceptionHandling.Pipelines 2.0.0.0 版</span><span class="sxs-lookup"><span data-stu-id="03a96-150">GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0</span></span>|  
|<span data-ttu-id="03a96-151">%Program Files %\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline 元件</span><span class="sxs-lookup"><span data-stu-id="03a96-151">%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline Components</span></span>|<span data-ttu-id="03a96-152">管線元件</span><span class="sxs-lookup"><span data-stu-id="03a96-152">Pipeline components</span></span>||