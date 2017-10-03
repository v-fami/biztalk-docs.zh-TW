---
title: "如何追蹤資訊記錄至檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, tracking
- DebugTrackingInterceptor
- Business Rules Framework, code samples
ms.assetid: c832b763-aa08-4a0e-9086-776dccb0a6ef
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cdaae8e727cedc784ecaade83178cf50f863f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-tracking-information-to-file"></a>如何將追蹤資訊記錄至檔案
當商務規則引擎在執行時，它會將執行追蹤資訊傳送到攔截器。 引擎會設定為使用 BizTalk 攔截器追蹤訊息事件和服務執行個體資料時使用。 當您呼叫 BizTalk 協調流程外部的引擎時，您可以在執行原則時傳送想使用的攔截器。 除了 BizTalk 攔截器，您也可以使用**DebugTrackingInterceptor**來追蹤資訊輸出到檔案。 下列程式碼範例示範如何使用**DebugTrackingInterceptor**。  
  
```  
DebugTrackingInterceptor tracker = new DebugTrackingInterceptor("TrackingOutput.txt");  
policy.Execute(shortTermFacts,tracker);  
```