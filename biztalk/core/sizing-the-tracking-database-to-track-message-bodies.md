---
title: "調整大小以追蹤訊息內文追蹤資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
- message variables [Tracking database], MsgNum
- HAT, ports
- Tracking database, messages
- tracking, orchestrations
- tracking, messages
- HAT, orchestrations
- tracking, ports
ms.assetid: ee75e530-f15d-4ceb-ba67-0b0b24d9df6b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b5abc3f2a48f2baea5d158e1a0268a7eede51c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sizing-the-tracking-database-to-track-message-bodies"></a>將追蹤資料庫的大小調整為追蹤訊息內文
若您計劃追蹤 BizTalk 追蹤資料庫中的訊息內文，也需要將這些內文的大小納入計算。 使用以下方程式：  
  
```  
[Msgs * MsgNum * (MsgSize)]/1024 = Data size in MB  
```  
  
 若與訊息大小比起來相差很多，請考慮將訊息內容的平均大小加到上述的 MsgSize。  
  
 MsgNum 變數取決於開啟連接埠層級或使用訊息事件和服務執行個體追蹤在 [群組中樞] 頁面中的協調流程層級的追蹤功能。 您也必須將此公式套用到每個訊息處理。  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)   
 [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)