---
title: 單一登入： 事件 10692 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78a476ca-32eb-4f37-a807-25850503db6e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37148a774504599b99665b57691316c35d0783bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987279"
---
# <a name="single-sign-on-event-10692"></a><span data-ttu-id="09275-102">單一登入： 事件 10692</span><span class="sxs-lookup"><span data-stu-id="09275-102">Single Sign-On: Event 10692</span></span>
## <a name="details"></a><span data-ttu-id="09275-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="09275-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="09275-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="09275-104">Product Name</span></span>   |                                                                                                                      <span data-ttu-id="09275-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="09275-105">Enterprise Single Sign-On</span></span>                                                                                                                      |
| <span data-ttu-id="09275-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="09275-106">Product Version</span></span> |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    <span data-ttu-id="09275-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="09275-107">Event ID</span></span>     |                                                                                                                                <span data-ttu-id="09275-108">10692</span><span class="sxs-lookup"><span data-stu-id="09275-108">10692</span></span>                                                                                                                                |
|  <span data-ttu-id="09275-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="09275-109">Event Source</span></span>   |                                                                                                                               <span data-ttu-id="09275-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="09275-110">ENTSSO</span></span>                                                                                                                                |
|    <span data-ttu-id="09275-111">元件</span><span class="sxs-lookup"><span data-stu-id="09275-111">Component</span></span>    |                                                                                                                                 <span data-ttu-id="09275-112">N\A</span><span class="sxs-lookup"><span data-stu-id="09275-112">N\A</span></span>                                                                                                                                 |
|  <span data-ttu-id="09275-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="09275-113">Symbolic Name</span></span>  |                                                                                                                    <span data-ttu-id="09275-114">SSO_WARN_REPLAY_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="09275-114">SSO_WARN_REPLAY_ACCESS_DENIED</span></span>                                                                                                                    |
|  <span data-ttu-id="09275-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="09275-115">Message Text</span></span>   | <span data-ttu-id="09275-116">無法重新執行的外部密碼變更，因為原始呼叫端不再 adapter.%r 存取帳戶的成員</span><span class="sxs-lookup"><span data-stu-id="09275-116">The external password change cannot be replayed because the original caller is no longer a member of the access account for the adapter.%r</span></span><br /><br /> <span data-ttu-id="09275-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="09275-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="09275-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="09275-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="09275-119">原始的呼叫端: %3 %r</span><span class="sxs-lookup"><span data-stu-id="09275-119">Original Caller: %3%r</span></span><br /><br /> <span data-ttu-id="09275-120">存取帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="09275-120">Access Account: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="09275-121">說明</span><span class="sxs-lookup"><span data-stu-id="09275-121">Explanation</span></span>  
 <span data-ttu-id="09275-122">這個警告事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法進行變更 （在 SSO 資料庫） 中指定重新執行檔案因為原本所指定變更的帳戶已不再有效。</span><span class="sxs-lookup"><span data-stu-id="09275-122">This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to make a change (in the SSO database) specified in the replay file because the account that originally specified the change is no longer valid.</span></span>  

 <span data-ttu-id="09275-123">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="09275-123">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="09275-124">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="09275-124">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="09275-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="09275-125">User Action</span></span>  
 <span data-ttu-id="09275-126">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="09275-126">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="09275-127">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="09275-127">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="09275-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="09275-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="09275-129">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="09275-129">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="09275-130">密碼同步</span><span class="sxs-lookup"><span data-stu-id="09275-130">Password Synchronization</span></span>](../core/password-synchronization2.md)
