---
title: REF CURSOR 的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- REF CURSORS, message schemas for
- IN REF CURSOR
- OUT REF CURSOR
- IN OUT REF CURSOR
ms.assetid: b62e7a9f-278c-41b3-90f0-2f621a34327b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bddfde0b0897c7d8c21a20126d2fa1d2f0f8c78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214758"
---
# <a name="message-schemas-for-ref-cursors"></a><span data-ttu-id="0be10-102">REF CURSOR 的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="0be10-102">Message Schemas for REF CURSORS</span></span>
<span data-ttu-id="0be10-103">REF CURSOR 是 Oracle 的 PL/SQL 資料類型，表示結果集的 Oracle 資料庫中的指標。</span><span class="sxs-lookup"><span data-stu-id="0be10-103">A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="0be10-104">REF CURSOR 類型啟用輸入和輸出資料的資料流，適合用來傳輸大量資料的 PL/SQL 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0be10-104">REF CURSOR types enable input and output streaming of data and are ideal for transferring large amounts of data to and from a PL/SQL code block.</span></span> [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="0be10-105">提供傳遞強型別和弱型別 REF CURSOR 參數的 PL/SQL 程序和函式中，逾時及在 OUT 參數的支援。</span><span class="sxs-lookup"><span data-stu-id="0be10-105"> provides support for passing strongly-typed and weakly-typed REF CURSOR parameters to PL/SQL procedures and functions as IN, OUT and IN OUT parameters.</span></span>  
  
 <span data-ttu-id="0be10-106">在 Oracle 資料庫中，REF CURSOR 類型可以是強型別或弱型別：</span><span class="sxs-lookup"><span data-stu-id="0be10-106">In the Oracle database, a REF CURSOR type can be either strongly-typed or weakly-typed:</span></span>  
  
-   <span data-ttu-id="0be10-107">RETURN 子句中宣告強類型的 REF CURSOR `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`。</span><span class="sxs-lookup"><span data-stu-id="0be10-107">A strongly-typed REF CURSOR is declared with a RETURN clause as in `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`.</span></span> <span data-ttu-id="0be10-108">強型別 REF 資料指標變數只能表示結果集，其中包含符合的型別與宣告其 REF 資料指標類型的資料。</span><span class="sxs-lookup"><span data-stu-id="0be10-108">A strongly-typed REF CURSOR variable can only represent a result set that contains data that matches the type with which its REF CURSOR type is declared.</span></span> <span data-ttu-id="0be10-109">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]傳回強型別結果集是強型別 REF 資料指標。</span><span class="sxs-lookup"><span data-stu-id="0be10-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a strongly-typed result set for a strongly-typed REF CURSOR.</span></span>  
  
-   <span data-ttu-id="0be10-110">弱型別 REF 資料指標宣告時沒有做為中的 RETURN 子句`TYPE WeakCurType IS REF CURSOR;`。</span><span class="sxs-lookup"><span data-stu-id="0be10-110">A weakly-typed REF CURSOR is declared without a RETURN clause as in `TYPE WeakCurType IS REF CURSOR;`.</span></span> <span data-ttu-id="0be10-111">Oracle 也提供一種特殊的 REF CURSOR 類型呼叫可以用來宣告弱型別 REF 資料指標變數的 SYS_REFCURSOR。</span><span class="sxs-lookup"><span data-stu-id="0be10-111">Oracle also provides a special REF CURSOR type called SYS_REFCURSOR that can be used to declare weakly-typed REF CURSOR variables.</span></span> <span data-ttu-id="0be10-112">弱型別 REF 資料指標變數可以表示結果集包含任何種類的資料列資料。</span><span class="sxs-lookup"><span data-stu-id="0be10-112">Weakly-typed REF CURSOR variables can represent a result set that contains any kind of row data.</span></span> <span data-ttu-id="0be10-113">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]弱式類型的 REF CURSOR 傳回弱式類型的結果集的一般記錄。</span><span class="sxs-lookup"><span data-stu-id="0be10-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a weakly-typed result set of generic records for a weakly-typed REF CURSOR.</span></span>  
  
