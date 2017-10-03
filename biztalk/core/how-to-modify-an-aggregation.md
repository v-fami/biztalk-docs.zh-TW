---
title: "如何修改彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], modifying
- BAM portal, aggregations
ms.assetid: dd5ce211-32d3-4e1d-8ee0-1225ec2c45fb
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6f5f157da15cb53da41d6735524ed502cd35156
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-an-aggregation"></a><span data-ttu-id="fd38d-102">如何修改彙總</span><span class="sxs-lookup"><span data-stu-id="fd38d-102">How to Modify an Aggregation</span></span>
<span data-ttu-id="fd38d-103">請依照在 Excel 中使用樞紐分析表的相同方式使用 Office Web Components 中的樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="fd38d-103">You use PivotTable reports in Office Web Components the same way you use PivotTable reports in Excel.</span></span> <span data-ttu-id="fd38d-104">您可以新增和移除列、欄以及篩選，以便在能夠建立警示的彙總資料上產生檢視。</span><span class="sxs-lookup"><span data-stu-id="fd38d-104">You can add and remove rows, columns, and filters to generate views of the aggregated data on which you can create alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fd38d-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fd38d-105">Prerequisites</span></span>  
 <span data-ttu-id="fd38d-106">若要執行這個程序，您必須具備含有彙總的部署檢視。</span><span class="sxs-lookup"><span data-stu-id="fd38d-106">To perform this procedure, you must have a deployed view that contains an aggregation.</span></span>  
  
### <a name="to-modify-an-aggregation"></a><span data-ttu-id="fd38d-107">修改彙總</span><span class="sxs-lookup"><span data-stu-id="fd38d-107">To modify an aggregation</span></span>  
  
1.  <span data-ttu-id="fd38d-108">在**彙總** 頁面上，從**樞紐分析表欄位清單**視窗中，拖曳欄位與您想要顯示於資料列並將它們放置到方格中，以新增列欄位左側資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="fd38d-108">On the **Aggregations** page, from the **PivotTable Field List** window, drag the fields with data that you want to display in rows and drop them onto the left column of the grid to add row fields.</span></span> <span data-ttu-id="fd38d-109">如果您沒有看到欄位清單，請在樞紐分析表拖放區的大綱內按一下，並確定出現 [顯示欄位清單]。</span><span class="sxs-lookup"><span data-stu-id="fd38d-109">If you don't see the field list, click within the outlines of the PivotTable drop areas, and make sure Show Field List appears.</span></span> <span data-ttu-id="fd38d-110">若要查看具有層級之欄位中可用的詳細資訊層級，請按一下適當欄位旁邊的加號 (+)。</span><span class="sxs-lookup"><span data-stu-id="fd38d-110">To see what levels of detail are available in fields that have levels, click the plus sign (+) next to the appropriate field.</span></span>  
  
2.  <span data-ttu-id="fd38d-111">將您想要顯示標示為拖放區的資料行之間的資料欄位拖曳**資料行欄位放置到此處**。</span><span class="sxs-lookup"><span data-stu-id="fd38d-111">Drag fields with data that you want to display across columns to the drop area labeled **Drop Column Fields Here**.</span></span> <span data-ttu-id="fd38d-112">只有指定為計數或進度欄位的欄位才可以拖曳到這個區域。</span><span class="sxs-lookup"><span data-stu-id="fd38d-112">Only fields that are designated as counts or progress fields can be dragged to this area.</span></span>  
  
3.  <span data-ttu-id="fd38d-113">如果您加入多個資料欄位，將這些欄位，您想要的順序排列： 以滑鼠右鍵按一下資料欄位，指向**順序**捷徑功能表上，使用上的命令和**順序**功能表移動欄位。</span><span class="sxs-lookup"><span data-stu-id="fd38d-113">If you add more than one data field, arrange these fields in the order you want: right-click a data field, point to **Order** on the shortcut menu, and use the commands on the **Order** menu to move the field.</span></span>  
  
4.  <span data-ttu-id="fd38d-114">若要重新排列欄位，請將欄位從一個區域拖曳到另一個區域。</span><span class="sxs-lookup"><span data-stu-id="fd38d-114">To rearrange fields, drag them from one area to another.</span></span> <span data-ttu-id="fd38d-115">若要移除欄位，請將欄位拖曳出樞紐分析表並移至巡覽框架。</span><span class="sxs-lookup"><span data-stu-id="fd38d-115">To remove a field, drag it out of the PivotTable report onto the navigation frame.</span></span>  
  
5.  <span data-ttu-id="fd38d-116">在樞紐分析表的總計欄中，使用滑鼠右鍵按一下含有您想要設定警示之總計的儲存格。</span><span class="sxs-lookup"><span data-stu-id="fd38d-116">From the totals column in the PivotTable report, right-click the cell containing the total on which you are going to set an alert.</span></span> <span data-ttu-id="fd38d-117">選取**建立警示**以開啟 [警示管理] 頁面。</span><span class="sxs-lookup"><span data-stu-id="fd38d-117">Select **Create Alert** to open the Alert Management page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd38d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd38d-118">See Also</span></span>  
 <span data-ttu-id="fd38d-119">[BAM 入口網站上的彙總頁面](../core/aggregations-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="fd38d-119">[Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="fd38d-120">如何設定警示</span><span class="sxs-lookup"><span data-stu-id="fd38d-120">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)