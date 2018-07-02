---
title: 要求-回應傳訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- request/response messaging, about request/response messaging
- SOAP adapters, message processing
- SOAP adapters, request/response messaging
- request/response messaging
- patterns, messages
- messages, request/response messaging
- request/response messaging, processing
- request/response messaging, SOAP adapters
- messages, patterns
ms.assetid: 1a2f79b5-1f44-4191-8ce1-b3c9043be4f4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8d58fbcac6803adb36495f1aa9982909580e1c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985071"
---
# <a name="request-response-messaging"></a>要求-回應傳訊
在要求/回應傳訊模式中，一個合作對象會傳送要求訊息，而接收的合作對象則會回傳回應訊息。 要求/回應處理的兩個典型範例，是瀏覽器與使用 HTTP 配接器的 Web 伺服器之間的互動，以及使用「簡單物件存取通訊協定」(SOAP) 配接器的 Web 服務處理之間的互動。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，要求與回應訊息都是透過典型的發佈/訂閱方式處理的。 在您微調 BizTalk 應用程式效能時，這是一個需要瞭解的重要考量，因為對於個別訊息，需要高輸送量的系統與需要低延遲的系統兩者在設定上有所不同。  
  
 ![要求&#47;回應傳訊](../core/media/arch-request-response-1.gif "arch_request-回應-1")  
  
 要求/回應模式的接收配接器收到訊息時，BizTalk Server 會先發佈要求訊息到 MessageBox 資料庫。 接著，適當的訂閱者會收到此訊息，該訂閱者可能是與接收埠繫結的協調流程。 此訂閱者會編寫回應訊息，連同屬性發佈到 MessageBox，這個屬性可讓訊息傳回到送來要求的接收埠。 最後，要求的發佈者 (即提交要求的接收配接器) 會拾取回應訊息，並將此訊息傳回到呼叫應用程式。 下圖提供這些步驟的詳細圖解。  
  
 ![要求&#47;SOAP 配接器收到的回應訊息](../core/media/arch-request-response-2.gif "arch_request 回應 2")  
  
 **SOAP 配接器接收的要求/回應訊息的流程**  
  
1. SOAP 配接器提交訊息到結束點管理員。  
  
2. 結束點管理員將訊息發佈到 MessageBox。  
  
3. 與接收埠繫結而因此訂閱訊息的協調流程，會接收訊息並進行處理。  
  
4. 協調流程傳送發佈到 MessageBox 的回應訊息。  
  
5. 結束點管理員接收回應訊息。  
  
6. 結束點管理員將回應傳回到 SOAP 配接器  
  
   如果不瞭解內部實作方式，可能會忽略這類行為對效能的影響。 BizTalk Server 最初是針對高輸送量進行微調，但是它也可以設定給具有較低輸送量且較低延遲的環境使用，特別是要求/回應實例中。 在此實例中的微調需要考量幾項因素。 首先，訂閱者是透過輪詢機制發現有發佈的訊息。 若是輪詢間隔設定得太長，可能會造成要求/回應模式的互動延遲比預期還要大。  
  
   請注意，在此實例中需要滿足兩個訂閱：初始訊息的訂閱以及回應訊息的訂閱，而這樣會增加對此輪詢間隔的影響。 第二，接收配接器的設定是以不同大小的批次方式將訊息插入到 MessageBox。 大部分的配接器可讓您透過一般配接器組態介面或是 BizTalk Server 或登錄中的參數來設定批次大小。 若是批次大小設定得太大，可能會增加個別訊息的延遲。 如需有關的效能特性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 規劃持續性效能](../core/planning-for-sustained-performance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段架構](../core/runtime-architecture.md)