## <a name="in-ref-cursor-parameters"></a><span data-ttu-id="0be10-114">中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="0be10-114">IN REF CURSOR Parameters</span></span>  
 <span data-ttu-id="0be10-115">沒有任何 ODP.NET API，來建立 REF CURSOR 在 Oracle 伺服器上，所以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]無法提供建立和維護 REF 資料指標變數的用戶端程式的功能。</span><span class="sxs-lookup"><span data-stu-id="0be10-115">There is no ODP.NET API to create a REF CURSOR on the Oracle server, so the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] cannot provide the capability for a client program to create and maintain REF CURSOR variables.</span></span>  
  
 <span data-ttu-id="0be10-116">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ，不過，讓用戶端中 REF CURSOR 參數傳遞給函式或預存程序，藉由指定傳回 REF CURSOR 的 PL/SQL 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0be10-116">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does, however, enable a client to pass IN REF CURSOR parameters to functions or stored procedures by specifying a block of PL/SQL code that returns a REF CURSOR.</span></span> <span data-ttu-id="0be10-117">配接器會使用此程式碼以建立並開啟 Oracle 伺服器上的 REF CURSOR 變數然後，它會呼叫函式或預存程序中使用這個變數做為 IN 參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-117">The adapter uses this code to create and OPEN a REF CURSOR variable on the Oracle server; it then calls the function or stored procedure using this variable as the IN parameter.</span></span>  
  
 <span data-ttu-id="0be10-118">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]以包含 PL/SQL 程式碼區塊的字串表示中 REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-118">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CURSOR parameters as strings that contain the PL/SQL code block.</span></span> <span data-ttu-id="0be10-119">在這個區塊中使用問號 （？） 指定 REF CURSOR 的位置。</span><span class="sxs-lookup"><span data-stu-id="0be10-119">Within this block, the location of the REF CURSOR is specified with a question mark (?).</span></span> <span data-ttu-id="0be10-120">PL/SQL 程式碼區塊可以包含開啟 FOR 陳述式，其中包含 SQL 查詢。或者也可以包含函數或程序呼叫中，開啟的 REF CURSOR 傳回 OUT 參數中。</span><span class="sxs-lookup"><span data-stu-id="0be10-120">The PL/SQL code block can contain an OPEN-FOR statement that contains a SQL query; or it can contain a function or procedure call in which an opened REF CURSOR is returned in an OUT parameter.</span></span>  
  
 <span data-ttu-id="0be10-121">以下顯示如何藉由呼叫預存程序或函式來開啟 REF CURSOR 指定中 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="0be10-121">The following shows how to specify an IN REF CURSOR by calling a stored procedure or function to open the REF CURSOR.</span></span>  
  
```  
<[IN_REF_CURSOR_PARAM_NAME]>begin [SP_NAME]([SP_PARAMS...], ?, [SP_PARAMS...]); end;</[IN_REF_CURSOR_PARAM_NAME]>  
  
Example:  
<EMP_RC>begin GETEMP(1, ?); end; </EMP_RC>  
```  
  
 <span data-ttu-id="0be10-122">以下顯示如何使用選取的查詢開啟 REF CURSOR 指定中 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="0be10-122">The following shows how to specify an IN REF CURSOR by using a SELECT query to open the REF CURSOR.</span></span>  
  
```  
<IN_REF_CURSOR_PARAM_NAME>begin open ? for select [FIELD_NAMES] from [TABLE_NAME]; end;</IN_REF_CURSOR_PARAM_NAME>  
  
Example:  
<EMP_RC>begin open ? for select * from EMP; end;</EMP_RC>  
```  
  
## <a name="out-ref-cursor-parameters"></a><span data-ttu-id="0be10-123">OUT REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="0be10-123">OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="0be10-124">OUT REF CURSOR 參數會傳回做為強型別或弱式類型的結果集。</span><span class="sxs-lookup"><span data-stu-id="0be10-124">OUT REF CURSOR parameters are returned as either strongly-typed or weakly-typed result sets.</span></span> <span data-ttu-id="0be10-125">傳回的結果集的類型取決於是否 REF CURSOR 參數宣告強型別或弱式類型的 REF CURSOR，在預存程序或函式定義為 Oracle 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0be10-125">The type of the result set returned depends on whether the REF CURSOR parameter is declared as a strongly-typed or weakly-typed REF CURSOR in the stored procedure or function definition on the Oracle server.</span></span> <span data-ttu-id="0be10-126">強類型傳回結果集是強型別 REF CURSOR 參數的和弱型別會傳回結果集的弱式類型的 REF CURSOR 參數 （例如，參數宣告的 SYS_REFCURSOR）。</span><span class="sxs-lookup"><span data-stu-id="0be10-126">A strongly-typed result set is returned for strongly-typed REF CURSOR parameters and a weakly-typed result set is returned for weakly-typed REF CURSOR parameters (for example, parameters declared with a SYS_REFCURSOR type).</span></span>  
  
 <span data-ttu-id="0be10-127">下圖顯示的強型別出 REF CURSOR 參數的 XML。</span><span class="sxs-lookup"><span data-stu-id="0be10-127">The following shows the XML for a strongly-typed OUT REF CURSOR parameter.</span></span>  
  
