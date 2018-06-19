---
title: BAM 動態基礎結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- infrastructure, BAM
- BAM, infrastructure
ms.assetid: 88f39438-3213-4f0d-8b8d-e6426c266138
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3660eeb6f85fb21ff78b7b833b21adbb3af87385
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230446"
---
# <a name="bam-dynamic-infrastructure"></a>BAM 動態基礎結構
BAM 基礎結構包含 SQL Server 資料表、 BAM 檢視、 預存程序和 Data Transformation Services (DTS) 封裝所設定和管理透過累加在 BAM 資料庫 （主要匯入、 封存、 星狀結構描述和分析）部署 BAM 定義。 基礎結構是 where、 在執行階段，事件會相互關聯、 彙總，且可供使用者查詢。  
  
 本節說明這些基礎結構程序中的一些程序。 例如，當您從應用程式 (BAM 定義) 擷取所需的資料之後，您就可以儲存它以便查詢。 此外，您還可以維護某些預先建立的資料彙總，以進行更快速的彙總查詢。  
  
 一般而言，您必須耗費許多開發精力來實作資料倉儲，才能達成這個功能。 但是，Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 BAM 卻可根據您的活動和檢視定義，自動產生 SQL 和 OLAP 基礎結構，而大幅簡化了這個程序。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [何謂 BAM 定義？](../core/what-is-a-bam-definition.md)  
  
-   [何謂 BAM 定義結構描述](../core/what-is-a-bam-definition-schema.md)  
  
-   [活動資料儲存區](../core/activity-data-storage.md)  
  
-   [什麼是彙總？](../core/what-is-an-aggregation.md)  
  
-   [查詢 BAM 資料](../core/querying-bam-data.md)  
  
-   [BAM 基礎結構限制](../core/bam-infrastructure-limitations.md)  
  
-   [如何在非英文的安裝中定義超出範圍的數字維度警示](../core/define-out-of-range-numeric-dimension-alerts-in-non-english-installations--bam.md)