---
title: 單一登入： 事件 10709 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98e86890-88dd-49f0-bb2c-1234507e8be5
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a28807d9307ba1217e5b48e24facfe36711536f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271166"
---
# <a name="single-sign-on-event-10709"></a><span data-ttu-id="41d6e-102">單一登入： 事件 10709</span><span class="sxs-lookup"><span data-stu-id="41d6e-102">Single Sign-On: Event 10709</span></span>
## <a name="details"></a><span data-ttu-id="41d6e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="41d6e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41d6e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="41d6e-104">Product Name</span></span>|<span data-ttu-id="41d6e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="41d6e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="41d6e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="41d6e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="41d6e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="41d6e-107">Event ID</span></span>|<span data-ttu-id="41d6e-108">10709</span><span class="sxs-lookup"><span data-stu-id="41d6e-108">10709</span></span>|  
|<span data-ttu-id="41d6e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="41d6e-109">Event Source</span></span>|<span data-ttu-id="41d6e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="41d6e-110">ENTSSO</span></span>|  
|<span data-ttu-id="41d6e-111">元件</span><span class="sxs-lookup"><span data-stu-id="41d6e-111">Component</span></span>|<span data-ttu-id="41d6e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="41d6e-112">N\A</span></span>|  
|<span data-ttu-id="41d6e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="41d6e-113">Symbolic Name</span></span>|<span data-ttu-id="41d6e-114">SSO_WARN_PS_PCNS_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="41d6e-114">SSO_WARN_PS_PCNS_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="41d6e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="41d6e-115">Message Text</span></span>|<span data-ttu-id="41d6e-116">來自 PCNS 的 Windows 密碼變更只能從網域控制站接受存取 domain.%r 中</span><span class="sxs-lookup"><span data-stu-id="41d6e-116">Windows password changes from PCNS will only be accepted from Domain Controllers in the access domain.%r</span></span><br /><br /> <span data-ttu-id="41d6e-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="41d6e-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="41d6e-118">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="41d6e-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="41d6e-119">存取網域: %3 %r</span><span class="sxs-lookup"><span data-stu-id="41d6e-119">Access Domain: %3%r</span></span><br /><br /> <span data-ttu-id="41d6e-120">存取 Sid: %4 %r</span><span class="sxs-lookup"><span data-stu-id="41d6e-120">Access Sid: %4%r</span></span><br /><br /> <span data-ttu-id="41d6e-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="41d6e-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41d6e-122">說明</span><span class="sxs-lookup"><span data-stu-id="41d6e-122">Explanation</span></span>  
 <span data-ttu-id="41d6e-123">這個警告事件表示 Windows 密碼變更已收到 ENTSSO 伺服器所在網域以外的伺服器從密碼變更通知服務 (PCNS)。</span><span class="sxs-lookup"><span data-stu-id="41d6e-123">This Warning event indicates that a Windows password change was received from Password Change Notification Services (PCNS) on a server outside the ENTSSO server's domain.</span></span> <span data-ttu-id="41d6e-124">Windows 密碼變更只能從與 ENTSSO 伺服器位於相同網域中網域控制站接受。</span><span class="sxs-lookup"><span data-stu-id="41d6e-124">Windows password changes will only be accepted from domain controllers in the same domain as the ENTSSO server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41d6e-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="41d6e-125">User Action</span></span>  
 <span data-ttu-id="41d6e-126">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="41d6e-126">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="41d6e-127">設定 PCNS 相同網域中的 ENTSSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="41d6e-127">Configure an ENTSSO server in the same domain as PCNS.</span></span>  
  
 <span data-ttu-id="41d6e-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="41d6e-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="41d6e-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="41d6e-129">Password Synchronization</span></span>](../core/password-synchronization2.md)