---
title: 單一登入： 事件 11071 |Microsoft 文件
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
ms.openlocfilehash: e744e4f477ee45e6f634e8e4b2ca976754cbecf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276294"
---
# <a name="single-sign-on-event-11071"></a><span data-ttu-id="92069-102">單一登入： 事件 11071</span><span class="sxs-lookup"><span data-stu-id="92069-102">Single Sign-On: Event 11071</span></span>
## <a name="details"></a><span data-ttu-id="92069-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="92069-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92069-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="92069-104">Product Name</span></span>|<span data-ttu-id="92069-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="92069-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="92069-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="92069-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="92069-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="92069-107">Event ID</span></span>|<span data-ttu-id="92069-108">11071</span><span class="sxs-lookup"><span data-stu-id="92069-108">11071</span></span>|  
|<span data-ttu-id="92069-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="92069-109">Event Source</span></span>|<span data-ttu-id="92069-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="92069-110">ENTSSO</span></span>|  
|<span data-ttu-id="92069-111">元件</span><span class="sxs-lookup"><span data-stu-id="92069-111">Component</span></span>|<span data-ttu-id="92069-112">不適用</span><span class="sxs-lookup"><span data-stu-id="92069-112">N/A</span></span>|  
|<span data-ttu-id="92069-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="92069-113">Symbolic Name</span></span>|<span data-ttu-id="92069-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span><span class="sxs-lookup"><span data-stu-id="92069-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span></span>|  
|<span data-ttu-id="92069-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="92069-115">Message Text</span></span>|<span data-ttu-id="92069-116">Windows 密碼變更已被捨棄，因為 Windows 密碼長度為零個字元。%r</span><span class="sxs-lookup"><span data-stu-id="92069-116">A Windows password change was discarded because the Windows password length is zero characters.%r</span></span><br /><br /> <span data-ttu-id="92069-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="92069-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="92069-118">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="92069-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="92069-119">用戶端使用者： %3</span><span class="sxs-lookup"><span data-stu-id="92069-119">Client User: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92069-120">說明</span><span class="sxs-lookup"><span data-stu-id="92069-120">Explanation</span></span>  
 <span data-ttu-id="92069-121">已捨棄 Windows 密碼變更，因為 Windows 密碼長度為零個字元。</span><span class="sxs-lookup"><span data-stu-id="92069-121">A Windows password change was discarded because the Windows password length is zero characters.</span></span> <span data-ttu-id="92069-122">提供的 Windows 帳戶和用戶端使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="92069-122">The Windows account and client user name are provided.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92069-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="92069-123">User Action</span></span>  
 <span data-ttu-id="92069-124">變更密碼，使用您的 SSO 系統所需的字元類型與數量。</span><span class="sxs-lookup"><span data-stu-id="92069-124">Change the password again, using the number and type of characters required by your SSO system.</span></span>