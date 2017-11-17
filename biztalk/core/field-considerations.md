---
title: "欄位考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7f1853-60ed-49c2-a592-61bde5445d36
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 861f8d8bacb7c0110c9ccbfdf55f8f0547c79bad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-considerations"></a><span data-ttu-id="9b18c-102">欄位考量</span><span class="sxs-lookup"><span data-stu-id="9b18c-102">Field Considerations</span></span>
<span data-ttu-id="9b18c-103">有許多考量使用時，應謹記在心**欄位項目**和**欄位屬性**節點在結構描述內。</span><span class="sxs-lookup"><span data-stu-id="9b18c-103">There are a number of considerations that you should keep in mind when working with **Field Element** and **Field Attribute** nodes within your schemas.</span></span> <span data-ttu-id="9b18c-104">這包括有關使用這些節點類型之時機的基本區別，以及與欄位長度、欄位對齊和欄位填補等規格相關的特定考量。</span><span class="sxs-lookup"><span data-stu-id="9b18c-104">This includes the basic distinctions regarding when to use each of these nodes types, as well as more specific considerations related to the specification of field lengths, field justification, and field padding.</span></span> <span data-ttu-id="9b18c-105">本節提供這些考量的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9b18c-105">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b18c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="9b18c-106">In This Section</span></span>  
  
-   [<span data-ttu-id="9b18c-107">欄位項目節點與。欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="9b18c-107">Field Element Nodes vs. Field Attribute Nodes</span></span>](../core/field-element-nodes-vs-field-attribute-nodes.md)  
  
-   [<span data-ttu-id="9b18c-108">自訂日期時間格式</span><span class="sxs-lookup"><span data-stu-id="9b18c-108">Custom Date-Time Formats</span></span>](../core/custom-date-time-formats.md)  
  
-   [<span data-ttu-id="9b18c-109">欄位填補</span><span class="sxs-lookup"><span data-stu-id="9b18c-109">Field Padding</span></span>](../core/field-padding.md)  
  
-   [<span data-ttu-id="9b18c-110">欄位左右對齊</span><span class="sxs-lookup"><span data-stu-id="9b18c-110">Field Justification</span></span>](../core/field-justification.md)  
  
-   [<span data-ttu-id="9b18c-111">在位置記錄中欄位位置的規格</span><span class="sxs-lookup"><span data-stu-id="9b18c-111">Specification of Field Positions within Positional Records</span></span>](../core/specification-of-field-positions-within-positional-records.md)  
  
-   [<span data-ttu-id="9b18c-112">分隔記錄中的最小欄位長度</span><span class="sxs-lookup"><span data-stu-id="9b18c-112">Minimum Field Lengths Within Delimited Records</span></span>](../core/minimum-field-lengths-within-delimited-records.md)