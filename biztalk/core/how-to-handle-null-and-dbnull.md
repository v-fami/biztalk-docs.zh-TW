---
title: 如何處理 Null 和 DBNull |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, NULL
ms.assetid: d235c265-4947-470b-9f2d-9936ae1b88a1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07ac74828a858b368cac5d401081a58b8602323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-null-and-dbnull"></a>如何處理 Null 和 DBNull
本主題描述處理與不同型別關聯之 Null 值時的預期行為，並討論用來檢查特定欄位或成員是否為 Null 或是否存在的選項。  
  
## <a name="xml"></a>XML  
 以下說明適用於 XML：  
  
-   XML 值絕對不會以 Null 從文件傳回。 這是空字串或「不存在」的錯誤。 若為空字串，即表示轉換特定型別時可能發生錯誤，例如在建立規則時將欄位指定為整數型別。  
  
-   「 商務規則編輯器 」 不允許您將欄位設定為 null，或設定欄位的類型**物件**。  
  
-   您可以透過物件模型將類型設**物件**。 在此情況下，傳回的值是 XPath 評估結果的類型 — **float**，**布林**，或**字串**，取決於 XPath 運算式。  
  
## <a name="net-classes"></a>.NET 類別  
 以下說明適用於 .NET 類別：  
  
-   不允許您與 null 比較，如果您傳回類型不是**物件**型別。  
  
-   您可以針對不是數值型別的參數傳遞 Null 做為參數，但是依據成員的實作而定，您可能會收到執行階段錯誤。  
  
-   您可以設定欄位的型別衍生自**物件**為 null。  
  
## <a name="data-connection"></a>資料連線  
 以下說明適用於資料連線：  
  
-   如果資料表允許 null 資料行和資料行類型不是，您可以比較任何資料庫資料表的資料行設為 null，**文字**， **ntext**，和**映像**。  
  
    > [!NOTE]
    >  「 商務規則編輯器 」 可讓您使用的類型，資料行**文字**和**ntext**，條件中。 不過，執行原則時，您可能會收到錯誤訊息，內容如下：「除了使用 IS NULL 或 LIKE 運算子時之外，無法比較或排序 text、ntext 及 image 資料類型。」  
  
-   如果資料表允許 Null 資料行，您就可以將任何資料庫資料表資料行設定為 Null。  
  
-   「 商務規則編輯器 」 會自動設定成員類型的繫結**物件**，如果您比較，或設為 null 的實值類型; 如果您重設或置換引數變更回原始型別。  
  
-   對於字串類型，其型別變更為**物件**如果您將它設定為 null，但是保留為字串，如果與 null 進行比較。  
  
-   您無法比較或設為**DBNull.Value**從 「 商務規則編輯器 」，因為它不會變更資料行類型**物件**。  
  
-   此引擎會將 DBNull 值轉換為 Null 以進行比較，而且會將 Null 轉換為 DBNull 值以插入資料庫中。  
  
-   測試會忽略 Null 值 (這是 SQL Server 的運作方式)。 例如，如果您擁有規則 "IF db.column > 5 THEN ."，只會測試在 db.column 中擁有值的資料列，並略過具有 Null 的資料列。  
  
## <a name="typeddatatable-and-typeddatarow"></a>TypedDataTable 和 TypedDataRow  
 以下說明適用於 TypedDataTable 和 TypedDataRow：  
  
-   「 商務規則編輯器 」 欄位型別變更為**物件**以相同方式與**DataConnection**s。  
  
-   除非您與 Null 比較，否則 Null 值的測試將會失敗。 例如，如果已判斷提示的任何資料列擁有 Null 值，規則 "IF db.column > 5 THEN " 就會發生錯誤。  
  
     請注意，由於條件會同時進行評估，因此諸如 "IF db.column != NULL AND db.column > 5 THEN  " 的測試仍會失敗，原因是這兩項測試可能會在每一個資料列上進行評估。  
  
## <a name="checking-for-null-or-existence"></a>檢查 Null 或存在狀況  
 編寫商務規則時，在比較欄位值之前檢查欄位是否存在是理所當然的。 不過，如果欄位是 Null 或不存在，比較值將會造成錯誤。 假設您有下列規則：  
  
 IF Product/Quantity Exists AND Product/Quantity > 1  
  
 如果 Product/Quantity 不存在，則會在規則中擲回錯誤。 避免這個問題的其中一種方式是將父節點傳遞給協助程式方法；如果項目值存在，協助程式方法就會傳回項目值，如果項目值不存在，則會傳回其他項目。 請參閱下列規則。  
  
 **規則 1**  
  
 IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)  
  
 **規則 2**  
  
 IF Helper.Value == X THEN...  
  
 另一種可能的解決方法是建立如下的規則：  
  
 IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)  
  
 在上述範例中，CheckQuantityAndDoSomething 函數會檢查參數值，並在符合條件時執行。  
  
> [!NOTE]
>  或者，您可以修改 XPath**欄位**來攔截任何錯誤，但它的 XML 事實的屬性不是建議的方法。