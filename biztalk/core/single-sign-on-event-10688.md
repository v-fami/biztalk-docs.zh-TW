---
title: 單一登入： 事件 10688 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63fe4ac5-dc1d-4d5a-8ce3-40ed4556afcf
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0efe057472366b713b00573a36fa15c0b092ec2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975903"
---
# <a name="single-sign-on-event-10688"></a><span data-ttu-id="13306-102">單一登入： 事件 10688</span><span class="sxs-lookup"><span data-stu-id="13306-102">Single Sign-On: Event 10688</span></span>
## <a name="details"></a><span data-ttu-id="13306-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="13306-103">Details</span></span>  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  <span data-ttu-id="13306-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="13306-104">Product Name</span></span>   |                         <span data-ttu-id="13306-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="13306-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="13306-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="13306-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    <span data-ttu-id="13306-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="13306-107">Event ID</span></span>     |                                   <span data-ttu-id="13306-108">10688</span><span class="sxs-lookup"><span data-stu-id="13306-108">10688</span></span>                                   |
|  <span data-ttu-id="13306-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="13306-109">Event Source</span></span>   |                                  <span data-ttu-id="13306-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="13306-110">ENTSSO</span></span>                                   |
|    <span data-ttu-id="13306-111">元件</span><span class="sxs-lookup"><span data-stu-id="13306-111">Component</span></span>    |                                    <span data-ttu-id="13306-112">N\A</span><span class="sxs-lookup"><span data-stu-id="13306-112">N\A</span></span>                                    |
|  <span data-ttu-id="13306-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="13306-113">Symbolic Name</span></span>  |                   <span data-ttu-id="13306-114">SSO_ERROR_REPLAY_FILE_UNEXPECTED_DATA</span><span class="sxs-lookup"><span data-stu-id="13306-114">SSO_ERROR_REPLAY_FILE_UNEXPECTED_DATA</span></span>                   |
|  <span data-ttu-id="13306-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="13306-115">Message Text</span></span>   | <span data-ttu-id="13306-116">在重新執行檔案中偵測到損毀。%r</span><span class="sxs-lookup"><span data-stu-id="13306-116">Corruption was detected in the replay file.%r</span></span><br /><br /> <span data-ttu-id="13306-117">重新執行檔案： %1</span><span class="sxs-lookup"><span data-stu-id="13306-117">Replay File: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="13306-118">說明</span><span class="sxs-lookup"><span data-stu-id="13306-118">Explanation</span></span>  
 <span data-ttu-id="13306-119">這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫，請連絡，但無法讀取重新執行檔案，因為已損毀。</span><span class="sxs-lookup"><span data-stu-id="13306-119">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="13306-120">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一步 重新執行檔案 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="13306-120">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  

 <span data-ttu-id="13306-121">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="13306-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="13306-122">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="13306-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="13306-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="13306-123">User Action</span></span>  
 <span data-ttu-id="13306-124">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="13306-124">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="13306-125">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="13306-125">Check System and Application event logs for associated events.</span></span>  

- <span data-ttu-id="13306-126">刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="13306-126">Delete the replay file.</span></span>  

  <span data-ttu-id="13306-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="13306-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="13306-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="13306-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="13306-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="13306-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
