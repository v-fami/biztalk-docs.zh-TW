---
title: "服務中繼模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfda54db-75fa-4bc2-9f48-11d8b3cde65b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af76e6c123a3a273bc2e100b1008f40523762695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="service-mediation-patterns"></a><span data-ttu-id="fba5c-102">服務中繼模式</span><span class="sxs-lookup"><span data-stu-id="fba5c-102">Service Mediation Patterns</span></span>
## <a name="vetovetro"></a><span data-ttu-id="fba5c-103">否決權/VETRO</span><span class="sxs-lookup"><span data-stu-id="fba5c-103">VETO/VETRO</span></span>  
 <span data-ttu-id="fba5c-104">VETRO 模式是常見的複合模式結合多個訊息接收時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="fba5c-104">The VETRO pattern is a common composite pattern that combines multiple actions taken on a message when it is received.</span></span> <span data-ttu-id="fba5c-105">該詞彙 VETRO 就代表驗證、 擴充、 轉換、 路由、 營運的 Fedramp 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="fba5c-105">The term VETRO is an acronym that stands for Validate, Enrich, Transform, Route, Operate.</span></span> <span data-ttu-id="fba5c-106">在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，可以當做個別階段關聯的接收位置的管線中處理這些動作。</span><span class="sxs-lookup"><span data-stu-id="fba5c-106">In the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], these actions can be handled as individual stages in the pipeline associated with the receive location.</span></span> <span data-ttu-id="fba5c-107">如需有關如何實作每個階段的詳細資訊，請參閱重要案例及開發工作。</span><span class="sxs-lookup"><span data-stu-id="fba5c-107">For more information about how each of these stages can be implemented, see Key Scenarios and Development Tasks.</span></span>  
  
## <a name="request-response"></a><span data-ttu-id="fba5c-108">要求-回應</span><span class="sxs-lookup"><span data-stu-id="fba5c-108">Request-Response</span></span>  
 <span data-ttu-id="fba5c-109">要求-回應模式會定義要求服務或合作對象傳送訊息並傳回預期從目的地服務的回覆訊息的解決方案。</span><span class="sxs-lookup"><span data-stu-id="fba5c-109">The Request-Response pattern defines a solution in which a service or party sends a request message and expects a reply message in return from the destination service.</span></span> <span data-ttu-id="fba5c-110">如需此模式的詳細說明，請參閱[要求-回覆](http://go.microsoft.com/fwlink/?LinkId=186849)([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) 上的企業整合模式站台。</span><span class="sxs-lookup"><span data-stu-id="fba5c-110">For a detailed description of this pattern, see [Request-Reply](http://go.microsoft.com/fwlink/?LinkId=186849) ([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) on the Enterprise Integration Patterns site.</span></span>  
  
 <span data-ttu-id="fba5c-111">如需如何實作此模式的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="fba5c-111">For more information about how to implement this pattern, see the following resources:</span></span>  
  
-   [<span data-ttu-id="fba5c-112">如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由</span><span class="sxs-lookup"><span data-stu-id="fba5c-112">How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern</span></span>](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
-   [<span data-ttu-id="fba5c-113">安裝及執行路線上手範例</span><span class="sxs-lookup"><span data-stu-id="fba5c-113">Installing and Running the Itinerary On-Ramp Sample</span></span>](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)