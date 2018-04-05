---
title: 批次排程 索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.batchschedule
helpviewer_keywords:
- batching, scheduling
- Batch Schedule tab [Configuration Explorer]
- scheduling batching
ms.assetid: 3792388b-6af2-41c2-8f41-bdfda7e17b2b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d870abad399dcca76c32a3a8d0e8c6637fc93284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-schedule-tab"></a>批次排程 索引標籤
您使用**批次排程**索引標籤來啟動、 要求或終止輸出批次。 啟用輸出批次包含兩個步驟： 設定以時間為基礎或訊息計數準則，然後啟動輸出批次處理協調流程。  
  
 您可以設定[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]建立輸出批次使用以時間為基礎或訊息計數的篩選條件或兩者的組合。 設定批次啟動準則是選擇性的。 如果未指定，則您可以手動啟動批次。 如果您想要啟用使用以時間為基礎的批次，或訊息計數準則，您必須指定這些準則，然後再啟動批次。  
  
 在**BTAHL7 Configuration 總管**對話方塊**批次排程**索引標籤上，執行下列動作：  
  
|使用|動作|  
|--------------|----------------|  
|**第一次批次之前的小時**|輸入再開始第一個批次的時數。<br /><br /> 此選項無法使用。 當您選取做為批次控制的訊息計數|  
|**重複之後的批次**|選取下列其中一個選項：<br /><br /> -                   **小時**。 輸入重複執行的批次程序之前要等待時的數。<br /><br /> -                   **訊息**。 輸入您想要在啟動下一個批次之前處理的訊息數目。|  
|**批次控制項**|使用下列選項：<br /><br /> -                   **啟動排程**： 選取此選項以啟動批次排程。<br /><br /> -                   **立即傳送**： 選取此選項即可立即啟動批次程序。 這會覆寫**第一個批次之前的小時**和**重複批次之後**設定。<br /><br /> -                   **停止排程**： 選取此選項即可停止目前的批次排程。 這會完成目前的批次，然後停止 批次協調流程。|