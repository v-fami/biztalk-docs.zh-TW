---
title: "多個 Web 服務範例運作的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16680ca7-16cc-47df-8c39-a3311d468a46
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3d9faf350654be69015ea940b6b4f034d4de74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-multiple-web-services-sample-works"></a><span data-ttu-id="1d3df-102">多個 Web 服務範例運作的方式</span><span class="sxs-lookup"><span data-stu-id="1d3df-102">How the Multiple Web Services Sample Works</span></span>
<span data-ttu-id="1d3df-103">多個 Web 服務範例會使用兩種不同技術來呼叫序列中的多個 Web 服務，同時仍然能夠正確的結果傳回給原始呼叫端。</span><span class="sxs-lookup"><span data-stu-id="1d3df-103">The Multiple Web Services sample uses two separate techniques to call multiple Web services in serial while still being able to return a proper result to the original caller.</span></span> <span data-ttu-id="1d3df-104">一種方法會在回應管線中，使用自訂管線元件和其他方法使用自訂雙向路由協調流程為基礎路線服務會略過匝道引動過程完成 Web 要求/回應呼叫的需求服務。</span><span class="sxs-lookup"><span data-stu-id="1d3df-104">One method uses a custom pipeline component in the response pipeline, and the other method uses a custom two-way routing orchestration-based itinerary service that bypasses the requirement of an off-ramp invocation to complete a request/response call to a Web service.</span></span>  
  
 <span data-ttu-id="1d3df-105">自訂管線元件方法會使用轉寄站管線元件。</span><span class="sxs-lookup"><span data-stu-id="1d3df-105">The custom pipeline component method uses the Forwarder Pipeline component.</span></span> <span data-ttu-id="1d3df-106">此元件有條件地將屬性升級為防止 Microsoft BizTalk 會處理所有的路線服務之前，將訊息路由回到上遞增的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="1d3df-106">This component conditionally promotes properties to keep Microsoft BizTalk from routing the message back to the send pipeline of the on-ramp until all the itinerary services are processed.</span></span>  
  
 <span data-ttu-id="1d3df-107">自訂協調流程為基礎的服務方法會使用包含在 ESB TwoWayRouting 協調流程。在 \Source\Samples\MultipleWebSerivces\Source\ESB MultipleWebServices.Orchestrations 專案。MultipleWebServices.Orchestrations 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d3df-107">The custom orchestration-based service method uses the TwoWayRouting orchestration contained in the ESB.MultipleWebServices.Orchestrations project in the \Source\Samples\MultipleWebSerivces\Source\ESB.MultipleWebServices.Orchestrations folder.</span></span> <span data-ttu-id="1d3df-108">此服務會處理相關聯的解析程式，以判斷雙向的 Web 服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="1d3df-108">This service processes an associated resolver to determine the endpoint address of a two-way Web service.</span></span> <span data-ttu-id="1d3df-109">然後，它會設定動態 Solict-回應傳送埠命名為 RoutingPort 來傳送訊息至 Web 服務，並將結果傳回至協調流程。</span><span class="sxs-lookup"><span data-stu-id="1d3df-109">It then configures a Dynamic Solict-Response Send Port named RoutingPort to send the message to the Web service and return the result to the orchestration.</span></span> <span data-ttu-id="1d3df-110">協調流程然後前進的路線，並傳回產生的訊息到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="1d3df-110">The orchestration then advances the itinerary and returns the resulting message to the MessageBox.</span></span>  
  
 <span data-ttu-id="1d3df-111">此範例包含的行程會使用一個或這兩種方法以確保訊息流程遵循路線所保留。</span><span class="sxs-lookup"><span data-stu-id="1d3df-111">The itineraries included with the sample use one or both of these methods to ensure message flow following the itinerary is maintained.</span></span> <span data-ttu-id="1d3df-112">如需詳細資訊，請參閱[範例多個 Web 服務旅](../esb-toolkit/the-sample-multiple-web-services-itineraries.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3df-112">For more information, see [The Sample Multiple Web Services Itineraries](../esb-toolkit/the-sample-multiple-web-services-itineraries.md).</span></span>