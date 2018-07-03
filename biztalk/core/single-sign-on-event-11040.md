---
title: 單一登入： 事件 11040 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6ccdc06-9677-4454-ae2c-8dde78d6f3f8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eefc6c65e07b430851606ce7779aad3771776a83
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019068"
---
# <a name="single-sign-on-event-11040"></a><span data-ttu-id="c8498-102">單一登入： 事件 11040</span><span class="sxs-lookup"><span data-stu-id="c8498-102">Single Sign-On: Event 11040</span></span>
## <a name="details"></a><span data-ttu-id="c8498-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c8498-103">Details</span></span>  
  
|                 |                                                                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c8498-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c8498-104">Product Name</span></span>   |                                                                  <span data-ttu-id="c8498-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c8498-105">Enterprise Single Sign-On</span></span>                                                                  |
| <span data-ttu-id="c8498-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c8498-106">Product Version</span></span> |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    <span data-ttu-id="c8498-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c8498-107">Event ID</span></span>     |                                                                            <span data-ttu-id="c8498-108">11040</span><span class="sxs-lookup"><span data-stu-id="c8498-108">11040</span></span>                                                                            |
|  <span data-ttu-id="c8498-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c8498-109">Event Source</span></span>   |                                                                           <span data-ttu-id="c8498-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c8498-110">ENTSSO</span></span>                                                                            |
|    <span data-ttu-id="c8498-111">元件</span><span class="sxs-lookup"><span data-stu-id="c8498-111">Component</span></span>    |                                                                             <span data-ttu-id="c8498-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c8498-112">N/A</span></span>                                                                             |
|  <span data-ttu-id="c8498-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c8498-113">Symbolic Name</span></span>  |                                                                  <span data-ttu-id="c8498-114">SSO_WARN_NETWORK_SERVICE</span><span class="sxs-lookup"><span data-stu-id="c8498-114">SSO_WARN_NETWORK_SERVICE</span></span>                                                                   |
|  <span data-ttu-id="c8498-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c8498-115">Message Text</span></span>   | <span data-ttu-id="c8498-116">SSO 服務正在網路服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c8498-116">The SSO service is running under the Network Service account.</span></span> <span data-ttu-id="c8498-117">這個帳戶有一些特殊考量。</span><span class="sxs-lookup"><span data-stu-id="c8498-117">There are some special considerations for this account.</span></span> <span data-ttu-id="c8498-118">請參閱 details.%r 您文件</span><span class="sxs-lookup"><span data-stu-id="c8498-118">See your documentation for details.%r</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="c8498-119">說明</span><span class="sxs-lookup"><span data-stu-id="c8498-119">Explanation</span></span>  
 <span data-ttu-id="c8498-120">SSO 服務正在網路服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c8498-120">The SSO service is running under the Network Service account.</span></span> <span data-ttu-id="c8498-121">這個帳戶有一些特殊考量。</span><span class="sxs-lookup"><span data-stu-id="c8498-121">There are some special considerations for this account.</span></span> <span data-ttu-id="c8498-122">例如，新增網路服務帳戶之後需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="c8498-122">For example, a reboot is required after adding a Network Service account.</span></span> <span data-ttu-id="c8498-123">而且，在網路服務帳戶下執行會限制您在相當有限的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="c8498-123">Also, running under a Network Service account restricts you to running in very limited scenarios.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8498-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c8498-124">User Action</span></span>  
 <span data-ttu-id="c8498-125">如需詳細資訊，請參閱 < [SSO 安全性建議](../core/sso-security-recommendations.md)。</span><span class="sxs-lookup"><span data-stu-id="c8498-125">For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).</span></span>