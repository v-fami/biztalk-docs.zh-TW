---
title: 單一登入： 事件 10687 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10b3fe2c-a7ba-47e1-a753-4eaa64b01a60
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 368e9bbad42e49ebd71bc1a581b0fb18bbcc2d5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270510"
---
# <a name="single-sign-on-event-10687"></a><span data-ttu-id="c86f8-102">單一登入： 事件 10687</span><span class="sxs-lookup"><span data-stu-id="c86f8-102">Single Sign-On: Event 10687</span></span>
## <a name="details"></a><span data-ttu-id="c86f8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c86f8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c86f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c86f8-104">Product Name</span></span>|<span data-ttu-id="c86f8-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c86f8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c86f8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c86f8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c86f8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c86f8-107">Event ID</span></span>|<span data-ttu-id="c86f8-108">10687</span><span class="sxs-lookup"><span data-stu-id="c86f8-108">10687</span></span>|  
|<span data-ttu-id="c86f8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c86f8-109">Event Source</span></span>|<span data-ttu-id="c86f8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c86f8-110">ENTSSO</span></span>|  
|<span data-ttu-id="c86f8-111">元件</span><span class="sxs-lookup"><span data-stu-id="c86f8-111">Component</span></span>|<span data-ttu-id="c86f8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c86f8-112">N\A</span></span>|  
|<span data-ttu-id="c86f8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c86f8-113">Symbolic Name</span></span>|<span data-ttu-id="c86f8-114">SSO_INFO_REPLAY_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="c86f8-114">SSO_INFO_REPLAY_COMPLETE</span></span>|  
|<span data-ttu-id="c86f8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c86f8-115">Message Text</span></span>|<span data-ttu-id="c86f8-116">重新執行預存外部密碼變更已完成。%r</span><span class="sxs-lookup"><span data-stu-id="c86f8-116">Replay of stored external password changes completed.%r</span></span><br /><br /> <span data-ttu-id="c86f8-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="c86f8-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="c86f8-118">其他資料： %2</span><span class="sxs-lookup"><span data-stu-id="c86f8-118">Additional Data: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c86f8-119">說明</span><span class="sxs-lookup"><span data-stu-id="c86f8-119">Explanation</span></span>  
 <span data-ttu-id="c86f8-120">這個資訊事件表示 SSO 已完成重新執行預存外部密碼變更檔案。</span><span class="sxs-lookup"><span data-stu-id="c86f8-120">This Information event indicates that SSO has completed replaying the stored external password changes file.</span></span> <span data-ttu-id="c86f8-121">在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="c86f8-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c86f8-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c86f8-122">User Action</span></span>  
  
-   <span data-ttu-id="c86f8-123">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="c86f8-123">No user action is necessary.</span></span>  
  
 <span data-ttu-id="c86f8-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="c86f8-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c86f8-125">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="c86f8-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="c86f8-126">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="c86f8-126">Password Synchronization</span></span>](../core/password-synchronization2.md)