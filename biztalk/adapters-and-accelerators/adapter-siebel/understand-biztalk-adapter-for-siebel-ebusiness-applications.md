---
title: "瞭解 BizTalk Adapter for Siebel eBusiness 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- features of Siebel adapters
- adapters, features
- adapter, overview
ms.assetid: 3249fb74-9ca1-4b81-971d-5151a2e354fe
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51c3576df5f62a0350f85d79b603c9f1cbda8a60
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="understand-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="df5f8-102">瞭解 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="df5f8-102">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="df5f8-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。</span><span class="sxs-lookup"><span data-stu-id="df5f8-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="df5f8-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="df5f8-104">The adapters provide the following advantages to clients:</span></span>  
  
-   <span data-ttu-id="df5f8-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="df5f8-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="df5f8-106">配接器會提供瀏覽、 搜尋和擷取的 LOB 成品的中繼資料的一般和使用者易記的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="df5f8-106">The adapters provide a common and user-friendly design time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
-   <span data-ttu-id="df5f8-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="df5f8-107">**Varied programming options**.</span></span> <span data-ttu-id="df5f8-108">配接器會提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援模型。</span><span class="sxs-lookup"><span data-stu-id="df5f8-108">The adapters provide a choice of programming model including Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
-   <span data-ttu-id="df5f8-109">**跨 Lob 統一經驗**。</span><span class="sxs-lookup"><span data-stu-id="df5f8-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="df5f8-110">標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="df5f8-110">The adapters standardize on using the WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
 <span data-ttu-id="df5f8-111">如所述，配接器會建立最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="df5f8-111">As mentioned, the adapters are built on top of the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="df5f8-112">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。</span><span class="sxs-lookup"><span data-stu-id="df5f8-112">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="df5f8-113">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。</span><span class="sxs-lookup"><span data-stu-id="df5f8-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="df5f8-114">如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="df5f8-114">For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation.</span></span> <span data-ttu-id="df5f8-115">連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="df5f8-115">The documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive\>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.</span></span>  
  
 <span data-ttu-id="df5f8-116">若要執行 Siebel 系統上的作業，配接器用戶端必須存取 Siebel 系統所公開的商務服務。</span><span class="sxs-lookup"><span data-stu-id="df5f8-116">To perform operations on a Siebel system, adapter clients must have access to business services exposed by the Siebel system.</span></span> <span data-ttu-id="df5f8-117">Siebel 應用程式公開資料做為商務元件和商務物件。</span><span class="sxs-lookup"><span data-stu-id="df5f8-117">A Siebel application exposes data as business components and business objects.</span></span> <span data-ttu-id="df5f8-118">Siebel*商務元件*是將一或多個資料表的資料行成單一結構相關聯的邏輯實體。</span><span class="sxs-lookup"><span data-stu-id="df5f8-118">A Siebel *business component* is a logical entity that associates columns from one or more tables into a single structure.</span></span> <span data-ttu-id="df5f8-119">Siebel*商務物件*實作商務模型繫結在一起的一組相互關聯的商務元件。</span><span class="sxs-lookup"><span data-stu-id="df5f8-119">A Siebel *business object* implements a business model by tying together a set of interrelated business components.</span></span> <span data-ttu-id="df5f8-120">與[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]，配接器用戶端可以在 Siebel 商務物件和商業元件介面。</span><span class="sxs-lookup"><span data-stu-id="df5f8-120">With the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)], adapter clients can surface Siebel business objects and business components.</span></span>  
  
 <span data-ttu-id="df5f8-121">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也包含[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="df5f8-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] also includes the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span></span> <span data-ttu-id="df5f8-122">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] Siebel 系統的 ADO 介面提供延伸的 ADO.NET 介面。</span><span class="sxs-lookup"><span data-stu-id="df5f8-122">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides an ADO interface to a Siebel system by extending ADO.NET interfaces.</span></span>  
  
 <span data-ttu-id="df5f8-123">本章節將討論的功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="df5f8-123">This section discusses the features of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df5f8-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="df5f8-124">In This Section</span></span>  
  
-   [<span data-ttu-id="df5f8-125">BizTalk Adapter for Siebel eBusiness Applications 概觀</span><span class="sxs-lookup"><span data-stu-id="df5f8-125">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [<span data-ttu-id="df5f8-126">Siebel 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="df5f8-126">Key Features in the Siebel Adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [<span data-ttu-id="df5f8-127">BizTalk Adapter for Siebel eBusiness Applications 的限制</span><span class="sxs-lookup"><span data-stu-id="df5f8-127">Limitations of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [<span data-ttu-id="df5f8-128">關於 Data Provider for Siebel</span><span class="sxs-lookup"><span data-stu-id="df5f8-128">About the Data Provider for Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)