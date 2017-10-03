---
title: "定義彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], creating
- Excel add-in [BAM], creating aggregations
- aggregations [BAM], Excel add-in
- aggregations [BAM], about aggregations
ms.assetid: d5bf22d5-f491-4b08-a604-c7158e6e282f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3412615d03fc9a9776d86fddfb062ab343c5aaeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-aggregations"></a>定義彙總
Excel 則定義**彙總**答案準備在問題提出之前為預先計算的資料摘要，改善查詢回應時間。 例如，當資料倉儲事實資料表包含數以萬計的資料列時，如果要查詢兩個特定產品的出貨排程，其必須掃描事實資料表進行計算，這可能需要花很長時間才能得到結果。 但是，如果已經預先計算好要回應的摘要資料，就幾乎可以立即做出回應。  
  
 下圖是預先計算好彙總資料的範例。  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
預先計算的彙總資料  
  
 上圖摘要了在兩個月的期間出貨至特定地點之各項產品的數量。 Excel 通常會定義這項資料當做**量值**。 用於篩選和分類的資料，Excel 則定義為**維度**。  
  
> [!NOTE]
>  BAM 不支援 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services 的具名執行個體。  
  
 如需有關瀏覽多維度資料的使用者經驗，請參閱「Excel 說明」中的＜樞紐分析表＞主題。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何定義量值](../core/how-to-define-measures.md)  
  
-   [定義維度](../core/defining-dimensions.md)  
  
-   [如何使用樞紐分析表](../core/how-to-use-the-pivottable.md)  
  
-   [定義即時彙總](../core/defining-real-time-aggregations.md)  
  
## <a name="see-also"></a>另請參閱  
 [定義 BAM 檢視](../core/defining-a-bam-view.md)