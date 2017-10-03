---
title: "如何備份 BAM 分析和追蹤 Analysis Server 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, DTS packages
- backing up [BAM], Tracking Analysis Server database
- backing up [BAM], OLAP cubes
- backing up [BAM], DTS packages
- purging, OLAP cubes
- Analysis database [BAM], backing up
- scheduling, BAM backups
- backing up [BAM], Analysis database
- OLAP cubes, purging
- backing up, BAM
- backing up [BAM], database order
- DTS packages, backing up
- backing up [BAM], Star Schema database
- backing up [BAM], scheduling
- Tracking Analysis Server database [BAM], backing up
- Star Schema database [BAM], backing up
ms.assetid: d39e3491-ab54-44f2-990a-7b8ee86f0501
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e210fbe805e5a942605920e481faa2f1ca7cf2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases"></a>如何備份 BAM 分析和追蹤 Analysis Server 資料庫
商務活動監控 (BAM) 分析資料庫和追蹤 Analysis Server 資料庫會將內容儲存在 SQL Server Analysis Services Cube 中。 「備份 BizTalk Server」工作不會備份這些資料庫。 相反的，若要備份這些資料庫，您必須使用 SQL Server 分析管理員。  
  
 備份這些資料庫之後，您可能需要清除 OLAP Cube。 清除 OLAP Cube 時，您也必須執行下列步驟：  
  
1.  清除 OLAP Cube 之前，請先在 BAMStarSchema 資料庫中，截斷您要清除之 Cube 的事實資料表。 資料表命名慣例為"bam_*\<CubeName >*_Facts"。  
  
2.  清除 OLAP Cube 之後，您必須完整地處理作用中、已完成和虛擬的 Cube。  
  
 如需有關備份分析資料庫的指示，請參閱《SQL Server 線上叢書》中的＜封存 Analysis Services 資料庫＞。  
  
 **排程 BAM 資料庫的備份**  
  
 如果您使用 BAM，請確認在備份封裝依排程執行時，沒有 BAM Cube 程序或資料維護 Data Transformation Services (DTS) 封裝在執行。  
  
 若要確保所有的 BAM 資料庫中都有一致的結構描述，請在每次部署或解除部署 BAM 活動時，備份 BAM 資料庫和 DTS 封裝。  
  
 在每次部署或解除部署 BAM 檢視時，備份 BAM 分析資料庫與 BAMStarSchema 資料庫。  
  
 依下列順序備份 BAM 資料庫：  
  
1.  執行「備份 BizTalk Server」作業以備份 BAMPrimaryImport 資料庫和其他 BizTalk Server 資料庫。  
  
2.  針對所有活動執行 BAM 資料維護 DTS 封裝。  
  
     將這些步驟併入 DTS 封裝，並排程封裝以定期執行。 若要確保資料完整性，請確定在此備份封裝依排程執行時，沒有其他 BAM Cube 或資料維護 DTS 封裝在執行。  
  
     為了確保可以在 BAMArchive 資料庫失敗時復原完整的封存資料，請在複製資料分割到 BAMArchive 資料庫之後，但是要在從 BAMPrimaryImport 資料庫刪除資料分割之前，備份 BAMArchive 資料庫。 如果要這樣做，請修改每個活動的資料維護 DTS 封裝，以在 DTS 封裝中的最後一個步驟「結束封存」之前插入備份 BAMArchive 資料庫的步驟。  
  
3.  備份 BAMAnalysis 資料庫，然後備份 BAMStarSchema 資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)