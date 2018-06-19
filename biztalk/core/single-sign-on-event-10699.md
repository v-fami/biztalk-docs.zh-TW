---
title: 單一登入： 事件 10699 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff26533-e4d7-47b5-92d5-bd8c72fab89a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b6ceb4ffe1e25a3828f406b881d4070b74a8d9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271702"
---
# <a name="single-sign-on-event-10699"></a><span data-ttu-id="63d36-102">單一登入： 事件 10699</span><span class="sxs-lookup"><span data-stu-id="63d36-102">Single Sign-On: Event 10699</span></span>
## <a name="details"></a><span data-ttu-id="63d36-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="63d36-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63d36-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="63d36-104">Product Name</span></span>|<span data-ttu-id="63d36-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="63d36-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="63d36-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="63d36-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="63d36-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="63d36-107">Event ID</span></span>|<span data-ttu-id="63d36-108">10699</span><span class="sxs-lookup"><span data-stu-id="63d36-108">10699</span></span>|  
|<span data-ttu-id="63d36-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="63d36-109">Event Source</span></span>|<span data-ttu-id="63d36-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="63d36-110">ENTSSO</span></span>|  
|<span data-ttu-id="63d36-111">元件</span><span class="sxs-lookup"><span data-stu-id="63d36-111">Component</span></span>|<span data-ttu-id="63d36-112">N\A</span><span class="sxs-lookup"><span data-stu-id="63d36-112">N\A</span></span>|  
|<span data-ttu-id="63d36-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="63d36-113">Symbolic Name</span></span>|<span data-ttu-id="63d36-114">SSO_INFO_EXTERNAL_PASSWORD_CHANGE_RECEIVED_REPLAY</span><span class="sxs-lookup"><span data-stu-id="63d36-114">SSO_INFO_EXTERNAL_PASSWORD_CHANGE_RECEIVED_REPLAY</span></span>|  
|<span data-ttu-id="63d36-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="63d36-115">Message Text</span></span>|<span data-ttu-id="63d36-116">從配接器 （來自重新執行 file).%r 收到外部密碼變更</span><span class="sxs-lookup"><span data-stu-id="63d36-116">An external password change was received from an adapter (from replay file).%r</span></span><br /><br /> <span data-ttu-id="63d36-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="63d36-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="63d36-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="63d36-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="63d36-119">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="63d36-119">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="63d36-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="63d36-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="63d36-121">記錄號碼： %5</span><span class="sxs-lookup"><span data-stu-id="63d36-121">Record Number: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63d36-122">說明</span><span class="sxs-lookup"><span data-stu-id="63d36-122">Explanation</span></span>  
 <span data-ttu-id="63d36-123">這個資訊事件表示外部密碼變更已收到來自配接器，這會記錄重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="63d36-123">This Information event indicates that an external password change was received from an adapter that was recorded to a replay file.</span></span> <span data-ttu-id="63d36-124">SSO 時，執行重新執行檔案上的預存外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="63d36-124">SSO is replaying the stored external password changes from the replay file.</span></span>  
  
 <span data-ttu-id="63d36-125">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="63d36-125">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="63d36-126">進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="63d36-126">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63d36-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="63d36-127">User Action</span></span>  
  
-   <span data-ttu-id="63d36-128">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="63d36-128">No user action is necessary.</span></span>  
  
 <span data-ttu-id="63d36-129">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="63d36-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="63d36-130">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="63d36-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="63d36-131">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="63d36-131">Password Synchronization</span></span>](../core/password-synchronization2.md)