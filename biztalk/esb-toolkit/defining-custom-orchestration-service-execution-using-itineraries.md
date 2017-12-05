---
title: "定義自訂協調流程服務執行使用旅 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6089169d-2fa1-4f81-afe1-db9d90a10382
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9336969db2c90168bf7c398276205043b06504ce
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="defining-custom-orchestration-service-execution-using-itineraries"></a>定義自訂協調流程服務執行，使用行程
在此使用案例，提交進行處理的訊息會包含路線的 SOAP 標頭描述要執行的服務和其解析需求的清單。 路線指定一個或多個自訂協調流程處理序訊息將會用來傳遞處理週期。 自訂協調流程具有路線和其他訊息內容中公開的自訂屬性的完整控制權。 （選擇性） 路線可以包含動態解析資訊會決定轉換需求和端點的訊息。 圖 1 所示處理程序的圖解的檢視。  
  
 ![定義自訂協調流程](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3 DefiningCustomOrchestration")  
  
 **圖 1**  
  
 **定義自訂協調流程服務執行，使用行程**  
  
 隨附的行程上手範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它會顯示如何建立包含一系列的路線定義 ESB 和 BizTalk Server 如何處理輸入的訊息的步驟解析、 路由及服務引動過程指示的行程。 單向和要求-回應 」 範例隨附。  
  
 如需詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。