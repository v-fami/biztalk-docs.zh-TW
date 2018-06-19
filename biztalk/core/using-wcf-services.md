---
title: 使用 WCF 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services
- Windows Communication Foundation (WCF)
ms.assetid: 34fe5e4c-6a92-4627-b2aa-e8b58a708320
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29b984bcda798796565113739c6088af6d569f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287790"
---
# <a name="using-wcf-services"></a><span data-ttu-id="1f90c-102">使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="1f90c-102">Using WCF Services</span></span>
<span data-ttu-id="1f90c-103">Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供內建支援的 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="1f90c-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Windows Communication Foundation (WCF).</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1f90c-104">可讓您重複使用和彙總所有現有的 WCF 服務協調流程中。</span><span class="sxs-lookup"><span data-stu-id="1f90c-104"> enables you to reuse and aggregate all your existing WCF services within your orchestrations.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1f90c-105">也實作 WCF 服務中原生配接器的支援。</span><span class="sxs-lookup"><span data-stu-id="1f90c-105"> also implements support for native adapters in WCF services.</span></span> <span data-ttu-id="1f90c-106">原生配接器支援為 WCF 服務提供擴充性、容錯和追蹤功能，您無須撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f90c-106">Native adapter support provides scalability, fault tolerance, and tracking capabilities for WCF services without requiring you to write code.</span></span> <span data-ttu-id="1f90c-107">WCF 配接器的相關資訊，請參閱[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="1f90c-107">For information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
 <span data-ttu-id="1f90c-108">WCF 服務中的支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]分為兩類： 發行或建立 WCF 服務，或呼叫或取用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="1f90c-108">The WCF services support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] falls into two categories: publishing or creating WCF services, or calling or consuming WCF services.</span></span>  
  
 <span data-ttu-id="1f90c-109">**發佈 WCF 服務**</span><span class="sxs-lookup"><span data-stu-id="1f90c-109">**Publishing WCF services**</span></span>  
  
 <span data-ttu-id="1f90c-110">您可以使用 WCF 配接器將協調流程和結構描述發佈 (公開) 為 WCF 服務，以區隔 WCF 服務邏輯與商務程序邏輯。</span><span class="sxs-lookup"><span data-stu-id="1f90c-110">You can publish (expose) your orchestrations and schemas as WCF services with the WCF adapters to separate the WCF service logic from the business process logic.</span></span> <span data-ttu-id="1f90c-111">針對外掛式 WCF 配接器，您可以使用 BizTalk WCF 服務發佈精靈建立由 Internet Information Services (IIS) 中執行的 Web 應用程式主控的外掛式 WCF 接收位置。</span><span class="sxs-lookup"><span data-stu-id="1f90c-111">For isolated WCF adapters, you can use the BizTalk WCF Service Publishing Wizard to create isolated WCF receive locations hosted by Web applications running in Internet Information Services (IIS).</span></span> <span data-ttu-id="1f90c-112">針對內建 WCF 配接器，您可以使用 BizTalk WCF 服務發佈精靈發佈任何 WCF 位置的服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1f90c-112">For the in-process WCF adapters, you can publish service metadata for any WCF locations with the BizTalk WCF Service Publishing Wizard.</span></span>  <span data-ttu-id="1f90c-113">發佈中繼資料可允許使用 svcutil.exe 公用程式建立用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f90c-113">The publishing of metadata allows the creation of client code using the svcutil.exe utility.</span></span>  
  
 <span data-ttu-id="1f90c-114">**使用 WCF 服務**</span><span class="sxs-lookup"><span data-stu-id="1f90c-114">**Consuming WCF services**</span></span>  
  
 <span data-ttu-id="1f90c-115">您可以使用 BizTalk WCF 服務使用精靈產生 BizTalk 成品 (例如 BizTalk 協調流程和類型)，使其根據 WCF 服務的中繼資料文件來使用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="1f90c-115">You can use the BizTalk WCF Service Consuming Wizard to generate the BizTalk artifacts, such as BizTalk orchestrations and types, to consume a WCF service based on the metadata document of the WCF service.</span></span> <span data-ttu-id="1f90c-116">中繼資料可讓傳送埠以用戶端身分存取外部服務。</span><span class="sxs-lookup"><span data-stu-id="1f90c-116">Metadata allows a send port to access an external service as a client.</span></span> <span data-ttu-id="1f90c-117">使用中繼資料純粹是為了描述端點位址、繫結與合約。</span><span class="sxs-lookup"><span data-stu-id="1f90c-117">Metadata is used purely for describing the endpoint address, binding, and contract.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f90c-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="1f90c-118">In This Section</span></span>  
  
-   [<span data-ttu-id="1f90c-119">發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="1f90c-119">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)  
  
-   [<span data-ttu-id="1f90c-120">使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="1f90c-120">Consuming WCF Services</span></span>](../core/consuming-wcf-services.md)  
  
-   [<span data-ttu-id="1f90c-121">指定訊息本文為 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="1f90c-121">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="1f90c-122">WCF 配接器逐步解說</span><span class="sxs-lookup"><span data-stu-id="1f90c-122">WCF Adapter Walkthroughs</span></span>](../core/wcf-adapter-walkthroughs.md)