---
title: "配接器訊息交換模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54a3fc8f-33d0-4b7e-ad4c-b00912dc3328
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f42368d8687bbed4cbce60243a3b8528364b5fda
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-message-exchange-patterns"></a>配接器訊息交換模式
BizTalk「配接器架構」支援豐富的訊息交換模式，可供配接器在許多功能強大的傳訊實例中使用。  
  
## <a name="one-way-asynchronous"></a>單向 (非同步)  
 其重要概念是訊息流程為單一方向。  
  
 在這個訊息交換模式中，訊息流程透過配接器到達 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 「傳訊引擎」會將訊息發佈至 MessageBox 資料庫。 如果協調流程目前訂閱該類型訊息，便會將訊息傳送至協調流程。  
  
 在處理訊息之後，協調流程會將訊息發佈回 MessageBox 資料庫中，然後再傳送至配接器，以傳輸至特定結束點。  
  
 訊息提交至引擎之後，不需要回應。 在輸出端，訊息傳輸之後，也不需要回應。 這一般稱為非同步傳訊，就許多方面來說是引擎使用於所有傳訊實例的基本建置區塊。  
  
## <a name="request-response-style-protocols-sync-on-async"></a>要求-回應樣式通訊協定 (Sync-on-Async)  
 要求-回應實例包含接收要求訊息、處理該訊息，以及傳送回應訊息。 它也稱為同步-非同步混合處理 (Sync-on-Async)，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 基礎架構基於擴充性理由是非同步的。 不過，除了非同步交換，BizTalk「傳訊引擎」還會公開同步訊息交換模式。 為了執行此操作，引擎會連結一些非同步訊息交換以公開同步介面，在向外擴充的架構上處理要求和回應訊息關聯的複雜工作。  
  
 例如，網頁上，檢查清查可能發出 SOAP 呼叫對 BizTalk SOAP 接收配接器。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會協調一連串彙總資訊，並傳回一個 SOAP 回應中的 Web 服務。 對用戶端來說，這看起來是同步 SOAP 呼叫，但實際上，這是引擎組合一些非同步訊息交換。  
  
## <a name="solicit-response-style-protocols"></a>請求-回應樣式通訊協定  
 這個實例始於傳送請求訊息，並以接收回應訊息結束。 這稱為請求-回應，因為傳送的初始訊息是向結束點請求回應訊息。 這種訊息交換模式的實例中，協調流程可能需要發出輸出 HTTP 呼叫 (回應的請求) 並等待回應。  
  
## <a name="request-multiresponse"></a>要求-多重回應  
 本實範例與要求-回應實例相似。 不過，在本實例中，可能針對指定的要求傳回多個回應。 API 允許指定逾時值，而且逾時期間內收到的所有回應都會傳回至接收配接器。  
  
## <a name="loop-back"></a>回送  
 本實範例與要求-回應實例相似。 要求訊息照常發佈，但引擎會確定回應訊息傳回至原來發佈要求訊息的相同配接器執行個體。 因為要求訊息是發佈至 MessageBox 資料庫，所以追蹤基礎結構會確定要求和回應訊息都受到追蹤。 這也是在訊息上叫用傳送管線處理，然後立即將輸出訊息傳回至配接器進行後續處理的好方法。  
  
 這個實例的例子是用戶端需要訊息的回條。 輸入訊息會發佈到 MessageBox 資料庫。 此訊息和回條會在相同批次中傳回至配接器。 在此情況下，會複製輸入訊息，其中一個執行個體傳回至用戶端，另一個則透過正常方式處理。 本特殊實例也需要撰寫自訂的 XML 解譯器。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是配接器架構？](../core/what-is-the-adapter-framework.md)