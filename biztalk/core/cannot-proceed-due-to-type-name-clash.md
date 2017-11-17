---
title: "無法繼續，因為型別名稱衝突 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ced6de4-0950-498e-a548-5c85419726d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de1d4962db915a462990962e933c1413a408eee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-proceed-due-to-type-name-clash"></a><span data-ttu-id="cd20c-102">無法繼續，因為型別名稱衝突</span><span class="sxs-lookup"><span data-stu-id="cd20c-102">Cannot proceed due to type name clash</span></span>
## <a name="details"></a><span data-ttu-id="cd20c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cd20c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd20c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cd20c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cd20c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cd20c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cd20c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cd20c-106">Event ID</span></span>|<span data-ttu-id="cd20c-107">0</span><span class="sxs-lookup"><span data-stu-id="cd20c-107">0</span></span>|  
|<span data-ttu-id="cd20c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cd20c-108">Event Source</span></span>|<span data-ttu-id="cd20c-109">0</span><span class="sxs-lookup"><span data-stu-id="cd20c-109">0</span></span>|  
|<span data-ttu-id="cd20c-110">元件</span><span class="sxs-lookup"><span data-stu-id="cd20c-110">Component</span></span>|<span data-ttu-id="cd20c-111">0</span><span class="sxs-lookup"><span data-stu-id="cd20c-111">0</span></span>|  
|<span data-ttu-id="cd20c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cd20c-112">Symbolic Name</span></span>|<span data-ttu-id="cd20c-113">0</span><span class="sxs-lookup"><span data-stu-id="cd20c-113">0</span></span>|  
|<span data-ttu-id="cd20c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cd20c-114">Message Text</span></span>|<span data-ttu-id="cd20c-115">無法繼續，因為型別名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="cd20c-115">Cannot proceed due to type name clash.</span></span> <span data-ttu-id="cd20c-116">命名空間中已經存在名稱為"{0}"</span><span class="sxs-lookup"><span data-stu-id="cd20c-116">The name "{0}" already exists in the namespace</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd20c-117">說明</span><span class="sxs-lookup"><span data-stu-id="cd20c-117">Explanation</span></span>  
 <span data-ttu-id="cd20c-118">此錯誤表示在相同定義的命名空間中的多個成品具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd20c-118">This error indicates multiple artifacts in the same defined namespace have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd20c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cd20c-119">User Action</span></span>  
 <span data-ttu-id="cd20c-120">重新命名相同的命名空間中的成品，或將它們放在不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cd20c-120">Rename the artifacts in the same namespace or put them in a different namespace.</span></span>