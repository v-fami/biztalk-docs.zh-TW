---
title: Oracle E-business Suite 配接器支援哪些作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64cd124a-5e7f-4ee8-85d3-f9540b25d766
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7236c21f1e298f2ccd4cbb97db481cbd3626d186
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217662"
---
# <a name="what-operations-are-supported-by-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="18519-102">Oracle E-business Suite 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="18519-102">What operations are supported by the Oracle E-Business Suite adapter</span></span>
## <a name="overview"></a><span data-ttu-id="18519-103">概觀</span><span class="sxs-lookup"><span data-stu-id="18519-103">Overview</span></span>
<span data-ttu-id="18519-104">配接器用戶端可以根據 Oracle E-business Suite 中執行作業：</span><span class="sxs-lookup"><span data-stu-id="18519-104">Adapter clients can perform operations in Oracle E-Business Suite by:</span></span>  
  
-   <span data-ttu-id="18519-105">建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="18519-105">Creating BizTalk projects</span></span>  
  
-   <span data-ttu-id="18519-106">使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="18519-106">Using the WCF channel model</span></span>  
  
-   <span data-ttu-id="18519-107">使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="18519-107">Using the WCF service model</span></span>  
  
 <span data-ttu-id="18519-108">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="18519-108">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="18519-109">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="18519-109">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="18519-110">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="18519-110">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="18519-111">訊息結構和與每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="18519-111">For information about the message structure and the SOAP action associated with each operation, see [messages and message schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
 <span data-ttu-id="18519-112">本章節提供支援在使用 Oracle E-business Suite 作業的相關資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="18519-112">This section provides information about the operations supported in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18519-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="18519-113">In this section</span></span>  
  
-   [<span data-ttu-id="18519-114">設定應用程式內容</span><span class="sxs-lookup"><span data-stu-id="18519-114">Set Application Context</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)  
  
-   [<span data-ttu-id="18519-115">介面在資料表和檢視介面上的作業</span><span class="sxs-lookup"><span data-stu-id="18519-115">Operations on Interface Tables and Interface Views</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)  
  
-   [<span data-ttu-id="18519-116">PL/SQL 應用程式開發介面作業</span><span class="sxs-lookup"><span data-stu-id="18519-116">Operations on PL/SQL APIs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-pl-sql-apis.md)  
  
-   [<span data-ttu-id="18519-117">並行程式的作業</span><span class="sxs-lookup"><span data-stu-id="18519-117">Operations on Concurrent Programs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)  
  
-   [<span data-ttu-id="18519-118">要求的作業</span><span class="sxs-lookup"><span data-stu-id="18519-118">Operations on Request Sets</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)  
  
-   [<span data-ttu-id="18519-119">介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業</span><span class="sxs-lookup"><span data-stu-id="18519-119">Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)  
  
-   [<span data-ttu-id="18519-120">資料表包含 BFILE 資料型別上的作業</span><span class="sxs-lookup"><span data-stu-id="18519-120">Operations on Tables That Contain BFILE Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [<span data-ttu-id="18519-121">函式和預存程序的作業</span><span class="sxs-lookup"><span data-stu-id="18519-121">Operations on Functions and Stored Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)  
  
-   [<span data-ttu-id="18519-122">函式和有 REF CURSOR 參數的程序的作業</span><span class="sxs-lookup"><span data-stu-id="18519-122">Operations on Functions and Procedures with REF CURSOR Parameters</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)  
  
-   [<span data-ttu-id="18519-123">函數和程序的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="18519-123">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
-   [<span data-ttu-id="18519-124">在同義字上的作業</span><span class="sxs-lookup"><span data-stu-id="18519-124">Operations on Synonyms</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)  
  
-   [<span data-ttu-id="18519-125">接收資料庫變更通知的考量</span><span class="sxs-lookup"><span data-stu-id="18519-125">Consideration for Receiving Database Change Notifications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="18519-126">使用輪詢進行傳入呼叫時的支援</span><span class="sxs-lookup"><span data-stu-id="18519-126">Support for Inbound Calls Using Polling</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)  
  
-   [<span data-ttu-id="18519-127">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的支援</span><span class="sxs-lookup"><span data-stu-id="18519-127">Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)  
  
-   [<span data-ttu-id="18519-128">複合作業的支援</span><span class="sxs-lookup"><span data-stu-id="18519-128">Support for Composite Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)  
  
-   [<span data-ttu-id="18519-129">支援的 Oracle 使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="18519-129">Support for Oracle User-Defined Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)  
  
## <a name="see-also"></a><span data-ttu-id="18519-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18519-130">See Also</span></span>  
[<span data-ttu-id="18519-131">瞭解 BizTalk Adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="18519-131">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)