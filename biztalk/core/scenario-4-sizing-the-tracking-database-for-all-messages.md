---
title: 案例 4： 所有訊息調整追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: db1126c7-0b86-4635-bfdc-3b69a82cc64b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 327953843b2d9b70f500796f43302320924a330c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269838"
---
# <a name="scenario-4-sizing-the-tracking-database-for-all-messages"></a>實例 4：為所有訊息調整追蹤資料庫的大小
若您在 Microsoft® BizTalk Server® 2004 實作中共有三個訊息實例，您將需要將所有實例結果相加以決定 BizTalk 追蹤資料庫的大小。  
  
 在上方所示的範例中：  
  
|狀況|每年所需的空間，以 GB 為單位|  
|--------------|-------------------------------------|  
|範例訊息|4.78|  
|協調流程中的訊息|7.18|  
|協調流程中傳送至通訊群組清單的訊息|10.8|  
|**總計**|22.04|  
  
 此外，若我們為所有三個實例開啟訊息內文追蹤，將取得以下結果：  
  
|狀況|每年所需的空間，以 GB 為單位|  
|--------------|-------------------------------------|  
|範例訊息|50.1|  
|協調流程中的訊息|50.1|  
|協調流程中傳送至通訊群組清單的訊息|83.45|  
|**總計**|183.65|  
  
 BizTalk 追蹤資料庫總計每年將成長 205.69 GB。 此圖不包括任何偶發事件。 若您決定按照建議將 10% 的偶發事件加到此總計，則您應規劃 BizTalk 追蹤資料庫每年成長 227.94 GB。 在頂端，您應該考慮因 SQL 索引、 儲存體和其他內容的額外負荷。您應該盡可能執行中測試的測試案例後，根據相乘因素。  
  
## <a name="other-factors-affecting-biztalk-tracking-database-size"></a>其他影響 BizTalk 追蹤資料庫大小的因素  
 有一些其他項目 (例如協調流程中所使用的圖形) 也會影響 BizTalk 追蹤資料庫的大小。  
  
 若您已開啟協調流程偵錯工具選項 (預設為開啟)，協調流程中每個圖形的狀態會儲存到 BizTalk 追蹤資料庫。  
  
 決定追蹤圖形狀態所需大小的公式為：  
  
```  
[(# of object shapes ] * 76 bytes  
```  
  
 例如，在下圖中，您將使用下列公式來決定 BizTalk 追蹤資料庫的大小：  
  
```  
((4) * 76 bytes = 304 bytes  
```  
  
 ![協調流程範例](../core/media/sample-orchestration.gif "Sample_orchestration")  
  
 假設此協調流程處理了三百五十萬個訊息，則追蹤此協調流程所需的額外空間為：  
  
```  
304 bytes * 3,500,000/1024/1024 = 1015 MB ~ 0.99 GB.  
```  
  
 您需要將每個協調流程偵錯工具設為 [開啟] 的協調流程納入計算，才能決定 BizTalk 追蹤資料庫的大約大小。  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)   
 [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)