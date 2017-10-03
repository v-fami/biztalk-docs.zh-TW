---
title: "訊息轉換模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef41642-d33b-4878-be65-ef336530647f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badfb450b51aebbdf81b2beccdeac98fc549bcb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-transformation-patterns"></a>訊息轉換模式
訊息轉換模式定義經過證實的轉換進行額外處理，或符合預期的文件格式的訊息將送往之服務的訊息指導方針。 訊息可能需要轉換，因為已接收訊息的結構不是預期的標準，或因為訊息必須從非標準格式轉換成 XML。  
  
## <a name="message-translator"></a>訊息轉譯程式  
 訊息轉譯程式模式會定義使用不相容的資料格式的系統之間進行通訊的解決方案。 比方說，用戶端應用程式可能會傳送一般檔案要求訊息，然後才能進行其他處理程序必須轉換成 XML。 如需此模式的詳細說明，請參閱[訊息轉譯程式](http://go.microsoft.com/fwlink/?LinkId=186845)([http://go.microsoft.com/fwlink/?LinkId=186845](http://go.microsoft.com/fwlink/?LinkId=186845)) 上的企業整合模式站台。  
  
 此模式在路線設計工具中的實作是組合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]轉換服務 」 和 「 單一的解析程式。 路線轉換服務會負責使用解析程式屬性來定義轉換所需的成品將訊息轉換。 解析程式實作會負責提供轉換的設定，也就是靜態或動態，根據的解析程式設定。  
  
 訊息轉譯程式模式的範例實作，請參閱下列資源：  
  
-   [安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
## <a name="normalizer"></a>正規化程式  
 正規化程式模式是資料模型轉換模式擴充功能。 此模式會定義以不同格式的方案中，從多個來源接收訊息的語意相等，但訊息到達。 如需此模式的詳細說明，請參閱[正規化程式](http://go.microsoft.com/fwlink/?LinkId=186847)([http://go.microsoft.com/fwlink/?LinkId=186847](http://go.microsoft.com/fwlink/?LinkId=186847)) 上的企業整合模式站台。  
  
 此模式在路線設計工具中的實作是組合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]轉換服務 」 和 「 單一的解析程式。 路線轉換服務會負責使用解析程式屬性來定義轉換所需的成品將訊息轉換。 解析程式實作會負責以動態方式解析指定的訊息類型的適當 Microsoft BizTalk 對應。  
  
 正規化程式模式的範例實作，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。  
  
## <a name="content-enricher"></a>內容 Enricher  
 內容 Enricher 模式定義為接收之訊息可能會包含所需的目標系統，才能適當地處理訊息的所有資料的解決方案。 比方說，傳送的服務可能包含郵遞區號不備援狀態程式碼中，但接收服務所預期的訊息，其中包含狀態碼和郵遞區號。接收服務可以處理所接收的訊息之前需要額外的資料。 如需此模式的詳細說明，請參閱[內容 Enricher](http://go.microsoft.com/fwlink/?LinkId=186848) ([http://go.microsoft.com/fwlink/?LinkId=186848](http://go.microsoft.com/fwlink/?LinkId=186848)) 上的企業整合模式站台。  
  
 內容 Enricher 模式的範例實作，請參閱[安裝及執行 「 訊息豐富 」 範例](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)應用程式。