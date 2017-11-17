---
title: "單一登入： 事件 11057 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e165e24-fe43-4899-ab6e-1437f639f534
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca69661d1421433c44472e0572c5d4d4bf76a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11057"></a><span data-ttu-id="ad773-102">單一登入： 事件 11057</span><span class="sxs-lookup"><span data-stu-id="ad773-102">Single Sign-On: Event 11057</span></span>
## <a name="details"></a><span data-ttu-id="ad773-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ad773-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad773-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ad773-104">Product Name</span></span>|<span data-ttu-id="ad773-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ad773-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ad773-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ad773-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ad773-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ad773-107">Event ID</span></span>|<span data-ttu-id="ad773-108">11057</span><span class="sxs-lookup"><span data-stu-id="ad773-108">11057</span></span>|  
|<span data-ttu-id="ad773-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ad773-109">Event Source</span></span>|<span data-ttu-id="ad773-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ad773-110">ENTSSO</span></span>|  
|<span data-ttu-id="ad773-111">元件</span><span class="sxs-lookup"><span data-stu-id="ad773-111">Component</span></span>|<span data-ttu-id="ad773-112">不適用</span><span class="sxs-lookup"><span data-stu-id="ad773-112">N/A</span></span>|  
|<span data-ttu-id="ad773-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ad773-113">Symbolic Name</span></span>|<span data-ttu-id="ad773-114">SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="ad773-114">SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS</span></span>|  
|<span data-ttu-id="ad773-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ad773-115">Message Text</span></span>|<span data-ttu-id="ad773-116">直接密碼變更。</span><span class="sxs-lookup"><span data-stu-id="ad773-116">Direct password change.</span></span> <span data-ttu-id="ad773-117">這種對應的部分遺失外部認證欄位已設為預設值。%r</span><span class="sxs-lookup"><span data-stu-id="ad773-117">Some missing external credential fields for this mapping have been set to default values.%r</span></span><br /><br /> <span data-ttu-id="ad773-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ad773-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="ad773-119">應用程式名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ad773-119">Application Name: %2%r</span></span><br /><br /> <span data-ttu-id="ad773-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="ad773-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="ad773-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="ad773-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad773-122">說明</span><span class="sxs-lookup"><span data-stu-id="ad773-122">Explanation</span></span>  
 <span data-ttu-id="ad773-123">雖然可能可以使用「直接密碼同步」變更密碼，但是此功能只支援一個外部認證欄位。</span><span class="sxs-lookup"><span data-stu-id="ad773-123">While it is possible to change passwords using Direct Password Sync, this feature only supports one external credential field.</span></span> <span data-ttu-id="ad773-124">在本例中，ENTSSO 系統遇到一個以上的外部認證欄位，且將這些欄位設為預設 (空白) 值。</span><span class="sxs-lookup"><span data-stu-id="ad773-124">In this case the ENTSSO System has encountered more than one external credential field, and has set those fields to default (blank) values.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad773-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ad773-125">User Action</span></span>  
 <span data-ttu-id="ad773-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="ad773-126">No user action is necessary.</span></span>