---
title: "單一登入： 事件 10686 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3e71f2a-e51d-4736-b06a-117142d30dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600226ef7440b8be9d7927481170291b6c63faae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10686"></a><span data-ttu-id="9fbed-102">單一登入： 事件 10686</span><span class="sxs-lookup"><span data-stu-id="9fbed-102">Single Sign-On: Event 10686</span></span>
## <a name="details"></a><span data-ttu-id="9fbed-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9fbed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fbed-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9fbed-104">Product Name</span></span>|<span data-ttu-id="9fbed-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9fbed-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9fbed-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="9fbed-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9fbed-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9fbed-107">Event ID</span></span>|<span data-ttu-id="9fbed-108">10686</span><span class="sxs-lookup"><span data-stu-id="9fbed-108">10686</span></span>|  
|<span data-ttu-id="9fbed-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9fbed-109">Event Source</span></span>|<span data-ttu-id="9fbed-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9fbed-110">ENTSSO</span></span>|  
|<span data-ttu-id="9fbed-111">元件</span><span class="sxs-lookup"><span data-stu-id="9fbed-111">Component</span></span>|<span data-ttu-id="9fbed-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9fbed-112">N\A</span></span>|  
|<span data-ttu-id="9fbed-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9fbed-113">Symbolic Name</span></span>|<span data-ttu-id="9fbed-114">SSO_INFO_REPLAY_STARTED</span><span class="sxs-lookup"><span data-stu-id="9fbed-114">SSO_INFO_REPLAY_STARTED</span></span>|  
|<span data-ttu-id="9fbed-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9fbed-115">Message Text</span></span>|<span data-ttu-id="9fbed-116">重新執行預存外部密碼 changes.%r</span><span class="sxs-lookup"><span data-stu-id="9fbed-116">Replaying stored external password changes.%r</span></span><br /><br /> <span data-ttu-id="9fbed-117">重新執行檔案： %1</span><span class="sxs-lookup"><span data-stu-id="9fbed-117">Replay File: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9fbed-118">說明</span><span class="sxs-lookup"><span data-stu-id="9fbed-118">Explanation</span></span>  
 <span data-ttu-id="9fbed-119">這個資訊事件表示 SSO 已重新執行預存外部密碼變更檔案。</span><span class="sxs-lookup"><span data-stu-id="9fbed-119">This Information event indicates that SSO is replaying the stored external password changes file.</span></span> <span data-ttu-id="9fbed-120">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="9fbed-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9fbed-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9fbed-121">User Action</span></span>  
  
-   <span data-ttu-id="9fbed-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="9fbed-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="9fbed-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="9fbed-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9fbed-124">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="9fbed-124">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="9fbed-125">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="9fbed-125">Password Synchronization</span></span>](../core/password-synchronization2.md)