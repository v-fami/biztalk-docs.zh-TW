---
title: BizTalk Adapter for SQL Server 的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e46690e-d5c4-4d6b-b7a0-9a5adf4431cd
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40d0c1fd3ce3a9f07367b7cc75ffeeb98f84b119
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222742"
---
# <a name="overview-of-biztalk-adapter-for-sql-server"></a><span data-ttu-id="6a08f-102">BizTalk Adapter for SQL Server 的概觀</span><span class="sxs-lookup"><span data-stu-id="6a08f-102">Overview of BizTalk Adapter for SQL Server</span></span>
<span data-ttu-id="6a08f-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6a08f-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the SQL Server database as a WCF service.</span></span> <span data-ttu-id="6a08f-104">配接器用戶端可以交換 SOAP 訊息的配接器，以執行 SQL Server 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="6a08f-104">Adapter clients can perform operations on the SQL Server database by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="6a08f-105">配接器會使用 SOAP 訊息，並會適當 ADO.NET 呼叫，以執行此作業。</span><span class="sxs-lookup"><span data-stu-id="6a08f-105">The adapter consumes the SOAP message and makes appropriate ADO.NET calls to perform the operation.</span></span> <span data-ttu-id="6a08f-106">配接器會傳回回應從 SQL Server 資料庫中的 SOAP 訊息形式的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6a08f-106">The adapter returns the response from the SQL Server database back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="6a08f-107">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表面的成品 （例如資料表、 檢視和程序） 的 SQL Server 資料庫中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6a08f-107">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces metadata of artifacts in the SQL Server database (such as tables, views, and procedures).</span></span>  <span data-ttu-id="6a08f-108">此中繼資料描述之表單的 Web 服務描述語言 (WSDL) 中的 SOAP 訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="6a08f-108">This metadata describes the structure of a SOAP message in the form of Web Services Description Language (WSDL).</span></span> <span data-ttu-id="6a08f-109">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6a08f-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations.</span></span> <span data-ttu-id="6a08f-110">配接器也會產生可使用的程式設計成品程式設計方案中。</span><span class="sxs-lookup"><span data-stu-id="6a08f-110">The adapter also generates programming artifacts that can be used in your programming solution.</span></span> <span data-ttu-id="6a08f-111">如需有關[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6a08f-111">For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to SQL Server in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="6a08f-112">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 ADO.NET，與 SQL Server 資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="6a08f-112">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses ADO.NET to communicate with the SQL Server database.</span></span> <span data-ttu-id="6a08f-113">您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以下列方式與 SQL Server 資料庫通訊：</span><span class="sxs-lookup"><span data-stu-id="6a08f-113">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to communicate with the SQL Server database in the following ways:</span></span>  
  
-   <span data-ttu-id="6a08f-114">開發 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a08f-114">By developing BizTalk applications.</span></span> <span data-ttu-id="6a08f-115">如需詳細資訊，請參閱[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6a08f-115">For more information, see [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="6a08f-116">使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="6a08f-116">By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model.</span></span> <span data-ttu-id="6a08f-117">如需詳細資訊，請參閱[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6a08f-117">For more information, see [Develop applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="6a08f-118">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="6a08f-118">By using the WCF channel model.</span></span> <span data-ttu-id="6a08f-119">如需詳細資訊，請參閱[開發應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6a08f-119">For more information, see [Develop applications using the WCF Channel model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a08f-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="6a08f-120">In This Section</span></span>  
  
-   [<span data-ttu-id="6a08f-121">配接器如何連接到 SQL Server？</span><span class="sxs-lookup"><span data-stu-id="6a08f-121">How Does the Adapter Connect to SQL Server?</span></span>](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [<span data-ttu-id="6a08f-122">配接器介面的 SQL Server 中繼資料的運作方式</span><span class="sxs-lookup"><span data-stu-id="6a08f-122">How Does the Adapter Surface SQL Server Metadata?</span></span>](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  <span data-ttu-id="6a08f-123">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="6a08f-123">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>  
  
-   [<span data-ttu-id="6a08f-124">SQL 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="6a08f-124">What operations are supported by the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a08f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a08f-125">See Also</span></span>  
 [<span data-ttu-id="6a08f-126">瞭解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a08f-126">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)