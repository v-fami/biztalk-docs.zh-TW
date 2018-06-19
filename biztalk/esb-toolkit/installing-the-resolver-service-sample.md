---
title: 安裝 「 解析程式服務 」 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bd438725b53362cda1b041af697283e68d77ba7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009575"
---
# <a name="installing-the-resolver-service-sample"></a><span data-ttu-id="f111a-102">安裝 「 解析程式服務 」 範例</span><span class="sxs-lookup"><span data-stu-id="f111a-102">Installing the Resolver Service Sample</span></span>
<span data-ttu-id="f111a-103">本章節描述解析程式服務範例的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="f111a-103">This section describes the process for installing the Resolver Service sample.</span></span> <span data-ttu-id="f111a-104">解析程式服務依存於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心方案。</span><span class="sxs-lookup"><span data-stu-id="f111a-104">The Resolver Service depends on the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core solution.</span></span> <span data-ttu-id="f111a-105">安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心自動複製並安裝到正確的位置，此範例所需的核心組件。</span><span class="sxs-lookup"><span data-stu-id="f111a-105">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the core assemblies required by this sample to the correct locations.</span></span>  
  
 <span data-ttu-id="f111a-106">**若要從方案專案安裝解析程式服務範例**</span><span class="sxs-lookup"><span data-stu-id="f111a-106">**To install the Resolver Service sample from the solution project**</span></span>  
  
1.  <span data-ttu-id="f111a-107">在 Windows 檔案總管 中，開啟 \Source\Samples\ResolverService\Install\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f111a-107">In Windows Explorer, open the \Source\Samples\ResolverService\Install\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="f111a-108">按兩下 Setup_bin.cmd 檔案。</span><span class="sxs-lookup"><span data-stu-id="f111a-108">Double-click the Setup_bin.cmd file.</span></span>  
  
3.  <span data-ttu-id="f111a-109">若要確認成功安裝範例的一部分，或如果您執行應用程式時遇到問題，您可以使用下表中所提供的清單來檢查是否有必要的組件和其他成品。</span><span class="sxs-lookup"><span data-stu-id="f111a-109">To confirm successful installation of the sample, or if you are encountering issues when you run applications, you can use the list provided in the following table to check for the presence of the required assemblies and other artifacts.</span></span>  
  
|<span data-ttu-id="f111a-110">位置</span><span class="sxs-lookup"><span data-stu-id="f111a-110">Location</span></span>|<span data-ttu-id="f111a-111">類別目錄</span><span class="sxs-lookup"><span data-stu-id="f111a-111">Category</span></span>|<span data-ttu-id="f111a-112">名稱和版本的元件</span><span class="sxs-lookup"><span data-stu-id="f111a-112">Name and version of the component</span></span>|  
|--------------|--------------|---------------------------------------|  
|<span data-ttu-id="f111a-113">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-113">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-114">協調流程</span><span class="sxs-lookup"><span data-stu-id="f111a-114">Orchestrations</span></span>|<span data-ttu-id="f111a-115">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-115">(none)</span></span>|  
|<span data-ttu-id="f111a-116">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-116">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-117">傳送埠</span><span class="sxs-lookup"><span data-stu-id="f111a-117">Send Ports</span></span>|<span data-ttu-id="f111a-118">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-118">(none)</span></span>|  
|<span data-ttu-id="f111a-119">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-119">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-120">接收埠</span><span class="sxs-lookup"><span data-stu-id="f111a-120">Receive Ports</span></span>|<span data-ttu-id="f111a-121">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-121">(none)</span></span>|  
|<span data-ttu-id="f111a-122">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-122">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-123">接收位置</span><span class="sxs-lookup"><span data-stu-id="f111a-123">Receive Locations</span></span>|<span data-ttu-id="f111a-124">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-124">(none)</span></span>|  
|<span data-ttu-id="f111a-125">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-125">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-126">結構描述</span><span class="sxs-lookup"><span data-stu-id="f111a-126">Schemas</span></span>|<span data-ttu-id="f111a-127">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-127">(none)</span></span>|  
|<span data-ttu-id="f111a-128">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-128">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-129">管線</span><span class="sxs-lookup"><span data-stu-id="f111a-129">Pipelines</span></span>|<span data-ttu-id="f111a-130">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-130">(none)</span></span>|  
|<span data-ttu-id="f111a-131">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-131">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-132">資源</span><span class="sxs-lookup"><span data-stu-id="f111a-132">Resources</span></span>|<span data-ttu-id="f111a-133">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-133">(none)</span></span>|  
|<span data-ttu-id="f111a-134">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-134">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-135">原則</span><span class="sxs-lookup"><span data-stu-id="f111a-135">Policies</span></span>|<span data-ttu-id="f111a-136">ResolveEndpoint</span><span class="sxs-lookup"><span data-stu-id="f111a-136">ResolveEndpoint</span></span>|  
|||<span data-ttu-id="f111a-137">ResolveMap</span><span class="sxs-lookup"><span data-stu-id="f111a-137">ResolveMap</span></span>|  
|<span data-ttu-id="f111a-138">BizTalk 應用程式 GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="f111a-138">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="f111a-139">地圖</span><span class="sxs-lookup"><span data-stu-id="f111a-139">Maps</span></span>|<span data-ttu-id="f111a-140">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-140">(none)</span></span>|  
|<span data-ttu-id="f111a-141">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="f111a-141">Global assembly cache</span></span>|<span data-ttu-id="f111a-142">組件</span><span class="sxs-lookup"><span data-stu-id="f111a-142">Assemblies</span></span>|<span data-ttu-id="f111a-143">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-143">(none)</span></span>|  
|<span data-ttu-id="f111a-144">%Program Files %\\BizTalk Server\Pipeline 元件</span><span class="sxs-lookup"><span data-stu-id="f111a-144">%Program Files%\\BizTalk Server\Pipeline Components</span></span>|<span data-ttu-id="f111a-145">管線元件</span><span class="sxs-lookup"><span data-stu-id="f111a-145">Pipeline components</span></span>|<span data-ttu-id="f111a-146">(無)</span><span class="sxs-lookup"><span data-stu-id="f111a-146">(none)</span></span>|