---
title: 單一登入： 事件 10695 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02c5dc1d-5626-4d24-ac4f-fcd2ae61cd98
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742d4f802aed2b497a32b20b007c5bac489a8169
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010287"
---
# <a name="single-sign-on-event-10695"></a><span data-ttu-id="81c9b-102">單一登入： 事件 10695</span><span class="sxs-lookup"><span data-stu-id="81c9b-102">Single Sign-On: Event 10695</span></span>
## <a name="details"></a><span data-ttu-id="81c9b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="81c9b-103">Details</span></span>  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="81c9b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="81c9b-104">Product Name</span></span>   |                                                 <span data-ttu-id="81c9b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="81c9b-105">Enterprise Single Sign-On</span></span>                                                 |
| <span data-ttu-id="81c9b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="81c9b-106">Product Version</span></span> |                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                 |
|    <span data-ttu-id="81c9b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="81c9b-107">Event ID</span></span>     |                                                           <span data-ttu-id="81c9b-108">10695</span><span class="sxs-lookup"><span data-stu-id="81c9b-108">10695</span></span>                                                           |
|  <span data-ttu-id="81c9b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="81c9b-109">Event Source</span></span>   |                                                          <span data-ttu-id="81c9b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="81c9b-110">ENTSSO</span></span>                                                           |
|    <span data-ttu-id="81c9b-111">元件</span><span class="sxs-lookup"><span data-stu-id="81c9b-111">Component</span></span>    |                                                            <span data-ttu-id="81c9b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="81c9b-112">N\A</span></span>                                                            |
|  <span data-ttu-id="81c9b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="81c9b-113">Symbolic Name</span></span>  |                                           <span data-ttu-id="81c9b-114">SSO_ERROR_REPLAY_INCORRECT_FILE_NAME</span><span class="sxs-lookup"><span data-stu-id="81c9b-114">SSO_ERROR_REPLAY_INCORRECT_FILE_NAME</span></span>                                            |
|  <span data-ttu-id="81c9b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="81c9b-115">Message Text</span></span>   | <span data-ttu-id="81c9b-116">重新執行或進度 file.%r 中偵測到損毀</span><span class="sxs-lookup"><span data-stu-id="81c9b-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="81c9b-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="81c9b-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="81c9b-118">解密檔案名稱： %2</span><span class="sxs-lookup"><span data-stu-id="81c9b-118">Decrypted File Name: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="81c9b-119">說明</span><span class="sxs-lookup"><span data-stu-id="81c9b-119">Explanation</span></span>  
 <span data-ttu-id="81c9b-120">這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫，請連絡，但無法讀取重新執行檔案，因為已損毀。</span><span class="sxs-lookup"><span data-stu-id="81c9b-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="81c9b-121">如果 SSO 無法開啟重新執行檔案，它將繼續進行下一步 重新執行檔案 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="81c9b-121">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  

 <span data-ttu-id="81c9b-122">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="81c9b-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="81c9b-123">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="81c9b-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="81c9b-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="81c9b-124">User Action</span></span>  
 <span data-ttu-id="81c9b-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="81c9b-125">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="81c9b-126">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="81c9b-126">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="81c9b-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="81c9b-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="81c9b-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="81c9b-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="81c9b-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="81c9b-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
