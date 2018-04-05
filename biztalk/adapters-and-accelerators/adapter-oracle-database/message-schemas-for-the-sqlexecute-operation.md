---
title: SQLEXECUTE 操作訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLEXECUTE operations, message schemas for
ms.assetid: 744645f4-0674-44e0-bf8d-8df70086b0f1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c7efc6a59e9dd4c163388803763a7b90a13b31
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-the-sqlexecute-operation"></a><span data-ttu-id="fa655-102">SQLEXECUTE 操作的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="fa655-102">Message Schemas for the SQLEXECUTE Operation</span></span>
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="fa655-103">呈現強型別中繼資料的成品存在於 LOB 系統，並公開在這些成品的標準作業。</span><span class="sxs-lookup"><span data-stu-id="fa655-103"> surfaces strongly-typed metadata for artifacts present in the LOB system and exposes standard operations on these artifacts.</span></span> <span data-ttu-id="fa655-104">不過，有一些的案例，其中的應用程式可能需要執行任意的 SQL 陳述式由應用程式中的商務邏輯所驅動。</span><span class="sxs-lookup"><span data-stu-id="fa655-104">However, there are scenarios where an application might require the execution of an arbitrary SQL statement that is driven by the business logic in the application.</span></span> <span data-ttu-id="fa655-105">例如，您可能想要：</span><span class="sxs-lookup"><span data-stu-id="fa655-105">For example, you may want to:</span></span>  
  
-   <span data-ttu-id="fa655-106">對資料庫成品，便不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。</span><span class="sxs-lookup"><span data-stu-id="fa655-106">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
-   <span data-ttu-id="fa655-107">執行資料定義語言 」 作業。例如，建立資料表。</span><span class="sxs-lookup"><span data-stu-id="fa655-107">Perform Data Definition Language operations; for example, create a table.</span></span>  
  
-   <span data-ttu-id="fa655-108">在未出現在設計階段; 資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="fa655-108">Perform operations on a database artifact that was not present at design-time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
-   <span data-ttu-id="fa655-109">更複雜 DML 資料表上執行作業的作業由顯示比[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 若為範例執行的查詢包含聯結子句。</span><span class="sxs-lookup"><span data-stu-id="fa655-109">Perform more complex DML operations on tables than the operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example perform a query that includes a JOIN clause.</span></span>  
  
 <span data-ttu-id="fa655-110">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現一個特殊稱為 SQLEXECUTE 操作以支援這種情況的作業。</span><span class="sxs-lookup"><span data-stu-id="fa655-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces a special operation called the SQLEXECUTE operation to support such scenarios.</span></span> <span data-ttu-id="fa655-111">藉由使用這項作業，您可以指定任意 SQL 陳述式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]Oracle 資料庫上執行。</span><span class="sxs-lookup"><span data-stu-id="fa655-111">By using this operation, you can specify an arbitrary SQL statement for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to execute on the Oracle database.</span></span> <span data-ttu-id="fa655-112">您也可以指定多個輸入參數的 SQL 陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="fa655-112">You can also specify multiple blocks of input parameters to the SQL statement.</span></span> <span data-ttu-id="fa655-113">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行每個參數集一次的 SQL 陳述式並傳回任何輸出做為泛型 （弱型別） 資料錄集。</span><span class="sxs-lookup"><span data-stu-id="fa655-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes the SQL statement once for each set of parameters and returns any output as a generic (weakly-typed) record set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa655-114">您可以傳遞 IN 與 IN OUT 參數的程序、 函數和 SQLEXECUTE 操作中的封裝。</span><span class="sxs-lookup"><span data-stu-id="fa655-114">You can pass IN and IN OUT parameters to procedures, functions, and packages in the SQLEXECUTE operation.</span></span> <span data-ttu-id="fa655-115">叫用的成品將使用 Oracle 資料庫上提供的參數來執行不過，SQLEXECUTE 作業不會傳回的 OUT 值及 IN OUT 參數，用戶端。</span><span class="sxs-lookup"><span data-stu-id="fa655-115">The invoked artifact will execute with the supplied parameters on the Oracle database; however, the SQLEXECUTE operation does not return the value of OUT and IN OUT parameters to the client.</span></span> <span data-ttu-id="fa655-116">如果您想要叫用程序、 函數或套件，Microsoft 建議您這麼做叫用的專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。</span><span class="sxs-lookup"><span data-stu-id="fa655-116">If you want to invoke procedures, functions, or packages, Microsoft recommends that you do so by invoking the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
 <span data-ttu-id="fa655-117">下列 XML 顯示 SQLEXECUTE 作業的結構：</span><span class="sxs-lookup"><span data-stu-id="fa655-117">The following XML shows the structure of the SQLEXECUTE operation:</span></span>  
  
```  
<SQLEXECUTE xmlns="SQLEXECUTE">  
  <SQLSTATEMENT> [STATEMENT] </SQLSTATEMENT>  
  <PARAMETERSCHEMA>[PARAM_SPEC]</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA>  
      <PARAMETER xmlns:c="http://schemas.microsoft.com/2003/10/Serialization/Arrays">  
        <c:string>[PARAM_VAL_1]</c:string>  
      </PARAMETER>  
    </PARAMETERDATA>  
    …  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 <span data-ttu-id="fa655-118">[陳述式] = 的 SQL 陳述式，才可執行，例如，「 選取 \* 從 emp WHERE empno =: emp_no"。</span><span class="sxs-lookup"><span data-stu-id="fa655-118">[STATEMENT] = The SQL statement to execute; for example, "SELECT \* from emp WHERE empno=:emp_no".</span></span>  
  
 <span data-ttu-id="fa655-119">[PARAM_SPEC] = 在 SQL 陳述式和其資料類型，在參數清單例如，"emp_no 數字 」。</span><span class="sxs-lookup"><span data-stu-id="fa655-119">[PARAM_SPEC] = The list of the IN parameters in the SQL statement and their data types; for example, "emp_no NUMBER".</span></span>  
  
 <span data-ttu-id="fa655-120">[PARAM_VAL_1] = 第一個參數的值。</span><span class="sxs-lookup"><span data-stu-id="fa655-120">[PARAM_VAL_1] = The value of the first parameter.</span></span>  
  
 <span data-ttu-id="fa655-121">每個\<PARAMETERDATA\>章節包含一組完整的\<參數\>符合結構描述中的項目\<PARAMETERSCHEMA\> > 一節。</span><span class="sxs-lookup"><span data-stu-id="fa655-121">Each \<PARAMETERDATA\> section contains a complete set of \<PARAMETER\> elements that match the schema in the \<PARAMETERSCHEMA\> section.</span></span> <span data-ttu-id="fa655-122">\<PARAMETERSET\>可以包含多個\<PARAMETERDATA\>區段。</span><span class="sxs-lookup"><span data-stu-id="fa655-122">The \<PARAMETERSET\> can contain multiple \<PARAMETERDATA\> sections.</span></span> <span data-ttu-id="fa655-123">如果這種情況，SQL 陳述式會執行許多次，一次針對每個參數集。</span><span class="sxs-lookup"><span data-stu-id="fa655-123">If this is the case, the SQL statement is executed multiple times, once against each parameter set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa655-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa655-124">See Also</span></span>  
 [<span data-ttu-id="fa655-125">BizTalk Adapter for Oracle Database 的訊息和訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="fa655-125">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)