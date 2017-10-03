---
title: "ESB 路線的轉寄站元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 607cc8a0-4964-4751-baca-c3329983c98b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c61643423021701186745ab4275520cb14d3ceca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-forwarder-component"></a><span data-ttu-id="d470b-102">ESB 路線的轉寄站元件</span><span class="sxs-lookup"><span data-stu-id="d470b-102">The ESB Itinerary Forwarder Component</span></span>
<span data-ttu-id="d470b-103">行程必須依序叫用多個 Web 服務時，會使用 ESB 行程轉寄站元件。</span><span class="sxs-lookup"><span data-stu-id="d470b-103">The ESB Itinerary Forwarder component is used when an itinerary must sequentially invoke multiple Web services.</span></span> <span data-ttu-id="d470b-104">使用此元件在接收管線，與雙向匝道的回應端相關聯。</span><span class="sxs-lookup"><span data-stu-id="d470b-104">The component can be used in receive pipelines that are associated with the response side of a two-way off-ramp.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="d470b-105">安裝</span><span class="sxs-lookup"><span data-stu-id="d470b-105">Installation</span></span>  
 <span data-ttu-id="d470b-106">自動安裝 ESB 核心安裝**路線轉寄站**元件的 BizTalk Server 管線元件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d470b-106">Installing the ESB Core automatically installs the **Itinerary Forwarder** component in the BizTalk Server Pipeline Components folder.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="d470b-107">運作方式</span><span class="sxs-lookup"><span data-stu-id="d470b-107">How It Works</span></span>  
 <span data-ttu-id="d470b-108">當 Microsoft BizTalk 收到訊息，以透過雙向接收埠，訊息會發佈到 Messagebox 資料庫時，建立執行個體訂閱。</span><span class="sxs-lookup"><span data-stu-id="d470b-108">When Microsoft BizTalk receives a message through a two-way receive port as the message is published to the Message Box database, an instance subscription is created.</span></span> <span data-ttu-id="d470b-109">此訂用帳戶包含**EpmRRCorrelationToken**升級屬性和**RouteDirectToTP**升級屬性。</span><span class="sxs-lookup"><span data-stu-id="d470b-109">This subscription consists of the **EpmRRCorrelationToken** promoted property and a **RouteDirectToTP** promoted property.</span></span> <span data-ttu-id="d470b-110">當 「 訂閱者 」 （協調流程或雙向傳送埠） 傳回回應訊息時，這些提升的屬性比對訂閱與通過傳送管線的接收埠，會立即傳回回應。</span><span class="sxs-lookup"><span data-stu-id="d470b-110">When the subscriber (orchestration or two-way send port) returns the response message, these promoted properties match the subscription and the response is immediately returned through the send pipeline of the receive port.</span></span>  
  
 <span data-ttu-id="d470b-111">ESB 行程轉寄站應該用於回應管線的雙向匝道匝道呼叫要求-回應 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d470b-111">The ESB Itinerary Forwarder should be used in the response pipeline for a two-way off-ramp where the off-ramp is calling a request-response Web service.</span></span> <span data-ttu-id="d470b-112">元件藉由變更會干擾一般 BizTalk 處理序**RouteDirectToTP**升級的屬性為 False，以確保在回應不會傳回至起始接收埠。</span><span class="sxs-lookup"><span data-stu-id="d470b-112">The component interferes with the typical BizTalk process by changing the **RouteDirectToTP** promoted property to False, thus ensuring that the response will not be returned to the initiating receive port.</span></span> <span data-ttu-id="d470b-113">達到路線的最後一個步驟之後， **RouteDirectToTP**屬性變更回**True**，因此傳回的結果來起始上手。</span><span class="sxs-lookup"><span data-stu-id="d470b-113">After the last step in the itinerary is reached, the **RouteDirectToTP** property is changed back to **True**, thus returning the result to the initiating on-ramp.</span></span>  
  
## <a name="using-the-esb-itinerary-forwarder-component"></a><span data-ttu-id="d470b-114">使用 ESB 路線的轉寄站元件</span><span class="sxs-lookup"><span data-stu-id="d470b-114">Using the ESB Itinerary Forwarder Component</span></span>  
 <span data-ttu-id="d470b-115">ESB ItineraryForwarder 元件新增至接收管線，然後使用管線的雙向匝道的回應部分。</span><span class="sxs-lookup"><span data-stu-id="d470b-115">Add the ESB ItineraryForwarder component to a receive pipeline and then use the pipeline with the response portion of a two-way off-ramp.</span></span> <span data-ttu-id="d470b-116">建立行程的鏈結多個 Web 服務，不論轉換路線服務之前，或在服務之間。</span><span class="sxs-lookup"><span data-stu-id="d470b-116">Create an itinerary that chains multiple Web services, with or without transformation itinerary services, before or between the services.</span></span> <span data-ttu-id="d470b-117">如需如何使用 ESB 行程轉寄站元件的範例，請參閱[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d470b-117">For an example of how to use the ESB Itinerary Forwarder Component, see the [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span></span>