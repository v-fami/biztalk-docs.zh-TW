---
title: 單一登入： 事件 10544 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f476e664d50d05a57f42006ec08aa03d901e9f1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983927"
---
# <a name="single-sign-on-event-10544"></a><span data-ttu-id="dbd9b-102">單一登入： 事件 10544</span><span class="sxs-lookup"><span data-stu-id="dbd9b-102">Single Sign-On: Event 10544</span></span>
## <a name="details"></a><span data-ttu-id="dbd9b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dbd9b-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="dbd9b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dbd9b-104">Product Name</span></span>   |                 <span data-ttu-id="dbd9b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="dbd9b-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="dbd9b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="dbd9b-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="dbd9b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dbd9b-107">Event ID</span></span>     |                           <span data-ttu-id="dbd9b-108">10544</span><span class="sxs-lookup"><span data-stu-id="dbd9b-108">10544</span></span>                            |
|  <span data-ttu-id="dbd9b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="dbd9b-109">Event Source</span></span>   |                           <span data-ttu-id="dbd9b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dbd9b-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="dbd9b-111">元件</span><span class="sxs-lookup"><span data-stu-id="dbd9b-111">Component</span></span>    |                             <span data-ttu-id="dbd9b-112">CO</span><span class="sxs-lookup"><span data-stu-id="dbd9b-112">CO</span></span>                             |
|  <span data-ttu-id="dbd9b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dbd9b-113">Symbolic Name</span></span>  |                  <span data-ttu-id="dbd9b-114">SSO_WARN_TICKET_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="dbd9b-114">SSO_WARN_TICKET_EXPIRED</span></span>                   |
|  <span data-ttu-id="dbd9b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dbd9b-115">Message Text</span></span>   | <span data-ttu-id="dbd9b-116">票證已過期。%r</span><span class="sxs-lookup"><span data-stu-id="dbd9b-116">The ticket has expired.%r</span></span><br /><br /> <span data-ttu-id="dbd9b-117">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="dbd9b-117">Application Name: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="dbd9b-118">說明</span><span class="sxs-lookup"><span data-stu-id="dbd9b-118">Explanation</span></span>  
 <span data-ttu-id="dbd9b-119">這個警告事件表示應用程式票證逾時已過期。</span><span class="sxs-lookup"><span data-stu-id="dbd9b-119">This Warning event indicates that an application ticket timeout has expired.</span></span> <span data-ttu-id="dbd9b-120">您可以在系統層級和應用程式層級指定票證逾時。</span><span class="sxs-lookup"><span data-stu-id="dbd9b-120">Ticket timeout can be specified at both the system level and the application level.</span></span> <span data-ttu-id="dbd9b-121">如果已指定系統層級和應用程式層級的逾時，應用程式層級的逾時用來決定到期時間。</span><span class="sxs-lookup"><span data-stu-id="dbd9b-121">If both system level and the application level timeout are specified, the application level timeout is used to determine the expiry time.</span></span>  

## <a name="user-action"></a><span data-ttu-id="dbd9b-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dbd9b-122">User Action</span></span>  
 <span data-ttu-id="dbd9b-123">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="dbd9b-123">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="dbd9b-124">決定票證到期之前要驗證的原因。</span><span class="sxs-lookup"><span data-stu-id="dbd9b-124">Determine why the ticket expired before being validated.</span></span>  

- <span data-ttu-id="dbd9b-125">確保票證逾時值是足以上次之間贖回時間發出票證的時間。</span><span class="sxs-lookup"><span data-stu-id="dbd9b-125">Ensure that the Ticket timeout value is long enough to last between the time when the ticket is issued to the time that it is redeemed.</span></span>  

  <span data-ttu-id="dbd9b-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="dbd9b-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="dbd9b-127">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="dbd9b-127">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="dbd9b-128">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="dbd9b-128">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)
