---
title: "如何識別 BAM 主要匯入資料庫中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0372f1f1-d892-4f7d-b6c4-e0f2b5a02f1c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5780c8fcc893126997b37f687f010c5eb62e74c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-primary-import-database"></a>如何識別 BAM 主要匯入資料庫中的瓶頸
若要識別商務活動監控 (BAM) 資料庫中的瓶頸，請執行下列步驟：  
  
1.  確定作用中執行個體的計數未上升。  
  
2.  確認 SQL-Agent 服務正在執行。  
  
3.  如果已設定 OLAP 分析，請確定 BAM_AN_\<activityname\>定期執行作業。  
  
4.  請確定該 BAM_DM_\<activityname\> (Data Maintenance) 工作排定在定期間隔執行。  
  
    > [!NOTE]  
    >  在高使用率案例 BAM 資料庫活動可能會影響到其他 BizTalk Server 資料庫，將會影響 BizTalk Server 的整體效能的效能。 在此情況下，請考慮採取下列動作：  
    >   
    >  -   請考慮減少從預設值 （6 個月） 的所有 BAM 活動的持續時間為 1 個月或更小。 這會降低其 BAM 資料會保留在 BAMPrimaryImport 資料庫封存之前的時間週期。 使用 BAM 管理公用程式`set-activitywindow`命令來修改 BAM 活動的持續時間。 如需 BAM 管理公用程式的活動管理命令查看[活動管理命令](http://go.microsoft.com/fwlink/?LinkId=210417)(http://go.microsoft.com/fwlink/?LinkId=210417)。  
    > -   將 BAM 封存資料庫移至未裝載任何 BizTalk MessageBox 資料庫的 SQL Server 執行個體。 這將會競用資源時，防止這些資料庫，並改善整體效能。  
  
5.  用於追蹤專用的主機，並測量在負載下的主控件佇列長度效能計數器。  
  
6.  經過一段時間檢查遞增趨勢的多工緩衝處理表格大小效能計數器。  
  
7.  請檢查長時間執行的封存/清除作業執行持續時間。  
  
8.  在裝載 「 BizTalk 追蹤資料庫的磁碟，請檢查磁碟回應性 （讀/寫效能計數器每次磁碟秒數）。  
  
## <a name="see-also"></a>請參閱  
 [資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)