---
title: "FRR 接收訊息的位置從後端應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d50f83feceac0238742cd474f70ecc1449f906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a>FRR 接收訊息的位置從後端應用程式
若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收位置從後端應用程式接收訊息並路由傳送到 BizTalk MessageBox 取用 FRR 協調流程。 接收位置會透過使用下列管線元件，您必須建立自訂 FRR 接收管線的訊息路由傳送：  
  
-   「 解譯 」 階段中的 SWIFT 解譯器  
  
-   SWIFT FRR 解碼器管線元件中的解碼器階段  
  
-   SWIFT FRR CorrelationSet 解決器管線元件中的合作對象解析階段  
  
 接收埠處理的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。 傳輸機制為後端應用程式所規定的任何內容。  
  
 此接收埠會接收位置相同的自訂接收管線，可使用來自 SWIFT 的訊息。 不過，管線會執行不同的函式的兩個接收位置。 在接收位置從後端應用程式的訊息，SWIFT FRR CorrelationSet 解決器管線元件會初始化相互關聯 token。