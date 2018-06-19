---
title: ESB 路線管理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f78240de-34da-4751-aceb-b69d81403124
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fb7c2566cbd445ea305089033935427b82046bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294334"
---
# <a name="esb-itinerary-management"></a><span data-ttu-id="49065-102">ESB 路線管理</span><span class="sxs-lookup"><span data-stu-id="49065-102">ESB Itinerary Management</span></span>
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="49065-103">提供兩個不同的選項，ESB 路線管理： 集中式與分散式。</span><span class="sxs-lookup"><span data-stu-id="49065-103"> offers two distinct options for ESB itinerary management: centralized and decentralized.</span></span> <span data-ttu-id="49065-104">本章節將討論這些選項的每個效益和風險。</span><span class="sxs-lookup"><span data-stu-id="49065-104">This section discusses benefits and risks for each of these options.</span></span>  
  
## <a name="decentralized-esb-policy-management"></a><span data-ttu-id="49065-105">非集中式的 ESB 原則管理</span><span class="sxs-lookup"><span data-stu-id="49065-105">Decentralized ESB Policy Management</span></span>  
 <span data-ttu-id="49065-106">在此案例中，ESB 用戶端應用程式會提供內容的 ESB 行程 ESB 來為每個已提交之訊息的附件。</span><span class="sxs-lookup"><span data-stu-id="49065-106">In this scenario, the ESB client application provides the content of the ESB itinerary as an attachment for each submitted message to the ESB.</span></span> <span data-ttu-id="49065-107">訊息包含 SOAP 標頭的計劃的內容;管線元件收到訊息時，它會解碼訊息，然後它會升級訊息內容中，做進一步路由路線。</span><span class="sxs-lookup"><span data-stu-id="49065-107">The message contains a SOAP header with the itinerary contents; when a pipeline component receives the message, it decodes the message, and then it promotes the itinerary to the message context for further routing.</span></span> <span data-ttu-id="49065-108">雖然這項設計提供的機會，以輕鬆地實作路由名單模式，完全可讓用戶端控制的訊息流程帶來下列挑戰：</span><span class="sxs-lookup"><span data-stu-id="49065-108">Although this design provides the opportunity to easily implement a Routing Slip pattern, fully allowing the client to control the flow of a message presents the following challenges:</span></span>  
  
-   <span data-ttu-id="49065-109">允許用戶端判斷哪些處理程序應該套用至訊息，可供選擇可用的處理序的詳細資料而言是透明 ESB 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="49065-109">By allowing the client to determine which processes should be applied to a message, the details of available processes from which to choose are transparent to the ESB client application.</span></span> <span data-ttu-id="49065-110">這種作法可能無法公開機密資訊給用戶端 ESB 行程。</span><span class="sxs-lookup"><span data-stu-id="49065-110">This practice could potentially expose sensitive information from ESB itinerary to the client.</span></span>  
  
-   <span data-ttu-id="49065-111">除了潛在的安全性考量，允許用戶端管理的每則訊息所送出行程不會強制執行 ESB 行程為原則除非它實作特定的用戶端。</span><span class="sxs-lookup"><span data-stu-id="49065-111">In addition to the potential security concerns, allowing the client to manage the itineraries for being submitted with each message does not enforce ESB itinerary as policy unless it is implemented for a specific client.</span></span> <span data-ttu-id="49065-112">因此，強制執行新版路線變更管理的成本極高，而且會增加受信任的用戶端應用程式的每個新的特定類型。</span><span class="sxs-lookup"><span data-stu-id="49065-112">Therefore, costs of change management for enforcing a new version of the itinerary are extremely high and will increase for each new specific type of a trusted client application.</span></span>  
  
-   <span data-ttu-id="49065-113">允許將整個路線已提交之訊息的用戶端，用戶端應該永遠是位於受信任的子系統。否則，ESB 行程可能無法指定已不再有效的惡意的處理指示。</span><span class="sxs-lookup"><span data-stu-id="49065-113">By allowing the client to pass the entire itinerary with the submitted message, the client should always be located within the trusted subsystem; otherwise, the ESB itinerary could potentially specify malicious processing instructions that are no longer valid.</span></span>  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="49065-114">處理在用戶端所提交的行程的支援不過，這個選項應該只能用於回溯相容性與測試之用。</span><span class="sxs-lookup"><span data-stu-id="49065-114"> supports processing itineraries submitted by the client; however, this option should only be used for backward compatibility and testing purposes.</span></span>  
  
 <span data-ttu-id="49065-115">如需啟用用戶端行程的詳細資訊，請參閱[使用管線元件讀取行程](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)。</span><span class="sxs-lookup"><span data-stu-id="49065-115">For more information about enabling client-side itineraries, see [Using a Pipeline Component to Read an Itinerary](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md).</span></span>  
  
