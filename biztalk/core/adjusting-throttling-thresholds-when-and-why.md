---
title: 調整節流閾值： 時間和原因 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9afb26c8-e5f4-4b78-9a45-a1263e3cb6ab
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b49ae78d4b2d0cf2dabfc69af9023b1e8676dea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229926"
---
# <a name="adjusting-throttling-thresholds-when-and-why"></a>調整節流閾值： 時間和原因
當處理節流時，一個大小無法滿足所有的需要。 有各種因素，可決定最佳的設定應該是什麼。 有一個現成的方式，就是 BizTalk Server 提供了已經過測試證明的預設值，可有效保護系統不受待處理項目的傷害。 但在某些情況下，這個作法可能太過激烈， 下列範例將說明這一點。  
  
## <a name="example-1-peak-loads-and-database-size"></a>範例 1： 尖峰負載和資料庫大小  
 BizTalk Server 上所建置的每一個方案都有持續性輸送量上限 (MST)。 就定義上而言，只要負載維持在此上限以下，系統就可以永遠維持該負載。 但就實際面而言，在負載設定檔中擁有尖峰和低峰要比擁有穩定且不會隨著時間變化的負載更為常見。  
  
 建置一個系統來處理尖峰負載下的某些待處理項目並在低峰時復原，是一個比較具成本效益的作法，而不要建置一個能夠處理永遠在最高尖峰負載的系統。 但是，如果尖峰負載時所預期的待處理項目高於資料庫大小的預設節流值，則系統將會節流輸入來封鎖待處理項目。 如果這不是您想要的結果 (例如，因為您需要盡快消耗所有的輸入檔案)，則解決方案就是要增加資料庫大小閾值，以便在節流之前接受預期的待處理項目。  
  
## <a name="example-2-memory-usage-optimization"></a>範例 2： 記憶體使用量最佳化  
 為了要測量處理速度，節流所使用的另一個資源，就是測量主控件處理序可使用多少記憶體。 如果與閾值相較之下，可用的記憶體變得太少，節流就會減少引擎從要處理之主控件佇列中擷取的訊息數目。 在現今的企業等級伺服器中，記憶體的數量和可用性都可以有變化，特別是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中提供了 x64 支援，所以可能需要增加或減少閾值，讓記憶體使用量最佳化。  
  
## <a name="recommendation"></a>建議  
 根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中會設定節流，為系統提供立即可用的完善保護。 但是，不應該理所當然地將預設設定視為最佳化設定。 請監視效能計數器來瞭解節流狀態，看看是否正在進行節流，然後自行測量節流所依據的資源 (例如，資料庫大小或記憶體使用量) 是過度利用還是利用不足，然後據此來往上或往下調整閾值。