---
title: Oracle 資料庫中的 SQLEXECUTE 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DML
- data manipulation language
- operations, DML
- SQLEXECUTE
ms.assetid: d7f881e4-c668-4f8e-b08a-ea6614b65910
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfae55d12ce3b244001bf04aef48ff40b97d97a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000509"
---
# <a name="sqlexecute-operation-in-oracle-database"></a><span data-ttu-id="a8978-102">Oracle 資料庫中的 SQLEXECUTE 作業</span><span class="sxs-lookup"><span data-stu-id="a8978-102">SQLEXECUTE Operation in Oracle Database</span></span>
<span data-ttu-id="a8978-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品的作業。</span><span class="sxs-lookup"><span data-stu-id="a8978-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a standard set of operations on Oracle database artifacts.</span></span> <span data-ttu-id="a8978-104">藉由使用這些作業，您可以執行如下呼叫的動作，Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。</span><span class="sxs-lookup"><span data-stu-id="a8978-104">By using these operations, you can do things like call an Oracle function or procedure, or perform basic SQL data manipulation language (DML) operations on tables.</span></span> <span data-ttu-id="a8978-105">不過，有可能是由您的商務邏輯驅動的案例會要求您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會不會出現。</span><span class="sxs-lookup"><span data-stu-id="a8978-105">However, there may be scenarios driven by your business logic that require you to perform operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not surface.</span></span> <span data-ttu-id="a8978-106">例如，您可能想要：</span><span class="sxs-lookup"><span data-stu-id="a8978-106">For example, you may want to:</span></span>  
  
- <span data-ttu-id="a8978-107">對資料庫成品是不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。</span><span class="sxs-lookup"><span data-stu-id="a8978-107">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
- <span data-ttu-id="a8978-108">執行資料定義語言作業;例如，建立資料表。</span><span class="sxs-lookup"><span data-stu-id="a8978-108">Perform data definition language operations; for example, create a table.</span></span>  
  
- <span data-ttu-id="a8978-109">在設計階段; 沒有為資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="a8978-109">Perform operations on a database artifact that was not present at design time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
- <span data-ttu-id="a8978-110">執行資料表上更複雜的 DML 作業，作業的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 比方說，若要執行的查詢包含聯結子句。</span><span class="sxs-lookup"><span data-stu-id="a8978-110">Perform more complex DML operations on tables than the operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces; for example, to perform a query that includes a JOIN clause.</span></span>  
  
  <span data-ttu-id="a8978-111">這種情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="a8978-111">For these kinds of scenarios, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the SQLEXECUTE operation.</span></span> <span data-ttu-id="a8978-112">SQLEXECUTE 作業時，會顯示在根節點 （/） 上，在**選取一個類別** 窗格中的[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8978-112">The SQLEXECUTE operation is surfaced under the root node (/) in the **Select a category** pane in the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
  <span data-ttu-id="a8978-113">藉由使用 SQLEXECUTE 作業，您可以執行的 Oracle 資料庫上的參數化的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a8978-113">By using the SQLEXECUTE operation, you can perform a parameterized SQL statement on the Oracle database.</span></span> <span data-ttu-id="a8978-114">SQLEXECUTE 作業支援參數集可讓您執行一次的每一組相同的 SQL 陳述式所組成的輸入的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="a8978-114">The SQLEXECUTE operation supports an input parameter block consisting of parameter sets that enable you to execute the same SQL statement once for each set.</span></span> <span data-ttu-id="a8978-115">SQLEXECUTE 作業會傳回一組標準的記錄中的 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="a8978-115">The SQLEXECUTE operation returns the results of the SQL statement in a generic record set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8978-116">您可以傳遞中及在 OUT 參數，程序、 函數和 SQLEXECUTE 作業中的封裝。</span><span class="sxs-lookup"><span data-stu-id="a8978-116">You can pass IN and IN OUT parameters to procedures, functions, and packages in the SQLEXECUTE operation.</span></span> <span data-ttu-id="a8978-117">叫用的成品將會執行以提供的 Oracle 資料庫中; 上的參數不過，在 SQLEXECUTE 作業不會傳回外的值和在 OUT 參數，用戶端。</span><span class="sxs-lookup"><span data-stu-id="a8978-117">The invoked artifact will execute with the supplied parameters on the Oracle database; however, the SQLEXECUTE operation does not return the value of OUT and IN OUT parameters to the client.</span></span> <span data-ttu-id="a8978-118">如果您想要叫用程序、 函式或套件，我們建議您這麼做叫用專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。</span><span class="sxs-lookup"><span data-stu-id="a8978-118">If you want to invoke procedures, functions, or packages, we recommend that you do so by invoking the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
 <span data-ttu-id="a8978-119">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="a8978-119">For more information about:</span></span>  
  
- <span data-ttu-id="a8978-120">使用執行 SQLEXECUTE 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 使用 BizTalk server 執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a8978-120">Performing a SQLEXECUTE operation by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run SQLEXECUTE Operation by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="a8978-121">執行 SQLEXECUTE 作業使用 WCF 服務模型，請參閱[使用 WCF 服務模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a8978-121">Performing a SQLEXECUTE operation by using the WCF service model, see [Run SQLEXECUTE Operation by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
- <span data-ttu-id="a8978-122">執行 SQLEXECUTE 作業所使用 WCF 通道模型，請參閱[使用 WCF 通道模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a8978-122">Performing the SQLEXECUTE operation by using the WCF channel model, see [Run SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
- <span data-ttu-id="a8978-123">訊息結構和執行 SQLEXECUTE 作業的 SOAP 動作，請參閱[LEXECUTE 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="a8978-123">Message structure and SOAP actions for performing a SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8978-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8978-124">See Also</span></span>  
 <span data-ttu-id="a8978-125">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="a8978-125">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>