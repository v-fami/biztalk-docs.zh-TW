---
title: 單一登入： 事件 10682 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79aeff556fbbbbbbbcf41f63a37ab3b47311d697
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271406"
---
# <a name="single-sign-on-event-10682"></a><span data-ttu-id="993a1-102">單一登入： 事件 10682</span><span class="sxs-lookup"><span data-stu-id="993a1-102">Single Sign-On: Event 10682</span></span>
## <a name="details"></a><span data-ttu-id="993a1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="993a1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="993a1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="993a1-104">Product Name</span></span>|<span data-ttu-id="993a1-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="993a1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="993a1-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="993a1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="993a1-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="993a1-107">Event ID</span></span>|<span data-ttu-id="993a1-108">10682</span><span class="sxs-lookup"><span data-stu-id="993a1-108">10682</span></span>|  
|<span data-ttu-id="993a1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="993a1-109">Event Source</span></span>|<span data-ttu-id="993a1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="993a1-110">ENTSSO</span></span>|  
|<span data-ttu-id="993a1-111">元件</span><span class="sxs-lookup"><span data-stu-id="993a1-111">Component</span></span>|<span data-ttu-id="993a1-112">N\A</span><span class="sxs-lookup"><span data-stu-id="993a1-112">N\A</span></span>|  
|<span data-ttu-id="993a1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="993a1-113">Symbolic Name</span></span>|<span data-ttu-id="993a1-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span><span class="sxs-lookup"><span data-stu-id="993a1-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span></span>|  
|<span data-ttu-id="993a1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="993a1-115">Message Text</span></span>|<span data-ttu-id="993a1-116">目錄中找不到重新執行檔案目錄-將 ignored.%r</span><span class="sxs-lookup"><span data-stu-id="993a1-116">A directory was found in the replay files directory - it will be ignored.%r</span></span><br /><span data-ttu-id="993a1-117">目錄： %1</span><span class="sxs-lookup"><span data-stu-id="993a1-117">Directory: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="993a1-118">說明</span><span class="sxs-lookup"><span data-stu-id="993a1-118">Explanation</span></span>  
 <span data-ttu-id="993a1-119">這個警告事件表示目錄已重新執行檔案目錄中找到。</span><span class="sxs-lookup"><span data-stu-id="993a1-119">This Warning event indicates that a directory was found in the replay files directory.</span></span> <span data-ttu-id="993a1-120">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="993a1-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="993a1-121">在此情況下密碼變更會儲存在暫時加密檔案，而且當它再次可用時傳回至 SSO 資料庫重新執行。</span><span class="sxs-lookup"><span data-stu-id="993a1-121">In this case the password changes are stored in a temporary encrypted file, and are replayed back to the SSO database when it becomes available again.</span></span> <span data-ttu-id="993a1-122">重新執行檔案目錄必須只包含重新執行檔案 – 如果找到目錄，則會發出這則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="993a1-122">The replay files directory is expected to contain only replay files – this error message is issued if a directory is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="993a1-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="993a1-123">User Action</span></span>  
 <span data-ttu-id="993a1-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="993a1-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="993a1-125">使用命令列工具 ssoconfig replayFiles 變更重新執行目錄。</span><span class="sxs-lookup"><span data-stu-id="993a1-125">Use command line tool ssoconfig -replayFiles to  change your replay directory.</span></span>  
  
-   <span data-ttu-id="993a1-126">如果未使用，請刪除不正確的目錄。</span><span class="sxs-lookup"><span data-stu-id="993a1-126">Delete the bad directory if it is not in use.</span></span>  
  
 <span data-ttu-id="993a1-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="993a1-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="993a1-128">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="993a1-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="993a1-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="993a1-129">Password Synchronization</span></span>](../core/password-synchronization2.md)