---
title: BizTalk Adapter for Oracle Database 概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, overview
- ODP.NET
- Oracle Data Provider for .NET 2.0
ms.assetid: 852b8f82-ab34-45b8-ad7f-263d719a87f9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d6629672ac1bbfdd5e0bc4e01cee37c5d71d137
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005175"
---
# <a name="overview-of-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="62947-102">BizTalk Adapter for Oracle Database 的概觀</span><span class="sxs-lookup"><span data-stu-id="62947-102">Overview of BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="62947-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開為 WCF 服務的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="62947-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes the Oracle database as a WCF service.</span></span> <span data-ttu-id="62947-104">配接器用戶端可以藉由交換的 SOAP 訊息使用配接器執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="62947-104">Adapter clients can perform operations on the Oracle database by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="62947-105">配接器會使用 WCF 訊息，並會執行作業的適當 ODP.NET 呼叫。</span><span class="sxs-lookup"><span data-stu-id="62947-105">The adapter consumes the WCF message and makes appropriate ODP.NET calls to perform the operation.</span></span> <span data-ttu-id="62947-106">配接器會傳回至用戶端的 SOAP 訊息的形式從 Oracle 資料庫的回應。</span><span class="sxs-lookup"><span data-stu-id="62947-106">The adapter returns the response from the Oracle database back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="62947-107">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表面的中繼資料 （資料表、 函數、 程序等） 的 Oracle 資料庫成品的描述結構的 SOAP 訊息中 WSDL 的形式。</span><span class="sxs-lookup"><span data-stu-id="62947-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces metadata of Oracle database artifacts (tables, functions, procedures, etc.) that describes the structure of a SOAP message in the form of WSDL.</span></span> <span data-ttu-id="62947-108">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，和[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生程式設計的成品，可以使用程式設計方案中。</span><span class="sxs-lookup"><span data-stu-id="62947-108">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], and [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.</span></span>  
  
 <span data-ttu-id="62947-109">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用 Oracle Data Provider for.NET (ODP.NET) 與 Oracle 資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="62947-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the Oracle Data Provider for .NET (ODP.NET) to communicate with the Oracle database.</span></span> <span data-ttu-id="62947-110">您可以使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與 Oracle 資料庫通訊，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="62947-110">You can use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to communicate with the Oracle database in the following ways:</span></span>  
  
- <span data-ttu-id="62947-111">開發 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62947-111">By developing BizTalk applications.</span></span> <span data-ttu-id="62947-112">請參閱[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62947-112">See [Develop your BizTalk applications](../../core/develop-your-biztalk-applications.md) for more information.</span></span>  
  
- <span data-ttu-id="62947-113">使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="62947-113">By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model.</span></span> <span data-ttu-id="62947-114">請參閱[開發的 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62947-114">See [Develop Oracle Database applications using the WCF Service model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) for more information.</span></span>  
  
- <span data-ttu-id="62947-115">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="62947-115">By using the WCF channel model.</span></span> <span data-ttu-id="62947-116">請參閱[開發的 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62947-116">See [Develop Oracle Database applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) for more information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62947-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="62947-117">In This Section</span></span>  
  
-   <span data-ttu-id="62947-118">[配接器如何連接到 Oracle 資料庫？](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="62947-118">[How Does the Adapter Connect to an Oracle Database?](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="62947-119">[配接器介面的 Oracle 中繼資料如何？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="62947-119">[How Does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="62947-120">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="62947-120">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span></span>  
  
-   [<span data-ttu-id="62947-121">配接器處理交易如何？</span><span class="sxs-lookup"><span data-stu-id="62947-121">How does the Adapter Handle Transactions?</span></span>](https://msdn.microsoft.com/library/dd788428.aspx)  
  
-   [<span data-ttu-id="62947-122">Oracle 資料庫中的 LOB 資料類型的串流支援</span><span class="sxs-lookup"><span data-stu-id="62947-122">Streaming Support for LOB Data Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)  
  
-   [<span data-ttu-id="62947-123">Oracle 資料庫配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="62947-123">What operations are supported by the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/what-operations-are-supported-by-the-oracle-database-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="62947-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62947-124">See Also</span></span>  
 [<span data-ttu-id="62947-125">瞭解 Biztalk Adapter for Oracle Database</span><span class="sxs-lookup"><span data-stu-id="62947-125">Understanding the Biztalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)