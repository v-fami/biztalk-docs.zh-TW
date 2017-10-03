---
title: "SQLEXECUTE 操作 Oracle 資料庫中的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DML
- data manipulation language
- operations, DML
- SQLEXECUTE
ms.assetid: d7f881e4-c668-4f8e-b08a-ea6614b65910
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac8d5c8284e1f273d4b9aef17e79e25636dc581
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sqlexecute-operation-in-oracle-database"></a><span data-ttu-id="cea13-102">SQLEXECUTE 操作 Oracle 資料庫中</span><span class="sxs-lookup"><span data-stu-id="cea13-102">SQLEXECUTE Operation in Oracle Database</span></span>
<span data-ttu-id="cea13-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品上的作業。</span><span class="sxs-lookup"><span data-stu-id="cea13-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a standard set of operations on Oracle database artifacts.</span></span> <span data-ttu-id="cea13-104">藉由使用這些作業，您可以呼叫之類的 Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。</span><span class="sxs-lookup"><span data-stu-id="cea13-104">By using these operations, you can do things like call an Oracle function or procedure, or perform basic SQL data manipulation language (DML) operations on tables.</span></span> <span data-ttu-id="cea13-105">不過，有可能會由您的商務邏輯驅動的案例需要您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]並不會出現。</span><span class="sxs-lookup"><span data-stu-id="cea13-105">However, there may be scenarios driven by your business logic that require you to perform operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not surface.</span></span> <span data-ttu-id="cea13-106">例如，您可能想要：</span><span class="sxs-lookup"><span data-stu-id="cea13-106">For example, you may want to:</span></span>  
  
-   <span data-ttu-id="cea13-107">對資料庫成品，便不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。</span><span class="sxs-lookup"><span data-stu-id="cea13-107">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
-   <span data-ttu-id="cea13-108">執行資料定義語言作業;例如，建立資料表。</span><span class="sxs-lookup"><span data-stu-id="cea13-108">Perform data definition language operations; for example, create a table.</span></span>  
  
-   <span data-ttu-id="cea13-109">在未出現在設計階段; 資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="cea13-109">Perform operations on a database artifact that was not present at design time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
-   <span data-ttu-id="cea13-110">更複雜 DML 資料表上執行作業比作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 例如，執行查詢，包括聯結子句。</span><span class="sxs-lookup"><span data-stu-id="cea13-110">Perform more complex DML operations on tables than the operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces; for example, to perform a query that includes a JOIN clause.</span></span>  
  
 <span data-ttu-id="cea13-111">這類情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 操作。</span><span class="sxs-lookup"><span data-stu-id="cea13-111">For these kinds of scenarios, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the SQLEXECUTE operation.</span></span> <span data-ttu-id="cea13-112">SQLEXECUTE 操作中，會顯示在根節點 （/） 下**選取類別目錄**窗格[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cea13-112">The SQLEXECUTE operation is surfaced under the root node (/) in the **Select a category** pane in the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
 <span data-ttu-id="cea13-113">藉由使用 SQLEXECUTE 操作，您可以在 Oracle 資料庫上執行參數化的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cea13-113">By using the SQLEXECUTE operation, you can perform a parameterized SQL statement on the Oracle database.</span></span> <span data-ttu-id="cea13-114">SQLEXECUTE 作業支援的參數集可讓您執行相同的 SQL 陳述式，一次針對每組所組成的輸入的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="cea13-114">The SQLEXECUTE operation supports an input parameter block consisting of parameter sets that enable you to execute the same SQL statement once for each set.</span></span> <span data-ttu-id="cea13-115">SQLEXECUTE 操作傳回泛型的記錄組中的 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="cea13-115">The SQLEXECUTE operation returns the results of the SQL statement in a generic record set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cea13-116">您可以傳遞 IN 與 IN OUT 參數的程序、 函數和 SQLEXECUTE 操作中的封裝。</span><span class="sxs-lookup"><span data-stu-id="cea13-116">You can pass IN and IN OUT parameters to procedures, functions, and packages in the SQLEXECUTE operation.</span></span> <span data-ttu-id="cea13-117">叫用的成品將使用 Oracle 資料庫上提供的參數來執行不過，SQLEXECUTE 作業不會傳回的 OUT 值及 IN OUT 參數，用戶端。</span><span class="sxs-lookup"><span data-stu-id="cea13-117">The invoked artifact will execute with the supplied parameters on the Oracle database; however, the SQLEXECUTE operation does not return the value of OUT and IN OUT parameters to the client.</span></span> <span data-ttu-id="cea13-118">如果您想要叫用程序、 函數或封裝，我們建議您這麼做叫用的專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。</span><span class="sxs-lookup"><span data-stu-id="cea13-118">If you want to invoke procedures, functions, or packages, we recommend that you do so by invoking the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
 <span data-ttu-id="cea13-119">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="cea13-119">For more information about:</span></span>  
  
-   <span data-ttu-id="cea13-120">使用執行 SQLEXECUTE 操作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk server 執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cea13-120">Performing a SQLEXECUTE operation by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run SQLEXECUTE Operation by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="cea13-121">執行 SQLEXECUTE 作業使用 WCF 服務模型時，請參閱[使用 WCF 服務模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="cea13-121">Performing a SQLEXECUTE operation by using the WCF service model, see [Run SQLEXECUTE Operation by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="cea13-122">執行 SQLEXECUTE 作業所使用 WCF 通道模型，請參閱[使用 WCF 通道模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="cea13-122">Performing the SQLEXECUTE operation by using the WCF channel model, see [Run SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
-   <span data-ttu-id="cea13-123">訊息結構和執行 SQLEXECUTE 作業的 SOAP 動作，請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="cea13-123">Message structure and SOAP actions for performing a SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea13-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea13-124">See Also</span></span>  
 <span data-ttu-id="cea13-125">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="cea13-125">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>