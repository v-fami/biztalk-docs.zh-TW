---
title: 使用 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- orchestrations, Web services
- Web services, consuming
- Web services, orchestrations
ms.assetid: 803ba623-86e7-479a-a4b6-5b576fee8825
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 528f61910dfc5e2d24a40b0ed29a23fcf85a72bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237822"
---
# <a name="consuming-web-services"></a><span data-ttu-id="9b6b7-102">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9b6b7-102">Consuming Web Services</span></span>
<span data-ttu-id="9b6b7-103">使用 Web 服務可讓您將現有 Web 服務加入至商務程序。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-103">Consuming Web services enables you to add existing Web services to your business process.</span></span> <span data-ttu-id="9b6b7-104">您可以將數個 Web 服務彙總成為一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-104">You can aggregate several Web services into a single orchestration.</span></span>  
  
 <span data-ttu-id="9b6b7-105">您可以透過 Web 連接埠，從協調流程使用 (呼叫) Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-105">You can consume (call) a Web service from your orchestration by using Web ports.</span></span> <span data-ttu-id="9b6b7-106">若要從協調流程取用 Web 服務，您必須建立 Web 連接埠，並建構 Web 訊息。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-106">To consume a Web service from an orchestration, you create a Web port and construct Web messages.</span></span>  
  
 <span data-ttu-id="9b6b7-107">您可以搭配已使用的 Web 服務來使用 SOAP 標頭，變更已使用 Web 服務的 URI，並且為已使用的 Web 服務動態設定 URI。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-107">You can use SOAP headers with the consumed Web service, change the URI of a consumed Web service, and dynamically set the URI for a consumed Web service.</span></span>  
  
 <span data-ttu-id="9b6b7-108">如需設定 SOAP 接收處理常式，請參閱[如何設定 SOAP 接收處理常式](../core/how-to-configure-a-soap-receive-handler.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-108">For information about configuring a SOAP receive handler, see [How to Configure a SOAP Receive Handler](../core/how-to-configure-a-soap-receive-handler.md).</span></span> <span data-ttu-id="9b6b7-109">如需設定 SOAP 接收位置，請參閱[如何設定 SOAP 接收位置](../core/how-to-configure-a-soap-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6b7-109">For information about configuring a SOAP receive location, see [How to Configure a SOAP Receive Location](../core/how-to-configure-a-soap-receive-location.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b6b7-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="9b6b7-110">In This Section</span></span>  
  
-   [<span data-ttu-id="9b6b7-111">加入 Web 參考</span><span class="sxs-lookup"><span data-stu-id="9b6b7-111">Adding Web References</span></span>](../core/adding-web-references.md)  
  
-   [<span data-ttu-id="9b6b7-112">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="9b6b7-112">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)  
  
-   [<span data-ttu-id="9b6b7-113">建立 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="9b6b7-113">Creating Web Ports</span></span>](../core/creating-web-ports.md)  
  
-   [<span data-ttu-id="9b6b7-114">使用 Web 服務時的考量</span><span class="sxs-lookup"><span data-stu-id="9b6b7-114">Considerations When Consuming Web Services</span></span>](../core/considerations-when-consuming-web-services.md)