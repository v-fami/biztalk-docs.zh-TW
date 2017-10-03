---
title: "定義路由和訊息透過多個協調流程，使用行程轉換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63141b83-798e-40d0-908d-6b7649923e69
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c5a87b06700794dca6c4aae9588c3068b98d995
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-through-multiple-orchestrations-using-itineraries"></a>定義路由和訊息的轉換，透過多個協調流程，使用行程
在此使用案例，提交進行處理的訊息會包含路線的 SOAP 標頭描述要執行的服務和其解析需求的清單。 路線指定一或多個 Microsoft BizTalk Server 協調流程，訊息將會用來傳遞處理週期。 （選擇性） 路線可以包含用來決定端點或訊息的轉換需求的動態路由資訊。 圖 1 所示處理程序的圖解的檢視。  
  
 ![定義路由傳送多個協調流程](../esb-toolkit/media/ch3-definingroutingmultipleorchestrations.gif "Ch3 DefiningRoutingMultipleOrchestrations")  
  
 **圖 1**  
  
 **定義多個協調流程，使用行程透過路由和訊息轉換**  
  
 隨附的行程上手範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它會顯示如何建立包含解析，路由的行程和服務驗證為一系列的路線步驟定義的引動過程指示如何[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，BizTalk Server 會處理輸入的訊息。 單向和要求-回應 」 範例隨附。  
  
 如需詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。