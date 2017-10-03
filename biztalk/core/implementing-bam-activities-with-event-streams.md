---
title: "實作 BAM 活動與事件資料流 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], about activities
- activities [BAM]
- BAM, activities
ms.assetid: 94e6d9dd-93c3-4ab0-9de7-a860dd1e3406
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63594b956affc0f5b94f26ccdcb10d904ef171cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-bam-activities-with-event-streams"></a>使用事件資料流實作 BAM 活動
BAM 活動代表商務中的工作單位，例如訂單或貸款申請。 活動會對商務使用者或資訊工作者顯示，有關此工作單位的歷程記錄 (里程碑) 和資料。 例如，貸款申請活動可能包含如「已核准貸款」的里程碑，以及如「申請者名稱」和「貸款金額」等資料。 BAM 活動通常會直接對應到商務程序，但是在高階抽象概念中，活動與您 IT 基礎結構的實際實作無關。  
  
 身為開發人員的工作，就是只從特定活動內容中的實作公開相關的里程碑和資料。 如需示範如何使用活動的程式碼範例，請參閱[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [為何為 BAM 撰寫程式碼？](../core/why-write-code-for-bam.md)  
  
-   [開發人員適用的 BAM 概念](../core/bam-concepts-for-the-developer.md)  
  
-   [BAM 開發程序的概觀](../core/overview-of-the-bam-development-process.md)  
  
-   [EventStream 類別](../core/eventstream-classes.md)  
  
-   [使用活動](../core/using-an-activity.md)  
  
-   [活動關係](../core/activity-relationships.md)  
  
-   [活動接續](../core/activity-continuation.md)  
  
-   [迴圈活動](../core/looping-activities.md)  
  
-   [檢測解決方案： 逐步 API 使用方式](../core/instrumenting-a-solution-step-by-step-api-usage.md)