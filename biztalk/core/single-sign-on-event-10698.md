---
title: 單一登入： 事件 10698 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f467934d-fef5-4962-a341-18f272d84108
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aacd272480ddb58de38960ae8dc1a744815ced64
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966471"
---
# <a name="single-sign-on-event-10698"></a><span data-ttu-id="efd68-102">單一登入： 事件 10698</span><span class="sxs-lookup"><span data-stu-id="efd68-102">Single Sign-On: Event 10698</span></span>
## <a name="details"></a><span data-ttu-id="efd68-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="efd68-103">Details</span></span>  

|                 |                                                                      |
|-----------------|----------------------------------------------------------------------|
|  <span data-ttu-id="efd68-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="efd68-104">Product Name</span></span>   |                      <span data-ttu-id="efd68-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="efd68-105">Enterprise Single Sign-On</span></span>                       |
| <span data-ttu-id="efd68-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="efd68-106">Product Version</span></span> |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    <span data-ttu-id="efd68-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="efd68-107">Event ID</span></span>     |                                <span data-ttu-id="efd68-108">10698</span><span class="sxs-lookup"><span data-stu-id="efd68-108">10698</span></span>                                 |
|  <span data-ttu-id="efd68-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="efd68-109">Event Source</span></span>   |                                <span data-ttu-id="efd68-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="efd68-110">ENTSSO</span></span>                                |
|    <span data-ttu-id="efd68-111">元件</span><span class="sxs-lookup"><span data-stu-id="efd68-111">Component</span></span>    |                                 <span data-ttu-id="efd68-112">N\A</span><span class="sxs-lookup"><span data-stu-id="efd68-112">N\A</span></span>                                  |
|  <span data-ttu-id="efd68-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="efd68-113">Symbolic Name</span></span>  |                     <span data-ttu-id="efd68-114">SSO_INFO_REPLAY_FILE_DELETED</span><span class="sxs-lookup"><span data-stu-id="efd68-114">SSO_INFO_REPLAY_FILE_DELETED</span></span>                     |
|  <span data-ttu-id="efd68-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="efd68-115">Message Text</span></span>   | <span data-ttu-id="efd68-116">重新執行或進度檔案已刪除。%r</span><span class="sxs-lookup"><span data-stu-id="efd68-116">The replay or progress file was deleted.%r</span></span><br /><br /> <span data-ttu-id="efd68-117">檔案名稱： %1</span><span class="sxs-lookup"><span data-stu-id="efd68-117">File Name: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="efd68-118">說明</span><span class="sxs-lookup"><span data-stu-id="efd68-118">Explanation</span></span>  
 <span data-ttu-id="efd68-119">這個資訊事件表示 SSO 已刪除重新執行和/或進度檔案。</span><span class="sxs-lookup"><span data-stu-id="efd68-119">This Information event indicates that SSO has deleted a replay and\or progress file.</span></span>  

 <span data-ttu-id="efd68-120">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="efd68-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="efd68-121">進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。</span><span class="sxs-lookup"><span data-stu-id="efd68-121">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  

## <a name="user-action"></a><span data-ttu-id="efd68-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="efd68-122">User Action</span></span>  

- <span data-ttu-id="efd68-123">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="efd68-123">No user action is necessary.</span></span>  

  <span data-ttu-id="efd68-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="efd68-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="efd68-125">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="efd68-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="efd68-126">密碼同步</span><span class="sxs-lookup"><span data-stu-id="efd68-126">Password Synchronization</span></span>](../core/password-synchronization2.md)
