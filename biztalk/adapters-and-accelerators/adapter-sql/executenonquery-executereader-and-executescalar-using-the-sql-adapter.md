---
title: 執行 ExecuteNonQuery、 ExecuteReader 和使用 SQL 配接器的 ExecuteScalar 作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fda0544-a028-4a95-aae6-1f6a90764c5d
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f68f4378a4d89d2a997f5a78a524e4f6bfca2c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222270"
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a><span data-ttu-id="15d2a-102">執行 ExecuteNonQuery、 ExecuteReader 和使用 SQL 配接器的 ExecuteScalar 作業</span><span class="sxs-lookup"><span data-stu-id="15d2a-102">Run ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations using the SQL adapter</span></span>
<span data-ttu-id="15d2a-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開根層級的下列作業：</span><span class="sxs-lookup"><span data-stu-id="15d2a-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the following operations at the root level:</span></span>  
  
-   <span data-ttu-id="15d2a-104">**ExecuteNonQuery**： 使用這個作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果不想讓任何結果集傳回。</span><span class="sxs-lookup"><span data-stu-id="15d2a-104">**ExecuteNonQuery**: Use this operation to execute any arbitrary SQL statements in SQL Server if you do not want any result set to be returned.</span></span> <span data-ttu-id="15d2a-105">您可以使用這項作業來建立資料庫物件或變更資料庫中的資料，藉由執行更新、 插入或刪除陳述式。</span><span class="sxs-lookup"><span data-stu-id="15d2a-105">You can use this operation to create database objects or change data in a database by executing UPDATE, INSERT, or DELETE statements.</span></span> <span data-ttu-id="15d2a-106">這項作業的傳回值屬於 Int32 資料型別，以及：</span><span class="sxs-lookup"><span data-stu-id="15d2a-106">The return value of this operation is of Int32 data type, and:</span></span>  
  
    -   <span data-ttu-id="15d2a-107">對於 INSERT、 UPDATE 和 DELETE 陳述式，傳回值會是 SQL 陳述式所影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="15d2a-107">For the UPDATE, INSERT, and DELETE statements, the return value is the number of rows affected by the SQL statement.</span></span>  
  
    -   <span data-ttu-id="15d2a-108">對於所有其他陳述式類型，則傳回值是 **-1**。</span><span class="sxs-lookup"><span data-stu-id="15d2a-108">For all other types of statements, the return value is **-1**.</span></span>  
  
-   <span data-ttu-id="15d2a-109">**ExecuteReader**： 使用 SQL Server 中執行任何任意的 SQL 陳述式，如果您想將結果集傳回，如果有的話，做為陣列的資料集的這項作業。</span><span class="sxs-lookup"><span data-stu-id="15d2a-109">**ExecuteReader**: Use this operation to execute any arbitrary SQL statements in SQL Server if you want the result set to be returned, if any, as an array of DataSet.</span></span> <span data-ttu-id="15d2a-110">資料集的相關資訊，請參閱 < 資料集類別 >，網址[http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853)。</span><span class="sxs-lookup"><span data-stu-id="15d2a-110">For information about DataSet, see “DataSet Class” at [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).</span></span>  
  
-   <span data-ttu-id="15d2a-111">**ExecuteScalar**： 執行傳回單一值的 SQL Server 中的任何任意的 SQL 陳述式中使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="15d2a-111">**ExecuteScalar**: Use this operation to execute any arbitrary SQL statements in SQL Server to return a single value.</span></span> <span data-ttu-id="15d2a-112">這項作業只能在 SQL 陳述式所傳回的結果集第一個資料列的第一個資料行中傳回的值。</span><span class="sxs-lookup"><span data-stu-id="15d2a-112">This operation returns the value only in the first column of the first row in the result set returned by the SQL statement.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15d2a-113">ExecuteScalar 優於 ExecuteReader 是較小 ExecuteReader 作業所傳回比較 ExecuteScalar 作業的回應訊息裝載。</span><span class="sxs-lookup"><span data-stu-id="15d2a-113">The advantage of ExecuteScalar over ExecuteReader is that the response message payload of the ExecuteScalar operation is much smaller compared to the one returned by the ExecuteReader operation.</span></span> <span data-ttu-id="15d2a-114">因此，如果您需要傳回只有一個值，您應該使用 ExecuteScalar 而不是 ExecuteReader。</span><span class="sxs-lookup"><span data-stu-id="15d2a-114">Therefore, if you require only one value to be returned, you should use ExecuteScalar instead of ExecuteReader.</span></span>  
  
 <span data-ttu-id="15d2a-115">您可以使用 ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar 作業來執行多個 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="15d2a-115">You can use the ExecuteNonQuery, ExecuteReader or ExecuteScalar operation to execute multiple SQL statements.</span></span>  
  
 <span data-ttu-id="15d2a-116">如需有關執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk server 的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="15d2a-116">For more information about performing these operations using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d2a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15d2a-117">See Also</span></span>  
 <span data-ttu-id="15d2a-118">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="15d2a-118">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>