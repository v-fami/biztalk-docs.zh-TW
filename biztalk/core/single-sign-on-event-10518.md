---
title: 單一登入： 事件 10518 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 274e29f9-1933-4e40-83c0-2e84c6708315
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76b267950d734f6a0935ed22e27782e8a6bcd1f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011407"
---
# <a name="single-sign-on-event-10518"></a><span data-ttu-id="35498-102">單一登入： 事件 10518</span><span class="sxs-lookup"><span data-stu-id="35498-102">Single Sign-On: Event 10518</span></span>
## <a name="details"></a><span data-ttu-id="35498-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35498-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="35498-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35498-104">Product Name</span></span>   |                                                                                                                                                                                                                                <span data-ttu-id="35498-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="35498-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                                                                                 |
| <span data-ttu-id="35498-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="35498-106">Product Version</span></span> |                                                                                                                                                                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                                                                |
|    <span data-ttu-id="35498-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35498-107">Event ID</span></span>     |                                                                                                                                                                                                                                          <span data-ttu-id="35498-108">10518</span><span class="sxs-lookup"><span data-stu-id="35498-108">10518</span></span>                                                                                                                                                                                                                                           |
|  <span data-ttu-id="35498-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="35498-109">Event Source</span></span>   |                                                                                                                                                                                                                                          <span data-ttu-id="35498-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="35498-110">ENTSSO</span></span>                                                                                                                                                                                                                                          |
|    <span data-ttu-id="35498-111">元件</span><span class="sxs-lookup"><span data-stu-id="35498-111">Component</span></span>    |                                                                                                                                                                                                                                           <span data-ttu-id="35498-112">N\A</span><span class="sxs-lookup"><span data-stu-id="35498-112">N\A</span></span>                                                                                                                                                                                                                                            |
|  <span data-ttu-id="35498-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35498-113">Symbolic Name</span></span>  |                                                                                                                                                                                                                                 <span data-ttu-id="35498-114">SSO_WARN_BAD_USER_GROUP</span><span class="sxs-lookup"><span data-stu-id="35498-114">SSO_WARN_BAD_USER_GROUP</span></span>                                                                                                                                                                                                                                  |
|  <span data-ttu-id="35498-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35498-115">Message Text</span></span>   | <span data-ttu-id="35498-116">此應用程式的應用程式使用者帳戶不是有效的。</span><span class="sxs-lookup"><span data-stu-id="35498-116">The Application Users account for this application is not valid.</span></span> <span data-ttu-id="35498-117">如果是本機帳戶核取此帳戶是否存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="35498-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="35498-118">如果是網域帳戶請連絡您的網域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="35498-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="35498-119">有效的帳戶時，請啟用應用程式。</span><span class="sxs-lookup"><span data-stu-id="35498-119">Enable the application when the account is valid.</span></span> <span data-ttu-id="35498-120">如果您不會在此 computer.%r 上使用此應用程式，您可以忽略此訊息</span><span class="sxs-lookup"><span data-stu-id="35498-120">You can ignore this message if you are not going to use this application on this computer.%r</span></span><br /><br /> <span data-ttu-id="35498-121">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="35498-121">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="35498-122">應用程式使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="35498-122">Application Users: %2%r</span></span><br /><br /> <span data-ttu-id="35498-123">無效的帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="35498-123">Invalid accounts: %3%r</span></span><br /><br /> <span data-ttu-id="35498-124">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="35498-124">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="35498-125">說明</span><span class="sxs-lookup"><span data-stu-id="35498-125">Explanation</span></span>  
 <span data-ttu-id="35498-126">這個警告事件表示應用程式使用者群組帳戶不是有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="35498-126">This Warning event indicates that an Application Users group account is not a valid Windows account.</span></span> <span data-ttu-id="35498-127">沒有一個應用程式使用者帳戶群組，每個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="35498-127">There is one Application Users account group for each affiliate application.</span></span>  

## <a name="user-action"></a><span data-ttu-id="35498-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35498-128">User Action</span></span>  
 <span data-ttu-id="35498-129">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="35498-129">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="35498-130">驗證指定的應用程式使用者帳戶存在。</span><span class="sxs-lookup"><span data-stu-id="35498-130">Verify the specified Application Users account exists.</span></span>  

- <span data-ttu-id="35498-131">使用 SSO 管理公用程式來驗證指定的分支機構應用程式設定為使用正確的應用程式的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="35498-131">Use the SSO Administration Utility to verify the specified affiliate application is configured to use the correct application users account.</span></span>  

  <span data-ttu-id="35498-132">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="35498-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="35498-133">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="35498-133">SSO User Groups</span></span>](../core/sso-user-groups.md)  

- [<span data-ttu-id="35498-134">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="35498-134">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  

- [<span data-ttu-id="35498-135">如何更新分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="35498-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
