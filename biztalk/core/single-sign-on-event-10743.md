---
title: "單一登入： 事件 10743 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2908bc9-1fac-4ab9-869f-0c5512864da4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8368b39ff73307e36a4789d85c9771657bdf8e26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10743"></a><span data-ttu-id="a4548-102">單一登入： 事件 10743</span><span class="sxs-lookup"><span data-stu-id="a4548-102">Single Sign-On: Event 10743</span></span>
## <a name="details"></a><span data-ttu-id="a4548-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4548-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4548-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a4548-104">Product Name</span></span>|<span data-ttu-id="a4548-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a4548-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a4548-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a4548-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a4548-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4548-107">Event ID</span></span>|<span data-ttu-id="a4548-108">10743</span><span class="sxs-lookup"><span data-stu-id="a4548-108">10743</span></span>|  
|<span data-ttu-id="a4548-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a4548-109">Event Source</span></span>|<span data-ttu-id="a4548-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a4548-110">ENTSSO</span></span>|  
|<span data-ttu-id="a4548-111">元件</span><span class="sxs-lookup"><span data-stu-id="a4548-111">Component</span></span>|<span data-ttu-id="a4548-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a4548-112">N\A</span></span>|  
|<span data-ttu-id="a4548-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a4548-113">Symbolic Name</span></span>|<span data-ttu-id="a4548-114">SSO_ERROR_REPLAY_STOPPED</span><span class="sxs-lookup"><span data-stu-id="a4548-114">SSO_ERROR_REPLAY_STOPPED</span></span>|  
|<span data-ttu-id="a4548-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a4548-115">Message Text</span></span>|<span data-ttu-id="a4548-116">由於 errors.%r 停止重新執行預存外部密碼變更</span><span class="sxs-lookup"><span data-stu-id="a4548-116">Replay of stored external password changes stopped due to errors.%r</span></span><br /><br /> <span data-ttu-id="a4548-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a4548-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="a4548-118">其他資料: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a4548-118">Additional Data: %2%r</span></span><br /><br /> <span data-ttu-id="a4548-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="a4548-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4548-120">說明</span><span class="sxs-lookup"><span data-stu-id="a4548-120">Explanation</span></span>  
 <span data-ttu-id="a4548-121">這個錯誤事件表示該重新執行預存外部密碼變更因為錯誤而停止。</span><span class="sxs-lookup"><span data-stu-id="a4548-121">This Error event indicates that replay of stored external password changes stopped due to errors.</span></span>  
  
 <span data-ttu-id="a4548-122">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="a4548-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="a4548-123">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="a4548-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4548-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a4548-124">User Action</span></span>  
 <span data-ttu-id="a4548-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a4548-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="a4548-126">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4548-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="a4548-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="a4548-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="a4548-128">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="a4548-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="a4548-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="a4548-129">Password Synchronization</span></span>](../core/password-synchronization2.md)