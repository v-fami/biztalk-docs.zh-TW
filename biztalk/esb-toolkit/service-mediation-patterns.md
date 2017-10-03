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
# <a name="service-mediation-patterns"></a>服務中繼模式
## <a name="vetovetro"></a>否決權/VETRO  
 VETRO 模式是常見的複合模式結合多個訊息接收時所採取的動作。 該詞彙 VETRO 就代表驗證、 擴充、 轉換、 路由、 營運的 Fedramp 的縮寫。 在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，可以當做個別階段關聯的接收位置的管線中處理這些動作。 如需有關如何實作每個階段的詳細資訊，請參閱重要案例及開發工作。  
  
## <a name="request-response"></a>要求-回應  
 要求-回應模式會定義要求服務或合作對象傳送訊息並傳回預期從目的地服務的回覆訊息的解決方案。 如需此模式的詳細說明，請參閱[要求-回覆](http://go.microsoft.com/fwlink/?LinkId=186849)([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) 上的企業整合模式站台。  
  
 如需如何實作此模式的詳細資訊，請參閱下列資源：  
  
-   [如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
-   [安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)