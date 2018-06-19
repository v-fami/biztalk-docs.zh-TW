---
title: 需求階段建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b510313-c3a7-42bc-9c9b-336c927a5d4a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d945e50d9c7b8f0a9feae5e0f93a4766d108c695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271014"
---
# <a name="requirements-phase-recommendations"></a>需求階段建議
與需求階段有關的主要工作事項是制定需求規格，或者說，制定一份包含附帶效能目標之需求的功能規格。 在決定這些目標時，必須將系統的使用者和企業主一併列入考慮，才能取得精確的效能分析資料。  
  
## <a name="establish-performance-criteria"></a>建立效能準則  
 從效能觀點來看，在此階段建立的功能規格中，最重要的部分是為專案定義詳細的效能目標，以及建立效能釋放準則。 定義效能準則時，有三個關鍵要素：  
  
-   以時間函式來定義效能的曲線。  
  
-   與效能函式關聯的效能需求。  
  
-   檔案大小與類型的散佈。  
  
 這些準則會討論[何謂持續性效能？](../core/what-is-sustainable-performance.md)  
  
 您可以從效能目標中推導出應用程式的效能釋放準則。 這些準則具體描述一個可達成且可評量的行為模式，您可以經由測試來證實。 除非已經符合所有的釋放準則，或者在無法達成時，認定發生了釋放準則的例外情況，否則不會將應用程式推出發行。  
  
 在產品週期的先期階段中設定釋放準則，是非常重要的。 這麼做，意味著所有相關人員在正式同意設計與實作前，都知道目標是什麼，以及未達成準則的後果。  
  
 此外，效能測試案例也將以釋放準則的評量方式為依歸，所以這個準則必須夠詳細，才能避免產生混淆。 例如，在陳述要達成的特定輸送量時，就應該包括：  
  
-   執行時必須使用的硬體，例如，伺服器的數量及類型、磁碟速度/類型等  
  
-   要測試什麼實例，例如，應用程式會採用何種路徑訊息  
  
-   評量的方法，例如，使用效能計數器、自訂程式碼、測試訊息抵達某部分的次數等  
  
 格式完整的釋放準則必須讓任何人都能夠檢視做成文件的釋放準則，並瞭解如何建立測試案例來驗證準則。  
  
## <a name="identify-performance-risks"></a>識別效能風險  
 在充分制定效能目標及釋放準則的細節之後，可以進行初步的效能風險範圍評估。 這項分析的目的是找出應用程式中可能需要在設計上多加注意、另行解決或刪減的部分，以利達成期望的準則。  
  
 例如，每個傳輸配接器類型都有本身的效能及容量縮放特性。 如果所需的輸送量超過其中一或多個 (接收或傳送) 配接器類型的能力，則可能有必要研究調查擴充配接器的替代方法。  
  
## <a name="estimate-sizing"></a>預估規模大小  
 確立目標和準則而知所遵循之後，最好盡早開始預估達到目標所需的硬體規模。 如同使用任何大小估計的投入時間，一個必須依據估計實際的測試結果。 在專案的先期階段中，這些結果可能得仰賴外部來源。 您可以在閱讀案例研究位於 BizTalk Server 開發人員中心， [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339)。 這些案例研究會提供有關已測試實例、執行測試的硬體及測試組態的詳細資料。 您可以從這些測試案例達成的效能進行推斷，來取得系統的初步規模預估。  
  
 請記住，沒有預測模型或模擬，準確預測的任何應用程式上執行的系統大小[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是一個平台可供部署繁多的應用程式方案，每個都有它自己的效能行為。 因此，雖然使用現有案例研究結果推得的預估資料，在規劃工作上提供了良好的起點，但即使是最簡單的應用程式架構，其系統的最終規模也必定需要加以調整。  
  
## <a name="plan-for-sufficient-testing"></a>規劃充分的測試  
 如上所述，目前沒有模型或模擬方法可以準確預測滿足效能目標所需的硬體。 這代表實際驗證系統是否能夠達成目標的唯一辦法，就是在實際執行等級的硬體上測試它。 也就是說，要在盡可能接近實際執行環境的硬體上執行測試案例。  
  
 這個部分的規劃工作是關鍵所在，您必須綜覽持續性效能的原則，並詳細瞭解輸送量分析資料和效能釋放準則。 使用現有資料推估而得的輸送量分析資料時，必須導出能夠一致地評量釋放準則的測試案例。 執行測試案例時，也必須考慮到持續性的問題。 如需持續性測試的範例，請參閱下列主題：  
  
-   [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)  
  
-   [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)  
  
## <a name="see-also"></a>另請參閱  
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [設計階段建議](../core/design-phase-recommendations.md)   
 [實作階段建議](../core/implementation-phase-recommendations.md)   
 [驗證階段建議](../core/verification-phase-recommendations.md)   
 [發行階段建議](../core/release-phase-recommendations.md)