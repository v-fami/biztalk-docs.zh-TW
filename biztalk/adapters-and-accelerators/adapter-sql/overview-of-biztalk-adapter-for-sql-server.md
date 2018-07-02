---
title: BizTalk Adapter for SQL Server 概觀 |Microsoft Docs
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
ms.openlocfilehash: 12c9393504332da636de8b09cca0e76f4dfe0da6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983455"
---
# <a name="overview-of-biztalk-adapter-for-sql-server"></a><span data-ttu-id="07dad-102">BizTalk Adapter for SQL Server 概觀</span><span class="sxs-lookup"><span data-stu-id="07dad-102">Overview of BizTalk Adapter for SQL Server</span></span>
<span data-ttu-id="07dad-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07dad-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the SQL Server database as a WCF service.</span></span> <span data-ttu-id="07dad-104">配接器用戶端可以交換使用配接器的 SOAP 訊息來執行 SQL Server 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="07dad-104">Adapter clients can perform operations on the SQL Server database by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="07dad-105">配接器會使用 SOAP 訊息，並使適當的 ADO.NET 呼叫，以執行此作業。</span><span class="sxs-lookup"><span data-stu-id="07dad-105">The adapter consumes the SOAP message and makes appropriate ADO.NET calls to perform the operation.</span></span> <span data-ttu-id="07dad-106">配接器會傳回至用戶端的 SOAP 訊息的形式從 SQL Server 資料庫的回應。</span><span class="sxs-lookup"><span data-stu-id="07dad-106">The adapter returns the response from the SQL Server database back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="07dad-107">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表面的成品 （例如資料表、 檢視和程序） 的 SQL Server 資料庫中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="07dad-107">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces metadata of artifacts in the SQL Server database (such as tables, views, and procedures).</span></span>  <span data-ttu-id="07dad-108">此中繼資料描述 Web 服務描述語言 (WSDL) 格式之 SOAP 訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="07dad-108">This metadata describes the structure of a SOAP message in the form of Web Services Description Language (WSDL).</span></span> <span data-ttu-id="07dad-109">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="07dad-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations.</span></span> <span data-ttu-id="07dad-110">配接器也會產生程式設計方案程式設計可用的成品。</span><span class="sxs-lookup"><span data-stu-id="07dad-110">The adapter also generates programming artifacts that can be used in your programming solution.</span></span> <span data-ttu-id="07dad-111">如需詳細資訊[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，並[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="07dad-111">For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to SQL Server in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="07dad-112">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 ADO.NET 與 SQL Server 資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="07dad-112">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses ADO.NET to communicate with the SQL Server database.</span></span> <span data-ttu-id="07dad-113">您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以下列方式與 SQL Server 資料庫通訊：</span><span class="sxs-lookup"><span data-stu-id="07dad-113">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to communicate with the SQL Server database in the following ways:</span></span>  
  
- <span data-ttu-id="07dad-114">開發 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="07dad-114">By developing BizTalk applications.</span></span> <span data-ttu-id="07dad-115">如需詳細資訊，請參閱 <<c0> [ 開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="07dad-115">For more information, see [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).</span></span>  
  
- <span data-ttu-id="07dad-116">使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="07dad-116">By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model.</span></span> <span data-ttu-id="07dad-117">如需詳細資訊，請參閱 <<c0> [ 開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="07dad-117">For more information, see [Develop applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).</span></span>  
  
- <span data-ttu-id="07dad-118">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="07dad-118">By using the WCF channel model.</span></span> <span data-ttu-id="07dad-119">如需詳細資訊，請參閱 <<c0> [ 使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="07dad-119">For more information, see [Develop applications using the WCF Channel model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07dad-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="07dad-120">In This Section</span></span>  
  
-   [<span data-ttu-id="07dad-121">配接器如何連接到 SQL Server？</span><span class="sxs-lookup"><span data-stu-id="07dad-121">How Does the Adapter Connect to SQL Server?</span></span>](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [<span data-ttu-id="07dad-122">配接器介面的 SQL Server 中繼資料如何？</span><span class="sxs-lookup"><span data-stu-id="07dad-122">How Does the Adapter Surface SQL Server Metadata?</span></span>](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  <span data-ttu-id="07dad-123">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="07dad-123">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>  
  
-   [<span data-ttu-id="07dad-124">SQL 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="07dad-124">What operations are supported by the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="07dad-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07dad-125">See Also</span></span>  
 [<span data-ttu-id="07dad-126">了解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="07dad-126">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)