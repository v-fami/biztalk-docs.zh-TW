---
title: "規則引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RuleEngine object
- Business Rules Engine, ruleset executor
- Business Rules Engine, ruleset translator
- Business Rules Engine, ruleset tracking interceptor
- Business Rules Engine, Business Rules Engine
ms.assetid: c4043a1f-357f-47bc-84e1-5e4bd9f8b5b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dc2d293697ccbb64851591037440d0371c1346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rule-engine"></a>規則引擎
本節會描述商務規則引擎的數個元件、功能及作業。 規則引擎會提供規則集的執行環境。 **RuleEngine**物件會使用下列外掛程式元件進行實作：  
  
-   **規則集執行子 （推斷引擎）**。 實作負責規則條件評估及動作執行的演算法。 預設的規則集執行子是一個辨識網路型向前鏈結推斷引擎，其設計目的是最佳化記憶體中的作業。  
  
-   **規則集轉譯程式**。 輸入**RuleSet**物件，並會產生可執行檔規則集的表示。 預設的記憶體中轉譯程式會從規則集定義中建立編譯的辨識網路。  
  
-   **規則集追蹤攔截器**。 接收來自規則集執行子 (推斷引擎) 的輸出，並將輸出轉送至規則集追蹤及監控工具。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)  
  
-   [議程與優先順序](../core/agenda-and-priority.md)  
  
-   [引擎控制函式](../core/engine-control-functions.md)  
  
-   [商務規則引擎中的資料存取](../core/data-access-in-the-business-rule-engine.md)  
  
-   [規則動作的副作用](../core/rule-action-side-effects.md)  
  
-   [商務規則引擎中的類別繼承支援](../core/support-for-class-inheritance-in-the-business-rule-engine.md)  
  
-   [規則引擎組態和調整參數](../core/rule-engine-configuration-and-tuning-parameters.md)  
  
-   [使用規則引擎時的效能考量](../core/performance-considerations-when-using-the-rule-engine.md)  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎](../core/business-rules-engine.md)