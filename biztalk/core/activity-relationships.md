---
title: 活動關係 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], relationships
ms.assetid: da7c7205-18c6-44df-af03-3140214c84e6
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3709ad02ed082595665c68485502847b52e5a1d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225230"
---
# <a name="activity-relationships"></a>活動關係
當活動與一或多個其他活動相關聯時，便存在活動關係， 例如，多個「出貨」活動與單一「訂單」活動相關聯，或者一個「出貨」活動包含兩個「訂單」活動的項目。  
  
 若要指示兩個相關的活動，您必須知道兩個活動的名稱，並且在記憶體中具有對應的 ActivityID 以便呼叫 AddRelatedActivity。 這個 API 會在對應的活動記錄之間建立連結。  
  
 在下圖中，反白的程式碼行說明您可以用何種方式在「訂單」活動執行個體 #123 以及「出貨」活動 #1549、1550 和 1551 之間建立關係。  
  
 ![](../core/media/activity-relationships-example.gif "activity_relationships_example")  
  
 商務使用者會查看一個顯示訂單歷程記錄的網頁。 它可能表示上午 10 到達時加以、 兩天後收到核准，和頁面會提供實際文件的連結。 網頁也會因為上圖中的程式碼，提供可將商務使用者導向對應的出貨網頁的超連結。  
  
> [!NOTE]
>  所有呼叫`AddRelatedActivity`之間應該發生`BeginActivity`和`EndActivity`。  
  
## <a name="see-also"></a>另請參閱  
  
 [活動接續](../core/activity-continuation.md)   
 [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)   
 [BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)   
 [BAM API，從協調流程運算式 （BizTalk Server 範例）](../core/bam-api-from-an-orchestration-expression-biztalk-server-sample.md)