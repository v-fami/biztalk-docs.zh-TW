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
# <a name="data-access-in-the-business-rule-engine"></a><span data-ttu-id="d6c83-102">商務規則引擎中的資料存取</span><span class="sxs-lookup"><span data-stu-id="d6c83-102">Data Access in the Business Rule Engine</span></span>
<span data-ttu-id="d6c83-103">規則引擎原生支援僅限.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d6c83-103">The rule engine supports only .NET objects natively.</span></span> <span data-ttu-id="d6c83-104">若要處理資料庫的資料，您可以直接使用 ADO.NET，不過，引擎可提供一些協助程式類別，以規則簡化資料庫資料的使用。</span><span class="sxs-lookup"><span data-stu-id="d6c83-104">To handle data from a database, you can use the ADO.NET objects directly, but the engine provides some helper classes to simplify the use of database data from rules.</span></span> <span data-ttu-id="d6c83-105">規則引擎藉由公開三個資料庫相關的類型以延伸支援： **TypedDataRow**， **TypedDataTable**，和**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="d6c83-105">The rule engine extends its support by exposing three database-related types: **TypedDataRow**, **TypedDataTable**, and **DataConnection**.</span></span> <span data-ttu-id="d6c83-106">本節描述這些協助程式類別、提供各種類型使用時機的建議，並討論使用這些類型時的部分效能影響。</span><span class="sxs-lookup"><span data-stu-id="d6c83-106">This section describes these helper classes, gives recommendations about when to use each type, and discusses some performance implications when using them.</span></span>  
  
 <span data-ttu-id="d6c83-107">協助程式類別如下：</span><span class="sxs-lookup"><span data-stu-id="d6c83-107">The helper classes are as follows:</span></span>  
  
-   <span data-ttu-id="d6c83-108">**TypedDataRow。**</span><span class="sxs-lookup"><span data-stu-id="d6c83-108">**TypedDataRow.**</span></span> <span data-ttu-id="d6c83-109">使用 ADO.NET 的參考來建構**DataRow**執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6c83-109">Constructed by using a reference to an ADO.NET **DataRow** instance.</span></span> <span data-ttu-id="d6c83-110">**TypedDataRow**是規則的明顯選項，只處理一個或少數特定資料表的資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="d6c83-110">The **TypedDataRow** is an obvious choice for rules that only deal with data from one or a small number of rows from a particular table.</span></span>  
  
-   <span data-ttu-id="d6c83-111">**TypedDataTable。**</span><span class="sxs-lookup"><span data-stu-id="d6c83-111">**TypedDataTable.**</span></span> <span data-ttu-id="d6c83-112">常值的集合**TypedDataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="d6c83-112">Literally a collection of **TypedDataRow** objects.</span></span> <span data-ttu-id="d6c83-113">資料庫資料表中的每個資料列會包裝為**TypedDataRow**和規則引擎的判斷提示至工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="d6c83-113">Each row in the database table will be wrapped as a **TypedDataRow** and asserted into the working memory by the rule engine.</span></span>  
  
     <span data-ttu-id="d6c83-114">A **TypedDataTable**需要記憶體中 ADO.NET **DataTable**，它可以是效能負擔，如果這個特定**DataTable**包含非常大量的資料列。</span><span class="sxs-lookup"><span data-stu-id="d6c83-114">A **TypedDataTable** requires an in-memory ADO.NET **DataTable**, which can be a performance overhead if this particular **DataTable** contains a very large number of rows.</span></span> <span data-ttu-id="d6c83-115">如果資料庫資料表中的資料列數少相關，而且您可以判斷之前呼叫的規則，使用這些資料列**DataTable**，否則使用**TypedDataRow**。此處的假設是 DataTable 中的資料列數目是相關的規則。</span><span class="sxs-lookup"><span data-stu-id="d6c83-115">If a small number of rows in the database table is relevant and you can determine these rows prior to calling the rules, use a **DataTable**, otherwise use **TypedDataRow**.The assumption is that a high number of rows in the DataTable are relevant to the rules.</span></span>  
  
-   <span data-ttu-id="d6c83-116">**DataConnection。**</span><span class="sxs-lookup"><span data-stu-id="d6c83-116">**DataConnection.**</span></span> <span data-ttu-id="d6c83-117">代表透過資料庫連線存取之資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c83-117">Represents a table in a database accessed through a database connection.</span></span> <span data-ttu-id="d6c83-118">之間的差異**DataConnection**和**TypedDataTable**資料集名稱和資料表名稱，除了**DataConnection**需要可用的資料庫連線並選擇性地在資料庫交易內容。</span><span class="sxs-lookup"><span data-stu-id="d6c83-118">The difference between **DataConnection** and **TypedDataTable** is that in addition to the dataset name and table name, **DataConnection** requires a usable database connection and optionally a database transaction context.</span></span>  
  
     <span data-ttu-id="d6c83-119">使用規則中使用的部分或所有述詞**DataConnection**將成為針對資料庫連接的查詢條件約束的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6c83-119">Some or all predicates used in rules with the **DataConnection** will become part of query constraints against the database connection.</span></span> <span data-ttu-id="d6c83-120">引擎只會從資料庫擷取並使用滿足查詢條件約束的資料列。</span><span class="sxs-lookup"><span data-stu-id="d6c83-120">Only rows that satisfy the query constraints will be retrieved from the database and used by the engine.</span></span> <span data-ttu-id="d6c83-121">此機制提供更佳的效能，也會耗用較少的記憶體比保留非常大量**DataTable**在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d6c83-121">This mechanism provides better performance and consumes less memory than holding a very large **DataTable** in memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6c83-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="d6c83-122">In This Section</span></span>  
  
-   [<span data-ttu-id="d6c83-123">使用 DataConnection 時的考量</span><span class="sxs-lookup"><span data-stu-id="d6c83-123">Considerations When Using DataConnection</span></span>](../core/considerations-when-using-dataconnection.md)  
  
-   [<span data-ttu-id="d6c83-124">使用 DataConnection 與 TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="d6c83-124">Using DataConnection and TypedDataTable</span></span>](../core/using-dataconnection-and-typeddatatable.md)