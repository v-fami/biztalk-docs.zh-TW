---
title: 單一登入： 事件 10536 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d493a45b-c4ed-40fc-8803-b3ca12f9795b
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 273533009d68c36d15f08b7ed106a3e1f7a1b380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271230"
---
# <a name="single-sign-on-event-10536"></a><span data-ttu-id="f10d2-102">單一登入： 事件 10536</span><span class="sxs-lookup"><span data-stu-id="f10d2-102">Single Sign-On: Event 10536</span></span>
## <a name="details"></a><span data-ttu-id="f10d2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f10d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f10d2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f10d2-104">Product Name</span></span>|<span data-ttu-id="f10d2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f10d2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f10d2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f10d2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f10d2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f10d2-107">Event ID</span></span>|<span data-ttu-id="f10d2-108">10536</span><span class="sxs-lookup"><span data-stu-id="f10d2-108">10536</span></span>|  
|<span data-ttu-id="f10d2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f10d2-109">Event Source</span></span>|<span data-ttu-id="f10d2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f10d2-110">ENTSSO</span></span>|  
|<span data-ttu-id="f10d2-111">元件</span><span class="sxs-lookup"><span data-stu-id="f10d2-111">Component</span></span>|<span data-ttu-id="f10d2-112">CO</span><span class="sxs-lookup"><span data-stu-id="f10d2-112">CO</span></span>|  
|<span data-ttu-id="f10d2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f10d2-113">Symbolic Name</span></span>|<span data-ttu-id="f10d2-114">SSO_WARN_API_AUDIT</span><span class="sxs-lookup"><span data-stu-id="f10d2-114">SSO_WARN_API_AUDIT</span></span>|  
|<span data-ttu-id="f10d2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f10d2-115">Message Text</span></span>|<span data-ttu-id="f10d2-116">SSO AUDIT%r</span><span class="sxs-lookup"><span data-stu-id="f10d2-116">SSO AUDIT%r</span></span><br /><br /> <span data-ttu-id="f10d2-117">函式: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f10d2-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="f10d2-118">追蹤識別碼: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f10d2-118">Tracking ID: %2%r</span></span><br /><br /> <span data-ttu-id="f10d2-119">用戶端電腦: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f10d2-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="f10d2-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="f10d2-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="f10d2-121">應用程式名稱: %5 %r</span><span class="sxs-lookup"><span data-stu-id="f10d2-121">Application Name: %5%r</span></span><br /><br /> <span data-ttu-id="f10d2-122">錯誤碼： %6</span><span class="sxs-lookup"><span data-stu-id="f10d2-122">Error Code: %6</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f10d2-123">說明</span><span class="sxs-lookup"><span data-stu-id="f10d2-123">Explanation</span></span>  
 <span data-ttu-id="f10d2-124">此稽核警告事件表示已發生事件符合使用者定義稽核層級。</span><span class="sxs-lookup"><span data-stu-id="f10d2-124">This Warning Audit event indicates that an event that meets the user defined audit level has occurred.</span></span> <span data-ttu-id="f10d2-125">包含此事件訊息：</span><span class="sxs-lookup"><span data-stu-id="f10d2-125">This event message includes:</span></span>  
  
 <span data-ttu-id="f10d2-126">**函式：** 正在執行的函式</span><span class="sxs-lookup"><span data-stu-id="f10d2-126">**Function:** Function being performed</span></span>  
  
 <span data-ttu-id="f10d2-127">**追蹤識別碼：** 呼叫第一個 SSO 應用程式開發介面時，產生的唯一 GUID。</span><span class="sxs-lookup"><span data-stu-id="f10d2-127">**Tracking ID:** Unique GUID generated when an SSO API is first called.</span></span>  
  
 <span data-ttu-id="f10d2-128">**用戶端電腦：** 參予函式的用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="f10d2-128">**Client Computer:** Client computer where the function originated.</span></span>  
  
 <span data-ttu-id="f10d2-129">**用戶端使用者：** 叫用該函數的使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="f10d2-129">**Client User:** The name of the user account that invoked the function.</span></span>  
  
 <span data-ttu-id="f10d2-130">**應用程式名稱：** 名稱的 sso 分支機構應用程式與這個函式相關聯。</span><span class="sxs-lookup"><span data-stu-id="f10d2-130">**Application Name:** Name of the SSO affiliate application associated with this function.</span></span>  
  
 <span data-ttu-id="f10d2-131">**錯誤碼：** 唯一的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="f10d2-131">**Error Code:** Unique error identifier.</span></span>  
  
 <span data-ttu-id="f10d2-132">這種類型的事件用於診斷問題，在開發期間疑難排解，或執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="f10d2-132">This type of event is used for diagnosing problems during development, troubleshooting, or running of an application.</span></span> <span data-ttu-id="f10d2-133">提供的資訊可以用來判斷正在進行的 SSO 應用程式開發介面呼叫。</span><span class="sxs-lookup"><span data-stu-id="f10d2-133">Information provided can be used to determine the SSO API call being made.</span></span>  
  
 <span data-ttu-id="f10d2-134">您可以將稽核層級為 0/1/2/3-0 表示 「 無 」，1 表示 「 低 」 會顯示錯誤只，2 代表"medium"會顯示錯誤和警告，而 3 表示 「 高 」 會顯示所有稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="f10d2-134">The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f10d2-135">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f10d2-135">User Action</span></span>  
  
-   <span data-ttu-id="f10d2-136">請檢查事件記錄檔中相關聯的事件訊息。</span><span class="sxs-lookup"><span data-stu-id="f10d2-136">Check the event log for associated event messages.</span></span>  
  
 <span data-ttu-id="f10d2-137">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="f10d2-137">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="f10d2-138">如何稽核 SSO</span><span class="sxs-lookup"><span data-stu-id="f10d2-138">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="f10d2-139">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="f10d2-139">Using SSO</span></span>](../core/using-sso.md)