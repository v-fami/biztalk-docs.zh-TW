---
title: 何謂 WCF-NetTcp 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, about WCF-NetTcp adapters
ms.assetid: 94dc24df-19a1-4701-9012-59d05b0c8abd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a741d3a4d7b7bcc80405d0fc25e37a31860523b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-nettcp-adapter"></a>何謂 WCF-NetTcp 配接器？
WCF-NetTcp 配接器可在服務與用戶端皆為 WCF 架構的環境中，提供連線的跨電腦或跨處理序通訊。 該配接器可完整存取 SOAP 安全性、可靠性和交易功能。 此配接器使用 TCP 傳輸，而且訊息具有二進位編碼。  
  
 下表摘要描述 WCF-NetTcp 配接器的特性。  
  
|Description|特性|  
|-----------------|--------------------|  
|互通性等級|.NET 設定檔|  
|訊息編碼|二進位|  
|界限|跨電腦或跨處理序|  
|傳輸通訊協定|TCP|  
|安全性模式|無 (None)、訊息 (Message)、傳輸 (Transport ) 和 TransportWithMessageCredential。|  
|用戶端驗證機制|傳輸安全性與訊息安全性|  
|支援 WS-ReliableMessaging|否|  
|支援 WS-AtomicTransaction|是|  
|支援單向傳訊|是|  
|支援雙向傳訊|是|  
|接收配接器的主控件類型|內含式|  
|傳送配接器的主控件類型|內含式|  
  
 WCF-NetTcp 配接器包含兩種配接器，也就是接收配接器和傳送配接器。  
  
 **Wcf-nettcp 接收配接器**  
  
 使用 WCF-NetTcp 接收配接器透過 TCP 通訊協定接收 WCF 服務要求。 使用 WCF-NetTcp 接收配接器的接收位置，可以設定為單向或要求-回應 (雙向)。  
  
 **Wcf-nettcp 傳送配接器**  
  
 使用 WCF-NetTcp 傳送配接器可使用 TCP 通訊協定，透過無型別合約呼叫 WCF 服務。  
  
 如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)