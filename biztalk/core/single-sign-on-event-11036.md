---
title: "單一登入： 事件 11036 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63b11005248471c222f63c88439a0e60571b341e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11036"></a><span data-ttu-id="38c99-102">單一登入： 事件 11036</span><span class="sxs-lookup"><span data-stu-id="38c99-102">Single Sign-On: Event 11036</span></span>
## <a name="details"></a><span data-ttu-id="38c99-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="38c99-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38c99-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="38c99-104">Product Name</span></span>|<span data-ttu-id="38c99-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="38c99-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="38c99-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="38c99-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="38c99-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="38c99-107">Event ID</span></span>|<span data-ttu-id="38c99-108">11036</span><span class="sxs-lookup"><span data-stu-id="38c99-108">11036</span></span>|  
|<span data-ttu-id="38c99-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="38c99-109">Event Source</span></span>|<span data-ttu-id="38c99-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="38c99-110">ENTSSO</span></span>|  
|<span data-ttu-id="38c99-111">元件</span><span class="sxs-lookup"><span data-stu-id="38c99-111">Component</span></span>|<span data-ttu-id="38c99-112">不適用</span><span class="sxs-lookup"><span data-stu-id="38c99-112">N/A</span></span>|  
|<span data-ttu-id="38c99-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="38c99-113">Symbolic Name</span></span>|<span data-ttu-id="38c99-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span><span class="sxs-lookup"><span data-stu-id="38c99-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span></span>|  
|<span data-ttu-id="38c99-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="38c99-115">Message Text</span></span>|<span data-ttu-id="38c99-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="38c99-116">Windows password change.</span></span> <span data-ttu-id="38c99-117">已偵測到此 Windows 帳戶的對應，但忽略，因為此應用程式設定的配接器不支援對外部 systems.%r 密碼同步</span><span class="sxs-lookup"><span data-stu-id="38c99-117">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.%r</span></span><br /><br /> <span data-ttu-id="38c99-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="38c99-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="38c99-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="38c99-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="38c99-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="38c99-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="38c99-121">配接器: %4 %r</span><span class="sxs-lookup"><span data-stu-id="38c99-121">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="38c99-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="38c99-122">Client User: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38c99-123">說明</span><span class="sxs-lookup"><span data-stu-id="38c99-123">Explanation</span></span>  
 <span data-ttu-id="38c99-124">已偵測到此 Windows 帳戶的對應但忽略，因為此應用程式設定的配接器不支援外部系統密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="38c99-124">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38c99-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="38c99-125">User Action</span></span>  
 <span data-ttu-id="38c99-126">請檢查您的配接器組態。</span><span class="sxs-lookup"><span data-stu-id="38c99-126">Check your adapter configuration.</span></span>  
  
 <span data-ttu-id="38c99-127">如需密碼同步處理資訊，請參閱[密碼同步化](../core/password-synchronization2.md)。</span><span class="sxs-lookup"><span data-stu-id="38c99-127">For information on Password Sync, see [Password Synchronization](../core/password-synchronization2.md).</span></span>