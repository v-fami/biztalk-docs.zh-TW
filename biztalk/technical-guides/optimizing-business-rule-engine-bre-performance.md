---
title: "商務規則引擎 (BRE) 效能最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c271b059-174d-4e8b-88b5-c3f408a97f1f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14c3adf32ac06d80c1aab8f870d82156470097a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-business-rule-engine-bre-performance"></a>商務規則引擎 (BRE) 效能最佳化
BizTalk Server 解決方案中實作商務規則引擎 (BRE) 時，應該考慮下列因素：  
  
## <a name="fact-types"></a>事實類型  
 規則引擎存取.NET 事實的時間比較所需的存取 XML 和資料庫事實會較少的時間。 如果您選擇在原則中使用.NET 或 XML 或資料庫事實，您應該考慮使用.NET 事實，以改善效能。  
  
## <a name="data-table-vs-data-connection"></a>資料表與資料連接  
 當資料集的大小很小 （< 10 左右）， **TypedDataTable**繫結會提供更佳的效能比**DataConnection**繫結。 不過， **DataConnection**繫結的執行效能比**TypedDataTable**繫結時的資料集很大 （大於或等於 10 個資料列大約）。 因此，您應該決定是否要使用**DataConnection**繫結或**TypedDataTable**繫結會根據資料集的估計大小。  
  
## <a name="fact-retrievers"></a>事實擷取器  
 事實擷取器實作通常會用來提供長期和緩時變更的事實到規則引擎執行原則之前的標準方法。 此引擎會快取這些事實，並透過多個執行循環來使用這些事實。 而非提交靜態或相當靜態事實每次叫用規則引擎，您應該建立事實擷取器的第一次，提交事實，然後更新 只在必要時，記憶體中的事實。  
  
## <a name="rule-priority"></a>規則優先順序  
 優先順序設定規則的任一端的範圍可以**0**，數目越大則優先順序愈高。 從最高的優先順序到最低優先順序的順序會執行動作。 當原則正向鏈結行為會藉由實作使用**Assert/Update**呼叫，鏈結 可最佳化使用的優先權設定。 例如，假設**Rule2**具有相依性所設定的值**Rule1**。 提供**Rule1**較高的優先順序表示**Rule2**之後不會只執行**Rule1**引發及更新的值。 相反地，如果**Rule2**已提供更高的優先權，它無法引發一次，並再一次之後，會引發**Rule1**引發及更新事實的**Rule2**使用的條件。 雖然這可能會提供正確的結果，讓**Rule1**較高的優先順序，在此案例中會提供更佳的效能。  
  
## <a name="update-calls"></a>Update 呼叫  
 Update 函式會導致重新評估使用更新的事實的所有規則。 更新函式呼叫可以是高度耗費資源，尤其是更新事實時，會重新評估規則的大型集合。 有很多情況下可以避免發生這種行為。 例如，假設下列規則。  
  
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
  
 原則使用的所有其餘規則**StatusObj.Flag**在其條件中。 因此，當**更新**上呼叫**StatusObj**物件，將會重新評估所有規則。 任何值**量**欄位時，所有規則都**Rule1**或**Rule2**會評估兩次，一次之前**更新**呼叫和一次之後**更新**呼叫。  
  
 若要減輕相關聯額外負荷，您可以設定的值**旗標**欄位設為**false**再叫用原則，然後使用僅**Rule1**中的原則設定的旗標. 在此情況下，**更新**，才會呼叫的值**量**欄位值大於 5，而**更新**如果不呼叫函式的值**數量**小於或等於 5。 因此，所有的規則都**Rule1**或**Rule2**會評估兩次才值**量**欄位值大於 5。  
  
## <a name="usage-of-logical-or-operators"></a>邏輯 OR 運算子的使用方式  
 在條件中使用的邏輯 OR 運算子會建立其他的排列，以擴充規則引擎的分析網路。 從效能觀點來看，您最好是將條件分割成不包含邏輯 OR 運算子的不可部分完成規則。  
  
