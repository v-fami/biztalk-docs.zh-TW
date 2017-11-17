---
title: "單一登入： 事件 10539 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a67f5719-da7c-4ae0-a6fe-ff7b653a184d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ca34f40359b518e1a52b3326dae9917ca4910e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10539"></a><span data-ttu-id="c0b99-102">單一登入： 事件 10539</span><span class="sxs-lookup"><span data-stu-id="c0b99-102">Single Sign-On: Event 10539</span></span>
## <a name="details"></a><span data-ttu-id="c0b99-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0b99-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0b99-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c0b99-104">Product Name</span></span>|<span data-ttu-id="c0b99-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c0b99-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c0b99-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c0b99-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c0b99-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c0b99-107">Event ID</span></span>|<span data-ttu-id="c0b99-108">10539</span><span class="sxs-lookup"><span data-stu-id="c0b99-108">10539</span></span>|  
|<span data-ttu-id="c0b99-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c0b99-109">Event Source</span></span>|<span data-ttu-id="c0b99-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c0b99-110">ENTSSO</span></span>|  
|<span data-ttu-id="c0b99-111">元件</span><span class="sxs-lookup"><span data-stu-id="c0b99-111">Component</span></span>|<span data-ttu-id="c0b99-112">CO</span><span class="sxs-lookup"><span data-stu-id="c0b99-112">CO</span></span>|  
|<span data-ttu-id="c0b99-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c0b99-113">Symbolic Name</span></span>|<span data-ttu-id="c0b99-114">SSO_WARN_SSO_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="c0b99-114">SSO_WARN_SSO_TICKETS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="c0b99-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c0b99-115">Message Text</span></span>|<span data-ttu-id="c0b99-116">未啟用 SSO 系統的票證。</span><span class="sxs-lookup"><span data-stu-id="c0b99-116">Tickets are not enabled for the SSO system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c0b99-117">說明</span><span class="sxs-lookup"><span data-stu-id="c0b99-117">Explanation</span></span>  
 <span data-ttu-id="c0b99-118">這個警告事件表示未啟用 使用 SSO 票證。</span><span class="sxs-lookup"><span data-stu-id="c0b99-118">This Warning event indicates that the use of SSO tickets is not enabled.</span></span> <span data-ttu-id="c0b99-119">允許使用 SSO 票證是 SSO 系統的選用功能。</span><span class="sxs-lookup"><span data-stu-id="c0b99-119">Allowing the use of SSO tickets is an optional feature of the SSO system.</span></span> <span data-ttu-id="c0b99-120">SSO 系統上尚未啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="c0b99-120">This feature has not been enabled on your SSO system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c0b99-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c0b99-121">User Action</span></span>  
 <span data-ttu-id="c0b99-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c0b99-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="c0b99-123">請連絡您的 SSO 系統管理員，才能啟用 SSO 系統的票證。</span><span class="sxs-lookup"><span data-stu-id="c0b99-123">Contact your SSO Administrator to enable tickets for the SSO system.</span></span> <span data-ttu-id="c0b99-124">這可以使用 SSO 管理工具 （GUI 或命令列）。</span><span class="sxs-lookup"><span data-stu-id="c0b99-124">This can be done using the SSO administration tools (GUI or command line).</span></span>  
  
 <span data-ttu-id="c0b99-125">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="c0b99-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c0b99-126">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="c0b99-126">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)  
  
-   [<span data-ttu-id="c0b99-127">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="c0b99-127">Using SSO</span></span>](../core/using-sso.md)