---
title: 單一登入： 事件 10731 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 605e77f0-61f2-4a97-9ea0-bdc56344e8d9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10960489638aa565a11ecc32c70fc3a8fc6d477b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270686"
---
# <a name="single-sign-on-event-10731"></a><span data-ttu-id="f5655-102">單一登入： 事件 10731</span><span class="sxs-lookup"><span data-stu-id="f5655-102">Single Sign-On: Event 10731</span></span>
## <a name="details"></a><span data-ttu-id="f5655-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f5655-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5655-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f5655-104">Product Name</span></span>|<span data-ttu-id="f5655-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f5655-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f5655-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f5655-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f5655-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f5655-107">Event ID</span></span>|<span data-ttu-id="f5655-108">10731</span><span class="sxs-lookup"><span data-stu-id="f5655-108">10731</span></span>|  
|<span data-ttu-id="f5655-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f5655-109">Event Source</span></span>|<span data-ttu-id="f5655-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f5655-110">ENTSSO</span></span>|  
|<span data-ttu-id="f5655-111">元件</span><span class="sxs-lookup"><span data-stu-id="f5655-111">Component</span></span>|<span data-ttu-id="f5655-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f5655-112">N\A</span></span>|  
|<span data-ttu-id="f5655-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f5655-113">Symbolic Name</span></span>|<span data-ttu-id="f5655-114">SSO_WARN_INVALID_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="f5655-114">SSO_WARN_INVALID_USER_NOT_IN_GROUP</span></span>|  
|<span data-ttu-id="f5655-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f5655-115">Message Text</span></span>|<span data-ttu-id="f5655-116">無法建立對應，因為指定的使用者不是應用程式使用者帳戶的成員。%r</span><span class="sxs-lookup"><span data-stu-id="f5655-116">A mapping could not be created because the specified user is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="f5655-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f5655-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="f5655-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f5655-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="f5655-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f5655-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="f5655-120">應用程式使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="f5655-120">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="f5655-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="f5655-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f5655-122">說明</span><span class="sxs-lookup"><span data-stu-id="f5655-122">Explanation</span></span>  
 <span data-ttu-id="f5655-123">這個警告事件表示因為指定的使用者不是應用程式使用者帳戶的成員，不可能建立對應。</span><span class="sxs-lookup"><span data-stu-id="f5655-123">This Warning event indicates that a mapping could not be created because the specified user is not a member of the Application Users account.</span></span>  
  
 <span data-ttu-id="f5655-124">每個分支機構應用程式的應用程式使用者群組帳戶存在。</span><span class="sxs-lookup"><span data-stu-id="f5655-124">An application user's group account exists for each affiliate application.</span></span> <span data-ttu-id="f5655-125">此帳戶的成員可以確認其分支機構應用程式中的認證，而且可以管理他們的認證對應的分支機構應用程式中。</span><span class="sxs-lookup"><span data-stu-id="f5655-125">Members of this account can verify their credentials in the affiliate application and can manage their credential mappings in the affiliate application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f5655-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f5655-126">User Action</span></span>  
 <span data-ttu-id="f5655-127">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f5655-127">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="f5655-128">將指定的使用者加入至指定的分支機構應用程式的應用程式使用者的群組。</span><span class="sxs-lookup"><span data-stu-id="f5655-128">Add the specified user to the application user's group for the specified affiliate application.</span></span>  
  
 <span data-ttu-id="f5655-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="f5655-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="f5655-130">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="f5655-130">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="f5655-131">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="f5655-131">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)