---
title: 短期事實與長期事實 |Microsoft 文件
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
ms.openlocfilehash: 3d5c37926fb1da5499f34e22c35f8a8f32d238bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271038"
---
# <a name="short-term-facts-vs-long-term-facts"></a>短期事實與長期事實
有兩種事實會判斷提示到規則引擎的工作記憶體 – 一為短期事實，另一為長期事實。  
  
## <a name="short-term-facts"></a>短期事實  
 短期事實是規則引擎的單一執行循環所特有的。 短期事實會在原則執行之後自動從規則引擎的工作記憶體中撤回。 如果原則的資料在規則引擎的執行循環之間有所變更，則可以將該資料當做短期事實提交至規則引擎。  
  
 短期事實的範例：  
  
-   做為參數提交的事實**Policy.Execute**方法。  
  
-   做為參數提交的事實**呼叫規則**圖形。  
  
-   從使用規則動作提交的事實**Assert**函式。  
  
## <a name="long-term-facts"></a>長期事實  
 長期事實會載入至規則引擎的工作記憶體中，供任意數目的執行循環使用。 一般而言，長期事實是變更緩慢的事實，一般不會在原則的執行作業之間變更。 例如，您可能只想建立一次資料庫連線，然後使用同一個資料庫連線來執行原則數次。 短期事實和長期事實唯一真正的差異在於實作。  
  
 若要將事實當做長期事實提交，需要執行下列步驟：  
  
1.  建立實作事實擷取器元件**IFactRetriever**介面。 建立和判斷提示至規則的工作記憶體的事實引擎**UpdateFacts**會叫用方法的第一個時間和更新事實時必要的後續引動過程上**UpdateFacts**方法。  
  
2.  使用商務規則編輯器將原則設定為使用事實擷取器。  
  
 如需建立事實擷取器並使用它在原則中的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。  
  
## <a name="see-also"></a>另請參閱  
 [事實](../core/facts.md)