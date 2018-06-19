---
title: 排程彙總 |Microsoft 文件
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
ms.openlocfilehash: 0cf2558b046d53deb6036553c5206beebd4d80ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269086"
---
# <a name="scheduled-aggregations"></a>排程彙總
BAM 排程彙總是以動態產生的 OLAP Cube 和 Data Transformation Services (DTS) 封裝為基礎。 排程彙總的資料代表商務活動在 DTS 封裝啟動時的快照。 若要達成此目的，分析的 DTS 封裝的第一個步驟是預存程序的呼叫**bam_Metadata_BeginAnalysis** ，將會擷取快照集組成：  
  
-   所有進行中之活動執行個體的快照複本  
  
-   檢視表，代表從上次執行 DTS 封裝到製作快照當時，將已完成的活動執行個體累加的視窗  
  
 為此，BAM 會極短暫地獨佔鎖定活動儲存區，以免在同一時間寫入任何資料。 一旦 BAM 製作快照時，DTS 封裝可能需要花費較長的時間進行處理，而 BAM 則將會忽略處理期間所送達的任何資料。 下圖說明這類活動：  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig9.gif "ebiz_prog_bam_data_maint_fig9")  
BAM 排程彙總  
  
 在此圖中，BAM 將已完成的活動執行個體之相關資料，移至已完成的執行個體 OLAP Cube。 BAM 以累加方式處理此 Cube。  
  
 同時，BAM 也將仍在進行中之活動的相關資料移至作用中的執行個體 Cube，以交由 DTS 封裝全權處理。 這是可以接受的做法，因為 BAM 假設任何特定時段只有少數活動仍在進行中。  
  
 排程彙總的資料存放於虛擬 Cube，此 Cube 隱藏了已完成活動與目前活動之間的差異。 如需詳細資訊，請參閱[查詢排程的彙總資料](../core/querying-scheduled-aggregated-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是彙總？](../core/what-is-an-aggregation.md)