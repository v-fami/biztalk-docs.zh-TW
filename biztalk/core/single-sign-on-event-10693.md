---
title: "單一登入： 事件 10693 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672bac7d-0ccc-4a42-a49d-57e387f4cf3a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f653af187e7ca36f45418e724fb73a2c6b1b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10693"></a><span data-ttu-id="47f3c-102">單一登入： 事件 10693</span><span class="sxs-lookup"><span data-stu-id="47f3c-102">Single Sign-On: Event 10693</span></span>
## <a name="details"></a><span data-ttu-id="47f3c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47f3c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47f3c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="47f3c-104">Product Name</span></span>|<span data-ttu-id="47f3c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="47f3c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="47f3c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="47f3c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="47f3c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="47f3c-107">Event ID</span></span>|<span data-ttu-id="47f3c-108">10693</span><span class="sxs-lookup"><span data-stu-id="47f3c-108">10693</span></span>|  
|<span data-ttu-id="47f3c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="47f3c-109">Event Source</span></span>|<span data-ttu-id="47f3c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="47f3c-110">ENTSSO</span></span>|  
|<span data-ttu-id="47f3c-111">元件</span><span class="sxs-lookup"><span data-stu-id="47f3c-111">Component</span></span>|<span data-ttu-id="47f3c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="47f3c-112">N\A</span></span>|  
|<span data-ttu-id="47f3c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="47f3c-113">Symbolic Name</span></span>|<span data-ttu-id="47f3c-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span><span class="sxs-lookup"><span data-stu-id="47f3c-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span></span>|  
|<span data-ttu-id="47f3c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="47f3c-115">Message Text</span></span>|<span data-ttu-id="47f3c-116">無法建立重新執行或進度 file.%r</span><span class="sxs-lookup"><span data-stu-id="47f3c-116">Could not create the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="47f3c-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="47f3c-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="47f3c-118">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="47f3c-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="47f3c-119">說明</span><span class="sxs-lookup"><span data-stu-id="47f3c-119">Explanation</span></span>  
 <span data-ttu-id="47f3c-120">這個警告事件表示 SSO 已無法連線到 SSO 資料庫已遺失時建立重新執行和/或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="47f3c-120">This Warning event indicates that SSO was unable to create a replay and\or progress file when connection to the SSO database was lost.</span></span>  
  
 <span data-ttu-id="47f3c-121">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="47f3c-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="47f3c-122">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="47f3c-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="47f3c-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="47f3c-123">User Action</span></span>  
 <span data-ttu-id="47f3c-124">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="47f3c-124">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="47f3c-125">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="47f3c-125">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="47f3c-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="47f3c-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="47f3c-127">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="47f3c-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="47f3c-128">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="47f3c-128">Password Synchronization</span></span>](../core/password-synchronization2.md)