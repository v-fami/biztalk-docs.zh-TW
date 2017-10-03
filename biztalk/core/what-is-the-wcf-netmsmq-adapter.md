---
title: "何謂 WCF-NetMsmq 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-NetMsmq adapters, about WCF-NetMsmq adapters
ms.assetid: 506c5e2d-6cbe-4788-8e37-49d009dc559a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1008cc7178c38532f1781890080eacf4b5dfb56c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netmsmq-adapter"></a>何謂 WCF-NetMsmq 配接器？
WCF-NetMsmq 配接器可在服務與用戶端皆為 WCF 架構的環境中，使用佇列技術提供離線的跨電腦通訊。 它會使用「訊息佇列」(MSMQ) 傳輸，而且訊息具有二進位編碼。  
  
 下表摘要說明 WCF-NetMsmq 配接器的特性。  
  
|Description|特性|  
|-----------------|--------------------|  
|互通性等級|.NET 設定檔|  
|訊息編碼|二進位|  
|界限|跨電腦|  
|傳輸通訊協定|MSMQ|  
|安全性模式|無、訊息、傳輸和兩者。|  
|用戶端驗證機制|傳輸安全性與訊息安全性|  
|支援 WS-ReliableMessaging|不適用|  
|支援 WS-AtomicTransaction|是|  
|支援單向傳訊|是|  
|支援雙向傳訊|否|  
|接收配接器的主控件類型|內含式|  
|傳送配接器的主控件類型|內含式|  
  
> [!NOTE]
>  WCF-NetMsmq 接收配接器提取訊息的來源佇列必須先行建立。 佇列中的訊息必須是 WCF 架構，否則這些訊息會送至無法傳送的信件佇列。  
  
 WCF-NetMsmq 配接器是由兩個配接器所組成：接收配接器和傳送配接器。  
  
 **Wcf-netmsmq 接收配接器**  
  
 您可以使用 WCF-NetMsmq 接收配接器透過 MSMQ 來接收 WCF 服務要求。 使用 WCF-NetMsmq 配接器的接收位置只能設定為單向接收。  
  
 **Wcf-netmsmq 傳送配接器**  
  
 您可以使用 WCF-NetMsmq 傳送配接器，透過 MSMQ 傳輸用無類型合約來呼叫 WCF 服務。  
  
 如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-netmsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)