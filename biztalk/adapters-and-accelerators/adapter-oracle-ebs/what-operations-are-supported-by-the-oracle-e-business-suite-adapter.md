---
title: Oracle E-business Suite 配接器支援哪些作業 |Microsoft Docs
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
ms.openlocfilehash: 07ad676d737fffc45898c31f68d0895fc6919b63
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984047"
---
# <a name="what-operations-are-supported-by-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="47c90-102">Oracle E-business Suite 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="47c90-102">What operations are supported by the Oracle E-Business Suite adapter</span></span>
## <a name="overview"></a><span data-ttu-id="47c90-103">概觀</span><span class="sxs-lookup"><span data-stu-id="47c90-103">Overview</span></span>
<span data-ttu-id="47c90-104">配接器用戶端可以在 Oracle E-business Suite，藉由執行作業：</span><span class="sxs-lookup"><span data-stu-id="47c90-104">Adapter clients can perform operations in Oracle E-Business Suite by:</span></span>  
  
- <span data-ttu-id="47c90-105">建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="47c90-105">Creating BizTalk projects</span></span>  
  
- <span data-ttu-id="47c90-106">使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="47c90-106">Using the WCF channel model</span></span>  
  
- <span data-ttu-id="47c90-107">使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="47c90-107">Using the WCF service model</span></span>  
  
  <span data-ttu-id="47c90-108">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開應用程式，可以在其上叫用並，它可以依次叫用應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="47c90-108">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="47c90-109">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="47c90-109">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="47c90-110">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="47c90-110">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="47c90-111">訊息結構和每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="47c90-111">For information about the message structure and the SOAP action associated with each operation, see [messages and message schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
  <span data-ttu-id="47c90-112">本章節提供支援使用 Oracle E-business Suite 作業的相關資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="47c90-112">This section provides information about the operations supported in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47c90-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="47c90-113">In this section</span></span>  
  
-   [<span data-ttu-id="47c90-114">設定應用程式內容</span><span class="sxs-lookup"><span data-stu-id="47c90-114">Set Application Context</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)  
  
-   [<span data-ttu-id="47c90-115">介面資料表和介面檢視的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-115">Operations on Interface Tables and Interface Views</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)  
  
-   [<span data-ttu-id="47c90-116">PL/SQL API 的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-116">Operations on PL/SQL APIs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-pl-sql-apis.md)  
  
-   [<span data-ttu-id="47c90-117">並行程式的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-117">Operations on Concurrent Programs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)  
  
-   [<span data-ttu-id="47c90-118">要求集的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-118">Operations on Request Sets</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)  
  
-   [<span data-ttu-id="47c90-119">介面資料表、介面檢視、資料表和包含 LOB 資料的檢視相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-119">Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)  
  
-   [<span data-ttu-id="47c90-120">包含 BFILE 資料類型的資料表相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-120">Operations on Tables That Contain BFILE Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [<span data-ttu-id="47c90-121">函式和預存程序的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-121">Operations on Functions and Stored Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)  
  
-   [<span data-ttu-id="47c90-122">函式和含有 REF CURSOR 參數之程序的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-122">Operations on Functions and Procedures with REF CURSOR Parameters</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)  
  
-   [<span data-ttu-id="47c90-123">函式和含有 RECORD 類型之程序的相關作業</span><span class="sxs-lookup"><span data-stu-id="47c90-123">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
-   [<span data-ttu-id="47c90-124">對同義字的作業</span><span class="sxs-lookup"><span data-stu-id="47c90-124">Operations on Synonyms</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)  
  
-   [<span data-ttu-id="47c90-125">接收資料庫變更通知的考量</span><span class="sxs-lookup"><span data-stu-id="47c90-125">Consideration for Receiving Database Change Notifications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="47c90-126">支援使用輪詢進行輸入呼叫</span><span class="sxs-lookup"><span data-stu-id="47c90-126">Support for Inbound Calls Using Polling</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)  
  
-   [<span data-ttu-id="47c90-127">支援 ExecuteNonQuery、ExecuteReader 和 ExecuteScalar 作業</span><span class="sxs-lookup"><span data-stu-id="47c90-127">Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)  
  
-   [<span data-ttu-id="47c90-128">支援複合作業</span><span class="sxs-lookup"><span data-stu-id="47c90-128">Support for Composite Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)  
  
-   [<span data-ttu-id="47c90-129">Oracle 使用者定義類型的支援</span><span class="sxs-lookup"><span data-stu-id="47c90-129">Support for Oracle User-Defined Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)  
  
## <a name="see-also"></a><span data-ttu-id="47c90-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c90-130">See Also</span></span>  
[<span data-ttu-id="47c90-131">了解 BizTalk Adapter for Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="47c90-131">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)