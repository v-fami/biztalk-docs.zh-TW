---
title: "單一登入： 事件 10518 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 274e29f9-1933-4e40-83c0-2e84c6708315
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27b82d7f0a6bbaf02400679add53851867d728c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10518"></a><span data-ttu-id="ee751-102">單一登入： 事件 10518</span><span class="sxs-lookup"><span data-stu-id="ee751-102">Single Sign-On: Event 10518</span></span>
## <a name="details"></a><span data-ttu-id="ee751-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee751-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee751-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee751-104">Product Name</span></span>|<span data-ttu-id="ee751-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ee751-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ee751-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ee751-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ee751-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee751-107">Event ID</span></span>|<span data-ttu-id="ee751-108">10518</span><span class="sxs-lookup"><span data-stu-id="ee751-108">10518</span></span>|  
|<span data-ttu-id="ee751-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee751-109">Event Source</span></span>|<span data-ttu-id="ee751-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ee751-110">ENTSSO</span></span>|  
|<span data-ttu-id="ee751-111">元件</span><span class="sxs-lookup"><span data-stu-id="ee751-111">Component</span></span>|<span data-ttu-id="ee751-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ee751-112">N\A</span></span>|  
|<span data-ttu-id="ee751-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ee751-113">Symbolic Name</span></span>|<span data-ttu-id="ee751-114">SSO_WARN_BAD_USER_GROUP</span><span class="sxs-lookup"><span data-stu-id="ee751-114">SSO_WARN_BAD_USER_GROUP</span></span>|  
|<span data-ttu-id="ee751-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee751-115">Message Text</span></span>|<span data-ttu-id="ee751-116">此應用程式的應用程式使用者帳戶不是有效的。</span><span class="sxs-lookup"><span data-stu-id="ee751-116">The Application Users account for this application is not valid.</span></span> <span data-ttu-id="ee751-117">如果是本機帳戶核取此帳戶是否存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="ee751-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="ee751-118">如果是網域帳戶請連絡您的網域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ee751-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="ee751-119">當帳戶有效，請讓應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee751-119">Enable the application when the account is valid.</span></span> <span data-ttu-id="ee751-120">如果您不打算使用此應用程式在此 computer.%r 上，您可以忽略這個訊息</span><span class="sxs-lookup"><span data-stu-id="ee751-120">You can ignore this message if you are not going to use this application on this computer.%r</span></span><br /><br /> <span data-ttu-id="ee751-121">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ee751-121">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="ee751-122">應用程式使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ee751-122">Application Users: %2%r</span></span><br /><br /> <span data-ttu-id="ee751-123">無效的帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="ee751-123">Invalid accounts: %3%r</span></span><br /><br /> <span data-ttu-id="ee751-124">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="ee751-124">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee751-125">說明</span><span class="sxs-lookup"><span data-stu-id="ee751-125">Explanation</span></span>  
 <span data-ttu-id="ee751-126">這個警告事件表示應用程式使用者群組帳戶不是有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee751-126">This Warning event indicates that an Application Users group account is not a valid Windows account.</span></span> <span data-ttu-id="ee751-127">沒有一個應用程式使用者帳戶群組，每個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee751-127">There is one Application Users account group for each affiliate application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee751-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee751-128">User Action</span></span>  
 <span data-ttu-id="ee751-129">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="ee751-129">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="ee751-130">請確認指定的應用程式使用者帳戶存在。</span><span class="sxs-lookup"><span data-stu-id="ee751-130">Verify the specified Application Users account exists.</span></span>  
  
-   <span data-ttu-id="ee751-131">使用 SSO 管理公用程式來驗證指定的分支機構應用程式設定為使用正確的應用程式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee751-131">Use the SSO Administration Utility to verify the specified affiliate application is configured to use the correct application users account.</span></span>  
  
 <span data-ttu-id="ee751-132">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="ee751-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ee751-133">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="ee751-133">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="ee751-134">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="ee751-134">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  
  
-   [<span data-ttu-id="ee751-135">如何更新分支機構應用程式的內容</span><span class="sxs-lookup"><span data-stu-id="ee751-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)