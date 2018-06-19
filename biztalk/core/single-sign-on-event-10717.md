---
title: 單一登入： 事件 10717 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14691e0f-a399-4b4d-9dd5-516bf8d3a167
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70195251b599daebd50b57f0b137dd026dd032e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270358"
---
# <a name="single-sign-on-event-10717"></a><span data-ttu-id="a87ec-102">單一登入： 事件 10717</span><span class="sxs-lookup"><span data-stu-id="a87ec-102">Single Sign-On: Event 10717</span></span>
## <a name="details"></a><span data-ttu-id="a87ec-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a87ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a87ec-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a87ec-104">Product Name</span></span>|<span data-ttu-id="a87ec-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a87ec-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a87ec-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a87ec-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a87ec-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a87ec-107">Event ID</span></span>|<span data-ttu-id="a87ec-108">10717</span><span class="sxs-lookup"><span data-stu-id="a87ec-108">10717</span></span>|  
|<span data-ttu-id="a87ec-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a87ec-109">Event Source</span></span>|<span data-ttu-id="a87ec-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a87ec-110">ENTSSO</span></span>|  
|<span data-ttu-id="a87ec-111">元件</span><span class="sxs-lookup"><span data-stu-id="a87ec-111">Component</span></span>|<span data-ttu-id="a87ec-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a87ec-112">N\A</span></span>|  
|<span data-ttu-id="a87ec-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a87ec-113">Symbolic Name</span></span>|<span data-ttu-id="a87ec-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span><span class="sxs-lookup"><span data-stu-id="a87ec-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span></span>|  
|<span data-ttu-id="a87ec-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a87ec-115">Message Text</span></span>|<span data-ttu-id="a87ec-116">無法建立重新執行檔案 directory.%r</span><span class="sxs-lookup"><span data-stu-id="a87ec-116">Failed to create the replay files directory.%r</span></span><br /><br /> <span data-ttu-id="a87ec-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a87ec-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="a87ec-118">重新執行檔案目錄: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a87ec-118">Replay Files Directory: %2%r</span></span><br /><br /> <span data-ttu-id="a87ec-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="a87ec-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a87ec-120">說明</span><span class="sxs-lookup"><span data-stu-id="a87ec-120">Explanation</span></span>  
 <span data-ttu-id="a87ec-121">這個錯誤事件表示無法建立重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="a87ec-121">This Error event indicates that a replay files directory could not be created.</span></span>  
  
 <span data-ttu-id="a87ec-122">當 SSO 服務，從密碼同步配接器接收密碼變更時，它們會儲存在 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a87ec-122">When password changes are received by the SSO service from a password sync adapter, they are stored in the SSO database.</span></span> <span data-ttu-id="a87ec-123">如果 SSO 資料庫暫時無法使用時，密碼變更會在本機儲存在重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="a87ec-123">If the SSO database is temporarily unavailable, the password changes are stored locally in replay files.</span></span> <span data-ttu-id="a87ec-124">重新執行檔案會儲存在重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="a87ec-124">Replay files are stored in the replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a87ec-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a87ec-125">User Action</span></span>  
 <span data-ttu-id="a87ec-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a87ec-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="a87ec-127">重新執行檔案目錄，如果一個核取不存在，嘗試建立它以手動方式為 SSO 服務使用相同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a87ec-127">Check the replay files directory, if one does not exist, attempt to create it manually using the same service account as the SSO service.</span></span> <span data-ttu-id="a87ec-128">如果您無法建立重新執行檔案目錄使用相同的帳戶做為 SSO 服務，請檢查該帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="a87ec-128">If you cannot create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  
  
 <span data-ttu-id="a87ec-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="a87ec-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="a87ec-130">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="a87ec-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="a87ec-131">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="a87ec-131">Password Synchronization</span></span>](../core/password-synchronization2.md)