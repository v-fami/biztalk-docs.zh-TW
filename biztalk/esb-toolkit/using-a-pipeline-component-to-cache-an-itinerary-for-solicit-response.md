---
title: "使用快取路線請求-回應管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add07ebf-785c-4c53-be69-efd40677a758
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64b6822a4f4ca70e88ee86277e00645982595b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response"></a><span data-ttu-id="53a2b-102">使用快取路線請求-回應管線元件</span><span class="sxs-lookup"><span data-stu-id="53a2b-102">Using a Pipeline Component to Cache an Itinerary for Solicit-Response</span></span>
<span data-ttu-id="53a2b-103">透過提交的郵件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線上手可以瀏覽單向路線或雙向 （要求-回應） 路線。</span><span class="sxs-lookup"><span data-stu-id="53a2b-103">Messages submitted through a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary on-ramp can go through either a one-way itinerary or a two-way (request-response) itinerary.</span></span> <span data-ttu-id="53a2b-104">若要支援要求-回應旅，路線機制必須提供 BizTalk 動態請求-回應傳送埠的快取。</span><span class="sxs-lookup"><span data-stu-id="53a2b-104">To support request-response itineraries, the itinerary mechanism must provide caching for BizTalk dynamic Solicit-Response send ports.</span></span>  
  
 <span data-ttu-id="53a2b-105">ESB 行程快取管線元件會將輸出訊息內容中儲存至快取的路線，並將其附加到回應訊息。它會使用可設定的快取金鑰的傳送埠傳回。</span><span class="sxs-lookup"><span data-stu-id="53a2b-105">The ESB Itinerary Cache pipeline component places the itinerary stored in the outbound message context into the cache and attaches it to the response message; it is returned by the send port using the configurable caching key.</span></span> <span data-ttu-id="53a2b-106">如此路線服務處理，並執行之後路線中目前的服務定義的後續服務。</span><span class="sxs-lookup"><span data-stu-id="53a2b-106">This allows the itinerary service to process and execute subsequent services defined after the current service in the itinerary.</span></span>  
  
 <span data-ttu-id="53a2b-107">根據預設，ESB 行程快取管線元件位於 ItineraryReceiveSend BizTalk 管線，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="53a2b-107">By default, the ESB Itinerary Cache pipeline component resides in the ItineraryReceiveSend BizTalk pipeline, as shown in Figure 1.</span></span> <span data-ttu-id="53a2b-108">這個管線應該是只用來做為接收管線的請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="53a2b-108">This pipeline should be used only as the receive pipeline for a Solicit-Response send port.</span></span>  
  
 <span data-ttu-id="53a2b-109">![管線元件快取](../esb-toolkit/media/ch4-pipelinecomponentcache.gif "第 4 章第 PipelineComponentCache")</span><span class="sxs-lookup"><span data-stu-id="53a2b-109">![Pipeline Component Cache](../esb-toolkit/media/ch4-pipelinecomponentcache.gif "Ch4-PipelineComponentCache")</span></span>  
  
 <span data-ttu-id="53a2b-110">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="53a2b-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="53a2b-111">**ESB 行程快取管線元件**</span><span class="sxs-lookup"><span data-stu-id="53a2b-111">**The ESB Itinerary Cache Pipeline component**</span></span>  
  
 <span data-ttu-id="53a2b-112">使用 biztalk ESB 行程快取管線元件的接收管線的請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="53a2b-112">Use the ESB Itinerary Cache Pipeline component in a BizTalk receive pipeline for a Solicit-Response send port.</span></span>