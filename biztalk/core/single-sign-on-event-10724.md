---
title: 單一登入： 事件 10724 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 022a6f73-a24b-4058-91a5-b831f6875409
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd9e65b18b66f119e3cc2acf7f078f17466e46b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271830"
---
# <a name="single-sign-on-event-10724"></a><span data-ttu-id="05fef-102">單一登入： 事件 10724</span><span class="sxs-lookup"><span data-stu-id="05fef-102">Single Sign-On: Event 10724</span></span>
## <a name="details"></a><span data-ttu-id="05fef-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="05fef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05fef-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="05fef-104">Product Name</span></span>|<span data-ttu-id="05fef-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="05fef-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="05fef-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="05fef-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="05fef-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="05fef-107">Event ID</span></span>|<span data-ttu-id="05fef-108">10724</span><span class="sxs-lookup"><span data-stu-id="05fef-108">10724</span></span>|  
|<span data-ttu-id="05fef-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="05fef-109">Event Source</span></span>|<span data-ttu-id="05fef-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="05fef-110">ENTSSO</span></span>|  
|<span data-ttu-id="05fef-111">元件</span><span class="sxs-lookup"><span data-stu-id="05fef-111">Component</span></span>|<span data-ttu-id="05fef-112">N\A</span><span class="sxs-lookup"><span data-stu-id="05fef-112">N\A</span></span>|  
|<span data-ttu-id="05fef-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="05fef-113">Symbolic Name</span></span>|<span data-ttu-id="05fef-114">SSO_ERROR_REPLAY_SECURITY_2</span><span class="sxs-lookup"><span data-stu-id="05fef-114">SSO_ERROR_REPLAY_SECURITY_2</span></span>|  
|<span data-ttu-id="05fef-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="05fef-115">Message Text</span></span>|<span data-ttu-id="05fef-116">重新執行或進度檔案上的安全性已從其原始值變更。%r</span><span class="sxs-lookup"><span data-stu-id="05fef-116">The security on the replay or progress file has been changed from its original value.%r</span></span><br /><br /> <span data-ttu-id="05fef-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="05fef-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="05fef-118">目前的檔案安全性: %2 %r</span><span class="sxs-lookup"><span data-stu-id="05fef-118">Current File Security: %2%r</span></span><br /><br /> <span data-ttu-id="05fef-119">原始的檔案安全性： %3</span><span class="sxs-lookup"><span data-stu-id="05fef-119">Original File Security: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05fef-120">說明</span><span class="sxs-lookup"><span data-stu-id="05fef-120">Explanation</span></span>  
 <span data-ttu-id="05fef-121">這個錯誤事件表示安全性上重新執行或進度檔案已變更。</span><span class="sxs-lookup"><span data-stu-id="05fef-121">This Error event indicates that the security on the replay or progress files has been changed.</span></span>  
  
 <span data-ttu-id="05fef-122">重新執行檔案會儲存在重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="05fef-122">Replay files are stored in the replay files directory.</span></span> <span data-ttu-id="05fef-123">根據預設，SSO 服務帳戶用來建立重新執行檔案和重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="05fef-123">By default, the SSO service account is used to create both the replay files and the replay files directory.</span></span> <span data-ttu-id="05fef-124">SSO 驗證，進行任何變更已重新執行檔案和重新執行檔案目錄的安全性設定以在建立後。</span><span class="sxs-lookup"><span data-stu-id="05fef-124">SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created.</span></span> <span data-ttu-id="05fef-125">如果與不同帳戶建立重新執行檔案目錄，密碼同步處理嘗試建立該目錄中的重新執行檔案時，可以會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="05fef-125">If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory.</span></span> <span data-ttu-id="05fef-126">強烈建議使用者不要變更任何的重新執行檔案和重新執行檔案目錄的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="05fef-126">It is strongly recommended that users not change any security configuration of the replay files and replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05fef-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="05fef-127">User Action</span></span>  
 <span data-ttu-id="05fef-128">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="05fef-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="05fef-129">檢查權限帳戶用來建立重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="05fef-129">Check permission for the account used to create the replay files.</span></span> <span data-ttu-id="05fef-130">這通常是 SSO 系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="05fef-130">This is typically the SSO system account.</span></span>  
  
 <span data-ttu-id="05fef-131">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="05fef-131">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="05fef-132">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="05fef-132">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="05fef-133">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="05fef-133">Password Synchronization</span></span>](../core/password-synchronization2.md)