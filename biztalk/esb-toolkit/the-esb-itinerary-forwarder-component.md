---
title: "ESB 路線的轉寄站元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 607cc8a0-4964-4751-baca-c3329983c98b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c61643423021701186745ab4275520cb14d3ceca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-forwarder-component"></a>ESB 路線的轉寄站元件
行程必須依序叫用多個 Web 服務時，會使用 ESB 行程轉寄站元件。 使用此元件在接收管線，與雙向匝道的回應端相關聯。  
  
## <a name="installation"></a>安裝  
 自動安裝 ESB 核心安裝**路線轉寄站**元件的 BizTalk Server 管線元件資料夾中。  
  
## <a name="how-it-works"></a>運作方式  
 當 Microsoft BizTalk 收到訊息，以透過雙向接收埠，訊息會發佈到 Messagebox 資料庫時，建立執行個體訂閱。 此訂用帳戶包含**EpmRRCorrelationToken**升級屬性和**RouteDirectToTP**升級屬性。 當 「 訂閱者 」 （協調流程或雙向傳送埠） 傳回回應訊息時，這些提升的屬性比對訂閱與通過傳送管線的接收埠，會立即傳回回應。  
  
 ESB 行程轉寄站應該用於回應管線的雙向匝道匝道呼叫要求-回應 Web 服務。 元件藉由變更會干擾一般 BizTalk 處理序**RouteDirectToTP**升級的屬性為 False，以確保在回應不會傳回至起始接收埠。 達到路線的最後一個步驟之後， **RouteDirectToTP**屬性變更回**True**，因此傳回的結果來起始上手。  
  
## <a name="using-the-esb-itinerary-forwarder-component"></a>使用 ESB 路線的轉寄站元件  
 ESB ItineraryForwarder 元件新增至接收管線，然後使用管線的雙向匝道的回應部分。 建立行程的鏈結多個 Web 服務，不論轉換路線服務之前，或在服務之間。 如需如何使用 ESB 行程轉寄站元件的範例，請參閱[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。