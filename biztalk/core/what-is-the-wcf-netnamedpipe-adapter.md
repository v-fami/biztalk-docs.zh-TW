---
title: 何謂 WCF-NetNamedPipe 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, about WCF-NetNamedPipe adapters
ms.assetid: b9f84256-e49d-4ee2-b0fa-d3f692ade1d4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c73a670139690c4a27d4784c6ad23225492f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netnamedpipe-adapter"></a>何謂 WCF-NetNamedPipe 配接器？
WCF-NetNamedPipe 配接器可在服務與用戶端皆為 WCF 架構的環境中，提供相同電腦上的跨處理序通訊。 它可以完整存取 SOAP 可靠性和交易功能。 這個配接器會使用具名管道傳輸，而且訊息具有二進位編碼。 不過，此配接器無法用於跨電腦的通訊。  
  
 下表摘要說明 WCF-NetNamedPipe 配接器的特性。  
  
|Description|特性|  
|-----------------|--------------------|  
|互通性等級|.NET 設定檔|  
|訊息編碼|二進位|  
|界限|跨處理序|  
|傳輸通訊協定|具名管道|  
|安全性模式|「無」與「傳輸」|  
|用戶端驗證機制|傳輸安全性與訊息安全性|  
|支援 WS-ReliableMessaging|否|  
|支援 WS-AtomicTransaction|是|  
|支援單向傳訊|是|  
|支援雙向傳訊|是|  
|接收配接器的主控件類型|內含式|  
|傳送配接器的主控件類型|內含式|  
  
 WCF-NetNamedPipe 配接器是由兩個配接器所組成：接收配接器和傳送配接器。  
  
 **Wcf-netnamedpipe 接收配接器**  
  
 您可以使用 WCF-NetNamedPipe 接收配接器，透過具名管道傳輸來接收 Web 服務要求。 使用 WCF-NetNamedPipe 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。  
  
 **Wcf-netnamedpipe 傳送配接器**  
  
 您可以使用 WCF-NetNamedPipe 傳送配接器，透過具名管道傳輸並經由無類型合約來呼叫 Web 服務。  
  
 如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-netnamedpipe 配接器](../core/configuring-the-wcf-netnamedpipe-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)