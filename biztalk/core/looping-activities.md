---
title: 迴圈活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], looping activities
- activities [BAM], orchestrations
- orchestrations, looping
- orchestrations, activities
ms.assetid: fb40fdd0-ac8f-486a-b3d0-9d2200a87cda
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cf2b768deca72b281bc189431b01f5e63a4887
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005065"
---
# <a name="looping-activities"></a>迴圈活動
迴圈活動是指，在協調流程中迴圈的動作。 您也許可以從協調流程內迴圈的動作擷取事件。 若要執行這項操作，請建立其他活動，並對應迴圈內所有的新活動里程碑和資料。 請務必這麼做，因為迴圈中的資料處理將會在每個排程執行發生一次以上。 下圖顯示此情況的範例。  
  
 ![](../core/media/handlingloops2.gif "handlingloops2")  
  
 如圖所示，如果您有 「 訂單處理迴圈中的多個明細項目使用，像是 「 哪個訂單有項目價格為 $100？ 」 是模稜兩可。 明確的問題如下：  
  
- 哪個訂單的明細項目價格為 $100?  
  
- 哪個訂單的總計/最小/最大項目價格為 $100?  
  
  建立明確的問題必須將明細項目與訂單當做兩回事來思考。 在追蹤設定檔編輯器中，根活動 (例如訂單) 會對應至迴圈外的所有動作。 子活動 (例如明細項目) 會對應至迴圈內的動作。  
  
  您需要使用內容項目當做根活動的 ActivityID。 讓這個內容項目可以用在迴圈內部的某些訊息中。 請將活動對應至子活動底下顯示的關係節點，並將該活動命名為根活動。  
  
## <a name="see-also"></a>另請參閱  
 [使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md)