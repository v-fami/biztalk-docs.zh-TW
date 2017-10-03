---
title: "單一登入： 事件 10689 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79e4e31f-18e4-4f52-9466-18e58842942f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af9910ee07744c76a6281f619fd7fff89a02f9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10689"></a><span data-ttu-id="58715-102">單一登入： 事件 10689</span><span class="sxs-lookup"><span data-stu-id="58715-102">Single Sign-On: Event 10689</span></span>
## <a name="details"></a><span data-ttu-id="58715-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58715-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58715-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="58715-104">Product Name</span></span>|<span data-ttu-id="58715-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="58715-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="58715-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="58715-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="58715-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="58715-107">Event ID</span></span>|<span data-ttu-id="58715-108">10689</span><span class="sxs-lookup"><span data-stu-id="58715-108">10689</span></span>|  
|<span data-ttu-id="58715-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="58715-109">Event Source</span></span>|<span data-ttu-id="58715-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="58715-110">ENTSSO</span></span>|  
|<span data-ttu-id="58715-111">元件</span><span class="sxs-lookup"><span data-stu-id="58715-111">Component</span></span>|<span data-ttu-id="58715-112">N\A</span><span class="sxs-lookup"><span data-stu-id="58715-112">N\A</span></span>|  
|<span data-ttu-id="58715-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="58715-113">Symbolic Name</span></span>|<span data-ttu-id="58715-114">SSO_ERROR_REPLAY_INCORRECT_RECORD_VERSION</span><span class="sxs-lookup"><span data-stu-id="58715-114">SSO_ERROR_REPLAY_INCORRECT_RECORD_VERSION</span></span>|  
|<span data-ttu-id="58715-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="58715-115">Message Text</span></span>|<span data-ttu-id="58715-116">在重新執行檔案中偵測到損毀。%r</span><span class="sxs-lookup"><span data-stu-id="58715-116">Corruption was detected in the replay file.%r</span></span><br /><br /> <span data-ttu-id="58715-117">重新執行檔案： %1</span><span class="sxs-lookup"><span data-stu-id="58715-117">Replay File: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58715-118">說明</span><span class="sxs-lookup"><span data-stu-id="58715-118">Explanation</span></span>  
 <span data-ttu-id="58715-119">這個錯誤事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法讀取的重新執行檔案，因為已損毀。</span><span class="sxs-lookup"><span data-stu-id="58715-119">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="58715-120">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一個重新執行檔案 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="58715-120">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="58715-121">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="58715-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="58715-122">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="58715-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58715-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="58715-123">User Action</span></span>  
 <span data-ttu-id="58715-124">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="58715-124">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="58715-125">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="58715-125">Check System and Application event logs for associated events.</span></span>  
  
-   <span data-ttu-id="58715-126">刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="58715-126">Delete the replay file.</span></span>  
  
 <span data-ttu-id="58715-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="58715-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="58715-128">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="58715-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="58715-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="58715-129">Password Synchronization</span></span>](../core/password-synchronization2.md)