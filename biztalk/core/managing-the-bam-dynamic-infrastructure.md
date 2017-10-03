---
title: "管理 BAM 動態基礎結構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- infrastructure, managing [BAM]
- managing [BAM], infrastructure
ms.assetid: af8a76b5-407a-484d-aff4-0d911f88313e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 631a6bb3bab613004e11410a382687147e4adad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bam-dynamic-infrastructure"></a>管理 BAM 動態基礎結構
商務活動監控 (BAM) 功能會使用動態產生的 SQL 和線上分析處理 (OLAP) 基礎結構。 系統管理員可以使用 BAM 管理公用程式，以部署商務分析師所開發的 BAM 定義活頁簿或 XML 檔案。  
  
 BAM 動態基礎結構是由 BAM 活頁簿檢視、BAM 部署、BAM Data Transformation Services (DTS) 封裝以及 BAM 資料庫所組成。 如需有關 BAM 動態基礎結構的詳細資訊，請參閱[BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)。  
  
 當您設定 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，BizTalk Server 會建立下列 BAM 資料庫：  
  
-   BAM 主要匯入 (BAMPrimaryImport) 資料庫  
  
-   BAM 星狀結構描述 (BAMStarSchema) 資料庫 (選擇性)  
  
-   BAM 分析 (BAMAnalysis) 資料庫 (選擇性)  
  
-   BAM 封存 (BAMArchive) 資料庫  
  
 BAM 資料庫的詳細資訊，請參閱[管理 BAM 資料庫](../core/managing-bam-databases.md)。  
  
 系統管理員負責執行下列 BAM 基礎結構的管理工作，本節將詳細說明這些工作：  
  
-   部署與解除部署 BAM 定義和檢視  
  
-   管理使用者對 BAM 檢視的存取  
  
-   執行 BAM DTS 封裝  
  
-   備份 BAM 資料庫  
  
## <a name="in-this-section"></a>本節內容  
  
-   [管理 BAM 定義](../core/managing-bam-definitions.md)
  
-   [管理 BAM 安全性](../core/managing-bam-security.md)  
  
-   [管理彙總](../core/managing-aggregations.md) 
  
-   [管理 BAM 資料庫](../core/managing-bam-databases.md)
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)