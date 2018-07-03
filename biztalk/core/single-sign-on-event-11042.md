---
title: 單一登入： 事件 11042 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1927bb5-a400-4e3a-8f80-95ef5693216c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 109678e68c3624cec11c4c9f235063288f342f1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985687"
---
# <a name="single-sign-on-event-11042"></a><span data-ttu-id="4da75-102">單一登入： 事件 11042</span><span class="sxs-lookup"><span data-stu-id="4da75-102">Single Sign-On: Event 11042</span></span>
## <a name="details"></a><span data-ttu-id="4da75-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4da75-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="4da75-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4da75-104">Product Name</span></span>   |                                                                                                                                                   <span data-ttu-id="4da75-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4da75-105">Enterprise Single Sign-On</span></span>                                                                                                                                                   |
| <span data-ttu-id="4da75-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="4da75-106">Product Version</span></span> |                                                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                   |
|    <span data-ttu-id="4da75-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4da75-107">Event ID</span></span>     |                                                                                                                                                             <span data-ttu-id="4da75-108">11042</span><span class="sxs-lookup"><span data-stu-id="4da75-108">11042</span></span>                                                                                                                                                             |
|  <span data-ttu-id="4da75-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="4da75-109">Event Source</span></span>   |                                                                                                                                                            <span data-ttu-id="4da75-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4da75-110">ENTSSO</span></span>                                                                                                                                                             |
|    <span data-ttu-id="4da75-111">元件</span><span class="sxs-lookup"><span data-stu-id="4da75-111">Component</span></span>    |                                                                                                                                                              <span data-ttu-id="4da75-112">不適用</span><span class="sxs-lookup"><span data-stu-id="4da75-112">N/A</span></span>                                                                                                                                                              |
|  <span data-ttu-id="4da75-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4da75-113">Symbolic Name</span></span>  |                                                                                                                                                <span data-ttu-id="4da75-114">SSO_WARN_ACCESS_DENIED_ACCOUNTS</span><span class="sxs-lookup"><span data-stu-id="4da75-114">SSO_WARN_ACCESS_DENIED_ACCOUNTS</span></span>                                                                                                                                                |
|  <span data-ttu-id="4da75-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4da75-115">Message Text</span></span>   | <span data-ttu-id="4da75-116">拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="4da75-116">Access denied.</span></span><br /><br /> <span data-ttu-id="4da75-117">用戶端使用者必須是其中一個下列帳戶的成員，才能執行此 function.%r</span><span class="sxs-lookup"><span data-stu-id="4da75-117">The client user must be a member of one of the following accounts to perform this function.%r</span></span><br /><br /> <span data-ttu-id="4da75-118">SSO 系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="4da75-118">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="4da75-119">SSO 分支機構系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="4da75-119">SSO Affiliate Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="4da75-120">應用程式系統管理員: %3 %r</span><span class="sxs-lookup"><span data-stu-id="4da75-120">Application Administrators: %3%r</span></span><br /><br /> <span data-ttu-id="4da75-121">應用程式使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="4da75-121">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="4da75-122">其他資料： %5</span><span class="sxs-lookup"><span data-stu-id="4da75-122">Additional Data: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="4da75-123">說明</span><span class="sxs-lookup"><span data-stu-id="4da75-123">Explanation</span></span>  
 <span data-ttu-id="4da75-124">用戶端使用者必須是其中一個警告，以執行此函式中所列帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="4da75-124">The client user must be a member of one of the accounts listed in the warning to perform this function.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4da75-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4da75-125">User Action</span></span>  
 <span data-ttu-id="4da75-126">您必須將其中一個帳戶來執行這項功能。</span><span class="sxs-lookup"><span data-stu-id="4da75-126">You must join one of the accounts to perform this function.</span></span>