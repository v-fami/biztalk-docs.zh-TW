---
title: 使用 DataConnection 時的考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Business Rules Engine, DataConnection tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], DataConnection
ms.assetid: 1b4c8aa5-053f-43d7-9f5f-050383405fed
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f99110daafa74cb16b6cc5b98e1382049bbb158
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22238950"
---
# <a name="considerations-when-using-dataconnection"></a>使用 DataConnection 時的考量
使用 DataConnection 與商務規則引擎時請考量以下幾點。  
  
## <a name="use-primary-keys"></a>使用主索引鍵  
 有主索引鍵時，兩個資料列的相等性是由資料列是否具有相同的主索引鍵，而非物件的比較而決定。 若資料列判定為相同，則記憶體中僅會保留一個複本，並釋出另一個。 如此可耗用較少的記憶體。  
  
 當 **DataConnection** 判斷提示至規則引擎第一次，引擎一律試圖找出它的結構描述從其主索引鍵資訊。 若是有主索引鍵，即會擷取主索引鍵資訊，然後用於所有後續的評估。  
  
> [!NOTE]
>  若是需要變更資料庫，則主索引鍵為必要項目。  
  
## <a name="provide-a-running-transaction-to-the-dataconnection-whenever-possible"></a>若是情況許可，儘可能為 DataConnection 提供執行中交易  
 不使用交易，每個查詢和更新 **DataConnection** 初始化它自己的本機交易，而不同的查詢可能傳回不同結果的規則評估的不同部分中。 若是基礎資料庫資料表中有所變更，使用者可能會發現處理不一致的情形。  
  
 雖然您可以使用 **DataConnection** 但沒有提供交易，資料表不會隨著時間變更時，建議使用的交易時，即使 **DataConnection** 只能用於讀取作業。  
  
 不過，更新資料時應該永遠會使用交易。  
  
## <a name="number-of-queries-may-grow-linearly"></a>查詢數目可能呈線性增加  
 對做為查詢 **DataConnection** 其他聯結的物件，針對執行的查詢數目會參數化 **DataConnection** 直接對應至聯結到達的物件數 **DataConnection**。 因此，如果的聯結物件數到達 **DataConnection** 物件呈線性增加，針對查詢數目 **DataConnection** 會成長以線性方式以及。 目前並沒有減少查詢數的最佳化方法。  
  
 此範例為規則：  
  
```  
IF A.x = 7 AND DC.y = A.y  
THEN  
```  
  
 代表 **ObjectBinding**, ，DC 代表 **DataConnection**, ，而 x 和 y 代表屬性的 A 和 DC。  
  
 通過測試的每個執行個體 (x = 7)，查詢會產生使用 **DataConnection**。 若是有許多相符的執行個體，會產生相同的查詢數。  
  
## <a name="use-or-conditions-with-caution"></a>小心使用 OR 條件  
 如果規則僅使用連結 (**AND**) 條件、 測試及查詢將會執行儘早，所以會減少傳遞之物件的執行個體。 如此一來，針對後續的查詢數目 **DataConnection** 會按比例縮小。 如果分離 (**或者**) 條件和 **DataConnection** 在規則中，所有條件的評估會被傳送至最終查詢一起使用。 如果多個 **DataConnection** 用在規則中，除了最後一個會有效地變成 SELECT-ALL 查詢陳述式的所有查詢。  
  
 一般而言，最好是將具有 OR 條件的規則分割為兩個或多個不連續規則，因為與多個不可部分完成的規則定義相較，使用 OR 條件的話將會降低效能。 無論是否使用 DataConnections 都會發生這種情形。  
  
 您也可以考慮使用不同的規則，只包含連結的條件，而不是使用一個規則 **或者** 條件。 使用 **或者** 條件，所有聯結物件之執行個體的倍數速度增加查詢的次數。 下列範例會顯示這一點。  
  
```  
IF (A.x ==7 OR A.x == 8) AND DC.y == A.y  
THEN DC.z = 10  
```  
  
 在此範例中，A 代表 **ObjectBinding**;DC 代表 **DataConnection**, ，和 x、 y 和 z 表示屬性的 A 和 DC。 如果 A 有 100 個執行個體，且 x 是 1 中的第一個物件中的第二個物件，到 100，100 物件中，第 2 100 個查詢都必須對執行 **DataConnection**。  
  
 最好是重寫前述規則，將它分割為兩個規則。  
  
 **規則 1**  
  
```  
IF A.x =7 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
 **規則 2**  
  
```  
IF A.x = 8 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
## <a name="sql-does-not-support-some-predicates-and-functions"></a>SQL 不支援某些述詞和函式  
 某些規則引擎支援的述詞和函式，SQL 是不支援的。 若在規則條件中使用這些不支援的述詞和函式，就無法併入查詢中。 下列詞彙無法最佳化為 SQL 查詢：  
  
-   某些引擎內建函式在 SQL 查詢中沒有相等函式。 這些是 **電源**, ，**FindFirst**, ，和 **FindAll**。 使用 **DataConnection** 當做其中一個或多個其引數的資料行不能最佳化為查詢的一部分; 例如，Power (2，dc。資料行 1)。  
  
-   內建述詞 Match 使用 **DataConnection** 資料行做為規則運算式引數 （第一個引數）。 例如，Match("abc*", dc1.Column2) 是有效的，但是 Match(dc1.Column1, dc1.Column2) 則是無法轉譯的。  
  
-   使用使用者函式具有 **DataConnection** 資料行做為其中一個參數。 例如，c1.M(dc.Column1) 無法最佳化，因為無法在資料庫伺服器上執行使用者函式，必須由商務規則引擎來執行。  
  
-   表示設定作業的使用者函式 **DataConnection**; 例如，dc。Column1(5)。  
  
-   函式會使用該 **ObjectReference** 至 **DataConnection**; 例如，objecref （dc）。  
  
-   若是一或多個函式引數是無法轉譯的，函式呼叫也會變成無法轉譯；例如，Add(c1.M(dc.Column1), 5)。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎中的資料存取](../core/data-access-in-the-business-rule-engine.md)