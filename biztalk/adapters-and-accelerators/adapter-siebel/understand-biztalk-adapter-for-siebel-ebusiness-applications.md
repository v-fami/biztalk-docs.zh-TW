---
title: 了解 BizTalk Adapter for Siebel eBusiness Application |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter features
- features of Siebel adapters
- adapters, features
- adapter, overview
ms.assetid: 3249fb74-9ca1-4b81-971d-5151a2e354fe
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 788db9ba048141256cfaa3cc5017fa48bd6ec7de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999231"
---
# <a name="understand-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="f8319-102">了解 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="f8319-102">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="f8319-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。</span><span class="sxs-lookup"><span data-stu-id="f8319-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="f8319-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="f8319-104">The adapters provide the following advantages to clients:</span></span>  
  
- <span data-ttu-id="f8319-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="f8319-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="f8319-106">配接器會提供瀏覽、 搜尋和擷取中繼資料的 LOB 成品的一般和方便使用的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="f8319-106">The adapters provide a common and user-friendly design time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
- <span data-ttu-id="f8319-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="f8319-107">**Varied programming options**.</span></span> <span data-ttu-id="f8319-108">配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型中，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援的模型。</span><span class="sxs-lookup"><span data-stu-id="f8319-108">The adapters provide a choice of programming model including Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.</span></span>  
  
- <span data-ttu-id="f8319-109">**統一的體驗，跨 Lob**。</span><span class="sxs-lookup"><span data-stu-id="f8319-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="f8319-110">使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="f8319-110">The adapters standardize on using the WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
  <span data-ttu-id="f8319-111">如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。</span><span class="sxs-lookup"><span data-stu-id="f8319-111">As mentioned, the adapters are built on top of the WCF LOB Adapter SDK.</span></span> <span data-ttu-id="f8319-112">WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。</span><span class="sxs-lookup"><span data-stu-id="f8319-112">The WCF LOB Adapter SDK provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="f8319-113">WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。</span><span class="sxs-lookup"><span data-stu-id="f8319-113">The WCF LOB Adapter SDK aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="f8319-114">如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="f8319-114">For more information about the WCF LOB Adapter SDK, see [WCF LOB Adapter SDK documentation](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md).</span></span>
  
  <span data-ttu-id="f8319-115">若要執行 Siebel 系統上的作業，配接器用戶端必須存取 Siebel 系統所公開的商務服務。</span><span class="sxs-lookup"><span data-stu-id="f8319-115">To perform operations on a Siebel system, adapter clients must have access to business services exposed by the Siebel system.</span></span> <span data-ttu-id="f8319-116">Siebel 應用程式公開資料做為商務元件和商務物件。</span><span class="sxs-lookup"><span data-stu-id="f8319-116">A Siebel application exposes data as business components and business objects.</span></span> <span data-ttu-id="f8319-117">Siebel*商務元件*是將一個或多個資料表的資料行成單一結構相關聯的邏輯實體。</span><span class="sxs-lookup"><span data-stu-id="f8319-117">A Siebel *business component* is a logical entity that associates columns from one or more tables into a single structure.</span></span> <span data-ttu-id="f8319-118">Siebel*商務物件*緊密結合在一起的一組相互關聯的商務元件實作的商務模型。</span><span class="sxs-lookup"><span data-stu-id="f8319-118">A Siebel *business object* implements a business model by tying together a set of interrelated business components.</span></span> <span data-ttu-id="f8319-119">使用[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]，配接器用戶端可能會出現 Siebel 商務物件和商務元件。</span><span class="sxs-lookup"><span data-stu-id="f8319-119">With the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)], adapter clients can surface Siebel business objects and business components.</span></span>  
  
  <span data-ttu-id="f8319-120">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也包含[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="f8319-120">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] also includes the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span></span> <span data-ttu-id="f8319-121">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]藉由擴充 ADO.NET 介面提供 Siebel 系統的 ADO 介面。</span><span class="sxs-lookup"><span data-stu-id="f8319-121">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides an ADO interface to a Siebel system by extending ADO.NET interfaces.</span></span>  
  
  <span data-ttu-id="f8319-122">本章節將討論的功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]而[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f8319-122">This section discusses the features of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8319-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="f8319-123">In This Section</span></span>  
  
-   [<span data-ttu-id="f8319-124">BizTalk Adapter for Siebel eBusiness Applications 概觀</span><span class="sxs-lookup"><span data-stu-id="f8319-124">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [<span data-ttu-id="f8319-125">Siebel 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="f8319-125">Key Features in the Siebel Adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [<span data-ttu-id="f8319-126">BizTalk Adapter for Siebel eBusiness Applications 的限制</span><span class="sxs-lookup"><span data-stu-id="f8319-126">Limitations of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [<span data-ttu-id="f8319-127">關於 Data Provider for Siebel</span><span class="sxs-lookup"><span data-stu-id="f8319-127">About the Data Provider for Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)