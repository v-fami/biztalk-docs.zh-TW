---
title: "環境變數如何指示部署狀態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041e77eadb7c1b62e3441ee3b3c138203299f3a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-environment-variables-indicate-deployment-state"></a><span data-ttu-id="a93ad-102">環境變數如何指示部署狀態</span><span class="sxs-lookup"><span data-stu-id="a93ad-102">How Environment Variables Indicate Deployment State</span></span>
<span data-ttu-id="a93ad-103">前置或後置處理指令碼一旦被叫用，便會檢查環境變數 BTAD_ChangeRequestAction、BTAD_InstallMode 與 BTAD_HostClass 以判斷目前所處的部署狀態 (安裝、匯入、刪除、解除安裝、匯入回復，或者安裝回復)。</span><span class="sxs-lookup"><span data-stu-id="a93ad-103">Once invoked, a pre- or post-processing script can determine in which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode and BTAD_HostClass.</span></span>  
  
 <span data-ttu-id="a93ad-104">下表描述三個指示不同部署狀態之變數的組合。</span><span class="sxs-lookup"><span data-stu-id="a93ad-104">The following table describes the combinations of the three variables that indicate the different deployment states.</span></span>  
  
|<span data-ttu-id="a93ad-105">部署狀態</span><span class="sxs-lookup"><span data-stu-id="a93ad-105">Deployment State</span></span>|<span data-ttu-id="a93ad-106">預期值</span><span class="sxs-lookup"><span data-stu-id="a93ad-106">Expected Values</span></span>|  
|----------------------|---------------------|  
||<span data-ttu-id="a93ad-107">BTAD_ChangeRequestAction</span><span class="sxs-lookup"><span data-stu-id="a93ad-107">BTAD_ChangeRequestAction</span></span>|<span data-ttu-id="a93ad-108">BTAD_InstallMode</span><span class="sxs-lookup"><span data-stu-id="a93ad-108">BTAD_InstallMode</span></span>|<span data-ttu-id="a93ad-109">BTAD_HostClass</span><span class="sxs-lookup"><span data-stu-id="a93ad-109">BTAD_HostClass</span></span>|  
|<span data-ttu-id="a93ad-110">不使用覆寫旗標匯入</span><span class="sxs-lookup"><span data-stu-id="a93ad-110">Import without overwrite flag</span></span>|<span data-ttu-id="a93ad-111">建立</span><span class="sxs-lookup"><span data-stu-id="a93ad-111">Create</span></span>|<span data-ttu-id="a93ad-112">匯入</span><span class="sxs-lookup"><span data-stu-id="a93ad-112">Import</span></span>|<span data-ttu-id="a93ad-113">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="a93ad-113">ConfigurationDb</span></span>|  
|<span data-ttu-id="a93ad-114">使用覆寫旗標匯入</span><span class="sxs-lookup"><span data-stu-id="a93ad-114">Import with overwrite flag</span></span>|<span data-ttu-id="a93ad-115">Update</span><span class="sxs-lookup"><span data-stu-id="a93ad-115">Update</span></span>|<span data-ttu-id="a93ad-116">匯入</span><span class="sxs-lookup"><span data-stu-id="a93ad-116">Import</span></span>|<span data-ttu-id="a93ad-117">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="a93ad-117">ConfigurationDb</span></span>|  
|<span data-ttu-id="a93ad-118">Install</span><span class="sxs-lookup"><span data-stu-id="a93ad-118">Install</span></span>|<span data-ttu-id="a93ad-119">Update</span><span class="sxs-lookup"><span data-stu-id="a93ad-119">Update</span></span>|<span data-ttu-id="a93ad-120">Install</span><span class="sxs-lookup"><span data-stu-id="a93ad-120">Install</span></span>|<span data-ttu-id="a93ad-121">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="a93ad-121">BizTalkHostInstance</span></span>|  
|<span data-ttu-id="a93ad-122">Uninstall</span><span class="sxs-lookup"><span data-stu-id="a93ad-122">Uninstall</span></span>|<span data-ttu-id="a93ad-123">Delete</span><span class="sxs-lookup"><span data-stu-id="a93ad-123">Delete</span></span>|<span data-ttu-id="a93ad-124">Uninstall</span><span class="sxs-lookup"><span data-stu-id="a93ad-124">Uninstall</span></span>|<span data-ttu-id="a93ad-125">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="a93ad-125">BizTalkHostInstance</span></span>|  
|<span data-ttu-id="a93ad-126">匯入回復</span><span class="sxs-lookup"><span data-stu-id="a93ad-126">Import rollback</span></span>|<span data-ttu-id="a93ad-127">Delete</span><span class="sxs-lookup"><span data-stu-id="a93ad-127">Delete</span></span>|<span data-ttu-id="a93ad-128">匯入</span><span class="sxs-lookup"><span data-stu-id="a93ad-128">Import</span></span>|<span data-ttu-id="a93ad-129">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="a93ad-129">ConfigurationDb</span></span>|  
|<span data-ttu-id="a93ad-130">安裝回復</span><span class="sxs-lookup"><span data-stu-id="a93ad-130">Install rollback</span></span>|<span data-ttu-id="a93ad-131">Delete</span><span class="sxs-lookup"><span data-stu-id="a93ad-131">Delete</span></span>|<span data-ttu-id="a93ad-132">Install</span><span class="sxs-lookup"><span data-stu-id="a93ad-132">Install</span></span>|<span data-ttu-id="a93ad-133">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="a93ad-133">BizTalkHostInstance</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a93ad-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a93ad-134">See Also</span></span>  
 <span data-ttu-id="a93ad-135">[使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="a93ad-135">[Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span></span>  
 <span data-ttu-id="a93ad-136">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span><span class="sxs-lookup"><span data-stu-id="a93ad-136">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span></span>  
 <span data-ttu-id="a93ad-137">[BTAD_InstallMode](../core/btad-installmode.md) </span><span class="sxs-lookup"><span data-stu-id="a93ad-137">[BTAD_InstallMode](../core/btad-installmode.md) </span></span>  
 [<span data-ttu-id="a93ad-138">BTAD_HostClass</span><span class="sxs-lookup"><span data-stu-id="a93ad-138">BTAD_HostClass</span></span>](../core/btad-hostclass.md)