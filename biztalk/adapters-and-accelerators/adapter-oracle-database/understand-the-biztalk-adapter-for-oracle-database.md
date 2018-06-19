---
title: 瞭解 BizTalk Adapter for Oracle 資料庫 |Microsoft 文件
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
ms.openlocfilehash: bb2d3603bb6d7c64d355c88420167344f564ddd8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961172"
---
# <a name="understand-the-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="2426d-102">瞭解 BizTalk Adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="2426d-102">Understand the BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="2426d-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。</span><span class="sxs-lookup"><span data-stu-id="2426d-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="2426d-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="2426d-104">The adapters provide the following advantages to clients:</span></span>  
  
-   <span data-ttu-id="2426d-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="2426d-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="2426d-106">配接器會提供一般和使用者易記的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2426d-106">The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
-   <span data-ttu-id="2426d-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="2426d-107">**Varied programming options**.</span></span> <span data-ttu-id="2426d-108">配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援模型。</span><span class="sxs-lookup"><span data-stu-id="2426d-108">The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
-   <span data-ttu-id="2426d-109">**跨 Lob 統一經驗**。</span><span class="sxs-lookup"><span data-stu-id="2426d-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="2426d-110">標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="2426d-110">The adapters standardize on using WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
 <span data-ttu-id="2426d-111">如所述，配接器會建立最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2426d-111">As mentioned, the adapters are built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="2426d-112">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。</span><span class="sxs-lookup"><span data-stu-id="2426d-112">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="2426d-113">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。</span><span class="sxs-lookup"><span data-stu-id="2426d-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="2426d-114">如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="2426d-114">For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation.</span></span> <span data-ttu-id="2426d-115">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="2426d-115">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive\>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.</span></span>  
  
 <span data-ttu-id="2426d-116">若要執行的 Oracle 資料庫作業，配接器用戶端必須存取相關的資料表、 函數和程序。</span><span class="sxs-lookup"><span data-stu-id="2426d-116">To perform operations on an Oracle database, adapter clients must have access to relevant tables, functions, and procedures.</span></span> <span data-ttu-id="2426d-117">資料庫資料表是 Oracle 資料庫中儲存的基本單位。</span><span class="sxs-lookup"><span data-stu-id="2426d-117">Database tables are the basic unit of storage in the Oracle database.</span></span> <span data-ttu-id="2426d-118">外部應用程式可以新增或移除資料表中的資料，使用 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2426d-118">External applications can add or remove data from a table by using SQL statements.</span></span> <span data-ttu-id="2426d-119">應用程式也可以使用檢視、 函數和程序來存取資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="2426d-119">Applications can also access data in the tables by using views, functions, and procedures.</span></span> <span data-ttu-id="2426d-120">與[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 封裝、 檢視和 Oracle 資料庫中的其他這類項目。</span><span class="sxs-lookup"><span data-stu-id="2426d-120">With [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], adapter clients can browse the artifacts such as tables, procedures, packages, views, and other such items in an Oracle database.</span></span> <span data-ttu-id="2426d-121">配接器用戶端可以選取他們為其方案所需，並擷取中繼資料，這些成品的成品。</span><span class="sxs-lookup"><span data-stu-id="2426d-121">Adapter clients can select the artifacts they require for their solution and retrieve metadata for those artifacts.</span></span> <span data-ttu-id="2426d-122">這可讓使用者存取，並執行的 Oracle 資料庫中的成品上的作業。</span><span class="sxs-lookup"><span data-stu-id="2426d-122">This enables users to access and execute the operations on the artifacts in the Oracle database.</span></span>  
  
 <span data-ttu-id="2426d-123">此區段會列出的功能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2426d-123">This section lists the features of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2426d-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="2426d-124">In This Section</span></span>  
  
-   [<span data-ttu-id="2426d-125">BizTalk Adapter for Oracle Database 概觀</span><span class="sxs-lookup"><span data-stu-id="2426d-125">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="2426d-126">BizTalk Adapter for Oracle 資料庫中的重要功能</span><span class="sxs-lookup"><span data-stu-id="2426d-126">Key Features in BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [<span data-ttu-id="2426d-127">Oracle Database 的 BizTalk 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="2426d-127">Limitations of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="2426d-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="2426d-128">See Also</span></span>  
[<span data-ttu-id="2426d-129">BizTalk Server 使用者入門</span><span class="sxs-lookup"><span data-stu-id="2426d-129">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)