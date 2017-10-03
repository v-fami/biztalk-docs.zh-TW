---
title: "實作階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04877156-cc32-480b-8410-d26eb073c327
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce6d7df21f15b40e0312438394859f4b94b7fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-phase-recommendations"></a>實作階段建議
實作階段承接需求和設計階段產品，並且使用適當的技術來加以實作。 在驗證測試實例中，完成和自動化測試實例以做好驗證測試的準備工作，即是在此階段進行。 一般而言，對於先期系統版本的許多測試也是在此階段中執行，不僅要驗證系統，而且也要驗證測試實例本身沒有問題。  
  
## <a name="implement-performance-test-cases"></a>實作效能測試實例  
 在需求和設計階段中，已經定義和設計了代表性的測試實例，以便證實系統效能符合或超越效能釋放準則。 在實作階段中，會實作、自動化並首次執行這些測試實例，確認 (當系統的各個部分都達到「程式碼完成」階段時) 測試是否已經可以驗證效能。  
  
 在實作階段，務必要盡可能將測試的安裝、執行和結果分析自動化。 效能測試的數量可能很龐大，而執行個別測試的時間也會很長，因此讓測試自動化可以增加執行測試的效率，並減少所需的人力資源。 此外，當您找到效能瓶頸並提出解決方法後，請在一段測試過程中，預先執行許多次的驗證測試。 自動化測試可讓您在不同的版本組建之間，更為輕鬆、快速和一致地重複執行效能驗證。  
  
## <a name="build-the-performance-test-bed"></a>建立效能測試台  
 以一致、可重現的方式執行所有的效能測試，極其重要。 如果還要比較這些測試的結果，使用完全相同的硬體來建立基準和執行測試，乃是關鍵所在。 視方案架構而定，有多種硬體變數都可能明顯影響測試結果。  
  
 例如，雖然無法單從檢視伺服器組態立即看出兩部伺服器的快取等級有何不同，但我們發現可用的記憶體快取 (即使在其他完全相同的伺服器上) 會明顯影響結果。 確保測試是在相同不變的測試台上執行，可以避免產生相容性問題。 如果您必須變更硬體組態 (例如，配合新的系統大小預估值進行調整時)，則應該重新建立基準，以利進行比較。  
  
## <a name="begin-performance-validation-testing"></a>開始效能驗證測試  
 效能測試幾乎總是與測試實作同時開始。  任何時候開始驗證釋放準則，永遠都不嫌早，因為愈快著手進行，就能愈快在發現問題時做出反應。  
  
 開始正式測試時，主要應考量測試中的系統 (或部分系統) 是否準備就緒。 系統是否準備就緒多半靠主觀判斷，但是應該與下列因素一併考慮：  
  
 您即將測試的系統途徑是否已完成程式碼？ 如果尚有重要的程式碼未加入途徑中，您最好考慮先將工作時間投入其他方面，等到所欠的「東風」吹來再說。  
  
 是否已經在系統上成功執行功能測試？ 它可以是非常耗時且效率不佳，設定和開始在系統或子系統找出沒有功能問題區塊進一步的效能測試所測試的效能。 請先確定您已經在功能上充分測試過該途徑，再開始進行效能測試。  
  
 要測試的系統或子系統風險等級如何？ 首先要調查的，應該是那些在達成效能釋放準則上帶有最高風險等級的系統途徑。 我們必須在專案生命週期中及早辨識出系統瓶頸，以爭取改變測試方向的時效，其重要性不言可喻。  
  
## <a name="see-also"></a>另請參閱  
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [需求階段建議](../core/requirements-phase-recommendations.md)   
 [設計階段建議](../core/design-phase-recommendations.md)   
 [驗證階段建議](../core/verification-phase-recommendations.md)   
 [發行階段建議](../core/release-phase-recommendations.md)