## <a name="caching-settings"></a>快取設定  
 規則引擎會使用兩個快取。 更新服務會使用第一個和第二個由每個 BizTalk 處理序。 第一次使用原則時，BizTalk 處理序會從更新服務要求的原則資訊。 更新服務會從規則引擎資料庫擷取原則資訊、 快取和將資訊傳回給 BizTalk 處理序。 BizTalk 處理序建立根據該資訊的原則物件，並將 [原則] 物件儲存在快取中，相關聯的規則引擎執行個體完成執行原則時。 當再次叫用相同的原則時，BizTalk 處理序重複使用 [原則] 物件從快取，如果有的話。 同樣地，如果 BizTalk 處理序從更新服務要求原則的相關資訊，請更新服務會尋找其快取中的原則資訊是否可用。 每隔 60 秒，更新服務也會檢查是否有任何更新資料庫中的原則。 如果有任何更新，更新服務擷取的資訊，並快取更新的資訊。  
  
 有三個調整參數，與這些快取相關的規則引擎： **CacheEntries**， **CacheTimeout**，和**PollingInterval**。 您可以在登錄或組態檔中，為這些參數指定值。 值**CacheEntries**參數是快取中的項目數目上限，並且預設設定為 32 的值。 您可能想要增加的值**CacheEntries**參數，在某些情況下改善效能。 例如，假設您使用 40 個原則重複。您可以增加值的**CacheEntries**參數到 40，以改善效能。 這樣可讓更新服務維持的最多 40 個原則在記憶體中的快取詳細資料。  
  
 值**CacheTimeout**是以秒為單位的一個項目會保存在更新服務快取中的時間。 換句話說， **CacheTimeout**值指的是時間的快取的原則會維護快取中，而不被參考。 預設值**CacheTimeout**參數為 3600 秒或 1 小時。 這表示如果在一小時內未參考快取項目，會刪除項目。 在某些情況下，可能會增加的值有幫助**CacheTimeout**參數，以改善效能。 例如，如果原則會叫用每隔兩小時，原則執行的效能會改善藉由增加**CacheTimeout**高於兩小時的值的參數。  
  
 **PollingInterval**規則引擎的參數定義的時間，以秒為單位的更新服務檢查規則引擎資料庫更新。 預設值為**PollingInterval**參數為 60 秒。 如果您知道原則根本沒有未取得更新，或很少會更新，您可以變更此參數為較高的值，以改善效能。  
  
## <a name="sideeffects-property"></a>SideEffects 屬性  
 **ClassMemberBinding**， **Xmldocumentfieldbinding**，和**XmlDocumentFieldBinding**類別有一個名為屬性**SideEffects**. 這個屬性可決定是否會快取繫結欄位、成員或資料行的值。 預設值**SideEffects**屬性**Xmldocumentfieldbinding**和**XmlDocumentFieldBinding**類別**false**. 預設值**SideEffects**屬性**ClassMemberBinding**類別是**true**。 因此，當第二次以後在原則中存取 XML 文件的欄位或資料庫資料表的資料行時，則會從快取中擷取其值。 但是，當第二次以後存取 .NET 物件的成員時，就會從此 .NET 物件擷取該值，而不是從快取中擷取。 設定**SideEffects** .NET 屬性**ClassMemberBinding**至**false**會改善效能，因為從快取中擷取欄位的值第二次以後。 您只能透過程式設計的方式進行這項處理。 「 商務規則編輯器 」 工具不會公開**SideEffects**屬性。  
  
## <a name="instances-and-selectivity"></a>執行個體與選擇性  
 **XmlDocumentBinding**， **ClassBinding**，和**DatabaseBinding**類別有兩個屬性：**執行個體**和**選擇性**。 執行個體的值是預期的工作記憶體中類別的執行個體數目。 值**選擇性**是將會成功通過規則條件的類別執行個體的百分比。 規則引擎會使用這些值來最佳化條件評估，以便先在條件評估中使用可能的最少執行個體，然後再使用剩餘的執行個體。 如果您事先知道物件的執行個體的數目，設定**執行個體**屬性設為該值將會提升效能。 同樣地，如果您事先知道這些物件通過條件的百分比，設定**選擇性**屬性設為該值將會提升效能。 您只能以程式設計方式設定這些參數的值。 「商務規則編輯器」工具不會公開這些參數。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能最佳化](../technical-guides/optimizing-biztalk-server-performance.md)