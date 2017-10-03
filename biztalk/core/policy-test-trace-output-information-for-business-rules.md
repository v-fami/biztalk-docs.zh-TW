---
title: "商務規則的原則測試追蹤輸出資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, business rules
- testing, policies
- business rules, testing
- policies, testing
ms.assetid: 26ff584e-97a1-4d76-a8a9-a55b4c99231f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c223e8bddae1ff68e77cdf881ea22e6be4cdab9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-information-for-business-rules"></a>商務規則的原則測試追蹤輸出資訊
本節提供在「商務規則編輯器」中測試原則時所顯示的追蹤資訊之相關資訊。 檢視使用 [群組中樞] 頁面上追蹤查詢的訊息事件和服務執行個體的原則執行的追蹤結果時，會看到非常類似的資訊。  
  
 追蹤輸出會顯示下列四種陳述式類型：  
  
-   事實活動  
  
-   條件評估  
  
-   議程更新  
  
-   規則被引發  
  
 下面內容將介紹每種陳述式類型。  
  
## <a name="fact-activity"></a>事實活動  
 這個陳述式指示引擎的工作記憶體中的事實變更。 以下為事實活動項目的範例：  
  
```  
FACT ACTIVITY 3/16/2004 9:50:28 AM  
Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
Ruleset Name: LoanProcessing  
Operation: Assert  
Object Type: MyTest.test  
Object Instance Identifier: 872  
```  
  
### <a name="rule-engine-instance-identifier"></a>規則引擎執行個體識別項  
 唯一識別項**RuleEngine**提供規則引發的執行環境的執行個體。  
  
### <a name="ruleset-name"></a>規則集名稱  
 規則集 (原則) 的名稱。  
  
### <a name="operation"></a>作業  
 事實活動可能會進行以下三種作業：  
  
 判斷提示  
  
 事實加入工作記憶體。  
  
 Update  
  
 事實由規則更新，然後需要重新判斷提示，根據新的日期和狀態在引擎重新評估。  
  
 撤回  
  
 事實從工作記憶體移除。  
  
> [!NOTE]
>  若事實經判斷提示其類型不符合原則中所使用的任何一種類型，「判斷提示」作業將會顯示 [判斷提示 - 事實無法辨識]。  
  
### <a name="object-type"></a>物件類型  
 特定活動的事實類型：  
  
-   DataConnection  
  
-   TypedDataTable  
  
-   TypedDataRow  
  
     若判斷提示 TypedDataTable，其中包含的所有資料列都會判斷提示為 TypedDataRow。  與 DataConnection 關聯的 TypedDataRow 必須等到條件經過評估，而且結果查詢已經執行之後，才會進行判斷提示。  
  
-   TypedXmlDocument  
  
     父系和子系的 TypedXmlDocument 執行個體都可以檢視判斷提示。  
  
### <a name="object-instance-identifier"></a>物件執行個體識別項  
 事實參考的唯一執行個體識別碼。  
  
## <a name="condition-evaluation"></a>條件評估  
 這項活動指示個別述詞的評估結果。 以下為條件評估項目的範例：  
  
```  
CONDITION EVALUATION TEST (MATCH) 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:Root.EmploymentType/TimeInMonths >= 18  
Left Operand Value: 31  
Right Operand Value: 18  
Test Result: True  
```  
  
 以下內容將描述上述範例提到的一些詞彙：  
  
-   **測試運算式。** 規則中的簡單 (一元或二元) 運算式。  
  
-   **左的運算元的值。** 位於運算式左邊的詞彙值。  
  
-   **右運算元值。** 位於運算式右邊的詞彙值。  
  
-   **測試結果。** 評估的結果，結果可為 True 或 False。  
  
## <a name="agenda-update"></a>議程更新  
 這項活動指示已加入規則引擎議程以便後續執行的規則。 以下為議程更新項目的範例：  
  
```  
AGENDA UPDATE 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Operation: Add  
Rule Name: Employment Status Rule  
Conflict Resolution Criteria: 0  
```  
  
 以下內容將描述上述範例提到的一些詞彙：  
  
-   **作業。** 規則可以新增到議程或是從中移除。  
  
-   **規則名稱。** 將要新增到議程的規則名稱。  
  
-   **衝突解決準則。** 規則的優先順序，決定執行動作的相對順序 (較高優先順序的動作會優先執行)。  
  
## <a name="rule-fired"></a>規則被引發  
 這項活動指示規則動作的執行。 以下為規則被引發項目的範例：  
  
```  
RULE FIRED 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Rule Name: Residency Status Rule  
Conflict Resolution Criteria: 10  
```