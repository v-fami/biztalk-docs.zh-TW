---
title: 根據指定的分隔符號集，產生有效的識別碼可能是 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ab5f018-b56f-4e3c-97e4-f9ea4258f6d9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d27cc4321826c824e93e43f94408bc08afc386ee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005663"
---
# <a name="based-on-the-specified-delimiter-set-no-valid-id-could-be-generated"></a><span data-ttu-id="5c12c-102">根據指定的分隔符號集，無法產生有效的識別碼</span><span class="sxs-lookup"><span data-stu-id="5c12c-102">Based on the specified delimiter set, no valid ID could be generated</span></span>
## <a name="details"></a><span data-ttu-id="5c12c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5c12c-103">Details</span></span>  
  
|                 |                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5c12c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5c12c-104">Product Name</span></span>   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]            |
| <span data-ttu-id="5c12c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5c12c-105">Product Version</span></span> |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                        |
|    <span data-ttu-id="5c12c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5c12c-106">Event ID</span></span>     |                                                    -                                                    |
|  <span data-ttu-id="5c12c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5c12c-107">Event Source</span></span>   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5c12c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5c12c-108"> EDI</span></span>          |
|    <span data-ttu-id="5c12c-109">元件</span><span class="sxs-lookup"><span data-stu-id="5c12c-109">Component</span></span>    |                                               <span data-ttu-id="5c12c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5c12c-110">EDI Engine</span></span>                                                |
|  <span data-ttu-id="5c12c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5c12c-111">Symbolic Name</span></span>  |                                                    -                                                    |
|  <span data-ttu-id="5c12c-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5c12c-112">Message Text</span></span>   | <span data-ttu-id="5c12c-113">根據指定的分隔符號集，無法產生有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5c12c-113">Based on the specified delimiter set, no valid ID could be generated.</span></span> <span data-ttu-id="5c12c-114">請使用另一個分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="5c12c-114">Please use another delimiter set.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="5c12c-115">說明</span><span class="sxs-lookup"><span data-stu-id="5c12c-115">Explanation</span></span>  
 <span data-ttu-id="5c12c-116">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法產生有效的識別碼值因為識別項欄位的外寄交換中使用的字元是分隔符號字元相同。</span><span class="sxs-lookup"><span data-stu-id="5c12c-116">This Error/Warning/Information event indicates that the EDI send pipeline could not generate a valid ID value because a character used in an identifier field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c12c-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5c12c-117">User Action</span></span>  
 <span data-ttu-id="5c12c-118">若要解決這個錯誤，EDI 所使用的分隔符號值的變更會傳送管線，以建立一則訊息，以便任何分隔符號字元會與識別碼欄位的外寄交換中使用的字元相同。</span><span class="sxs-lookup"><span data-stu-id="5c12c-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a character used in an identifier field of the outgoing interchange.</span></span> <span data-ttu-id="5c12c-119">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="5c12c-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5c12c-120">對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="5c12c-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="5c12c-121">對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="5c12c-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="5c12c-122">正在傳送給已解析合作對象的 EDIFACT 交換，變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="5c12c-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="5c12c-123">正在傳送給未解析的合作對象的 EDIFACT 交換，變更 [UNA 區段定義] 全域屬性頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="5c12c-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>