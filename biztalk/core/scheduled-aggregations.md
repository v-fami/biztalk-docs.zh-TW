---
title: 排程彙總 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- scheduling, aggregations [BAM]
- aggregations [BAM], scheduling
ms.assetid: 4e2da2eb-b1fc-4b27-98d6-564e6df719e1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04aaf0a3eefb018dbe23f3e05e7e684b595820d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998471"
---
# <a name="scheduled-aggregations"></a>排程彙總
BAM 排程彙總是以動態產生的 OLAP Cube 和 Data Transformation Services (DTS) 封裝為基礎。 排程彙總的資料代表商務活動在 DTS 封裝啟動時的快照。 若要這麼做，分析 DTS 封裝的第一個步驟是呼叫預存程序**bam_Metadata_BeginAnalysis** ，就會擷取快照集所組成：  
  
- 所有進行中之活動執行個體的快照複本  
  
- 檢視表，代表從上次執行 DTS 封裝到製作快照當時，將已完成的活動執行個體累加的視窗  
  
  為此，BAM 會極短暫地獨佔鎖定活動儲存區，以免在同一時間寫入任何資料。 一旦 BAM 製作快照時，DTS 封裝可能需要花費較長的時間進行處理，而 BAM 則將會忽略處理期間所送達的任何資料。 下圖說明這類活動：  
  
  ![](../core/media/ebiz-prog-bam-data-maint-fig9.gif "ebiz_prog_bam_data_maint_fig9")  
  BAM 排程彙總  
  
  在此圖中，BAM 將已完成的活動執行個體之相關資料，移至已完成的執行個體 OLAP Cube。 BAM 以累加方式處理此 Cube。  
  
  同時，BAM 也將仍在進行中之活動的相關資料移至作用中的執行個體 Cube，以交由 DTS 封裝全權處理。 這是可以接受的做法，因為 BAM 假設任何特定時段只有少數活動仍在進行中。  
  
  排程彙總的資料存放於虛擬 Cube，此 Cube 隱藏了已完成活動與目前活動之間的差異。 如需詳細資訊，請參閱 <<c0> [ 查詢排程的彙總資料](../core/querying-scheduled-aggregated-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 [何謂彙總？](../core/what-is-an-aggregation.md)