---
title: "案例範例路線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d438580-2b24-493c-a7d9-27632a75459c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9359a6fb3d0ce4d4f0d8fbd787c0d6a30f0f499
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-sample-itinerary-scenarios"></a>路線案例的範例
下表列出路線上手範例包含所有預先定義的行程檔案。 這些位於 \Source\Samples\Itinerary\Itineraries 資料夾中。  
  
|檔案名稱|Description|  
|---------------|-----------------|  
|Disassembler_OneWay MessageTransform-MessageRouting MessgeSendPort.xml|這個行程示範預先定義的訊息流程，時送出至路線上手，指示要執行地圖，以針對提交的訊息，然後將轉換後的訊息路由至 n 個位置透過自訂動態的 Microsoft BizTalk傳送埠。 與服務相關聯的解析程式數目會決定路由的數目。 所有轉換和路由，就會發生在 BizTalk 傳訊層中，使用 ESB 發送器管線元件所支援的選擇性路由訊息服務。 服務會在路線內相關聯的 「 解決者 」 會決定路由的位置。 執行這個行程會產生下列訊息：|  
||在資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\Out 2 則訊息|  
||FTP 資料夾中的 1 訊息： FTP://localhost/out/%MessageID%.xml|  
||MQSeries 佇列中的 1 訊息： MQS://localhost/ESB。DEP 來管理。Sample.QueueManager/TEST。OUT/%MessageID.xml|  
|Disassembler_OneWay-MessageTransform-MessgeSendPort.xml|這個行程示範，提交至路線上手，會指示執行地圖，以針對提交的訊息，然後路由傳送至 BizTalk 轉換的訊息到 n 個位置透過自訂的動態傳送埠的預先定義的訊息流程。 與服務相關聯的解析程式數目會決定路由的數目。 全部 」 轉換和路由在 BizTalk 傳訊層，就會發生。 服務會在路線內相關聯的 「 解決者 」 會決定路由的位置。 執行這個行程會產生下列訊息：|  
||在資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\Out 2 則訊息|  
||FTP 資料夾中的 1 訊息： FTP://localhost/out/%MessageID%.xml|  
||MQSeries 佇列中的 1 訊息： MQS://localhost/ESB。DEP 來管理。Sample.QueueManager/TEST。OUT/%MessageID.xml|  
|OneWay MessageTransform-MessageRouting MessgeSendPort.xml|這個行程示範，提交至路線上手，會指示執行地圖，以針對提交的訊息，然後路由傳送至 BizTalk 轉換的訊息的單一位置透過自訂的動態傳送埠的預先定義的訊息流程。 所有轉換和路由，就會發生在 BizTalk 傳訊層中，使用 ESB 發送器管線元件所支援的選擇性路由訊息服務。 執行這個行程 \Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾中產生單一訊息。|  
|OneWay-MessageTransform-MessgeSendPort.xml|這個行程示範，提交至路線上手，會指示執行地圖，以針對提交的訊息，然後路由傳送至 BizTalk 轉換的訊息的單一位置透過自訂的動態傳送埠的預先定義的訊息流程。 所有的轉換和路由在 BizTalk 傳訊層，就會發生。 執行這個行程 \Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾中產生單一訊息。|  
|OneWay MessgeSendPort.xml|這個行程示範時送出至路線上手，會指示 BizTalk 來路由傳送, 訊息的單一位置透過自訂的動態傳送埠的預先定義的訊息流程。 所有的路由，就會發生在 BizTalk 傳訊層。 執行這個行程 \Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾中產生單一訊息。|  
|OneWay OrchTransform-OrchRoutingGroup MessgeSendPort.xml|這個行程示範預先定義的訊息的範例資料流程，時送出至路線上手，指示要執行的對應，針對使用自訂協調流程服務送出訊息的 BizTalk。 然後，第二個自訂協調流程服務會處理輸出，並將四個訊息路由至三個位置。 此服務相關聯的解析程式決定路由的下列位置：|  
||在資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\Out 2 則訊息|  
||FTP 資料夾中的 1 訊息： FTP://localhost/out/%MessageID%.xml|  
||MQSeries 佇列中的 1 訊息： MQS://localhost/ESB。DEP 來管理。Sample.QueueManager/TEST。OUT/%MessageID.xml|  
||最後，路線向下路由傳送原始訊息的單一位置 （\Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾） 的自訂動態傳送埠。 所有的轉換和路由會透過 BizTalk 傳訊和協調流程服務的組合進行。 執行此計劃的範例會產生五個訊息。|  
|TwoWay MessageTransform-MessageRouting MessageTwoWaySendPort.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示要執行地圖，以針對提交的訊息，然後將轉換的訊息傳送至 Web 服務，透過 BizTalk自訂的動態雙向傳送埠。 這個範例會使用 ESB 發送器管線元件所支援的選擇性路由訊息服務。 所有的轉換和路由會發生在 BizTalk 傳訊層。 執行這個行程範例時，會產生單一回應訊息，路線將路由至原始呼叫端，會在此情況下路線測試用戶端。|  
|TwoWay-MessageTransform-MessageRouting-MessageTwoWaySendPort-MessageTransform.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示要執行地圖，以針對提交的訊息，然後將轉換的訊息傳送至 Web 服務，透過 BizTalk自訂的動態雙向傳送埠。 從 Web 服務會傳回回應路線指示 BizTalk 執行針對回應訊息的對應。 這個範例會使用 ESB 發送器管線元件所支援的選擇性路由訊息服務。 所有的轉換和路由會發生在 BizTalk 傳訊層。 執行這個行程範例時，會產生單一回應訊息，路線將路由至原始呼叫端，會在此情況下路線測試用戶端。|  
|TwoWay-MessageTransform-MessageTwoWaySendPort.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示要執行地圖，以針對提交的訊息，然後將轉換的訊息傳送至 Web 服務，透過 BizTalk自訂的動態雙向傳送埠。 所有的轉換和路由會發生在 BizTalk 傳訊層。 執行這個行程範例時，會產生單一回應訊息，路線將路由至原始呼叫端，會在此情況下路線測試用戶端。|  
|TwoWay MessageTransform-MessageTwoWaySendPort MessageTransform.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示要執行地圖，以針對提交的訊息，然後將轉換的訊息傳送至 Web 服務，透過 BizTalk自訂的動態雙向傳送埠。 從 Web 服務會傳回回應路線指示 BizTalk 執行針對回應訊息的對應。 所有的轉換和路由會發生在 BizTalk 傳訊層。 執行這個行程範例會產生單一回應訊息，路線會路由傳送至原始呼叫端 （在此情況下，路線測試用戶端）。|  
|TwoWay MessageTransform-OrchRoutingGroup OrchTwoWayCustom.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示 BizTalk 執行針對使用訊息處理服務已提交之訊息的對應。 路線然後會將輸出傳遞至程序的自訂協調流程服務。 與服務相關聯的解析程式決定下列四個路由位置：|  
||在資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\Out 2 則訊息|  
||FTP 資料夾中的 1 訊息： FTP://localhost/out/%MessageID%.xml|  
||MQSeries 佇列中的 1 訊息： MQS://localhost/ESB。DEP 來管理。Sample.QueueManager/TEST。OUT/%MessageID.xml|  
||最後，路線將原始訊息傳遞至另一個會將回應訊息傳送至原始的呼叫端 （在此情況下，路線測試用戶端） 的自訂雙向的直接繫結協調流程服務。 全部 」 轉換和路由透過 BizTalk 傳訊和協調流程服務的組合，就會發生。|  
|TwoWay OrchTransform-OrchRoutingGroup OrchTwoWayCustom.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示要執行的對應，針對使用自訂協調流程服務送出訊息的 BizTalk。 路線然後會將輸出傳遞至程序的自訂協調流程服務。 與服務相關聯的解析程式決定下列四個路由位置：|  
||在資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\Out 2 則訊息|  
||FTP 資料夾中的 1 訊息： FTP://localhost/out/%MessageID%.xml|  
||MQSeries 佇列中的 1 訊息： MQS://localhost/ESB。DEP 來管理。Sample.QueueManager/TEST。OUT/%MessageID.xml|  
||最後，路線會將原始訊息路由至另一個會將回應訊息傳送至原始的呼叫端 （在此情況下，路線測試用戶端） 的自訂雙向的直接繫結協調流程服務。 所有的轉換和路由透過 BizTalk 傳訊和協調流程服務的組合，就會發生。|  
|TwoWay TwoWayCustom （直接繫結）.xml|這個行程示範預先定義雙向 （要求/回應） 訊息流程，時送出至路線上手，指示 BizTalk 來執行自訂雙向的直接繫結協調流程服務。 此服務會將回應訊息路由回到原始的呼叫端，在此情況下路線測試用戶端。|