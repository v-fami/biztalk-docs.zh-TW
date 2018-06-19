---
title: 開發 SQL 應用程式使用 WCF 服務模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3ecfd6f-9144-4e41-a4b8-0c768a6ac254
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645b783ad23d79b4f6be177f6d38287e62abab1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223206"
---
# <a name="develop-sql-applications-using-the-wcf-service-model"></a><span data-ttu-id="73787-102">開發 SQL 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="73787-102">Develop SQL applications using the WCF Service model</span></span>
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="73787-103">提供程式設計模型的 WCF 通道的替代方式為呼叫 WCF 服務模型程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="73787-103"> provides a programming model called the WCF service model, as an alternative to the WCF channel programming model.</span></span>  
  
 <span data-ttu-id="73787-104">WCF 服務模型會使用熟悉的.NET 開發架構，隱藏的通道上交換 SOAP 訊息複雜性。</span><span class="sxs-lookup"><span data-stu-id="73787-104">The WCF service model uses familiar .NET paradigms to hide the complexities of exchanging SOAP messages over a channel.</span></span> <span data-ttu-id="73787-105">服務模型可完成此簡化作業由讀入記憶體中的整個 SOAP 訊息，然後再將資訊複製到.NET 資料結構。</span><span class="sxs-lookup"><span data-stu-id="73787-105">The service model accomplishes this simplification by reading the entire SOAP message into memory before copying the information into .NET data structures.</span></span> <span data-ttu-id="73787-106">長訊息載入記憶體，不過，可能不適合某些應用程式。</span><span class="sxs-lookup"><span data-stu-id="73787-106">Loading long messages into memory, however, may not be practical for some applications.</span></span> <span data-ttu-id="73787-107">在這些情況下，開發人員應該使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="73787-107">In these cases, developers should use the WCF channel model.</span></span> <span data-ttu-id="73787-108">如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="73787-108">For more information about using the WCF channel model, see [Develop SQL applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).</span></span>  
  
 <span data-ttu-id="73787-109">最低層級，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]呈現在其中用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息的 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="73787-109">At the lowest level, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] presents the WCF channel model, in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints.</span></span> <span data-ttu-id="73787-110">WCF 通道模型公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。</span><span class="sxs-lookup"><span data-stu-id="73787-110">The WCF channel model exposes data types and methods that enable you to operate directly on the WCF channel architecture.</span></span> <span data-ttu-id="73787-111">WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]取用。</span><span class="sxs-lookup"><span data-stu-id="73787-111">The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] consume them.</span></span> <span data-ttu-id="73787-112">不過，建立格式正確透過通道傳送的 SOAP 訊息並驗證傳回回覆訊息可以是詳細的精確的工作。</span><span class="sxs-lookup"><span data-stu-id="73787-112">However, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.</span></span>  
  
 <span data-ttu-id="73787-113">WCF 服務模型會使用 proxy 類別，來叫用目標服務上的作業，或從用戶端接收作業。</span><span class="sxs-lookup"><span data-stu-id="73787-113">The WCF service model uses proxy classes to invoke operations on a target service or to receive operations from a client.</span></span> <span data-ttu-id="73787-114">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開為 WCF 服務，您可以在其叫用作業的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="73787-114">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the SQL Server database as a WCF service on which you can invoke operations.</span></span>  
  
-   <span data-ttu-id="73787-115">用來叫用作業的目標服務上的 proxy 類別，稱為 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="73787-115">The proxy class that is used to invoke operations on a target service is called a WCF client class.</span></span> <span data-ttu-id="73787-116">這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。</span><span class="sxs-lookup"><span data-stu-id="73787-116">This class models the operations exposed by a service as .NET methods with strongly-typed parameters.</span></span> <span data-ttu-id="73787-117">藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]為 WCF 用戶端上的.NET 方法。</span><span class="sxs-lookup"><span data-stu-id="73787-117">By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] as .NET methods on the WCF client.</span></span> <span data-ttu-id="73787-118">如需 WCF 用戶端的詳細資訊，請參閱[WCF 用戶端概觀](https://msdn.microsoft.com/library/ms735103.aspx)。</span><span class="sxs-lookup"><span data-stu-id="73787-118">For more information about WCF clients, see [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx).</span></span>
  
 <span data-ttu-id="73787-119">您可以使用下列工具來產生 WCF 用戶端類別，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開：</span><span class="sxs-lookup"><span data-stu-id="73787-119">You can use either of the following tools to generate a WCF client class and associated helper code from the service metadata that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes:</span></span>  
  
-   <span data-ttu-id="73787-120">**ServiceModel Metadata Utility Tool (svcutil.exe)**，隨附 WCF。</span><span class="sxs-lookup"><span data-stu-id="73787-120">**The ServiceModel Metadata Utility Tool (svcutil.exe)**, which ships with WCF.</span></span>  
  
-   <span data-ttu-id="73787-121">**[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** ，隨附[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以及與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗。</span><span class="sxs-lookup"><span data-stu-id="73787-121">**The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**, which ships with [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience.</span></span> <span data-ttu-id="73787-122">此工具會顯示標準 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器會公開的作業。</span><span class="sxs-lookup"><span data-stu-id="73787-122">This tool presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations that the adapter exposes.</span></span> <span data-ttu-id="73787-123">如需如何產生 WCF 用戶端應用程式的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="73787-123">For more information about how to generate a WCF client application, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
     <span data-ttu-id="73787-124">本節中的主題包含資訊、 程序和範例，以協助您建立及使用 WCF 服務模型來開發應用程式使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73787-124">The topics in this section contain information, procedures, and examples to help you create and use the WCF service model to develop applications by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73787-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="73787-125">In This Section</span></span>  
  
-   [<span data-ttu-id="73787-126">SQL 配接器的 WCF 服務模型概觀</span><span class="sxs-lookup"><span data-stu-id="73787-126">Overview of the WCF service model with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="73787-127">中繼資料和 SQL 配接器之 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="73787-127">Metadata and the WCF Service Model with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/metadata-and-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="73787-128">SQL Server 成品產生 WCF 用戶端或 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="73787-128">Generate a WCF Client or WCF Service Contract for SQL Server Artifacts</span></span>](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)  
  
-   [<span data-ttu-id="73787-129">設定 SQL 配接器的用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="73787-129">Configure a Client Binding for the SQL Adapter</span></span>](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)  
  
-   [<span data-ttu-id="73787-130">插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業</span><span class="sxs-lookup"><span data-stu-id="73787-130">Insert, update, delete, or select operations on interface tables and views using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [<span data-ttu-id="73787-131">使用 SQL 使用 WCF 服務模型中的大型資料類型執行資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="73787-131">Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)  
  
-   [<span data-ttu-id="73787-132">叫用預存程序，在 SQL 中使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="73787-132">Invoke Stored Procedures in SQL using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="73787-133">使用 WCF 服務模型來叫用 SQL Server 中的純量函式</span><span class="sxs-lookup"><span data-stu-id="73787-133">Invoke Scalar Functions in SQL Server by Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="73787-134">使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="73787-134">Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="73787-135">ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery SQL 使用 WCF 服務模型中的作業</span><span class="sxs-lookup"><span data-stu-id="73787-135">ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)  
  
-   [<span data-ttu-id="73787-136">搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="73787-136">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)  
  
-   [<span data-ttu-id="73787-137">使用 WCF 服務模型的 sql 接收查詢通知</span><span class="sxs-lookup"><span data-stu-id="73787-137">Receive Query Notifications from SQL using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="73787-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73787-138">See Also</span></span>  
[<span data-ttu-id="73787-139">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="73787-139">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)