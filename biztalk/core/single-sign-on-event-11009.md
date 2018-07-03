---
title: 單一登入： 事件 11009 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5f06f8c-1614-4538-83e6-689657135776
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96dc58b9f4a0e3fbed894323e2d281b1e9884961
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972119"
---
# <a name="single-sign-on-event-11009"></a><span data-ttu-id="878cc-102">單一登入： 事件 11009</span><span class="sxs-lookup"><span data-stu-id="878cc-102">Single Sign-On: Event 11009</span></span>
## <a name="details"></a><span data-ttu-id="878cc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="878cc-103">Details</span></span>  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="878cc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="878cc-104">Product Name</span></span>   |                                                                      <span data-ttu-id="878cc-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="878cc-105">Enterprise Single Sign-On</span></span>                                                                      |
| <span data-ttu-id="878cc-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="878cc-106">Product Version</span></span> |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    <span data-ttu-id="878cc-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="878cc-107">Event ID</span></span>     |                                                                                <span data-ttu-id="878cc-108">11009</span><span class="sxs-lookup"><span data-stu-id="878cc-108">11009</span></span>                                                                                |
|  <span data-ttu-id="878cc-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="878cc-109">Event Source</span></span>   |                                                                               <span data-ttu-id="878cc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="878cc-110">ENTSSO</span></span>                                                                                |
|    <span data-ttu-id="878cc-111">元件</span><span class="sxs-lookup"><span data-stu-id="878cc-111">Component</span></span>    |                                                                                 <span data-ttu-id="878cc-112">不適用</span><span class="sxs-lookup"><span data-stu-id="878cc-112">N/A</span></span>                                                                                 |
|  <span data-ttu-id="878cc-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="878cc-113">Symbolic Name</span></span>  |                                                                       <span data-ttu-id="878cc-114">SSO_WARN_NOT_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="878cc-114">SSO_WARN_NOT_SSO_ADMIN</span></span>                                                                        |
|  <span data-ttu-id="878cc-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="878cc-115">Message Text</span></span>   | <span data-ttu-id="878cc-116">用戶端使用者不是 SSO 系統管理員 account.%r 的成員</span><span class="sxs-lookup"><span data-stu-id="878cc-116">Client user is not a member of the SSO Administrators account.%r</span></span><br /><br /> <span data-ttu-id="878cc-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="878cc-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="878cc-118">用戶端使用者： %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="878cc-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="878cc-119">SSO 系統管理員： %4</span><span class="sxs-lookup"><span data-stu-id="878cc-119">SSO Administrators: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="878cc-120">說明</span><span class="sxs-lookup"><span data-stu-id="878cc-120">Explanation</span></span>  
 <span data-ttu-id="878cc-121">用戶端使用者不是 SSO 系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="878cc-121">The client user is not a member of the SSO Administrators account.</span></span> <span data-ttu-id="878cc-122">稽核層級設定為高時，才會出現這個警告。</span><span class="sxs-lookup"><span data-stu-id="878cc-122">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="878cc-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="878cc-123">User Action</span></span>  
 <span data-ttu-id="878cc-124">若要補救這種情況，您必須進行用戶端使用者的 SSO 系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="878cc-124">To remedy the situation, you must make the client user a member of the SSO Administrators account.</span></span> <span data-ttu-id="878cc-125">若要停止這項警告不會出現在未來，您可以降低稽核層級。</span><span class="sxs-lookup"><span data-stu-id="878cc-125">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>