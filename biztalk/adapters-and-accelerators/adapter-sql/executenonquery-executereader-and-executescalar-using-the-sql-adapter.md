---
title: 執行 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業使用 SQL 配接器 |Microsoft Docs
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
ms.openlocfilehash: 9d7374a0852c4f6689a0c092e5ddf0b11c038d6e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990319"
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a><span data-ttu-id="e6678-102">執行 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="e6678-102">Run ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations using the SQL adapter</span></span>
<span data-ttu-id="e6678-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會公開下列作業的根層級：</span><span class="sxs-lookup"><span data-stu-id="e6678-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the following operations at the root level:</span></span>  
  
- <span data-ttu-id="e6678-104">**ExecuteNonQuery**： 使用此作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果您不想設定要傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="e6678-104">**ExecuteNonQuery**: Use this operation to execute any arbitrary SQL statements in SQL Server if you do not want any result set to be returned.</span></span> <span data-ttu-id="e6678-105">您可以使用這項作業建立資料庫物件，或變更資料庫中的資料執行 INSERT、 UPDATE 或 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6678-105">You can use this operation to create database objects or change data in a database by executing UPDATE, INSERT, or DELETE statements.</span></span> <span data-ttu-id="e6678-106">這項作業的傳回值是 Int32 資料型別，以及：</span><span class="sxs-lookup"><span data-stu-id="e6678-106">The return value of this operation is of Int32 data type, and:</span></span>  
  
  -   <span data-ttu-id="e6678-107">UPDATE、 INSERT 和 DELETE 陳述式，傳回的值會是 SQL 陳述式所影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="e6678-107">For the UPDATE, INSERT, and DELETE statements, the return value is the number of rows affected by the SQL statement.</span></span>  
  
  -   <span data-ttu-id="e6678-108">對於所有其他類型的陳述式，則傳回值是 **-1**。</span><span class="sxs-lookup"><span data-stu-id="e6678-108">For all other types of statements, the return value is **-1**.</span></span>  
  
- <span data-ttu-id="e6678-109">**ExecuteReader**： 使用此作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果您想要的結果集傳回，如果有的話，為資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="e6678-109">**ExecuteReader**: Use this operation to execute any arbitrary SQL statements in SQL Server if you want the result set to be returned, if any, as an array of DataSet.</span></span> <span data-ttu-id="e6678-110">資料集的相關資訊，請參閱 < 資料集類別 >，網址[ http://go.microsoft.com/fwlink/?LinkID=196853 ](http://go.microsoft.com/fwlink/?LinkID=196853)。</span><span class="sxs-lookup"><span data-stu-id="e6678-110">For information about DataSet, see “DataSet Class” at [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).</span></span>  
  
- <span data-ttu-id="e6678-111">**ExecuteScalar**： 執行傳回單一值的 SQL Server 中的任何任意的 SQL 陳述式中使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="e6678-111">**ExecuteScalar**: Use this operation to execute any arbitrary SQL statements in SQL Server to return a single value.</span></span> <span data-ttu-id="e6678-112">這項作業只能在 SQL 陳述式所傳回的結果集第一個資料列的第一個資料行中傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e6678-112">This operation returns the value only in the first column of the first row in the result set returned by the SQL statement.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="e6678-113">ExecuteScalar 優於 ExecuteReader 是小得多 ExecuteReader 作業所傳回比較 ExecuteScalar 作業的回應訊息承載。</span><span class="sxs-lookup"><span data-stu-id="e6678-113">The advantage of ExecuteScalar over ExecuteReader is that the response message payload of the ExecuteScalar operation is much smaller compared to the one returned by the ExecuteReader operation.</span></span> <span data-ttu-id="e6678-114">因此，如果您需要只能有一個要傳回的值時，您應該使用 ExecuteScalar 代替 ExecuteReader。</span><span class="sxs-lookup"><span data-stu-id="e6678-114">Therefore, if you require only one value to be returned, you should use ExecuteScalar instead of ExecuteReader.</span></span>  
  
  <span data-ttu-id="e6678-115">您可以使用 ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar 作業執行多個 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6678-115">You can use the ExecuteNonQuery, ExecuteReader or ExecuteScalar operation to execute multiple SQL statements.</span></span>  
  
  <span data-ttu-id="e6678-116">如需有關執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業所使用的 BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="e6678-116">For more information about performing these operations using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6678-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6678-117">See Also</span></span>  
 <span data-ttu-id="e6678-118">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e6678-118">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>