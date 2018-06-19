---
title: 何謂 WCF-WSHttp 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, about WCF-WSHttp adapters
ms.assetid: 183a19e3-10b1-403f-b274-34a441e774d1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5d244dcfe26cf10bc4ae10c63374eef0824444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289334"
---
# <a name="what-is-the-wcf-wshttp-adapter"></a>何謂 WCF-WSHttp 配接器？
您可以使用 WCF-WSHttp 配接器，利用具有文字或 Message Transmission Optimization Mechanism (MTOM) 編碼的 HTTP 或 HTTPS 傳輸，與能夠瞭解下一代 Web 服務標準的服務和用戶端進行跨電腦的通訊。 WCF-WSHttp 配接器可完整存取 SOAP 安全性、可靠性和交易等功能。  
  
 下表摘要說明 WCF-WSHttp 配接器的特性。  
  
|Description|特性|  
|-----------------|--------------------|  
|互通性等級|WS-Profile|  
|訊息編碼|文字或 MTOM|  
|界限|跨電腦|  
|傳輸通訊協定|HTTP 或 HTTPS|  
|安全性模式|無 (None)、訊息 (Message)、傳輸 (Transport ) 和 TransportWithMessageCredential。|  
|用戶端驗證機制|傳輸安全性與訊息安全性|  
|支援 WS-ReliableMessaging|否|  
|支援 WS-AtomicTransaction|是|  
|支援單向傳訊|是|  
|支援雙向傳訊|是|  
|接收配接器的主控件類型|外掛式|  
|傳送配接器的主控件類型|內含式|  
  
 WCF-WSHttp 配接器是由兩個配接器所組成：接收配接器和傳送配接器。  
  
 **Wcf-wshttp 接收配接器**  
  
 您可以使用 WCF-WSHttp 接收配接器，透過 HTTP 或 HTTPS 通訊協定接收 WCF 服務要求。 使用 WCF-WSHttp 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。  
  
 **Wcf-wshttp 傳送配接器**  
  
 您可以使用 WCF-WSHttp 傳送配接器，利用 HTTP 或 HTTPS 通訊協定，透過無類型合約來呼叫 WCF 服務。  
  
 如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)