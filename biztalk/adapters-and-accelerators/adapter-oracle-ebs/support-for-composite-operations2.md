---
title: "支援複合 Operations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f65cf10-4e27-4872-bc6a-defe6cbab198
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5766adec70c1a1fe7eaabe4ffaf07499e33d210c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-composite-operations"></a><span data-ttu-id="51fc4-102">複合作業的支援</span><span class="sxs-lookup"><span data-stu-id="51fc4-102">Support for Composite Operations</span></span>
<span data-ttu-id="51fc4-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行複合操作，可包含任意數目的下列作業，並以任何順序：</span><span class="sxs-lookup"><span data-stu-id="51fc4-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:</span></span>  
  
-   <span data-ttu-id="51fc4-104">Select、 Insert、 Update 和 Delete 的介面資料表和資料庫資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="51fc4-104">Select, Insert, Update, and Delete operations on an interface table and database table.</span></span>  
  
-   <span data-ttu-id="51fc4-105">選取的介面檢視和資料庫檢視上的作業。</span><span class="sxs-lookup"><span data-stu-id="51fc4-105">Select operation on an interface view and database view.</span></span>  
  
-   <span data-ttu-id="51fc4-106">預存程序、 函數和當成配接器中的作業之封裝內的程序。</span><span class="sxs-lookup"><span data-stu-id="51fc4-106">Stored procedures, functions, and procedures within packages that are surfaced as operations in the adapter.</span></span>  
  
 <span data-ttu-id="51fc4-107">資料表和檢視表中的相同資料庫或不同的資料庫，可鎖定目標的複合運算中的作業。</span><span class="sxs-lookup"><span data-stu-id="51fc4-107">The operations in a composite operation can target tables and views in the same database or different databases.</span></span> <span data-ttu-id="51fc4-108">不過，資料無法共用，或重複用在不同的作業，在複合作業。</span><span class="sxs-lookup"><span data-stu-id="51fc4-108">However, data cannot be shared or reused across different operations in a composite operation.</span></span> <span data-ttu-id="51fc4-109">比方說，在複合作業中，選取作業的結果集不能做為輸入參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="51fc4-109">For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.</span></span>  
  
 <span data-ttu-id="51fc4-110">執行複合作業中的每個作業使用個別的連接。</span><span class="sxs-lookup"><span data-stu-id="51fc4-110">Each operation in a composite operation is performed using a separate connection.</span></span> <span data-ttu-id="51fc4-111">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目和取得執行的作業，然後釋出連線。</span><span class="sxs-lookup"><span data-stu-id="51fc4-111">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed.</span></span> <span data-ttu-id="51fc4-112">不過，複合作業中的作業會傳回結果集，如果連接是之後才釋放使用訊息。</span><span class="sxs-lookup"><span data-stu-id="51fc4-112">However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51fc4-113">如果您執行複合操作時遇到逾時問題然後可能是因為連線的數目小於的複合運算涉及作業數目：</span><span class="sxs-lookup"><span data-stu-id="51fc4-113">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
>   
>  -   <span data-ttu-id="51fc4-114">預存程序包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 做為 OUT 或 IN OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="51fc4-114">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
> -   <span data-ttu-id="51fc4-115">選取作業。</span><span class="sxs-lookup"><span data-stu-id="51fc4-115">Select operation.</span></span>  
>   
>  <span data-ttu-id="51fc4-116">若要解決此問題，您必須確定是否有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。</span><span class="sxs-lookup"><span data-stu-id="51fc4-116">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="51fc4-117">如需有關**MinPoolSize**繫結屬性，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="51fc4-117">For more information about the **MinPoolSize** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
 <span data-ttu-id="51fc4-118">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="51fc4-118">For information about:</span></span>  
  
-   <span data-ttu-id="51fc4-119">如何執行複合操作中的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="51fc4-119">How to perform composite operations in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see  [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="51fc4-120">訊息結構描述的複合作業，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)。</span><span class="sxs-lookup"><span data-stu-id="51fc4-120">Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51fc4-121">您也可以設定應用程式內容中的複合作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51fc4-121">You can also set the applications context for composite operations in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="51fc4-122">它是強制設定複合操作的應用程式內容，如果介面資料表或介面檢視上執行任何作業中的複合運算。</span><span class="sxs-lookup"><span data-stu-id="51fc4-122">It is mandatory to set the applications context for the composite operations if any of the operations in a composite operation is performed on an interface table or interface view.</span></span> <span data-ttu-id="51fc4-123">應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="51fc4-123">For information about applications context, and how to set it, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fc4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fc4-124">See Also</span></span>  
 [<span data-ttu-id="51fc4-125">Oracle E-business Suite 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="51fc4-125">What operations are supported by the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)