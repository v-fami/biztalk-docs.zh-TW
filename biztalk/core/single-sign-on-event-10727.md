---
title: 單一登入： 事件 10727 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ff7ac94-6f1e-4e56-853e-efc50b1fa1b6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f25dd71e223452707ff00e23b6a3a3bc797d10f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970543"
---
# <a name="single-sign-on-event-10727"></a><span data-ttu-id="024e4-102">單一登入： 事件 10727</span><span class="sxs-lookup"><span data-stu-id="024e4-102">Single Sign-On: Event 10727</span></span>
## <a name="details"></a><span data-ttu-id="024e4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="024e4-103">Details</span></span>  

|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="024e4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="024e4-104">Product Name</span></span>   |                                                        <span data-ttu-id="024e4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="024e4-105">Enterprise Single Sign-On</span></span>                                                         |
| <span data-ttu-id="024e4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="024e4-106">Product Version</span></span> |                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                        |
|    <span data-ttu-id="024e4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="024e4-107">Event ID</span></span>     |                                                                  <span data-ttu-id="024e4-108">10727</span><span class="sxs-lookup"><span data-stu-id="024e4-108">10727</span></span>                                                                   |
|  <span data-ttu-id="024e4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="024e4-109">Event Source</span></span>   |                                                                  <span data-ttu-id="024e4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="024e4-110">ENTSSO</span></span>                                                                  |
|    <span data-ttu-id="024e4-111">元件</span><span class="sxs-lookup"><span data-stu-id="024e4-111">Component</span></span>    |                                                                   <span data-ttu-id="024e4-112">N\A</span><span class="sxs-lookup"><span data-stu-id="024e4-112">N\A</span></span>                                                                    |
|  <span data-ttu-id="024e4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="024e4-113">Symbolic Name</span></span>  |                                                      <span data-ttu-id="024e4-114">SSO_WARN_REPLAY_RECORD_FAILED</span><span class="sxs-lookup"><span data-stu-id="024e4-114">SSO_WARN_REPLAY_RECORD_FAILED</span></span>                                                       |
|  <span data-ttu-id="024e4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="024e4-115">Message Text</span></span>   | <span data-ttu-id="024e4-116">重新執行預存外部密碼變更 failed.%r</span><span class="sxs-lookup"><span data-stu-id="024e4-116">Replay of the stored external password change failed.%r</span></span><br /><br /> <span data-ttu-id="024e4-117">配接器: %1 %r</span><span class="sxs-lookup"><span data-stu-id="024e4-117">Adapter: %1%r</span></span><br /><br /> <span data-ttu-id="024e4-118">檔案名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="024e4-118">File Name: %2%r</span></span><br /><br /> <span data-ttu-id="024e4-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="024e4-119">Error Code: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="024e4-120">說明</span><span class="sxs-lookup"><span data-stu-id="024e4-120">Explanation</span></span>  
 <span data-ttu-id="024e4-121">這則警告表示 SSO 無法重新執行記錄重新執行檔案中的密碼變更。</span><span class="sxs-lookup"><span data-stu-id="024e4-121">This Warning indicates that SSO was unable to replay a password change recorded in the replay file.</span></span>  

 <span data-ttu-id="024e4-122">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="024e4-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="024e4-123">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="024e4-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="024e4-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="024e4-124">User Action</span></span>  
 <span data-ttu-id="024e4-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="024e4-125">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="024e4-126">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="024e4-126">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="024e4-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="024e4-127">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="024e4-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="024e4-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="024e4-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="024e4-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
