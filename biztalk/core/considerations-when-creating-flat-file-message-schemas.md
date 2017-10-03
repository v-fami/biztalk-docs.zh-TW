---
title: "考量當建立一般檔案訊息結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52271b17-4f0b-4286-a462-cd5951ae49aa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d0cbe19b85fc65c492f1e0ae377da94dad75baf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-creating-flat-file-message-schemas"></a><span data-ttu-id="f1cfb-102">考量當建立一般檔案訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="f1cfb-102">Considerations When Creating Flat File Message Schemas</span></span>
<span data-ttu-id="f1cfb-103">使用一般檔案訊息結構描述時有一些考量。</span><span class="sxs-lookup"><span data-stu-id="f1cfb-103">There are a number of considerations when working with flat file message schemas.</span></span> <span data-ttu-id="f1cfb-104">這包括適用於所有一般檔案訊息結構描述的考量，以及只適用於序數記錄、分隔記錄、序數欄位或分隔欄位的考量。</span><span class="sxs-lookup"><span data-stu-id="f1cfb-104">This includes considerations that apply to all flat file schemas, as well as considerations that apply specifically to positional records, delimited records, positional fields, or delimited fields.</span></span> <span data-ttu-id="f1cfb-105">還有一些關於如何將其他特殊字元解譯為一般資料的考量。</span><span class="sxs-lookup"><span data-stu-id="f1cfb-105">There are also considerations about how to interpret otherwise special characters as regular data.</span></span> <span data-ttu-id="f1cfb-106">本節提供這些考量的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f1cfb-106">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1cfb-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1cfb-107">In This Section</span></span>  
  
-   [<span data-ttu-id="f1cfb-108">一般檔案結構描述的字碼頁規格</span><span class="sxs-lookup"><span data-stu-id="f1cfb-108">Code Page Specification for Flat File Schemas</span></span>](../core/code-page-specification-for-flat-file-schemas.md)  
  
-   [<span data-ttu-id="f1cfb-109">在 一般檔案結構描述中處理的案例</span><span class="sxs-lookup"><span data-stu-id="f1cfb-109">Case Handling in Flat File Schemas</span></span>](../core/case-handling-in-flat-file-schemas.md)  
  
-   [<span data-ttu-id="f1cfb-110">限制的字元範圍</span><span class="sxs-lookup"><span data-stu-id="f1cfb-110">Restricted Character Ranges</span></span>](../core/restricted-character-ranges.md)  
  
-   [<span data-ttu-id="f1cfb-111">巢狀位置和分隔記錄</span><span class="sxs-lookup"><span data-stu-id="f1cfb-111">Nested Positional and Delimited Records</span></span>](../core/nested-positional-and-delimited-records.md)  
  
-   [<span data-ttu-id="f1cfb-112">位置記錄的考量</span><span class="sxs-lookup"><span data-stu-id="f1cfb-112">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)  
  
-   [<span data-ttu-id="f1cfb-113">分隔記錄的考量</span><span class="sxs-lookup"><span data-stu-id="f1cfb-113">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)  
  
-   [<span data-ttu-id="f1cfb-114">欄位考量</span><span class="sxs-lookup"><span data-stu-id="f1cfb-114">Field Considerations</span></span>](../core/field-considerations.md)  
  
-   [<span data-ttu-id="f1cfb-115">如何將特殊字元解譯為欄位值的一部分</span><span class="sxs-lookup"><span data-stu-id="f1cfb-115">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)