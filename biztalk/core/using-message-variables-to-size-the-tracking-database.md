---
title: "使用訊息變數調整追蹤資料庫的大小 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message variables [Tracking database], CMsgs
- message variables [Tracking database], Events
- message variables [Tracking database], Properties
- Tracking database, database size
- message variables [Tracking database], Nserv
- message variables [Tracking database], Msgs
- message variables [Tracking database], PropSize
- message variables [Tracking database]
- message variables [Tracking database], MsgSize
- message variables [Tracking database], MsgNum
- Tracking database, messages
ms.assetid: 2d31ae25-3d16-4002-b5a5-dca25e764ecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5418cdf79499302e6127db7fb66f108825a0d8c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-message-variables-to-size-the-tracking-database"></a>使用訊息變數調整追蹤資料庫的大小
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以使用一些變數來決定 BizTalk 追蹤 (BizTalkDTADb) 資料庫在經過一段指定時間後的大小。 這些變數是：  
  
-   使用的管線數目  
  
-   相關的協調流程數目  
  
-   產生的事件數目  
  
-   追蹤的訊息屬性數目  
  
-   建立的其他訊息數目  
  
-   在指定的一段時間中所接收訊息的預估數目  
  
 雖然您用來預估 BizTalk 追蹤資料庫大小的方程式很明確，不過您必須將它套用到每個使用 BizTalk Server 實作的內送和外寄訊息程序。 換句話說，您必須為每個不同的訊息實例套用此方程式，然後加總這些結果以取得最後預估的資料庫大小。 在此文件中，我們將研究兩個實例。 實例為：  
  
1.  接收訊息、轉換訊息，然後傳送結果訊息  
  
2.  接收訊息、執行使用訊息的商務程序，然後傳送結果訊息。  
  
 這兩個實例可能會出現在 BizTalk Server 安裝中，而且每個實例都會產生不同的追蹤資料量。 產生的 BizTalk Server 安裝總追蹤資料是所有實例的總和。  
  
 下列項目是用於方程式的部分變數：  
  
|變數|Description|  
|--------------|-----------------|  
|**Nserv**|服務的數目 (管線數目 + 協調流程數目)|  
|**事件**|產生的訊息事件數目|  
|**屬性**|追蹤的訊息屬性數目|  
|**PropSize**|升級屬性 (欄位) 的大小 (以位元組為單位)|  
|**CMsgs**|每個內送訊息建立的額外訊息數目|  
|**訊息的上限數**|在指定的一段時間中的預估內送訊息數目|  
|**MsgSize**|訊息大小|  
|**MsgNum**|每個內送訊息的已追蹤訊息數目|  
  
 方程式如下：  
  
```  
[((Nserv * 150 bytes) + (Events * 230 bytes) + (Properties * CMsgs*(52 bytes + PropSize))) * Msgs]/1024/1024 = Data size in MB  
```  
  
 此方程式僅計算訊息所產生的追蹤資料，不包括為「協調流程偵錯工具」所產生的追蹤資料。 您必須將此公式套用到每個訊息程序以預估 BizTalk 追蹤資料庫的大小。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)