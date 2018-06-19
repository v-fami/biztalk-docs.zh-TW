---
title: Oracle 資料庫中執行複合操作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b877d8e3-2016-40e8-888f-6b768021d6b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5595823fab4f25948e3d88db759ae525f62130
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215118"
---
# <a name="run-composite-operations-in-oracle-database"></a><span data-ttu-id="a7dfc-102">Oracle 資料庫中執行複合操作</span><span class="sxs-lookup"><span data-stu-id="a7dfc-102">Run Composite Operations in Oracle Database</span></span>
<span data-ttu-id="a7dfc-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行複合操作，可包含任意數目的下列作業，並以任何順序：</span><span class="sxs-lookup"><span data-stu-id="a7dfc-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:</span></span>  
  
-   <span data-ttu-id="a7dfc-104">Select、 Insert、 Update 和 Delete 資料表和檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-104">Select, Insert, Update, and Delete operations on tables and views.</span></span>  
  
-   <span data-ttu-id="a7dfc-105">預存程序、 函數和程序或當成配接器中的作業之封裝內的函式。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-105">Stored procedures, functions, and procedures or functions within packages that are surfaced as operations in the adapter.</span></span>  
  
 <span data-ttu-id="a7dfc-106">資料表和檢視表中的相同資料庫或不同的資料庫，可鎖定目標的複合運算中的作業。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-106">The operations in a composite operation can target tables and views in the same database or different databases.</span></span> <span data-ttu-id="a7dfc-107">不過，資料無法共用，或重複用在不同的作業，在複合作業。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-107">However, data cannot be shared or reused across different operations in a composite operation.</span></span> <span data-ttu-id="a7dfc-108">比方說，在複合作業中，選取作業的結果集不能做為輸入參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-108">For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.</span></span>  
  
 <span data-ttu-id="a7dfc-109">執行複合作業中的每個作業使用個別的連接。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-109">Each operation in a composite operation is performed using a separate connection.</span></span> <span data-ttu-id="a7dfc-110">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目和取得執行的作業，然後釋出連線。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed.</span></span> <span data-ttu-id="a7dfc-111">不過，複合作業中的作業會傳回結果集，如果連接是之後才釋放使用訊息。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-111">However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7dfc-112">如果您執行複合操作時遇到逾時問題然後可能是因為連線的數目小於的複合運算涉及作業數目：</span><span class="sxs-lookup"><span data-stu-id="a7dfc-112">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
>   
>  -   <span data-ttu-id="a7dfc-113">預存程序包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 做為 OUT 或 IN OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-113">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
> -   <span data-ttu-id="a7dfc-114">選取作業。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-114">Select operation.</span></span>  
>   
>  <span data-ttu-id="a7dfc-115">若要解決此問題，您必須確定是否有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-115">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="a7dfc-116">如需有關**MinPoolSize**繫結屬性，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-116">For more information about the **MinPoolSize** binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="a7dfc-117">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="a7dfc-117">For information about:</span></span>  
  
-   <span data-ttu-id="a7dfc-118">如何執行複合操作中的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-118">How to perform composite operations in [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Composite Operations on Oracle Database by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="a7dfc-119">訊息結構描述的複合作業，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dfc-119">Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dfc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7dfc-120">See Also</span></span>  
 <span data-ttu-id="a7dfc-121">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="a7dfc-121">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>