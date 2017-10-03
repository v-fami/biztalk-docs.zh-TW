---
title: "定義路由和訊息轉換服務引動過程使用旅 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6f2448e-a5a7-496c-86d3-47f12e6f1251
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975c830f73e0de362b25f312a8d41c4b15368cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-service-invocations-using-itineraries"></a>定義路由和訊息轉換服務使用旅的引動過程
在此使用案例，提交進行處理的訊息會包含路線的 SOAP 標頭描述要執行的服務和其解析需求的清單。 具體而言，轉換和路由服務會定義，每個選擇性需要透過通用描述、 探索與整合 (UDDI)、 商務規則引擎原則、 XML 路徑語言 (XPath) 或靜態查閱解析。 此使用案例可以透過在發行訊息時，將其他服務加入至路線擴充。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供兩種類型的路線上坡道提升： 支援單向通訊及支援要求-回應實例。 動態解析機制可以使用在路線資訊，來查閱端點或動態地繫結至端點，因為沒有為 Microsoft BizTalk Server 包含特定端點的路由詳細資料的需求。 圖 1 所示處理程序的圖解的檢視。  
  
 ![定義路由服務引動過程](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3 DefiningRoutingServiceInvocation")  
  
 **圖 1**  
  
 **定義路由和訊息轉換服務引動過程使用旅**  
  
 隨附的行程上手範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它會顯示如何建立包含解析，路由的行程和服務驗證為一系列的路線步驟定義的引動過程指示如何[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]和 BizTalk Server 會處理訊息使用發行-訂閱的功能BizTalk Server。 單向和要求-回應 」 範例隨附。  
  
 如需詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。