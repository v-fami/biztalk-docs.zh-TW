---
title: "位置記錄的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f383d34-60a6-430f-ab0f-b1fc35cde568
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7d42dd70b91d3e11231f6d140b6c3b217045a0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="positional-record-considerations"></a><span data-ttu-id="45ca1-102">位置記錄的考量</span><span class="sxs-lookup"><span data-stu-id="45ca1-102">Positional Record Considerations</span></span>
<span data-ttu-id="45ca1-103">有許多考量，您應該謹記在心時使用位置**記錄**節點在結構描述內。</span><span class="sxs-lookup"><span data-stu-id="45ca1-103">There are a number of considerations that you should keep in mind when working with positional **Record** nodes within your schemas.</span></span> <span data-ttu-id="45ca1-104">這些考量包括標記處理、巢狀的位置記錄、計算位置的方式，以及計算欄位位置的方式。</span><span class="sxs-lookup"><span data-stu-id="45ca1-104">This includes the considerations about tag handling, positional record nesting, how positions are counted, and how field positions are calculated.</span></span> <span data-ttu-id="45ca1-105">本節提供這些考量的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="45ca1-105">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45ca1-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="45ca1-106">In This Section</span></span>  
  
-   [<span data-ttu-id="45ca1-107">位置記錄中處理標記</span><span class="sxs-lookup"><span data-stu-id="45ca1-107">Tag Handling in Positional Records</span></span>](../core/tag-handling-in-positional-records.md)  
  
-   [<span data-ttu-id="45ca1-108">巢狀序數記錄</span><span class="sxs-lookup"><span data-stu-id="45ca1-108">Nested Positional Records</span></span>](../core/nested-positional-records.md)  
  
-   [<span data-ttu-id="45ca1-109">以位元組為單位計算位置</span><span class="sxs-lookup"><span data-stu-id="45ca1-109">Position Counting in Bytes</span></span>](../core/position-counting-in-bytes.md)  
  
-   [<span data-ttu-id="45ca1-110">欄位位置計算</span><span class="sxs-lookup"><span data-stu-id="45ca1-110">Field Position Calculation</span></span>](../core/field-position-calculation.md)