---
title: "單一登入： 事件 11060 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1423b7385e6c0b8f78fb815ec48b749556cd291f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11060"></a><span data-ttu-id="5f3b5-102">單一登入： 事件 11060</span><span class="sxs-lookup"><span data-stu-id="5f3b5-102">Single Sign-On: Event 11060</span></span>
## <a name="details"></a><span data-ttu-id="5f3b5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5f3b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f3b5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5f3b5-104">Product Name</span></span>|<span data-ttu-id="5f3b5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5f3b5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5f3b5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5f3b5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5f3b5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5f3b5-107">Event ID</span></span>|<span data-ttu-id="5f3b5-108">11060</span><span class="sxs-lookup"><span data-stu-id="5f3b5-108">11060</span></span>|  
|<span data-ttu-id="5f3b5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5f3b5-109">Event Source</span></span>|<span data-ttu-id="5f3b5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5f3b5-110">ENTSSO</span></span>|  
|<span data-ttu-id="5f3b5-111">元件</span><span class="sxs-lookup"><span data-stu-id="5f3b5-111">Component</span></span>|<span data-ttu-id="5f3b5-112">不適用</span><span class="sxs-lookup"><span data-stu-id="5f3b5-112">N/A</span></span>|  
|<span data-ttu-id="5f3b5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5f3b5-113">Symbolic Name</span></span>|<span data-ttu-id="5f3b5-114">SSO_WARN_PS_MIIS_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="5f3b5-114">SSO_WARN_PS_MIIS_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="5f3b5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5f3b5-115">Message Text</span></span>|<span data-ttu-id="5f3b5-116">來自 MIIS 的 Windows 密碼變更只能從 SSO 服務 account.%r 接受</span><span class="sxs-lookup"><span data-stu-id="5f3b5-116">Windows password changes from MIIS will only be accepted from the SSO service account.%r</span></span><br /><br /> <span data-ttu-id="5f3b5-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="5f3b5-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="5f3b5-118">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="5f3b5-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="5f3b5-119">SSO 服務帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="5f3b5-119">SSO Service Account: %3%r</span></span><br /><br /> <span data-ttu-id="5f3b5-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="5f3b5-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f3b5-121">說明</span><span class="sxs-lookup"><span data-stu-id="5f3b5-121">Explanation</span></span>  
 <span data-ttu-id="5f3b5-122">已由 ENTSSO 伺服器從 Microsoft Identity Integration Server (MIIS) 接收密碼變更。</span><span class="sxs-lookup"><span data-stu-id="5f3b5-122">A password change has been received by the ENTSSO server from Microsoft Identity Integration Server (MIIS).</span></span> <span data-ttu-id="5f3b5-123">不過，如果用戶端使用者 （呼叫端） 是做為 SSO 服務帳戶的相同帳戶 ENTSSO 伺服器將只接受來自 MIIS 的密碼變更。</span><span class="sxs-lookup"><span data-stu-id="5f3b5-123">However, the ENTSSO server will only accept password changes from MIIS if the Client User (the caller) is the same account as the SSO service account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f3b5-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5f3b5-124">User Action</span></span>  
 <span data-ttu-id="5f3b5-125">檢查呼叫端的 MIIS 的密碼同步處理的設定。</span><span class="sxs-lookup"><span data-stu-id="5f3b5-125">Check the configuration of the caller for password sync in MIIS.</span></span> <span data-ttu-id="5f3b5-126">如需詳細資訊，請參閱[如何設定 ENTSSO 進行 MIIS 密碼同步](../core/how-to-configure-entsso-for-miis-password-sync.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3b5-126">For more information, see [How to Configure ENTSSO for MIIS Password Sync](../core/how-to-configure-entsso-for-miis-password-sync.md).</span></span>