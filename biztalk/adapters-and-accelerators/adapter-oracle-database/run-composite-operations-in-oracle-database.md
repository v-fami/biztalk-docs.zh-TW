---
title: Oracle 資料庫中執行複合作業 |Microsoft Docs
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
ms.openlocfilehash: bd5bc7e1454cb00b3f163ec7201de327fccbd637
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001439"
---
# <a name="run-composite-operations-in-oracle-database"></a><span data-ttu-id="35a31-102">Oracle 資料庫中執行複合作業</span><span class="sxs-lookup"><span data-stu-id="35a31-102">Run Composite Operations in Oracle Database</span></span>
<span data-ttu-id="35a31-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行複合作業可包含任意數目的下列作業，並依照任何順序：</span><span class="sxs-lookup"><span data-stu-id="35a31-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:</span></span>  
  
- <span data-ttu-id="35a31-104">選取、 插入、 更新和刪除資料表和檢視上的作業。</span><span class="sxs-lookup"><span data-stu-id="35a31-104">Select, Insert, Update, and Delete operations on tables and views.</span></span>  
  
- <span data-ttu-id="35a31-105">預存程序、 函數和程序或當成作業配接器中的封裝內的函式。</span><span class="sxs-lookup"><span data-stu-id="35a31-105">Stored procedures, functions, and procedures or functions within packages that are surfaced as operations in the adapter.</span></span>  
  
  <span data-ttu-id="35a31-106">資料表和檢視表相同的資料庫或不同的資料庫中的複合運算中的作業可以為目標。</span><span class="sxs-lookup"><span data-stu-id="35a31-106">The operations in a composite operation can target tables and views in the same database or different databases.</span></span> <span data-ttu-id="35a31-107">不過，資料無法共用，或在複合作業中的不同作業間重複使用。</span><span class="sxs-lookup"><span data-stu-id="35a31-107">However, data cannot be shared or reused across different operations in a composite operation.</span></span> <span data-ttu-id="35a31-108">比方說，在複合作業中，選取作業的結果集不能用於做為輸入參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="35a31-108">For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.</span></span>  
  
  <span data-ttu-id="35a31-109">複合作業中的每項作業會使用個別的連接。</span><span class="sxs-lookup"><span data-stu-id="35a31-109">Each operation in a composite operation is performed using a separate connection.</span></span> <span data-ttu-id="35a31-110">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目及取得執行的作業，然後再釋放連接。</span><span class="sxs-lookup"><span data-stu-id="35a31-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed.</span></span> <span data-ttu-id="35a31-111">不過，複合作業的作業會傳回結果集，如果連接已釋放，才使用訊息。</span><span class="sxs-lookup"><span data-stu-id="35a31-111">However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="35a31-112">如果您執行複合作業時遇到逾時問題則可能是因為連線的數目小於中複合作業牽涉到的作業數目：</span><span class="sxs-lookup"><span data-stu-id="35a31-112">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
> 
> - <span data-ttu-id="35a31-113">做為 OUT 包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 的預存程序或在 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="35a31-113">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
>   -   <span data-ttu-id="35a31-114">選取作業。</span><span class="sxs-lookup"><span data-stu-id="35a31-114">Select operation.</span></span>  
> 
>   <span data-ttu-id="35a31-115">若要解決此問題，您必須確定有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。</span><span class="sxs-lookup"><span data-stu-id="35a31-115">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="35a31-116">如需詳細資訊**MinPoolSize**繫結屬性，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="35a31-116">For more information about the **MinPoolSize** binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="35a31-117">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="35a31-117">For information about:</span></span>  
  
- <span data-ttu-id="35a31-118">如何執行中的複合作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[Oracle 資料庫所使用的 BizTalk Server 上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="35a31-118">How to perform composite operations in [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Composite Operations on Oracle Database by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="35a31-119">訊息複合作業的結構描述，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。</span><span class="sxs-lookup"><span data-stu-id="35a31-119">Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a31-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a31-120">See Also</span></span>  
 <span data-ttu-id="35a31-121">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="35a31-121">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>