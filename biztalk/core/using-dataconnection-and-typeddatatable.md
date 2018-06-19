---
title: 使用 DataConnection 與 TypedDataTable |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Assert function [Business Rules Engine], TypedData table
- Business Rules Engine, DataConnection tips
- TypedData table
- Business Rules Engine, TypedData table tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], DataConnection
ms.assetid: e825803e-6626-4ddd-a77e-75a3ba2b74a4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b5a0a490023d77676cc5d156ad5126ad5d7d6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287542"
---
# <a name="using-dataconnection-and-typeddatatable"></a>使用 DataConnection 與 TypedDataTable
在許多情況下，使用**DataConnection**提供更佳的效能，並耗用較少的記憶體比使用**TypedDataTable**。 不過， **TypedDataTable**可能需要在某些情況下，因為使用的特定限制**DataConnection**。 在某些其他情況下，使用**TypedDataTable**可能會產生較佳的效能比使用**DataConnection**。 本主題描述您在選擇正確方法時應該考量的準則和因素。  
  
## <a name="when-to-use-typeddatatable-instead-of-dataconnection"></a>何時使用 TypedDataTable 而非 DataConnection  
 在下列情況下使用 TypedDataTable 代替 DataConnection：  
  
-   必須進行資料變更但資料表沒有主索引鍵。 藉由使用讓資料變更**DataConnection**，主索引鍵為必要。 因此，如果沒有主索引鍵， **TypedDataTable**是唯一可行的方法。  
  
    > [!NOTE]
    >  規則引擎只會更新記憶體中的值**TypedDataTable**。 由呼叫者決定這些變更是否為永久的。  
  
-   選擇性高時，即代表資料表中大部分的資料列都會通過規則條件所指定的測試。 在此情況下， **DataConnection**並未提供很多優點，它可能會執行最糟**TypedDataTable**。  
  
-   資料表很小，通常一個資料表包含的資料列會少於 500 列。 請注意，根據規則圖形與規則引擎可用的記憶體而定，這個數字可能會更大或更小。  
  
-   預期在規則集中會有規則鏈結行為。 呼叫**更新**函式上**DataConnection**不支援，但您無法叫用**DataConnection.Update**中使用的 helper 方法的規則。 需要規則鏈結時**TypedDataTable**是較佳選擇。  
  
-   資料表中一或多個資料行會保有規則不需要之非常大量的資料。 影像資料庫就是一個範例，影像資料庫中的資料行會存放影像 (大量資料)、名稱、日期等。 如果不需要影像，最好只選擇規則所需的資料行。 例如，發出"SELECT name，Date from TABLE"的查詢可以是更有效率使用**DataConnection**。  
  
-   如果許多規則需要或更新相同的資料庫資料列，使用**TypedDataTable**，所有規則之間共用的資料列，如果條件為相同 (例如，Table.Column = = 5)，條件評估可以最佳化。 與**DataConnection**，一般情況下，會使用每個規則會產生查詢**DataConnection**。 雖然資料列會重複使用 (如果資料表有主索引鍵)，每次都可產生多個查詢來取得相同的資料。  
  
## <a name="when-to-use-dataconnection-instead-of-typeddatatable"></a>何時使用 DataConnection 而非 TypedDataTable  
 在下列情況下使用 DataConnection 代替 TypedDataTable：  
  
-   資料表包含大量的資料列，但選擇性很低，即只有少數的資料列符合規則條件。  
  
-   只有一個資料庫資料表是大的，規則中所使用的所有其他物件只擁有少數的執行個體。 在最壞的狀況下，對資料庫執行的查詢數目會等於規則中所使用之所有其他執行個體的產品。  
  
-   規則僅由連結的條件所組成，在這些規則中所使用的是資料庫資料表以外的物件。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎中的資料存取](../core/data-access-in-the-business-rule-engine.md)