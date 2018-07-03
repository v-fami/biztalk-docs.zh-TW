---
title: 單一登入： 事件 10535 |Microsoft Docs
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
ms.openlocfilehash: 2e075adb07b42194d8ea502c4ad50d9ebd47663b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023892"
---
# <a name="single-sign-on-event-10535"></a><span data-ttu-id="70ed4-102">單一登入： 事件 10535</span><span class="sxs-lookup"><span data-stu-id="70ed4-102">Single Sign-On: Event 10535</span></span>
## <a name="details"></a><span data-ttu-id="70ed4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="70ed4-103">Details</span></span>  

|                 |                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="70ed4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="70ed4-104">Product Name</span></span>   |                                                                       <span data-ttu-id="70ed4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="70ed4-105">Enterprise Single Sign-On</span></span>                                                                       |
| <span data-ttu-id="70ed4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="70ed4-106">Product Version</span></span> |                                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                       |
|    <span data-ttu-id="70ed4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="70ed4-107">Event ID</span></span>     |                                                                                 <span data-ttu-id="70ed4-108">10535</span><span class="sxs-lookup"><span data-stu-id="70ed4-108">10535</span></span>                                                                                 |
|  <span data-ttu-id="70ed4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="70ed4-109">Event Source</span></span>   |                                                                                <span data-ttu-id="70ed4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="70ed4-110">ENTSSO</span></span>                                                                                 |
|    <span data-ttu-id="70ed4-111">元件</span><span class="sxs-lookup"><span data-stu-id="70ed4-111">Component</span></span>    |                                                                                  <span data-ttu-id="70ed4-112">CO</span><span class="sxs-lookup"><span data-stu-id="70ed4-112">CO</span></span>                                                                                   |
|  <span data-ttu-id="70ed4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="70ed4-113">Symbolic Name</span></span>  |                                                                          <span data-ttu-id="70ed4-114">SSO_INFO_API_AUDIT</span><span class="sxs-lookup"><span data-stu-id="70ed4-114">SSO_INFO_API_AUDIT</span></span>                                                                           |
|  <span data-ttu-id="70ed4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="70ed4-115">Message Text</span></span>   | <span data-ttu-id="70ed4-116">SSO AUDIT%r</span><span class="sxs-lookup"><span data-stu-id="70ed4-116">SSO AUDIT%r</span></span><br /><br /> <span data-ttu-id="70ed4-117">函式: %1 %r</span><span class="sxs-lookup"><span data-stu-id="70ed4-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="70ed4-118">追蹤識別碼: %2 %r</span><span class="sxs-lookup"><span data-stu-id="70ed4-118">Tracking ID: %2%r</span></span><br /><br /> <span data-ttu-id="70ed4-119">用戶端電腦: %3 %r</span><span class="sxs-lookup"><span data-stu-id="70ed4-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="70ed4-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="70ed4-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="70ed4-121">應用程式名稱： %5</span><span class="sxs-lookup"><span data-stu-id="70ed4-121">Application Name: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="70ed4-122">說明</span><span class="sxs-lookup"><span data-stu-id="70ed4-122">Explanation</span></span>  
 <span data-ttu-id="70ed4-123">此稽核資訊事件表示發生符合使用者定義稽核層級的事件。</span><span class="sxs-lookup"><span data-stu-id="70ed4-123">This Information Audit event indicates that an event that meets the user defined audit level has occurred.</span></span> <span data-ttu-id="70ed4-124">此事件訊息包含：</span><span class="sxs-lookup"><span data-stu-id="70ed4-124">This event message includes:</span></span>  

 <span data-ttu-id="70ed4-125">**函式：** 正在執行的函式</span><span class="sxs-lookup"><span data-stu-id="70ed4-125">**Function:** Function being performed</span></span>  

 <span data-ttu-id="70ed4-126">**追蹤識別碼：** 呼叫第一個 SSO API 時，產生的唯一 GUID。</span><span class="sxs-lookup"><span data-stu-id="70ed4-126">**Tracking ID:** Unique GUID generated when an SSO API is first called.</span></span>  

 <span data-ttu-id="70ed4-127">**用戶端電腦：** 函式的起源的用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="70ed4-127">**Client Computer:** Client computer where the function originated.</span></span>  

 <span data-ttu-id="70ed4-128">**用戶端使用者：** 叫用函式的使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="70ed4-128">**Client User:** The name of the user account that invoked the function.</span></span>  

 <span data-ttu-id="70ed4-129">**應用程式名稱：** 名稱的 SSO 分支機構應用程式，此函式相關聯。</span><span class="sxs-lookup"><span data-stu-id="70ed4-129">**Application Name:** Name of the SSO affiliate application associated with this function.</span></span>  

 <span data-ttu-id="70ed4-130">這種類型的事件用於在開發期間診斷問題、 疑難排解、 或執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="70ed4-130">This type of event is used for diagnosing problems during development, troubleshooting, or running of an application.</span></span> <span data-ttu-id="70ed4-131">提供的資訊可用來判斷正在進行的 SSO API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="70ed4-131">Information provided can be used to determine the SSO API call being made.</span></span>  

 <span data-ttu-id="70ed4-132">可以設定的稽核層級為 0/1/2/3-0 表示 「 無 」、 「 低 」 的 1 表示會顯示只記錄錯誤、 2 表示 「 中 」 會顯示錯誤和警告，和 3 表示 「 高 」 會顯示所有的稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="70ed4-132">The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.</span></span>  

## <a name="user-action"></a><span data-ttu-id="70ed4-133">使用者動作</span><span class="sxs-lookup"><span data-stu-id="70ed4-133">User Action</span></span>  

- <span data-ttu-id="70ed4-134">請檢查事件記錄檔相關聯的事件訊息。</span><span class="sxs-lookup"><span data-stu-id="70ed4-134">Check the event log for associated event messages.</span></span>  

  <span data-ttu-id="70ed4-135">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="70ed4-135">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="70ed4-136">如何稽核 SSO</span><span class="sxs-lookup"><span data-stu-id="70ed4-136">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  

- [<span data-ttu-id="70ed4-137">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="70ed4-137">Using SSO</span></span>](../core/using-sso.md)
