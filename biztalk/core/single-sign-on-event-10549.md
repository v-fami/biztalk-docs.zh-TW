---
title: "單一登入： 事件 10549 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a18eb63-700c-4f49-acc4-890abe2a00ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a59feecdcf5daeef7013dd99eca1e778d49278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10549"></a><span data-ttu-id="51a80-102">單一登入： 事件 10549</span><span class="sxs-lookup"><span data-stu-id="51a80-102">Single Sign-On: Event 10549</span></span>
## <a name="details"></a><span data-ttu-id="51a80-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51a80-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51a80-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="51a80-104">Product Name</span></span>|<span data-ttu-id="51a80-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="51a80-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="51a80-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="51a80-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="51a80-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="51a80-107">Event ID</span></span>|<span data-ttu-id="51a80-108">10549</span><span class="sxs-lookup"><span data-stu-id="51a80-108">10549</span></span>|  
|<span data-ttu-id="51a80-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="51a80-109">Event Source</span></span>|<span data-ttu-id="51a80-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="51a80-110">ENTSSO</span></span>|  
|<span data-ttu-id="51a80-111">元件</span><span class="sxs-lookup"><span data-stu-id="51a80-111">Component</span></span>|<span data-ttu-id="51a80-112">CO</span><span class="sxs-lookup"><span data-stu-id="51a80-112">CO</span></span>|  
|<span data-ttu-id="51a80-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="51a80-113">Symbolic Name</span></span>|<span data-ttu-id="51a80-114">SSO_ERROR_CREATE_DATABASE_FAILED</span><span class="sxs-lookup"><span data-stu-id="51a80-114">SSO_ERROR_CREATE_DATABASE_FAILED</span></span>|  
|<span data-ttu-id="51a80-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="51a80-115">Message Text</span></span>|<span data-ttu-id="51a80-116">建立及初始化 SSO 資料庫失敗。%r</span><span class="sxs-lookup"><span data-stu-id="51a80-116">Creation and initialization of the SSO database failed.%r</span></span><br /><br /> <span data-ttu-id="51a80-117">SQL Server 名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="51a80-117">SQL Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="51a80-118">SSO 資料庫名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="51a80-118">SSO Database Name: %2%r</span></span><br /><br /> <span data-ttu-id="51a80-119">用戶端使用者: %3 %r</span><span class="sxs-lookup"><span data-stu-id="51a80-119">Client User: %3%r</span></span><br /><br /> <span data-ttu-id="51a80-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="51a80-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="51a80-121">說明</span><span class="sxs-lookup"><span data-stu-id="51a80-121">Explanation</span></span>  
 <span data-ttu-id="51a80-122">此錯誤表示建立與初始化 SSO 資料庫失敗。</span><span class="sxs-lookup"><span data-stu-id="51a80-122">This Error indicates that creation and initialization of the SSO database failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="51a80-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="51a80-123">User Action</span></span>  
 <span data-ttu-id="51a80-124">若要解決此錯誤，請執行下列：</span><span class="sxs-lookup"><span data-stu-id="51a80-124">To resolve this error do the following:</span></span>  
  
-   <span data-ttu-id="51a80-125">檢查系統和應用程式事件記錄檔相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="51a80-125">Check the system and application event logs for associated messages.</span></span>  
  
-   <span data-ttu-id="51a80-126">再次執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="51a80-126">Run Setup again.</span></span>  
  
 <span data-ttu-id="51a80-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="51a80-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="51a80-128">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="51a80-128">Installing SSO</span></span>](../core/installing-sso.md)