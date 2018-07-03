---
title: Siebel 中的 SELECT 陳述式的語法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, searching and sorting data using
- Data Provider for Siebel, SELECT statement
- SELECT statement, syntax for
ms.assetid: 8528b115-d6f3-420d-8617-0e56dc8922bf
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 543445fe6958a156894bb6c0d268d9b3b5814b23
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022660"
---
# <a name="syntax-for-a-select-statement-in-siebel"></a><span data-ttu-id="5e74b-102">Siebel 中的 SELECT 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="5e74b-102">Syntax for a SELECT Statement in Siebel</span></span>
<span data-ttu-id="5e74b-103">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，ADO.NET 用戶端可以藉由指定 WHERE 子句，表示有效的 Siebel 搜尋規格在 Siebel 商務元件中執行 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="5e74b-103">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can perform a SELECT query on Siebel business components by specifying a WHERE clause that represents a valid Siebel search specification.</span></span> <span data-ttu-id="5e74b-104">SELECT 陳述式的語法是：</span><span class="sxs-lookup"><span data-stu-id="5e74b-104">The syntax for the SELECT statement is:</span></span>  
  
```  
SELECT  
<column name 1> AS <column alias 1>,  
<column name 2> AS <column alias 2>,  
…  
FROM  
<Business object name>.<Business component name> AS <table alias>  
WHERE  
<filter condition>  
OPTION  
'ViewMode <value>'  
```  
  
 <span data-ttu-id="5e74b-105">在上述語法中，檢視模式選項對應至 Siebel 系統的檢視模式，這是篩選機制來限制的一組符合查詢的記錄。</span><span class="sxs-lookup"><span data-stu-id="5e74b-105">In the above syntax, the ViewMode option corresponds to the Siebel system View Modes, which is a filtering mechanism to restrict the set of records that match the query.</span></span> <span data-ttu-id="5e74b-106">允許的值組，請參閱 Siebel 文件。</span><span class="sxs-lookup"><span data-stu-id="5e74b-106">For the allowed set of values, see the Siebel documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e74b-107">如果在 WHERE 子句中的欄位名稱包含特殊字元或空格，請確定您一律將括在方括號內的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="5e74b-107">If the field names in the WHERE clause contain special characters or empty spaces, make sure you always enclose the field names within square brackets.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="5e74b-108">在選取查詢中包含的特殊字元的別名名稱，請確定您包含方括號中的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="5e74b-108">In SELECT queries containing alias names with special characters, make sure you include the alias names within square brackets.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="5e74b-109">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援別名的資料表名稱在 SELECT 子句中，但不是在 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="5e74b-109">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause but not in the WHERE clause.</span></span>  
  
## <a name="searching-and-sorting-data-using-the-data-provider-for-siebel"></a><span data-ttu-id="5e74b-110">搜尋和排序資料，使用 Data Provider for Siebel</span><span class="sxs-lookup"><span data-stu-id="5e74b-110">Searching and Sorting Data Using the Data Provider for Siebel</span></span>  
 <span data-ttu-id="5e74b-111">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] Siebel 系統所支援的搜尋規格為基礎的 SQL 陳述式中支援篩選條件。</span><span class="sxs-lookup"><span data-stu-id="5e74b-111">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports a filter condition in SQL statements based on the search specifications supported by the Siebel system.</span></span>  
  
 <span data-ttu-id="5e74b-112">如需搜尋規格的規則包括：</span><span class="sxs-lookup"><span data-stu-id="5e74b-112">The rules for the search specification are:</span></span>  
  
- <span data-ttu-id="5e74b-113">要比較的常數、 欄位或另一個欄位的一個欄位，必須使用標準的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="5e74b-113">Standard comparison operators must be used to compare a field to a constant, or one field to another field.</span></span> <span data-ttu-id="5e74b-114">這些包括 =、 ！ =，>，<>、 =、 和 < =。</span><span class="sxs-lookup"><span data-stu-id="5e74b-114">These include =, !=, >, <, >=, and <=.</span></span>  
  
  ```  
  Example: [Revenue] > 5000  
  ```  
  
- <span data-ttu-id="5e74b-115">字串常數必須括在雙引號括住，並必須區分大小寫的字串值。</span><span class="sxs-lookup"><span data-stu-id="5e74b-115">String constants must be enclosed in double quotation marks, and the string values must be case-sensitive.</span></span>  
  
  ```  
  Example: [Type] != "COST LIST"  
  ```  
  
