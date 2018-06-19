---
title: 單一登入： 事件 11035 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d551083c-a897-4a76-a40c-2254d3a3e52e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e104d28517eab153880e3c922f3fd1f174a6170a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276710"
---
# <a name="single-sign-on-event-11035"></a><span data-ttu-id="58313-102">單一登入： 事件 11035</span><span class="sxs-lookup"><span data-stu-id="58313-102">Single Sign-On: Event 11035</span></span>
## <a name="details"></a><span data-ttu-id="58313-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58313-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58313-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="58313-104">Product Name</span></span>|<span data-ttu-id="58313-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="58313-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="58313-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="58313-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="58313-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="58313-107">Event ID</span></span>|<span data-ttu-id="58313-108">11035</span><span class="sxs-lookup"><span data-stu-id="58313-108">11035</span></span>|  
|<span data-ttu-id="58313-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="58313-109">Event Source</span></span>|<span data-ttu-id="58313-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="58313-110">ENTSSO</span></span>|  
|<span data-ttu-id="58313-111">元件</span><span class="sxs-lookup"><span data-stu-id="58313-111">Component</span></span>|<span data-ttu-id="58313-112">不適用</span><span class="sxs-lookup"><span data-stu-id="58313-112">N/A</span></span>|  
|<span data-ttu-id="58313-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="58313-113">Symbolic Name</span></span>|<span data-ttu-id="58313-114">SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="58313-114">SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER</span></span>|  
|<span data-ttu-id="58313-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="58313-115">Message Text</span></span>|<span data-ttu-id="58313-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="58313-116">Windows password change.</span></span> <span data-ttu-id="58313-117">已偵測到此 Windows 帳戶的對應，但忽略，因為 application.%r 未設定密碼同步</span><span class="sxs-lookup"><span data-stu-id="58313-117">A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.%r</span></span><br /><br /> <span data-ttu-id="58313-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="58313-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="58313-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="58313-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="58313-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="58313-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="58313-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="58313-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="58313-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="58313-122">Client User: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58313-123">說明</span><span class="sxs-lookup"><span data-stu-id="58313-123">Explanation</span></span>  
 <span data-ttu-id="58313-124">已偵測到此 Windows 帳戶的對應但忽略，因為此應用程式未設定密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="58313-124">A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58313-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="58313-125">User Action</span></span>  
 <span data-ttu-id="58313-126">如需設定密碼同步處理的資訊，請參閱[密碼同步化](../core/password-synchronization2.md)。</span><span class="sxs-lookup"><span data-stu-id="58313-126">For information on configuring Password Sync, see [Password Synchronization](../core/password-synchronization2.md).</span></span>