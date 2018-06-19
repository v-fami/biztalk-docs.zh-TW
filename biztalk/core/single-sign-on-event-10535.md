---
title: 單一登入： 事件 10535 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b570b0b-5c45-4be3-80c9-a2c50601b677
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f96032c8176a251090453e493487a97d9cf0fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270078"
---
# <a name="single-sign-on-event-10535"></a><span data-ttu-id="f9178-102">單一登入： 事件 10535</span><span class="sxs-lookup"><span data-stu-id="f9178-102">Single Sign-On: Event 10535</span></span>
## <a name="details"></a><span data-ttu-id="f9178-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f9178-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9178-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f9178-104">Product Name</span></span>|<span data-ttu-id="f9178-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f9178-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f9178-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f9178-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f9178-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f9178-107">Event ID</span></span>|<span data-ttu-id="f9178-108">10535</span><span class="sxs-lookup"><span data-stu-id="f9178-108">10535</span></span>|  
|<span data-ttu-id="f9178-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f9178-109">Event Source</span></span>|<span data-ttu-id="f9178-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f9178-110">ENTSSO</span></span>|  
|<span data-ttu-id="f9178-111">元件</span><span class="sxs-lookup"><span data-stu-id="f9178-111">Component</span></span>|<span data-ttu-id="f9178-112">CO</span><span class="sxs-lookup"><span data-stu-id="f9178-112">CO</span></span>|  
|<span data-ttu-id="f9178-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f9178-113">Symbolic Name</span></span>|<span data-ttu-id="f9178-114">SSO_INFO_API_AUDIT</span><span class="sxs-lookup"><span data-stu-id="f9178-114">SSO_INFO_API_AUDIT</span></span>|  
|<span data-ttu-id="f9178-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f9178-115">Message Text</span></span>|<span data-ttu-id="f9178-116">SSO AUDIT%r</span><span class="sxs-lookup"><span data-stu-id="f9178-116">SSO AUDIT%r</span></span><br /><br /> <span data-ttu-id="f9178-117">函式: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f9178-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="f9178-118">追蹤識別碼: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f9178-118">Tracking ID: %2%r</span></span><br /><br /> <span data-ttu-id="f9178-119">用戶端電腦: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f9178-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="f9178-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="f9178-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="f9178-121">應用程式名稱： %5</span><span class="sxs-lookup"><span data-stu-id="f9178-121">Application Name: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f9178-122">說明</span><span class="sxs-lookup"><span data-stu-id="f9178-122">Explanation</span></span>  
 <span data-ttu-id="f9178-123">此稽核資訊事件表示已發生事件符合使用者定義稽核層級。</span><span class="sxs-lookup"><span data-stu-id="f9178-123">This Information Audit event indicates that an event that meets the user defined audit level has occurred.</span></span> <span data-ttu-id="f9178-124">包含此事件訊息：</span><span class="sxs-lookup"><span data-stu-id="f9178-124">This event message includes:</span></span>  
  
 <span data-ttu-id="f9178-125">**函式：** 正在執行的函式</span><span class="sxs-lookup"><span data-stu-id="f9178-125">**Function:** Function being performed</span></span>  
  
 <span data-ttu-id="f9178-126">**追蹤識別碼：** 呼叫第一個 SSO 應用程式開發介面時，產生的唯一 GUID。</span><span class="sxs-lookup"><span data-stu-id="f9178-126">**Tracking ID:** Unique GUID generated when an SSO API is first called.</span></span>  
  
 <span data-ttu-id="f9178-127">**用戶端電腦：** 參予函式的用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="f9178-127">**Client Computer:** Client computer where the function originated.</span></span>  
  
 <span data-ttu-id="f9178-128">**用戶端使用者：** 叫用該函數的使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9178-128">**Client User:** The name of the user account that invoked the function.</span></span>  
  
 <span data-ttu-id="f9178-129">**應用程式名稱：** 名稱的 sso 分支機構應用程式與這個函式相關聯。</span><span class="sxs-lookup"><span data-stu-id="f9178-129">**Application Name:** Name of the SSO affiliate application associated with this function.</span></span>  
  
 <span data-ttu-id="f9178-130">這種類型的事件用於診斷問題，在開發期間疑難排解，或執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9178-130">This type of event is used for diagnosing problems during development, troubleshooting, or running of an application.</span></span> <span data-ttu-id="f9178-131">提供的資訊可以用來判斷正在進行的 SSO 應用程式開發介面呼叫。</span><span class="sxs-lookup"><span data-stu-id="f9178-131">Information provided can be used to determine the SSO API call being made.</span></span>  
  
 <span data-ttu-id="f9178-132">您可以將稽核層級為 0/1/2/3-0 表示 「 無 」，1 表示 「 低 」 會顯示錯誤只，2 代表"medium"會顯示錯誤和警告，而 3 表示 「 高 」 會顯示所有稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="f9178-132">The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f9178-133">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f9178-133">User Action</span></span>  
  
-   <span data-ttu-id="f9178-134">請檢查事件記錄檔中相關聯的事件訊息。</span><span class="sxs-lookup"><span data-stu-id="f9178-134">Check the event log for associated event messages.</span></span>  
  
 <span data-ttu-id="f9178-135">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="f9178-135">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="f9178-136">如何稽核 SSO</span><span class="sxs-lookup"><span data-stu-id="f9178-136">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="f9178-137">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="f9178-137">Using SSO</span></span>](../core/using-sso.md)