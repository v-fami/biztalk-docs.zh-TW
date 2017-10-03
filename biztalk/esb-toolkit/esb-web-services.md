---
title: "ESB Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c122ecdd-344a-4f76-9c73-bf692d479c09
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e6f59770e14e14ed9599d0c26bae187f340e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="esb-web-services"></a><span data-ttu-id="ed83e-102">ESB Web 服務</span><span class="sxs-lookup"><span data-stu-id="ed83e-102">ESB Web Services</span></span>
<span data-ttu-id="ed83e-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="ed83e-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains the following Web services:</span></span>  
  
-   <span data-ttu-id="ed83e-104">**路線上手 Web 服務。**這些服務會接受外部的訊息，並提交訊息以供處理。</span><span class="sxs-lookup"><span data-stu-id="ed83e-104">**Itinerary On-ramp Web services.**These services accept external messages and submit the messages for processing.</span></span> <span data-ttu-id="ed83e-105">內容的行程包含中繼資料和處理指示，說明要執行哪些服務。</span><span class="sxs-lookup"><span data-stu-id="ed83e-105">The content of an itinerary contains metadata and processing instructions that describe which services to execute.</span></span> <span data-ttu-id="ed83e-106">路由服務會定義的端點的訊息應路由，雖然轉換服務指定轉換訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ed83e-106">Routing services define the endpoints to which the message should be routed, while transformation services specify how messages should be transformed.</span></span> <span data-ttu-id="ed83e-107">這些服務支援單向和雙向 （要求-回應） 處理。ASMX 和 Windows Communication Foundation (WCF) 實作所提供。</span><span class="sxs-lookup"><span data-stu-id="ed83e-107">These services support both one-way and two-way (request-response) processing; both ASMX and Windows Communication Foundation (WCF) implementations are provided.</span></span> <span data-ttu-id="ed83e-108">行程上手 Web 服務不是訊息類型特有的因此可接受任何訊息類型。</span><span class="sxs-lookup"><span data-stu-id="ed83e-108">The Itinerary On-ramp Web services are not message type–specific, so they accept any message type.</span></span>  
  
-   <span data-ttu-id="ed83e-109">**解析程式的 Web 服務。**此服務可讓外部應用程式呼叫 Microsoft ESB 解析程式架構，來查閱 ESB 端點解析程式 Framework 所支援的解析機制為基礎。</span><span class="sxs-lookup"><span data-stu-id="ed83e-109">**Resolver Web service.**This service allows external applications to call the Microsoft ESB Resolver Framework to look up ESB endpoints based on resolution mechanisms supported by the Resolver Framework.</span></span> <span data-ttu-id="ed83e-110">服務也提供 ASMX 和 WCF 實作。</span><span class="sxs-lookup"><span data-stu-id="ed83e-110">The service also offers both ASMX and WCF implementations.</span></span>  
  
-   <span data-ttu-id="ed83e-111">**轉換的 Web 服務。**此服務可讓執行 Microsoft BizTalk Server 對應訊息方塊的持續性，不會以 BizTalk Server 為基礎的應用程式的對應執行擴充的 BizTalk Server 功能的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ed83e-111">**Transformation Web service.**This service allows execution of Microsoft BizTalk Server maps without the overhead of Message Box persistence, extending the capability of BizTalk Server map execution to applications that are not based on BizTalk Server.</span></span> <span data-ttu-id="ed83e-112">服務提供 ASMX 和 WCF 實作。</span><span class="sxs-lookup"><span data-stu-id="ed83e-112">The service offers both ASMX and WCF implementations.</span></span>  
  
-   <span data-ttu-id="ed83e-113">**例外狀況處理的 Web 服務。**這項服務會接受來自外部來源的例外狀況訊息，並使用錯誤處理器管線的路由會正規化、 追蹤和例外狀況訊息發佈至 ESB 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="ed83e-113">**Exception Handling Web service.**This service accepts exception messages from external sources and routes using the fault processor pipeline will normalize, track, and publish the exception message to the ESB Management Portal.</span></span> <span data-ttu-id="ed83e-114">服務提供 ASMX 和 WCF 實作。</span><span class="sxs-lookup"><span data-stu-id="ed83e-114">The service offers both ASMX and WCF implementations.</span></span>  
  
-   <span data-ttu-id="ed83e-115">**UDDI Web 服務。**此服務可讓應用程式和使用者查閱根據服務名稱、 商業提供者或商務分類的端點; 它也可讓應用程式和使用者管理商務提供者服務和分類儲存在UDDI 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ed83e-115">**UDDI Web service.**This service enables applications and users to look up endpoints based on the service name, business provider, or business category; it also allows applications and users to manipulate the business providers, services, and categories stored in a UDDI repository.</span></span> <span data-ttu-id="ed83e-116">這是 ESB 管理入口網站和協力廠商提供者所使用的基礎結構服務。</span><span class="sxs-lookup"><span data-stu-id="ed83e-116">This is a key infrastructure service used by the ESB Management Portal and third-party providers.</span></span>  
  
-   <span data-ttu-id="ed83e-117">**BizTalk 作業 Web 服務。**此 ASMX 為基礎的服務會顯示有關 BizTalk Server 主控件、 協調流程、 應用程式和狀態，讓使用者和第三方，以輕鬆地查詢應用程式與主機的狀態，不論內的電腦上的位置BizTalk Server 群組。</span><span class="sxs-lookup"><span data-stu-id="ed83e-117">**BizTalk Operations Web service.**This ASMX-based service exposes information about BizTalk Server hosts, orchestration, applications, and status, enabling users and third parties to easily query for application and host status, regardless of the location of computer(s) within the BizTalk Server group.</span></span> <span data-ttu-id="ed83e-118">查詢可以包含訊息狀態和流程、 變更狀態、 目前的服務執行個體和訊息詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ed83e-118">Queries can include message status and flow, status changes, current service instances, and message details.</span></span> <span data-ttu-id="ed83e-119">也可以更新服務的接收位置。</span><span class="sxs-lookup"><span data-stu-id="ed83e-119">The service can also update receive locations.</span></span> <span data-ttu-id="ed83e-120">這是 ESB 管理入口網站和協力廠商提供者所使用的基礎結構服務。</span><span class="sxs-lookup"><span data-stu-id="ed83e-120">This is a key infrastructure service used by the ESB Management Portal and third-party providers.</span></span>  
  
 <span data-ttu-id="ed83e-121">如需有關 Web 服務的一部分[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ed83e-121">For more information about the Web services provided as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).</span></span>