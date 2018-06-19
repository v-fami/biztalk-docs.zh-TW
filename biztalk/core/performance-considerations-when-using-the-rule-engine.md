---
title: 使用規則引擎時的效能考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e9020c2-5152-40f6-940b-d4ce4081f069
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24a1c6ffb278d257e16c192e5fc7d827df70e24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266502"
---
# <a name="performance-considerations-when-using-the-rule-engine"></a>使用規則引擎時的效能考量
本主題討論規則引擎如何在各種情況下執行，以及使用各種不同的組態/調整參數值來執行。  
  
## <a name="fact-types"></a>事實類型  
 規則引擎存取 .NET 事實所需的時間，少於存取 XML 和資料庫事實所需的時間。 如果您可選擇在原則中使用 .NET、XML 或資料庫事實，您應該考慮使用 .NET 事實，以取得更好的效能。  
  
## <a name="data-table-vs-data-connection-binding"></a>資料表與。資料連接繫結  
 當資料集的大小很小 （少於約 10 個資料列） **TypedDataTable**繫結的執行效能比**DataConnection**繫結。 當資料集很大 （大於或等於約 10 個資料列） **DataConnection**繫結的執行效能比**TypedDataTable**繫結。 因此，您應該決定是否要使用**DataConnection**繫結或**TypedDataTable**繫結會根據資料集的估計大小。  
  
## <a name="fact-retrievers"></a>事實擷取器  
 您可以撰寫事實擷取器，它是實作標準方法的物件，而且通常會在執行原則之前，使用這些方法將長期與緩慢變化的事實提供給規則引擎。 此引擎會快取這些事實，並透過多個執行循環來使用這些事實。 您應該在第一次叫用規則引擎時建立事實擷取器來提交事實，然後只有在需要時才更新記憶體中的事實，而不要在每次叫用規則引擎時都提交靜態或相當靜態的事實。  
  
## <a name="rule-priority"></a>規則優先順序  
 優先順序設定規則的任一端的範圍可以**0**，數目越大則優先順序愈高。 會依照最高優先順序到最低優先順序的順序來執行動作。 當原則正向鏈結行為會藉由實作使用**Assert/Update**呼叫，鏈結 可最佳化使用的優先權設定。 例如，假設**Rule2**具有相依性由所設定的值**Rule1**。 提供**Rule1**較高的優先順序表示**Rule2**之後才會執行**Rule1**引發及更新的值。 相反地，如果**Rule2**會提供更高的優先權，它可以引發一次，並再一次之後，會引發**Rule1**引發及更新事實的**Rule2**條件中使用。 這樣不一定會產生正確的結果，但清楚的一點是，引發兩次與只引發一次相較之下，會有效能上的影響。  
  
## <a name="update-calls"></a>Update 呼叫  
 **更新**函式會更新事實的規則引擎工作記憶體中存在，而且會導致重新評估在條件中使用已更新的事實的所有規則。 **更新**函式呼叫可能會耗費資源，尤其是許多規則需要重新評估，因為更新事實。 有一些情況可避免必須重新評估規則， 例如，假設下列規則：  
  
 **Rule1:**  
  
```  
IF PurchaseOrder.Amount > 5   
THEN StatusObj.Flag = true; Update(StatusObj)  
```  
  
 **Rule2:**  
  
```  
IF PurchaseOrder.Amount <= 5   
THEN StatusObj.Flag = false; Update(StatusObj)  
```  
  
 原則使用的所有其餘規則**StatusObj.Flag**在其條件中。 因此，當**更新**上呼叫**StatusObj**物件，將會重新評估所有規則。 任何值**量**欄位時，所有的規則都**Rule1**和**Rule2**會評估兩次，一次之前**更新**呼叫和之後的一次**更新**呼叫。  
  
 相反地，您可以設定的值**旗標**欄位設為**false**叫用原則，則只使用之前**Rule1**中的原則設定的旗標。 在此情況下，**更新**才會呼叫的值**量**欄位值大於 5，和**更新**若數量小於或等於 5，不會呼叫。 因此，所有的規則都**Rule1**和**Rule2**會評估兩次才值**量**欄位值大於 5。  
  
## <a name="use-of-logical-or-operators"></a>使用邏輯 OR 運算子  
 規則引擎最適合用於執行邏輯**AND**運算子和其重新建構所剖析的規則中以 disjunctive normal form 因此的**或**只在最上層使用運算子。 使用遞增的邏輯**或**中條件運算子會建立其他的排列，以擴充規則引擎的分析網路，而且可能需要很長的時間來標準化此規則的規則引擎。 下列清單包含這個問題的可能因應措施。  
  
-   會修改規則，是以分離的一般形式因此**或**運算子是只在最上層。 請注意，在商務規則編輯器中以 Disjunctive Normal Form (DNF) 開發規則可能需要一些訣竅。 您可以考慮以程式設計方式建立規則。  
  
-   開發協助程式元件，以執行**或**作業會傳回布林值，並使用規則中的元件。  
  
