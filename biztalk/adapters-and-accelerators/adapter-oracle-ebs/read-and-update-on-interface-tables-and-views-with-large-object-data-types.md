---
title: 介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f6e8db6-ba68-4e3f-84b2-1cc31ce89bcb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b12eeae422f5da90c6874f70d2ffddbc19f75bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964700"
---
# <a name="operations-on-interface-tables-interface-views-tables-and-views-that-contain-lob-data"></a><span data-ttu-id="44f52-102">介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業</span><span class="sxs-lookup"><span data-stu-id="44f52-102">Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data</span></span>
<span data-ttu-id="44f52-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供 Oracle 大型物件 (LOB) 資料類型的支援：</span><span class="sxs-lookup"><span data-stu-id="44f52-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] provides support for the Oracle large object (LOB) data types:</span></span>  
  
-   <span data-ttu-id="44f52-104">二進位大型物件 (BLOB)</span><span class="sxs-lookup"><span data-stu-id="44f52-104">Binary large object (BLOB)</span></span>  
  
-   <span data-ttu-id="44f52-105">字元大型物件 (CLOB)</span><span class="sxs-lookup"><span data-stu-id="44f52-105">Character large object (CLOB)</span></span>  
  
-   <span data-ttu-id="44f52-106">國家 （地區） 的字元大型物件 (NCLOB)</span><span class="sxs-lookup"><span data-stu-id="44f52-106">National character large object (NCLOB)</span></span>  
  
