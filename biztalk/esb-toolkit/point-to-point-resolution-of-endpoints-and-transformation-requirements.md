---
title: "端點的轉換需求點對點解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4c570bf-8274-4779-ae83-2aef2bf57ded
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8899c5f713f1c9ebfe299d3e431754dd8b9794d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="point-to-point-resolution-of-endpoints-and-transformation-requirements"></a><span data-ttu-id="3d199-102">點對點的端點和轉換需求的解決方式</span><span class="sxs-lookup"><span data-stu-id="3d199-102">Point-to-Point Resolution of Endpoints and Transformation Requirements</span></span>
<span data-ttu-id="3d199-103">在此使用情況下，Web 服務用戶端會呼叫 Web 服務，而不需要透過 ESB。</span><span class="sxs-lookup"><span data-stu-id="3d199-103">In this use case, a Web service client calls a Web service without going through the ESB.</span></span> <span data-ttu-id="3d199-104">直接通訊的兩個點，但用戶端會發出的呼叫之前，它必須解決的 Web 服務端點。</span><span class="sxs-lookup"><span data-stu-id="3d199-104">The two points communicate directly, but before the client makes the call, it must resolve the endpoint of the Web service.</span></span> <span data-ttu-id="3d199-105">呼叫 Web 服務可以是單向或要求-回應。</span><span class="sxs-lookup"><span data-stu-id="3d199-105">The call to the Web service can be either a one-way or a request-response.</span></span> <span data-ttu-id="3d199-106">達到這個目的的一個方法是使用 ESB 的動態解析功能，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="3d199-106">One way of achieving this is to use the dynamic resolution features of the ESB, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="3d199-107">![點 &#45; 若要 &#45;端點的端點解析](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3 PointToPoint")</span><span class="sxs-lookup"><span data-stu-id="3d199-107">![Point&#45;to&#45;Point Resolution of Endpoints](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3-PointToPoint")</span></span>  
  
 <span data-ttu-id="3d199-108">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="3d199-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="3d199-109">**解決使用 UDDI 端點**</span><span class="sxs-lookup"><span data-stu-id="3d199-109">**Resolving endpoints using UDDI**</span></span>  
  
 <span data-ttu-id="3d199-110">解析程式服務 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="3d199-110">The Resolver Service sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="3d199-111">此範例示範如何呼叫 ESB 解析程式服務來執行解析，可讓您測試解析，因為您正在開發的後端存放區，例如通用描述、 探索與整合 (UDDI)，XML 路徑語言 (XPath) 的內容Static 或 BizTalk Server 商務規則引擎中的原則。</span><span class="sxs-lookup"><span data-stu-id="3d199-111">The sample shows how to call the ESB Resolver Service to perform resolution, which enables you to test resolution as you are developing the contents of the back-end stores, such as Universal Description, Discovery, and Integration (UDDI), XML Path Language (XPath), Static, or policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="3d199-112">如需詳細資訊，請參閱[安裝及執行 「 解析程式服務 」 範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="3d199-112">For more information, see [Installing and Running the Resolver Service Sample](../esb-toolkit/installing-and-running-the-resolver-service-sample.md).</span></span>