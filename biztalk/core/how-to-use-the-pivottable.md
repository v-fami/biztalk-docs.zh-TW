---
title: 如何使用樞紐分析表 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM views, pivot tables
- BAM views, previewing data
ms.assetid: af34494b-f577-4d36-9a9e-5d6e9c5fafbe
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed416f7a04392804c4c031a69940c4229eabe99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256654"
---
# <a name="how-to-use-the-pivottable"></a><span data-ttu-id="2b167-102">如何使用樞紐分析表</span><span class="sxs-lookup"><span data-stu-id="2b167-102">How to Use the PivotTable</span></span>
<span data-ttu-id="2b167-103">在定義包含維度和量值的 BAM 檢視之後，您必須更新一或多個與該檢視關聯的樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="2b167-103">When you have defined a BAM view that includes dimensions and measures, you need to update one or more PivotTables associated with that view.</span></span>  
  
 <span data-ttu-id="2b167-104">Excel 中的樞紐分析表是可供您用來輕鬆組合及比較大量資料的互動式表格。</span><span class="sxs-lookup"><span data-stu-id="2b167-104">A PivotTable report in Excel is an interactive table that enables you to easily combine and compare large amounts of data.</span></span> <span data-ttu-id="2b167-105">您可以旋轉資料列與資料行中的值來查看所顯示資料的不同摘要。</span><span class="sxs-lookup"><span data-stu-id="2b167-105">The values in its rows and columns can be rotated to look at different summaries of the displayed data.</span></span> <span data-ttu-id="2b167-106">您也可以使用樞紐分析表來執行資料的計算，如彙總計數或平均。</span><span class="sxs-lookup"><span data-stu-id="2b167-106">A PivotTable also enables you perform calculations on the data, such as aggregate counts or averages.</span></span>  
  
 <span data-ttu-id="2b167-107">若要在建立樞紐分析表之後加以使用，請依照下列程序中的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="2b167-107">To use the PivotTable after you have created it, follow the steps in this procedure.</span></span> <span data-ttu-id="2b167-108">如需有關使用樞紐分析表的詳細資訊，請參閱 Microsoft Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="2b167-108">For more information about using PivotTables, see the Microsoft Excel documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b167-109">建立即時彙總樞紐分析表時，此表格最多可以包含 14 個維度層級。</span><span class="sxs-lookup"><span data-stu-id="2b167-109">When you create a real-time aggregation pivot table, it can contain a maximum of 14 dimension levels.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b167-110">如果在 Excel 工作表中定義了多個樞紐分析表，且活動傳回大型的資料集，則產生的表格可能會增大而彼此重疊。</span><span class="sxs-lookup"><span data-stu-id="2b167-110">If you define multiple PivotTables on the Excel Worksheet, it is possible the resulting tables can grow and overlap each other if the Activity returns a large dataset.</span></span> <span data-ttu-id="2b167-111">在此案例中，當您在重新整理資料時，會收到「樞紐分析表不能重疊在另一個樞紐分析表之上」的訊息。</span><span class="sxs-lookup"><span data-stu-id="2b167-111">In this scenario, you will receive "A PivotTable report cannot overlap another PivotTable report" when you refresh the data.</span></span> <span data-ttu-id="2b167-112">您可以在樞紐分析表之間新增資料行或資料列，讓表格增大而不彼此重疊，藉此修正這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b167-112">You can correct this error by adding addition columns or rows between the pivot tables to allow the tables to grow with out overlapping.</span></span>  
  
### <a name="to-use-the-pivottable"></a><span data-ttu-id="2b167-113">使用樞紐分析表</span><span class="sxs-lookup"><span data-stu-id="2b167-113">To use the PivotTable</span></span>  
  
1.  <span data-ttu-id="2b167-114">建立要搭配樞紐分析表使用的 BAM 檢視。</span><span class="sxs-lookup"><span data-stu-id="2b167-114">Create a BAM view to be used with a PivotTable.</span></span> <span data-ttu-id="2b167-115">如需有關建立 BAM 檢視的詳細資訊，請參閱[定義商務活動檢視](../core/defining-a-bam-view.md)</span><span class="sxs-lookup"><span data-stu-id="2b167-115">For more information about creating a BAM view, see [Defining a Business Activity View](../core/defining-a-bam-view.md)</span></span>  
  
2.  <span data-ttu-id="2b167-116">使用**樞紐分析表欄位清單**，拖放一個或多個可用維度放到樞紐分析表範本的資料行和資料列區域。</span><span class="sxs-lookup"><span data-stu-id="2b167-116">Using the **PivotTable Field List**, drag-and-drop one or more available dimensions into the column and row areas of the PivotTable template.</span></span>  
  
3.  <span data-ttu-id="2b167-117">使用**樞紐分析表欄位清單**，拖放一個或多個可用的量值放到資料的項目區域的樞紐分析表範本。</span><span class="sxs-lookup"><span data-stu-id="2b167-117">Using the  **PivotTable Field List**, drag-and-drop one or more available measures into the data items area of the PivotTable template.</span></span>  
  
     <span data-ttu-id="2b167-118">更新樞紐分析表時，您將會發現其中已填入範例資料。</span><span class="sxs-lookup"><span data-stu-id="2b167-118">As you are updating the PivotTable, you will notice that it is populated with sample data.</span></span> <span data-ttu-id="2b167-119">這樣可以協助您判斷如何設定樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="2b167-119">This helps you determine how the PivotTable should be configured.</span></span>  
  
4.  <span data-ttu-id="2b167-120">使用**樞紐分析表**關聯圖表與樞紐分析表 工具列。</span><span class="sxs-lookup"><span data-stu-id="2b167-120">Using the **PivotTable** toolbar, associate a chart with the PivotTable.</span></span>  
  
5.  <span data-ttu-id="2b167-121">儲存 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="2b167-121">Save your Excel workbook.</span></span>