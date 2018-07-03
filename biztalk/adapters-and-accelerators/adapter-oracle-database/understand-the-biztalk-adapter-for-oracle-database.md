---
title: 了解 BizTalk Adapter for Oracle Database |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF LOB Adapter SDK
- features of Oracle database adapter
- table
- adapter client
- service model
- WCF
- artifacts
- database tables
- adapters, features
- Windows Communication Foundation
- adapter features
- channel model
ms.assetid: a8691957-0430-4cba-83f8-b60c21a86849
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fda25d77571a3c0128317a557e5f9d15bbc472
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994615"
---
# <a name="understand-the-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="eb52a-102">了解 BizTalk Adapter for Oracle Database</span><span class="sxs-lookup"><span data-stu-id="eb52a-102">Understand the BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="eb52a-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。</span><span class="sxs-lookup"><span data-stu-id="eb52a-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="eb52a-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="eb52a-104">The adapters provide the following advantages to clients:</span></span>  
  
- <span data-ttu-id="eb52a-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="eb52a-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="eb52a-106">配接器會提供一般和方便使用的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="eb52a-106">The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
- <span data-ttu-id="eb52a-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="eb52a-107">**Varied programming options**.</span></span> <span data-ttu-id="eb52a-108">配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援的模型。</span><span class="sxs-lookup"><span data-stu-id="eb52a-108">The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
- <span data-ttu-id="eb52a-109">**統一的體驗，跨 Lob**。</span><span class="sxs-lookup"><span data-stu-id="eb52a-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="eb52a-110">使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="eb52a-110">The adapters standardize on using WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
  <span data-ttu-id="eb52a-111">如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。</span><span class="sxs-lookup"><span data-stu-id="eb52a-111">As mentioned, the adapters are built on top of the WCF LOB Adapter SDK.</span></span> <span data-ttu-id="eb52a-112">WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。</span><span class="sxs-lookup"><span data-stu-id="eb52a-112">The WCF LOB Adapter SDK provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="eb52a-113">WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。</span><span class="sxs-lookup"><span data-stu-id="eb52a-113">The WCF LOB Adapter SDK aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="eb52a-114">如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="eb52a-114">For more information about the WCF LOB Adapter SDK, see [WCF LOB Adapter SDK documentation](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md).</span></span>
  
  <span data-ttu-id="eb52a-115">若要執行的 Oracle 資料庫的作業，配接器用戶端必須存取相關的資料表、 函數和程序。</span><span class="sxs-lookup"><span data-stu-id="eb52a-115">To perform operations on an Oracle database, adapter clients must have access to relevant tables, functions, and procedures.</span></span> <span data-ttu-id="eb52a-116">資料庫資料表是 Oracle 資料庫中的儲存體的基本單位。</span><span class="sxs-lookup"><span data-stu-id="eb52a-116">Database tables are the basic unit of storage in the Oracle database.</span></span> <span data-ttu-id="eb52a-117">外部應用程式可以新增或移除資料表中的資料，使用 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb52a-117">External applications can add or remove data from a table by using SQL statements.</span></span> <span data-ttu-id="eb52a-118">應用程式也可以使用檢視、 函數和程序中存取資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="eb52a-118">Applications can also access data in the tables by using views, functions, and procedures.</span></span> <span data-ttu-id="eb52a-119">使用[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 封裝、 檢視和 Oracle 資料庫中的其他這類項目。</span><span class="sxs-lookup"><span data-stu-id="eb52a-119">With [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], adapter clients can browse the artifacts such as tables, procedures, packages, views, and other such items in an Oracle database.</span></span> <span data-ttu-id="eb52a-120">配接器用戶端可以選取的成品，它們需要解決方案，並擷取這些構件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="eb52a-120">Adapter clients can select the artifacts they require for their solution and retrieve metadata for those artifacts.</span></span> <span data-ttu-id="eb52a-121">這可讓使用者存取和 Oracle 資料庫中執行的構件上的作業。</span><span class="sxs-lookup"><span data-stu-id="eb52a-121">This enables users to access and execute the operations on the artifacts in the Oracle database.</span></span>  
  
  <span data-ttu-id="eb52a-122">本節列出的功能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb52a-122">This section lists the features of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb52a-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb52a-123">In This Section</span></span>  
  
-   [<span data-ttu-id="eb52a-124">BizTalk Adapter for Oracle Database 概觀</span><span class="sxs-lookup"><span data-stu-id="eb52a-124">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="eb52a-125">BizTalk Adapter for Oracle 資料庫中的主要功能</span><span class="sxs-lookup"><span data-stu-id="eb52a-125">Key Features in BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="eb52a-126">BizTalk Adapter for Oracle 資料庫的限制</span><span class="sxs-lookup"><span data-stu-id="eb52a-126">Limitations of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="eb52a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb52a-127">See Also</span></span>  
[<span data-ttu-id="eb52a-128">開始使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="eb52a-128">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)