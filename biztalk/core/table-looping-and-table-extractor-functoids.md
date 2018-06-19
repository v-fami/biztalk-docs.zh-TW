---
title: 表格迴圈和表格擷取程式運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2907aada-f11a-485c-85c8-03092803ccf7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d4433255ac00d51c88b45bd1a2b5205bd1c735
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278358"
---
# <a name="table-looping-and-table-extractor-functoids"></a><span data-ttu-id="d2d42-102">表格迴圈和表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="d2d42-102">Table Looping and Table Extractor Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="d2d42-103">概觀</span><span class="sxs-lookup"><span data-stu-id="d2d42-103">Overview</span></span>
<span data-ttu-id="d2d42-104">在對應中，輸入執行個體訊息中的每個結構通常在輸出執行個體訊息中有一個結構。</span><span class="sxs-lookup"><span data-stu-id="d2d42-104">In a map, you commonly have one structure in the output instance message for each structure in the input instance message.</span></span> <span data-ttu-id="d2d42-105">然而，有時候您也會需要建立輸入執行個體結構，以便產生多重輸出執行個體結構。</span><span class="sxs-lookup"><span data-stu-id="d2d42-105">However, there are cases when you need an input instance structure to produce multiple output instance structures.</span></span> <span data-ttu-id="d2d42-106">您可以使用表格驅動迴圈來建立可產生這類多重結構的對應。</span><span class="sxs-lookup"><span data-stu-id="d2d42-106">Table-driven looping enables you to create maps generating such multiple structures.</span></span>  
  
 <span data-ttu-id="d2d42-107">表格驅動迴圈使用**表格迴圈**運算質和**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="d2d42-107">Table-driven looping uses the **Table Looping** functoid and the **Table Extractor** functoid.</span></span> <span data-ttu-id="d2d42-108">**表格迴圈**運算質有您所設定的內部資料表。</span><span class="sxs-lookup"><span data-stu-id="d2d42-108">The **Table Looping** functoid has an internal table you configure.</span></span> <span data-ttu-id="d2d42-109">每個輸入記錄或欄位，**表格迴圈**運算質會輸出一次一個資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="d2d42-109">For each input record or field, the **Table Looping** functoid outputs the rows of the table, one at a time.</span></span> <span data-ttu-id="d2d42-110">例如，如果有十筆記錄，在輸入執行個體訊息和內部資料表中的兩個資料列**表格迴圈**，運算質最後總共 20 個資料列，每十筆記錄輸出。</span><span class="sxs-lookup"><span data-stu-id="d2d42-110">For example, if there are ten records in the input instance message and two rows in the internal table of the **Table Looping**, the functoid outputs a total of twenty rows, two for each of the ten records.</span></span> <span data-ttu-id="d2d42-111">**表格抽選程式**運算質從一個資料列擷取所需的項目，並將它傳遞到輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="d2d42-111">The **Table Extractor** functoid extracts the desired item from a row and passes it on to the output instance message.</span></span>  
  
 <span data-ttu-id="d2d42-112">如需詳細資訊，請參閱**表格迴圈運算質參考**和**表格抽選程式運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2d42-112">For more details, see the **Table Looping Functoid Reference** and **Table Extractor Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="d2d42-113">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="d2d42-113">Next steps</span></span>
  
-   [<span data-ttu-id="d2d42-114">表格迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="d2d42-114">Table Looping Functoid</span></span>](../core/table-looping-functoid.md)  
  
-   [<span data-ttu-id="d2d42-115">表格抽選程式運算質</span><span class="sxs-lookup"><span data-stu-id="d2d42-115">Table Extractor Functoid</span></span>](../core/table-extractor-functoid.md)  
  
-   [<span data-ttu-id="d2d42-116">表格驅動迴圈組態</span><span class="sxs-lookup"><span data-stu-id="d2d42-116">Table-Driven Looping Configuration</span></span>](../core/table-driven-looping-configuration.md)  
  
-   [<span data-ttu-id="d2d42-117">表格驅動迴圈範例</span><span class="sxs-lookup"><span data-stu-id="d2d42-117">Table-Driven Looping Example</span></span>](../core/table-driven-looping-example.md)