---
title: 查詢活動關係 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, activity relationships
- queries [BAM], relationships
ms.assetid: e3d42b7c-cc11-4707-9095-cfc518902b26
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cec34263598f50c9852ffe3f3a7d749914c977
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984015"
---
# <a name="querying-activity-relationships"></a>查詢活動關係
活動關係資訊可以在為每個活動動態建立的 SQL 檢視中取得。 這個檢視的名稱為  
  
 **bam_\<**  *活動*  **\>_AllRelationships**  
  
 何處\<*活動*\>是 BAM 定義 XML 中 Activity 項目的 Name 屬性與輸入使用適用於 Excel 的 BAM 增益集的 Activity 名稱相同。  
  
 關係事件會發生在特定活動的環境中。 比方說，如果採購單和出貨之間的關係發生 Purchase Order 活動的內容中，關聯性記錄將會出現在**bam_PurchaseOrder_AllRelationships**，但無法顯示於**bam_Shipment_AllRelationships**。 如需詳細資訊，請參閱 <<c0> [ 活動關係](../core/activity-relationships.md)。  
  
 若要尋找所有要購買的相關的活動可讓您排序您要查詢這兩個檢視**bam_PurchaseOrder_AllRelationships**以及 所有檢視**bam_\<**<em>OtherActivity</em>  **\>_AllRelationships**，其中\< *OtherActivity* \>是相同的 BAM 檢視中的活動。  
  
 關係記錄屬於活動執行個體，以及它們保留的執行個體資料的同步處理中所述[活動資料儲存區](../core/activity-data-storage.md)。  
  
## <a name="see-also"></a>另請參閱  
 [查詢 BAM 資料](../core/querying-bam-data.md)