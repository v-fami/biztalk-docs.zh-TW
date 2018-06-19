---
title: 協調流程發佈為 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- orchestrations, Web services
- Web services, orchestrations
- BizTalk Web Services Publishing Wizard, orchestrations
- BizTalk Web Services Publishing Wizard, prerequisites
- orchestrations, publishing
ms.assetid: f209310d-c265-4c37-8424-c9b287e713ca
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b6d36f6c56851bfedcd522f96d01a8256232826
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269062"
---
# <a name="publishing-an-orchestration-as-a-web-service"></a><span data-ttu-id="fd623-102">協調流程發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="fd623-102">Publishing an Orchestration as a Web Service</span></span>
<span data-ttu-id="fd623-103">您可以使用 [BizTalk Web 服務發佈精靈] 將協調流程發佈為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fd623-103">You use the BizTalk Web Services Publishing Wizard to publish an orchestration as a Web service.</span></span> <span data-ttu-id="fd623-104">精靈會根據 BizTalk 組件中的協調流程來建立 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fd623-104">The wizard creates a Web service based on an orchestration in a BizTalk assembly.</span></span> <span data-ttu-id="fd623-105">使用此精靈，即可選取協調流程和接收埠來發佈 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fd623-105">Using the wizard, you select orchestrations and receive ports to publish Web services.</span></span> <span data-ttu-id="fd623-106">您可以定義目標命名空間、SOAP 標頭需求，以及精靈所產生 Web 服務專案的位置。</span><span class="sxs-lookup"><span data-stu-id="fd623-106">You can define target namespaces, SOAP header requirements, and locations for the Web service project the wizard generates.</span></span>  
  
 <span data-ttu-id="fd623-107">在執行精靈之前，您必須編譯其中包含要發佈為 Web 服務之協調流程和結構描述的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="fd623-107">Before you run the wizard, you must compile your BizTalk assemblies that contain the orchestrations and schemas that you intend to publish as a Web service.</span></span>  
  
 <span data-ttu-id="fd623-108">您必須先啟用 Web 服務，才能執行 [BizTalk Web 服務發佈精靈]。</span><span class="sxs-lookup"><span data-stu-id="fd623-108">Prior to running the BizTalk Web Services Publishing Wizard, you must enable Web services.</span></span> <span data-ttu-id="fd623-109">如需有關啟用 Web 服務系統的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fd623-109">For more information about enabling Web services for your system, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd623-110">您必須先安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，才能夠將協調流程發佈為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fd623-110">You must install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] before you can publish an orchestration as a Web service.</span></span> <span data-ttu-id="fd623-111">您不需要安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd623-111">You don't need to install Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd623-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="fd623-112">In This Section</span></span>  
  
-   [<span data-ttu-id="fd623-113">如何將協調流程對應至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="fd623-113">How to Map Orchestrations to Web Services</span></span>](../core/how-to-map-orchestrations-to-web-services.md)  
  
-   [<span data-ttu-id="fd623-114">如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="fd623-114">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)  
  
-   [<span data-ttu-id="fd623-115">如何從協調流程發佈為 Web 服務擲回 SOAP 例外狀況</span><span class="sxs-lookup"><span data-stu-id="fd623-115">How to Throw SOAP Exceptions from Orchestrations Published as a Web Service</span></span>](../core/how-to-throw-soap-exceptions-from-orchestrations-published-as-a-web-service.md)