-   <span data-ttu-id="44f52-107">二進位檔案 (BFILE)。</span><span class="sxs-lookup"><span data-stu-id="44f52-107">Binary file (BFILE).</span></span> <span data-ttu-id="44f52-108">如需詳細資訊，請參閱[資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="44f52-108">For more information, see [Operations on Tables That Contain BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).</span></span>  
  
 <span data-ttu-id="44f52-109">在基礎 Oracle 資料庫時，LOB 資料類型用來儲存大量的資料，最多為 4 gb (GB)。</span><span class="sxs-lookup"><span data-stu-id="44f52-109">In the underlying Oracle database, LOB data types are used to store large amounts of data, up to 4 gigabytes (GB).</span></span> <span data-ttu-id="44f52-110">除了 BFILE 資料型別，LOB 資料類型支援輸入和輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="44f52-110">Except for the BFILE data type, LOB data types support both input and output streaming.</span></span>  

## <a name="operations-for-tables-and-views"></a><span data-ttu-id="44f52-111">資料表和檢視表的作業</span><span class="sxs-lookup"><span data-stu-id="44f52-111">Operations for tables and views</span></span>  
 <span data-ttu-id="44f52-112">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料行的下列作業：</span><span class="sxs-lookup"><span data-stu-id="44f52-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces the following operations for interface tables, interface views, tables and views that contain LOB columns:</span></span>  
  
-   <span data-ttu-id="44f52-113">**Read_\<LOBColName\>**:`Read_<LOBColName>`作業會顯示介面資料表、 介面檢視、 資料表和檢視表，包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行，其中\<LOBColName\>類型 BLOB、 CLOB、 NCLOB 或 BFILE 資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="44f52-113">**Read_\<LOBColName\>**: The `Read_<LOBColName>` operation is surfaced for interface tables, interface views, tables and views that contain BLOB, CLOB, NCLOB, and BFILE columns, where \<LOBColName\> is the name of the column of type BLOB, CLOB, NCLOB or BFILE.</span></span> <span data-ttu-id="44f52-114">使用 Read_\<LOBColName\>作業中，配接器用戶端可以讀取 LOB 資料行做為資料流中的值。</span><span class="sxs-lookup"><span data-stu-id="44f52-114">By using the Read_\<LOBColName\> operation, adapter clients can read values in an LOB column as a data stream.</span></span> <span data-ttu-id="44f52-115">這項作業會接受做為參數的篩選條件字串。</span><span class="sxs-lookup"><span data-stu-id="44f52-115">This operation takes a filter string as parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44f52-116">`Read_<LOBColName>`作業設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。</span><span class="sxs-lookup"><span data-stu-id="44f52-116">The `Read_<LOBColName>` operation is designed to support input streaming of LOB data in the WCF service model.</span></span> <span data-ttu-id="44f52-117">您應該使用資料表的 Select 作業讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="44f52-117">You should use a table Select operation to read LOB data from a WCF channel model or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="44f52-118">**Update_\<LOBColName\>**:`Update_<LOBColName>`作業中會顯示介面資料表和資料表只包含 BLOB、 CLOB、 和 NCLOB 資料行，其中\<LOBColName\>的名稱資料行中的輸入 BLOB、 CLOB、 和 NCLOB。</span><span class="sxs-lookup"><span data-stu-id="44f52-118">**Update_\<LOBColName\>**: The `Update_<LOBColName>` operation is surfaced for interface tables and tables only that contain BLOB, CLOB, and NCLOB columns, where \<LOBColName\> is the name of the column of type BLOB, CLOB, and NCLOB.</span></span> <span data-ttu-id="44f52-119">使用 Update_\<LOBColName\>作業中，配接器用戶端可以更新 LOB 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="44f52-119">By using the Update_\<LOBColName\> operation, adapter clients can update values in an LOB column.</span></span> <span data-ttu-id="44f52-120">BLOB 資料類型，這項作業接受 base64binary 編碼的資料做為參數，而對於 CLOB 和 NCLOB 資料類型，這項作業會做為參數字串篩選條件。</span><span class="sxs-lookup"><span data-stu-id="44f52-120">For the BLOB data type, this operation takes base64binary encoded data as the parameter, whereas for the CLOB and NCLOB data types, this operation takes a string filter as the parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44f52-121">`Update_<LOBColName>`作業：</span><span class="sxs-lookup"><span data-stu-id="44f52-121">The `Update_<LOBColName>` operation:</span></span>  
    >   
    >  -   <span data-ttu-id="44f52-122">不支援 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="44f52-122">Is not supported for the BFILE data type.</span></span> <span data-ttu-id="44f52-123">或者，配接器用戶端可以使用更新作業。</span><span class="sxs-lookup"><span data-stu-id="44f52-123">Adapter clients can alternatively use the Update operation.</span></span> <span data-ttu-id="44f52-124">如需詳細資訊，請參閱[資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="44f52-124">For more information, see [Operations on Tables That Contain BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).</span></span>  
    > -   <span data-ttu-id="44f52-125">不會公開的介面檢視和檢視。</span><span class="sxs-lookup"><span data-stu-id="44f52-125">Is not exposed for interface views and views.</span></span>  
    > -   <span data-ttu-id="44f52-126">必須執行交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="44f52-126">Must be performed as part of a transaction.</span></span> <span data-ttu-id="44f52-127">若要確保這點， **UseAmbientTransaction**繫結屬性必須設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="44f52-127">To ensure this, the **UseAmbientTransaction** binding property must be set to **True**.</span></span> <span data-ttu-id="44f52-128">如需有關資訊**UseAmbientTransaction**繫結屬性，請參閱[Rad BizTalk Adapter for Oracle E-business Suite 繫結屬性的相關](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="44f52-128">For information about the **UseAmbientTransaction** binding property, see [Rad about the  BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44f52-129">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]介面`Read_<LOBColName>`和`Update_<LOBColName>`資料表中每一個 LOB 資料行的作業。</span><span class="sxs-lookup"><span data-stu-id="44f52-129">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces a `Read_<LOBColName>` and an `Update_<LOBColName>` operation for each LOB column in a table.</span></span> <span data-ttu-id="44f52-130">因此，如果資料表 （LOBCol1 和 LOBCol2） 中有兩個 LOB 資料行，您有兩個`Read_<LOBColName>`作業 （Read_LOBCol1 和 Read_LOBCol2） 和兩個`Update_<LOBColName>`作業 （Update_LOBCol1 和 Update_LOBCol2）。</span><span class="sxs-lookup"><span data-stu-id="44f52-130">So, if there are two LOB columns in a table (LOBCol1 and LOBCol2), you have two `Read_<LOBColName>` operations (Read_LOBCol1 and Read_LOBCol2) and two `Update_<LOBColName>` operations (Update_LOBCol1 and Update_LOBCol2).</span></span>  
  
## <a name="more-good-info"></a><span data-ttu-id="44f52-131">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="44f52-131">More good info</span></span>  
  
-   <span data-ttu-id="44f52-132">叫用`Read_<LOBColName>`和`Update_<LOBColName>`在 Oracle E-business Suite 中使用基礎資料庫中資料表上的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[大型資料類型使用 BizTalk Server 之資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="44f52-132">Invoking the `Read_<LOBColName>` and `Update_<LOBColName>` operations on a table in the underlying database in Oracle E-Business Suite using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Operations on Tables with Large Data Types Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="44f52-133">訊息結構和 SOAP 動作來執行`Read_<LOBColName>`和`Update_<LOBColName>`作業，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)。</span><span class="sxs-lookup"><span data-stu-id="44f52-133">Message structure and SOAP actions for performing `Read_<LOBColName>` and `Update_<LOBColName>` operations, see [Message Schemas for Special LOB Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f52-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="44f52-134">See Also</span></span>  
 <span data-ttu-id="44f52-135">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="44f52-135">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>