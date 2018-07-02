---
title: 從後端應用程式的 FRR 接收位置的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9133a4499e655003ec2cc3d2e0d654e5a225f58b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981527"
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a>從後端應用程式的 FRR 接收位置的訊息
若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收位置，接收來自後端應用程式和路由傳送到 BizTalk MessageBox 取用 FRR 協調流程。 接收位置路由傳送訊息，以透過自訂的 FRR 接收管線，您必須建立下列管線元件：  
  
- SWIFT 解譯器的解譯階段  
  
- SWIFT 的 FRR 解碼器管線元件中的解碼器階段  
  
- SWIFT 的 FRR CorrelationSet 解析管線元件中的合作對象解析 」 階段  
  
  接收埠處理之訊息的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。 傳輸機制是後端應用程式所規定的任何內容。  
  
  此接收埠會使用相同的自訂接收管線會使用接收位置所來自 SWIFT 的訊息。 不過，管線會執行不同的函式的兩個接收位置。 在 接收位置從後端應用程式的訊息，SWIFT 的 FRR CorrelationSet 解析管線元件會初始化的相互關聯 token。