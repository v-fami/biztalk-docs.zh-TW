---
title: "查詢即時彙總資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], real-time data
- BAM, real-time data
ms.assetid: f60a34a1-ac64-47c7-8f83-1bc301170590
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b71c3adbcbe5aaaea4d9fa4bf25b2aa4191c580
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="querying-real-time-aggregated-data"></a>查詢即時彙總資料
透過 BAM 主要匯入資料庫中動態建立的 SQL 檢視，可以查詢即時彙總 (RTA) 資料。  
  
 這個檢視的名稱為  
  
 **bam_\<**  *ViewName*  **\>_\<**  *RTAName*  **\>_RTAView**  
  
 位置  
  
 **\<***ViewName*  **\>** 是 BAM 定義 XML 中 View 項目的 Name 屬性相同相關 Microsoft Excel 精靈中輸入的檢視名稱。  
  
 **\<***RTAName*  **\>**  BAM 產生的唯一 BAM 定義 XML 中 RealTimeAggregation 項目的 Name 屬性根據檢視名稱。  
  
 在查詢即時彙總資料時，請特別注意下列條件：  
  
-   即時彙總必須設定成在指定的時間內 (預設值是一天) 保留彙總，並且彙總絕不能變得太大。 OLAP Cube 中應該可以取得較舊的彙總。  
  
-   針對 RTA 的任何查詢必須包含會在 RTA 資料的線上視窗內的時間維度上篩選。 這是必要的，因為 BAM 會根據 BAM 資料上的時間戳記執行 RTA 資料維護，並經過最佳化以便將資料放置在區塊中。 因此，如果您只傳送 Transact-SQL 命令 "`select *`"，將無法預期結果。  
  
-   如果透過 DirectEventStream 將活動資料傳送至 BAM，即時彙總資料便沒有延遲，也就是說，當呼叫應用程式中的交易認可時，資料就會立即出現。  
  
-   如果透過 BufferedEventStream 將活動資料傳送至 BAM，將會根據 BAM 事件匯流排服務的負載，以及裝載 BAM 主要匯入資料庫的 SQL Server，在幾秒鐘後顯示查詢的 RTA 資料。  
  
-   BAM 會將它使用觸發程序維護與活動資料儲存記錄中變更或插入作業同步的資料表，當做即時彙總的基礎。 如需詳細資訊，請參閱[活動資料儲存區](../core/activity-data-storage.md)。 因此，即時彙總可能對效能有顯著的影響。 如需詳細資訊，請參閱[即時彙總](../core/real-time-aggregations.md)。  
  
## <a name="see-also"></a>請參閱  
 [查詢排程彙總資料](../core/querying-scheduled-aggregated-data.md)   
 [查詢 BAM 資料](../core/querying-bam-data.md)