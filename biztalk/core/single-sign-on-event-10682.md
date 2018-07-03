---
title: 單一登入： 事件 10682 |Microsoft Docs
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
ms.openlocfilehash: 5c7ed830c44404e0365505b7dc0f3a5c6fec8a85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999711"
---
# <a name="single-sign-on-event-10682"></a><span data-ttu-id="66b81-102">單一登入： 事件 10682</span><span class="sxs-lookup"><span data-stu-id="66b81-102">Single Sign-On: Event 10682</span></span>
## <a name="details"></a><span data-ttu-id="66b81-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="66b81-103">Details</span></span>  

|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="66b81-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="66b81-104">Product Name</span></span>   |                                   <span data-ttu-id="66b81-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="66b81-105">Enterprise Single Sign-On</span></span>                                    |
| <span data-ttu-id="66b81-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="66b81-106">Product Version</span></span> |                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    <span data-ttu-id="66b81-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="66b81-107">Event ID</span></span>     |                                             <span data-ttu-id="66b81-108">10682</span><span class="sxs-lookup"><span data-stu-id="66b81-108">10682</span></span>                                              |
|  <span data-ttu-id="66b81-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="66b81-109">Event Source</span></span>   |                                             <span data-ttu-id="66b81-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="66b81-110">ENTSSO</span></span>                                             |
|    <span data-ttu-id="66b81-111">元件</span><span class="sxs-lookup"><span data-stu-id="66b81-111">Component</span></span>    |                                              <span data-ttu-id="66b81-112">N\A</span><span class="sxs-lookup"><span data-stu-id="66b81-112">N\A</span></span>                                               |
|  <span data-ttu-id="66b81-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="66b81-113">Symbolic Name</span></span>  |                               <span data-ttu-id="66b81-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span><span class="sxs-lookup"><span data-stu-id="66b81-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span></span>                                |
|  <span data-ttu-id="66b81-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="66b81-115">Message Text</span></span>   | <span data-ttu-id="66b81-116">已找到的目錄中重新執行檔案目錄中-將予以 ignored.%r</span><span class="sxs-lookup"><span data-stu-id="66b81-116">A directory was found in the replay files directory - it will be ignored.%r</span></span><br /><span data-ttu-id="66b81-117">目錄： %1</span><span class="sxs-lookup"><span data-stu-id="66b81-117">Directory: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="66b81-118">說明</span><span class="sxs-lookup"><span data-stu-id="66b81-118">Explanation</span></span>  
 <span data-ttu-id="66b81-119">這個警告事件表示在重新執行檔案目錄中已找到的目錄。</span><span class="sxs-lookup"><span data-stu-id="66b81-119">This Warning event indicates that a directory was found in the replay files directory.</span></span> <span data-ttu-id="66b81-120">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="66b81-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="66b81-121">在此情況下變更密碼會儲存在暫時加密檔案，並會重新執行回 SSO 資料庫當它再次可用時。</span><span class="sxs-lookup"><span data-stu-id="66b81-121">In this case the password changes are stored in a temporary encrypted file, and are replayed back to the SSO database when it becomes available again.</span></span> <span data-ttu-id="66b81-122">重新執行檔案目錄必須包含只重新執行檔案，如果找到目錄，則會發出此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="66b81-122">The replay files directory is expected to contain only replay files – this error message is issued if a directory is found.</span></span>  

## <a name="user-action"></a><span data-ttu-id="66b81-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="66b81-123">User Action</span></span>  
 <span data-ttu-id="66b81-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="66b81-124">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="66b81-125">您可以使用命令列工具 ssoconfig-replayFiles 變更重新執行目錄。</span><span class="sxs-lookup"><span data-stu-id="66b81-125">Use command line tool ssoconfig -replayFiles to  change your replay directory.</span></span>  

- <span data-ttu-id="66b81-126">如果未使用，請刪除不正確的目錄。</span><span class="sxs-lookup"><span data-stu-id="66b81-126">Delete the bad directory if it is not in use.</span></span>  

  <span data-ttu-id="66b81-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="66b81-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="66b81-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="66b81-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="66b81-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="66b81-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
