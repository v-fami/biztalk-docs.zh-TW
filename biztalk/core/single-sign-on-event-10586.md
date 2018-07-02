---
title: 單一登入： 事件 10586 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7d480e9-dc34-44ac-9272-0caf80237bd9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b353c5d9fb569da7bcc35927e31ce5c3e68ae11
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978869"
---
# <a name="single-sign-on-event-10586"></a><span data-ttu-id="90ffd-102">單一登入： 事件 10586</span><span class="sxs-lookup"><span data-stu-id="90ffd-102">Single Sign-On: Event 10586</span></span>
## <a name="details"></a><span data-ttu-id="90ffd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="90ffd-103">Details</span></span>  
  
|                 |                                                             |
|-----------------|-------------------------------------------------------------|
|  <span data-ttu-id="90ffd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="90ffd-104">Product Name</span></span>   |                  <span data-ttu-id="90ffd-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="90ffd-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="90ffd-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="90ffd-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]  |
|    <span data-ttu-id="90ffd-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="90ffd-107">Event ID</span></span>     |                            <span data-ttu-id="90ffd-108">10586</span><span class="sxs-lookup"><span data-stu-id="90ffd-108">10586</span></span>                            |
|  <span data-ttu-id="90ffd-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="90ffd-109">Event Source</span></span>   |                           <span data-ttu-id="90ffd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="90ffd-110">ENTSSO</span></span>                            |
|    <span data-ttu-id="90ffd-111">元件</span><span class="sxs-lookup"><span data-stu-id="90ffd-111">Component</span></span>    |                             <span data-ttu-id="90ffd-112">不適用</span><span class="sxs-lookup"><span data-stu-id="90ffd-112">N/A</span></span>                             |
|  <span data-ttu-id="90ffd-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="90ffd-113">Symbolic Name</span></span>  |                   <span data-ttu-id="90ffd-114">SSO_WARN_CRED_CACHE_OFF</span><span class="sxs-lookup"><span data-stu-id="90ffd-114">SSO_WARN_CRED_CACHE_OFF</span></span>                   |
|  <span data-ttu-id="90ffd-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="90ffd-115">Message Text</span></span>   | <span data-ttu-id="90ffd-116">已停用這部 SSO 伺服器的認證快取。</span><span class="sxs-lookup"><span data-stu-id="90ffd-116">The credential cache has been disabled for this SSO server.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="90ffd-117">說明</span><span class="sxs-lookup"><span data-stu-id="90ffd-117">Explanation</span></span>  
 <span data-ttu-id="90ffd-118">認證快取，通常會啟用，已停用。</span><span class="sxs-lookup"><span data-stu-id="90ffd-118">The credential cache, which is generally enabled, has been disabled.</span></span> <span data-ttu-id="90ffd-119">只有系統管理員可以啟用或停用認證快取。</span><span class="sxs-lookup"><span data-stu-id="90ffd-119">Only a system administrator can enable or disable the credential cache.</span></span> <span data-ttu-id="90ffd-120">停用認證快取將有時可能會導致較新的認證，從 ENTSSO 系統中，雖然它會降低效能。</span><span class="sxs-lookup"><span data-stu-id="90ffd-120">Disabling the credential cache will sometimes result in more current credentials from the ENTSSO system, although it could slow down peformance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="90ffd-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="90ffd-121">User Action</span></span>  
 <span data-ttu-id="90ffd-122">若要重新啟用認證快取，請參閱 Afflilate 應用程式屬性的表格[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="90ffd-122">To re-enable the credential cache, see the Afflilate Application Properties table in [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>