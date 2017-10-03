---
title: "單一登入： 事件 10723 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00536f3e-26d6-4e19-a98f-e687bb1b6611
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d1bb94e6bb528d58d895b528135674a3e47f83b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10723"></a><span data-ttu-id="f347b-102">單一登入： 事件 10723</span><span class="sxs-lookup"><span data-stu-id="f347b-102">Single Sign-On: Event 10723</span></span>
## <a name="details"></a><span data-ttu-id="f347b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f347b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f347b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f347b-104">Product Name</span></span>|<span data-ttu-id="f347b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f347b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f347b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f347b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f347b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f347b-107">Event ID</span></span>|<span data-ttu-id="f347b-108">10723</span><span class="sxs-lookup"><span data-stu-id="f347b-108">10723</span></span>|  
|<span data-ttu-id="f347b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f347b-109">Event Source</span></span>|<span data-ttu-id="f347b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f347b-110">ENTSSO</span></span>|  
|<span data-ttu-id="f347b-111">元件</span><span class="sxs-lookup"><span data-stu-id="f347b-111">Component</span></span>|<span data-ttu-id="f347b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f347b-112">N\A</span></span>|  
|<span data-ttu-id="f347b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f347b-113">Symbolic Name</span></span>|<span data-ttu-id="f347b-114">SSO_ERROR_REPLAY_SECURITY_1</span><span class="sxs-lookup"><span data-stu-id="f347b-114">SSO_ERROR_REPLAY_SECURITY_1</span></span>|  
|<span data-ttu-id="f347b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f347b-115">Message Text</span></span>|<span data-ttu-id="f347b-116">重新執行檔案目錄的安全性不符上重新執行或進度 file.%r 安全性</span><span class="sxs-lookup"><span data-stu-id="f347b-116">The security on the replay files directory does not match the security on the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="f347b-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f347b-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="f347b-118">檔案安全性: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f347b-118">File Security: %2%r</span></span><br /><br /> <span data-ttu-id="f347b-119">目錄安全性： %3</span><span class="sxs-lookup"><span data-stu-id="f347b-119">Directory Security: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f347b-120">說明</span><span class="sxs-lookup"><span data-stu-id="f347b-120">Explanation</span></span>  
 <span data-ttu-id="f347b-121">這個錯誤事件表示重新執行檔案目錄的安全性不符上重新執行檔案或進度檔案的安全性。</span><span class="sxs-lookup"><span data-stu-id="f347b-121">This Error event indicates that the security on the replay files directory does not match the security on the replay or progress file.</span></span>  
  
 <span data-ttu-id="f347b-122">重新執行檔案會儲存在重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="f347b-122">Replay files are stored in the replay files directory.</span></span> <span data-ttu-id="f347b-123">根據預設，SSO 服務帳戶用來建立重新執行檔案和重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="f347b-123">By default, the SSO service account is used to create both the replay files and the replay files directory.</span></span> <span data-ttu-id="f347b-124">SSO 驗證，進行任何變更已重新執行檔案和重新執行檔案目錄的安全性設定以在建立後。</span><span class="sxs-lookup"><span data-stu-id="f347b-124">SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created.</span></span> <span data-ttu-id="f347b-125">如果與不同帳戶建立重新執行檔案目錄，密碼同步處理嘗試建立該目錄中的重新執行檔案時，可以會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="f347b-125">If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory.</span></span> <span data-ttu-id="f347b-126">強烈建議使用者不要變更任何的重新執行檔案和重新執行檔案目錄的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f347b-126">It is strongly recommended that users not change any security configuration of the replay files and replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f347b-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f347b-127">User Action</span></span>  
 <span data-ttu-id="f347b-128">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f347b-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="f347b-129">請檢查用來建立重新執行檔案目錄的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f347b-129">Check the account used to create the replay files directory.</span></span> <span data-ttu-id="f347b-130">如果目錄是空的請嘗試再次執行密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="f347b-130">If the directory is empty, attempt running password sync again.</span></span> <span data-ttu-id="f347b-131">可能必須重新建立為 SSO 服務使用相同的服務帳戶的目錄。</span><span class="sxs-lookup"><span data-stu-id="f347b-131">It may be necessary to re-create the directory using the same service account as the SSO service.</span></span> <span data-ttu-id="f347b-132">如果您無法重新建立為 SSO 服務使用相同的帳戶重新執行檔案目錄，請檢查該帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="f347b-132">If you cannot re-create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  
  
 <span data-ttu-id="f347b-133">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="f347b-133">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="f347b-134">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="f347b-134">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="f347b-135">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="f347b-135">Password Synchronization</span></span>](../core/password-synchronization2.md)