```  
<[PARAM_NAME]>  
 <[PARAM_NAME]RECORD>  
  <[COL1_NAME]>value1</[COL1_NAME]>  
  <[COL2_NAME]>value2</[COL2_NAME]>  
  ...  
 </[PARAM_NAME]RECORD>  
</[PARAM_NAME]>  
  
[PARAM_NAME] = OUT REF CURSOR parameter name; for example, EMP_REFCURSOR  
[COL_NAME] = Name of a column in the REF CURSOR type; for example, Name.  
```  
  
 <span data-ttu-id="0be10-128">下圖顯示弱型別出 REF CURSOR 參數的 XML。</span><span class="sxs-lookup"><span data-stu-id="0be10-128">The following shows the XML for a weakly-typed OUT REF CURSOR parameter.</span></span>  
  
```  
<[PARAM_NAME]>  
 <GenRecordRow xmlns="oracledb">  
  <GenRecordColumn>  
   <ColumnName>COL_NAME</ColumnName>  
   <ColumnValue>COL_VALUE</ColumnValue>  
   <ColumnType>COL_TYPE</ColumnType>  
  </GenRecordColumn>  
  …  
 </GenRecordRow>  
 …  
</[PARAM_NAME]>  
  
[COL_NAME] = Name of column; for example, Name  
[COL_VALUE] = Column value; for example, Scott  
[COL_TYPE] = Column data type; for example, System.String  
```  
  
## <a name="in-out-ref-cursor-parameters"></a><span data-ttu-id="0be10-129">IN，OUT REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="0be10-129">IN OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="0be10-130">因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]模型中 REF CURSOR 參數做為字串和複雜類型的 REF CURSOR OUT 參數，它不能支援單一類型 IN OUT REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-130">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] models IN REF CURSOR parameters as strings and OUT REF CURSOR parameters as complex types, it cannot support a single type for an IN OUT REF CURSOR parameter.</span></span> <span data-ttu-id="0be10-131">基於這個理由，它會將 IN OUT REF CURSOR 參數視為兩個不同的參數： 在要求訊息和回應訊息中的 OUT 參數，為 IN 參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-131">For this reason, it treats IN OUT REF CURSOR parameters as two different parameters: an IN parameter in the request message and an OUT parameter in the response message.</span></span>  
  
 <span data-ttu-id="0be10-132">若要避免名稱衝突，在服務模型程式設計中，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將字串"_IN"附加至 IN 參數，要求訊息中，以便針對給定的參數，名為 [PARAM_NAME]，建立兩個參數：</span><span class="sxs-lookup"><span data-stu-id="0be10-132">To avoid a name conflict in service model programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] appends the string "_IN" to the IN parameter in the request message so that for a given parameter named [PARAM_NAME], two parameters are created:</span></span>  
  
-   <span data-ttu-id="0be10-133">[PARAM_NAME] _IN 是中 REF CURSOR 參數的預存程序或函式要求訊息中。</span><span class="sxs-lookup"><span data-stu-id="0be10-133">[PARAM_NAME]_IN is an IN REF CURSOR parameter in the stored procedure or function request message.</span></span> <span data-ttu-id="0be10-134">它包含的 PL/SQL 陳述式 （select 查詢或預存程序或函式呼叫） 傳回 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="0be10-134">It contains a PL/SQL statement (either a select query or a stored procedure or function call) that returns a REF CURSOR.</span></span>  
  
-   <span data-ttu-id="0be10-135">[PARAM_NAME] 是出 REF CURSOR 參數的預存程序或函式的回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="0be10-135">[PARAM_NAME] is an OUT REF CURSOR parameter in the stored procedure or function response message.</span></span> <span data-ttu-id="0be10-136">它包含 OUT REF CURSOR 做為強型別或弱式類型的結果集。</span><span class="sxs-lookup"><span data-stu-id="0be10-136">It contains the OUT REF CURSOR as a strongly-typed or weakly-typed result set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0be10-137">配接器不支援的程序或函數，其中包含名為 [PARAM_NAME] _IN 和 IN OUT REF CURSOR 參數名為 [PARAM_NAME] 為 IN 參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-137">The adapter cannot support a procedure or function that contains an IN parameter named [PARAM_NAME]_IN and an IN OUT REF CURSOR parameter named [PARAM_NAME].</span></span> <span data-ttu-id="0be10-138">這是因為配接器必須要有一個名為 [PARAM_NAME] _IN 代表 REF CURSOR 參數的輸入參數，而且您無法在要求訊息中指定這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="0be10-138">This is because the adapter expects a parameter named [PARAM_NAME]_IN to represent the input to the REF CURSOR parameter, and you cannot specify both parameters in the request message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be10-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0be10-139">See Also</span></span>  
 [<span data-ttu-id="0be10-140">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="0be10-140">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)