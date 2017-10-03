---
title: "單一登入： 事件 10698 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f467934d-fef5-4962-a341-18f272d84108
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ca4d65927e7e9d01f7c73eb64a19bc613496f5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10698"></a><span data-ttu-id="0f544-102">單一登入： 事件 10698</span><span class="sxs-lookup"><span data-stu-id="0f544-102">Single Sign-On: Event 10698</span></span>
## <a name="details"></a><span data-ttu-id="0f544-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f544-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f544-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0f544-104">Product Name</span></span>|<span data-ttu-id="0f544-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0f544-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="0f544-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0f544-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="0f544-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0f544-107">Event ID</span></span>|<span data-ttu-id="0f544-108">10698</span><span class="sxs-lookup"><span data-stu-id="0f544-108">10698</span></span>|  
|<span data-ttu-id="0f544-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0f544-109">Event Source</span></span>|<span data-ttu-id="0f544-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0f544-110">ENTSSO</span></span>|  
|<span data-ttu-id="0f544-111">元件</span><span class="sxs-lookup"><span data-stu-id="0f544-111">Component</span></span>|<span data-ttu-id="0f544-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0f544-112">N\A</span></span>|  
|<span data-ttu-id="0f544-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0f544-113">Symbolic Name</span></span>|<span data-ttu-id="0f544-114">SSO_INFO_REPLAY_FILE_DELETED</span><span class="sxs-lookup"><span data-stu-id="0f544-114">SSO_INFO_REPLAY_FILE_DELETED</span></span>|  
|<span data-ttu-id="0f544-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0f544-115">Message Text</span></span>|<span data-ttu-id="0f544-116">重新執行或進度檔案已刪除。%r</span><span class="sxs-lookup"><span data-stu-id="0f544-116">The replay or progress file was deleted.%r</span></span><br /><br /> <span data-ttu-id="0f544-117">檔案名稱： %1</span><span class="sxs-lookup"><span data-stu-id="0f544-117">File Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f544-118">說明</span><span class="sxs-lookup"><span data-stu-id="0f544-118">Explanation</span></span>  
 <span data-ttu-id="0f544-119">這個資訊事件表示 SSO 已刪除重新執行和/或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="0f544-119">This Information event indicates that SSO has deleted a replay and\or progress file.</span></span>  
  
 <span data-ttu-id="0f544-120">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="0f544-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="0f544-121">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="0f544-121">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f544-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0f544-122">User Action</span></span>  
  
-   <span data-ttu-id="0f544-123">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="0f544-123">No user action is necessary.</span></span>  
  
 <span data-ttu-id="0f544-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="0f544-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="0f544-125">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="0f544-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="0f544-126">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="0f544-126">Password Synchronization</span></span>](../core/password-synchronization2.md)