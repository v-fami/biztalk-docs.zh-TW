---
title: 單一登入： 事件 10726 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12fbac2d-30ca-4f4c-989b-d770b0f623d9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5784ba85018ab6d02393ca3f684a08b21718ec47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22272062"
---
# <a name="single-sign-on-event-10726"></a><span data-ttu-id="fba0b-102">單一登入： 事件 10726</span><span class="sxs-lookup"><span data-stu-id="fba0b-102">Single Sign-On: Event 10726</span></span>
## <a name="details"></a><span data-ttu-id="fba0b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fba0b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fba0b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fba0b-104">Product Name</span></span>|<span data-ttu-id="fba0b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fba0b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fba0b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fba0b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fba0b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fba0b-107">Event ID</span></span>|<span data-ttu-id="fba0b-108">10726</span><span class="sxs-lookup"><span data-stu-id="fba0b-108">10726</span></span>|  
|<span data-ttu-id="fba0b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fba0b-109">Event Source</span></span>|<span data-ttu-id="fba0b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fba0b-110">ENTSSO</span></span>|  
|<span data-ttu-id="fba0b-111">元件</span><span class="sxs-lookup"><span data-stu-id="fba0b-111">Component</span></span>|<span data-ttu-id="fba0b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fba0b-112">N\A</span></span>|  
|<span data-ttu-id="fba0b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fba0b-113">Symbolic Name</span></span>|<span data-ttu-id="fba0b-114">SSO_ERROR_REPLAY_CORRUPTION</span><span class="sxs-lookup"><span data-stu-id="fba0b-114">SSO_ERROR_REPLAY_CORRUPTION</span></span>|  
|<span data-ttu-id="fba0b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fba0b-115">Message Text</span></span>|<span data-ttu-id="fba0b-116">重新執行或進度 file.%r 中偵測到損毀</span><span class="sxs-lookup"><span data-stu-id="fba0b-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="fba0b-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fba0b-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="fba0b-118">其他資料: %2 %r</span><span class="sxs-lookup"><span data-stu-id="fba0b-118">Additional Data: %2%r</span></span><br /><br /> <span data-ttu-id="fba0b-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="fba0b-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fba0b-120">說明</span><span class="sxs-lookup"><span data-stu-id="fba0b-120">Explanation</span></span>  
 <span data-ttu-id="fba0b-121">這個錯誤事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法讀取的重新執行檔案，因為已損毀。</span><span class="sxs-lookup"><span data-stu-id="fba0b-121">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="fba0b-122">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一個重新執行檔案 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="fba0b-122">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="fba0b-123">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="fba0b-123">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="fba0b-124">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="fba0b-124">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fba0b-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fba0b-125">User Action</span></span>  
 <span data-ttu-id="fba0b-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fba0b-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="fba0b-127">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fba0b-127">Check System and Application event logs for associated events.</span></span>  
  
-   <span data-ttu-id="fba0b-128">刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="fba0b-128">Delete the replay file.</span></span>  
  
 <span data-ttu-id="fba0b-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="fba0b-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="fba0b-130">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="fba0b-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="fba0b-131">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="fba0b-131">Password Synchronization</span></span>](../core/password-synchronization2.md)