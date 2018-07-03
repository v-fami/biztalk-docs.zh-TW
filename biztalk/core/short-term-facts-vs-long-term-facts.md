---
title: 短期事實與長期事實 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- facts, short-term
- facts, long-term
- short-term facts
- business rules, facts
- long-term facts
ms.assetid: de020b20-1012-498a-969e-4adc4549918c
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ed46b71c205ef7db5dc8d918ba0cdae68ebd41d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990007"
---
# <a name="short-term-facts-vs-long-term-facts"></a>短期事實與長期事實
有兩種事實會判斷提示到規則引擎的工作記憶體 – 一為短期事實，另一為長期事實。  
  
## <a name="short-term-facts"></a>短期事實  
 短期事實是規則引擎的單一執行循環所特有的。 短期事實會在原則執行之後自動從規則引擎的工作記憶體中撤回。 如果原則的資料在規則引擎的執行循環之間有所變更，則可以將該資料當做短期事實提交至規則引擎。  
  
 短期事實的範例：  
  
-   做為參數提交的事實**Policy.Execute**方法。  
  
-   做為參數提交的事實**呼叫規則**圖形。  
  
-   從動作的規則，使用您提交的事實**Assert**函式。  
  
## <a name="long-term-facts"></a>長期事實  
 長期事實會載入至規則引擎的工作記憶體中，供任意數目的執行循環使用。 一般而言，長期事實是變更緩慢的事實，一般不會在原則的執行作業之間變更。 例如，您可能只想建立一次資料庫連線，然後使用同一個資料庫連線來執行原則數次。 短期事實和長期事實唯一真正的差異在於實作。  
  
 若要將事實當做長期事實提交，需要執行下列步驟：  
  
1. 建立事實擷取器可實作**IFactRetriever**介面。 建立和判斷提示至規則的工作記憶體的事實引擎何時**UpdateFacts**會叫用方法的第一次的時間和更新時在後續叫用的事實**UpdateFacts**方法。  
  
2. 使用商務規則編輯器將原則設定為使用事實擷取器。  
  
   如需建立事實擷取器和原則中使用它的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。  
  
## <a name="see-also"></a>另請參閱  
 [事實](../core/facts.md)