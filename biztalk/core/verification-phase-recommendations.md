---
title: "驗證階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00663354-ce5d-4391-b835-89940c92c1ce
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25344eafc37f492474b3f0bb36318afaf566829a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="verification-phase-recommendations"></a>驗證階段建議
在系統程式碼完成之後，即可開始全面加強其穩定性，並驗證其是否符合釋放準則。 這個階段通常稱為穩定化階段。 此階段的最終目標是要找出並修復錯誤，以及證實系統已準備好可以實際執行。 因此，在這個階段中，會對系統的發行候選版本進行終段測試。  
  
 發行候選版本是指在通過所有驗證測試的條件下，我們認為其完成度及穩定性夠得上發行水準的系統版本 (通常是最近完成的)。 要證實這點，就必須順利完成許多功能、效能及壓力測試，確認系統已準備就緒。  
  
## <a name="test-to-verify-sustainable-throughput-and-latency"></a>測試以確認持續性輸送量與潛在因素  
 驗證效能的測試雖然和實作階段同時展開，但最後必須在證明成功通過整套釋放準則測試的發行候選版本上定案。 最理想的情況是，發行候選版本在終段測試期間，其測試結果未出現任何改變，讓人十分確信沒有帶進回復 (新功能對舊功能產生負面影響) 的因子。 這在實務上頗為困難，因為只要在組建內稍做變更，就必須對回復的風險進行評估。  
  
 例如，如果系統成品 (如管線或協調流程) 中發生基本的變更，很可能就必須重新執行效能測試，以便驗證這個新的發行候選版本。  
  
 為了確保系統已經準備好可以實際執行，您必須確認系統已在持續性方式下經過首尾連貫的測試。 這表示所有的作業活動，例如資料庫維護，操作查詢與計劃和未規劃的中斷必須進行測試，如本主題中所定義[何謂持續性效能？](../core/what-is-sustainable-performance.md) 這是證明系統整備所以結合一套完整的最終測試通過中的持續性效能測試的最後機會。  
  
## <a name="identify-bottlenecks-and-adjust-hardware-or-solution-to-remove-goal-blockers"></a>識別瓶頸與調整硬體，或者說，移除目標阻礙的解決方案  
 在實務上，因此常會最終測試通過的測試平台會更接近硬體方面的生產環境與測試台的開發環境。  因此，最終測試通過期間利用這個機會，識別系統中的任何新的或現有的瓶頸，並決定它們是否足以需要調整硬體的相當重要。 即使不需要立即調整硬體，發現最主要的系統瓶頸將可以提供寶貴的規劃和作業資訊。  
  
 例如，如果系統可以支應實際執行時的一般負載情況，但發覺 MessageBox 伺服器上的實體磁碟閒置率很低 (例如，低於 20%)，那麼您就可以將實際執行期間對此磁碟的監控結果認定為一個關鍵狀況指標。 此外，任何要增加系統負載能力的計劃，也可以將磁碟子系統需要改善的這項認知納入考量。  
  
## <a name="see-also"></a>另請參閱  
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [需求階段建議](../core/requirements-phase-recommendations.md)   
 [設計階段建議](../core/design-phase-recommendations.md)   
 [實作階段建議](../core/implementation-phase-recommendations.md)   
 [發行階段建議](../core/release-phase-recommendations.md)