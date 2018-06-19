---
title: 定義即時彙總 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- real-time data, aggregating
- aggregations [BAM], real-time data
ms.assetid: cb3d7124-1663-4af2-9540-4171cc51568a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b2df32149f67a002a5a6281b6f1abd848523a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238678"
---
# <a name="defining-real-time-aggregations"></a>定義即時彙總
在某些情況下，多維度彙總的特定配量會講求時效而分秒必爭，以致您希望能即時取得該資訊。 例如，您的業務是銷售容易腐壞的產品，所以希望即時取得各個出貨階段的產品數量彙總。 同時，您也有其他想要看到的彙總，如典型客戶的年齡彙總，但是這只有在月底進行商業智慧分析時才需要。  
  
-   使用**樞紐分析表**工具列上，將選取的樞紐分析表標示為即時彙總 (RTA)，，如果適用的話。 樞紐分析表所含資料的類型應該可以用來判斷此資料是否需要即時檢視。 例如，每小時追蹤網頁訂單的報告可能就必須即時加以檢視，然而追蹤每日銷售總額的報告則無須即時檢視。  
  
     ![](../core/media/ebiz-sdk-sample-bam12.gif "ebiz_sdk_sample_bam12")  
RTA 按鈕  
  
> [!IMPORTANT]
>  請勿定義多個使用相同 BAM 活動的 RTA。 若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。  
  
 如需有關樞紐分析表的詳細資訊，請參閱 Excel 線上說明。 在建立樞紐分析表之後，您就可以檢視即時 BAM 資料。  
  
## <a name="see-also"></a>另請參閱  
 [檢視即時 BAM 資料](../core/viewing-live-bam-data.md)   
 [進度維度](../core/progress-dimension.md)   
 [資料維度](../core/data-dimension.md)   
 [時間維度](../core/time-dimension.md)   
 [數字範圍維度](../core/numeric-range-dimension.md)   
 [定義維度](../core/defining-dimensions.md)