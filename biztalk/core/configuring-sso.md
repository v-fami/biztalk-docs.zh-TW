---
title: "設定 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, command line utilities
- configuring, SSO
- SSO, interfaces
- SSOConfig [SSO]
- SSO, configuring
- SSOClient [SSO]
- SSO, tools
- SSOManage [SSO]
ms.assetid: 6f755735-9b48-4771-beec-ced844f3d532
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d729633717d709a83c10e9b50c55791029902010
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-sso"></a><span data-ttu-id="535b0-102">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="535b0-102">Configuring SSO</span></span>
<span data-ttu-id="535b0-103">您可以使用命令列公用程式、UI 工具、COM 或 Microsoft .NET 介面，以設定「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="535b0-103">You can configure Enterprise Single Sign-On by using command line utilities, UI tools, or COM or Microsoft .NET interfaces.</span></span>  
  
## <a name="sso-command-line-utilities"></a><span data-ttu-id="535b0-104">SSO 命令列公用程式</span><span class="sxs-lookup"><span data-stu-id="535b0-104">SSO command line utilities</span></span>  
 <span data-ttu-id="535b0-105">您可使用 3 種不同的命令列公用程式，以執行「企業單一登入」工作：</span><span class="sxs-lookup"><span data-stu-id="535b0-105">You use three different command line utilities to perform Enterprise Single Sign-On tasks:</span></span>  
  
 <span data-ttu-id="535b0-106">**SSOConfig。**</span><span class="sxs-lookup"><span data-stu-id="535b0-106">**SSOConfig.**</span></span> <span data-ttu-id="535b0-107">可讓 SSO 系統管理員設定 SSO 資料庫和管理主要密碼。</span><span class="sxs-lookup"><span data-stu-id="535b0-107">Enables an SSO administrator to configure the SSO database and to manage the master secret.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="535b0-108">「組態精靈」會建立 SSO 資料庫和主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="535b0-108">The Configuration Wizard creates the SSO database and the master secret server.</span></span>  
  
 <span data-ttu-id="535b0-109">**SSOManage。**</span><span class="sxs-lookup"><span data-stu-id="535b0-109">**SSOManage.**</span></span> <span data-ttu-id="535b0-110">可讓 SSO 系統管理員、SSO 分支機構系統管理員及應用程式系統管理員，更新 SSO 資料庫以新增、刪除和管理應用程式、管理使用者對應，以及設定分支機構應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="535b0-110">Enables SSO administrators, SSO affiliate administrators, and application administrators to update the SSO database to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users.</span></span> <span data-ttu-id="535b0-111">部分作業只能由 SSO 系統管理員執行，或只能由 SSO 系統管理員和 SSO 分支機構系統管理員執行。</span><span class="sxs-lookup"><span data-stu-id="535b0-111">Some operations can be performed only by the SSO administrators, or, only by the SSO administrators and SSO affiliate administrators.</span></span> <span data-ttu-id="535b0-112">「應用程式系統管理員」執行的所有作業，也可由「SSO 系統管理員」或「SSO 分支機構系統管理員」執行。</span><span class="sxs-lookup"><span data-stu-id="535b0-112">All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and the SSO Affiliate Administrators.</span></span>  
  
 <span data-ttu-id="535b0-113">**SSOClient。**</span><span class="sxs-lookup"><span data-stu-id="535b0-113">**SSOClient.**</span></span> <span data-ttu-id="535b0-114">可讓「單一登入」使用者管理自己的使用者對應和設定其認證。</span><span class="sxs-lookup"><span data-stu-id="535b0-114">Enables Single Sign-On users to manage their own user mappings and set their credentials.</span></span>  
  
 <span data-ttu-id="535b0-115">如需有關 SSO 帳戶的詳細資訊，請參閱[SSO 使用者群組](../core/sso-user-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="535b0-115">For more information about the SSO accounts, see [SSO User Groups](../core/sso-user-groups.md).</span></span>  
  
## <a name="sso-ui-tools"></a><span data-ttu-id="535b0-116">SSO UI 工具</span><span class="sxs-lookup"><span data-stu-id="535b0-116">SSO UI tools</span></span>  
 <span data-ttu-id="535b0-117">**企業 SSO MMC 嵌入式管理單元。**</span><span class="sxs-lookup"><span data-stu-id="535b0-117">**Enterprise SSO MMC Snap-in.**</span></span> <span data-ttu-id="535b0-118">可讓 SSO 系統管理員、SSO 分支機構系統管理員及應用程式系統管理員，更新 SSO 資料庫以新增、刪除和管理應用程式、管理使用者對應，以及設定分支機構應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="535b0-118">Enables SSO Administrators, SSO Affiliate Administrators, and Application Administrators to update the SSO database, to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users.</span></span> <span data-ttu-id="535b0-119">部分作業只能由 SSO 系統管理員執行，或只能由 SSO 系統管理員和 SSO 分支機構系統管理員執行。</span><span class="sxs-lookup"><span data-stu-id="535b0-119">Some operations can be performed only by the SSO administrators, or only by the SSO administrators and SSO affiliate administrators.</span></span> <span data-ttu-id="535b0-120">「應用程式系統管理員」執行的所有作業，也可由「SSO 系統管理員」或「SSO 分支機構系統管理員」執行。</span><span class="sxs-lookup"><span data-stu-id="535b0-120">All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and SSO Affiliate Administrators.</span></span>  
  
 <span data-ttu-id="535b0-121">**SSO 用戶端公用程式。**</span><span class="sxs-lookup"><span data-stu-id="535b0-121">**SSO Client Utility.**</span></span> <span data-ttu-id="535b0-122">可讓一般使用者使用 UI 工具，管理自己的對應和設定其認證。</span><span class="sxs-lookup"><span data-stu-id="535b0-122">Enables end users to manage their own mappings and set their credentials using the UI tool.</span></span>  
  
## <a name="sso-com-and-net-interfaces"></a><span data-ttu-id="535b0-123">SSO COM 和 .NET 介面</span><span class="sxs-lookup"><span data-stu-id="535b0-123">SSO COM and .NET interfaces</span></span>  
 <span data-ttu-id="535b0-124">「企業單一登入」提供 COM 和 .NET 程式設計介面，讓您可以建立自訂元件，以及建立指令碼以協助 SSO 系統的管理。</span><span class="sxs-lookup"><span data-stu-id="535b0-124">Enterprise Single Sign-On provides COM and .NET programmatic interfaces that enable you to create custom components, and to create scripts to facilitate the administration of the SSO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535b0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="535b0-125">See Also</span></span>  
 [<span data-ttu-id="535b0-126">SSO 元件</span><span class="sxs-lookup"><span data-stu-id="535b0-126">SSO Components</span></span>](../core/sso-components.md)