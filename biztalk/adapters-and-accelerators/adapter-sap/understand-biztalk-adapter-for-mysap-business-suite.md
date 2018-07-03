---
title: 了解 BizTalk Adapter for mySAP Business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter features
- adapters, features
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- features of SAP adapter
- adapters, about SAP ADO Provider
ms.assetid: 136ca828-2724-454b-9d4d-a491d45e1eda
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709833ecec71a98e0e09d2cd660b68bf5b647d8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985607"
---
# <a name="understand-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="d7d35-102">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d7d35-102">Understand BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="d7d35-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。</span><span class="sxs-lookup"><span data-stu-id="d7d35-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="d7d35-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="d7d35-104">The adapters provide the following advantages to clients:</span></span>  
  
- <span data-ttu-id="d7d35-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="d7d35-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="d7d35-106">配接器會提供瀏覽、 搜尋和擷取中繼資料的 LOB 成品的一般和方便使用的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="d7d35-106">The adapters provide a common and user-friendly design time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
- <span data-ttu-id="d7d35-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="d7d35-107">**Varied programming options**.</span></span> <span data-ttu-id="d7d35-108">配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型、 WCF 服務模型、 ADO.NET、 web 服務或 BizTalk 支援模型。</span><span class="sxs-lookup"><span data-stu-id="d7d35-108">The adapters provide a choice of programming model including Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, web services, or BizTalk supported models.</span></span>  
  
- <span data-ttu-id="d7d35-109">**統一的體驗，跨 Lob**。</span><span class="sxs-lookup"><span data-stu-id="d7d35-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="d7d35-110">使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="d7d35-110">The adapters standardize on using the WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
  <span data-ttu-id="d7d35-111">如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。</span><span class="sxs-lookup"><span data-stu-id="d7d35-111">As mentioned, the adapters are built on top of the WCF LOB Adapter SDK.</span></span> <span data-ttu-id="d7d35-112">WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。</span><span class="sxs-lookup"><span data-stu-id="d7d35-112">The WCF LOB Adapter SDK provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="d7d35-113">WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。</span><span class="sxs-lookup"><span data-stu-id="d7d35-113">The WCF LOB Adapter SDK aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="d7d35-114">如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="d7d35-114">For more information about the WCF LOB Adapter SDK, see [WCF LOB Adapter SDK documentation](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md).</span></span>
  
  <span data-ttu-id="d7d35-115">若要執行 SAP 系統上的作業，配接器用戶端必須存取相關的遠端函式呼叫 (Rfc)、 商務應用程式發展介面 (Bapi) 和 Idoc （或中繼文件）。</span><span class="sxs-lookup"><span data-stu-id="d7d35-115">To perform operations on an SAP system, adapter clients must have access to the relevant Remote Function Calls (RFCs), Business Application Programming Interfaces (BAPIs), and IDOCs (or intermediate documents).</span></span> <span data-ttu-id="d7d35-116">SAP R/3 系統會將 Rfc、 Bapi 和 Idoc 公開商務整合。</span><span class="sxs-lookup"><span data-stu-id="d7d35-116">An SAP R/3 system exposes RFCs, BAPIs, and IDOCs for business integration.</span></span> <span data-ttu-id="d7d35-117">Rfc 是實作特定的商務邏輯的遠端函式模組。</span><span class="sxs-lookup"><span data-stu-id="d7d35-117">RFCs are remote function modules that implement specific business logic.</span></span> <span data-ttu-id="d7d35-118">可以叫用此邏輯，從外部的應用程式，例如 BizTalk Server 或.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7d35-118">This logic can be invoked from an external application such as BizTalk Server or a .NET application.</span></span> <span data-ttu-id="d7d35-119">Bapi 是 SAP 商務物件，接著會透過標準的 RFC 介面公開的介面方法。</span><span class="sxs-lookup"><span data-stu-id="d7d35-119">BAPIs are method interfaces to SAP business objects, which are in turn exposed through standard RFC interfaces.</span></span> <span data-ttu-id="d7d35-120">Idoc 是抽象電子資料交換 (EDI) 的通訊層，SAP 和非 SAP 系統之間進行通訊的機制。</span><span class="sxs-lookup"><span data-stu-id="d7d35-120">IDOCs are a mechanism to abstract the electronic data interchange (EDI) communication layer for communication between SAP and non-SAP systems.</span></span> <span data-ttu-id="d7d35-121">使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]，您可以存取的 Rfc、 Bapi 和 Idoc 公開的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d7d35-121">With [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)], you can access the RFCs, BAPIs, and IDOCs exposed by an SAP system.</span></span>  
  
  <span data-ttu-id="d7d35-122">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也包含[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，可讓 SAP 系統的 ADO 介面。</span><span class="sxs-lookup"><span data-stu-id="d7d35-122">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] also includes [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], which provides an ADO interface to the SAP system.</span></span>  
  
  <span data-ttu-id="d7d35-123">此區段會列出的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]而[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d7d35-123">This section lists the features for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7d35-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="d7d35-124">In This Section</span></span>  
  
-   [<span data-ttu-id="d7d35-125">BizTalk adapter for mySAP Business Suite 的架構概觀</span><span class="sxs-lookup"><span data-stu-id="d7d35-125">Architecture overview of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [<span data-ttu-id="d7d35-126">SAP 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="d7d35-126">Key Features in the SAP Adapter</span></span>](../../adapters-and-accelerators/adapter-sap/key-features-in-the-sap-adapter.md)  
  
-   [<span data-ttu-id="d7d35-127">BizTalk Adapter for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="d7d35-127">Limitations of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/limitations-of-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [<span data-ttu-id="d7d35-128">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d7d35-128">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7d35-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7d35-129">See Also</span></span>  
[<span data-ttu-id="d7d35-130">開始使用 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d7d35-130">Get started with the BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)