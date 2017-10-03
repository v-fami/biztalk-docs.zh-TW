---
title: "查詢活動關係 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, activity relationships
- queries [BAM], relationships
ms.assetid: e3d42b7c-cc11-4707-9095-cfc518902b26
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11570bbf42001ac11b5be61ff7b76d06f3df0889
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="querying-activity-relationships"></a>查詢活動關係
活動關係資訊可以在為每個活動動態建立的 SQL 檢視中取得。 這個檢視的名稱為  
  
 **bam_\<**  *活動* **> _AllRelationships**  
  
 其中\<*活動*> 是 BAM 定義 XML 中 Activity 項目的 Name 屬性適用於 Excel 的 BAM 增益集使用輸入的活動名稱相同。  
  
 關係事件會發生在特定活動的環境中。 例如，如果採購單和出貨之間的關係發生 Purchase Order 活動的內容中，關聯性記錄會顯示在**bam_PurchaseOrder_AllRelationships**，但無法在**bam_Shipment_AllRelationships**。 如需詳細資訊，請參閱[活動關係](../core/activity-relationships.md)。  
  
 若要尋找所有要購買的相關的活動順序必須查詢這兩個檢視**bam_PurchaseOrder_AllRelationships**以及所有檢視**bam_\<***OtherActivity* **> _AllRelationships**，其中\< *OtherActivity*> 相同的 BAM 檢視中的活動。  
  
 關聯性記錄屬於活動執行個體，但它們保留的執行個體資料的同步處理中所述[活動資料儲存區](../core/activity-data-storage.md)。  
  
## <a name="see-also"></a>另請參閱  
 [查詢 BAM 資料](../core/querying-bam-data.md)