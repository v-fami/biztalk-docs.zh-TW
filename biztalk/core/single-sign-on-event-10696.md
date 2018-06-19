---
title: 單一登入： 事件 10696 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4dff6d08-8a1f-4137-bda7-55271071da55
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1a2b704b45774e0489f9c765cee45326bf0ff59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271790"
---
# <a name="single-sign-on-event-10696"></a><span data-ttu-id="b9702-102">單一登入： 事件 10696</span><span class="sxs-lookup"><span data-stu-id="b9702-102">Single Sign-On: Event 10696</span></span>
## <a name="details"></a><span data-ttu-id="b9702-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9702-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9702-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b9702-104">Product Name</span></span>|<span data-ttu-id="b9702-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b9702-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b9702-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b9702-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b9702-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b9702-107">Event ID</span></span>|<span data-ttu-id="b9702-108">10696</span><span class="sxs-lookup"><span data-stu-id="b9702-108">10696</span></span>|  
|<span data-ttu-id="b9702-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b9702-109">Event Source</span></span>|<span data-ttu-id="b9702-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b9702-110">ENTSSO</span></span>|  
|<span data-ttu-id="b9702-111">元件</span><span class="sxs-lookup"><span data-stu-id="b9702-111">Component</span></span>|<span data-ttu-id="b9702-112">N\A</span><span class="sxs-lookup"><span data-stu-id="b9702-112">N\A</span></span>|  
|<span data-ttu-id="b9702-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b9702-113">Symbolic Name</span></span>|<span data-ttu-id="b9702-114">SSO_ERROR_PROGRESS_INCORRECT_RECORD_VERSION</span><span class="sxs-lookup"><span data-stu-id="b9702-114">SSO_ERROR_PROGRESS_INCORRECT_RECORD_VERSION</span></span>|  
|<span data-ttu-id="b9702-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b9702-115">Message Text</span></span>|<span data-ttu-id="b9702-116">進度 file.%r 中偵測到損毀</span><span class="sxs-lookup"><span data-stu-id="b9702-116">Corruption was detected in the progress file.%r</span></span><br /><br /> <span data-ttu-id="b9702-117">檔案名稱： %1</span><span class="sxs-lookup"><span data-stu-id="b9702-117">File Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9702-118">說明</span><span class="sxs-lookup"><span data-stu-id="b9702-118">Explanation</span></span>  
 <span data-ttu-id="b9702-119">這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫的連絡，但是因為損毀所以無法讀取進度檔案。</span><span class="sxs-lookup"><span data-stu-id="b9702-119">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the progress file because of corruption.</span></span> <span data-ttu-id="b9702-120">如果 SSO 無法開啟進行檔案，就會開始在第一次重新執行檔的開頭記錄。</span><span class="sxs-lookup"><span data-stu-id="b9702-120">If SSO cannot open a progress file, it will start at the beginning record of the first replay file.</span></span>  
  
 <span data-ttu-id="b9702-121">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="b9702-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="b9702-122">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="b9702-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9702-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b9702-123">User Action</span></span>  
 <span data-ttu-id="b9702-124">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b9702-124">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="b9702-125">檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b9702-125">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="b9702-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="b9702-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="b9702-127">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="b9702-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="b9702-128">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="b9702-128">Password Synchronization</span></span>](../core/password-synchronization2.md)