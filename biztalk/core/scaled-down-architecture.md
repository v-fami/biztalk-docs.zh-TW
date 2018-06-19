---
title: 縮小架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
ms.assetid: e25798aa-4a1e-418c-9e0c-db964e8b5a80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a112f3f737a1a5aec0cfac16b7689d3dada1e8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269358"
---
# <a name="scaled-down-architecture"></a>縮小架構
如需系統架構的完整資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下圖提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構範例，這個架構合併了部分網域與 BizTalk Server，以降低您需要的伺服器與防火牆數量。 雖然此架構並非最分散的架構，但仍根據其功能來分隔 BizTalk Server。  
  
 ![縮小架構](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")  
  
        Scaled Down Architecture  
  
 在上圖中，服務介面與服務網域中的伺服器對應至 BizTalk 主控件，而不是實體伺服器。 雖然建議您將主要密碼伺服器與管理工具保存在獨立電腦中，但您可以讓追蹤、處理、傳送以及接收主控件的主控件執行個體在多重電腦上執行。 同理，周邊網路中的伺服器對應至邏輯位置。  
  
 周邊網路中 SMTP、訊息佇列、檔案及 SQL 等伺服器，分別對應至郵件伺服器、佇列、目錄或 SQL Server，處理與服務網域中的 BizTalk 接收與傳送主控件會由此接收和傳送訊息。  
  
## <a name="see-also"></a>另請參閱  
 [縮小具有資訊工作者服務的架構](../core/scaled-down-architecture-with-information-worker-services.md)   
 [大型分散式的架構](../core/large-distributed-architecture.md)   
 [設計安全架構](../core/designing-a-secure-architecture.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)