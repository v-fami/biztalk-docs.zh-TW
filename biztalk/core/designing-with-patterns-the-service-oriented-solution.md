---
title: 使用模式設計： 服務導向解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- patterns [service solutions], examples
- examples, programming patterns
- patterns [service solutions], designing
- designing, programming patterns
ms.assetid: c196cd9d-2b2d-4548-bc7d-26196f7c2878
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32096bfa790f52ab29eed9d4b6b849688c73c922
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970999"
---
# <a name="designing-with-patterns-the-service-oriented-solution"></a>使用模式設計： 服務導向解決方案
服務導向解決方案會示範如何將 BizTalk 應用程式公開為供其他應用程式使用的服務。 將應用程式當作服務使用，可讓其他應用程式更輕易地使用資訊以及在它們提供的服務中使用資訊。 如需服務介面查看 「 服務介面 」 [ http://go.microsoft.com/fwlink/?LinkId=46185 ](http://go.microsoft.com/fwlink/?LinkId=46185)。 如需服務導向整合的詳細資訊請參閱 < Service-Oriented Integration 網址[ http://go.microsoft.com/fwlink/?LinkId=46186 ](http://go.microsoft.com/fwlink/?LinkId=46186)。  
  
 解決方案是一個信用資訊應用程式，彙總來自其他三個不同應用程式的相關資訊後，提供資訊做為 Web 服務回應。 應用程式會合併結果，並傳回包含摘要信用資訊的一個訊息。 三個後端系統如下：  
  
- **SAP 企業系統。** SAP 後端提供客戶的整體信用限制。 解決方案會與此使用中的 SAP 配接器的後端系統通訊[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  
  
- **擱置交易系統。** 暫停交易系統會報告超過帳戶的交易總數。 解決方案會使用 Microsoft Host Integration Server (HIS) 與 Windows Server 的大型主機通訊。 解決方案也會使用 HIS 的交易整合器技術。 這些技術可讓系統以 Web 服務的方式與大型主機互動。 BizTalk 協調流程會使用這個 Web 服務。  
  
- **付款追蹤系統。** 付款追蹤系統可報告個人上次進行的付款。 這個系統使用 MQSeries。  
  
  如同您回想起的解決方案概觀，您也可以透過 MQSeries 查詢來使用非 Web 服務。 (如需應用程式的一般結構的詳細資訊，請參閱[了解服務導向解決方案](../core/understanding-the-service-oriented-solution.md))。 雖然 Web 服務是建立服務導向架構最常用的方法，但不是所有應用程式都可使用 Web 服務。 使用 BizTalk Server 解決方案，您可提供除了 Web 服務外，其他的方法讓傳統應用程式來使用服務。  
  
  MQSeries 存取可模擬傳統互動式語音回應系統可能會使用解決方案的作法。 MQSeries 存取加上 Web 服務存取，可示範一個解決方案如何被傳統應用程式及新應用程式所使用。  
  
## <a name="patterns-used-in-the-service-oriented-solution"></a>服務導向解決方案使用的模式  
 下圖顯示服務導向解決方案中簡易的模式版本。  
  
 ![服務&#45;導向解決方案模式](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")  
  
 解決方案包含四個主要部分，每一個都代表一種模式： 服務介面、 以內容為基礎的路由器、 收件者的清單和彙總工具。 服務介面代表連線到解決方案的介面機制。 內容型路由器會檢查訊息的有效性，若訊息無效則會傳送錯誤訊息。 收件者清單會將訊息傳送給三個後端應用程式。 後端應用程式回應時，彙總程式會將回應結合為單一的回應訊息。 然後回應訊息會透過服務介面回到要求者。  
  
 請注意，圖表中有許多未指定項目：  
  
-   圖表中省略了訊息轉譯程式，解決方案需要它來與外部系統通訊。  
  
-   圖表未指明如何與後端程序通訊。  
  
-   圖表也未指明服務介面的本質。  
  
-   圖表未指出要不要使用同步或非同步通訊。  
  
## <a name="see-also"></a>另請參閱  
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)   
 [轉譯模式的服務導向解決方案](../core/translating-the-patterns-of-the-service-oriented-solution.md)