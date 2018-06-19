---
title: 單一登入： 事件 10517 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b63e4b0-0ef6-45c2-b8b1-55ac20e79e26
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2716eb7d331ec5c15070555a028c00310188856c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271238"
---
# <a name="single-sign-on-event-10517"></a><span data-ttu-id="3a504-102">單一登入： 事件 10517</span><span class="sxs-lookup"><span data-stu-id="3a504-102">Single Sign-On: Event 10517</span></span>
## <a name="details"></a><span data-ttu-id="3a504-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a504-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a504-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a504-104">Product Name</span></span>|<span data-ttu-id="3a504-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3a504-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3a504-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3a504-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3a504-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a504-107">Event ID</span></span>|<span data-ttu-id="3a504-108">10517</span><span class="sxs-lookup"><span data-stu-id="3a504-108">10517</span></span>|  
|<span data-ttu-id="3a504-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a504-109">Event Source</span></span>|<span data-ttu-id="3a504-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3a504-110">ENTSSO</span></span>|  
|<span data-ttu-id="3a504-111">元件</span><span class="sxs-lookup"><span data-stu-id="3a504-111">Component</span></span>|<span data-ttu-id="3a504-112">N\A</span><span class="sxs-lookup"><span data-stu-id="3a504-112">N\A</span></span>|  
|<span data-ttu-id="3a504-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a504-113">Symbolic Name</span></span>|<span data-ttu-id="3a504-114">SSO_ERROR_BAD_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="3a504-114">SSO_ERROR_BAD_SSO_ADMIN</span></span>|  
|<span data-ttu-id="3a504-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a504-115">Message Text</span></span>|<span data-ttu-id="3a504-116">SSO 系統管理員帳戶無效。</span><span class="sxs-lookup"><span data-stu-id="3a504-116">The SSO Administrators account is not valid.</span></span> <span data-ttu-id="3a504-117">如果是本機帳戶核取此帳戶是否存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="3a504-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="3a504-118">如果是網域帳戶請連絡您的網域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3a504-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="3a504-119">當帳戶 valid.%r 啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="3a504-119">Enable SSO when the account is valid.%r</span></span><br /><br /> <span data-ttu-id="3a504-120">SSO 系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="3a504-120">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="3a504-121">無效的帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="3a504-121">Invalid accounts: %2%r</span></span><br /><br /> <span data-ttu-id="3a504-122">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="3a504-122">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a504-123">說明</span><span class="sxs-lookup"><span data-stu-id="3a504-123">Explanation</span></span>  
 <span data-ttu-id="3a504-124">這個錯誤事件表示針對企業單一登入指定的 SSO 系統管理員帳戶不是有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="3a504-124">This Error event indicates that the SSO Administrators account specified for Enterprise Single Sign-On is not a valid Windows account.</span></span> <span data-ttu-id="3a504-125">執行「企業單一登入」服務的服務帳戶需為此帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="3a504-125">The service account running the Enterprise Single Sign-On service must be a member of this account.</span></span> <span data-ttu-id="3a504-126">SSO 系統管理員帳戶可以是 Windows 群組帳戶或個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="3a504-126">The SSO Administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="3a504-127">SSO 系統管理員帳戶也可以是網域或本機群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="3a504-127">The SSO Administrators account can also be either a domain or local group account.</span></span> <span data-ttu-id="3a504-128">若使用個人帳戶，您無法將此帳戶改為另一個個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="3a504-128">When using an individual account, you cannot change this account to another individual account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a504-129">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a504-129">User Action</span></span>  
 <span data-ttu-id="3a504-130">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3a504-130">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="3a504-131">請確認 SSO 系統管理員帳戶存在。</span><span class="sxs-lookup"><span data-stu-id="3a504-131">Verify the SSO Administrators account exists.</span></span>  
  
 <span data-ttu-id="3a504-132">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="3a504-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="3a504-133">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="3a504-133">SSO User Groups</span></span>](../core/sso-user-groups.md)