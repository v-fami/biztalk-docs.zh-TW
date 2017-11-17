---
title: "Edifact 交易集有 UNT01 不相符的計數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180abe338441917afa6691400a02a42e88026052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a><span data-ttu-id="55289-102">Edifact 交易集有 UNT01 不相符的計數</span><span class="sxs-lookup"><span data-stu-id="55289-102">The Edifact Transaction set had a mismatched count in UNT01</span></span>
## <a name="details"></a><span data-ttu-id="55289-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55289-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55289-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="55289-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="55289-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="55289-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="55289-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="55289-106">Event ID</span></span>|-|  
|<span data-ttu-id="55289-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="55289-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="55289-108">EDI</span><span class="sxs-lookup"><span data-stu-id="55289-108"> EDI</span></span>|  
|<span data-ttu-id="55289-109">元件</span><span class="sxs-lookup"><span data-stu-id="55289-109">Component</span></span>|<span data-ttu-id="55289-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="55289-110">EDI Engine</span></span>|  
|<span data-ttu-id="55289-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="55289-111">Symbolic Name</span></span>|<span data-ttu-id="55289-112">EfactUnhUntCountMismatch</span><span class="sxs-lookup"><span data-stu-id="55289-112">EfactUnhUntCountMismatch</span></span>|  
|<span data-ttu-id="55289-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="55289-113">Message Text</span></span>|<span data-ttu-id="55289-114">Edifact 交易集有 UNT01 不相符的計數。</span><span class="sxs-lookup"><span data-stu-id="55289-114">The Edifact Transaction set had a mismatched count in UNT01.</span></span> <span data-ttu-id="55289-115">UNT01 為 {0}，而它應該已被 {1}。</span><span class="sxs-lookup"><span data-stu-id="55289-115">UNT01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="55289-116">已更正。</span><span class="sxs-lookup"><span data-stu-id="55289-116">It has been corrected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55289-117">說明</span><span class="sxs-lookup"><span data-stu-id="55289-117">Explanation</span></span>  
 <span data-ttu-id="55289-118">這個警告表示 UNT01 欄位，也就是區段計數不符交易集中的區段數目。</span><span class="sxs-lookup"><span data-stu-id="55289-118">This Warning indicates that the UNT01 field, which is the segment count, did not match the number of segments in the transaction set.</span></span> <span data-ttu-id="55289-119">UNT01 值已變更或損毀，或是新增或刪除之後發現計數區段。</span><span class="sxs-lookup"><span data-stu-id="55289-119">Either the value of UNT01 was changed or corrupted, or segments were added or deleted after the count was determined.</span></span> <span data-ttu-id="55289-120">傳送管線重 UNT01 欄位設為正確的區段數目，然後傳送交換。</span><span class="sxs-lookup"><span data-stu-id="55289-120">The send pipeline reset the UNT01 field to the correct number of segments, and then sent the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55289-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="55289-121">User Action</span></span>  
 <span data-ttu-id="55289-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="55289-122">No user action is necessary.</span></span>