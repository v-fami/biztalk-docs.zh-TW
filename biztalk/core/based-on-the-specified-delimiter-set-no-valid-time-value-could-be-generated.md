---
title: "根據指定的分隔符號集，沒有有效的時間值可能會產生 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e22958-e1fa-474d-85a2-aa69e05b7228
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00b8b06922109ae5817c67b26f1a23977d1b607b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="based-on-the-specified-delimiter-set-no-valid-time-value-could-be-generated"></a><span data-ttu-id="36052-102">根據指定的分隔符號集，沒有有效的時間值無法產生</span><span class="sxs-lookup"><span data-stu-id="36052-102">Based on the specified delimiter set, no valid Time value could be generated</span></span>
## <a name="details"></a><span data-ttu-id="36052-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="36052-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36052-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="36052-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="36052-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="36052-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="36052-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="36052-106">Event ID</span></span>|-|  
|<span data-ttu-id="36052-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="36052-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="36052-108">EDI</span><span class="sxs-lookup"><span data-stu-id="36052-108"> EDI</span></span>|  
|<span data-ttu-id="36052-109">元件</span><span class="sxs-lookup"><span data-stu-id="36052-109">Component</span></span>|<span data-ttu-id="36052-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="36052-110">EDI Engine</span></span>|  
|<span data-ttu-id="36052-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="36052-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="36052-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="36052-112">Message Text</span></span>|<span data-ttu-id="36052-113">根據指定的分隔符號集，無法產生任何有效的時間值。</span><span class="sxs-lookup"><span data-stu-id="36052-113">Based on the specified delimiter set, no valid Time value could be generated.</span></span> <span data-ttu-id="36052-114">請使用另一個的分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="36052-114">Please use another delimiter set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="36052-115">說明</span><span class="sxs-lookup"><span data-stu-id="36052-115">Explanation</span></span>  
 <span data-ttu-id="36052-116">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法產生有效的時間值，因為時間欄位的外寄交換中使用的字元是分隔符號字元相同。</span><span class="sxs-lookup"><span data-stu-id="36052-116">This Error/Warning/Information event indicates that the EDI send pipeline could not generate a valid time value because a character used in a time field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36052-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="36052-117">User Action</span></span>  
 <span data-ttu-id="36052-118">若要解決這個錯誤，變更 EDI 傳送管線用來建立一則訊息，以便任何分隔字元是字元，在時間欄位中使用相同的分隔符號值。</span><span class="sxs-lookup"><span data-stu-id="36052-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character is the same as a character used in a time field.</span></span> <span data-ttu-id="36052-119">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="36052-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="36052-120">對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="36052-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="36052-121">對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="36052-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="36052-122">EDIFACT 交換傳送至合作對象解析變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="36052-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="36052-123">針對傳送至合作對象已解析的 EDIFACT 交換，變更分隔符號設定 UNA 區段定義 全域屬性頁面中。</span><span class="sxs-lookup"><span data-stu-id="36052-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>