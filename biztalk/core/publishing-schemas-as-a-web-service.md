---
title: 結構描述發佈為 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- schemas, publishing
- Web services, schemas
- schemas, Web services
ms.assetid: 65b5f826-6abf-437f-b2dc-b36e488ba6da
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e48076ee46d380a2223aa246a334063d08f1552e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269038"
---
# <a name="publishing-schemas-as-a-web-service"></a><span data-ttu-id="ae2e8-102">將結構描述發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="ae2e8-102">Publishing Schemas as a Web Service</span></span>
<span data-ttu-id="ae2e8-103">您可以使用「BizTalk Web 服務發佈精靈」來建立使用現有結構描述的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-103">You use the BizTalk Web Services Publishing Wizard to create Web services that use existing schemas.</span></span> <span data-ttu-id="ae2e8-104">您可以宣告 Web 服務、Web 方法以及要發佈的要求和回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-104">You declare the Web services, Web methods, and request and response schemas that you want to publish.</span></span> <span data-ttu-id="ae2e8-105">使用精靈，您可以定義目標命名空間、SOAP 標頭需求，以及所產生 Web 服務專案的位置。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-105">Using the wizard, you define the target namespace, SOAP header requirements, and the location of the generated Web service project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae2e8-106">您必須編譯包含結構描述的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-106">You must compile the BizTalk assemblies containing the schemas.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae2e8-107">每個 Web 方法都可以有一個要求結構描述和一個回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-107">Each Web method can have one request schema and one response schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae2e8-108">如果要將結構描述發佈為 Web 服務，您必須安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-108">To publish schemas as a Web service, you must have [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae2e8-109">您必須先啟用 Web 服務，才能執行 [BizTalk Web 服務發佈精靈]。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-109">Prior to running the BizTalk Web Services Publishing Wizard, you must enable Web services.</span></span> <span data-ttu-id="ae2e8-110">如需有關啟用 Web 服務的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2e8-110">For more information about enabling Web services, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae2e8-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="ae2e8-111">In This Section</span></span>  
  
-   [<span data-ttu-id="ae2e8-112">建立 Web 服務與 Web 方法</span><span class="sxs-lookup"><span data-stu-id="ae2e8-112">Creating Web Services and Web Methods</span></span>](../core/creating-web-services-and-web-methods.md)  
  
-   [<span data-ttu-id="ae2e8-113">如何使用 BizTalk Web 服務發佈精靈將結構描述發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="ae2e8-113">How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service</span></span>](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)