---
title: "單一登入： 事件 10762 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 487fbeb0f077950605432861a9118eacd93f2c89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10762"></a><span data-ttu-id="b9768-102">單一登入： 事件 10762</span><span class="sxs-lookup"><span data-stu-id="b9768-102">Single Sign-On: Event 10762</span></span>
## <a name="details"></a><span data-ttu-id="b9768-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9768-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9768-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b9768-104">Product Name</span></span>|<span data-ttu-id="b9768-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b9768-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b9768-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b9768-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b9768-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b9768-107">Event ID</span></span>|<span data-ttu-id="b9768-108">10762</span><span class="sxs-lookup"><span data-stu-id="b9768-108">10762</span></span>|  
|<span data-ttu-id="b9768-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b9768-109">Event Source</span></span>|<span data-ttu-id="b9768-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b9768-110">ENTSSO</span></span>|  
|<span data-ttu-id="b9768-111">元件</span><span class="sxs-lookup"><span data-stu-id="b9768-111">Component</span></span>|<span data-ttu-id="b9768-112">不適用</span><span class="sxs-lookup"><span data-stu-id="b9768-112">N/A</span></span>|  
|<span data-ttu-id="b9768-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b9768-113">Symbolic Name</span></span>|<span data-ttu-id="b9768-114">ENTSSO_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="b9768-114">ENTSSO_E_WRONG_THREAD</span></span>|  
|<span data-ttu-id="b9768-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b9768-115">Message Text</span></span>|<span data-ttu-id="b9768-116">SSO 用戶端元件已經在錯誤的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="b9768-116">The SSO client component has been called on the wrong thread.</span></span> <span data-ttu-id="b9768-117">因為它有一項交易，所以目前被鎖定至執行緒。</span><span class="sxs-lookup"><span data-stu-id="b9768-117">It is currently locked to a thread because it has a transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9768-118">說明</span><span class="sxs-lookup"><span data-stu-id="b9768-118">Explanation</span></span>  
 <span data-ttu-id="b9768-119">元件只能是多執行緒時不需要交易。</span><span class="sxs-lookup"><span data-stu-id="b9768-119">Components can only be multi-threaded when they do not have a transaction.</span></span> <span data-ttu-id="b9768-120">這個元件有交易，所以它已鎖定至執行緒。</span><span class="sxs-lookup"><span data-stu-id="b9768-120">This component has a transaction so it is locked to a thread.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9768-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b9768-121">User Action</span></span>  
 <span data-ttu-id="b9768-122">設定您的應用程式，讓它不會呼叫 SSO 用戶端元件在多個執行緒上使用交易時。</span><span class="sxs-lookup"><span data-stu-id="b9768-122">Configure your application so that it will not call SSO client components on multiple threads when using transactions.</span></span>