---
title: 單一登入： 事件 11035 |Microsoft Docs
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
ms.openlocfilehash: 194d3069f0b74022e6b16a28de1c7f81ae3030f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001719"
---
# <a name="single-sign-on-event-11035"></a><span data-ttu-id="debbd-102">單一登入： 事件 11035</span><span class="sxs-lookup"><span data-stu-id="debbd-102">Single Sign-On: Event 11035</span></span>
## <a name="details"></a><span data-ttu-id="debbd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="debbd-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="debbd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="debbd-104">Product Name</span></span>   |                                                                                                                                               <span data-ttu-id="debbd-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="debbd-105">Enterprise Single Sign-On</span></span>                                                                                                                                                |
| <span data-ttu-id="debbd-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="debbd-106">Product Version</span></span> |                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                               |
|    <span data-ttu-id="debbd-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="debbd-107">Event ID</span></span>     |                                                                                                                                                         <span data-ttu-id="debbd-108">11035</span><span class="sxs-lookup"><span data-stu-id="debbd-108">11035</span></span>                                                                                                                                                          |
|  <span data-ttu-id="debbd-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="debbd-109">Event Source</span></span>   |                                                                                                                                                         <span data-ttu-id="debbd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="debbd-110">ENTSSO</span></span>                                                                                                                                                         |
|    <span data-ttu-id="debbd-111">元件</span><span class="sxs-lookup"><span data-stu-id="debbd-111">Component</span></span>    |                                                                                                                                                          <span data-ttu-id="debbd-112">不適用</span><span class="sxs-lookup"><span data-stu-id="debbd-112">N/A</span></span>                                                                                                                                                           |
|  <span data-ttu-id="debbd-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="debbd-113">Symbolic Name</span></span>  |                                                                                                                                           <span data-ttu-id="debbd-114">SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="debbd-114">SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER</span></span>                                                                                                                                            |
|  <span data-ttu-id="debbd-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="debbd-115">Message Text</span></span>   | <span data-ttu-id="debbd-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="debbd-116">Windows password change.</span></span> <span data-ttu-id="debbd-117">已偵測到此 Windows 帳戶的對應，但忽略，因為此 application.%r 未設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="debbd-117">A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.%r</span></span><br /><br /> <span data-ttu-id="debbd-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="debbd-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="debbd-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="debbd-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="debbd-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="debbd-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="debbd-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="debbd-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="debbd-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="debbd-122">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="debbd-123">說明</span><span class="sxs-lookup"><span data-stu-id="debbd-123">Explanation</span></span>  
 <span data-ttu-id="debbd-124">已偵測到此 Windows 帳戶的對應，但忽略，因為未針對此應用程式設定密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="debbd-124">A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="debbd-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="debbd-125">User Action</span></span>  
 <span data-ttu-id="debbd-126">如需設定密碼同步處理資訊，請參閱[密碼同步化](../core/password-synchronization2.md)。</span><span class="sxs-lookup"><span data-stu-id="debbd-126">For information on configuring Password Sync, see [Password Synchronization](../core/password-synchronization2.md).</span></span>