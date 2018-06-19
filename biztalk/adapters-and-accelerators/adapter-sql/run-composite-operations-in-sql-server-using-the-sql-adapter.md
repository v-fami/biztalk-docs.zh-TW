---
title: 使用 SQL 配接器的 SQL Server 中執行複合操作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 906c6352-44f3-4624-9e32-aea3fbb7510d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36a1ff6e4b2c7d4d56855ce1531f99cd490a2a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223326"
---
# <a name="run-composite-operations-in-sql-server--using-the-sql-adapter"></a><span data-ttu-id="28054-102">使用 SQL 配接器的 SQL Server 中執行複合操作</span><span class="sxs-lookup"><span data-stu-id="28054-102">Run composite operations in SQL Server  using the SQL adapter</span></span>
<span data-ttu-id="28054-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓配接器用戶端執行複合操作上的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="28054-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] enables adapter clients to perform composite operations on the SQL Server database.</span></span> <span data-ttu-id="28054-104">複合作業可以包含任意數目的下列作業，並以任何順序：</span><span class="sxs-lookup"><span data-stu-id="28054-104">A composite operation can include any number of the following operations, and in any order:</span></span>  
  
-   <span data-ttu-id="28054-105">上的資料表和檢視插入、 更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="28054-105">The Insert, Update, and Delete operations on the tables and views.</span></span>  
  
-   <span data-ttu-id="28054-106">顯示為配接器中的作業的預存程序。</span><span class="sxs-lookup"><span data-stu-id="28054-106">Stored procedures that are surfaced as operations in the adapter.</span></span>  
  
 <span data-ttu-id="28054-107">中的複合運算作業*必須*目標資料表和檢視表，只能在單一資料庫中的。</span><span class="sxs-lookup"><span data-stu-id="28054-107">The operations in a composite operation *must* target tables and views only in a single database.</span></span>  
  
 <span data-ttu-id="28054-108">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="28054-108">For information about:</span></span>  
  
-   <span data-ttu-id="28054-109">如何執行複合操作中的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[SQL Server 使用 BizTalk Server 上執行複合操作](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="28054-109">How to perform composite operations in [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Composite Operations on SQL Server Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="28054-110">訊息結構描述的複合作業，請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="28054-110">Message schemas for the composite operation, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28054-111">如果有"n"中的作業數目的複合運算傳回的結果設定然後"n + 1"的連線次數作業所需的複合執行。</span><span class="sxs-lookup"><span data-stu-id="28054-111">If there are “n” number of operations in a composite operation that return a result set then “n+1” number of connections are required for the composite operation to be executed.</span></span> <span data-ttu-id="28054-112">因此，您必須確定指定的值**MaxConnectionPoolSize**繫結屬性為 n + 1 或更高。</span><span class="sxs-lookup"><span data-stu-id="28054-112">Therefore, you must ensure that the value specified for the **MaxConnectionPoolSize** binding property is n+1 or greater.</span></span> <span data-ttu-id="28054-113">如需有關**MaxConnectionPoolSize**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="28054-113">For more information about the **MaxConnectionPoolSize** binding property, see [Read about BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28054-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28054-114">See Also</span></span>  
 <span data-ttu-id="28054-115">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="28054-115">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>