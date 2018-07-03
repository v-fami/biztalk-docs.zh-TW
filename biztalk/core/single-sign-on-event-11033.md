---
title: 單一登入： 事件 11033 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eed8e984-2b6c-4a9e-8603-175fdcabeb0a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25db9678dbef67672c2d86273f8938e94de09000
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011719"
---
# <a name="single-sign-on-event-11033"></a><span data-ttu-id="a0c2c-102">單一登入： 事件 11033</span><span class="sxs-lookup"><span data-stu-id="a0c2c-102">Single Sign-On: Event 11033</span></span>
## <a name="details"></a><span data-ttu-id="a0c2c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0c2c-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a0c2c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a0c2c-104">Product Name</span></span>   |                                                                                                                                   <span data-ttu-id="a0c2c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a0c2c-105">Enterprise Single Sign-On</span></span>                                                                                                                                   |
| <span data-ttu-id="a0c2c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a0c2c-106">Product Version</span></span> |                                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                   |
|    <span data-ttu-id="a0c2c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a0c2c-107">Event ID</span></span>     |                                                                                                                                             <span data-ttu-id="a0c2c-108">11033</span><span class="sxs-lookup"><span data-stu-id="a0c2c-108">11033</span></span>                                                                                                                                             |
|  <span data-ttu-id="a0c2c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a0c2c-109">Event Source</span></span>   |                                                                                                                                            <span data-ttu-id="a0c2c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a0c2c-110">ENTSSO</span></span>                                                                                                                                             |
|    <span data-ttu-id="a0c2c-111">元件</span><span class="sxs-lookup"><span data-stu-id="a0c2c-111">Component</span></span>    |                                                                                                                                              <span data-ttu-id="a0c2c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a0c2c-112">N/A</span></span>                                                                                                                                              |
|  <span data-ttu-id="a0c2c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a0c2c-113">Symbolic Name</span></span>  |                                                                                                                              <span data-ttu-id="a0c2c-114">SSO_INFO_PS_WIN_CHANGE_APP_DISABLED</span><span class="sxs-lookup"><span data-stu-id="a0c2c-114">SSO_INFO_PS_WIN_CHANGE_APP_DISABLED</span></span>                                                                                                                              |
|  <span data-ttu-id="a0c2c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a0c2c-115">Message Text</span></span>   | <span data-ttu-id="a0c2c-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="a0c2c-116">Windows password change.</span></span> <span data-ttu-id="a0c2c-117">已偵測到此 Windows 帳戶的對應，但忽略，因為應用程式是 disabled.%r</span><span class="sxs-lookup"><span data-stu-id="a0c2c-117">A mapping for this Windows account has been detected but ignored because the application is disabled.%r</span></span><br /><br /> <span data-ttu-id="a0c2c-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a0c2c-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a0c2c-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a0c2c-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="a0c2c-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="a0c2c-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="a0c2c-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="a0c2c-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="a0c2c-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="a0c2c-122">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a0c2c-123">說明</span><span class="sxs-lookup"><span data-stu-id="a0c2c-123">Explanation</span></span>  
 <span data-ttu-id="a0c2c-124">已偵測到此 Windows 帳戶的對應，但忽略，因為應用程式已停用。</span><span class="sxs-lookup"><span data-stu-id="a0c2c-124">A mapping for this Windows account has been detected but ignored because the application is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0c2c-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a0c2c-125">User Action</span></span>  
 <span data-ttu-id="a0c2c-126">若要啟用應用程式，請參閱[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c2c-126">To enable the application, see [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md).</span></span>