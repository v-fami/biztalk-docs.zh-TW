---
title: "單一登入： 事件 10551 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c4b315744749d232c30f4cc28c4d297a0f5243
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10551"></a><span data-ttu-id="a805c-102">單一登入： 事件 10551</span><span class="sxs-lookup"><span data-stu-id="a805c-102">Single Sign-On: Event 10551</span></span>
## <a name="details"></a><span data-ttu-id="a805c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a805c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a805c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a805c-104">Product Name</span></span>|<span data-ttu-id="a805c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a805c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a805c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a805c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a805c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a805c-107">Event ID</span></span>|<span data-ttu-id="a805c-108">10551</span><span class="sxs-lookup"><span data-stu-id="a805c-108">10551</span></span>|  
|<span data-ttu-id="a805c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a805c-109">Event Source</span></span>|<span data-ttu-id="a805c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a805c-110">ENTSSO</span></span>|  
|<span data-ttu-id="a805c-111">元件</span><span class="sxs-lookup"><span data-stu-id="a805c-111">Component</span></span>|<span data-ttu-id="a805c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a805c-112">N/A</span></span>|  
|<span data-ttu-id="a805c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a805c-113">Symbolic Name</span></span>|<span data-ttu-id="a805c-114">SSO_WARN_INVALID_USER</span><span class="sxs-lookup"><span data-stu-id="a805c-114">SSO_WARN_INVALID_USER</span></span>|  
|<span data-ttu-id="a805c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a805c-115">Message Text</span></span>|<span data-ttu-id="a805c-116">無法建立對應，因為此應用程式的指定使用者無效。%r</span><span class="sxs-lookup"><span data-stu-id="a805c-116">A mapping could not be created because the specified user is not valid for this application.%r</span></span><br /><br /> <span data-ttu-id="a805c-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a805c-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="a805c-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a805c-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="a805c-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="a805c-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="a805c-120">應用程式使用者： %4</span><span class="sxs-lookup"><span data-stu-id="a805c-120">Application Users: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a805c-121">說明</span><span class="sxs-lookup"><span data-stu-id="a805c-121">Explanation</span></span>  
 <span data-ttu-id="a805c-122">指定的使用者無效。</span><span class="sxs-lookup"><span data-stu-id="a805c-122">The specified user is not valid.</span></span> <span data-ttu-id="a805c-123">這可能是打字的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a805c-123">This could be a typing error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a805c-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a805c-124">User Action</span></span>  
 <span data-ttu-id="a805c-125">檢查警告資訊中列出的使用者名稱，確認它是正確的，然後再次建立對應。</span><span class="sxs-lookup"><span data-stu-id="a805c-125">Check the User Name listed in the warning information, confirm that it is correct, and then create the mapping again.</span></span>