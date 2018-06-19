---
title: Update1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Update function [Business Rules Engine]
- Update function [Business Rules Engine], TypedXMLDocument
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], .NET objects
- .NET objects
- Update function [Business Rules Engine], DataConnection
ms.assetid: 939e45dc-6433-42f3-a336-8f3c247417ac
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a4ea10e72be2a39eedaafa0e00c8f8ac630393b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288398"
---
# <a name="update"></a>Update
當**更新**函式會叫用物件，該物件會判斷提示引擎重新進行評估，根據新資料和狀態。 物件可以是類型**TypedXmlDocument**或.NET 類別或**DataConnection**或**TypedDataTable**。  
  
 您也可以使用**更新**函式改善引擎效能和避免無止盡迴圈實例，本主題中所述。  
  
 通常，您會使用**Assert**規則引擎工作記憶體中放置新物件，並使用**更新**無法更新工作記憶體中的現有物件。 當您判斷提示新物件時，所有規則中的條件都會受到評估。 當您更新現有物件時，只有用到已更新事實的條件會受到重新評估，而這些條件若評估為 true，即會在議程中新增動作。  
  
## <a name="using-update-function-on-net-facts"></a>在 .NET 事實上使用 Update 函式  
 以下兩個規則為範例。 假設物件**ItemA**和**ItemB**存在於工作記憶體。 規則 1 會評估**識別碼**屬性**ItemA**，設定**識別碼**屬性**ItemB**，然後重新判斷提示和**ItemB**變更之後。 當**ItemB**重新判斷提示，它會被視為新的物件和引擎重新評估使用物件的所有規則**ItemB**中述詞或動作。 這可確保 「 規則 2 」 的新值重新評估**ItemB.Id**，規則 1 中所設定。 規則 2 可能無法在第一次它已評估，但評估為**true**第二次評估時。  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Assert(ItemB)  
```  
  
### <a name="rule-2"></a>規則 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 這種在工作記憶體中重新判斷提示的能力，可讓使用者明確控制正向鏈結實例中的行為。 不過，此範例中重新判斷提示的副作用是「規則 1」也會重新評估。 因為**ItemA.Id**未變更，規則 1 再次評估為**true**和**assert （itemb)** 的動作引發一次。 其結果是，規則建立了無止盡迴圈的狀況。  
  
> [!NOTE]
>  重新評估規則的預設最大迴圈計數為 2 ^32。 對於特定規則，原則執行可以持續很長的時間。 您可以藉由調整減少計數**最大執行迴圈深度**原則版本的屬性。  
  
 您必須能夠重新判斷提示物件，而不需要建立無止盡的迴圈，而**更新**函式提供這項功能。 要重新判斷提示一樣，**更新**函式會執行**Retract**和**Assert**相關聯的物件執行個體，其中已從規則動作，但有兩個主要差異：  
  
-   執行個體類型僅用於動作 (而非述詞) 的規則之議程上的動作，將保留在議程上。  
  
-   在動作中僅使用執行個體類型的規則將不會重新評估。  
  
 因此，僅在述詞或在述詞與動作兩者中使用執行個體類型的規則將會重新評估，而其動作會適當地加入到議程。  
  
 若要使用上述範例變更**更新**函式可確保只有 「 規則 2 會重新評估，因為**ItemB**用於規則 2 的條件。 規則 1 則不會受到因為**ItemB**僅用於動作的規則 1，消除了迴圈實例。  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Update(ItemB)  
```  
  
### <a name="rule-2"></a>規則 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 不過，仍然可能建立迴圈實例。 例如，考慮下列規則。  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF ItemA.Id == 1  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 因為**ItemA**用在述詞中，它會重新評估時**更新**上呼叫**ItemA**。 如果值**ItemA.Id**不會變更其他地方，規則 1 」 會持續評估為**true**，因而導致**更新**A.上再次呼叫規則設計工具，必須確定不會建立這類的迴圈實例。  
  
 適用於此的適當方式將依據規則本質而有所差異。 以下是解決上述範例中之問題的簡單機制。  
  
 **更新**函式可用於商務規則編輯器的類別，參考如同**Assert**， **Retract**，或**RetractByType**函式。  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF ItemA.Id == 1 and ItemA.Value != 20  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 上加入檢查**ItemA.Value**防止評估規則 1 **true**再次之後第一次執行規則 1 的動作。  
  
## <a name="using-update-function-on-xml-facts"></a>在 XML 事實上使用 Update 函式  
 以下兩個規則為範例。 假設： 「規則 1」會評估訂單訊息中的項目總數，而「規則 2」會在總數大於或等於 10 時，將狀態設定為「需要核准」。  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count)  
```  
  
### <a name="rule-2"></a>規則 2  
  
```  
IF ProcessPO.Order:/Order/Items/TotalCount >= 10  
THEN ProcessPO.Order:/Order/Status = "Needs approval"  
```  
  
 如果您將下列訂單 (PO) 訊息傳遞做為輸入，請為此原則時，您注意到的狀態未設定為 「 需要核准 」 即使總項目計數為 14。 這是因為 rule2 會評估只會在開始時的值**TotalCount**欄位為 0，而且此規則不會評估每次可用總數更新時。 若要將條件重新評估每次**TotalCount**會更新，您需要呼叫**更新**父節點上的函式 (**項目**) 的已修改的節點 (**TotalCount**)。 如果您如下文所示變更「規則 1」，然後再測試一次，您應會看見 [狀態] 欄位的值設定為「需要核准」。  
  
```  
<ns0:Order xmlns:ns0="http://ProcessPO.Order">  
    <Items>  
        <Item>  
            <Id>ITM1</Id>  
            <Count>2</Count>  
        </Item>  
        <Item>  
            <Id>ITM2</Id>  
            <Count>5</Count>  
        </Item>  
        <Item>  
            <Id>ITM3</Id>  
            <Count>7</Count>  
        </Item>  
        <TotalCount>0</TotalCount>  
    </Items>  
    <Status>No approval needed</Status>  
</ns0:Order>  
```  
  
 修改**規則 1**如下所示：  
  
### <a name="rule-1"></a>規則 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count) AND  
Update(ProcessPO.Order:/Order/Items)  
```  
  
## <a name="using-update-function-on-database-facts"></a>在 資料庫事實上使用 Update 函式  
  
### <a name="typeddatatable"></a>TypedDataTable  
 如果**更新**上呼叫**TypedDataTable**，**更新**上所有相關聯的引擎會呼叫**TypedDataRows**。 **更新**也稱為個別**TypedDataRows**。  
  
### <a name="dataconnection"></a>DataConnection  
 更新的**DataConnection**不支援。 使用**Assert**改為。  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)