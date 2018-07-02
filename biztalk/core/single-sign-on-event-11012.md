---
title: 單一登入： 事件 11012 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 252bedc8-8dc3-4962-b078-465f9b064ead
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28f78d834e57a85e05de143612d376b77ebed799
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988007"
---
# <a name="single-sign-on-event-11012"></a><span data-ttu-id="bc758-102">單一登入： 事件 11012</span><span class="sxs-lookup"><span data-stu-id="bc758-102">Single Sign-On: Event 11012</span></span>
## <a name="details"></a><span data-ttu-id="bc758-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bc758-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="bc758-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bc758-104">Product Name</span></span>   |                                                                                               <span data-ttu-id="bc758-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="bc758-105">Enterprise Single Sign-On</span></span>                                                                                                |
| <span data-ttu-id="bc758-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="bc758-106">Product Version</span></span> |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    <span data-ttu-id="bc758-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bc758-107">Event ID</span></span>     |                                                                                                         <span data-ttu-id="bc758-108">11012</span><span class="sxs-lookup"><span data-stu-id="bc758-108">11012</span></span>                                                                                                          |
|  <span data-ttu-id="bc758-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="bc758-109">Event Source</span></span>   |                                                                                                         <span data-ttu-id="bc758-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="bc758-110">ENTSSO</span></span>                                                                                                         |
|    <span data-ttu-id="bc758-111">元件</span><span class="sxs-lookup"><span data-stu-id="bc758-111">Component</span></span>    |                                                                                                          <span data-ttu-id="bc758-112">不適用</span><span class="sxs-lookup"><span data-stu-id="bc758-112">N/A</span></span>                                                                                                           |
|  <span data-ttu-id="bc758-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bc758-113">Symbolic Name</span></span>  |                                                                                           <span data-ttu-id="bc758-114">SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME</span><span class="sxs-lookup"><span data-stu-id="bc758-114">SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME</span></span>                                                                                            |
|  <span data-ttu-id="bc758-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bc758-115">Message Text</span></span>   | <span data-ttu-id="bc758-116">用戶端使用者不是應用程式系統管理員 account.%r 的成員</span><span class="sxs-lookup"><span data-stu-id="bc758-116">Client user is not a member of the Application Administrators account.%r</span></span><br /><br /> <span data-ttu-id="bc758-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="bc758-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="bc758-118">用戶端使用者： %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="bc758-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="bc758-119">應用程式名稱: %4 %r</span><span class="sxs-lookup"><span data-stu-id="bc758-119">Application Name: %4%r</span></span><br /><br /> <span data-ttu-id="bc758-120">應用程式系統管理員： %5</span><span class="sxs-lookup"><span data-stu-id="bc758-120">Application Administrators: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="bc758-121">說明</span><span class="sxs-lookup"><span data-stu-id="bc758-121">Explanation</span></span>  
 <span data-ttu-id="bc758-122">用戶端使用者不是應用程式系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="bc758-122">The client user is not a member of the Application Administrators account.</span></span> <span data-ttu-id="bc758-123">稽核層級設定為高時，才會出現這個警告。</span><span class="sxs-lookup"><span data-stu-id="bc758-123">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bc758-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bc758-124">User Action</span></span>  
 <span data-ttu-id="bc758-125">若要補救這種情況，您必須進行用戶端使用者應用程式系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="bc758-125">To remedy the situation, you must make the client user a member of the Application Administrators account.</span></span> <span data-ttu-id="bc758-126">若要停止這項警告不會出現在未來，您可以降低稽核層級。</span><span class="sxs-lookup"><span data-stu-id="bc758-126">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>