---
title: 範例凍結計算 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4da41d0d-10ee-4f64-97d1-3cfa9da153f7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ff231b630a5848494c45cd8d4d05f89e764eb41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268878"
---
# <a name="sample-dehydration-calculation"></a>範例凍結計算
以下是範例計算的範例，使用私用位元組來決定 BizTalk 是否會凍結。 該範例使用預設的設定值，以及一些範例執行階段值。  
  
 假設凍結屬性具有下列的值：  
  
-   **TimeBlocked** = 60 （範例封鎖時間以秒為單位）  
  
-   **WaitingHistory** = 90 （以秒為單位範例等候記錄）  
  
-   **ActualPrivateBytes** = 250 （私用位元組的範例值）  
  
-   **OptimalUsage** = 50 （預設組態值）  
  
-   **MaximalUsage** = 350 （預設組態值）  
  
 因為**ActualPrivateBytes**之間**OptimalUsage**和**MaximalUsage**，計算 alpha:  
  
```  
alpha(private) = (350 – 250) / 350 – 50)  
alpha(private) = 100 / 300  
alpha(private) = 0.33  
```  
  
 然後您計算**TestThreshold** ，如下所示：  
  
```  
TestThreshold = 1 + (0.33 * (1800 – 1))  
TestThreshold = 1 + 599.66  
TestThreshold = 600.66  
```  
  
 最後，再決定是否要凍結：  
  
```  
Dehydrate = (90 == -1 OR 90 > 600 OR 60 > (2 * 600))  
Dehydrate = false  
```  
  
 使用這個範例，您可以決定此時將不會凍結協調流程。