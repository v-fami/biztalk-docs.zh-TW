---
title: "單一登入： 事件 10691 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fcefb49-c068-41e9-850d-99864c0899bf
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da914bff656ff63e65cd041e57e291beea5128e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10691"></a><span data-ttu-id="1c5db-102">單一登入： 事件 10691</span><span class="sxs-lookup"><span data-stu-id="1c5db-102">Single Sign-On: Event 10691</span></span>
## <a name="details"></a><span data-ttu-id="1c5db-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c5db-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c5db-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1c5db-104">Product Name</span></span>|<span data-ttu-id="1c5db-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1c5db-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1c5db-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1c5db-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1c5db-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1c5db-107">Event ID</span></span>|<span data-ttu-id="1c5db-108">10691</span><span class="sxs-lookup"><span data-stu-id="1c5db-108">10691</span></span>|  
|<span data-ttu-id="1c5db-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1c5db-109">Event Source</span></span>|<span data-ttu-id="1c5db-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1c5db-110">ENTSSO</span></span>|  
|<span data-ttu-id="1c5db-111">元件</span><span class="sxs-lookup"><span data-stu-id="1c5db-111">Component</span></span>|<span data-ttu-id="1c5db-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1c5db-112">N\A</span></span>|  
|<span data-ttu-id="1c5db-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1c5db-113">Symbolic Name</span></span>|<span data-ttu-id="1c5db-114">SSO_ERROR_REPLAY_FILE_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="1c5db-114">SSO_ERROR_REPLAY_FILE_MISMATCH</span></span>|  
|<span data-ttu-id="1c5db-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1c5db-115">Message Text</span></span>|<span data-ttu-id="1c5db-116">在重新執行檔案中偵測到損毀。%r</span><span class="sxs-lookup"><span data-stu-id="1c5db-116">Corruption was detected in the replay file.%r</span></span><br /><br /> <span data-ttu-id="1c5db-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="1c5db-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="1c5db-118">其他資料： %2</span><span class="sxs-lookup"><span data-stu-id="1c5db-118">Additional Data: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1c5db-119">說明</span><span class="sxs-lookup"><span data-stu-id="1c5db-119">Explanation</span></span>  
 <span data-ttu-id="1c5db-120">這個錯誤事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法開啟重新執行檔案因為不相符，與對應的進度檔案。</span><span class="sxs-lookup"><span data-stu-id="1c5db-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to open the replay file because of a mismatch with the corresponding progress file.</span></span> <span data-ttu-id="1c5db-121">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一個重新執行檔案 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="1c5db-121">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="1c5db-122">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="1c5db-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="1c5db-123">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="1c5db-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1c5db-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1c5db-124">User Action</span></span>  
 <span data-ttu-id="1c5db-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1c5db-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="1c5db-126">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1c5db-126">Check System and Application event logs for associated events.</span></span>  
  
-   <span data-ttu-id="1c5db-127">刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="1c5db-127">Delete the replay file.</span></span>  
  
 <span data-ttu-id="1c5db-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="1c5db-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="1c5db-129">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="1c5db-129">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="1c5db-130">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="1c5db-130">Password Synchronization</span></span>](../core/password-synchronization2.md)