---
title: "單一登入： 事件 10585 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51c55ada-1ee3-4626-b044-9c537d11f0d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b4781628121edad8904130e546038698de03161
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10585"></a><span data-ttu-id="74d65-102">單一登入： 事件 10585</span><span class="sxs-lookup"><span data-stu-id="74d65-102">Single Sign-On: Event 10585</span></span>
## <a name="details"></a><span data-ttu-id="74d65-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="74d65-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74d65-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="74d65-104">Product Name</span></span>|<span data-ttu-id="74d65-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="74d65-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="74d65-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="74d65-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="74d65-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="74d65-107">Event ID</span></span>|<span data-ttu-id="74d65-108">10585</span><span class="sxs-lookup"><span data-stu-id="74d65-108">10585</span></span>|  
|<span data-ttu-id="74d65-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="74d65-109">Event Source</span></span>|<span data-ttu-id="74d65-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="74d65-110">ENTSSO</span></span>|  
|<span data-ttu-id="74d65-111">元件</span><span class="sxs-lookup"><span data-stu-id="74d65-111">Component</span></span>|<span data-ttu-id="74d65-112">不適用</span><span class="sxs-lookup"><span data-stu-id="74d65-112">N/A</span></span>|  
|<span data-ttu-id="74d65-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="74d65-113">Symbolic Name</span></span>|<span data-ttu-id="74d65-114">SSO_WARN_EXPIRED_TICKET_REDEEMED</span><span class="sxs-lookup"><span data-stu-id="74d65-114">SSO_WARN_EXPIRED_TICKET_REDEEMED</span></span>|  
|<span data-ttu-id="74d65-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="74d65-115">Message Text</span></span>|<span data-ttu-id="74d65-116">票證逾時期限過期後，就會贖回票證。</span><span class="sxs-lookup"><span data-stu-id="74d65-116">A ticket is being redeemed after the ticket time-out period has expired.</span></span> <span data-ttu-id="74d65-117">這是允許的，因為已停用此應用程式的票證逾時。%r</span><span class="sxs-lookup"><span data-stu-id="74d65-117">This is allowed because the ticket time-out is disabled for this application.%r</span></span><br /><br /> <span data-ttu-id="74d65-118">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="74d65-118">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74d65-119">說明</span><span class="sxs-lookup"><span data-stu-id="74d65-119">Explanation</span></span>  
 <span data-ttu-id="74d65-120">票證逾時可啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="74d65-120">Ticket time-out can be enabled or disabled.</span></span> <span data-ttu-id="74d65-121">在此案例中，即使票證逾時期限過期也會贖回票證，因為逾時已停用。</span><span class="sxs-lookup"><span data-stu-id="74d65-121">In this case a ticket is being redeemed even though its time-out period has expired, because the time-out is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74d65-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="74d65-122">User Action</span></span>  
 <span data-ttu-id="74d65-123">如果逾時為停用，則使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="74d65-123">If the time-out was supposed to be disabled, no user action is required.</span></span> <span data-ttu-id="74d65-124">但是，如果您不知道此特定應用程式已停用其逾時，請立即檢查應用程式以確定您要允許停用。</span><span class="sxs-lookup"><span data-stu-id="74d65-124">However, if you were not aware that this particular application had its time-out disabled, check the application immediately to be sure you want to allow it.</span></span>