- <span data-ttu-id="5e74b-116">邏輯運算子 AND、 OR，您必須用來否定或運算式結合。</span><span class="sxs-lookup"><span data-stu-id="5e74b-116">The logical operators AND, OR, and NOT must be used to negate or combine expressions.</span></span> <span data-ttu-id="5e74b-117">區分大小寫會忽略這些運算子;比方說，「 和 」 等同於"AND"。</span><span class="sxs-lookup"><span data-stu-id="5e74b-117">Case sensitivity is ignored in these operators; for example, “and” is the same as “AND”.</span></span>  
  
  ```  
  Example: [Competitor] IS NOT NULL and [Competitor] != "N"  
  ```  
  
- <span data-ttu-id="5e74b-118">在搜尋規格中的欄位名稱必須以方括弧括住。</span><span class="sxs-lookup"><span data-stu-id="5e74b-118">A field name in a search specification must be enclosed in square brackets.</span></span>  
  
  ```  
  Example: [Conflict Id] = 0  
  ```  
  
- <span data-ttu-id="5e74b-119">LIKE 運算子可能會用來建立文字字串比較運算式中的欄位相較於常數，或以另一個欄位，而只有前的幾個字元比對的欄位是必要的。</span><span class="sxs-lookup"><span data-stu-id="5e74b-119">The LIKE operator may be used to create text string comparison expressions in which a field is compared to a constant, or a field to another field and a match on only the first several characters is required.</span></span> <span data-ttu-id="5e74b-120">萬用字元"\*"和"？"</span><span class="sxs-lookup"><span data-stu-id="5e74b-120">The wildcard characters “\*” and “?”</span></span> <span data-ttu-id="5e74b-121">必須用於分別表示任意數目的字元，以及單一字元。</span><span class="sxs-lookup"><span data-stu-id="5e74b-121">must be used to indicate any number of characters, and a single character, respectively.</span></span>  
  
- <span data-ttu-id="5e74b-122">ADO.NET 用戶端可以指定原始的 Siebel 商務物件、 商務元件和商務元件欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="5e74b-122">ADO.NET clients can specify original Siebel business objects, business components, and business component field names.</span></span> <span data-ttu-id="5e74b-123">這些名稱必須括在方括號中，如果它們包含任何特殊字元或空白字元。</span><span class="sxs-lookup"><span data-stu-id="5e74b-123">These names must be enclosed in square brackets if they contain any special characters or white space.</span></span> <span data-ttu-id="5e74b-124">支援的查詢的範例包括：</span><span class="sxs-lookup"><span data-stu-id="5e74b-124">Examples of queries that are supported are:</span></span>  
  
  ```  
  SELECT [Name], [Postal Code] FROM Account.Account where [Postal Code] != '11065'  
  SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC  
  SELECT * FROM [Admin Price List].[Price Book Items]  
  ```  
  
  <span data-ttu-id="5e74b-125">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援排序依據排序規格 Siebel 所支援的 SQL 陳述式中的規格。</span><span class="sxs-lookup"><span data-stu-id="5e74b-125">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports sort specifications in SQL statements based on the sort specification supported by Siebel.</span></span> <span data-ttu-id="5e74b-126">排序規格的規則如下：</span><span class="sxs-lookup"><span data-stu-id="5e74b-126">The rules for the sort specification are:</span></span>  
  
- <span data-ttu-id="5e74b-127">使用逗號來分隔欄位名稱，在排序規格;比方說，「 名稱 」、 「 位置</span><span class="sxs-lookup"><span data-stu-id="5e74b-127">Use commas to separate field names in a sort specification; for instance, Name, Location</span></span>  
  
- <span data-ttu-id="5e74b-128">若要表示以遞減順序排序清單中的欄位，包括 (DESC) 在欄位名稱後面，如同 「 開始日期 (DESC)。 」</span><span class="sxs-lookup"><span data-stu-id="5e74b-128">To indicate that a field in the list sorts in descending order, include (DESC) after the field name, as in “Start Date (DESC).”</span></span> <span data-ttu-id="5e74b-129">如果沒有未指定排序順序，會使用遞增的順序。</span><span class="sxs-lookup"><span data-stu-id="5e74b-129">If no sort order is specified, ascending order is used.</span></span> <span data-ttu-id="5e74b-130">若要明確地指定遞增順序，使用關鍵字 (ASC)。</span><span class="sxs-lookup"><span data-stu-id="5e74b-130">To explicitly specify ascending order, use the keyword (ASC).</span></span>  
  
- <span data-ttu-id="5e74b-131">排序規格運算式必須是 255 個字元或更少。</span><span class="sxs-lookup"><span data-stu-id="5e74b-131">The sort specification expression must be 255 characters or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e74b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e74b-132">See Also</span></span>  
 [<span data-ttu-id="5e74b-133">使用 .NET Framework Data Provider for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="5e74b-133">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)