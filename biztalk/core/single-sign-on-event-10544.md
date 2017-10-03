---
title: "單一登入： 事件 10544 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1a01cda4272e2851f929c35fd2b767c321a9dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10544"></a><span data-ttu-id="692b6-102">單一登入： 事件 10544</span><span class="sxs-lookup"><span data-stu-id="692b6-102">Single Sign-On: Event 10544</span></span>
## <a name="details"></a><span data-ttu-id="692b6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="692b6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="692b6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="692b6-104">Product Name</span></span>|<span data-ttu-id="692b6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="692b6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="692b6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="692b6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="692b6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="692b6-107">Event ID</span></span>|<span data-ttu-id="692b6-108">10544</span><span class="sxs-lookup"><span data-stu-id="692b6-108">10544</span></span>|  
|<span data-ttu-id="692b6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="692b6-109">Event Source</span></span>|<span data-ttu-id="692b6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="692b6-110">ENTSSO</span></span>|  
|<span data-ttu-id="692b6-111">元件</span><span class="sxs-lookup"><span data-stu-id="692b6-111">Component</span></span>|<span data-ttu-id="692b6-112">CO</span><span class="sxs-lookup"><span data-stu-id="692b6-112">CO</span></span>|  
|<span data-ttu-id="692b6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="692b6-113">Symbolic Name</span></span>|<span data-ttu-id="692b6-114">SSO_WARN_TICKET_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="692b6-114">SSO_WARN_TICKET_EXPIRED</span></span>|  
|<span data-ttu-id="692b6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="692b6-115">Message Text</span></span>|<span data-ttu-id="692b6-116">票證已過期。%r</span><span class="sxs-lookup"><span data-stu-id="692b6-116">The ticket has expired.%r</span></span><br /><br /> <span data-ttu-id="692b6-117">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="692b6-117">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="692b6-118">說明</span><span class="sxs-lookup"><span data-stu-id="692b6-118">Explanation</span></span>  
 <span data-ttu-id="692b6-119">這個警告事件表示應用程式票證逾時已過期。</span><span class="sxs-lookup"><span data-stu-id="692b6-119">This Warning event indicates that an application ticket timeout has expired.</span></span> <span data-ttu-id="692b6-120">您可以在系統層級和應用程式層級指定票證逾時。</span><span class="sxs-lookup"><span data-stu-id="692b6-120">Ticket timeout can be specified at both the system level and the application level.</span></span> <span data-ttu-id="692b6-121">如果未指定系統層級和應用程式層級的逾時，應用程式層級的逾時用來決定到期時間。</span><span class="sxs-lookup"><span data-stu-id="692b6-121">If both system level and the application level timeout are specified, the application level timeout is used to determine the expiry time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="692b6-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="692b6-122">User Action</span></span>  
 <span data-ttu-id="692b6-123">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="692b6-123">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="692b6-124">決定票證過期之前要驗證的原因。</span><span class="sxs-lookup"><span data-stu-id="692b6-124">Determine why the ticket expired before being validated.</span></span>  
  
-   <span data-ttu-id="692b6-125">請確認時間長度仍足以上次票證發給當贖回票證的時間的時間之間的票證逾時值。</span><span class="sxs-lookup"><span data-stu-id="692b6-125">Ensure that the Ticket timeout value is long enough to last between the time when the ticket is issued to the time that it is redeemed.</span></span>  
  
 <span data-ttu-id="692b6-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="692b6-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="692b6-127">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="692b6-127">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="692b6-128">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="692b6-128">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)