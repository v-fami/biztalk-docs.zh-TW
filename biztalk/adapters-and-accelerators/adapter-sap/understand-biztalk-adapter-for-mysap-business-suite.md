---
title: "瞭解 BizTalk Adapter for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- adapters, features
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- features of SAP adapter
- adapters, about SAP ADO Provider
ms.assetid: 136ca828-2724-454b-9d4d-a491d45e1eda
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 359bbc9d25465cf5c293d24a12ffeb698b11ab02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understand-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="bb7f6-102">瞭解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="bb7f6-102">Understand BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="bb7f6-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system.</span></span> <span data-ttu-id="bb7f6-104">配接器用戶端提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="bb7f6-104">The adapters provide the following advantages to clients:</span></span>  
  
-   <span data-ttu-id="bb7f6-105">**一致的設計階段經驗**。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-105">**Consistent design-time experience**.</span></span> <span data-ttu-id="bb7f6-106">配接器會提供瀏覽、 搜尋和擷取的 LOB 成品的中繼資料的一般和使用者易記的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-106">The adapters provide a common and user-friendly design time experience for browsing, searching, and retrieving metadata of LOB artifacts.</span></span>  
  
-   <span data-ttu-id="bb7f6-107">**各種程式設計選項**。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-107">**Varied programming options**.</span></span> <span data-ttu-id="bb7f6-108">配接器提供的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型、 WCF 服務模型、 ADO.NET、 web 服務或 BizTalk 支援模型的選擇。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-108">The adapters provide a choice of programming model including Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, web services, or BizTalk supported models.</span></span>  
  
-   <span data-ttu-id="bb7f6-109">**跨 Lob 統一經驗**。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-109">**Uniform experience across LOBs**.</span></span> <span data-ttu-id="bb7f6-110">標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-110">The adapters standardize on using the WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and hence provide a uniform experience of gaining access to any LOB system.</span></span>  
  
 <span data-ttu-id="bb7f6-111">如所述，配接器會建立最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-111">As mentioned, the adapters are built on top of the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="bb7f6-112">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-112">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume.</span></span> <span data-ttu-id="bb7f6-113">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="bb7f6-114">如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-114">For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation.</span></span> <span data-ttu-id="bb7f6-115">連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機 >: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-115">The documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.</span></span>  
  
 <span data-ttu-id="bb7f6-116">若要執行的 SAP 系統上的作業，配接器用戶端必須存取相關的遠端函式呼叫 (Rfc)、 商務應用程式發展介面 (Bapi)，和 Idoc （或中繼文件）。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-116">To perform operations on an SAP system, adapter clients must have access to the relevant Remote Function Calls (RFCs), Business Application Programming Interfaces (BAPIs), and IDOCs (or intermediate documents).</span></span> <span data-ttu-id="bb7f6-117">SAP / 3 系統公開 Rfc、 Bapi，與 Idoc 適用於商務整合。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-117">An SAP R/3 system exposes RFCs, BAPIs, and IDOCs for business integration.</span></span> <span data-ttu-id="bb7f6-118">Rfc 是實作特定的商務邏輯的遠端函式模組。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-118">RFCs are remote function modules that implement specific business logic.</span></span> <span data-ttu-id="bb7f6-119">可以叫用這個邏輯，例如 BizTalk Server 外部應用程式或.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-119">This logic can be invoked from an external application such as BizTalk Server or a .NET application.</span></span> <span data-ttu-id="bb7f6-120">Bapi 是 SAP 商務物件，又公開會透過標準的 RFC 介面方法的介面。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-120">BAPIs are method interfaces to SAP business objects, which are in turn exposed through standard RFC interfaces.</span></span> <span data-ttu-id="bb7f6-121">Idoc 是抽象的電子資料交換 (EDI) 通訊層的 SAP 和非 SAP 系統之間進行通訊的機制。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-121">IDOCs are a mechanism to abstract the electronic data interchange (EDI) communication layer for communication between SAP and non-SAP systems.</span></span> <span data-ttu-id="bb7f6-122">與[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]、 您可以存取的 Rfc Bapi，和 SAP 系統所公開的 Idoc。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-122">With [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)], you can access the RFCs, BAPIs, and IDOCs exposed by an SAP system.</span></span>  
  
 <span data-ttu-id="bb7f6-123">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也包含[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，這樣會提供 SAP 系統的 ADO 介面。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-123">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] also includes [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], which provides an ADO interface to the SAP system.</span></span>  
  
 <span data-ttu-id="bb7f6-124">此區段會列出的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb7f6-124">This section lists the features for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb7f6-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="bb7f6-125">In This Section</span></span>  
  
-   [<span data-ttu-id="bb7f6-126">BizTalk adapter for mySAP Business Suite 的架構概觀</span><span class="sxs-lookup"><span data-stu-id="bb7f6-126">Architecture overview of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [<span data-ttu-id="bb7f6-127">SAP 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="bb7f6-127">Key Features in the SAP Adapter</span></span>](../../adapters-and-accelerators/adapter-sap/key-features-in-the-sap-adapter.md)  
  
-   [<span data-ttu-id="bb7f6-128">BizTalk adapter for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="bb7f6-128">Limitations of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/limitations-of-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [<span data-ttu-id="bb7f6-129">關於.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="bb7f6-129">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb7f6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb7f6-130">See Also</span></span>  
[<span data-ttu-id="bb7f6-131">開始使用 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="bb7f6-131">Get started with the BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)