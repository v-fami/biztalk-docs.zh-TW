---
title: 單一登入： 事件 10516 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d20df92f-c995-4cbc-a8f9-21cea30b82c9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b74ca4a47bc62d28b25564bd5843729c56362
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269894"
---
# <a name="single-sign-on-event-10516"></a><span data-ttu-id="830c0-102">單一登入： 事件 10516</span><span class="sxs-lookup"><span data-stu-id="830c0-102">Single Sign-On: Event 10516</span></span>
## <a name="details"></a><span data-ttu-id="830c0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="830c0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="830c0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="830c0-104">Product Name</span></span>|<span data-ttu-id="830c0-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="830c0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="830c0-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="830c0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="830c0-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="830c0-107">Event ID</span></span>|<span data-ttu-id="830c0-108">10516</span><span class="sxs-lookup"><span data-stu-id="830c0-108">10516</span></span>|  
|<span data-ttu-id="830c0-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="830c0-109">Event Source</span></span>|<span data-ttu-id="830c0-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="830c0-110">ENTSSO</span></span>|  
|<span data-ttu-id="830c0-111">元件</span><span class="sxs-lookup"><span data-stu-id="830c0-111">Component</span></span>|<span data-ttu-id="830c0-112">N\A</span><span class="sxs-lookup"><span data-stu-id="830c0-112">N\A</span></span>|  
|<span data-ttu-id="830c0-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="830c0-113">Symbolic Name</span></span>|<span data-ttu-id="830c0-114">SSO_ERROR_BAD_SSO_APP_ADMIN</span><span class="sxs-lookup"><span data-stu-id="830c0-114">SSO_ERROR_BAD_SSO_APP_ADMIN</span></span>|  
|<span data-ttu-id="830c0-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="830c0-115">Message Text</span></span>|<span data-ttu-id="830c0-116">SSO 分支機構系統管理員帳戶無效。</span><span class="sxs-lookup"><span data-stu-id="830c0-116">The SSO Affiliate Administrators account is not valid.</span></span> <span data-ttu-id="830c0-117">如果是本機帳戶核取此帳戶是否存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="830c0-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="830c0-118">如果是網域帳戶請連絡您的網域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="830c0-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="830c0-119">當帳戶 valid.%r 啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="830c0-119">Enable SSO when the account is valid.%r</span></span><br /><br /> <span data-ttu-id="830c0-120">SSO 分支機構系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="830c0-120">SSO Affiliate Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="830c0-121">無效的帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="830c0-121">Invalid accounts: %2%r</span></span><br /><br /> <span data-ttu-id="830c0-122">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="830c0-122">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="830c0-123">說明</span><span class="sxs-lookup"><span data-stu-id="830c0-123">Explanation</span></span>  
 <span data-ttu-id="830c0-124">這個錯誤事件表示，SSO 分支機構系統管理員帳戶或企業登登入所建立的群組不是有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="830c0-124">This Error event indicates that the SSO Affiliate Administrator account or group created by Enterprise Sing Sign-on is not a valid Windows account.</span></span> <span data-ttu-id="830c0-125">SSO 分支機構系統管理員帳戶可以是 Windows 群組帳戶或個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="830c0-125">The SSO Affiliate Administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="830c0-126">SSO 分支機構系統管理員帳戶也可以是網域或本機群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="830c0-126">The SSO Affiliate Administrator account can also be either a domain or local group account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="830c0-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="830c0-127">User Action</span></span>  
 <span data-ttu-id="830c0-128">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="830c0-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="830c0-129">請確認 SSO 分支機構系統管理員帳戶存在。</span><span class="sxs-lookup"><span data-stu-id="830c0-129">Verify the SSO Affiliate Administrator account exists.</span></span>  
  
 <span data-ttu-id="830c0-130">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="830c0-130">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="830c0-131">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="830c0-131">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="830c0-132">如何更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="830c0-132">How to Update the SSO Database</span></span>](../core/how-to-update-the-sso-database.md)