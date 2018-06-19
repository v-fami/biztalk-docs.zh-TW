---
title: 查詢執行個體資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, instance data
- queries [BAM], instance data
ms.assetid: ae4a8854-d5c2-4b36-a0ef-3f74e138306e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43310756cf12c0c2a48eb6716221afc5395ecb0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971828"
---
# <a name="querying-instance-data"></a>查詢執行個體資料
透過 BAM 主要匯入資料庫中動態建立的 SQL 檢視，可以查詢有關個別活動執行個體的資料。  
  
 這個檢視的名稱為  
  
 **bam_\<**  *ViewName*  **\>_\<**  *ActivityName* **\>檢視 （_v)**  
  
 位置  
  
 **\<***ViewName*  **\>** 是 BAM 定義 XML 中 View 項目的 Name 屬性相同相關 Microsoft Excel 精靈中輸入的檢視名稱。  
  
 **\<***ActivityName*  **\>** 是 BAM 定義 XML 中 Activity 項目的 Name 屬性相同 Excel 精靈中輸入的活動名稱。  
  
 在查詢執行個體資料時，請特別注意下列條件：  
  
-   如果您透過 DirectEventStream 將活動資料傳送至 BAM，執行個體資料便不會延遲，這表示只要呼叫應用程式中的交易一經過認可，執行個體資料就會立即顯示出來。  
  
-   如果透過 BufferedEventStream 將活動資料傳送至 BAM，將會根據 BAM 事件匯流排服務的負載，以及裝載 BAM 主要匯入資料庫的 SQL Server，在幾秒鐘後顯示查詢的執行個體資料。  
  
-   此檢視背後的資料表實際結構更為複雜，這都是為了確保目前或最近活動的資料可供查詢使用，至於已經完成且使用中查詢也不再需要的活動資料，就會封存起來或清除，而不需要讓系統離線。 如需詳細資訊，請參閱[活動資料儲存區](../core/activity-data-storage.md)。  
  
## <a name="see-also"></a>請參閱  
 [活動資料儲存區](../core/activity-data-storage.md)   
 [查詢 BAM 資料](../core/querying-bam-data.md)