---
title: 使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eef9a4b4-552d-4552-b318-1deab506bad9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 971de39bff2149b1b6bdb5d20d6e8b721821a8ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996439"
---
# <a name="poll-sql-server-using-the-sql-adapter-with-biztalk-server"></a><span data-ttu-id="e70c7-102">使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e70c7-102">Poll SQL Server using the SQL Adapter with BizTalk Server</span></span>
<span data-ttu-id="e70c7-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從 SQL Server 接收以輪詢為基礎的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="e70c7-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server.</span></span> <span data-ttu-id="e70c7-104">您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="e70c7-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="e70c7-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="e70c7-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="e70c7-106">根據接收的輪詢訊息類型，則配接器會公開三種不同方式用於輪詢：</span><span class="sxs-lookup"><span data-stu-id="e70c7-106">Based on the type of polling message received, the adapter exposes three different ways of polling:</span></span>  
  
- <span data-ttu-id="e70c7-107">**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="e70c7-107">**Polling**.</span></span> <span data-ttu-id="e70c7-108">此操作會傳回資料集當做輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="e70c7-108">This operation returns a data set as part of the polling message.</span></span> <span data-ttu-id="e70c7-109">在設計階段，您可能不提供要輪詢的資料庫物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e70c7-109">At design time, the schema of the database object being polled is not available.</span></span> <span data-ttu-id="e70c7-110">相反地，會提供結構描述執行階段期間，輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="e70c7-110">Instead, the schema is available as part of the polling message during run time.</span></span>  
  
- <span data-ttu-id="e70c7-111">**TypedPolling**。</span><span class="sxs-lookup"><span data-stu-id="e70c7-111">**TypedPolling**.</span></span> <span data-ttu-id="e70c7-112">這項作業會傳回強型別輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="e70c7-112">This operation returns a strongly-typed polling message.</span></span> <span data-ttu-id="e70c7-113">在設計階段，也會提供資料庫物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e70c7-113">At design time, the schema of the database object is also available.</span></span> <span data-ttu-id="e70c7-114">您必須使用這項作業輪詢，如果您想要將對應從輪詢訊息可能是另一項作業的另一個結構描述的特定項目。</span><span class="sxs-lookup"><span data-stu-id="e70c7-114">You must use this operation for polling if you want to map certain elements from the polling message to another schema, which could be for another operation.</span></span>  
  
- <span data-ttu-id="e70c7-115">**XmlPolling**。</span><span class="sxs-lookup"><span data-stu-id="e70c7-115">**XmlPolling**.</span></span> <span data-ttu-id="e70c7-116">這項作業會傳回做為 XML 訊息的輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="e70c7-116">This operation returns the polling message as an XML message.</span></span> <span data-ttu-id="e70c7-117">如果您想要使用 SELECT 陳述式或使用 FOR XML 子句來傳回資料做為 XML 訊息的預存程序，您必須使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="e70c7-117">You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages.</span></span> <span data-ttu-id="e70c7-118">如需有關 FOR XML 子句的詳細資訊，請參閱 < [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e70c7-118">For more information about the FOR XML clause, see [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx).</span></span> 
  
  <span data-ttu-id="e70c7-119">如需有關這些輪詢作業的詳細資訊，請參閱 <<c0> [ 輪詢支援](https://msdn.microsoft.com/library/dd788416.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e70c7-119">For more information about these polling operations, see [Support for Polling](https://msdn.microsoft.com/library/dd788416.aspx).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e70c7-120">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有相同的資料庫或資料表的一個以上的輪詢或 TypedPolling 作業的單一 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e70c7-120">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single BizTalk application with more than one Polling or TypedPolling operations for the same database or table.</span></span> <span data-ttu-id="e70c7-121">若要支援此情況下，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="e70c7-121">To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI.</span></span> <span data-ttu-id="e70c7-122">當加入至 連線 URI，此識別碼可唯一的藉此讓多個在單一的 BizTalk 應用程式中的輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="e70c7-122">This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single BizTalk application.</span></span>  
  
 <span data-ttu-id="e70c7-123">在本節中的主題提供有關如何使用 BizTalk 應用程式中的 輪詢、 TypedPolling 和 XmlPolling 的指示。</span><span class="sxs-lookup"><span data-stu-id="e70c7-123">The topics in this section provide instructions on how to use Polling, TypedPolling, and XmlPolling in a BizTalk application.</span></span> <span data-ttu-id="e70c7-124">本章節也提供有關如何使用資訊**InboundID**連接屬性。</span><span class="sxs-lookup"><span data-stu-id="e70c7-124">This section also provides information about how to use the **InboundID** connection property.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e70c7-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="e70c7-125">In This Section</span></span>  
  
-   [<span data-ttu-id="e70c7-126">使用 BizTalk Server 從 SQL Server 接收以輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="e70c7-126">Receive Polling-based Data-changed Messages from SQL Server by using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="e70c7-127">使用 BizTalk Server 從 SQL Server 接收強型別輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="e70c7-127">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [<span data-ttu-id="e70c7-128">從使用 BizTalk Server 的 SQL 接收輪詢訊息使用 SELECT 陳述式與 FOR XML 子句</span><span class="sxs-lookup"><span data-stu-id="e70c7-128">Receive Polling Messages Using SELECT Statements with FOR XML Clause from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="e70c7-129">從使用 BizTalk Server 的 SQL 接收輪詢訊息跨多個接收埠</span><span class="sxs-lookup"><span data-stu-id="e70c7-129">Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## <a name="see-also"></a><span data-ttu-id="e70c7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e70c7-130">See Also</span></span>  
[<span data-ttu-id="e70c7-131">使用 SQL 配接器開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e70c7-131">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)