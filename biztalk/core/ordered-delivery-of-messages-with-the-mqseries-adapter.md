---
title: 依序傳遞訊息與 MQSeries 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MQSeries adapters, ordered delivery
ms.assetid: 517ff2a4-7315-43b5-8d4b-7494adf141e4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8b602adf93152f6af1e5dbbc576180d570a4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264526"
---
# <a name="ordered-delivery-of-messages-with-the-mqseries-adapter"></a>使用 MQSeries 配接器依序傳遞訊息
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供**排序的傳遞**選項用於靜態傳送埠。 設定**排序的傳遞**至傳送埠上的選項**True**可確保 BizTalk Server 將訊息傳遞至傳送埠，它們會發佈到 BizTalk MessageBox 資料庫的順序相同。 若要提供端對端排序的傳遞，必須符合下列條件：  
  
-   必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。 例如，接收訊息時使用 MQSeries 接收配接器，接收位置應該設定的選項**含有停止的順序**或**含有擱置的順序**。  
  
-   您必須訂閱這些訊息的傳送埠**排序的傳遞**選項設定為**True**。  
  
-   如果應使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組，而**排序的傳遞**屬性協調流程的接收埠應該設定為**True**。  
  
## <a name="using-the-mqseries-adapter-for-ordered-delivery-of-messages"></a>使用 MQSeries 配接器依序傳遞訊息  
 MQSeries 接收配接器支援保留訊息提交到 BizTalk Server 時的順序。 端對端排序的傳遞訊息透過 BizTalk Server 接收訊息與 MQSeries 配接器，如果透過已設定的傳送埠來處理訊息時可達到**排序的傳遞**選項設定為**True**。  
  
## <a name="see-also"></a>另請參閱  
 [依序傳遞訊息](../core/ordered-delivery-of-messages.md)   
 [如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)