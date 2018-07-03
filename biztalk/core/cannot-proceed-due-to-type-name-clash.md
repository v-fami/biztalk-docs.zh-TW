---
title: 無法繼續，因為類型名稱衝突 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ced6de4-0950-498e-a548-5c85419726d8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742d537f2329c53cd974abbaac9a6b9f7f8f5126
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008479"
---
# <a name="cannot-proceed-due-to-type-name-clash"></a><span data-ttu-id="049d0-102">無法繼續，因為類型名稱衝突</span><span class="sxs-lookup"><span data-stu-id="049d0-102">Cannot proceed due to type name clash</span></span>
## <a name="details"></a><span data-ttu-id="049d0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="049d0-103">Details</span></span>  
  
|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
|  <span data-ttu-id="049d0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="049d0-104">Product Name</span></span>   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="049d0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="049d0-105">Product Version</span></span> |              [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    <span data-ttu-id="049d0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="049d0-106">Event ID</span></span>     |                                           <span data-ttu-id="049d0-107">0</span><span class="sxs-lookup"><span data-stu-id="049d0-107">0</span></span>                                           |
|  <span data-ttu-id="049d0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="049d0-108">Event Source</span></span>   |                                           <span data-ttu-id="049d0-109">0</span><span class="sxs-lookup"><span data-stu-id="049d0-109">0</span></span>                                           |
|    <span data-ttu-id="049d0-110">元件</span><span class="sxs-lookup"><span data-stu-id="049d0-110">Component</span></span>    |                                           <span data-ttu-id="049d0-111">0</span><span class="sxs-lookup"><span data-stu-id="049d0-111">0</span></span>                                           |
|  <span data-ttu-id="049d0-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="049d0-112">Symbolic Name</span></span>  |                                           <span data-ttu-id="049d0-113">0</span><span class="sxs-lookup"><span data-stu-id="049d0-113">0</span></span>                                           |
|  <span data-ttu-id="049d0-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="049d0-114">Message Text</span></span>   | <span data-ttu-id="049d0-115">無法繼續，因為類型名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="049d0-115">Cannot proceed due to type name clash.</span></span> <span data-ttu-id="049d0-116">名稱"{0}"已經存在於的命名空間</span><span class="sxs-lookup"><span data-stu-id="049d0-116">The name "{0}" already exists in the namespace</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="049d0-117">說明</span><span class="sxs-lookup"><span data-stu-id="049d0-117">Explanation</span></span>  
 <span data-ttu-id="049d0-118">此錯誤表示在同一個定義的命名空間中的多個成品具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="049d0-118">This error indicates multiple artifacts in the same defined namespace have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="049d0-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="049d0-119">User Action</span></span>  
 <span data-ttu-id="049d0-120">重新命名相同的命名空間中的成品，或將它們放在不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="049d0-120">Rename the artifacts in the same namespace or put them in a different namespace.</span></span>