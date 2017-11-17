---
title: "執行 SQL Server 使用 SQL 配接器中的資料表值函式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fb8c81c-9384-4eba-b0a0-baed1782245b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69877f214a2a4b700de22ec043094510707114d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="execute-table-valued-functions-in-sql-server-using-the-sql-adapter"></a><span data-ttu-id="ac710-102">執行 SQL Server 使用 SQL 配接器中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="ac710-102">Execute Table-Valued Functions in SQL Server using the SQL adapter</span></span>
<span data-ttu-id="ac710-103">SQL Server 中的 TRANSACT-SQL 和 CLR 資料表值函式中的作業當成[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac710-103">The Transact-SQL and CLR table valued functions in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="ac710-104">中的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]值在 SQL Server 中的函式的資料表名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="ac710-104">The operation name in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the name of the table valued function in SQL Server.</span></span>  
  
 <span data-ttu-id="ac710-105">資料表值函式中的所有參數會都公開在對應的作業。</span><span class="sxs-lookup"><span data-stu-id="ac710-105">All the parameters in the table valued function are exposed in the corresponding operation.</span></span> <span data-ttu-id="ac710-106">如果您沒有指定之輸入的參數的資料表值函式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]內部叫用函數的 DEFAULT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ac710-106">If you do not specify an input parameter for a table valued function, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] internally invokes the function using the DEFAULT keyword.</span></span> <span data-ttu-id="ac710-107">這表示使用預設值，指定定義函式時執行資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="ac710-107">This implies that the table valued function is executed using the default value specified while defining the function.</span></span>  
  
 <span data-ttu-id="ac710-108">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="ac710-108">For more information about:</span></span>  
  
-   <span data-ttu-id="ac710-109">使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 BizTalk Server 叫用 SQL Server 中的資料表值函式，請參閱[Invoking Table-Valued 函式中使用 BizTalk server 的 SQL Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ac710-109">Using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with BizTalk Server to invoke table valued functions in SQL Server, see [Invoking Table-Valued Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="ac710-110">訊息結構和資料表值函式的 SOAP 動作，請參閱[訊息結構描述的程序和函式](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="ac710-110">Message structure and SOAP actions for table valued functions, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac710-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac710-111">See Also</span></span>  
 <span data-ttu-id="ac710-112">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ac710-112">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>