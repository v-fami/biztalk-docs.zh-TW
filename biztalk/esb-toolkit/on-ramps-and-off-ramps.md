---
title: 在坡道提升和關閉坡道提升 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cce5d2-f16f-4bda-94ac-20c4f457cfc7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0aafa69315dba07219ad8510c77cdc9de2d4bce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294558"
---
# <a name="on-ramps-and-off-ramps"></a><span data-ttu-id="4049c-102">在坡道提升和關閉坡道提升</span><span class="sxs-lookup"><span data-stu-id="4049c-102">On-Ramps and Off-Ramps</span></span>
<span data-ttu-id="4049c-103">在環境中其中[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是部署，BizTalk 接收位置負責接收 ESB 目的地的訊息指 「 上手。 」</span><span class="sxs-lookup"><span data-stu-id="4049c-103">In an environment where [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is deployed, a BizTalk receive location responsible for receiving ESB-destined messages is referred to as an "on-ramp."</span></span> <span data-ttu-id="4049c-104">若要設定 ESB 上手的標準 BizTalk 接收位置，接收位置關聯其中一個管線工具組的一部分，並正確設定來決定，或讀取的行程該管線元件輸入的訊息，根據您的案例。</span><span class="sxs-lookup"><span data-stu-id="4049c-104">To configure a standard BizTalk receive location to an ESB on-ramp, associate the receive location with one of the pipelines provided as part of the toolkit, and then correctly configure the components of that pipeline to determine or read the itinerary for the inbound message, depending on your scenario.</span></span>  
  
 <span data-ttu-id="4049c-105">ESB"匝道 」 對應到 BizTalk 動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="4049c-105">An ESB "off-ramp" corresponds to a BizTalk dynamic send port.</span></span> <span data-ttu-id="4049c-106">處理行程時，值會升級為使用系統 Properties.xsd 結構描述的相關訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="4049c-106">As an itinerary is being processed, values are promoted to the context properties of the associated message using the System-Properties.xsd schema.</span></span> <span data-ttu-id="4049c-107">BizTalk 發行-訂閱機制會使用這些升級屬性來路由訊息，以透過動態傳送埠 （匝道） 以完成訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="4049c-107">The BizTalk publish-subscribe mechanism uses these promoted properties to route a message through a dynamic send port (off-ramp) to complete a message delivery.</span></span>  
  
 <span data-ttu-id="4049c-108">下表列出在-坡道提升所提供的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4049c-108">The following table lists the on-ramps that are provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
|<span data-ttu-id="4049c-109">名稱</span><span class="sxs-lookup"><span data-stu-id="4049c-109">Name</span></span>|<span data-ttu-id="4049c-110">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="4049c-110">Message exchange pattern</span></span>|<span data-ttu-id="4049c-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="4049c-111">**Description**</span></span>|  
|----------|------------------------------|---------------------|  
|<span data-ttu-id="4049c-112">ESB。ItineraryServices</span><span class="sxs-lookup"><span data-stu-id="4049c-112">ESB.ItineraryServices</span></span>|<span data-ttu-id="4049c-113">單向</span><span class="sxs-lookup"><span data-stu-id="4049c-113">One-Way</span></span>|<span data-ttu-id="4049c-114">ASMX 上手。SOAP 標頭中預期 ESB 路線內容。</span><span class="sxs-lookup"><span data-stu-id="4049c-114">ASMX on-ramp; expects ESB itinerary content in SOAP header.</span></span>|  
|<span data-ttu-id="4049c-115">ESB。ItineraryServices.Response</span><span class="sxs-lookup"><span data-stu-id="4049c-115">ESB.ItineraryServices.Response</span></span>|<span data-ttu-id="4049c-116">要求-回應</span><span class="sxs-lookup"><span data-stu-id="4049c-116">Request-Response</span></span>|<span data-ttu-id="4049c-117">ASMX 上手。SOAP 標頭中預期 ESB 路線內容。</span><span class="sxs-lookup"><span data-stu-id="4049c-117">ASMX on-ramp; expects ESB itinerary content in SOAP header.</span></span>|  
|<span data-ttu-id="4049c-118">ESB。ItineraryServices.WCF</span><span class="sxs-lookup"><span data-stu-id="4049c-118">ESB.ItineraryServices.WCF</span></span>|<span data-ttu-id="4049c-119">單向</span><span class="sxs-lookup"><span data-stu-id="4049c-119">One-Way</span></span>|<span data-ttu-id="4049c-120">Windows Communication Foundation (WCF) 上手。需要 ESB 路線參考 SOAP 標頭中。</span><span class="sxs-lookup"><span data-stu-id="4049c-120">Windows Communication Foundation (WCF) on-ramp; expects ESB itinerary reference in SOAP header.</span></span>|  
|<span data-ttu-id="4049c-121">ESB。ItineraryServices.Response.WCF</span><span class="sxs-lookup"><span data-stu-id="4049c-121">ESB.ItineraryServices.Response.WCF</span></span>|<span data-ttu-id="4049c-122">要求-回應</span><span class="sxs-lookup"><span data-stu-id="4049c-122">Request-Response</span></span>|<span data-ttu-id="4049c-123">WCF 上手。需要 ESB 路線參考 SOAP 標頭中。</span><span class="sxs-lookup"><span data-stu-id="4049c-123">WCF on-ramp; expects ESB itinerary reference in SOAP header.</span></span>|  
|<span data-ttu-id="4049c-124">ESB。ItineraryServices.Generic.WCF</span><span class="sxs-lookup"><span data-stu-id="4049c-124">ESB.ItineraryServices.Generic.WCF</span></span>|<span data-ttu-id="4049c-125">單向</span><span class="sxs-lookup"><span data-stu-id="4049c-125">One-Way</span></span>|<span data-ttu-id="4049c-126">WCF 上手。預期只要求訊息。</span><span class="sxs-lookup"><span data-stu-id="4049c-126">WCF on-ramp; expects request message only.</span></span>|  
|<span data-ttu-id="4049c-127">ESB。ItineraryServices.Generic.Response.WCF</span><span class="sxs-lookup"><span data-stu-id="4049c-127">ESB.ItineraryServices.Generic.Response.WCF</span></span>|<span data-ttu-id="4049c-128">要求-回應</span><span class="sxs-lookup"><span data-stu-id="4049c-128">Request-Response</span></span>|<span data-ttu-id="4049c-129">WCF 上手。預期只要求訊息。</span><span class="sxs-lookup"><span data-stu-id="4049c-129">WCF on-ramp; expects request message only.</span></span>|  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="4049c-130">在-坡道提升不 ASMX 應該設定為選取 ESB 行程。</span><span class="sxs-lookup"><span data-stu-id="4049c-130"> on-ramps that are not ASMX should be configured to select ESB itineraries.</span></span> <span data-ttu-id="4049c-131">如需如何選取 ESB 行程的詳細資訊，請參閱[使用管線元件，選取現有的行程](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)。</span><span class="sxs-lookup"><span data-stu-id="4049c-131">For more information about how to select an ESB itinerary, see [Using a Pipeline Component to Select an Existing Itinerary](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md).</span></span>