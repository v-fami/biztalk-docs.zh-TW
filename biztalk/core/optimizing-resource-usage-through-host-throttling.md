---
title: "透過主控件節流將資源使用最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host throttling
- performance, host throttling
ms.assetid: 823b431d-707d-4201-9a6e-4a879e767b66
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa30cb66371ef519741658dec47e08f6f92e871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-resource-usage-through-host-throttling"></a>透過主控件節流將資源使用最佳化
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]利用數種不同的 Microsoft 技術，其中每個可能會耗用大量記憶體、 磁碟和 BizTalk server 和包含 BizTalk Server 資料庫的 SQL 伺服器上可用的 CPU 資源。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]利用節流機制協助管理以降低使用的資源競爭可用資源的使用。 本主題討論此機制的設計。 如需如何調整節流值的資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能微調](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [什麼是主控件節流？](../core/what-is-host-throttling.md)  
  
-   [BizTalk Server 如何實作主控件節流](../core/how-biztalk-server-implements-host-throttling.md)  
  
-   [主控件節流效能計數器](../core/host-throttling-performance-counters.md)  
  
-   [節流設計建議](../core/throttling-design-recommendations.md)