---
title: 可能未安裝 Windows 元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc78ac0a-ee21-4633-afb3-1357efd29903
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d61ded5b2ddb077ff0851c20d673fad4f9de9d26
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975503"
---
# <a name="windows-components-may-not-be-installed"></a><span data-ttu-id="3111b-102">Windows 元件可能無法安裝</span><span class="sxs-lookup"><span data-stu-id="3111b-102">Windows components may not be installed</span></span>
## <a name="details"></a><span data-ttu-id="3111b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3111b-103">Details</span></span>  

|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="3111b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3111b-104">Product Name</span></span>   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                           |
| <span data-ttu-id="3111b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3111b-105">Product Version</span></span> |                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                       |
|    <span data-ttu-id="3111b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3111b-106">Event ID</span></span>     |                                                                   <span data-ttu-id="3111b-107">0</span><span class="sxs-lookup"><span data-stu-id="3111b-107">0</span></span>                                                                    |
|  <span data-ttu-id="3111b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3111b-108">Event Source</span></span>   |                                                                   <span data-ttu-id="3111b-109">0</span><span class="sxs-lookup"><span data-stu-id="3111b-109">0</span></span>                                                                    |
|    <span data-ttu-id="3111b-110">元件</span><span class="sxs-lookup"><span data-stu-id="3111b-110">Component</span></span>    |                                                                   <span data-ttu-id="3111b-111">0</span><span class="sxs-lookup"><span data-stu-id="3111b-111">0</span></span>                                                                    |
|  <span data-ttu-id="3111b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3111b-112">Symbolic Name</span></span>  |                                                                   <span data-ttu-id="3111b-113">0</span><span class="sxs-lookup"><span data-stu-id="3111b-113">0</span></span>                                                                    |
|  <span data-ttu-id="3111b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3111b-114">Message Text</span></span>   | <span data-ttu-id="3111b-115">下列 Windows 元件可能未安裝： 應用程式伺服器-&gt; Internet Information Services (IIS)-&gt;常見的檔案。</span><span class="sxs-lookup"><span data-stu-id="3111b-115">The following Windows component may not be installed: Application Server -&gt; Internet Information Services (IIS) -&gt; Common Files.</span></span> |

## <a name="explanation"></a><span data-ttu-id="3111b-116">說明</span><span class="sxs-lookup"><span data-stu-id="3111b-116">Explanation</span></span>  
 <span data-ttu-id="3111b-117">而不需要網際網路資訊服務 (IIS) 安裝在本機電腦上嘗試發佈時，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3111b-117">This error will occur when publishing is attempted without Internet Information Services (IIS) installed on the local computer.</span></span>  

## <a name="user-action"></a><span data-ttu-id="3111b-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3111b-118">User Action</span></span>  
 <span data-ttu-id="3111b-119">Windows 7 和 Windows Vista SP2，將 IIS 安裝在本機電腦，並將 IIS 設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3111b-119">For Windows 7 and Windows Vista SP2, Install IIS on the local machine and configure IIS as follows:</span></span>  

1. <span data-ttu-id="3111b-120">按一下 **開始**，按一下**控制台**，然後按一下**程式**。</span><span class="sxs-lookup"><span data-stu-id="3111b-120">Click **Start**, click **Control Panel**, and click **Programs**.</span></span>  

2. <span data-ttu-id="3111b-121">按一下 **開啟或關閉開啟的 Windows 功能**。</span><span class="sxs-lookup"><span data-stu-id="3111b-121">Click **Turn Windows features on and off**.</span></span> <span data-ttu-id="3111b-122">[Windows 功能精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3111b-122">The Windows Features Wizard appears.</span></span>  

3. <span data-ttu-id="3111b-123">若要新增，請核取 IIS 元件。</span><span class="sxs-lookup"><span data-stu-id="3111b-123">To add, check the IIS component.</span></span>  

   <span data-ttu-id="3111b-124">針對[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，將 IIS 安裝在本機電腦，並將 IIS 設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3111b-124">For [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Install IIS on the local machine and configure IIS as follows:</span></span>  

4. <span data-ttu-id="3111b-125">按一下 **開始**，按一下**控制台**，然後按一下**系統管理工具**。</span><span class="sxs-lookup"><span data-stu-id="3111b-125">Click **Start**, click **Control Panel**, and click **Administrative Tools**.</span></span>  

5. <span data-ttu-id="3111b-126">按一下 **伺服器管理員**。</span><span class="sxs-lookup"><span data-stu-id="3111b-126">Click **Server Manager**.</span></span> <span data-ttu-id="3111b-127">[伺服器管理員] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3111b-127">The Server Manger window appears.</span></span>  

6. <span data-ttu-id="3111b-128">按一下 [**新增角色**，新增角色精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3111b-128">Click **Add Roles**, Add Roles Wizard appears.</span></span>  

7. <span data-ttu-id="3111b-129">若要新增，請選取 IIS 元件。</span><span class="sxs-lookup"><span data-stu-id="3111b-129">To add, Select IIS component.</span></span>
