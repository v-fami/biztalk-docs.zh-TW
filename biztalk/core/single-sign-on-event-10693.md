---
title: 單一登入： 事件 10693 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 672bac7d-0ccc-4a42-a49d-57e387f4cf3a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f9dd254fd81d54f0c60a2ea8b0a143e94ddd516
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009479"
---
# <a name="single-sign-on-event-10693"></a><span data-ttu-id="7544d-102">單一登入： 事件 10693</span><span class="sxs-lookup"><span data-stu-id="7544d-102">Single Sign-On: Event 10693</span></span>
## <a name="details"></a><span data-ttu-id="7544d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7544d-103">Details</span></span>  

|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="7544d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7544d-104">Product Name</span></span>   |                                       <span data-ttu-id="7544d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="7544d-105">Enterprise Single Sign-On</span></span>                                        |
| <span data-ttu-id="7544d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="7544d-106">Product Version</span></span> |                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                       |
|    <span data-ttu-id="7544d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7544d-107">Event ID</span></span>     |                                                 <span data-ttu-id="7544d-108">10693</span><span class="sxs-lookup"><span data-stu-id="7544d-108">10693</span></span>                                                  |
|  <span data-ttu-id="7544d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7544d-109">Event Source</span></span>   |                                                 <span data-ttu-id="7544d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7544d-110">ENTSSO</span></span>                                                 |
|    <span data-ttu-id="7544d-111">元件</span><span class="sxs-lookup"><span data-stu-id="7544d-111">Component</span></span>    |                                                  <span data-ttu-id="7544d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="7544d-112">N\A</span></span>                                                   |
|  <span data-ttu-id="7544d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7544d-113">Symbolic Name</span></span>  |                                    <span data-ttu-id="7544d-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span><span class="sxs-lookup"><span data-stu-id="7544d-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span></span>                                    |
|  <span data-ttu-id="7544d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7544d-115">Message Text</span></span>   | <span data-ttu-id="7544d-116">無法建立重新執行或進度 file.%r</span><span class="sxs-lookup"><span data-stu-id="7544d-116">Could not create the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="7544d-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="7544d-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="7544d-118">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="7544d-118">Error Code: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="7544d-119">說明</span><span class="sxs-lookup"><span data-stu-id="7544d-119">Explanation</span></span>  
 <span data-ttu-id="7544d-120">這個警告事件表示 SSO 找不到 SSO 資料庫的連線遺失時，請建立重新執行和/或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="7544d-120">This Warning event indicates that SSO was unable to create a replay and\or progress file when connection to the SSO database was lost.</span></span>  

 <span data-ttu-id="7544d-121">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="7544d-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="7544d-122">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="7544d-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="7544d-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7544d-123">User Action</span></span>  
 <span data-ttu-id="7544d-124">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7544d-124">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="7544d-125">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7544d-125">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="7544d-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="7544d-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="7544d-127">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="7544d-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="7544d-128">密碼同步</span><span class="sxs-lookup"><span data-stu-id="7544d-128">Password Synchronization</span></span>](../core/password-synchronization2.md)
