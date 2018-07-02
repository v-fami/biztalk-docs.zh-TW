---
title: 單一登入： 事件 10551 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a014d9fa9adec99a05eba3f4a0f17047e2e1175
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973487"
---
# <a name="single-sign-on-event-10551"></a><span data-ttu-id="18c06-102">單一登入： 事件 10551</span><span class="sxs-lookup"><span data-stu-id="18c06-102">Single Sign-On: Event 10551</span></span>
## <a name="details"></a><span data-ttu-id="18c06-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="18c06-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="18c06-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="18c06-104">Product Name</span></span>   |                                                                                                   <span data-ttu-id="18c06-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="18c06-105">Enterprise Single Sign-On</span></span>                                                                                                   |
| <span data-ttu-id="18c06-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="18c06-106">Product Version</span></span> |                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                   |
|    <span data-ttu-id="18c06-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="18c06-107">Event ID</span></span>     |                                                                                                             <span data-ttu-id="18c06-108">10551</span><span class="sxs-lookup"><span data-stu-id="18c06-108">10551</span></span>                                                                                                             |
|  <span data-ttu-id="18c06-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="18c06-109">Event Source</span></span>   |                                                                                                            <span data-ttu-id="18c06-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="18c06-110">ENTSSO</span></span>                                                                                                             |
|    <span data-ttu-id="18c06-111">元件</span><span class="sxs-lookup"><span data-stu-id="18c06-111">Component</span></span>    |                                                                                                              <span data-ttu-id="18c06-112">不適用</span><span class="sxs-lookup"><span data-stu-id="18c06-112">N/A</span></span>                                                                                                              |
|  <span data-ttu-id="18c06-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="18c06-113">Symbolic Name</span></span>  |                                                                                                     <span data-ttu-id="18c06-114">SSO_WARN_INVALID_USER</span><span class="sxs-lookup"><span data-stu-id="18c06-114">SSO_WARN_INVALID_USER</span></span>                                                                                                     |
|  <span data-ttu-id="18c06-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="18c06-115">Message Text</span></span>   | <span data-ttu-id="18c06-116">無法建立對應，因為此應用程式的指定使用者無效。%r</span><span class="sxs-lookup"><span data-stu-id="18c06-116">A mapping could not be created because the specified user is not valid for this application.%r</span></span><br /><br /> <span data-ttu-id="18c06-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="18c06-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="18c06-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="18c06-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="18c06-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="18c06-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="18c06-120">應用程式使用者： %4</span><span class="sxs-lookup"><span data-stu-id="18c06-120">Application Users: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="18c06-121">說明</span><span class="sxs-lookup"><span data-stu-id="18c06-121">Explanation</span></span>  
 <span data-ttu-id="18c06-122">指定的使用者無效。</span><span class="sxs-lookup"><span data-stu-id="18c06-122">The specified user is not valid.</span></span> <span data-ttu-id="18c06-123">這可能是打字的錯誤。</span><span class="sxs-lookup"><span data-stu-id="18c06-123">This could be a typing error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="18c06-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="18c06-124">User Action</span></span>  
 <span data-ttu-id="18c06-125">檢查警告資訊中列出的使用者名稱，確認它是正確的，然後再次建立對應。</span><span class="sxs-lookup"><span data-stu-id="18c06-125">Check the User Name listed in the warning information, confirm that it is correct, and then create the mapping again.</span></span>