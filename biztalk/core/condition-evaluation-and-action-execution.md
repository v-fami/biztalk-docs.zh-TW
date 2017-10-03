---
title: "條件評估與動作執行 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Action stage [Business Rules Engine]
- examples, business rules
- Business Rules Engine, policies
- Match stage [Business Rules Engine]
- business rules, examples
- Business Rules Engine, algorithm
- Business Rules Engine, examples
- conflict resolution [Business Rules Engine]
- Business Rules Engine, stages
ms.assetid: dcaa32c2-3403-4f54-92e2-128686bfc193
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2814a97c1907b1bb29eee2a718d04d14cfe901a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="condition-evaluation-and-action-execution"></a>條件評估與動作執行
「商務規則架構」提供高效率的推斷引擎，可將規則連結至 .NET 物件、XML 文件或是資料庫資料表。  
  
 「商務規則引擎」使用三階段的演算法以執行原則。 這些階段如下所示：  
  
-   **比對**。 在比對階段，會使用規則條件中定義的述詞，針對使用事實類型 (物件參考由規則引擎的工作記憶體維護) 的述詞比對事實。 基於效率的緣故，模式比對會在原則中的所有規則上執行，而不同規則之間共用的條件則只會比對一次。 有可能會將部分條件比對儲存在工作記憶體中，以加速後續的模式比對作業。 模式比對階段的輸出是由對規則引擎議程的更新所組成。  
  
-   **衝突解決**。 在衝突解決階段中，會檢查候選執行的規則，以根據預先決定的解決配置來決定下一組要執行的規則動作。 在比對階段找到的所有候選規則都會加入規則引擎的議程中。  
  
     預設的衝突解決配置是根據原則中的規則優先順序。 優先順序是在「商務規則編輯器」中可設定的規則屬性。 數目愈大，優先順序就愈高，因此若觸發多個規則，就會先執行較高優先順序的動作。  
  
-   **動作**。 在動作階段，會執行已解析規則中的動作。 請注意，規則動作可判斷提示新事實到規則引擎，這會造成週期繼續。 這也稱為正向鏈結。 請務必注意，演算法永遠無法比目前執行的規則先執行。 在重複比對階段之前，將會先執行目前引發的規則之所有動作。 不過，在比對階段再次開始之前，將不會引發在議程上的其他規則。 比對階段可能造成在引發議程上的規則之前，從議程移除它們。  
  
 下列範例顯示比對衝突解析動作的三階段演算法。  
  
 **規則 1： 評估收入**  
  
-   宣告式表示法：  
  
     只有在申請者的收入對貸款的比率小於 0.2 時，才取得申請者的信用等級。  
  
-   使用商務物件的 IF—THEN 表示法：  
  
    ```  
    IF Application.Income / Property.Price < 0.2    
    THEN Assert new CreditRating( Application)   
    ```  
  
 **規則 2： 評估信用等級**  
  
-   宣告式表示法：  
  
     只有當申請者的信用等級大於 725 時才核准申請者。  
  
-   使用商務物件的 IF—THEN 表示法：  
  
    ```  
    IF Application.SSN = CreditRating.SSN AND CreditRating.Value > 725    
    THEN SendApprovalLetter(Application)    
    ```  
  
 下表摘要這些事實。  
  
|事實|欄位|  
|----------|------------|  
|Application – 代表房屋貸款申請的 XML 文件|-收入 = $65,000<br />SSN = XXX XX XXXX|  
|Property – 代表購買的財產之 XML 文件|-Price = $225,000|  
|CreditRating – 包含貸款申請者信用等級的 XML 文件|的值 = 0 – 800<br />SSN = XXX XX XXXX|  
  
 在一開始時，規則引擎工作記憶體與議程是空的。 在應用程式新增 Application 與 Property 事實之後，規則引擎工作記憶體與議程就會更新如下。  
  
|工作記憶體|議程|  
|--------------------|------------|  
|應用程式<br />屬性|規則 1|  
  
 規則 1 加入議程，因為其條件 (Application.Income / Property.Price < 0.2) 評估為**true**在比對階段。 在工作記憶體中沒有 CreditRating 事實，因此不會評估規則 2 的條件。 因為在議程中的唯一規則為規則 1，所以會執行該規則，然後從議程消失。 為規則 1 定義的單一動件會使得新事實 (申請者的 CreditRating 文件) 加入工作記憶體。 在完成執行規則 1 之後，控制會返回比對階段。 因為唯一要比對的新物件是 CreditRating 事實，所以比對階段的結果如下：  
  
|工作記憶體|議程|  
|--------------------|------------|  
|應用程式<br />屬性<br />-CreditRating|規則 2|  
  
 在執行規則 2 時，會造成叫用傳送核准信件給申請者的函式。 在完成規則 2 之後，正向鏈結演算法的執行會返回比對階段。 因為已經沒有要比對的新事實，而且議程是空的，所以正向鏈結會終止並且會完成執行原則。  
  
## <a name="see-also"></a>另請參閱  
 [規則引擎](../core/rule-engine.md)