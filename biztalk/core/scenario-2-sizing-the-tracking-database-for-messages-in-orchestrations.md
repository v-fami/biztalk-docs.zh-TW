---
title: "案例 2： 在協調流程中的訊息調整追蹤資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: d1cfb8b9-d4e2-4069-8db3-18f72358652b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62ea6e463dfb3a44e2628f57b632634d7a9bd212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2-sizing-the-tracking-database--for-messages-in-orchestrations"></a>實例 2：為協調流程中的訊息調整追蹤資料庫的大小
讓我們看一個包括協調流程的範例。 下圖顯示整個商務程序。 在此實例中，一個訊息進入 BizTalk Server，透過協調流程傳送，在協調流程中變更，然後透過傳送埠傳送出去。  
  
 ![BizTalk Server 訊息程序](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")  
  
 **BizTalk Server 訊息程序**  
  
 以下是與此實例相關的事實：  
  
-   訊息大小為 5K。  
  
-   我們未升級任何屬性。  
  
-   我們一年內所接收的訊息數目為三百五十萬。  
  
-   開啟所有事件的追蹤。 在此實例中有 6 個事件：  
  
    -   收到訊息 M0  
  
    -   接收埠輸出訊息 M1  
  
    -   協調流程收到訊息 M1  
  
    -   協調流程輸出訊息 M2  
  
    -   傳送埠收到訊息 M2  
  
    -   傳送管線輸出訊息 M3  
  
-   在此實例中建立了三個額外的訊息。 訊息 M0 是內送訊息，因此並不是由 BizTalk Server 所建立。 訊息 M1 是來自接收埠的輸出訊息、M2 是來自協調流程的輸出訊息，而 M3 則是來自傳輸埠的輸出訊息。  
  
 將此資訊套用至公式會產生下列結果：  
  
```  
[(3*150 bytes) + (6*230 bytes) + (0*0(52 bytes + 0) * 3,500,000]/1024/1024  
[(450 + 1380 + 0) * 3,500,000]/1024/1024 = 6108 MB ~ 5.96 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-a-single-promoted-property"></a>協調流程中含有單一升級屬性的訊息  
 現在讓我們來升級此實例中的單一欄位，就如先前範例所執行。 升級的屬性約為 10 個位元組大小。 方程式現在看起來像這樣：  
  
```  
[((3*150 bytes) + (6*230 bytes) + (1*3*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 186) * 3,500,000]/1024/1024 = 6729 MB ~ 6.57 GB per year  
```  
  
 若您需要升級 20 個位元組大小的其他屬性，則公式現在看起來像這樣：  
  
```  
[(3*150 bytes) + (6*230 bytes) + ((1*3*(52 bytes + 10 bytes) + (1*3*(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 372) * 3,500,000]/1024/1024 = 7350 MB ~ 7.18 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-message-body-tracking-activated"></a>協調流程中已啟動訊息內文追蹤的訊息  
 若您要啟動訊息追蹤，則計算所需額外空間的結果會與先前實例的結果相同，或為每年 50.1 GB。  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)   
 [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)