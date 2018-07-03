---
title: 規劃資料庫測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4cf5e1f-a960-4702-a050-a2cdacddcbca
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce48244f67fd757fae5c2657634274625677850
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996615"
---
# <a name="planning-for-database-testing"></a>規劃資料庫測試
完整的壓力負載測試 BizTalk 解決方案 ultimate 的成功或失敗的方案中以突顯的方式判斷。 由於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能非常依賴的效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫、 測試和最佳化的 BizTalk 解決方案常見問題的焦點在於測試和最佳化執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]除此之外[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
## <a name="considerations-when-planning-for-database-testing"></a>規劃資料庫測試時的考量  
 規劃資料庫測試時，請考慮下列：  
  
1. **請確定測試環境盡可能符合生產環境。** 使用虛擬環境，例如 Microsoft HYPER-V Server 2008 進行單元測試是完全可以接受;不過，所有的載入/壓力測試應執行針對儘可能密集地符合最後一個生產環境的硬體。  
  
2. **計劃測量最大持續輸送量和 BizTalk Server 系統的最大持續性追蹤輸送量**。 最大持續輸送量會以 BizTalk Server 系統在生產環境中可無限處理的訊息流量最高的負載。 請依照下列 BizTalk Server 說明中的下列主題中的步驟：  
  
   - [測量最大持續性引擎輸送量](http://go.microsoft.com/fwlink/?LinkID=154388)(http://go.microsoft.com/fwlink/?LinkID=154388)。  
  
   - [測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)。  
  
     這些主題說明的方法來產生負載與針對系統、 要測量的參數和測試 MST 時要遵循的一般建議。  
  
3. **了解如何影響 BizTalk Server**  
    **實作主控件節流。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件節流演算法會嘗試中度的工作負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體，以確保工作負載不超過主控件執行個體的容量，或任何下游主控件執行個體。 節流機制會自行調整而且預設的設定選項適用於大部分的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理案例。 您應，不過，有的節流機制實作負載/壓力測試之前先深入了解。 如需詳細資訊，請參閱 <<c0> [ 最佳化資源使用狀況透過主控件節流](http://go.microsoft.com/fwlink/?LinkId=155770)(<http://go.microsoft.com/fwlink/?LinkId=155770>) 在 BizTalk Server 說明中。