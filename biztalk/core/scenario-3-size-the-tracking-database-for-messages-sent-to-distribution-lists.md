---
title: 案例 3： 調整追蹤資料庫大小的訊息傳送至通訊群組清單的 Out |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: bc6e0da0-46d1-42d6-8ec9-29a28719fbb3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dca1722e24e0c76c85699ea00fcf6ffc120b2e14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271102"
---
# <a name="scenario-3-sizing-the-tracking-database--for-messages-sent-out-to-distribution-lists"></a>實例 3：為外送到通訊群組清單之訊息的追蹤資料庫設定大小
在下圖中，有一個透過協調流程繼續的訊息在協調流程中變更了，而且已透過通訊群組清單傳送到數個不同的傳送埠。  
  
 ![透過多個連接埠至協調流程訊息](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")  
  
 **透過協調流程，並且在送出至數個不同的連接埠的 BizTalk Server 訊息**  
  
 以下是與此實例相關的事實：  
  
-   訊息大小是 10 K。  
  
-   您未升級任何屬性。  
  
-   您一年內所接收的訊息數目為三百五十萬。  
  
-   開啟所有事件的追蹤。 在此實例中有 5 個事件：  
  
    -   收到訊息 M0  
  
    -   接收埠輸出訊息 M1  
  
    -   傳送埠輸出訊息 M3  
  
    -   傳送埠輸出訊息 M4  
  
    -   傳送埠輸出訊息 M5  
  
 將此資訊套用至方程式會產生下列結果：  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-a-single-promoted-property"></a>傳送至通訊群組清單的協調流程中具有單一升級屬性的訊息  
 在此範例中，將升級單一屬性，大約 10 個位元組的大小，就如先前的實例所執行。 方程式現在看起來像這樣：  
  
```  
[((5*150 bytes) + (10*230 bytes) + (1*5(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 260) * 3,500,000]/1024/1024 = 11048 MB ~ 10.79 GB per year  
```  
  
 若升級 20 個位元組大小的其他屬性，則方程式現在看起來像這樣：  
  
```  
[((5*150 bytes) + (10*230 bytes) + ((1*5(52 bytes + 10 bytes) + (1*5(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 670) * 3,500,000]/1024/1024 = 12417 MB ~ 12.13 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-message-body-tracking-activated"></a>傳送至通訊群組清單的協調流程中已啟動訊息內文追蹤的訊息  
 若您要啟動訊息追蹤，則此範例的方程式看起來如下：  
  
```  
[3,500,000 * 6 * 5KB]/1024 = 102539.06 MB ~ 100.14 GB per year  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)   
 [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)