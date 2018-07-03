---
title: 單一登入： 事件 10717 |Microsoft Docs
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
ms.openlocfilehash: 7beabfc76ce1c5ab72ac577be2dfbe549b35a4a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004527"
---
# <a name="single-sign-on-event-10717"></a><span data-ttu-id="5b13d-102">單一登入： 事件 10717</span><span class="sxs-lookup"><span data-stu-id="5b13d-102">Single Sign-On: Event 10717</span></span>
## <a name="details"></a><span data-ttu-id="5b13d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b13d-103">Details</span></span>  

|                 |                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5b13d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5b13d-104">Product Name</span></span>   |                                                            <span data-ttu-id="5b13d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5b13d-105">Enterprise Single Sign-On</span></span>                                                             |
| <span data-ttu-id="5b13d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5b13d-106">Product Version</span></span> |                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                            |
|    <span data-ttu-id="5b13d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5b13d-107">Event ID</span></span>     |                                                                      <span data-ttu-id="5b13d-108">10717</span><span class="sxs-lookup"><span data-stu-id="5b13d-108">10717</span></span>                                                                       |
|  <span data-ttu-id="5b13d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5b13d-109">Event Source</span></span>   |                                                                      <span data-ttu-id="5b13d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5b13d-110">ENTSSO</span></span>                                                                      |
|    <span data-ttu-id="5b13d-111">元件</span><span class="sxs-lookup"><span data-stu-id="5b13d-111">Component</span></span>    |                                                                       <span data-ttu-id="5b13d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5b13d-112">N\A</span></span>                                                                        |
|  <span data-ttu-id="5b13d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5b13d-113">Symbolic Name</span></span>  |                                                         <span data-ttu-id="5b13d-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span><span class="sxs-lookup"><span data-stu-id="5b13d-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span></span>                                                          |
|  <span data-ttu-id="5b13d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5b13d-115">Message Text</span></span>   | <span data-ttu-id="5b13d-116">無法建立重新執行檔案 directory.%r</span><span class="sxs-lookup"><span data-stu-id="5b13d-116">Failed to create the replay files directory.%r</span></span><br /><br /> <span data-ttu-id="5b13d-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="5b13d-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="5b13d-118">重新執行檔案目錄: %2 %r</span><span class="sxs-lookup"><span data-stu-id="5b13d-118">Replay Files Directory: %2%r</span></span><br /><br /> <span data-ttu-id="5b13d-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="5b13d-119">Error Code: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="5b13d-120">說明</span><span class="sxs-lookup"><span data-stu-id="5b13d-120">Explanation</span></span>  
 <span data-ttu-id="5b13d-121">這個錯誤事件表示無法建立重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="5b13d-121">This Error event indicates that a replay files directory could not be created.</span></span>  

 <span data-ttu-id="5b13d-122">當密碼同步配接器的 SSO 服務會收到密碼變更時，它們會儲存在 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5b13d-122">When password changes are received by the SSO service from a password sync adapter, they are stored in the SSO database.</span></span> <span data-ttu-id="5b13d-123">如果 SSO 資料庫暫時無法使用時，密碼變更會儲存在本機重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="5b13d-123">If the SSO database is temporarily unavailable, the password changes are stored locally in replay files.</span></span> <span data-ttu-id="5b13d-124">重新執行檔案會儲存在重新執行檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="5b13d-124">Replay files are stored in the replay files directory.</span></span>  

## <a name="user-action"></a><span data-ttu-id="5b13d-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5b13d-125">User Action</span></span>  
 <span data-ttu-id="5b13d-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5b13d-126">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="5b13d-127">檢查重新執行檔案目錄，如果不存在，嘗試以手動方式為 SSO 服務使用相同的服務帳戶加以建立。</span><span class="sxs-lookup"><span data-stu-id="5b13d-127">Check the replay files directory, if one does not exist, attempt to create it manually using the same service account as the SSO service.</span></span> <span data-ttu-id="5b13d-128">如果您無法建立使用相同的帳戶為 SSO 服務的重新執行檔案目錄，請檢查該帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="5b13d-128">If you cannot create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  

  <span data-ttu-id="5b13d-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="5b13d-129">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="5b13d-130">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="5b13d-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="5b13d-131">密碼同步</span><span class="sxs-lookup"><span data-stu-id="5b13d-131">Password Synchronization</span></span>](../core/password-synchronization2.md)
