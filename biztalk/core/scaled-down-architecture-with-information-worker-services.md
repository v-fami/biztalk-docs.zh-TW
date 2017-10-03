---
title: "縮小架構具有資訊工作者服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
ms.assetid: ce1217bf-84a5-4888-89ba-dce85dc38340
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d02558e5904bf740c09ea0db614b2189555ac75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-down-architecture-with-information-worker-services"></a>使用資訊工作者服務縮小架構
完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下圖提供範例 BizTalk Server 架構，包括結合一些網域與 BizTalk Server 以降低您需要的伺服器與防火牆之數目的資訊工作者服務。 雖然此架構並非最分散的架構，但仍根據其功能來分隔 BizTalk Server。  
  
 ![規模縮減拓撲](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")  
  
        Scaled Down Architecture with Information Worker Services  
  
 在上圖中，服務介面與服務網域中的伺服器對應至 BizTalk 主控件，而不是實體伺服器。 雖然建議您將主要密碼伺服器與管理工具保存在獨立電腦中，但您可以讓追蹤、處理、傳送以及接收主控件的主控件執行個體在多重電腦上執行。 同理，周邊網路中的伺服器對應至邏輯位置。  
  
 周邊網路中的 SMTP、Windows 訊息佇列 (也稱為 MSMQ)、檔案以及 SQL 伺服器，分別對應至郵件伺服器、佇列、目錄或 SQL Server，服務介面網域中的 BizTalk 接收與傳送主控件由此接收和傳送訊息。  
  
 資料網域中的 BAM 資料庫包含「BAM 主要匯入」、「BAM 分析」、「BAM 星狀結構描述」以及「BAM 封存」資料庫。 「資料」網域中的「追蹤」與「分析」資料庫是 BizTalk Server 用於儲存追蹤資訊的資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [縮小架構](../core/scaled-down-architecture.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [設計安全架構](../core/designing-a-secure-architecture.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)