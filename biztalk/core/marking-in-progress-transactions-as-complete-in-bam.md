---
title: "標示為在 BAM 中完成進行中交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, data recovery
- data recovery, BAM
- BAM, data loss
- data loss, BAM
ms.assetid: 8f734953-483a-481a-9ded-b48923859199
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 508001fcc1023acfd54b7d28bea7f246cb6a1a2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="marking-in-progress-transactions-as-complete-in-bam"></a>在 BAM 中將進行中的交易標示為完成
商務活動監控 (BAM) 會將未完成追蹤執行個體的資料保留在特殊的作用中執行個體資料表。 如果部分執行個體記錄在最後一次備份前開始，但在備份之後完成，則這些記錄將會保留在作用中執行個體資料表。 雖然這不會讓系統無法運作，您仍然可以將這些記錄手動標示為已完成，如此即可從作用中執行個體資料表中將其移出。  
  
 對 BAM 主要匯出資料庫發出下列查詢，即可判定指定活動的未完成 ActivityID 清單：  
  
```  
Select ActivityID from bam_<ActivityName> where IsComplete = 0  
```  
  
 如果外部系統的資料顯示活動執行個體已完成，您可以使用下列查詢手動完成此執行個體：  
  
```  
exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
```  
  
## <a name="see-also"></a>另請參閱  
 [解決資料遺失](../core/resolving-data-loss.md)