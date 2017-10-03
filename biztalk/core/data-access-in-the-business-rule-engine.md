---
title: "商務規則引擎中的資料存取 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, data access
- Business Rules Engine, helper classes
- data, data access
ms.assetid: 38da32af-1e0d-43fb-b946-fb49a11f1681
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58de70c2befd13f4995ebd073ebd70a2e7d84ea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-access-in-the-business-rule-engine"></a>商務規則引擎中的資料存取
規則引擎原生支援僅限.NET 物件。 若要處理資料庫的資料，您可以直接使用 ADO.NET，不過，引擎可提供一些協助程式類別，以規則簡化資料庫資料的使用。 規則引擎藉由公開三個資料庫相關的類型以延伸支援： **TypedDataRow**， **TypedDataTable**，和**DataConnection**。 本節描述這些協助程式類別、提供各種類型使用時機的建議，並討論使用這些類型時的部分效能影響。  
  
 協助程式類別如下：  
  
-   **TypedDataRow。** 使用 ADO.NET 的參考來建構**DataRow**執行個體。 **TypedDataRow**是規則的明顯選項，只處理一個或少數特定資料表的資料列的資料。  
  
-   **TypedDataTable。** 常值的集合**TypedDataRow**物件。 資料庫資料表中的每個資料列會包裝為**TypedDataRow**和規則引擎的判斷提示至工作記憶體。  
  
     A **TypedDataTable**需要記憶體中 ADO.NET **DataTable**，它可以是效能負擔，如果這個特定**DataTable**包含非常大量的資料列。 如果資料庫資料表中的資料列數少相關，而且您可以判斷之前呼叫的規則，使用這些資料列**DataTable**，否則使用**TypedDataRow**。此處的假設是 DataTable 中的資料列數目是相關的規則。  
  
-   **DataConnection。** 代表透過資料庫連線存取之資料庫中的資料表。 之間的差異**DataConnection**和**TypedDataTable**資料集名稱和資料表名稱，除了**DataConnection**需要可用的資料庫連線並選擇性地在資料庫交易內容。  
  
     使用規則中使用的部分或所有述詞**DataConnection**將成為針對資料庫連接的查詢條件約束的一部分。 引擎只會從資料庫擷取並使用滿足查詢條件約束的資料列。 此機制提供更佳的效能，也會耗用較少的記憶體比保留非常大量**DataTable**在記憶體中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 DataConnection 時的考量](../core/considerations-when-using-dataconnection.md)  
  
-   [使用 DataConnection 與 TypedDataTable](../core/using-dataconnection-and-typeddatatable.md)