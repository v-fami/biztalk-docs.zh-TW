---
title: 執行 SQL Server 使用 SQL 配接器中的資料表值函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fb8c81c-9384-4eba-b0a0-baed1782245b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dab49fa57a3132a75fd937f1d89333577d28c420
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007231"
---
# <a name="execute-table-valued-functions-in-sql-server-using-the-sql-adapter"></a><span data-ttu-id="488ce-102">執行 SQL Server 使用 SQL 配接器中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="488ce-102">Execute Table-Valued Functions in SQL Server using the SQL adapter</span></span>
<span data-ttu-id="488ce-103">SQL Server 中的 TRANSACT-SQL 和 CLR 資料表值函式當成作業[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="488ce-103">The Transact-SQL and CLR table valued functions in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="488ce-104">中的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]為相同值的資料表名稱在 SQL Server 中的函式。</span><span class="sxs-lookup"><span data-stu-id="488ce-104">The operation name in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the name of the table valued function in SQL Server.</span></span>  
  
 <span data-ttu-id="488ce-105">資料表值函式中的所有參數會都公開在對應的作業。</span><span class="sxs-lookup"><span data-stu-id="488ce-105">All the parameters in the table valued function are exposed in the corresponding operation.</span></span> <span data-ttu-id="488ce-106">如果您未指定輸入的參數是資料表值函式，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]內部叫用函數的 DEFAULT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="488ce-106">If you do not specify an input parameter for a table valued function, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] internally invokes the function using the DEFAULT keyword.</span></span> <span data-ttu-id="488ce-107">這表示資料表值函式會使用預設值，指定定義此函式時執行。</span><span class="sxs-lookup"><span data-stu-id="488ce-107">This implies that the table valued function is executed using the default value specified while defining the function.</span></span>  
  
 <span data-ttu-id="488ce-108">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="488ce-108">For more information about:</span></span>  
  
- <span data-ttu-id="488ce-109">使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]BizTalk server 叫用 SQL Server 中的資料表值函式，請參閱[Invoking Table-Valued 函式中使用 BizTalk server 的 SQL Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="488ce-109">Using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with BizTalk Server to invoke table valued functions in SQL Server, see [Invoking Table-Valued Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="488ce-110">訊息結構和資料表值函式的 SOAP 動作，請參閱[程序和函式的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="488ce-110">Message structure and SOAP actions for table valued functions, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488ce-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="488ce-111">See Also</span></span>  
 <span data-ttu-id="488ce-112">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="488ce-112">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>