---
title: "查詢排程彙總資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, scheduled data
- queries [BAM], scheduled data
ms.assetid: fb785ec0-7862-4d83-bb6f-0ebd69a28ce6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1aed1d63b1ebd1e54fd229236a94f3ac9a5f6837
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="querying-scheduled-aggregated-data"></a>查詢排程的彙總資料
透過 BAM 分析資料庫中動態建立的 OLAP Cube 可以查詢排程的彙總資料。  
  
 這個 Cube 的名稱與 BAM 定義 XML 中 View 項目的 Name 屬性相同 (與 Excel 精靈中輸入的檢視名稱相同)。 當您執行 Data Transformation Services (DTS) 封裝 BAM_AN_< BAM 重新整理此 cube\<*ViewName*\>，其中\< *ViewName* \>為檢視的名稱，描述您在 Excel 精靈中使用。  
  
 在查詢排程的彙總資料時，請特別注意下列條件：  
  
-   這是虛擬 Cube，其中包含在 DTS 封裝開始執行的確切時間擷取到的商務快照。 它同時包含完成的活動以及仍在進行中的活動的彙總。 您可以使用進度維度篩選彙總或將彙總分組。  
  
-   如果您不感興趣目前的活動 （例如，如果它們的完成速度非常快），您就可以查詢對應的真實 cube \< *ViewName*\>#Completed。  
  
-   如果您也有即時彙總，請排程 DTS 封裝，讓重新整理 Cube 的頻率，比為即時彙總設定的線上視窗更頻繁。 否則，將會出現一個時間窗口，而您在此時間窗口內沒有任何彙總。  
  
## <a name="see-also"></a>請參閱  
 [查詢 BAM 資料](../core/querying-bam-data.md)