---
title: 即時彙總 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- aggregations [BAM], real-time data
ms.assetid: 0ef44641-e067-4108-b318-f4373ca8fa8f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1bc335c1c53fe106c460b7dcb5a27b803db97b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269078"
---
# <a name="real-time-aggregations"></a>即時彙總
在某些情況下，多維度彙總的特定配量有時間緊迫性，因此必須可即時取得。 例如，您的業務是銷售容易腐壞的產品，所以希望即時取得各個出貨階段的產品數量彙總。 同時，您也有其他想要看到的彙總，如典型客戶的年齡彙總，但是這只有在月底進行商業智慧分析時才需要。  
  
 BAM 實作即時彙總 (RTA)，這是由活動儲存區資料表的觸發程序所維護的資料表。 就上述商務處理採購單 (PO) 的情況而言，RTA 檢視將如下圖的範例所示。  
  
 ![](../core/media/bam-realtime-aggregations.gif "bam_realtime_aggregations")  
BAM 即時彙總  
  
 在此圖中，如果收到 Redmond $100 的新 PO，BAM 將帳目加入對應的資料列中的資料格 {redmond，InProcess} 上執行的作業，例如`Count=Count+1`和`Amount=Amount+$100`。  
  
 更新版本中，如果相同訂單出貨，BAM 從 {Redmond，InProcess} 的資料列移除其帳目，然後將它加入 {Redmond，Shipped} 資料列。  
  
 BAM 會在 RTA 中保存指定線上視窗的資料，然後予以刪除。 您可以藉由變更對應的資料列的資料表設定線上視窗**bam_Metadata_RealTimeAggregations**。  
  
 下列陳述式也適用於即時彙總：  
  
-   即時彙總會大幅影響 BAM 可以在其中寫入資料的速度。 因此，您應該只將彙總結構中最重要的配量定義成 RTA。  
  
-   即時彙總的維度層級的限制為 14。 例如，如果您建立資料維度位置的狀態和縣 （市），這也算是兩個層級 （State 和 City）。 進度維度的層級數目是樹狀結構的深度，而時間維度則是所有的子單位計數。 例如，時間維度 「 年、 月、 日、 小時 」 算成四個層級。  
  
-   BAM 不支援的型別即時彙總**Min**和**Max**。 BAM 支援的彙總是**計數**，**總和**，和**平均**。  
  
-   您必須一律為 RTA 建立時間維度並始終應用在所有的資料配量，因為 RTA 中的資料過時根據伺服器的時間戳記，而非特定的商務里程碑。  
  
-   請勿定義多個使用相同 BAM 活動的 RTA。 若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。  
  
 即時彙總會大幅影響 BAM 可以在其中寫入資料的速度。 因此，您應該只將彙總結構中最重要的配量定義成 RTA。  
  
 即時彙總的維度層級的限制為 14。 例如，如果您建立資料維度位置的狀態和縣 （市），這也算是兩個層級 （State 和 City）。 進度維度的層級數目是樹狀結構的深度，而時間維度則是所有的子單位計數。 例如，時間維度 「 年、 月、 日、 小時 」 算成四個層級。  
  
 BAM 不支援的型別即時彙總**Min**和**Max**。 BAM 支援的彙總是**計數**，**總和**，和**平均**。  
  
 請勿定義多個使用相同 BAM 活動的 RTA。 若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是彙總？](../core/what-is-an-aggregation.md)