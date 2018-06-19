---
title: 議程與優先順序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, executing
- Business Rules Engine, agendas
- Business Rules Engine, priorities
- business rules, priorities
- business rules, examples
- Business Rules Engine, examples
- examples, Business Rules Engine
- Business Rules Engine, rules
ms.assetid: ca54f750-4f2d-4734-8e6e-7af1b4967e6a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4529753251c2bf7934616b91662bde836c8339e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230206"
---
# <a name="agenda-and-priority"></a>議程與優先順序
若要了解商務規則引擎如何評估規則與執行動作，您必須了解的概念*議程*和*優先順序*。  
  
## <a name="agenda"></a>議程  
 議程是引擎用來佇列要執行的規則之排程。 引擎執行個體具有議程，並做為單一原則，而不是一系列的原則。 當事實判斷提示至工作記憶體，且符合指定規則的條件時，規則就會放置在議程中，並根據優先順序執行。 規則的動作會依照由上至下的順序來執行，接著再執行議程中下一個規則的動作。  
  
 屬於一個規則的動作會被視為一個區塊，如此可以在移到下一個規則之前先執行所有動作。 不論區塊中的其他動做為何，規則區塊中的所有動作都會執行。 如需判斷提示的詳細資訊，請參閱[引擎控制函式](../core/engine-control-functions.md)。  
  
 下列範例示範議程的運作方式。  
  
 **規則 1**  
  
```  
IF  
Fact1 == 1  
THEN  
Action1  
Action2  
```  
  
 **Rule2**  
  
```  
IF  
Fact1 > 0  
THEN  
Action3  
Action4  
```  
  
 將事實 Fact1 (其值為 1) 判斷提示至引擎。 因為同時符合 Rule1 與 Rule2 的條件，所以這兩個規則都會移到議程中以執行其動作。  
  
|工作記憶體|議程|  
|--------------------|------------|  
|Fact1 (value=1)|**規則 1**<br /><br /> -Action1<br />-Action2<br /><br /> **Rule2**<br /><br /> -Action3<br />-Action4|  
  
## <a name="priority"></a>優先權  
 要執行的優先順序會設定在每個個別規則上，而所有規則的預設優先順序均為 0。 優先順序的範圍可從 0 的任一邊開始，數目愈大則優先順序愈高。 會依照最高優先順序到最低優先順序的順序來執行動作。  
  
 下列範例顯示優先順序如何影響規則執行的順序。  
  
 **Rule1 (優先順序 = 0)**  
  
```  
IF  
Fact1 == 1  
THEN  
Discount = 10%  
```  
  
 **Rule2 (優先順序 = 10)**  
  
```  
IF  
Fact1 > 0  
THEN  
Discount = 15%  
```  
  
 已同時符合兩個規則的條件，但是會先執行 Rule2，因為它的優先順序比較高。 最終的折扣是 10%，因為它是為 Rule1 執行的動作之結果，如下表所示。  
  
|工作記憶體|議程|  
|--------------------|------------|  
|Fact1 (value=1)|**Rule2**<br /><br /> 折扣 = 15%<br /><br /> **規則 1**<br /><br /> Discount = 10%|  
  
## <a name="see-also"></a>另請參閱  
 [規則引擎](../core/rule-engine.md)