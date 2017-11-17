---
title: "單一登入： 事件 10718 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de075c59-8396-48d1-be55-79303f83f984
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4bf86f4db59033b1ee4202c739ffeda43a587e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10718"></a><span data-ttu-id="95b14-102">單一登入： 事件 10718</span><span class="sxs-lookup"><span data-stu-id="95b14-102">Single Sign-On: Event 10718</span></span>
## <a name="details"></a><span data-ttu-id="95b14-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="95b14-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95b14-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="95b14-104">Product Name</span></span>|<span data-ttu-id="95b14-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="95b14-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="95b14-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="95b14-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="95b14-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="95b14-107">Event ID</span></span>|<span data-ttu-id="95b14-108">10718</span><span class="sxs-lookup"><span data-stu-id="95b14-108">10718</span></span>|  
|<span data-ttu-id="95b14-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="95b14-109">Event Source</span></span>|<span data-ttu-id="95b14-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="95b14-110">ENTSSO</span></span>|  
|<span data-ttu-id="95b14-111">元件</span><span class="sxs-lookup"><span data-stu-id="95b14-111">Component</span></span>|<span data-ttu-id="95b14-112">N\A</span><span class="sxs-lookup"><span data-stu-id="95b14-112">N\A</span></span>|  
|<span data-ttu-id="95b14-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="95b14-113">Symbolic Name</span></span>|<span data-ttu-id="95b14-114">SSO_ERROR_REPLAY_INCORRECT_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="95b14-114">SSO_ERROR_REPLAY_INCORRECT_ADAPTER</span></span>|  
|<span data-ttu-id="95b14-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="95b14-115">Message Text</span></span>|<span data-ttu-id="95b14-116">重新執行或進度 file.%r 中偵測到損毀</span><span class="sxs-lookup"><span data-stu-id="95b14-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="95b14-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="95b14-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="95b14-118">清除配接器名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="95b14-118">Clear Adapter Name: %2%r</span></span><br /><br /> <span data-ttu-id="95b14-119">解密的配接器名稱： %3</span><span class="sxs-lookup"><span data-stu-id="95b14-119">Decrypted Adapter Name: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95b14-120">說明</span><span class="sxs-lookup"><span data-stu-id="95b14-120">Explanation</span></span>  
 <span data-ttu-id="95b14-121">這個錯誤事件表示重新執行檔案或進度檔案中偵測到損毀。</span><span class="sxs-lookup"><span data-stu-id="95b14-121">This Error event indicates that corruption was detected in the replay or progress file.</span></span>  
  
 <span data-ttu-id="95b14-122">因此它可以播放該特定配接器為特定的密碼同步配接器會儲存重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="95b14-122">A replay file is stored for a particular password sync adapter so it can be played back as that particular adapter.</span></span> <span data-ttu-id="95b14-123">配接器名稱會儲存在清除加密形式。</span><span class="sxs-lookup"><span data-stu-id="95b14-123">The adapter name is stored in both clear and encrypted forms.</span></span> <span data-ttu-id="95b14-124">此訊息表示，當重新執行檔案已播放的解密解密的配接器名稱不符合配接器名稱。</span><span class="sxs-lookup"><span data-stu-id="95b14-124">This message indicates that when the replay file was decrypted for playback the decrypted adapter name did not match the adapter name.</span></span> <span data-ttu-id="95b14-125">這可以建議已部分損毀或遭竄改而重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="95b14-125">This can suggest that there has been some corruption or possible tampering with the replay file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95b14-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="95b14-126">User Action</span></span>  
 <span data-ttu-id="95b14-127">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="95b14-127">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="95b14-128">判斷為什麼重新執行檔案的內容可能已修改，請參閱備份是否存在。</span><span class="sxs-lookup"><span data-stu-id="95b14-128">Determine why the contents of the replay file might have been modified, see if a backup exists.</span></span>  
  
-   <span data-ttu-id="95b14-129">檢查是否 SSO 主要密碼已變更或 SSO 服務帳戶已變更，這可能會影響加密行為。</span><span class="sxs-lookup"><span data-stu-id="95b14-129">Check if the SSO master secret was changed or the SSO service account was changed, this could affect encryption behavior.</span></span>  
  
-   <span data-ttu-id="95b14-130">刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="95b14-130">Delete the replay file.</span></span>  
  
 <span data-ttu-id="95b14-131">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="95b14-131">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="95b14-132">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="95b14-132">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="95b14-133">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="95b14-133">Password Synchronization</span></span>](../core/password-synchronization2.md)