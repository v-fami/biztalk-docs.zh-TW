---
title: 單一登入： 事件 10685 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b276432363f6073627aaa9033c2b78b730ccda1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992516"
---
# <a name="single-sign-on-event-10685"></a><span data-ttu-id="734e3-102">單一登入： 事件 10685</span><span class="sxs-lookup"><span data-stu-id="734e3-102">Single Sign-On: Event 10685</span></span>
## <a name="details"></a><span data-ttu-id="734e3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="734e3-103">Details</span></span>  

|                 |                                                                                                      |
|-----------------|------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="734e3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="734e3-104">Product Name</span></span>   |                                      <span data-ttu-id="734e3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="734e3-105">Enterprise Single Sign-On</span></span>                                       |
| <span data-ttu-id="734e3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="734e3-106">Product Version</span></span> |                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                      |
|    <span data-ttu-id="734e3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="734e3-107">Event ID</span></span>     |                                                <span data-ttu-id="734e3-108">10685</span><span class="sxs-lookup"><span data-stu-id="734e3-108">10685</span></span>                                                 |
|  <span data-ttu-id="734e3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="734e3-109">Event Source</span></span>   |                                                <span data-ttu-id="734e3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="734e3-110">ENTSSO</span></span>                                                |
|    <span data-ttu-id="734e3-111">元件</span><span class="sxs-lookup"><span data-stu-id="734e3-111">Component</span></span>    |                                                 <span data-ttu-id="734e3-112">N\A</span><span class="sxs-lookup"><span data-stu-id="734e3-112">N\A</span></span>                                                  |
|  <span data-ttu-id="734e3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="734e3-113">Symbolic Name</span></span>  |                                     <span data-ttu-id="734e3-114">SSO_WARN_REPLAY_CANNOT_OPEN</span><span class="sxs-lookup"><span data-stu-id="734e3-114">SSO_WARN_REPLAY_CANNOT_OPEN</span></span>                                      |
|  <span data-ttu-id="734e3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="734e3-115">Message Text</span></span>   | <span data-ttu-id="734e3-116">無法開啟重新執行或進度 file.%r</span><span class="sxs-lookup"><span data-stu-id="734e3-116">Could not open the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="734e3-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="734e3-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="734e3-118">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="734e3-118">Error Code: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="734e3-119">說明</span><span class="sxs-lookup"><span data-stu-id="734e3-119">Explanation</span></span>  
 <span data-ttu-id="734e3-120">這個警告事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法開啟重新執行或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="734e3-120">This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to open the replay or progress file.</span></span> <span data-ttu-id="734e3-121">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一步 重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="734e3-121">If SSO cannot open a replay file, it will proceed to the next replay file.</span></span>  

 <span data-ttu-id="734e3-122">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="734e3-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="734e3-123">進行檔案表示遠透過 SSO 已能夠讀取與 SSO 資料庫重新執行檔案中案例的連絡人會中斷一次中途播放背面重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="734e3-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is lost again part-way through playing back of a replay file.</span></span>  

## <a name="user-action"></a><span data-ttu-id="734e3-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="734e3-124">User Action</span></span>  
 <span data-ttu-id="734e3-125">若要解決這個警告事件，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="734e3-125">To resolve this Warning event, do the following:</span></span>  

- <span data-ttu-id="734e3-126">您應該檢查相關聯的事件，以判斷為什麼 SSO 無法連絡 SSO 資料庫的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="734e3-126">You should check the System and Application Event logs for associated events to determine why SSO was unable to contact the SSO database.</span></span>  

  <span data-ttu-id="734e3-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="734e3-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="734e3-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="734e3-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="734e3-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="734e3-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
