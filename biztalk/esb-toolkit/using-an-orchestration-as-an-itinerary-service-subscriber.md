---
title: 使用協調流程作為路線服務訂閱者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 278564f1-de9f-4fbf-8c7f-09b3e607c28b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd787ec23e09bc420939d33c25005dd611f5fd38
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009559"
---
# <a name="using-an-orchestration-as-an-itinerary-service-subscriber"></a>使用協調流程作為路線服務訂閱者
協調流程也可作為路線服務。 若要參與路線，您必須先設計將協調流程直接繫結;若要這樣做，請使用 類似於上一個主題中的傳送埠篩選訂用帳戶[使用傳送埠作為路線服務訂閱者](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)。 圖 1 顯示適當的協調流程挑選符合下列條件的任何訊息篩選條件運算式的範例：  

- **ServiceName = Microsoft.Practices.ESB.Services.Transform**  

- **ServiceState = 暫止**  

- **ServiceType = 協調流程**  

  ![協調流程](../esb-toolkit/media/ch4-orchestration.jpg "第 4 章第協調流程")  

  **圖 1**  

  **要參與路線身為訂閱者的協調流程的範例篩選條件運算式**  

  Microsoft BizTalk Server 中的訊息是透過 ESB 入口匝到達，ESB 管線中的驗證步驟會將篩選條件屬性的屬性值寫入至內送訊息的 BizTalk 內容屬性這會將它們升級至訊息內容。 路線服務永遠設定**ServiceName**目前作用中的服務，以處理接下來，並與服務的名稱屬性**ServiceState**屬性值為**暫止**。 訂用帳戶，您必須設定至少第三個下列屬性：  

- **ServiceName。** 這是服務的名稱，因為儲存在 ESB 路線，，而且可以是任何名稱。 路線會使用此名稱來識別要執行的服務。  

- **ServiceState。** 這是要執行目前的路線服務步驟的狀態。 目前的服務步驟 （適用於處理 下一步） 將一律具有值**暫止**、 由其中一個 ESB 路線的管線元件，ESB 路線選取器管線元件中，設定或程式碼呼叫**進階**路線 API 方法。  

- **ServiceType。** 這個屬性會定義服務，指出它是來自協調流程 」 或 「 biztalk 傳訊子系統的型別。  

- **IsRequestResponse。** 此選擇性屬性必須有相同的值**IsRequestResponse**服務的屬性。
