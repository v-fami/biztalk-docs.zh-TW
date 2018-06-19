---
title: 根據指定的分隔符號集，沒有有效的日期值可能會產生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdd157c0-9a0d-421b-8350-aa1263126ca0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 747d00c7628853d3a99f007f70701311d25c22bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230814"
---
# <a name="based-on-the-specified-delimiter-set-no-valid-date-value-could-be-generated"></a><span data-ttu-id="eb08b-102">根據指定的分隔符號集，沒有有效的日期值可能會產生</span><span class="sxs-lookup"><span data-stu-id="eb08b-102">Based on the specified delimiter set, no valid Date value could be generated</span></span>
## <a name="details"></a><span data-ttu-id="eb08b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eb08b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb08b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="eb08b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eb08b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="eb08b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eb08b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="eb08b-106">Event ID</span></span>|-|  
|<span data-ttu-id="eb08b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="eb08b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eb08b-108">EDI</span><span class="sxs-lookup"><span data-stu-id="eb08b-108"> EDI</span></span>|  
|<span data-ttu-id="eb08b-109">元件</span><span class="sxs-lookup"><span data-stu-id="eb08b-109">Component</span></span>|<span data-ttu-id="eb08b-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="eb08b-110">EDI Engine</span></span>|  
|<span data-ttu-id="eb08b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="eb08b-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="eb08b-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="eb08b-112">Message Text</span></span>|<span data-ttu-id="eb08b-113">根據指定的分隔符號集，無法產生沒有有效的日期值。</span><span class="sxs-lookup"><span data-stu-id="eb08b-113">Based on the specified delimiter set, no valid Date value could be generated.</span></span> <span data-ttu-id="eb08b-114">請使用另一個的分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="eb08b-114">Please use another delimiter set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eb08b-115">說明</span><span class="sxs-lookup"><span data-stu-id="eb08b-115">Explanation</span></span>  
 <span data-ttu-id="eb08b-116">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法產生有效的日期值，因為日期欄位的外寄交換中使用的字元是分隔符號字元相同。</span><span class="sxs-lookup"><span data-stu-id="eb08b-116">This Error/Warning/Information event indicates that the EDI send pipeline could not generate a valid date value because a character used in a Date field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eb08b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="eb08b-117">User Action</span></span>  
 <span data-ttu-id="eb08b-118">若要解決這個錯誤，變更分隔符號值用於 edi 傳送管線，建立一則訊息，如此分隔符號的字元將日期欄位的外寄交換中使用字元相同。</span><span class="sxs-lookup"><span data-stu-id="eb08b-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a character used in a Date field of the outgoing interchange.</span></span> <span data-ttu-id="eb08b-119">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="eb08b-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="eb08b-120">對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="eb08b-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="eb08b-121">對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="eb08b-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="eb08b-122">EDIFACT 交換傳送至合作對象解析變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。</span><span class="sxs-lookup"><span data-stu-id="eb08b-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="eb08b-123">針對傳送至合作對象已解析的 EDIFACT 交換，變更分隔符號設定 UNA 區段定義 全域屬性頁面中。</span><span class="sxs-lookup"><span data-stu-id="eb08b-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>