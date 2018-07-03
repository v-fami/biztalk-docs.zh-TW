---
title: 單一登入： 事件 11031 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f90be8f631bbd9503de3401bc84d27af32aa991a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015079"
---
# <a name="single-sign-on-event-11031"></a><span data-ttu-id="1151c-102">單一登入： 事件 11031</span><span class="sxs-lookup"><span data-stu-id="1151c-102">Single Sign-On: Event 11031</span></span>
## <a name="details"></a><span data-ttu-id="1151c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1151c-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1151c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1151c-104">Product Name</span></span>   |                                                                                                                                <span data-ttu-id="1151c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1151c-105">Enterprise Single Sign-On</span></span>                                                                                                                                |
| <span data-ttu-id="1151c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1151c-106">Product Version</span></span> |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    <span data-ttu-id="1151c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1151c-107">Event ID</span></span>     |                                                                                                                                          <span data-ttu-id="1151c-108">11031</span><span class="sxs-lookup"><span data-stu-id="1151c-108">11031</span></span>                                                                                                                                          |
|  <span data-ttu-id="1151c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1151c-109">Event Source</span></span>   |                                                                                                                                         <span data-ttu-id="1151c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1151c-110">ENTSSO</span></span>                                                                                                                                          |
|    <span data-ttu-id="1151c-111">元件</span><span class="sxs-lookup"><span data-stu-id="1151c-111">Component</span></span>    |                                                                                                                                           <span data-ttu-id="1151c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="1151c-112">N/A</span></span>                                                                                                                                           |
|  <span data-ttu-id="1151c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1151c-113">Symbolic Name</span></span>  |                                                                                                                         <span data-ttu-id="1151c-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span><span class="sxs-lookup"><span data-stu-id="1151c-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span></span>                                                                                                                          |
|  <span data-ttu-id="1151c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1151c-115">Message Text</span></span>   | <span data-ttu-id="1151c-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="1151c-116">Windows password change.</span></span> <span data-ttu-id="1151c-117">已偵測到此 Windows 帳戶的對應，但忽略，因為它已經 valid.%r</span><span class="sxs-lookup"><span data-stu-id="1151c-117">A mapping for this Windows account has been detected but ignored because it is no longer valid.%r</span></span><br /><br /> <span data-ttu-id="1151c-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="1151c-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="1151c-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="1151c-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="1151c-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="1151c-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="1151c-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="1151c-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="1151c-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="1151c-122">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1151c-123">說明</span><span class="sxs-lookup"><span data-stu-id="1151c-123">Explanation</span></span>  
 <span data-ttu-id="1151c-124">它可能是 Windows 帳戶存在且有效，但並非應用程式使用者帳戶中。</span><span class="sxs-lookup"><span data-stu-id="1151c-124">It may be that the Windows account exists and is valid, but is not in the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1151c-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1151c-125">User Action</span></span>  
 <span data-ttu-id="1151c-126">刪除對應，然後再次嘗試重新建立它。</span><span class="sxs-lookup"><span data-stu-id="1151c-126">Delete the mapping and try to recreate it.</span></span>