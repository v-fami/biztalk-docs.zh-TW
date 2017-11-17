---
title: "EDI 訊息結構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c9a0447-447f-483c-825d-547c06ad691e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9395ed5e0b03bda48e19d6413f95ca2e74a3f1e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-structure"></a><span data-ttu-id="18d84-102">EDI 訊息結構</span><span class="sxs-lookup"><span data-stu-id="18d84-102">EDI Message Structure</span></span>
<span data-ttu-id="18d84-103">EDI 訊息由一個信封和一系列階層式的結構元素組成。</span><span class="sxs-lookup"><span data-stu-id="18d84-103">EDI messages consist of an envelope and a hierarchical series of structural elements.</span></span> <span data-ttu-id="18d84-104">信封中包含一組標頭和結尾；各組標頭和結尾分別描述及包含一個結構元素。</span><span class="sxs-lookup"><span data-stu-id="18d84-104">The envelope contains a set of headers and trailers, each set of which describes and contains a structural element.</span></span> <span data-ttu-id="18d84-105">這些結構元素如下：</span><span class="sxs-lookup"><span data-stu-id="18d84-105">These structural elements are as follows:</span></span>  
  
```  
Interchange  
   Group  
      Transaction set/message  
         Segment  
            Data Element  
               Sub Element  
```  
  
 <span data-ttu-id="18d84-106">EDI 訊息的階層式結構可讓您批次處理交易集/訊息和群組。</span><span class="sxs-lookup"><span data-stu-id="18d84-106">The hierarchical structure of an EDI message enables transaction sets/messages and groups to be batched.</span></span> <span data-ttu-id="18d84-107">即使交換中只包含一個交易集/訊息和一個群組，在建立該項交換的結構時，也會使用與批次處理時相同的基本結構項目，唯一的不同是這項交換的結構中不會有多個交易集/訊息或群組元素。</span><span class="sxs-lookup"><span data-stu-id="18d84-107">Even if an interchange contains only one transaction set/message and only one group, that interchange is structured with the same basic structural elements that it would have if it were batched, with the exception that there would not be multiple transaction set/message or group elements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18d84-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="18d84-108">In This Section</span></span>  
  
-   [<span data-ttu-id="18d84-109">EDI 標頭和結尾</span><span class="sxs-lookup"><span data-stu-id="18d84-109">EDI Headers and Trailers</span></span>](../core/edi-headers-and-trailers.md)  
  
-   [<span data-ttu-id="18d84-110">EDI 交換結構元素</span><span class="sxs-lookup"><span data-stu-id="18d84-110">EDI Interchange Structural Element</span></span>](../core/edi-interchange-structural-element.md)  
  
-   [<span data-ttu-id="18d84-111">EDI 群組結構元素</span><span class="sxs-lookup"><span data-stu-id="18d84-111">EDI Group Structural Element</span></span>](../core/edi-group-structural-element.md)  
  
-   [<span data-ttu-id="18d84-112">EDI 交易集訊息結構元素</span><span class="sxs-lookup"><span data-stu-id="18d84-112">EDI Transaction Set-Message Structural Element</span></span>](../core/edi-transaction-set-message-structural-element.md)  
  
-   [<span data-ttu-id="18d84-113">EDI 區段結構項目</span><span class="sxs-lookup"><span data-stu-id="18d84-113">EDI Segment Structural Element</span></span>](../core/edi-segment-structural-element.md)  
  
-   [<span data-ttu-id="18d84-114">EDI 資料項目結構元素</span><span class="sxs-lookup"><span data-stu-id="18d84-114">EDI Data Element Structural Element</span></span>](../core/edi-data-element-structural-element.md)