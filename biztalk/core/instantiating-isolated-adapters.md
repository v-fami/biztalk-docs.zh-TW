---
title: 具現化外掛式配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8359a3-b098-4bb6-87b4-d3432d2671b1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e3090252f63221547604a4fdf88388bcbf8296f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257486"
---
# <a name="instantiating-isolated-adapters"></a>讓外掛式配接器具現化
之前討論過，外掛式配接器不會由 BizTalk Server 具現化， 而是在另一個處理序中具現化及裝載。 要建立它的傳輸 proxy 的配接器負責**QueryInterface**，如**IBTTransportProxy**，然後呼叫**IBTTransportProxy**。**RegisterIsolatedReceiver**向 「 傳訊引擎。  
  
 註冊作業會要求配接器傳遞它的其中一個已設定及啟用的接收位置給傳訊引擎。 此配接器的主控件處理序認證必須是 BizTalk 外掛式主控件使用者群組的成員。 除非使用者為該群組的成員，否則在這裡單單使用模擬是不夠的。 此外，查詢此配接器是以確定它具有正確**ClassID** ，且已設定該主控件執行個體之電腦上執行。 配接器已順利註冊其傳輸 proxy 之後，其設定傳送給它所呼叫的 Load 方法使用**IPersistPropertyBag**介面。  
  
 下圖顯示 API 呼叫的順序。 藍色的介面是此配接器實作的介面。  
  
 ![](../core/media/isolated-adapter-init.gif "Isolated_adapter_init")  
  
 下列程式碼片段說明註冊 API 呼叫：  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Component.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,   
 IBaseComponent  
{  
...  
private IBTTransportProxy transportProxy;  
  
 public void Register(string uri)  
 {  
 // Create the Transport Proxy...  
 this.transportProxy =   
 (IBTTransportProxy)new BTTransportProxy();  
  
// Register on of the adapters uri’s with the TP  
 this.transportProxy.RegisterIsolatedReceiver(  
 uri,   
 (IBTTransportConfig)this );  
 }  
}  
```  
  
 **實作秘訣：** 建議配接器應進行中的計數。 此配接器應封鎖**Terminate**訊息計數達到零以前。 在接收端，這項工作包含尚未發佈至 BizTalk Server 的任何未完成的要求。 回應訊息不會傳遞至接收配接器之後**Terminate**已呼叫。  
  
 對於傳送配接器而言，應該會以適當方式處理進行中的訊息。 這表示，已成功傳遞的任何訊息都應該從配接器的私用應用程式訊息佇列中刪除，以免將訊息傳送一次以上。  
  
 之後**Terminate**稱為 「 傳訊引擎不接受發佈新訊息，除了請求-回應組的回應訊息的要求。