---
title: 具現化，並初始化傳送配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f10e6507-3351-4173-95f5-48546ca5f5c4
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ed590b73d31a03a4b3316a4d84edfc1e39eb0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257662"
---
# <a name="instantiating-and-initializing-a-send-adapter"></a>產生並初始化傳送配接器
根據預設，傳送配接器是在第一個訊息傳遞給它們時才會產生，這項程序稱為「延遲建立」。 預設的延遲建立方法有助於保存系統資源。 傳送配接器在建立之後，就會存入快取，並維持到 BizTalk Server 服務停止為止。  
  
 **InitTransmitterOnServiceStart**隸屬**功能**列舉型別指示傳訊引擎，在服務啟動時，而不是使用預設的延遲建立，建立傳送配接器如果這預期。  
  
 就訊息批次處理而言，傳送訊息的模型與接收訊息的不同。 在接收時，配接器是將內送訊息插入從傳訊引擎所取得的批次中。 在傳送時，傳訊引擎則是從配接器取得批次，並將要傳輸的訊息傳送到該配接器。 這兩種作業都使用傳輸 Proxy 來取得訊息批次物件。  
  
## <a name="how-a-send-adapter-is-initialized"></a>傳送配接器初始化的方式  
 若要啟用組態並與傳輸 Proxy 繫結，配接器必須實作下列的組態介面：  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
 下列步驟描述初始化傳送配接器所涉及的事件順序：  
  
1.  當傳訊引擎在初始化傳送配接器時，會先執行**QueryInterface**如**IPersistPropertyBag**，這是選擇性的介面。 如果配接器實作此介面，處理常式組態會傳遞給配接器在**負載**方法呼叫。 配接器會使用此資訊，確保其設定正確。  
  
2.  傳訊引擎會執行**QueryInterface**如**IBTTransportControl**，這是必要的介面。  
  
3.  引擎會呼叫**IBTTransportControl.Initialize**傳遞給配接器傳輸 proxy。  
  
4.  傳訊引擎會執行**QueryInterface**如**IBTTransmitter**。  
  
     如果傳訊引擎探索這個介面，配接器就會被視為非批次感知的傳輸器。  
  
     如果傳訊引擎不會探索這個介面，「 傳訊引擎會執行**QueryInterface**如**IBTBatchTransmitter**的探索代表配接器是批次感知傳輸器。  
  
     如果傳訊引擎未探索上述兩種介面，就會產生錯誤狀況，導致初始化失敗。 在未探索任何必要介面時，初始化會失敗。  
  
 下列圖表說明這個 API 呼叫序列；以藍色顯示的介面是由配接器實作。  
  
 ![](../core/media/transmit-adapter-init.gif "Transmit_adapter_init")  
  
 配接器只要一旦初始化和設定，就可以傳送訊息。  
  
 下圖顯示在初使化傳送配接器時所涉及的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter10.gif "ebiz_sdk_devadapter10")  
初始化傳送配接器的工作流程  
  
> [!NOTE]
>  介面卡不應該封鎖傳訊引擎中呼叫這類**IBTTransportControl.Initialize**和**IPersistPropertyBag.Load**。 在這些呼叫中執行過多的處理，可能會對服務啟動時間造成影響。