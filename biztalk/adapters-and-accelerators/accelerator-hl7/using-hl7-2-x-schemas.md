---
title: "使用 HL7 2.X 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas
- HL7, 2.X schemas
- schemas, 2.X schemas
ms.assetid: 7f2d7dd4-76f1-463e-b579-9839a74b9631
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 934ca60bb3d89e08c9e803813f3548f196c3d56d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-hl7-2x-schemas"></a><span data-ttu-id="0352a-102">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="0352a-102">Using HL7 2.X Schemas</span></span>
<span data-ttu-id="0352a-103">本章節將討論 2.X 版所支援的健全狀況層級七 (HL7) 標準[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0352a-103">This section discusses the 2.X versions of the Health Level Seven (HL7) standard supported by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0352a-104">您可能需要更新安裝 BTAHL7 以符合標準 HL7 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0352a-104">You may need to update the schemas installed with BTAHL7 to conform to the HL7 standard.</span></span> <span data-ttu-id="0352a-105">若要這樣做，請參閱[解決資料庫錯誤](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="0352a-105">To do so, see [Resolving Database Errors](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0352a-106">BTAHL7 引擎無法處理具有模稜兩可的結構描述結構的 HL7 結構描述不符合的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="0352a-106">The BTAHL7 engine cannot process message instances conforming to HL7 schemas that have an ambiguous schema structure.</span></span> <span data-ttu-id="0352a-107">模稜兩可的結構描述結構是一種標準 HL7 未完全定義。</span><span class="sxs-lookup"><span data-stu-id="0352a-107">An ambiguous schema structure is one that the HL7 standard has not completely defined.</span></span> <span data-ttu-id="0352a-108">這類結構描述包含的訊息類型 CSU 以及 SUR.</span><span class="sxs-lookup"><span data-stu-id="0352a-108">Such schemas include those for message types CSU and SUR.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0352a-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="0352a-109">In This Section</span></span>  
  
-   [<span data-ttu-id="0352a-110">HL7 2.X 版</span><span class="sxs-lookup"><span data-stu-id="0352a-110">HL7 2.X Versions</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-versions.md)  
  
-   [<span data-ttu-id="0352a-111">HL7 2.X 子資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="0352a-111">HL7 2.X Subfolders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md)  
  
-   [<span data-ttu-id="0352a-112">HL7 2.X 通用結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="0352a-112">HL7 2.X Common Schema Files</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)  
  
-   [<span data-ttu-id="0352a-113">擴充 HL7 2.X Z 物件結構描述</span><span class="sxs-lookup"><span data-stu-id="0352a-113">Extending HL7 2.X Schemas with Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)  
  
-   [<span data-ttu-id="0352a-114">解決資料庫錯誤</span><span class="sxs-lookup"><span data-stu-id="0352a-114">Resolving Database Errors</span></span>](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)  
  
-   [<span data-ttu-id="0352a-115">'X' 和 'Y' 選用性</span><span class="sxs-lookup"><span data-stu-id="0352a-115">'X' and 'Y' Optionality</span></span>](../../adapters-and-accelerators/accelerator-hl7/x-and-y-optionality.md)  
  
-   [<span data-ttu-id="0352a-116">可重複的欄位區段</span><span class="sxs-lookup"><span data-stu-id="0352a-116">Repeatable Field Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/repeatable-field-segments.md)