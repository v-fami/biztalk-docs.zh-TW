---
title: "資料庫測試規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4cf5e1f-a960-4702-a050-a2cdacddcbca
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c0f9b54c866b3ab3d1eebc56bb815284ba3d7c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-database-testing"></a>規劃資料庫測試
徹底的壓力負載測試 BizTalk 解決方案中的最後成功或失敗方案圖以突顯的方式。 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能非常依賴的效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫、 測試和最佳化的 BizTalk 解決方案經常將著重在測試和最佳化執行之電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，存放[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
## <a name="considerations-when-planning-for-database-testing"></a>規劃資料庫的測試時的考量  
 資料庫測試計劃時，請考慮下列：  
  
1.  **確保測試環境，儘可能密集地符合實際執行環境。** 使用單元測試的虛擬環境，例如 Microsoft HYPER-V Server 2008 是完全可以接受;不過，所有負載/壓力測試應該都執行對儘可能密集地符合最後的實際執行環境的硬體。  
  
2.  **計劃來測量最大持續輸送量和 BizTalk Server 系統的最大持續性追蹤輸送量**。 在生產環境中 BizTalk Server 系統可無限處理的訊息流量的最高負載會以最大持續輸送量。 請依照下列中的下列主題中的步驟[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]協助：  
  
    -   [測量最大持續性引擎輸送量](http://go.microsoft.com/fwlink/?LinkID=154388)(http://go.microsoft.com/fwlink/?LinkID=154388)。  
  
    -   [測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)。  
  
     這些主題會說明產生負載的系統、 要測量的參數和測試 MST 時所應遵循的一般建議的方法。  
  
3.  **了解如何影響 BizTalk Server**  
     **實作主控件節流。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件節流演算法會嘗試進行中等程度的工作負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體，以確保工作負載不超過主控件執行個體的容量，或任何下游主控件執行個體。 節流機制會自行調整而且適用於大部分的預設組態選項[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理實例。 您應，不過，深入了解實作/壓力的負載測試之前的節流機制。 如需詳細資訊，請參閱[最佳化資源使用量透過主控件節流](http://go.microsoft.com/fwlink/?LinkId=155770)(http://go.microsoft.com/fwlink/?LinkId=155770) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。