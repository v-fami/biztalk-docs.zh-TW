---
title: 擱置的訊息會包含在訊息中的計數資料庫節流閾值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9eb708bb-6d6d-4494-8b8d-67aa44800a20
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f8ea0643ccf2d6206ba86bc56b5dd54c0d51115
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278126"
---
# <a name="suspended-messages-are-included-in-the-message-count-in-database-throttling-threshold"></a>資料庫節流閾值中的訊息計數有包含擱置的訊息
根據預設，主控件**訊息 DB 中的計數**節流閾值會設為 50000，將會觸發節流狀況，在下列情況下的值：  
  
-   主控件執行個體發佈到訂閱之主控件的工作、狀態和擱置佇列的訊息總數超過 50,000。  
  
-   多工緩衝處理表格或追蹤表格中的訊息數目超過 50,000 個訊息。  
  
 因為已擱置的訊息會包含在**訊息 DB 中的計數**計算，可以進行訊息發佈即使 BizTalk server 很低或完全無負載的節流。  
  
## <a name="recommendations"></a>建議  
  
-   如果您預期，您可能會有大量擱置的訊息，請考慮增加的預設值為**訊息 DB 中的計數**包含 SQL server 的空間需求納入考量的臨界值BizTalk 資料庫。 也請考慮增加**多工緩衝處理乘數**和**追蹤資料乘數**值，以便讓多工緩衝處理資料表中的其他待處理項目。  
  
     如需有關這些值的詳細資訊，請參閱[如何修改資源基礎節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。  
  
-   使用**訊息發佈節流狀態**與相關聯的效能監視器計數器**biztalk: Messageagent**效能物件類別，來測量目前的節流狀態。 如果這個計數器傳回 6 的值，則會檢查是否有擱置的執行個體，並視需要終止擱置的執行個體，或讓它繼續。  
  
     如需主控件節流效能計數器的詳細資訊，請參閱[主控件節流效能計數器](../core/host-throttling-performance-counters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [節流設計建議](../core/throttling-design-recommendations.md)