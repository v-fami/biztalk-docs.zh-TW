---
title: 單一登入： 事件 11071 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c0f61b9-cd86-482b-a8fe-0093a928c89b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74bc4793937574cc90021b95b6c1850409d57871
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975887"
---
# <a name="single-sign-on-event-11071"></a><span data-ttu-id="f17c6-102">單一登入： 事件 11071</span><span class="sxs-lookup"><span data-stu-id="f17c6-102">Single Sign-On: Event 11071</span></span>
## <a name="details"></a><span data-ttu-id="f17c6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f17c6-103">Details</span></span>  
  
|                 |                                                                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f17c6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f17c6-104">Product Name</span></span>   |                                                                                   <span data-ttu-id="f17c6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f17c6-105">Enterprise Single Sign-On</span></span>                                                                                   |
| <span data-ttu-id="f17c6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f17c6-106">Product Version</span></span> |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                   |
|    <span data-ttu-id="f17c6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f17c6-107">Event ID</span></span>     |                                                                                             <span data-ttu-id="f17c6-108">11071</span><span class="sxs-lookup"><span data-stu-id="f17c6-108">11071</span></span>                                                                                             |
|  <span data-ttu-id="f17c6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f17c6-109">Event Source</span></span>   |                                                                                            <span data-ttu-id="f17c6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f17c6-110">ENTSSO</span></span>                                                                                             |
|    <span data-ttu-id="f17c6-111">元件</span><span class="sxs-lookup"><span data-stu-id="f17c6-111">Component</span></span>    |                                                                                              <span data-ttu-id="f17c6-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f17c6-112">N/A</span></span>                                                                                              |
|  <span data-ttu-id="f17c6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f17c6-113">Symbolic Name</span></span>  |                                                                         <span data-ttu-id="f17c6-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f17c6-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span></span>                                                                          |
|  <span data-ttu-id="f17c6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f17c6-115">Message Text</span></span>   | <span data-ttu-id="f17c6-116">Windows 密碼變更已被捨棄，因為 Windows 密碼長度為零個字元。%r</span><span class="sxs-lookup"><span data-stu-id="f17c6-116">A Windows password change was discarded because the Windows password length is zero characters.%r</span></span><br /><br /> <span data-ttu-id="f17c6-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f17c6-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="f17c6-118">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f17c6-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="f17c6-119">用戶端使用者： %3</span><span class="sxs-lookup"><span data-stu-id="f17c6-119">Client User: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="f17c6-120">說明</span><span class="sxs-lookup"><span data-stu-id="f17c6-120">Explanation</span></span>  
 <span data-ttu-id="f17c6-121">已捨棄 Windows 密碼變更，因為 Windows 密碼長度為零個字元。</span><span class="sxs-lookup"><span data-stu-id="f17c6-121">A Windows password change was discarded because the Windows password length is zero characters.</span></span> <span data-ttu-id="f17c6-122">提供的 Windows 帳戶和用戶端使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f17c6-122">The Windows account and client user name are provided.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f17c6-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f17c6-123">User Action</span></span>  
 <span data-ttu-id="f17c6-124">變更密碼同樣地，使用的 SSO 系統所需的字元類型與數量。</span><span class="sxs-lookup"><span data-stu-id="f17c6-124">Change the password again, using the number and type of characters required by your SSO system.</span></span>