## <a name="centralized-esb-policy-management"></a><span data-ttu-id="49065-116">集中式的 ESB 原則管理</span><span class="sxs-lookup"><span data-stu-id="49065-116">Centralized ESB Policy Management</span></span>  
 <span data-ttu-id="49065-117">有潛在的安全性和同步處理考量固有與允許旅附加，以提交訊息，因此最佳做法是為了管理 ESB 行程實作成 SQL database中包含的中央儲存機制中的用戶端[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]針對此目的。</span><span class="sxs-lookup"><span data-stu-id="49065-117">There are potential security and synchronization concerns inherent with allowing a client to submit messages with itineraries attached, so the best practice is to manage ESB itineraries in a central repository implemented as a SQL database and included in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] for this purpose.</span></span> <span data-ttu-id="49065-118">藉由部署旅到中央位置，ESB 路線原則可以輕鬆地管理和修改而不需要實作重大用戶端變更，而且組織可以控制訊息的處理而不會暴露潛在機密資訊給用戶端。</span><span class="sxs-lookup"><span data-stu-id="49065-118">By deploying itineraries to a central location, ESB itinerary policies can be easily managed and modified without the need to implement dramatic client-side changes, and the organization can control the processing of messages without exposing potentially sensitive information to the client.</span></span>  
  
 <span data-ttu-id="49065-119">若要判斷適當 ESB 行程附加至輸入訊息提供特製化的管線元件。</span><span class="sxs-lookup"><span data-stu-id="49065-119">Specialized pipeline components are provided to determine the appropriate ESB itinerary to attach to an inbound message.</span></span> <span data-ttu-id="49065-120">此方法提供兩個不同的選項，讓您提交於行程為基礎的路由的訊息。</span><span class="sxs-lookup"><span data-stu-id="49065-120">This approach provides two distinct options for submitting a message for itinerary-based routing:</span></span>  
  
-   <span data-ttu-id="49065-121">使用第一個選項，用戶端應用程式仍可能不同的 ESB 行程藉由提供 SOAP 標頭附上要求訊息，而非提交完成路線 ESB 路線的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="49065-121">Using the first option, the client application can still indicate a distinct ESB itinerary by providing ESB itinerary reference information in the SOAP header along with request message, instead of submitting a complete itinerary.</span></span> <span data-ttu-id="49065-122">這項資訊包括 ESB 路線名稱和選擇性的版本。</span><span class="sxs-lookup"><span data-stu-id="49065-122">This information includes ESB itinerary name and optional version.</span></span> <span data-ttu-id="49065-123">在此案例中，用戶端仍可以指定如何路由訊息，但沒有任何原則同步處理錯誤或安全性項目都會破壞的風險所公開的 ESB 行程，用戶端應用程式的內容。</span><span class="sxs-lookup"><span data-stu-id="49065-123">In this scenario, clients can still specify how message can be routed, but there is no risk of policy synchronization errors or security compromises by exposing content of the ESB itinerary to client applications.</span></span>  
  
-   <span data-ttu-id="49065-124">第二個選項是設定 ESB 上手來自動判斷適當的 ESB 行程中，為基礎的內容或內容的訊息，而不需要從提交的用戶端的任何標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="49065-124">The second option is to configure the ESB on-ramp to automatically determine the appropriate ESB itinerary, based on the content or context of the message, without requiring any header information from the submitting client.</span></span> <span data-ttu-id="49065-125">此案例可讓組織可以控制送出訊息的流程，並不需要留意的訊息路由用戶端。</span><span class="sxs-lookup"><span data-stu-id="49065-125">This scenario enables the organization to control the flow of a submitted message and eliminates the need for the client to be aware of how the message is being routed.</span></span>