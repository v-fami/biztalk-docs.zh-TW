---
title: BAM 入口網站中的彙總 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM portal, pivot tables
- BAM, data analysis
- pivot tables [BAM portal]
- BAM portal, charts
- data, analysis [BAM]
- data, OLAP cubes
- aggregations [BAM], BAM portal
- charts, BAM portal
- BAM portal, aggregations
ms.assetid: 1c689563-714b-4573-9c18-a5b0efe97fb8
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43ef0adfacea0a29ea47584ed545884ffb8fa8bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230542"
---
# <a name="aggregations-in-the-bam-portal"></a>BAM 入口網站中的彙總
彙總是預先計算好的資料表格，您可以搭配 OLAP Cube 進行分析處理。 彙總有助於提升多維度資料庫的查詢效率。 當您使用 Excel 的 BAM 增益集建立和部署觀察模型 (商務資料的高階定義) 時，便會建立彙總以利迅速評估與關鍵效能指標 (KPI) 相關的資料集合。  
  
## <a name="types-of-aggregations"></a>彙總類型  
 彙總有兩種類型：排程或即時。 排程彙總是 OLAP Cube，代表您所指定時間上的商務資料快照集。 即時彙總能依據指定的觸發點提供商務資料檢視，讓 BAM 系統得以在達到 KPI 時立即透過警示通知您。  
  
## <a name="pivottable-view"></a>樞紐分析表檢視  
 [樞紐分析表檢視] 區域顯示使用 Excel 的 BAM 增益集所設計的樞紐分析表。 「Office Web 元件」可讓您操控樞紐分析表，以最符合個人需求的方式顯示資料檢視。  
  
> [!NOTE]
>  當您檢視樞紐分析表時，如果活動中的里程碑已達到，但進度維度中並未使用這些里程碑，即時彙總 (RTA) 和預先計算彙總 (OLAP 實作) 的某幾列可能都會包含空值資料。 若在進度維度的內容中使用時間維度並將其錨定至特定里程碑，例如「已通知」而非「已接收」，則某幾列也可能會包含空值資料。 在此情況下會接收活動執行個體並觸發已接收里程碑，但因活動尚未觸發通知里程碑，以致時間維度列顯示零值。  若要避免這種情形，請將時間維度向上連結至已接收里程碑。  
  
 ![](../core/media/aggregationpivottabletotal.gif "AggregationPivotTableTotal")  
  
 在 BAM 入口網站中使用 Office Web Components 修改樞紐分析表時，請記住下列重點：  
  
-   Excel 中的樞紐分析表包含 [頁面] 欄位，您可以在此放置時間配量維度。 BAM 入口網站所使用的 Office Web Components 則沒有 [頁面] 欄位。 如果 Excel 樞紐分析表對於任一維度都使用了 [頁面] 欄位，則 BAM 入口網站中的樞紐分析表便不會顯示該欄位的資料。  
  
-   Office Web Components 會將資料顯示在 BAM 入口網站的內容框架中。 由於此框架有空間限制，從欄位清單將維度新增至欄區域可能導致樞紐分析表所顯示的維度名稱部分或全部超出檢視畫面。  
  
 樞紐分析表的詳細資訊，請參閱 < 樞紐分析表詞彙釋疑 」，網址[http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416)。  
  
## <a name="chart-view"></a>圖表檢視  
 [圖表檢視] 區域以圖形方式顯示彙總。 Office Web Components 可讓您透過圖表檢視操控彙總的詳細資料，以便視需要調整報告的資料。 從 [圖表欄位] 清單拖放資料項目來調整彙總時，彙總的樞紐分析表會自動更新以反映您的變更。 您可以鑽研樞紐分析表，進而在新的彙總檢視中建立警示。  
  
 ![](../core/media/aggregationchartview.gif "AggregationChartView")  
  
## <a name="more"></a>其他  
  
-   [如何設定警示](../core/how-to-set-an-alert.md)  
  
-   [如何檢視活動搜尋的結果](../core/how-to-view-the-results-of-an-activity-search.md)  
  
-   [如何修改彙總](../core/how-to-modify-an-aggregation.md)  
  
## <a name="see-also"></a>另請參閱  
 [什麼是彙總？](../core/what-is-an-aggregation.md)