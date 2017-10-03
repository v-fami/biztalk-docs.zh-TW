---
title: "如何計算凍結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f2d09c-60db-4daf-b850-23f2c8915502
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a327695099ec575f2a13ccb75b4152e4a7de1af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-calculate-dehydration"></a>如何計算凍結
若要計算凍結，您可使用設定的屬性及某些執行階段的值。 下列範例會示範如何計算假設性的凍結案例。  
  
### <a name="to-calculate-dehydration"></a>計算凍結  
  
1.  讓 Alpha 代表 0 和 1 之間測量記憶體壓力的因數。  在實務中，Alpha 對於 3 個記憶體節流準則 (凍結屬性) 的每一個都有一個元件；在此範例中，我們用 alpha(virtual)、alpha(private) 和 alpha(physical) 來代表它們。 定義以下項目：  
  
    ```  
    IF ActualPrivateBytes < OptimalUsage  
       alpha(private) = 1  
    ELSE IF ActualPrivateBytes > MaximalUsage  
       alpha(private) = 0  
    ELSE  
       alpha(private) = (MaximalUsage - ActualPrivateBytes) / (MaximalUsage - OptimalUsage)  
    ```  
  
    > [!NOTE]
    >  OptimalUsage 和 MaximalUsage 針對每一個凍結屬性皆有預設值。 您可以在 BTSNTSvc.exe.config 檔案中變更這些值 。 如需詳細資訊，請參閱[凍結預設屬性](../core/dehydration-default-properties.md)。  
  
2.  以類似方式定義其他 Alpha 元件。 定義以下項目：  
  
    ```  
    alpha = Minimum { alpha(virtual), alpha(private), alpha(physical) }  
    where alpha(…) = 1 whenever IsActive=false for that given memory unit  
    ```  
  
3.  然後定義 TestThreshold (TestThreshold 、 MinThreshold 和 MaxThreshold 的定義單位為秒數)：  
  
    ```  
    TestThreshold = MinThreshold + (alpha * (MaxThreshold – MinThreshold))  
    ```  
  
    > [!NOTE]
    >  MinThreshold 預設值 = 1。 MaxThreshold 預設值 = 1800年。 您可以在 BTSNTSvc.exe.config 檔案中變更這些值 。 如需詳細資訊，請參閱[凍結預設屬性](../core/dehydration-default-properties.md)。  
  
4.  然後定義 TimeBlocked 和 EstimatedTime：  
  
    -   TimeBlocked = 我們實際等待此訂閱獲得滿足的時間  
  
    -   EstimatedTime = 預估此協調流程將維持閒置的時間 (例如：剩餘要接聽的逾時)  
  
 是否要凍結的決定是下列布林值條件的結果 (true = 凍結)：  
  
-   凍結 = (EstimatedTime > TestThreshold OR TimeBlocked > (2* TestThreshold))  
  
> [!NOTE]
>  預估時間就是在延遲結束前的剩餘時間 (如果延遲 5 分鐘並且已經過了 2 分鐘，則 TimeBlocked=120 秒、EstimatedTime=180 秒)。  
  
## <a name="see-also"></a>另請參閱  
 [凍結預設屬性](../core/dehydration-default-properties.md)   
 [BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)