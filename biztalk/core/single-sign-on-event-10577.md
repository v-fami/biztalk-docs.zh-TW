---
title: 單一登入： 事件 10577 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4563567a-9ee3-4c32-a202-c2521fd95b6a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 769576430df7ac3ce7ec0ec31a3e7b3eea03968c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003055"
---
# <a name="single-sign-on-event-10577"></a><span data-ttu-id="a0a28-102">單一登入： 事件 10577</span><span class="sxs-lookup"><span data-stu-id="a0a28-102">Single Sign-On: Event 10577</span></span>
## <a name="details"></a><span data-ttu-id="a0a28-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0a28-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a0a28-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a0a28-104">Product Name</span></span>   |                                                                                                             <span data-ttu-id="a0a28-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a0a28-105">Enterprise Single Sign-On</span></span>                                                                                                             |
| <span data-ttu-id="a0a28-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a0a28-106">Product Version</span></span> |                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                             |
|    <span data-ttu-id="a0a28-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a0a28-107">Event ID</span></span>     |                                                                                                                       <span data-ttu-id="a0a28-108">10577</span><span class="sxs-lookup"><span data-stu-id="a0a28-108">10577</span></span>                                                                                                                       |
|  <span data-ttu-id="a0a28-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a0a28-109">Event Source</span></span>   |                                                                                                                      <span data-ttu-id="a0a28-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a0a28-110">ENTSSO</span></span>                                                                                                                       |
|    <span data-ttu-id="a0a28-111">元件</span><span class="sxs-lookup"><span data-stu-id="a0a28-111">Component</span></span>    |                                                                                                                        <span data-ttu-id="a0a28-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a0a28-112">N/A</span></span>                                                                                                                        |
|  <span data-ttu-id="a0a28-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a0a28-113">Symbolic Name</span></span>  |                                                                                                          <span data-ttu-id="a0a28-114">SSO_INFO_CHANGED_SSO_AFF_ADMIN</span><span class="sxs-lookup"><span data-stu-id="a0a28-114">SSO_INFO_CHANGED_SSO_AFF_ADMIN</span></span>                                                                                                           |
|  <span data-ttu-id="a0a28-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a0a28-115">Message Text</span></span>   | <span data-ttu-id="a0a28-116">更新的 SSO 分支機構系統管理員 account.%r</span><span class="sxs-lookup"><span data-stu-id="a0a28-116">Updated SSO Affiliate Administrators account.%r</span></span><br /><br /> <span data-ttu-id="a0a28-117">新的 SSO 分支機構系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a0a28-117">New SSO Affiliate Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="a0a28-118">舊的 SSO 分支機構系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a0a28-118">Old SSO Affiliate Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="a0a28-119">追蹤識別碼: %3 %r</span><span class="sxs-lookup"><span data-stu-id="a0a28-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="a0a28-120">用戶端電腦: %4 %r</span><span class="sxs-lookup"><span data-stu-id="a0a28-120">Client Computer: %4%r</span></span><br /><br /> <span data-ttu-id="a0a28-121">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="a0a28-121">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a0a28-122">說明</span><span class="sxs-lookup"><span data-stu-id="a0a28-122">Explanation</span></span>  
 <span data-ttu-id="a0a28-123">這是參考用訊息，而且可用於追蹤重要的安全性相關事件，會進行 SSO 系統中。</span><span class="sxs-lookup"><span data-stu-id="a0a28-123">This is an informational message and can be useful for tracking significant security-related events that occurr within the SSO system.</span></span> <span data-ttu-id="a0a28-124">此訊息表示已更新的 SSO 分支機構系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0a28-124">This message states that the SSO Affiliate Administrators account has been updated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0a28-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a0a28-125">User Action</span></span>  
 <span data-ttu-id="a0a28-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a0a28-126">No user action is required.</span></span>