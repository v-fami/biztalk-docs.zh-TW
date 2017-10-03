---
title: "開發 BizTalk 應用程式使用 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5471f28e-bce1-4295-b56d-954690e60749
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9963764a298246c5a236d10b6010feee8497278f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sql-adapter"></a><span data-ttu-id="bd28d-102">開發 BizTalk 應用程式使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="bd28d-102">Develop BizTalk applications using the SQL adapter</span></span>
<span data-ttu-id="bd28d-103">建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="bd28d-103">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate XML schema.</span></span> <span data-ttu-id="bd28d-104">一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="bd28d-104">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.</span></span>  
  
 <span data-ttu-id="bd28d-105">CBR 可用在案例中傳送到 SQL Server 的訊息不需要任何大量的處理。</span><span class="sxs-lookup"><span data-stu-id="bd28d-105">CBR can be used in scenarios where the messages being sent to SQL Server do not require any intensive processing.</span></span> <span data-ttu-id="bd28d-106">例如，如果您知道接收埠將會接收僅特定類型的訊息，您可以加入篩選條件要比對傳送埠的篩選運算式的路由傳送訊息的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bd28d-106">For example, if you know that the receive port will receive messages only of a certain type, you can add a filter to the send port to route messages that match the filter expression to the send port.</span></span>  
  
 <span data-ttu-id="bd28d-107">在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd28d-107">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bd28d-108">本節提供使用 BizTalk 協調流程使用 SQL Server 上執行作業的相關資訊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd28d-108">This section provides information about using BizTalk orchestrations to perform operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="bd28d-109">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它可以與 WCF 繫結互動。</span><span class="sxs-lookup"><span data-stu-id="bd28d-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which can interact with a WCF binding.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd28d-110">若要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。</span><span class="sxs-lookup"><span data-stu-id="bd28d-110">To use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="bd28d-111">如需如何設定繫結屬性的資訊，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="bd28d-111">For information about how to set binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd28d-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="bd28d-112">In This Section</span></span>  
  
-   [<span data-ttu-id="bd28d-113">若要建立使用 SQL 配接器的 SQL 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="bd28d-113">Prerequisites to create SQL applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md) 
  
-   [<span data-ttu-id="bd28d-114">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="bd28d-114">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md) 
  
-   [<span data-ttu-id="bd28d-115">Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業</span><span class="sxs-lookup"><span data-stu-id="bd28d-115">Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="bd28d-116">使用 SQL 配接器的大型資料類型執行資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="bd28d-116">Run Operations on Tables and Views with Large Data Types using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="bd28d-117">使用 BizTalk Server 的執行 SQL Server 中的預存程序</span><span class="sxs-lookup"><span data-stu-id="bd28d-117">Execute Stored Procedures in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="bd28d-118">執行具有單一 XML 參數的預存程序</span><span class="sxs-lookup"><span data-stu-id="bd28d-118">Execute Stored Procedures With a Single XML Parameter</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)  
  
-   [<span data-ttu-id="bd28d-119">執行預存程序具有 FOR XML 子句中使用 BizTalk server 的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bd28d-119">Execute Stored Procedures Having a FOR XML Clause in SQL Server using BizTalk server</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="bd28d-120">使用 BizTalk Server 來執行 SQL Server 上的複合作業</span><span class="sxs-lookup"><span data-stu-id="bd28d-120">Run Composite Operations on SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="bd28d-121">使用 BizTalk Server 叫用 SQL Server 中的純量函式</span><span class="sxs-lookup"><span data-stu-id="bd28d-121">Invoke Scalar Functions in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="bd28d-122">使用 BizTalk Server 叫用 SQL Server 中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="bd28d-122">Invoke Table-Valued Functions in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md) 
  
-   [<span data-ttu-id="bd28d-123">使用 BizTalk Server 執行 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業</span><span class="sxs-lookup"><span data-stu-id="bd28d-123">Performing ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="bd28d-124">輪詢 SQL Server 與 BizTalk Server 使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="bd28d-124">Polling SQL Server by Using the SQL Adapter with BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)  
  
-   [<span data-ttu-id="bd28d-125">使用 BizTalk Server 接收 SQL 查詢通知</span><span class="sxs-lookup"><span data-stu-id="bd28d-125">Receive SQL Query Notifications by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd28d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd28d-126">See Also</span></span>  
[<span data-ttu-id="bd28d-127">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="bd28d-127">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)