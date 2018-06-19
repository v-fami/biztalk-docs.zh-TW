---
title: 單一登入： 事件 10545 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64cb10ceef5827f9c0b0aab5d9810db061af8a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270646"
---
# <a name="single-sign-on-event-10545"></a><span data-ttu-id="d39a5-102">單一登入： 事件 10545</span><span class="sxs-lookup"><span data-stu-id="d39a5-102">Single Sign-On: Event 10545</span></span>
## <a name="details"></a><span data-ttu-id="d39a5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d39a5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d39a5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d39a5-104">Product Name</span></span>|<span data-ttu-id="d39a5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d39a5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d39a5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d39a5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d39a5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d39a5-107">Event ID</span></span>|<span data-ttu-id="d39a5-108">10545</span><span class="sxs-lookup"><span data-stu-id="d39a5-108">10545</span></span>|  
|<span data-ttu-id="d39a5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d39a5-109">Event Source</span></span>|<span data-ttu-id="d39a5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d39a5-110">ENTSSO</span></span>|  
|<span data-ttu-id="d39a5-111">元件</span><span class="sxs-lookup"><span data-stu-id="d39a5-111">Component</span></span>|<span data-ttu-id="d39a5-112">CO</span><span class="sxs-lookup"><span data-stu-id="d39a5-112">CO</span></span>|  
|<span data-ttu-id="d39a5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d39a5-113">Symbolic Name</span></span>|<span data-ttu-id="d39a5-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="d39a5-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="d39a5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d39a5-115">Message Text</span></span>|<span data-ttu-id="d39a5-116">未啟用 SSO 系統的票證。</span><span class="sxs-lookup"><span data-stu-id="d39a5-116">Tickets are not enabled for the SSO system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d39a5-117">說明</span><span class="sxs-lookup"><span data-stu-id="d39a5-117">Explanation</span></span>  
 <span data-ttu-id="d39a5-118">這個警告事件表示不 SSO 系統啟用票證。</span><span class="sxs-lookup"><span data-stu-id="d39a5-118">This Warning event indicates that tickets are not enabled for the SSO System.</span></span> <span data-ttu-id="d39a5-119">如果在系統層級停用票證，票證無法使用分支機構應用程式層級是。</span><span class="sxs-lookup"><span data-stu-id="d39a5-119">If ticketing is disabled at the system level, ticketing cannot be used at the Affiliate Application level either.</span></span> <span data-ttu-id="d39a5-120">可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。</span><span class="sxs-lookup"><span data-stu-id="d39a5-120">It is possible to enable tickets at the system level and disable it at the Affiliate Application level.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d39a5-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d39a5-121">User Action</span></span>  
 <span data-ttu-id="d39a5-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d39a5-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="d39a5-123">在中啟用票證的 SSO 系統層級。</span><span class="sxs-lookup"><span data-stu-id="d39a5-123">Enable tickets at the SSO System level.</span></span>  
  
 <span data-ttu-id="d39a5-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="d39a5-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d39a5-125">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="d39a5-125">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="d39a5-126">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="d39a5-126">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)