---
title: "建立 PeopleSoft HTTP 主控件和連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP port
- HTTP host
ms.assetid: 3e1ce5fd-32ee-409f-b4c8-f2bc68470f17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673b2a2acdcd5248391f245ab990d424aefd298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-peoplesoft-http-host-and-port"></a>建立 PeopleSoft HTTP 主控件和連接埠
PeopleSoft 中的訊息發佈架構稱為 Integration Broker。 Integration Broker 的主要元件包括：  
  
-   閘道  
  
-   發佈節點  
  
-   訂閱者節點  
  
 這三種元件一起使用便可發佈訊息到 HTTP 接聽程式的 URL。 您必須設定發佈節點。 PeopleSoft 有預設發行節點，也稱為本機訊息節點。 您必須啟用節點，並為發佈節點啟用交易。 您必須將訂閱節點設定為外部節點類型，然後啟用節點與交易。 對於此節點，您也必須將類型設定為 HTTP，並設定連線資訊。  
  
 您可以使用 PeopleSoft Integration Broker 建立 PeopleSoft HTTP 主控件和連接埠，讓 PeopleSoft 傳送事件。 您確定訊息使用中的程序使用中和路由是[如何驗證訊息的活動狀態](../core/how-to-verify-activity-status-of-a-message.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何驗證訊息的活動狀態](../core/how-to-verify-activity-status-of-a-message.md)  
  
-   [如何設定整合閘道和 HTTP 輸出連接器](../core/how-to-configure-the-integration-gateway-and-http-output-connector.md)  
  
-   [如何建立新的 Gateway 節點](../core/how-to-create-a-new-gateway-node.md)  
  
-   [如何新增交易](../core/how-to-add-a-transaction.md)  
  
-   [如何測試 HTTP 節點](../core/how-to-test-the-http-node.md)