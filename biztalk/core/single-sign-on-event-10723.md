---
title: 單一登入： 事件 10723 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00536f3e-26d6-4e19-a98f-e687bb1b6611
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1ac448e1826f89041dc0bab16c6cfb76d5038e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972087"
---
# <a name="single-sign-on-event-10723"></a><span data-ttu-id="14d06-102">單一登入： 事件 10723</span><span class="sxs-lookup"><span data-stu-id="14d06-102">Single Sign-On: Event 10723</span></span>
## <a name="details"></a><span data-ttu-id="14d06-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14d06-103">Details</span></span>  

|                 |                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="14d06-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="14d06-104">Product Name</span></span>   |                                                                                        <span data-ttu-id="14d06-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="14d06-105">Enterprise Single Sign-On</span></span>                                                                                        |
| <span data-ttu-id="14d06-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="14d06-106">Product Version</span></span> |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                        |
|    <span data-ttu-id="14d06-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="14d06-107">Event ID</span></span>     |                                                                                                  <span data-ttu-id="14d06-108">10723</span><span class="sxs-lookup"><span data-stu-id="14d06-108">10723</span></span>                                                                                                  |
|  <span data-ttu-id="14d06-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="14d06-109">Event Source</span></span>   |                                                                                                 <span data-ttu-id="14d06-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="14d06-110">ENTSSO</span></span>                                                                                                  |
|    <span data-ttu-id="14d06-111">元件</span><span class="sxs-lookup"><span data-stu-id="14d06-111">Component</span></span>    |                                                                                                   <span data-ttu-id="14d06-112">N\A</span><span class="sxs-lookup"><span data-stu-id="14d06-112">N\A</span></span>                                                                                                   |
|  <span data-ttu-id="14d06-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="14d06-113">Symbolic Name</span></span>  |                                                                                       <span data-ttu-id="14d06-114">SSO_ERROR_REPLAY_SECURITY_1</span><span class="sxs-lookup"><span data-stu-id="14d06-114">SSO_ERROR_REPLAY_SECURITY_1</span></span>                                                                                       |
|  <span data-ttu-id="14d06-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="14d06-115">Message Text</span></span>   | <span data-ttu-id="14d06-116">重新執行檔案目錄的安全性不符上重新執行或進度 file.%r 的安全性</span><span class="sxs-lookup"><span data-stu-id="14d06-116">The security on the replay files directory does not match the security on the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="14d06-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="14d06-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="14d06-118">檔案安全性: %2 %r</span><span class="sxs-lookup"><span data-stu-id="14d06-118">File Security: %2%r</span></span><br /><br /> <span data-ttu-id="14d06-119">目錄安全性： %3</span><span class="sxs-lookup"><span data-stu-id="14d06-119">Directory Security: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="14d06-120">說明</span><span class="sxs-lookup"><span data-stu-id="14d06-120">Explanation</span></span>  
 <span data-ttu-id="14d06-121">這個錯誤事件表示重新執行檔案目錄的安全性不符上重新執行或進度檔案的安全性。</span><span class="sxs-lookup"><span data-stu-id="14d06-121">This Error event indicates that the security on the replay files directory does not match the security on the replay or progress file.</span></span>  

 <span data-ttu-id="14d06-122">重新執行檔案會儲存在重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="14d06-122">Replay files are stored in the replay files directory.</span></span> <span data-ttu-id="14d06-123">根據預設，SSO 服務帳戶用來建立重新執行檔案和重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="14d06-123">By default, the SSO service account is used to create both the replay files and the replay files directory.</span></span> <span data-ttu-id="14d06-124">SSO 驗證，任何已變更的重新執行檔案和重新執行檔案目錄的安全性組態建立之後。</span><span class="sxs-lookup"><span data-stu-id="14d06-124">SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created.</span></span> <span data-ttu-id="14d06-125">如果重新執行檔案目錄已建立具有不同的帳戶，密碼同步處理嘗試建立該目錄中的重新執行檔案時，可以會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="14d06-125">If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory.</span></span> <span data-ttu-id="14d06-126">強烈建議使用者未變更的重新執行檔案和重新執行檔案目錄的任何安全性設定。</span><span class="sxs-lookup"><span data-stu-id="14d06-126">It is strongly recommended that users not change any security configuration of the replay files and replay files directory.</span></span>  

## <a name="user-action"></a><span data-ttu-id="14d06-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="14d06-127">User Action</span></span>  
 <span data-ttu-id="14d06-128">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="14d06-128">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="14d06-129">請檢查用來建立重新執行檔案目錄的帳戶。</span><span class="sxs-lookup"><span data-stu-id="14d06-129">Check the account used to create the replay files directory.</span></span> <span data-ttu-id="14d06-130">如果目錄是空的請嘗試再次執行密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="14d06-130">If the directory is empty, attempt running password sync again.</span></span> <span data-ttu-id="14d06-131">它可能需要重新建立為 SSO 服務使用相同的服務帳戶的目錄。</span><span class="sxs-lookup"><span data-stu-id="14d06-131">It may be necessary to re-create the directory using the same service account as the SSO service.</span></span> <span data-ttu-id="14d06-132">如果您無法重新建立為 SSO 服務使用相同的帳戶重新執行檔案目錄，請檢查該帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="14d06-132">If you cannot re-create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  

  <span data-ttu-id="14d06-133">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="14d06-133">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="14d06-134">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="14d06-134">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="14d06-135">密碼同步</span><span class="sxs-lookup"><span data-stu-id="14d06-135">Password Synchronization</span></span>](../core/password-synchronization2.md)
