---
title: "單一登入： 事件 10741 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b6b093-d136-498f-a3b5-c413150da956
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52ad76e20937bfa4af1dbec6d71ba59003874435
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10741"></a><span data-ttu-id="051b5-102">單一登入： 事件 10741</span><span class="sxs-lookup"><span data-stu-id="051b5-102">Single Sign-On: Event 10741</span></span>
## <a name="details"></a><span data-ttu-id="051b5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="051b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="051b5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="051b5-104">Product Name</span></span>|<span data-ttu-id="051b5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="051b5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="051b5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="051b5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="051b5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="051b5-107">Event ID</span></span>|<span data-ttu-id="051b5-108">10741</span><span class="sxs-lookup"><span data-stu-id="051b5-108">10741</span></span>|  
|<span data-ttu-id="051b5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="051b5-109">Event Source</span></span>|<span data-ttu-id="051b5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="051b5-110">ENTSSO</span></span>|  
|<span data-ttu-id="051b5-111">元件</span><span class="sxs-lookup"><span data-stu-id="051b5-111">Component</span></span>|<span data-ttu-id="051b5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="051b5-112">N\A</span></span>|  
|<span data-ttu-id="051b5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="051b5-113">Symbolic Name</span></span>|<span data-ttu-id="051b5-114">SSO_WARN_SAVING_REPLAY_FILE</span><span class="sxs-lookup"><span data-stu-id="051b5-114">SSO_WARN_SAVING_REPLAY_FILE</span></span>|  
|<span data-ttu-id="051b5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="051b5-115">Message Text</span></span>|<span data-ttu-id="051b5-116">正在儲存重新執行或進度 file.%r</span><span class="sxs-lookup"><span data-stu-id="051b5-116">Saving replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="051b5-117">已儲存的檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="051b5-117">Saved File: %1%r</span></span><br /><br /> <span data-ttu-id="051b5-118">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="051b5-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="051b5-119">說明</span><span class="sxs-lookup"><span data-stu-id="051b5-119">Explanation</span></span>  
 <span data-ttu-id="051b5-120">這個警告事件表示 SSO 已儲存重新執行或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="051b5-120">This Warning event indicates that SSO is saving a replay or progress file.</span></span>  
  
 <span data-ttu-id="051b5-121">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="051b5-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="051b5-122">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="051b5-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="051b5-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="051b5-123">User Action</span></span>  
  
-   <span data-ttu-id="051b5-124">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="051b5-124">No user action is necessary.</span></span>  
  
 <span data-ttu-id="051b5-125">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="051b5-125">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="051b5-126">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="051b5-126">Password Synchronization</span></span>](../core/password-synchronization2.md)