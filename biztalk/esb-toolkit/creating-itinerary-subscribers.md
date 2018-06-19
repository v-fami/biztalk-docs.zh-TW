---
title: 建立計劃的訂閱者 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84a76aeb-8d40-490a-8ae6-7abfdd2d2573
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f470ed5268c445ab3b7175f1cba07ff1de52a27
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007191"
---
# <a name="creating-itinerary-subscribers"></a><span data-ttu-id="d4f87-102">建立計劃的訂閱者</span><span class="sxs-lookup"><span data-stu-id="d4f87-102">Creating Itinerary Subscribers</span></span>
<span data-ttu-id="d4f87-103">BizTalk Server 會自動發佈到 Messagebox 資料庫中; 透過接收管線抵達訊息這可讓訊息供拾取相關的 「 訂閱者 」。</span><span class="sxs-lookup"><span data-stu-id="d4f87-103">BizTalk Server automatically publishes messages arriving through a receive pipeline to the Message Box database; this makes the messages ready for pick-up by the relevant subscriber.</span></span> <span data-ttu-id="d4f87-104">此分離的方法是慣用的方法來開發 BizTalk 解決方案，因為它提供最大的彈性、 可調整，並使用發佈-訂閱機制。</span><span class="sxs-lookup"><span data-stu-id="d4f87-104">This decoupled approach is the preferred way to develop BizTalk solutions because it provides maximum flexibility, scales well, and uses the publish-subscribe mechanism.</span></span>  
  
 <span data-ttu-id="d4f87-105">有兩種方式可建立路線服務的訂閱者：</span><span class="sxs-lookup"><span data-stu-id="d4f87-105">There are two ways to create an itinerary service subscriber:</span></span>  
  
-   [<span data-ttu-id="d4f87-106">使用傳送埠作為路線服務訂閱者</span><span class="sxs-lookup"><span data-stu-id="d4f87-106">Using a Send Port as an Itinerary Service Subscriber</span></span>](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)  
  
-   [<span data-ttu-id="d4f87-107">使用協調流程作為路線服務訂閱者</span><span class="sxs-lookup"><span data-stu-id="d4f87-107">Using an Orchestration as an Itinerary Service Subscriber</span></span>](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md)