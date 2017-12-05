---
title: "相關活動 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], related activities
- Query Builder [BAM portal], related activities
- queries [BAM], related activities
- Query Builder [BAM portal], viewing details
- queries [BAM], viewing details
ms.assetid: 141b7943-d244-4810-aa88-12aa4a2b7658
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f50e4de965e8f1efaa1454bb9123317ae904f7e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="related-activities"></a><span data-ttu-id="b5614-102">相關活動</span><span class="sxs-lookup"><span data-stu-id="b5614-102">Related Activities</span></span>
<span data-ttu-id="b5614-103">[相關活動] 區域包含與查詢基礎活動相關的活動清單。</span><span class="sxs-lookup"><span data-stu-id="b5614-103">The Related Activities area contains a list of activities that are related to the activity on which the query is based.</span></span> <span data-ttu-id="b5614-104">多個「出貨」活動便是「訂單」活動之相關活動的典型範例，因為單一訂單上的項目可以分成多次出貨來交運。</span><span class="sxs-lookup"><span data-stu-id="b5614-104">An example of a related activity for a Purchase Order activity would be multiple Shipment activities, since items on a single purchase order can be delivered in multiple shipments.</span></span>  
  
## <a name="creating-related-activities"></a><span data-ttu-id="b5614-105">建立相關活動</span><span class="sxs-lookup"><span data-stu-id="b5614-105">Creating related activities</span></span>  
 <span data-ttu-id="b5614-106">相關活動的清單可以由下列兩種方式產生：</span><span class="sxs-lookup"><span data-stu-id="b5614-106">The list of related activities is generated in one of two ways:</span></span>  
  
-   <span data-ttu-id="b5614-107">定義兩個活動，然後建立包含這兩個活動的單一檢視。</span><span class="sxs-lookup"><span data-stu-id="b5614-107">You define two activities and then create a single view that includes both of them.</span></span> <span data-ttu-id="b5614-108">開發人員可以透過實作活動間的索引鍵、欄位和數值關係，藉此在這兩個活動之間建立相互關聯連接。</span><span class="sxs-lookup"><span data-stu-id="b5614-108">Your developer makes a correlation connection between the two by implementing the key, field, and value relationships between the activities.</span></span>  
  
-   <span data-ttu-id="b5614-109">定義兩個活動。</span><span class="sxs-lookup"><span data-stu-id="b5614-109">You define two activities.</span></span> <span data-ttu-id="b5614-110">您的開發人員在自訂應用程式中建立相互關聯連接，藉由呼叫 AddRelationship() 定義索引鍵、 欄位和值在活動之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b5614-110">Your developer makes a correlation connection in your custom application by calling AddRelationship() and defining the key, field, and value relationships between the activities.</span></span>  
  
 <span data-ttu-id="b5614-111">其中一種方式來定義活動關係中加入資料列\<activityname\>_Relationships 資料表。</span><span class="sxs-lookup"><span data-stu-id="b5614-111">Defining the activity relationships in either of these ways adds a row in the \<activityname\>_Relationships table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5614-112">只有第一種定義關係的方法可以使相關活動彼此間存在即時連結。</span><span class="sxs-lookup"><span data-stu-id="b5614-112">Only the first method of defining relationships results in the related activities having live links to each other.</span></span> <span data-ttu-id="b5614-113">第二種方法不會定義跨距檢視，因此，入口網站無法得知兩個活動之間的關係。</span><span class="sxs-lookup"><span data-stu-id="b5614-113">The second method does not define a spanning view and therefore the portal cannot know about the relationship between the two activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5614-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5614-114">See Also</span></span>  
 [<span data-ttu-id="b5614-115">如何檢視活動搜尋的結果</span><span class="sxs-lookup"><span data-stu-id="b5614-115">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)