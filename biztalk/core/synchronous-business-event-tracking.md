---
title: 同步的商務事件追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 302c7918-bc62-46f1-a949-fbf94a7073e3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84223714e2e04cec6c079862693a09786cb19a7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277934"
---
# <a name="synchronous-business-event-tracking"></a>同步的商務事件追蹤
將事件資料傳送至 BAM 的最簡單方式是使用 DirectEventStream 類別的執行個體。 在目前應用程式交易環境 (如果有的話) 中，此類別會將事件資料直接儲存到「BAM 主要匯入資料庫」。  
  
 如果執行此作業期間發生任何錯誤，方法呼叫將在呼叫的應用程式中擲回例外狀況。 例如，如果 UpdateActivity 傳遞的項目名稱與 BAM 活動定義不符，或者您尚未部署 BAM 定義，就會發生這種情形。 這讓呼叫的應用程式可以在儲存 BAM 資料時攔截並復原任何錯誤，使稍後的管理簡單許多。  
  
 同步地儲存資料可能會影響效能，因為呼叫的應用程式必須等候 BAM 執行所有預存程序與觸發程序。  
  
## <a name="see-also"></a>另請參閱  
 [非同步的商務事件追蹤](../core/asynchronous-business-event-tracking.md)