---
title: "解決資料遺失的進行中協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, MessageBox database
- data recovery
- data loss, recovery
- data loss, orchestrations
- data recovery, MessageBox database
- data recovery, orchestrations
- data loss, data recovery
- orchestrations, data recovery
- orchestrations, data loss
ms.assetid: dc6f1fd2-1976-40f2-ab57-41c7db40705e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eca757b80e31ee5db829d2d2079bf657d01079b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-data-loss-of-in-progress-orchestrations"></a>解析進行中協調流程的資料遺失
MessageBox 資料庫包含目前進行中協調流程的狀態。 雖然沒有方法可以精確判斷 MessageBox 資料庫中遺失的資料為何，您還是可以採取一些步驟來收集遺失資料的相關資訊：  
  
-   判斷在目前協調流程中已傳送及接收的訊息為何，以及在復原點之後已使用的外部系統為何。 例如，如果您的系統會維護訊息及事件的外部記錄，您就可以檢查該記錄。 您可能也需要手動檢視外部系統來查看發生了哪些活動。  
  
-   判定資料遺失的原因之後，您就可以開始修正還原的系統，並決定哪些程序可以繼續、哪些程序必須終止和重新啟動 (方法為重新提交遺失的啟動訊息)，以及哪些程序已成功完成，可以被終止。 這個程序主要取決於系統的架構，必須視為系統修復計畫的一部分來加以考量。  
  
## <a name="see-also"></a>另請參閱  
 [解決資料遺失](../core/resolving-data-loss.md)