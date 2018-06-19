---
title: 設定 AS2 方案的通訊埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715358b1-4226-476b-b0de-2b91434aa24c
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8f02c5de0edd7956f00e10ce8782e4865033076
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233582"
---
# <a name="configuring-ports-for-an-as2-solution"></a>設定 AS2 方案的連接埠
您可以使用下列接收埠和傳送埠，透過 AS2 來傳輸 EDI 訊息和非 EDI 訊息：  
  
 **接收埠**  
  
|負責接收|負責傳送|連接埠類型|  
|----------------|-------------|------------------|  
|EDI 或非 EDI 訊息或是通知|MDN 回應 (若是在同步模式下) 或 HTTP 回應 (若是在非同步模式下)|雙向要求-回應 HTTP 接收埠|  
|MDN 回應|-|單向 HTTP 接收埠|  
  
 **傳送埠**  
  
|負責傳送|負責接收|連接埠類型|  
|-------------|----------------|------------------|  
|EDI 或非 EDI 訊息或是通知<br /><br /> (根據協議決定路由)|-|靜態單向 HTTP 傳送埠|  
|EDI 或非 EDI 訊息或是通知<br /><br /> (根據訊息內容決定路由)|MDN 回應|動態雙向請求-回應 HTTP 傳送埠|  
|EDI 或非 EDI 訊息或是通知<br /><br /> (根據訊息內容決定路由)|-|動態單向 HTTP 傳送埠|  
|非同步 MDN 回應<br /><br /> (根據訊息內容決定路由)|-|動態單向傳送埠|  
|非同步 MDN 回應|-|靜態單向傳送埠|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定透過 AS2 接收訊息的連接埠](../core/configuring-a-receive-port-for-messages-over-as2.md)  
  
-   [設定內送 Mdn 的接收埠](../core/configuring-a-receive-port-for-incoming-mdns.md)  
  
-   [透過 AS2 的訊息設定靜態傳送埠](../core/configuring-a-static-send-port-for-messages-over-as2.md)  
  
-   [透過 AS2 的訊息設定動態傳送埠](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)  
  
-   [設定透過 AS2 之非同步 Mdn 的靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)  
  
-   [設定透過 AS2 之非同步 Mdn 的動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)