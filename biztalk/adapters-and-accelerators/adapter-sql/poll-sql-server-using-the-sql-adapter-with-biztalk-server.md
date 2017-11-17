---
title: "與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef9a4b4-552d-4552-b318-1deab506bad9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e631a966ffee632e6c866a962c4fe47b2f1025
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-biztalk-server"></a><span data-ttu-id="271c2-102">與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="271c2-102">Poll SQL Server using the SQL Adapter with BizTalk Server</span></span>
<span data-ttu-id="271c2-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以接收來自 SQL Server 輪詢基礎資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="271c2-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server.</span></span> <span data-ttu-id="271c2-104">您可以指定執行以輪詢資料庫配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="271c2-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="271c2-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="271c2-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="271c2-106">根據接收的輪詢訊息類型，則配接器會公開輪詢的三種不同的方式：</span><span class="sxs-lookup"><span data-stu-id="271c2-106">Based on the type of polling message received, the adapter exposes three different ways of polling:</span></span>  
  
-   <span data-ttu-id="271c2-107">**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="271c2-107">**Polling**.</span></span> <span data-ttu-id="271c2-108">此操作會傳回資料集當做輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="271c2-108">This operation returns a data set as part of the polling message.</span></span> <span data-ttu-id="271c2-109">在設計階段，輪詢之資料庫物件的結構描述無法使用。</span><span class="sxs-lookup"><span data-stu-id="271c2-109">At design time, the schema of the database object being polled is not available.</span></span> <span data-ttu-id="271c2-110">相反地，會提供結構描述做為執行階段期間，輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="271c2-110">Instead, the schema is available as part of the polling message during run time.</span></span>  
  
-   <span data-ttu-id="271c2-111">**TypedPolling**。</span><span class="sxs-lookup"><span data-stu-id="271c2-111">**TypedPolling**.</span></span> <span data-ttu-id="271c2-112">此操作會傳回強型別輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="271c2-112">This operation returns a strongly-typed polling message.</span></span> <span data-ttu-id="271c2-113">在設計階段，也會提供資料庫物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="271c2-113">At design time, the schema of the database object is also available.</span></span> <span data-ttu-id="271c2-114">您必須使用這項作業輪詢，如果您想要將對應從輪詢訊息可能是針對另一項作業的另一個結構描述的特定項目。</span><span class="sxs-lookup"><span data-stu-id="271c2-114">You must use this operation for polling if you want to map certain elements from the polling message to another schema, which could be for another operation.</span></span>  
  
-   <span data-ttu-id="271c2-115">**XmlPolling**。</span><span class="sxs-lookup"><span data-stu-id="271c2-115">**XmlPolling**.</span></span> <span data-ttu-id="271c2-116">此操作會傳回做為 XML 訊息的輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="271c2-116">This operation returns the polling message as an XML message.</span></span> <span data-ttu-id="271c2-117">如果您想要使用 SELECT 陳述式或預存程序來傳回資料當做 XML 訊息中使用 FOR XML 子句，您必須使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="271c2-117">You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages.</span></span> <span data-ttu-id="271c2-118">如需 FOR XML 子句的詳細資訊，請參閱[FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx)。</span><span class="sxs-lookup"><span data-stu-id="271c2-118">For more information about the FOR XML clause, see [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx).</span></span> 
  
 <span data-ttu-id="271c2-119">如需有關這些輪詢作業的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。</span><span class="sxs-lookup"><span data-stu-id="271c2-119">For more information about these polling operations, see [Support for Polling](https://msdn.microsoft.com/library/dd788416.aspx).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="271c2-120">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端安裝相同的資料庫或資料表的多個輪詢或 TypedPolling 作業了單一 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="271c2-120">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single BizTalk application with more than one Polling or TypedPolling operations for the same database or table.</span></span> <span data-ttu-id="271c2-121">為了支援這類案例中，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="271c2-121">To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI.</span></span> <span data-ttu-id="271c2-122">當加入連接 URI，這個識別碼可唯一的藉此讓單一的 BizTalk 應用程式中的多個輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="271c2-122">This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single BizTalk application.</span></span>  
  
 <span data-ttu-id="271c2-123">本節中的主題提供有關如何使用輪詢、 TypedPolling 和 XmlPolling BizTalk 應用程式中的指示。</span><span class="sxs-lookup"><span data-stu-id="271c2-123">The topics in this section provide instructions on how to use Polling, TypedPolling, and XmlPolling in a BizTalk application.</span></span> <span data-ttu-id="271c2-124">本章節也提供有關如何使用資訊**InboundID**連接屬性。</span><span class="sxs-lookup"><span data-stu-id="271c2-124">This section also provides information about how to use the **InboundID** connection property.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="271c2-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="271c2-125">In This Section</span></span>  
  
-   [<span data-ttu-id="271c2-126">使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="271c2-126">Receive Polling-based Data-changed Messages from SQL Server by using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="271c2-127">從 SQL Server 使用 BizTalk Server 接收強型別輪詢基礎資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="271c2-127">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [<span data-ttu-id="271c2-128">使用 BizTalk Server sql 接收輪詢訊息使用 SELECT 陳述式與 FOR XML 子句</span><span class="sxs-lookup"><span data-stu-id="271c2-128">Receive Polling Messages Using SELECT Statements with FOR XML Clause from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="271c2-129">使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠</span><span class="sxs-lookup"><span data-stu-id="271c2-129">Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## <a name="see-also"></a><span data-ttu-id="271c2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="271c2-130">See Also</span></span>  
[<span data-ttu-id="271c2-131">開發 BizTalk 應用程式使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="271c2-131">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)