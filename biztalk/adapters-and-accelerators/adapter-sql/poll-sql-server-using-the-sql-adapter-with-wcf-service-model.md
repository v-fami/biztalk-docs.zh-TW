---
title: "搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20d0ab576e5feddb0b5f3e867ca549a45bb2af97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a><span data-ttu-id="e9ccb-102">搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e9ccb-102">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>
<span data-ttu-id="e9ccb-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以接收來自 SQL Server 輪詢基礎資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server.</span></span> <span data-ttu-id="e9ccb-104">您可以指定執行以輪詢資料庫配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="e9ccb-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="e9ccb-106">根據接收的輪詢訊息類型，則配接器會公開不同的輪詢作業：</span><span class="sxs-lookup"><span data-stu-id="e9ccb-106">Based on the type of polling message received, the adapter exposes different polling operations:</span></span>  
  
-   <span data-ttu-id="e9ccb-107">**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-107">**Polling**.</span></span> <span data-ttu-id="e9ccb-108">此操作會傳回資料集當做輪詢訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-108">This operation returns a data set as part of the polling message.</span></span>  
  
-   <span data-ttu-id="e9ccb-109">**TypedPolling**。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-109">**TypedPolling**.</span></span> <span data-ttu-id="e9ccb-110">此操作會傳回強型別輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-110">This operation returns a strongly-typed polling message.</span></span>  
  
-   <span data-ttu-id="e9ccb-111">**XmlPolling**。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-111">**XmlPolling**.</span></span> <span data-ttu-id="e9ccb-112">此操作會傳回做為 XML 訊息的輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-112">This operation returns the polling message as an XML message.</span></span> <span data-ttu-id="e9ccb-113">如果您想要使用 SELECT 陳述式或預存程序來傳回資料當做 XML 訊息中使用 FOR XML 子句，您必須使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-113">You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages.</span></span> <span data-ttu-id="e9ccb-114">[FOR XML 子句](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-114">[FOR XML clause](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) provides more info.</span></span> 
  
 <span data-ttu-id="e9ccb-115">如需有關這些輪詢作業的詳細資訊，請參閱[在 SQL Server 中使用 SQL 配接器輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-115">For more information about these polling operations, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9ccb-116">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有具有相同的資料庫或資料表的多個輪詢或 TypedPolling 作業的單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single application with more than one Polling or TypedPolling operations for the same database or table.</span></span> <span data-ttu-id="e9ccb-117">為了支援這類案例中，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-117">To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI.</span></span> <span data-ttu-id="e9ccb-118">當加入連接 URI，這個識別碼可唯一的藉此讓單一應用程式中的多個輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-118">This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single application.</span></span>  
  
 <span data-ttu-id="e9ccb-119">此章節的主題提供有關如何在.NET 應用程式中使用輪詢和 TypedPolling 作業的指示。</span><span class="sxs-lookup"><span data-stu-id="e9ccb-119">The topics in this section provide instructions on how to use both Polling and TypedPolling operations in a .NET application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9ccb-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="e9ccb-120">In This Section</span></span>  
  
-   [<span data-ttu-id="e9ccb-121">從 SQL Server 使用 WCF 服務模型收到輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="e9ccb-121">Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [<span data-ttu-id="e9ccb-122">使用 WCF 服務模型的 SQL Server 從接收強型別輪詢基礎資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="e9ccb-122">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9ccb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9ccb-123">See Also</span></span>  
[<span data-ttu-id="e9ccb-124">開發 SQL 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="e9ccb-124">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)