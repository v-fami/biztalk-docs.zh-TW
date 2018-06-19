---
title: SOAP 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP adapters, receive adapters
- receive adapters, SOAP adapters
ms.assetid: bb968fa8-0515-4f3a-bb39-9effb83e960c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fac19580d6083ed1b0d4be315d3285acf14fcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278390"
---
# <a name="soap-receive-adapter"></a>SOAP 接收配接器
您可以使用 SOAP 接收配接器來接收 Web 服務要求。 SOAP 接收配接器會建立 BizTalk 訊息物件，並將關聯的屬性升級為訊息內容。  
  
 SOAP 接收配接器 URI 必須聯結至一或多個 BizTalk 協調流程或結構描述已經發行為 web 服務與**BizTalk Web 服務發佈精靈**。 已發佈的 Web 服務會公開一或多個 Web 方法，這些方法都與 BizTalk 組件中的一或多個 BizTalk Server 協調流程或結構描述相互關聯。 實際上，已發佈的 Web 服務是做為 BizTalk 協調流程或結構描述的伺服器 Proxy，在用戶端與 BizTalk 協調流程或結構描述之間轉寄要求和回應。 如需有關發佈 BizTalk 協調流程或結構描述為 web 服務，請參閱[發佈 Web 服務](../core/publishing-web-services.md)。  
  
 使用 SOAP 配接器的接收位置可以設定為單向或要求回應 (雙向)。 當單向接收位置設定為使用 SOAP 配接器時，相關聯的 Web 服務會叫用接收埠所繫結的 BizTalk 組件，並將要求狀態傳回用戶端。 當要求回應 (雙向) 接收位置設定為使用 SOAP 配接器時，相關聯的 Web 服務會叫用接收埠所繫結的 BizTalk 組件，並將回應文件傳回用戶端。 如需有關要求回應訊息，請參閱[要求-回應傳訊](../core/request-response-messaging.md)。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是 SOAP 配接器？](../core/what-is-the-soap-adapter.md)   
 [SOAP 配接器安全性建議](../core/soap-adapter-security-recommendations.md)