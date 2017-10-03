---
title: "安裝 「 解析程式服務 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b06c7383dee805612a3f599148f1d631891ace79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-resolver-service-sample"></a><span data-ttu-id="a86c7-102">安裝 「 解析程式服務 」 範例</span><span class="sxs-lookup"><span data-stu-id="a86c7-102">Installing the Resolver Service Sample</span></span>
<span data-ttu-id="a86c7-103">本章節描述解析程式服務範例的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="a86c7-103">This section describes the process for installing the Resolver Service sample.</span></span> <span data-ttu-id="a86c7-104">解析程式服務依存於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心方案。</span><span class="sxs-lookup"><span data-stu-id="a86c7-104">The Resolver Service depends on the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core solution.</span></span> <span data-ttu-id="a86c7-105">安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心自動複製並安裝到正確的位置，此範例所需的核心組件。</span><span class="sxs-lookup"><span data-stu-id="a86c7-105">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the core assemblies required by this sample to the correct locations.</span></span>  
  
 <span data-ttu-id="a86c7-106">**若要從方案專案安裝解析程式服務範例**</span><span class="sxs-lookup"><span data-stu-id="a86c7-106">**To install the Resolver Service sample from the solution project**</span></span>  
  
1.  <span data-ttu-id="a86c7-107">在 Windows 檔案總管 中，開啟 \Source\Samples\ResolverService\Install\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a86c7-107">In Windows Explorer, open the \Source\Samples\ResolverService\Install\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="a86c7-108">按兩下 Setup_bin.cmd 檔案。</span><span class="sxs-lookup"><span data-stu-id="a86c7-108">Double-click the Setup_bin.cmd file.</span></span>  
  
3.  <span data-ttu-id="a86c7-109">若要確認成功安裝範例的一部分，或如果您執行應用程式時遇到問題，您可以使用下表中所提供的清單來檢查是否有必要的組件和其他成品。</span><span class="sxs-lookup"><span data-stu-id="a86c7-109">To confirm successful installation of the sample, or if you are encountering issues when you run applications, you can use the list provided in the following table to check for the presence of the required assemblies and other artifacts.</span></span>  
  
|<span data-ttu-id="a86c7-110">位置</span><span class="sxs-lookup"><span data-stu-id="a86c7-110">Location</span></span>|<span data-ttu-id="a86c7-111">類別目錄</span><span class="sxs-lookup"><span data-stu-id="a86c7-111">Category</span></span>|<span data-ttu-id="a86c7-112">名稱和版本的元件</span><span class="sxs-lookup"><span data-stu-id="a86c7-112">Name and version of the component</span></span>|  
|--------------|--------------|---------------------------------------|  
|<span data-ttu-id="a86c7-113">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-113">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-114">協調流程</span><span class="sxs-lookup"><span data-stu-id="a86c7-114">Orchestrations</span></span>|<span data-ttu-id="a86c7-115">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-115">(none)</span></span>|  
|<span data-ttu-id="a86c7-116">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-116">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-117">傳送埠</span><span class="sxs-lookup"><span data-stu-id="a86c7-117">Send Ports</span></span>|<span data-ttu-id="a86c7-118">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-118">(none)</span></span>|  
|<span data-ttu-id="a86c7-119">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-119">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-120">接收埠</span><span class="sxs-lookup"><span data-stu-id="a86c7-120">Receive Ports</span></span>|<span data-ttu-id="a86c7-121">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-121">(none)</span></span>|  
|<span data-ttu-id="a86c7-122">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-122">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-123">接收位置</span><span class="sxs-lookup"><span data-stu-id="a86c7-123">Receive Locations</span></span>|<span data-ttu-id="a86c7-124">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-124">(none)</span></span>|  
|<span data-ttu-id="a86c7-125">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-125">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-126">結構描述</span><span class="sxs-lookup"><span data-stu-id="a86c7-126">Schemas</span></span>|<span data-ttu-id="a86c7-127">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-127">(none)</span></span>|  
|<span data-ttu-id="a86c7-128">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-128">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-129">管線</span><span class="sxs-lookup"><span data-stu-id="a86c7-129">Pipelines</span></span>|<span data-ttu-id="a86c7-130">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-130">(none)</span></span>|  
|<span data-ttu-id="a86c7-131">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-131">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-132">資源</span><span class="sxs-lookup"><span data-stu-id="a86c7-132">Resources</span></span>|<span data-ttu-id="a86c7-133">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-133">(none)</span></span>|  
|<span data-ttu-id="a86c7-134">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-134">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-135">原則</span><span class="sxs-lookup"><span data-stu-id="a86c7-135">Policies</span></span>|<span data-ttu-id="a86c7-136">ResolveEndpoint</span><span class="sxs-lookup"><span data-stu-id="a86c7-136">ResolveEndpoint</span></span>|  
|||<span data-ttu-id="a86c7-137">ResolveMap</span><span class="sxs-lookup"><span data-stu-id="a86c7-137">ResolveMap</span></span>|  
|<span data-ttu-id="a86c7-138">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="a86c7-138">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="a86c7-139">地圖</span><span class="sxs-lookup"><span data-stu-id="a86c7-139">Maps</span></span>|<span data-ttu-id="a86c7-140">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-140">(none)</span></span>|  
|<span data-ttu-id="a86c7-141">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a86c7-141">Global assembly cache</span></span>|<span data-ttu-id="a86c7-142">組件</span><span class="sxs-lookup"><span data-stu-id="a86c7-142">Assemblies</span></span>|<span data-ttu-id="a86c7-143">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-143">(none)</span></span>|  
|<span data-ttu-id="a86c7-144">%Program Files %\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline 元件</span><span class="sxs-lookup"><span data-stu-id="a86c7-144">%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline Components</span></span>|<span data-ttu-id="a86c7-145">管線元件</span><span class="sxs-lookup"><span data-stu-id="a86c7-145">Pipeline components</span></span>|<span data-ttu-id="a86c7-146">(無)</span><span class="sxs-lookup"><span data-stu-id="a86c7-146">(none)</span></span>|