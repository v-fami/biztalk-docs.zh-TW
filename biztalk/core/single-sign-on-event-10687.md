---
title: 單一登入： 事件 10687 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10b3fe2c-a7ba-47e1-a753-4eaa64b01a60
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e928e779d8b2d22a20cc502fb65fd321fb99668c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976471"
---
# <a name="single-sign-on-event-10687"></a><span data-ttu-id="29375-102">單一登入： 事件 10687</span><span class="sxs-lookup"><span data-stu-id="29375-102">Single Sign-On: Event 10687</span></span>
## <a name="details"></a><span data-ttu-id="29375-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="29375-103">Details</span></span>  

|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="29375-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="29375-104">Product Name</span></span>   |                                               <span data-ttu-id="29375-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="29375-105">Enterprise Single Sign-On</span></span>                                               |
| <span data-ttu-id="29375-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="29375-106">Product Version</span></span> |                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                               |
|    <span data-ttu-id="29375-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="29375-107">Event ID</span></span>     |                                                         <span data-ttu-id="29375-108">10687</span><span class="sxs-lookup"><span data-stu-id="29375-108">10687</span></span>                                                         |
|  <span data-ttu-id="29375-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="29375-109">Event Source</span></span>   |                                                        <span data-ttu-id="29375-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="29375-110">ENTSSO</span></span>                                                         |
|    <span data-ttu-id="29375-111">元件</span><span class="sxs-lookup"><span data-stu-id="29375-111">Component</span></span>    |                                                          <span data-ttu-id="29375-112">N\A</span><span class="sxs-lookup"><span data-stu-id="29375-112">N\A</span></span>                                                          |
|  <span data-ttu-id="29375-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="29375-113">Symbolic Name</span></span>  |                                               <span data-ttu-id="29375-114">SSO_INFO_REPLAY_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="29375-114">SSO_INFO_REPLAY_COMPLETE</span></span>                                                |
|  <span data-ttu-id="29375-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="29375-115">Message Text</span></span>   | <span data-ttu-id="29375-116">重新執行預存外部密碼變更已完成。%r</span><span class="sxs-lookup"><span data-stu-id="29375-116">Replay of stored external password changes completed.%r</span></span><br /><br /> <span data-ttu-id="29375-117">重新執行檔案: %1 %r</span><span class="sxs-lookup"><span data-stu-id="29375-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="29375-118">其他資料： %2</span><span class="sxs-lookup"><span data-stu-id="29375-118">Additional Data: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="29375-119">說明</span><span class="sxs-lookup"><span data-stu-id="29375-119">Explanation</span></span>  
 <span data-ttu-id="29375-120">這個資訊事件表示 SSO 已完成重新執行預存外部密碼變更檔案。</span><span class="sxs-lookup"><span data-stu-id="29375-120">This Information event indicates that SSO has completed replaying the stored external password changes file.</span></span> <span data-ttu-id="29375-121">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="29375-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  

## <a name="user-action"></a><span data-ttu-id="29375-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="29375-122">User Action</span></span>  

- <span data-ttu-id="29375-123">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="29375-123">No user action is necessary.</span></span>  

  <span data-ttu-id="29375-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="29375-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="29375-125">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="29375-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="29375-126">密碼同步</span><span class="sxs-lookup"><span data-stu-id="29375-126">Password Synchronization</span></span>](../core/password-synchronization2.md)
