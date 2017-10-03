---
title: "分隔記錄的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f93dd94-6ab1-4ae0-801d-e44e722d6f09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc6cbd642717b485a1be5cefab07f6a8298d638a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimited-record-considerations"></a><span data-ttu-id="9ebbf-102">分隔記錄的考量</span><span class="sxs-lookup"><span data-stu-id="9ebbf-102">Delimited Record Considerations</span></span>
<span data-ttu-id="9ebbf-103">有許多考量，您應該謹記在心時使用分隔**記錄**節點在結構描述內。</span><span class="sxs-lookup"><span data-stu-id="9ebbf-103">There are a number of considerations that you should keep in mind when working with delimited **Record** nodes within your schemas.</span></span> <span data-ttu-id="9ebbf-104">這包括附屬節點與其分隔符號的相對順序、組合訊息的一般檔案表示法時可選擇省略分隔符號的情況，以及與混合分隔和位置記錄有關的限制。</span><span class="sxs-lookup"><span data-stu-id="9ebbf-104">This includes the considerations about the order of subordinate nodes relative to their delimiters, cases in which you can choose to omit delimiters when assembling the flat file representation of a message, and restrictions regarding the intermixing of delimited and positional records.</span></span> <span data-ttu-id="9ebbf-105">本節提供這些考量的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9ebbf-105">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ebbf-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="9ebbf-106">In This Section</span></span>  
  
-   [<span data-ttu-id="9ebbf-107">分隔記錄中處理標記</span><span class="sxs-lookup"><span data-stu-id="9ebbf-107">Tag Handling in Delimited Records</span></span>](../core/tag-handling-in-delimited-records.md)  
  
-   [<span data-ttu-id="9ebbf-108">子順序考量</span><span class="sxs-lookup"><span data-stu-id="9ebbf-108">Child Order Considerations</span></span>](../core/child-order-considerations.md)  
  
-   [<span data-ttu-id="9ebbf-109">保留和隱藏分隔符號</span><span class="sxs-lookup"><span data-stu-id="9ebbf-109">Delimiter Preservation and Suppression</span></span>](../core/delimiter-preservation-and-suppression.md)