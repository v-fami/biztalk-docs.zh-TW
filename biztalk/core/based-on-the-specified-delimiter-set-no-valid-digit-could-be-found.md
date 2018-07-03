---
title: 根據指定的分隔符號集，有效的數字找不到 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08887f7d-8256-4de3-8db9-b890451521ff
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc117a9c9d08d664f397557ab08f9c6f2e7dc7c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989223"
---
# <a name="based-on-the-specified-delimiter-set-no-valid-digit-could-be-found"></a><span data-ttu-id="d56b9-102">根據指定的分隔符號集，有效的數字找不到</span><span class="sxs-lookup"><span data-stu-id="d56b9-102">Based on the specified delimiter set, no valid Digit could be found</span></span>
## <a name="details"></a><span data-ttu-id="d56b9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d56b9-103">Details</span></span>  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d56b9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d56b9-104">Product Name</span></span>   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| <span data-ttu-id="d56b9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d56b9-105">Product Version</span></span> |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    <span data-ttu-id="d56b9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d56b9-106">Event ID</span></span>     |                                                   -                                                    |
|  <span data-ttu-id="d56b9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d56b9-107">Event Source</span></span>   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d56b9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d56b9-108"> EDI</span></span>         |
|    <span data-ttu-id="d56b9-109">元件</span><span class="sxs-lookup"><span data-stu-id="d56b9-109">Component</span></span>    |                                               <span data-ttu-id="d56b9-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d56b9-110">EDI Engine</span></span>                                               |
|  <span data-ttu-id="d56b9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d56b9-111">Symbolic Name</span></span>  |                                                   -                                                    |
|  <span data-ttu-id="d56b9-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d56b9-112">Message Text</span></span>   | <span data-ttu-id="d56b9-113">根據指定的分隔符號集，無法找到有效的數字。</span><span class="sxs-lookup"><span data-stu-id="d56b9-113">Based on the specified delimiter set, no valid Digit could be found.</span></span> <span data-ttu-id="d56b9-114">請使用另一個分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="d56b9-114">Please use another delimiter set.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d56b9-115">說明</span><span class="sxs-lookup"><span data-stu-id="d56b9-115">Explanation</span></span>  
 <span data-ttu-id="d56b9-116">這個錯誤/警告/資訊事件表示 EDI 傳送管線找不到有效的數字時產生外寄交換，因為欄位的外寄交換中使用的數字分隔符號字元相同。</span><span class="sxs-lookup"><span data-stu-id="d56b9-116">This Error/Warning/Information event indicates that the EDI send pipeline could not find a valid digit when generating an outgoing interchange because a digit used in a field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d56b9-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d56b9-117">User Action</span></span>  
 <span data-ttu-id="d56b9-118">若要解決這個錯誤，變更 EDI 傳送管線用來建立一則訊息，以便任何分隔符號字元會與數字欄位的外寄交換中使用相同的分隔符號值。</span><span class="sxs-lookup"><span data-stu-id="d56b9-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a digit used in a field of the outgoing interchange.</span></span> <span data-ttu-id="d56b9-119">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="d56b9-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d56b9-120">對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="d56b9-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="d56b9-121">對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="d56b9-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="d56b9-122">正在傳送給已解析合作對象的 EDIFACT 交換，變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="d56b9-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="d56b9-123">正在傳送給未解析的合作對象的 EDIFACT 交換，變更 [UNA 區段定義] 全域屬性頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="d56b9-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>