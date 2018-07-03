---
title: 支援複合 Operations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f65cf10-4e27-4872-bc6a-defe6cbab198
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 724d5bc41686abc3928716a0e08801107df25055
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979383"
---
# <a name="support-for-composite-operations"></a><span data-ttu-id="e49a2-102">支援複合作業</span><span class="sxs-lookup"><span data-stu-id="e49a2-102">Support for Composite Operations</span></span>
<span data-ttu-id="e49a2-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行複合作業可包含任意數目的下列作業，並依照任何順序：</span><span class="sxs-lookup"><span data-stu-id="e49a2-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:</span></span>  
  
- <span data-ttu-id="e49a2-104">選取、 插入、 更新和刪除作業的介面資料表和資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="e49a2-104">Select, Insert, Update, and Delete operations on an interface table and database table.</span></span>  
  
- <span data-ttu-id="e49a2-105">選取介面檢視和資料庫檢視上的作業。</span><span class="sxs-lookup"><span data-stu-id="e49a2-105">Select operation on an interface view and database view.</span></span>  
  
- <span data-ttu-id="e49a2-106">預存程序、 函數和內顯示為配接器中的作業的封裝的程序。</span><span class="sxs-lookup"><span data-stu-id="e49a2-106">Stored procedures, functions, and procedures within packages that are surfaced as operations in the adapter.</span></span>  
  
  <span data-ttu-id="e49a2-107">資料表和檢視表相同的資料庫或不同的資料庫中的複合運算中的作業可以為目標。</span><span class="sxs-lookup"><span data-stu-id="e49a2-107">The operations in a composite operation can target tables and views in the same database or different databases.</span></span> <span data-ttu-id="e49a2-108">不過，資料無法共用，或在複合作業中的不同作業間重複使用。</span><span class="sxs-lookup"><span data-stu-id="e49a2-108">However, data cannot be shared or reused across different operations in a composite operation.</span></span> <span data-ttu-id="e49a2-109">比方說，在複合作業中，選取作業的結果集不能用於做為輸入參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="e49a2-109">For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.</span></span>  
  
  <span data-ttu-id="e49a2-110">複合作業中的每項作業會使用個別的連接。</span><span class="sxs-lookup"><span data-stu-id="e49a2-110">Each operation in a composite operation is performed using a separate connection.</span></span> <span data-ttu-id="e49a2-111">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目及取得執行的作業，然後再釋放連接。</span><span class="sxs-lookup"><span data-stu-id="e49a2-111">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed.</span></span> <span data-ttu-id="e49a2-112">不過，複合作業的作業會傳回結果集，如果連接已釋放，才使用訊息。</span><span class="sxs-lookup"><span data-stu-id="e49a2-112">However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e49a2-113">如果您執行複合作業時遇到逾時問題則可能是因為連線的數目小於中複合作業牽涉到的作業數目：</span><span class="sxs-lookup"><span data-stu-id="e49a2-113">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
> 
> - <span data-ttu-id="e49a2-114">做為 OUT 包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 的預存程序或在 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="e49a2-114">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
>   -   <span data-ttu-id="e49a2-115">選取作業。</span><span class="sxs-lookup"><span data-stu-id="e49a2-115">Select operation.</span></span>  
> 
>   <span data-ttu-id="e49a2-116">若要解決此問題，您必須確定有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e49a2-116">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="e49a2-117">如需詳細資訊**MinPoolSize**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e49a2-117">For more information about the **MinPoolSize** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
 <span data-ttu-id="e49a2-118">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="e49a2-118">For information about:</span></span>  
  
- <span data-ttu-id="e49a2-119">如何執行中的複合作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合作業](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e49a2-119">How to perform composite operations in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see  [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="e49a2-120">訊息複合作業的結構描述，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)。</span><span class="sxs-lookup"><span data-stu-id="e49a2-120">Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e49a2-121">您也可以設定應用程式內容中的複合作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e49a2-121">You can also set the applications context for composite operations in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="e49a2-122">它是必要設定複合作業的應用程式內容，如果任一項中複合作業的作業會在介面資料表或介面檢視上執行。</span><span class="sxs-lookup"><span data-stu-id="e49a2-122">It is mandatory to set the applications context for the composite operations if any of the operations in a composite operation is performed on an interface table or interface view.</span></span> <span data-ttu-id="e49a2-123">應用程式內容，以及如何將它設定的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="e49a2-123">For information about applications context, and how to set it, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49a2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e49a2-124">See Also</span></span>  
 [<span data-ttu-id="e49a2-125">Oracle E-business Suite 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="e49a2-125">What operations are supported by the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)