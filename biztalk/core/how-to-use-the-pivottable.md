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
# <a name="how-to-use-the-pivottable"></a>如何使用樞紐分析表
在定義包含維度和量值的 BAM 檢視之後，您必須更新一或多個與該檢視關聯的樞紐分析表。  
  
 Excel 中的樞紐分析表是可供您用來輕鬆組合及比較大量資料的互動式表格。 您可以旋轉資料列與資料行中的值來查看所顯示資料的不同摘要。 您也可以使用樞紐分析表來執行資料的計算，如彙總計數或平均。  
  
 若要在建立樞紐分析表之後加以使用，請依照下列程序中的步驟執行。 如需有關使用樞紐分析表的詳細資訊，請參閱 Microsoft Excel 文件。  
  
> [!NOTE]
>  建立即時彙總樞紐分析表時，此表格最多可以包含 14 個維度層級。  
  
> [!IMPORTANT]
>  如果在 Excel 工作表中定義了多個樞紐分析表，且活動傳回大型的資料集，則產生的表格可能會增大而彼此重疊。 在此案例中，當您在重新整理資料時，會收到「樞紐分析表不能重疊在另一個樞紐分析表之上」的訊息。 您可以在樞紐分析表之間新增資料行或資料列，讓表格增大而不彼此重疊，藉此修正這項錯誤。  
  
### <a name="to-use-the-pivottable"></a>使用樞紐分析表  
  
1.  建立要搭配樞紐分析表使用的 BAM 檢視。 如需有關建立 BAM 檢視的詳細資訊，請參閱[定義商務活動檢視](../core/defining-a-bam-view.md)  
  
2.  使用**樞紐分析表欄位清單**，拖放一個或多個可用維度放到樞紐分析表範本的資料行和資料列區域。  
  
3.  使用**樞紐分析表欄位清單**，拖放一個或多個可用的量值放到資料的項目區域的樞紐分析表範本。  
  
     更新樞紐分析表時，您將會發現其中已填入範例資料。 這樣可以協助您判斷如何設定樞紐分析表。  
  
4.  使用**樞紐分析表**關聯圖表與樞紐分析表 工具列。  
  
5.  儲存 Excel 活頁簿。