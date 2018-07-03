---
title: 單一登入： 事件 11036 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f19a3ff1d35d3c2de04ec9c3846de94d7a2657a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013911"
---
# <a name="single-sign-on-event-11036"></a><span data-ttu-id="665a6-102">單一登入： 事件 11036</span><span class="sxs-lookup"><span data-stu-id="665a6-102">Single Sign-On: Event 11036</span></span>
## <a name="details"></a><span data-ttu-id="665a6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="665a6-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="665a6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="665a6-104">Product Name</span></span>   |                                                                                                                                                                <span data-ttu-id="665a6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="665a6-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                |
| <span data-ttu-id="665a6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="665a6-106">Product Version</span></span> |                                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                |
|    <span data-ttu-id="665a6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="665a6-107">Event ID</span></span>     |                                                                                                                                                                          <span data-ttu-id="665a6-108">11036</span><span class="sxs-lookup"><span data-stu-id="665a6-108">11036</span></span>                                                                                                                                                                          |
|  <span data-ttu-id="665a6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="665a6-109">Event Source</span></span>   |                                                                                                                                                                         <span data-ttu-id="665a6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="665a6-110">ENTSSO</span></span>                                                                                                                                                                          |
|    <span data-ttu-id="665a6-111">元件</span><span class="sxs-lookup"><span data-stu-id="665a6-111">Component</span></span>    |                                                                                                                                                                           <span data-ttu-id="665a6-112">不適用</span><span class="sxs-lookup"><span data-stu-id="665a6-112">N/A</span></span>                                                                                                                                                                           |
|  <span data-ttu-id="665a6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="665a6-113">Symbolic Name</span></span>  |                                                                                                                                                         <span data-ttu-id="665a6-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span><span class="sxs-lookup"><span data-stu-id="665a6-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span></span>                                                                                                                                                          |
|  <span data-ttu-id="665a6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="665a6-115">Message Text</span></span>   | <span data-ttu-id="665a6-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="665a6-116">Windows password change.</span></span> <span data-ttu-id="665a6-117">已偵測到此 Windows 帳戶的對應，但忽略，因為此應用程式設定的配接器不支援對外部 systems.%r 的密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="665a6-117">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.%r</span></span><br /><br /> <span data-ttu-id="665a6-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="665a6-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="665a6-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="665a6-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="665a6-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="665a6-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="665a6-121">配接器: %4 %r</span><span class="sxs-lookup"><span data-stu-id="665a6-121">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="665a6-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="665a6-122">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="665a6-123">說明</span><span class="sxs-lookup"><span data-stu-id="665a6-123">Explanation</span></span>  
 <span data-ttu-id="665a6-124">已偵測到此 Windows 帳戶的對應，但忽略，因為此應用程式設定的配接器不支援密碼同步處理到外部系統。</span><span class="sxs-lookup"><span data-stu-id="665a6-124">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="665a6-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="665a6-125">User Action</span></span>  
 <span data-ttu-id="665a6-126">請檢查您的配接器組態。</span><span class="sxs-lookup"><span data-stu-id="665a6-126">Check your adapter configuration.</span></span>  
  
 <span data-ttu-id="665a6-127">如需有關密碼同步處理，請參閱[密碼同步化](../core/password-synchronization2.md)。</span><span class="sxs-lookup"><span data-stu-id="665a6-127">For information on Password Sync, see [Password Synchronization](../core/password-synchronization2.md).</span></span>