-   考慮將規則分割為多個規則，讓下一個規則檢查上一個執行過的規則所設定的旗標，或使用上一個執行過的規則所判斷提示的物件，如下列範例所示：  
  
    -   規則 1： 如果 (= = 1 或 3 = =) 然後 b = true  
  
         規則 2： 如果 (b = = true) 然後...  
  
    -   規則 1： 如果 (= = 1 或 3 = =) 然後判斷提示 (新 c())  
  
         規則 2: IF (c.flag = = true) 然後...  
  
## <a name="caching-settings"></a>快取設定  
 規則引擎會使用兩個快取， 第一個是在更新服務中，第二個是在每一個 BizTalk 處理序中。 當第一次使用原則時，BizTalk 處理序會從更新服務要求原則資訊。 更新服務會從規則引擎資料庫擷取原則資訊、快取該資訊，並將該資訊傳回到 BizTalk 處理序。 BizTalk 處理序會根據該資訊來建立原則物件，並在關聯的規則引擎執行個體完成原則的執行時，將該原則物件儲存在快取中。 當再次叫用相同的原則時，如果快取中有可用的原則物件，則 BizTalk 處理序會重複使用快取中的原則物件。  
  
 同樣地，如果 BizTalk 處理序從更新服務要求與原則有關的資訊，則更新服務會先在快取中尋找原則資訊。 更新服務也會每隔 60 秒鐘 (1 分鐘) 檢查一次，看看資料庫中的原則是否有任何更新。 如果有任何更新，更新服務會擷取資訊，並快取更新的資訊。  
  
 有三個調整參數，與這些快取相關的規則引擎： **CacheEntries**， **CacheTimeout**，和**PollingInterval**。 您可以在登錄或組態檔中，為這些參數指定值。  
  
 值**CacheEntries**是快取中的項目數目上限。 預設值**CacheEntries**為 32。 您可能想要增加的值**CacheEntries**參數，在某些情況下改善效能。 例如，假設您重複使用 40 個原則， 在此情況下您可能想要增加的值**CacheEntries**到 40，以改善效能。 如此可讓更新服務在記憶體中快取多達 40 個原則的詳細資料， 也可讓 BizTalk 服務在記憶體中快取多達 40 個原則執行個體。 在 BizTalk 服務的快取中，可能會有一個以上的原則執行個體。  
  
 值**CacheTimeout**為項目超過更新服務快取的時間 （以秒為單位）。 換句話說， **CacheTimeout**值是指原則的快取項目保留多久快取中是否有任何參考。 預設值**CacheTimeout**為 3600 秒 （1 小時）。 這表示，如果在一個小時內未參考此快取項目，就會將它刪除。 在某些情況下，您可能想要增加**CacheTimeout**值來提升效能。 例如，假設每隔兩個小時叫用此原則一次， 增加的值即可改善效能的原則執行**CacheTimeout**參數大於兩個小時的值。  
  
 **PollingInterval**參數的規則引擎更新服務會檢查規則引擎資料庫更新的間隔 （秒） 定義的時間。 預設值為**PollingInterval**參數為 60 秒 （一分鐘）。 如果您知道原則根本不會更新或是很少更新，您可以增加這個值來提升效能。  
  
## <a name="sideeffects-property"></a>SideEffects 屬性  
 **ClassMemberBinding**， **Xmldocumentfieldbinding**，和**XmlDocumentFieldBinding**類別有一個名為屬性**SideEffects**. 這個屬性可決定是否會快取繫結欄位、成員或資料行的值。 預設值**SideEffects**屬性**Xmldocumentfieldbinding**和**XmlDocumentFieldBinding**類別**false**. 預設值**SideEffects**屬性**ClassMemberBinding**類別是**true**。 因此，當第二次以後在原則中存取 XML 文件的欄位或資料庫資料表的資料行時，則會從快取中擷取其值。 但是，當第二次以後存取 .NET 物件的成員時，就會從此 .NET 物件擷取該值，而不是從快取中擷取。 設定**SideEffects** .NET 屬性**ClassMemberBinding**至**false**會改善效能，因為從快取中擷取欄位的值第二次以後。 您只能透過程式設計的方式進行這項處理。 「 商務規則編輯器 」 工具不會公開**SideEffects**屬性。  
  
## <a name="instances-and-selectivity"></a>執行個體與選擇性  
 **XmlDocumentBinding**， **ClassBinding**，和**DatabaseBinding**類別有兩個屬性：**執行個體**和**選擇性**。 值**執行個體**是預期的工作記憶體中類別的執行個體數目。 值**選擇性**是將會成功通過規則條件的類別執行個體的百分比。 規則引擎會使用這些值來最佳化條件評估，以便先在條件評估中使用可能的最少執行個體，然後再使用剩餘的執行個體。 如果您事先知道物件的執行個體的數目，設定**執行個體**屬性設為該值將會提升效能。 同樣地，如果您事先知道這些物件通過條件的百分比，設定**選擇性**屬性設為該值將會提升效能。 您只能以程式設計方式設定這些參數的值。 「商務規則編輯器」工具不會公開這些參數。