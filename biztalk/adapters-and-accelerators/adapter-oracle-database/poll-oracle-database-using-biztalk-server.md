---
title: "使用 BizTalk Server 輪詢 Oracle 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2578d00518a9f1632e690e84db04426575619109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-database-using-biztalk-server"></a><span data-ttu-id="a73fa-102">使用 BizTalk Server 輪詢 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="a73fa-102">Poll Oracle Database using BizTalk Server</span></span>
<span data-ttu-id="a73fa-103">您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="a73fa-103">You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive polling-based messages from Oracle database.</span></span> <span data-ttu-id="a73fa-104">配接器會提供兩種輪詢 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="a73fa-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
-   <span data-ttu-id="a73fa-105">**使用 SELECT 陳述式**。</span><span class="sxs-lookup"><span data-stu-id="a73fa-105">**Using SELECT statements**.</span></span> <span data-ttu-id="a73fa-106">您可以指定要輪詢的資料表和檢視 Oracle 資料庫中的簡單 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a73fa-106">You can specify a simple SELECT statement to poll the tables and views in the Oracle database.</span></span> <span data-ttu-id="a73fa-107">配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="a73fa-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
-   <span data-ttu-id="a73fa-108">**使用預存程序、 函數或程序或函式，在封裝內**。</span><span class="sxs-lookup"><span data-stu-id="a73fa-108">**Using stored procedures, functions, or procedures or functions within a package**.</span></span> <span data-ttu-id="a73fa-109">您可以指定預存程序、 函數或程序或函式，以輪詢 Oracle 資料庫在封裝內。</span><span class="sxs-lookup"><span data-stu-id="a73fa-109">You can specify a stored procedure, function, or procedure or function within a package to poll the Oracle database.</span></span> <span data-ttu-id="a73fa-110">配接器指定的間隔執行的要求訊息，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="a73fa-110">The adapter executes the request message at specified intervals and returns the result to the adapter clients.</span></span>  
  
 <span data-ttu-id="a73fa-111">兩種方法中的主要差異是方式配接器用戶端指定配接器輪詢 Oracle 資料庫所使用的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="a73fa-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="a73fa-112">輪詢陳述式的第一種方法是簡單的 SELECT 陳述式，而另一種方法的輪詢陳述式是執行預存程序、 函數或程序或函式，在封裝內的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a73fa-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the other approach is a request message that executes the stored procedure, function, or procedure or function within a package.</span></span> <span data-ttu-id="a73fa-113">配接器用戶端指定輪詢陳述式，兩種方法，在**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a73fa-113">Adapter clients specify the polling statement, for either approach, in the **PollingStatement** binding property.</span></span> <span data-ttu-id="a73fa-114">如需繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a73fa-114">For more information about the binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
 <span data-ttu-id="a73fa-115">此章節的主題提供如何輪詢使用 SELECT 陳述式和預存程序、 函數或程序的指示，或在封裝內函式。</span><span class="sxs-lookup"><span data-stu-id="a73fa-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure, function, or procedure or function within a package.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a73fa-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="a73fa-116">In This Section</span></span>  
  
-   [<span data-ttu-id="a73fa-117">使用 SELECT 陳述式的輪詢 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="a73fa-117">Poll Oracle Database using the SELECT statement</span></span>](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [<span data-ttu-id="a73fa-118">使用預存程序、 函數或封裝的程序和函式的輪詢 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="a73fa-118">Poll Oracle Database Using Stored Procedures, Functions, or Packaged Procedures and Functions</span></span>](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## <a name="see-also"></a><span data-ttu-id="a73fa-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a73fa-119">See Also</span></span>  
[<span data-ttu-id="a73fa-120">開發 BizTalk 應用程式使用 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="a73fa-120">Develop BizTalk applications using the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)