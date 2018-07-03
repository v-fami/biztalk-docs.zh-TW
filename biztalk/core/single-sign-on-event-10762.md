---
title: 單一登入： 事件 10762 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 905c59062f8f4af397872f3f7d4434a67b19842e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996007"
---
# <a name="single-sign-on-event-10762"></a><span data-ttu-id="d0512-102">單一登入： 事件 10762</span><span class="sxs-lookup"><span data-stu-id="d0512-102">Single Sign-On: Event 10762</span></span>
## <a name="details"></a><span data-ttu-id="d0512-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d0512-103">Details</span></span>  
  
|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d0512-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d0512-104">Product Name</span></span>   |                                                   <span data-ttu-id="d0512-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d0512-105">Enterprise Single Sign-On</span></span>                                                    |
| <span data-ttu-id="d0512-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d0512-106">Product Version</span></span> |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    <span data-ttu-id="d0512-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d0512-107">Event ID</span></span>     |                                                             <span data-ttu-id="d0512-108">10762</span><span class="sxs-lookup"><span data-stu-id="d0512-108">10762</span></span>                                                              |
|  <span data-ttu-id="d0512-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d0512-109">Event Source</span></span>   |                                                             <span data-ttu-id="d0512-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d0512-110">ENTSSO</span></span>                                                             |
|    <span data-ttu-id="d0512-111">元件</span><span class="sxs-lookup"><span data-stu-id="d0512-111">Component</span></span>    |                                                              <span data-ttu-id="d0512-112">不適用</span><span class="sxs-lookup"><span data-stu-id="d0512-112">N/A</span></span>                                                               |
|  <span data-ttu-id="d0512-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d0512-113">Symbolic Name</span></span>  |                                                     <span data-ttu-id="d0512-114">ENTSSO_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="d0512-114">ENTSSO_E_WRONG_THREAD</span></span>                                                      |
|  <span data-ttu-id="d0512-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d0512-115">Message Text</span></span>   | <span data-ttu-id="d0512-116">SSO 用戶端元件已經在錯誤的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0512-116">The SSO client component has been called on the wrong thread.</span></span> <span data-ttu-id="d0512-117">因為它有一項交易，所以目前被鎖定至執行緒。</span><span class="sxs-lookup"><span data-stu-id="d0512-117">It is currently locked to a thread because it has a transaction.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d0512-118">說明</span><span class="sxs-lookup"><span data-stu-id="d0512-118">Explanation</span></span>  
 <span data-ttu-id="d0512-119">它們並沒有交易時，元件可以只是多執行緒。</span><span class="sxs-lookup"><span data-stu-id="d0512-119">Components can only be multi-threaded when they do not have a transaction.</span></span> <span data-ttu-id="d0512-120">此元件會有交易，因此它已鎖定至執行緒。</span><span class="sxs-lookup"><span data-stu-id="d0512-120">This component has a transaction so it is locked to a thread.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0512-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d0512-121">User Action</span></span>  
 <span data-ttu-id="d0512-122">設定您的應用程式，讓它將不會呼叫 SSO 用戶端元件在多個執行緒上使用交易時。</span><span class="sxs-lookup"><span data-stu-id="d0512-122">Configure your application so that it will not call SSO client components on multiple threads when using transactions.</span></span>