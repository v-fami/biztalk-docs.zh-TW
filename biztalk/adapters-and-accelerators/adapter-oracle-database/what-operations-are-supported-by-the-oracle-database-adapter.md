---
title: "Oracle 資料庫配接器支援哪些作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP
- operations, performing
ms.assetid: d78dbeb8-9dab-4a71-982e-f7ada51472e8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 014b0fc6158c151d510152550c0093f6ffa9031b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-database-adapter"></a><span data-ttu-id="34825-102">Oracle 資料庫配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="34825-102">What operations are supported by the Oracle Database adapter</span></span>
<span data-ttu-id="34825-103">建立 BizTalk 專案、 使用 WCF 通道模型，或使用 WCF 服務模型，配接器用戶端可以執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="34825-103">Adapter clients can perform operations on the Oracle database by creating BizTalk projects, by using the WCF channel model, or by using the WCF service model.</span></span> <span data-ttu-id="34825-104">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="34825-104">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="34825-105">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="34825-105">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="34825-106">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="34825-106">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="34825-107">訊息結構和與每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="34825-107">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="34825-108">本節提供有關 Oracle 資料庫使用支援的作業的相關資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="34825-108">This section provides information about the operations supported on the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34825-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="34825-109">In This Section</span></span>  
  
-   [<span data-ttu-id="34825-110">執行基本 Insert、 Update、 Delete 和 Oracle 資料表和檢視表上的 Select 作業</span><span class="sxs-lookup"><span data-stu-id="34825-110">Performing Basic Insert, Update, Delete, and Select Operations on Oracle Tables and Views</span></span>](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md)  
  
-   [<span data-ttu-id="34825-111">資料表和檢視表包含 LOB 資料的作業</span><span class="sxs-lookup"><span data-stu-id="34825-111">Operations on Tables and Views That Contain LOB Data</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-112">函式和 Oracle 資料庫中的預存程序的作業</span><span class="sxs-lookup"><span data-stu-id="34825-112">Operations on Functions and Stored Procedures in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-stored-procedures-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-113">函式和 Oracle 資料庫中的 REF CURSOR 參數的程序的作業</span><span class="sxs-lookup"><span data-stu-id="34825-113">Operations on Functions and Procedures with REF CURSOR Parameters in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/ref-cursor-parameters-in-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="34825-114">函數和程序與 Oracle 資料庫中的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="34825-114">Operations on Functions and Procedures with RECORD Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-procedures-with-record-types-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-115">BFILE 資料型別之資料表上的作業</span><span class="sxs-lookup"><span data-stu-id="34825-115">Operations on Tables With BFILE Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [<span data-ttu-id="34825-116">Oracle 資料庫內的同義字上的作業</span><span class="sxs-lookup"><span data-stu-id="34825-116">Operations on Synonyms in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-117">SQLEXECUTE 操作 Oracle 資料庫中</span><span class="sxs-lookup"><span data-stu-id="34825-117">SQLEXECUTE Operation in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-118">在 Oracle 資料庫中執行複合操作</span><span class="sxs-lookup"><span data-stu-id="34825-118">Performing Composite Operations in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-119">支援 Oracle 資料庫中接收輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="34825-119">Support for Receiving Polling-based Data-changed Messages in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)  
  
-   [<span data-ttu-id="34825-120">接收資料庫變更通知使用 Oracle 資料庫配接器的考量</span><span class="sxs-lookup"><span data-stu-id="34825-120">Considerations for Receiving Database Change Notifications Using the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="34825-121">Oracle 資料庫中的 Oracle 使用者定義型別支援</span><span class="sxs-lookup"><span data-stu-id="34825-121">Support for Oracle User-Defined Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="34825-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34825-122">See Also</span></span>  
 [<span data-ttu-id="34825-123">BizTalk Adapter for Oracle 資料庫的概觀</span><span class="sxs-lookup"><span data-stu-id="34825-123">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)