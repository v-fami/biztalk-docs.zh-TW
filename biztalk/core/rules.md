---
title: 規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, actions
- Business Rules Engine, business rules
- business rules, about business rules
- business rules, conditions
- business rules, facts
- business rules
ms.assetid: b288dd07-33f1-42fe-bbfb-02674ef3b3ca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35f398cf98181d17833be79fbe9d282e8515e052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268774"
---
# <a name="rules"></a>規則
商務規則是控管商務程序進行的宣告陳述式。 規則是由條件與動作組成。 評估條件時，如果其評估結果為**true**，規則引擎就會初始一或多個動作。  
  
 商務規則架構中的規則會使用下列格式來定義：  
  
 如果`condition`然後`action`  
  
 請設想下列範例：  
  
 IF amount is less than or equal to available funds  
  
 THEN conduct transaction and print receipt  
  
 這個規則會將商務邏輯 (以比較兩個貨幣值的形式) 套用到資料或事實 (以交易數量與可用資金的形式)，以判斷是否要進行交易。  
  
 您可使用「商務規則編輯器」來建立、修改、訂定版本及部署商務規則。 或者，您可以透過程式設計方式來執行前面的工作。  
  
## <a name="conditions"></a>條件  
 條件就是一個 True/False (布林值) 運算式，其中包含一或多個套用到事實的述詞。  
  
 在本例中，則述詞**小於或等於**套用到事實**量**和**可用資金**。 此條件將一律評估為**true**或**false**。  
  
 述詞可以與邏輯運算子結合**AND**，**或者**，和**不**邏輯運算式可能很大，但將一律評估為表單任一**true**或**false**。  
  
## <a name="actions"></a>動作  
 動作是條件評估的功能結果。 若符合某規則條件，就會初始對應的一個或多個動作。  
  
 在我們的範例中，"conduct transaction" 及 "print receipt" 就是在條件 (在此案例中就是 "IF amount is less than or equal to available funds") 為 True 時會執行的動作，而且也只有在此時才會執行。  
  
 而商務規則架構中的動作，是藉由呼叫方法或設定物件上的屬性，或是在 XML 文件或資料庫資料表上執行設定作業來表現。  
  
## <a name="facts"></a>事實  
 事實就是規則運作依據的資料。 在我們的範例中 "amount" 及 "available funds" 就是事實。 如需詳細資訊，請參閱[事實](../core/facts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立原則和規則](../core/how-to-create-policies-and-rules.md)