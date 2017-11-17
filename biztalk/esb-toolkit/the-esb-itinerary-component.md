---
title: "ESB 路線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 379edc6a-7d53-4338-87a5-47b5238453a4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80aa7c1ef4bc53ad2e2821eaf8dc4184777900a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-component"></a><span data-ttu-id="650cc-102">ESB 路線元件</span><span class="sxs-lookup"><span data-stu-id="650cc-102">The ESB Itinerary Component</span></span>
<span data-ttu-id="650cc-103">ESB 行程元件設定以 ESB 路線上手隨訊息一起傳送的 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="650cc-103">The ESB Itinerary component sets the context properties from the SOAP header sent along with the message to an ESB itinerary on-ramp.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="650cc-104">安裝</span><span class="sxs-lookup"><span data-stu-id="650cc-104">Installation</span></span>  
 <span data-ttu-id="650cc-105">自動安裝 ESB 核心安裝**路線**BizTalk Server 管線元件資料夾中的管線元件。</span><span class="sxs-lookup"><span data-stu-id="650cc-105">Installing the ESB Core automatically installs the **Itinerary** pipeline component in the BizTalk Server Pipeline Components folder.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="650cc-106">運作方式</span><span class="sxs-lookup"><span data-stu-id="650cc-106">How It Works</span></span>  
 <span data-ttu-id="650cc-107">ESB 行程元件是一個接收管線中只可位於 Microsoft BizTalk 管線元件。</span><span class="sxs-lookup"><span data-stu-id="650cc-107">The ESB Itinerary component is a Microsoft BizTalk pipeline component that can reside only in a receive pipeline.</span></span> <span data-ttu-id="650cc-108">它會將值升級從 SOAP 訊息標頭或元件的設定為訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="650cc-108">It promotes values from either SOAP message headers or component settings into the message context as properties.</span></span> <span data-ttu-id="650cc-109">您可以找到的升級中隨附的行程上手 Web 服務 SOAP 標頭範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="650cc-109">You can find an example of promoting SOAP headers in the Itinerary On-Ramp Web services provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="650cc-110">這些 Web 服務公開 SOAP 標頭做為其合約的一部分，並且用戶端應用程式必須設定標頭。</span><span class="sxs-lookup"><span data-stu-id="650cc-110">These Web services expose SOAP headers as part of their contracts, and client applications must set the headers.</span></span> <span data-ttu-id="650cc-111">當訊息通過接收管線中的元件，元件會讀取 SOAP 標頭值，並將升級 （寫入） 至訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="650cc-111">As the message passes through the component in a receive pipeline, the component reads the SOAP header values and promotes (writes) them to the message context properties.</span></span>  
  
## <a name="using-the-esb-itinerary-component"></a><span data-ttu-id="650cc-112">使用 ESB 路線元件</span><span class="sxs-lookup"><span data-stu-id="650cc-112">Using the ESB Itinerary Component</span></span>  
 <span data-ttu-id="650cc-113">您可以 ESB 行程元件新增至接收管線，然後使用管線，接收位置中。</span><span class="sxs-lookup"><span data-stu-id="650cc-113">You can add the ESB Itinerary component to a receive pipeline and then use the pipeline in a receive location.</span></span> <span data-ttu-id="650cc-114">元件會自動升級 SOAP 標頭值或元件內送訊息的內容屬性的設定。</span><span class="sxs-lookup"><span data-stu-id="650cc-114">The component automatically promotes SOAP header values or component settings into the context properties of the incoming message.</span></span>  
  
 <span data-ttu-id="650cc-115">如需如何使用此元件的範例，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="650cc-115">For an example of how to use this component, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>