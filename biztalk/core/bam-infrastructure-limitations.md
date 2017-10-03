---
title: "BAM 基礎結構限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, limitations
- infrastructure, BAM
- BAM, objects
- BAM, infrastructure
- BAM, naming conventions
ms.assetid: e33d2f6c-8d26-4a76-810e-85d810cfdbee
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfb8751e42918a64f13d35685d7d73b4f2406ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-infrastructure-limitations"></a>BAM 基礎結構限制
此版本的 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 有下列 BAM 基礎結構設計限制：  
  
-   即時彙總 (RTA) 不支援 MIN 或 MAX 函式。  
  
-   在一個 RTA 檢視中，您無法經由一個以上的資料維度參考單一層級的別名。  
  
-   標準 Cube 和 RTA 都不支援不同計數量值。 BAM 管理公用程式會為標準 Cube 和 RTA 建立預設計數量值。 預設計數是事實的總計數 (也稱為「活動執行個體」)，而非不同計數。  
  
-   請勿定義多個使用相同 BAM 活動的 RTA。 若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。  
  
## <a name="bam-maximum-number-of-objects"></a>物件的 BAM 數目上限  
 下表列出 BAM 基礎結構中的物件數目上限。  
  
|物件|實作限制|Reason|  
|------------|--------------------------|------------|  
|活動中的檢查點|1,000|SQL Server 支援 1,024 預存程序引數和 BizTalk Server 會使用三個系統程序。|  
|活動中的索引|245|SQL Server 支援每個資料表可以有 245 個非叢集索引。 BizTalk Server 一律會在 ActivityID 上建立索引。|  
|DataLength|4,000 個 Unicode 字元|使用 NVARCHAR 類型的 SQL 變數。|  
|ActivityRef|128|您可以聯結「主要匯入」資料庫和「關係」資料表 (每個活動有兩個) 以取得檢視。 SQL Server 支援 SELECT 陳述式中可以有 256 個資料表。|  
|檢視中的資料行<br /><br /> (別名、持續時間加上維度層級)|150|SQL Server 限制「臨時資料表」上只能有 1,024 個資料行，並且其中 BAM 會保留 24 個做為系統資料行。|  
|OLAP Cube 中的維度|128|OLAP 限制-每個 cube 有 128 個維度|  
|OLAP 中的量值|1,024|OLAP 限制 - 每個 Cube 有 1,024 個量值， 一定會建立的 Count 量值。|  
|在 OLAP 維度層級|64|OLAP 額外限制每個 Cube 只能有 256 個層級。|  
|RTA 檢視中的維度層級|14 個維度層級|BAM 會在所有維度層級上建立索引，可以建立最多 16 個資料行的 SQL Server 索引，並且 BAM 會保留兩個資料行做為系統資料行。|  
|量值、 隱藏的量值 （預設計數，AVG 的隱藏 SUM 量值） 和 RTA 檢視中的維度層級|1,024|SQL 資料表/檢視中最多有 1,024 個資料行。|  
|ActivityViews|63|當您設定警示時，您受限於下 63 ActivityViews [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]。|  
  
## <a name="bam-object-names"></a>BAM 物件名稱  
 下表列出 BAM 定義結構描述和 Microsoft Excel 試算表中的物件名稱限制。  
  
|物件名稱|XSD 限制|Excel 限制|  
|------------------|--------------------|----------------------|  
|檢查點名稱|50 個字元|50 個字元|  
|索引名稱|100 個字元|100 個字元|  
|持續時間名稱|100 個字元|100 個字元|  
|別名名稱|50 個字元|50 個字元|  
|活動名稱|48 個字元|20 個字元|  
|檢視表名稱|18 個字元|18 個字元|  
|ActivityView 名稱|52 字元 (名稱是由前置詞 "View" 加上 48 個字元檢視名稱而組成)。|N/A (衍生自活動名稱)|  
|Cube 名稱|20 個字元|N/A (衍生自檢視名稱)|  
|RealTimeAggregation 名稱|48 個字元|N/A (衍生自 Cube 名稱)|  
|維度名稱|20 個字元|20 個字元|  
|層級名稱|20 個字元|20 個字元|  
|量值名稱|20 個字元|20 個字元|  
|警示名稱|128 個字元|不適用|  
|警示訊息|1024 個字元|不適用|  
|事件規則名稱|255 個字元|不適用|  
|事件提供者名稱|255 個字元|不適用|  
  
## <a name="see-also"></a>另請參閱  
 [BAM 組態結構描述](../core/bam-configuration-schema.md)   
 [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)