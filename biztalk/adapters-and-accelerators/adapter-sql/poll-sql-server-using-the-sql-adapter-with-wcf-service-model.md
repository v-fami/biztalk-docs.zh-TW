---
title: 使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb3bbd42c732f3377c5823831b9507bbeb0c83bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022308"
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a><span data-ttu-id="bdc96-102">使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bdc96-102">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>
<span data-ttu-id="bdc96-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從 SQL Server 接收以輪詢為基礎的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="bdc96-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server.</span></span> <span data-ttu-id="bdc96-104">您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="bdc96-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="bdc96-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="bdc96-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="bdc96-106">根據接收的輪詢訊息類型，則配接器會公開不同的輪詢作業：</span><span class="sxs-lookup"><span data-stu-id="bdc96-106">Based on the type of polling message received, the adapter exposes different polling operations:</span></span>  
  
- <span data-ttu-id="bdc96-107">**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="bdc96-107">**Polling**.</span></span> <span data-ttu-id="bdc96-108">此操作會傳回資料集當做輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="bdc96-108">This operation returns a data set as part of the polling message.</span></span>  
  
- <span data-ttu-id="bdc96-109">**TypedPolling**。</span><span class="sxs-lookup"><span data-stu-id="bdc96-109">**TypedPolling**.</span></span> <span data-ttu-id="bdc96-110">這項作業會傳回強型別輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="bdc96-110">This operation returns a strongly-typed polling message.</span></span>  
  
- <span data-ttu-id="bdc96-111">**XmlPolling**。</span><span class="sxs-lookup"><span data-stu-id="bdc96-111">**XmlPolling**.</span></span> <span data-ttu-id="bdc96-112">這項作業會傳回做為 XML 訊息的輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="bdc96-112">This operation returns the polling message as an XML message.</span></span> <span data-ttu-id="bdc96-113">如果您想要使用 SELECT 陳述式或使用 FOR XML 子句來傳回資料做為 XML 訊息的預存程序，您必須使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="bdc96-113">You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages.</span></span> <span data-ttu-id="bdc96-114">[FOR XML 子句](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="bdc96-114">[FOR XML clause](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) provides more info.</span></span> 
  
  <span data-ttu-id="bdc96-115">如需有關這些輪詢作業的詳細資訊，請參閱 <<c0> [ 在使用 SQL 配接器的 SQL Server 中輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="bdc96-115">For more information about these polling operations, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdc96-116">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有一個以上的輪詢或 TypedPolling 作業的同一個資料庫或資料表的單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="bdc96-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single application with more than one Polling or TypedPolling operations for the same database or table.</span></span> <span data-ttu-id="bdc96-117">若要支援此情況下，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="bdc96-117">To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI.</span></span> <span data-ttu-id="bdc96-118">當加入至 連線 URI，此識別碼可唯一的藉此讓單一應用程式中的多個輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="bdc96-118">This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single application.</span></span>  
  
 <span data-ttu-id="bdc96-119">在本節中的主題提供有關如何使用.NET 應用程式中輪詢和 TypedPolling 作業的指示。</span><span class="sxs-lookup"><span data-stu-id="bdc96-119">The topics in this section provide instructions on how to use both Polling and TypedPolling operations in a .NET application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdc96-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="bdc96-120">In This Section</span></span>  
  
-   [<span data-ttu-id="bdc96-121">使用 WCF 服務模型的 SQL Server 從接收以輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="bdc96-121">Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [<span data-ttu-id="bdc96-122">接收從 SQL Server 使用 WCF 服務模型的強型別輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="bdc96-122">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="bdc96-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdc96-123">See Also</span></span>  
[<span data-ttu-id="bdc96-124">開發 SQL 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="bdc96-124">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)