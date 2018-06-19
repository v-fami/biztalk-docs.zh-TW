---
title: 相關活動 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], related activities
- Query Builder [BAM portal], related activities
- queries [BAM], related activities
- Query Builder [BAM portal], viewing details
- queries [BAM], viewing details
ms.assetid: 141b7943-d244-4810-aa88-12aa4a2b7658
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f50e4de965e8f1efaa1454bb9123317ae904f7e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971852"
---
# <a name="related-activities"></a>相關活動
[相關活動] 區域包含與查詢基礎活動相關的活動清單。 多個「出貨」活動便是「訂單」活動之相關活動的典型範例，因為單一訂單上的項目可以分成多次出貨來交運。  
  
## <a name="creating-related-activities"></a>建立相關活動  
 相關活動的清單可以由下列兩種方式產生：  
  
-   定義兩個活動，然後建立包含這兩個活動的單一檢視。 開發人員可以透過實作活動間的索引鍵、欄位和數值關係，藉此在這兩個活動之間建立相互關聯連接。  
  
-   定義兩個活動。 您的開發人員在自訂應用程式中建立相互關聯連接，藉由呼叫 AddRelationship() 定義索引鍵、 欄位和值在活動之間的關聯性。  
  
 其中一種方式來定義活動關係中加入資料列\<activityname\>_Relationships 資料表。  
  
> [!NOTE]
>  只有第一種定義關係的方法可以使相關活動彼此間存在即時連結。 第二種方法不會定義跨距檢視，因此，入口網站無法得知兩個活動之間的關係。  
  
## <a name="see-also"></a>請參閱  
 [如何檢視活動搜尋的結果](../core/how-to-view-the-results-of-an-activity-search.md)