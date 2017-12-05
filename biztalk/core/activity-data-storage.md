---
title: "活動資料儲存區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- databases [BAM], performance
- activities [BAM], peformance
- databases [BAM], partitioning
- BAM, performance
ms.assetid: 1f736599-3d16-496e-a459-8b0507d57fcb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0139e76512eb9ca60089cb3c5f1e71b4f5524690
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="activity-data-storage"></a>活動資料儲存區
本主題說明活動資料儲存區、活動資料表隨時間成長所造成的效能問題，以及 BAM 如何將進行中與已完成的活動存放在不同的資料表以解決這些效能問題。 本主題也將說明用於查詢資料的線上視窗，及如何在 BAM 中使用分割以獲得更高的效能。  
  
 活動資料儲存區的基本構想是將每一種活動類型存放在不同的資料表，當中每一筆記錄均代表不同的活動執行個體 (例如，進行中或已完成)。  
  
 此處以「採購單」活動為例，其資料表看起來如下所示：  
  
|採購單編號|接單時間|City|Quantity|交貨時間|送達時間|  
|----------|--------------|----------|--------------|--------------|------------------|  
|123|8:00 am|Seattle|150|上午 8:24|12:45pm|  
|124|8:30 am|Seattle|234|8:45 am|下午 1:20|  
|125|8:35 am|Redmond|87|上午 9:05|2:30 pm|  
|126|8:45 am|Seattle|450|上午 9:20|3:10 pm|  
|127|8:55am|Redmond|200|上午 9:30|\<NULL\>|  
|128|上午 8:57|Seattle|340|上午 9:20|3:05 pm|  
|129|上午 9:12|Seattle|120|上午 9:45|\<NULL\>|  
|130|上午 9:30|Redmond|25|10:15 am|\<NULL\>|  
|131|9:45|Seattle|250|10:35 am|\<NULL\>|  
|132|10:00 am|Redmond|100|\<NULL\>|\<NULL\>|  
|133|10:15 am|Seattle|230|\<NULL\>|\<NULL\>|  
|134|10:25 am|Redmond|45|\<NULL\>|\<NULL\>|  
  
 當 BAM 收到新的採購單時，便會在此資料表中插入新的一列，並將某幾欄設定為非空值 (「接單時間」、「縣/市」、「數量」等等)。 稍後一旦核准該筆採購單並已交貨，BAM 則將「交貨時間」設定為非空值。 最後，如果收到貨品且確認無誤，BAM 會將「送達時間」設定為非空值。  
  
 這種過度簡化的實作，其效能將隨著時間而迅速降低。 起初，效能受限於 SQL 伺服器所能執行的交易數目 (基本上受限於 CPU 處理能力)，但經過一段時間後，效能將會大幅降低。 同時，磁碟 IO 的平均佇列長度也會增加以致超出可接受的上限：  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig4.gif "ebiz_prog_bam_data_maint_fig4")  
BAM 寫入效能與磁碟佇列長度的比較  
  
 之所以發生這種情形，是因為資料表的大小會隨著商務程序所完成的執行個體而成長。 例如在初次執行時，預存程序的 UPDATE 陳述式會在叢集索引上搜尋採購單編號，並讀取記憶體中的某些分頁。 由於採購單程序的執行個體是各自獨立的 (花費的時間長短不一)，下一次呼叫預存程序可能是要處理其他某些採購單執行個體，因而需要讀取記憶體中其他的資料分頁。 只要採購單記錄的總數不多，SQL Server 就會將所有的資料分頁快取在記憶體中。 當記錄總數增長到一定的大小之後，快取記憶體觸及率便會降低，而每個作業便都必須讀取實體磁碟。 顯然地，這種情況下根本無法對資料表執行查詢活動。  
  
## <a name="bam-tables"></a>BAM 資料表  
 為了避免此問題，BAM 使用兩個不同的資料表，其中一個用以儲存仍在進行中的活動，另一個則是儲存已完成的活動，如下圖所示：  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig5.gif "ebiz_prog_bam_data_maint_fig5")  
BAM 資料表  
  
 上圖的構想是，將更新作業保留在相對較小的資料表內執行，而另一個大小會增長的資料表則是以累加方式存取 (僅執行 INSERT)。 在此範例中，只有在當下仍在處理中的訂單會放置在作用資料表，而所有已送達的訂單都將存入已完成的資料表。  
  
 由於觸發程序之故，這種雙重資料表結構起初會比 INSERT/UPDATE 集中在單一資料表更慢，但長期而言仍能維持穩定的寫入效能。  
  
## <a name="online-window-for-activity-data"></a>活動資料的線上視窗  
 活動儲存區主要是處理目前活動或最近完成活動的查詢作業。 BAM 會封存然後清理 BAM 主要匯入資料庫中極舊的已完成活動。 因此，活動資料就能通過 BAM 以供可設定的線上視窗進行查詢。  
  
## <a name="bam-partitioning"></a>BAM 分割  
 為求更高的效能並避免停機，活動儲存區會使用以活動完成的時間戳記為基礎的分割。 BAM 的做法是定期將已完成的資料表，與另一個格式完全相同的空資料表交換。 一旦 BAM 執行此動作，後續完成的活動就會存放在新資料表，而 BAM 也會保留舊資料表僅供查詢，如下圖所示：  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig8.gif "ebiz_prog_bam_data_maint_fig8")  
BAM 分割交換  
  
 任何分割只要完全移出線上視窗，BAM 便會予以封存然後卸除。 為了不讓使用者覺得這種做法太複雜，BAM 也維持以下型式的分割檢視：  
  
```  
SELECT * FROM Active   
UNION ALL   
SELECT * FROM Completed   
UNION ALL  
  
```  
  
 每當 BAM 建立或卸除分割，就會自動重新建立此檢視。  
  
 請注意下列有關 BAM 分割的資訊：  
  
-   資料分割檢視的名稱是**bam_\<ActivityName\>_AllInstances**。 此檢視並非用於直接查詢，但疑難排解 BAM 檢測時可能很有用。 您應該透過在此檢視上方所建立的每個商務使用者類別，以其特定的檢視查詢資料。 如需詳細資訊，請參閱[查詢執行個體資料](../core/querying-instance-data.md)。  
  
-   您所修改的值設定線上視窗**OnlineWindowTimeUnit**和**Onlinewindowtimeunit**表格中目前的活動記錄中**bam_Metadata_Activities**主要匯入資料庫中。  
  
-   DTS 封裝， **BAM_DM_\<ActivityName\>**、 執行資料分割和封存/清理。 每次執行此封裝時，都會截斷另一分割並封存/卸除所有已移出線上視窗的分割。  
  
-   若您並未設定封存資料庫，BAM 將卸除舊活動而不進行封存。  
  
## <a name="see-also"></a>請參閱  
 [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)