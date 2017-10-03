---
title: "協調流程凍結效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ab92e0e-6a33-4aaa-ab14-0c82322b04d5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e81052f0061ff4ad802a084536c09d48cb6cb55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-dehydration-performance-counters"></a>協調流程凍結效能計數器
下表列出監視凍結行為專用之「協調流程引擎」效能計數器的名稱。 使用 [效能監視器] 即可在調整凍結參數時觀看這些計數器。  
  
|凍結效能計數器|說明|  
|-------------------------------------|-----------------|  
|可凍結的協調流程數|目前由主控件執行個體裝載，而可凍結的協調流程執行個體數。|  
|凍結中的協調流程數|目前正在凍結的協調流程數。|  
|進行中凍結循環|指示目前是否有凍結循環正在進行中。|  
|凍結循環數|完成的凍結循環數目。|  
|凍結閾值|以毫秒為單位的數字，用來判斷協調流程是否適度凍結。 如果協調流程引擎預測某執行個體可凍結的時間長短超出此閾值，就會凍結該執行個體。|  
|凍結的協調流程數|自從主控件執行個體啟動之後，已凍結的協調流程執行個體數。|  
|凍結的協調流程數/秒|平均每秒凍結的數目。|  
|解除凍結的協調流程數|自從主控件執行個體啟動之後，已解除凍結的協調流程執行個體數。|  
|解除凍結的協調流程數/秒|平均每秒解除凍結的數目|  
|排程等候凍結的協調流程數|具有擱置中凍結要求的可凍結協調流程數。|