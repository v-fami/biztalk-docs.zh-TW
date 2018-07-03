---
title: 了解 BizTalk Adapter for SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 302a7f20-ffa2-49f1-a4c4-dd713adc23e1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea21a06ad5d87e94118aaa45e2f6f541627aae9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996928"
---
# <a name="understand-biztalk-adapter-for-sql-server"></a><span data-ttu-id="99d21-102">了解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="99d21-102">Understand BizTalk Adapter for SQL Server</span></span>
<span data-ttu-id="99d21-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計使得與外部系統互動的存取。</span><span class="sxs-lookup"><span data-stu-id="99d21-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access making it possible to interact with an external system.</span></span> <span data-ttu-id="99d21-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="99d21-104">The adapters provide the following advantages to clients:</span></span>  
  
- <span data-ttu-id="99d21-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="99d21-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="99d21-106">配接器會提供一般和方便使用的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="99d21-106">The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
- <span data-ttu-id="99d21-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="99d21-107">**Varied programming options**.</span></span> <span data-ttu-id="99d21-108">配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援的模型。</span><span class="sxs-lookup"><span data-stu-id="99d21-108">The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
- <span data-ttu-id="99d21-109">**統一的體驗，跨 Lob**。</span><span class="sxs-lookup"><span data-stu-id="99d21-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="99d21-110">使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="99d21-110">The adapters standardize on using WCF and the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
  <span data-ttu-id="99d21-111">如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。</span><span class="sxs-lookup"><span data-stu-id="99d21-111">As mentioned, the adapters are built on top of the WCF LOB Adapter SDK.</span></span> <span data-ttu-id="99d21-112">WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。</span><span class="sxs-lookup"><span data-stu-id="99d21-112">The WCF LOB Adapter SDK provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="99d21-113">WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。</span><span class="sxs-lookup"><span data-stu-id="99d21-113">The WCF LOB Adapter SDK aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="99d21-114">如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="99d21-114">For more information about the WCF LOB Adapter SDK, see [WCF LOB Adapter SDK documentation](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md).</span></span>
  
  <span data-ttu-id="99d21-115">若要執行 SQL Server 資料庫上的作業，必須可以存取相關的資料表、 程序、 檢視、 純量函數，配接器用戶端，並將其資料表值函式中。</span><span class="sxs-lookup"><span data-stu-id="99d21-115">To perform operations on a SQL Server database, adapter clients must have access to relevant tables, procedures, views, scalar functions, and table valued functions.</span></span> <span data-ttu-id="99d21-116">資料庫資料表會儲存在 SQL Server 資料庫中的基本單位。</span><span class="sxs-lookup"><span data-stu-id="99d21-116">Database tables are the basic unit of storage in the SQL Server database.</span></span> <span data-ttu-id="99d21-117">外部應用程式，都可以選取、 插入、 刪除及更新資料表的資料使用 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="99d21-117">External applications can select, insert, delete, and update data from a table by using SQL statements.</span></span> <span data-ttu-id="99d21-118">應用程式也可以使用程序、 檢視、 純量函數和資料表值函式中存取資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="99d21-118">Applications can also access data in the tables by using procedures, views, scalar functions, and table valued functions.</span></span> <span data-ttu-id="99d21-119">使用[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 檢視和 SQL Server 資料庫中的其他這類項目。</span><span class="sxs-lookup"><span data-stu-id="99d21-119">With [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], adapter clients can browse artifacts such as tables, procedures, views, and other such items in a SQL Server database.</span></span> <span data-ttu-id="99d21-120">配接器用戶端可以選取解決方案，它們需要的成品，並擷取這些構件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="99d21-120">Adapter clients can select the artifacts they require for their solution, and retrieve metadata for those artifacts.</span></span> <span data-ttu-id="99d21-121">這可讓使用者存取和 SQL Server 資料庫中執行的構件上的作業。</span><span class="sxs-lookup"><span data-stu-id="99d21-121">This enables users to access and execute the operations on the artifacts in the SQL Server database.</span></span>  
  
  <span data-ttu-id="99d21-122">本節列出的功能[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99d21-122">This section lists the features of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99d21-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="99d21-123">In This Section</span></span>  
  
-   [<span data-ttu-id="99d21-124">BizTalk Adapter for SQL Server 概觀</span><span class="sxs-lookup"><span data-stu-id="99d21-124">Overview of BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)  
  
-   [<span data-ttu-id="99d21-125">BizTalk Adapter for SQL Server 中的主要功能</span><span class="sxs-lookup"><span data-stu-id="99d21-125">Key features in BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md) 
  
-   [<span data-ttu-id="99d21-126">BizTalk Adapter for SQL Server 的限制</span><span class="sxs-lookup"><span data-stu-id="99d21-126">Limitations of BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/limitations-of-biztalk-adapter-for-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="99d21-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99d21-127">See Also</span></span>  
[<span data-ttu-id="99d21-128">開始使用 BizTalk adapter for SQL</span><span class="sxs-lookup"><span data-stu-id="99d21-128">Get started with the BizTalk adapter for SQL</span></span>](../../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)