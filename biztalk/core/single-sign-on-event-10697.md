---
title: 單一登入： 事件 10697 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4263ecbd-939e-4374-b0b6-aada3b2af900
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991d17351ddbaa998c0f7c90774e1615f3bc472e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980399"
---
# <a name="single-sign-on-event-10697"></a><span data-ttu-id="0785c-102">單一登入： 事件 10697</span><span class="sxs-lookup"><span data-stu-id="0785c-102">Single Sign-On: Event 10697</span></span>
## <a name="details"></a><span data-ttu-id="0785c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0785c-103">Details</span></span>  

|                 |                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0785c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0785c-104">Product Name</span></span>   |                                           <span data-ttu-id="0785c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0785c-105">Enterprise Single Sign-On</span></span>                                           |
| <span data-ttu-id="0785c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0785c-106">Product Version</span></span> |                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                           |
|    <span data-ttu-id="0785c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0785c-107">Event ID</span></span>     |                                                     <span data-ttu-id="0785c-108">10697</span><span class="sxs-lookup"><span data-stu-id="0785c-108">10697</span></span>                                                     |
|  <span data-ttu-id="0785c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0785c-109">Event Source</span></span>   |                                                    <span data-ttu-id="0785c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0785c-110">ENTSSO</span></span>                                                     |
|    <span data-ttu-id="0785c-111">元件</span><span class="sxs-lookup"><span data-stu-id="0785c-111">Component</span></span>    |                                                      <span data-ttu-id="0785c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0785c-112">N\A</span></span>                                                      |
|  <span data-ttu-id="0785c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0785c-113">Symbolic Name</span></span>  |                                       <span data-ttu-id="0785c-114">SSO_ERROR_PROGRESS_FILE_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="0785c-114">SSO_ERROR_PROGRESS_FILE_MISMATCH</span></span>                                        |
|  <span data-ttu-id="0785c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0785c-115">Message Text</span></span>   | <span data-ttu-id="0785c-116">進度 file.%r 中偵測到損毀</span><span class="sxs-lookup"><span data-stu-id="0785c-116">Corruption was detected in the progress file.%r</span></span><br /><br /> <span data-ttu-id="0785c-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="0785c-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="0785c-118">其他資料： %2</span><span class="sxs-lookup"><span data-stu-id="0785c-118">Additional Data: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="0785c-119">說明</span><span class="sxs-lookup"><span data-stu-id="0785c-119">Explanation</span></span>  
 <span data-ttu-id="0785c-120">這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫，請連絡，但無法使用對應的重新執行檔案，開啟因為不符的進度檔案。</span><span class="sxs-lookup"><span data-stu-id="0785c-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to open the progress file because of a mismatch with the corresponding replay file.</span></span> <span data-ttu-id="0785c-121">如果 SSO 無法開啟進行檔案，就會開始在第一個重新執行檔案的開頭記錄。</span><span class="sxs-lookup"><span data-stu-id="0785c-121">If SSO cannot open a progress file, it will start at the beginning record of the first replay file.</span></span>  

 <span data-ttu-id="0785c-122">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="0785c-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="0785c-123">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="0785c-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="0785c-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0785c-124">User Action</span></span>  
 <span data-ttu-id="0785c-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0785c-125">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="0785c-126">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0785c-126">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="0785c-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="0785c-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="0785c-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="0785c-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="0785c-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="0785c-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
