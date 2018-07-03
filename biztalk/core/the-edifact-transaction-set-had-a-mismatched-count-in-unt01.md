---
title: Edifact 交易集在 UNT01 中有不相符的計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717260f8e45298c19756707ed042b97ab6e207fb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016045"
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a><span data-ttu-id="a308c-102">Edifact 交易集在 UNT01 中有不相符的計數</span><span class="sxs-lookup"><span data-stu-id="a308c-102">The Edifact Transaction set had a mismatched count in UNT01</span></span>
## <a name="details"></a><span data-ttu-id="a308c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a308c-103">Details</span></span>  
  
|                 |                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a308c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a308c-104">Product Name</span></span>   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| <span data-ttu-id="a308c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a308c-105">Product Version</span></span> |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    <span data-ttu-id="a308c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a308c-106">Event ID</span></span>     |                                                                  -                                                                  |
|  <span data-ttu-id="a308c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a308c-107">Event Source</span></span>   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a308c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a308c-108"> EDI</span></span>                        |
|    <span data-ttu-id="a308c-109">元件</span><span class="sxs-lookup"><span data-stu-id="a308c-109">Component</span></span>    |                                                             <span data-ttu-id="a308c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a308c-110">EDI Engine</span></span>                                                              |
|  <span data-ttu-id="a308c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a308c-111">Symbolic Name</span></span>  |                                                      <span data-ttu-id="a308c-112">EfactUnhUntCountMismatch</span><span class="sxs-lookup"><span data-stu-id="a308c-112">EfactUnhUntCountMismatch</span></span>                                                       |
|  <span data-ttu-id="a308c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a308c-113">Message Text</span></span>   | <span data-ttu-id="a308c-114">Edifact 交易集在 UNT01 中有不相符的計數。</span><span class="sxs-lookup"><span data-stu-id="a308c-114">The Edifact Transaction set had a mismatched count in UNT01.</span></span> <span data-ttu-id="a308c-115">UNT01 已{0}，但它應該是{1}。</span><span class="sxs-lookup"><span data-stu-id="a308c-115">UNT01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="a308c-116">已更正。</span><span class="sxs-lookup"><span data-stu-id="a308c-116">It has been corrected.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a308c-117">說明</span><span class="sxs-lookup"><span data-stu-id="a308c-117">Explanation</span></span>  
 <span data-ttu-id="a308c-118">這則警告表示 UNT01 欄位，也就是區段計數，不符的交易集的區段數目。</span><span class="sxs-lookup"><span data-stu-id="a308c-118">This Warning indicates that the UNT01 field, which is the segment count, did not match the number of segments in the transaction set.</span></span> <span data-ttu-id="a308c-119">UNT01 值已變更或損毀，或是加入或刪除之後決定計數區段。</span><span class="sxs-lookup"><span data-stu-id="a308c-119">Either the value of UNT01 was changed or corrupted, or segments were added or deleted after the count was determined.</span></span> <span data-ttu-id="a308c-120">傳送管線重 UNT01 欄位設為正確的區段數目，然後傳送交換。</span><span class="sxs-lookup"><span data-stu-id="a308c-120">The send pipeline reset the UNT01 field to the correct number of segments, and then sent the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a308c-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a308c-121">User Action</span></span>  
 <span data-ttu-id="a308c-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a308c-122">No user action is necessary.</span></span>