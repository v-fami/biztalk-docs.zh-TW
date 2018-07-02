---
title: 單一登入： 事件 10612 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9d9e6f5-06b8-4989-a0dc-6e2e5980443b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fdc86dd2143bf8b2b4c27dab66cc4c06ddff5ae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973015"
---
# <a name="single-sign-on-event-10612"></a><span data-ttu-id="869a8-102">單一登入： 事件 10612</span><span class="sxs-lookup"><span data-stu-id="869a8-102">Single Sign-On: Event 10612</span></span>
## <a name="details"></a><span data-ttu-id="869a8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="869a8-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="869a8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="869a8-104">Product Name</span></span>   |                                                                                                                            <span data-ttu-id="869a8-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="869a8-105">Enterprise Single Sign-On</span></span>                                                                                                                            |
| <span data-ttu-id="869a8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="869a8-106">Product Version</span></span> |                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                            |
|    <span data-ttu-id="869a8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="869a8-107">Event ID</span></span>     |                                                                                                                                      <span data-ttu-id="869a8-108">10612</span><span class="sxs-lookup"><span data-stu-id="869a8-108">10612</span></span>                                                                                                                                      |
|  <span data-ttu-id="869a8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="869a8-109">Event Source</span></span>   |                                                                                                                                     <span data-ttu-id="869a8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="869a8-110">ENTSSO</span></span>                                                                                                                                      |
|    <span data-ttu-id="869a8-111">元件</span><span class="sxs-lookup"><span data-stu-id="869a8-111">Component</span></span>    |                                                                                                                                       <span data-ttu-id="869a8-112">不適用</span><span class="sxs-lookup"><span data-stu-id="869a8-112">N/A</span></span>                                                                                                                                       |
|  <span data-ttu-id="869a8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="869a8-113">Symbolic Name</span></span>  |                                                                                                                          <span data-ttu-id="869a8-114">SSO_WARN_TRANSACTION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="869a8-114">SSO_WARN_TRANSACTION_TIMEOUT</span></span>                                                                                                                           |
|  <span data-ttu-id="869a8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="869a8-115">Message Text</span></span>   | <span data-ttu-id="869a8-116">交易逾時超過建議的最大，這項作業。</span><span class="sxs-lookup"><span data-stu-id="869a8-116">The transaction time-out exceeds the recommended maximum for this operation.</span></span> <span data-ttu-id="869a8-117">請參閱 details.%r 文件</span><span class="sxs-lookup"><span data-stu-id="869a8-117">See documentation for details.%r</span></span><br /><br /> <span data-ttu-id="869a8-118">交易識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="869a8-118">Transaction ID: %1%r</span></span><br /><br /> <span data-ttu-id="869a8-119">交易逾時: （輸入 0 表示無限逾時） 的 %2 分鐘 %r</span><span class="sxs-lookup"><span data-stu-id="869a8-119">Transaction time-out: %2 minutes (zero indicates an infinite time-out)%r</span></span><br /><br /> <span data-ttu-id="869a8-120">最大建議的值： %3 分鐘</span><span class="sxs-lookup"><span data-stu-id="869a8-120">Recommended maximum: %3 minutes</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="869a8-121">說明</span><span class="sxs-lookup"><span data-stu-id="869a8-121">Explanation</span></span>  
 <span data-ttu-id="869a8-122">交易已進入系統的非常大型的逾時值。</span><span class="sxs-lookup"><span data-stu-id="869a8-122">A transaction has entered the system with an exceedingly large timeout value.</span></span> <span data-ttu-id="869a8-123">如果鎖定長時間執行交易時，ENTSSO 系統就會輪詢 SSO 資料庫，系統會最後變成離線。</span><span class="sxs-lookup"><span data-stu-id="869a8-123">If the ENTSSO system polls the SSO database while it’s locked by a long-running transaction, the system will eventually go offline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="869a8-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="869a8-124">User Action</span></span>  
 <span data-ttu-id="869a8-125">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="869a8-125">No user action is required.</span></span>