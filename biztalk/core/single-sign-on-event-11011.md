---
title: 單一登入： 事件 11011 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ef430a-fb3b-4bf7-936f-a866262a6c3a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ba98bf7fb3f57fdf9ce082028f2fff9ea7f618
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972967"
---
# <a name="single-sign-on-event-11011"></a><span data-ttu-id="89e49-102">單一登入： 事件 11011</span><span class="sxs-lookup"><span data-stu-id="89e49-102">Single Sign-On: Event 11011</span></span>
## <a name="details"></a><span data-ttu-id="89e49-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="89e49-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="89e49-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="89e49-104">Product Name</span></span>   |                                                                                               <span data-ttu-id="89e49-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="89e49-105">Enterprise Single Sign-On</span></span>                                                                                                |
| <span data-ttu-id="89e49-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="89e49-106">Product Version</span></span> |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    <span data-ttu-id="89e49-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="89e49-107">Event ID</span></span>     |                                                                                                         <span data-ttu-id="89e49-108">11011</span><span class="sxs-lookup"><span data-stu-id="89e49-108">11011</span></span>                                                                                                          |
|  <span data-ttu-id="89e49-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="89e49-109">Event Source</span></span>   |                                                                                                         <span data-ttu-id="89e49-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="89e49-110">ENTSSO</span></span>                                                                                                         |
|    <span data-ttu-id="89e49-111">元件</span><span class="sxs-lookup"><span data-stu-id="89e49-111">Component</span></span>    |                                                                                                          <span data-ttu-id="89e49-112">不適用</span><span class="sxs-lookup"><span data-stu-id="89e49-112">N/A</span></span>                                                                                                           |
|  <span data-ttu-id="89e49-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="89e49-113">Symbolic Name</span></span>  |                                                                                                 <span data-ttu-id="89e49-114">SSO_WARN_NOT_APP_ADMIN</span><span class="sxs-lookup"><span data-stu-id="89e49-114">SSO_WARN_NOT_APP_ADMIN</span></span>                                                                                                 |
|  <span data-ttu-id="89e49-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="89e49-115">Message Text</span></span>   | <span data-ttu-id="89e49-116">用戶端使用者不是應用程式系統管理員 account.%r 的成員</span><span class="sxs-lookup"><span data-stu-id="89e49-116">Client user is not a member of the Application Administrators account.%r</span></span><br /><br /> <span data-ttu-id="89e49-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="89e49-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="89e49-118">用戶端使用者： %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="89e49-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="89e49-119">應用程式名稱: %4 %r</span><span class="sxs-lookup"><span data-stu-id="89e49-119">Application Name: %4%r</span></span><br /><br /> <span data-ttu-id="89e49-120">應用程式系統管理員： %5</span><span class="sxs-lookup"><span data-stu-id="89e49-120">Application Administrators: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="89e49-121">說明</span><span class="sxs-lookup"><span data-stu-id="89e49-121">Explanation</span></span>  
 <span data-ttu-id="89e49-122">用戶端使用者不是應用程式系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="89e49-122">The client user is not a member of the Application Administrators account.</span></span> <span data-ttu-id="89e49-123">稽核層級設定為高時，才會出現這個警告。</span><span class="sxs-lookup"><span data-stu-id="89e49-123">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89e49-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="89e49-124">User Action</span></span>  
 <span data-ttu-id="89e49-125">若要補救這種情況，您必須進行用戶端使用者應用程式系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="89e49-125">To remedy the situation, you must make the client user a member of the Application Administrators account.</span></span> <span data-ttu-id="89e49-126">若要停止這項警告不會出現在未來，您可以降低稽核層級。</span><span class="sxs-lookup"><span data-stu-id="89e49-126">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>