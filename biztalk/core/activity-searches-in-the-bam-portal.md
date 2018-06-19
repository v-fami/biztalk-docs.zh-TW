---
title: BAM 入口網站中的活動搜尋 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], searching
- queries [BAM], field descriptions
- Query Builder [BAM portal], creating queries
- queries [BAM], activity searches
- Query Builder [BAM portal], about Query Builder
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal]
- Query Builder [BAM portal], field descriptions
- BAM portal, Query Builder
- BAM portal, activity searches
ms.assetid: 60ab8deb-ebe2-4959-97fd-261ff64d500c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723848f61294cc710bd2292758383cf674093265
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966596"
---
# <a name="activity-searches-in-the-bam-portal"></a>BAM 入口網站中的活動搜尋
活動搜尋可讓您對 BAM 資料執行搜尋，根據 BAM 檢視中的追蹤值和項目尋找符合您指定之準則的活動，並顯示這些活動讓您進行編輯或根據這些活動建立警示。  
  
## <a name="parts-of-the-query-builder"></a>查詢建立器的組成部分  
 您可以選取商務資料項目，針對這些項目建立布林值比較來擷取所需的資料，以建置活動搜尋的查詢。 您選取從 BAM 檢視，啟動**我的檢視**入口網站的框架。 從選取的檢視中，您可以選取要建置查詢的活動。  
  
 ![](../core/media/bamportalviewschooser.gif "BAMPortalViewsChooser")  
  
 選取活動之後，入口網站的內容框架就會顯示 [查詢建立器]、[欄位選擇器] 和 [結果] 方塊。 您可以開啟現有的查詢或建置新的查詢。  
  
 ![](../core/media/activitysearchquerybuilder.gif "ActivitySearchQueryBuilder")  
  
 若要建立新的查詢，您所選取的商務資料的項目從開始**商務資料**下拉式清單。  
  
 ![](../core/media/activitysearchquerybuilderbusinessdatadropdown.gif "ActivitySearchQueryBuilderBusinessDataDropdown")  
  
 接著，您可以在 [運算子] 下拉式清單中選取比較運算子。 比較運算子可讓您精簡查詢的結果。  
  
 ![](../core/media/activitysearchcomparisonoperatordropdown.gif "ActivitySearchComparisonOperatorDropDown")  
  
 [值] 下拉式清單會根據商務資料項目所代表的資料類型顯示其內容。 使用者介面 (UI) 會隨著允取資料的類型變更而變更。  
  
 您可以加入與查詢子句，或 OR 運算子，以形成更複雜的查詢，方法是按一下**新增** 按鈕。  
  
 ![](../core/media/activitysearchjoiningclauses.gif "ActivitySearchJoiningClauses")  
  
> [!NOTE]
>  您無法群組子句。 查詢是由以 AND/OR 運算子加入的個別子句所組成的簡單字串。  
  
 下表說明日期和時間欄位。  
  
|運算子|Description|  
|--------------|-----------------|  
|**在**|指定完全相符的項目。 相當於布林值的等於 (=) 運算。 **注意：** 如果您選取**在**運算子，然後在入口網站會使用午夜做為預設值沒有時間部分指定日期。 如果這不是您的目的，使用**當時或之前**或**在或之後**運算子取得所需的結果。|  
|**在或之前**|指定只有在指定日期當天或之前的交易才符合。 相當於布林值的小於或等於 (≤ 運算。|  
|**在或之後**|指定只有在指定日期當天或之後的交易才符合。 相當於布林值的大於或等於 (≥ 運算。|  
|**之前**|指定只有在指定日期之前的交易才符合。 相當於布林值的小於 (<) 運算。|  
|**After**|指定只有在指定日期之後的交易才符合。 相當於布林值的大於 (>) 運算。|  
|**在過去**|指定只有在先前指定時間週期發生的交易才符合。 時間週期可以秒、分、小時或天為單位指定。|  
|**最後一個之前**|指定只有在指定時間週期之前發生的交易才符合。 時間週期可以秒、分、小時或天為單位指定。|  
|**是空的**|指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。|  
|**不是空的**|指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。|  
  
 下表說明數字欄位和持續時間欄位。 數字欄位包含如量或貨幣數的資料。 持續時間欄位指定時間週期。  
  
|運算子|Description|  
|--------------|-----------------|  
|**等於**|指定完全相符的項目。 相當於布林值的等於 (=) 運算。|  
|**大於**|指定完全相符的項目。 相當於布林值的大於 (>) 運算。|  
|**大於或等於**|指定完全相符的項目。 相當於布林值的大於或等於 (≥ 運算。|  
|**小於**|指定完全相符的項目。 相當於布林值的小於 (<) 運算。|  
|**小於或等於**|指定完全相符的項目。 相當於布林值的小於或等於 (≤ 運算。|  
|**不等於**|指定完全相符的項目。 相當於布林值的不等於 (≠) 運算。|  
|**是空的**|指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。|  
|**不是空的**|指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。|  
  
 下表說明文字欄位。  
  
|運算子|Description|  
|--------------|-----------------|  
|**完全**|指定完全相符的項目。 相當於布林值的等於 (=) 運算。|  
|**包含**|指定商務資料項目中的文字包含指定的值。 這可讓您在資料上執行部分相符。|  
|**不包含**|指定商務資料項目中的文字不包含指定的值。|  
|**是空的**|指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。|  
|**不是空的**|指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何在活動搜尋中建立查詢](../core/how-to-create-a-query-in-activity-search.md)  
  
-   [如何設定警示](../core/how-to-set-an-alert.md)  
  
-   [如何檢視活動搜尋的結果](../core/how-to-view-the-results-of-an-activity-search.md)  
  
## <a name="see-also"></a>請參閱  
 [BAM 入口網站](../core/bam-portal.md)