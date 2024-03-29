---
title: 來自 SWIFT 的 FRR 接收位置的訊息 |Microsoft Docs
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
ms.assetid: d15989de-56f9-4d62-8394-f4fd6e971495
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc4666e90510e7076a3f901ce6fc95b07ef16c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002079"
---
# <a name="frr-receive-location-for-messages-from-swift"></a>來自 SWIFT 的 FRR 接收位置的訊息
若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收管線元件，以從 SAA 接收訊息，並準備處理[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 接收管線包含下列元件：  
  
- SWIFT 解譯器的解譯階段  
  
- SWIFT 的 FRR 解碼器管線元件中的解碼器階段  
  
- SWIFT 的 FRR CorrelationSet 解析管線元件中的合作對象解析 」 階段  
  
  當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收移動瀏覽/NAN、 SWIFT 的 FRR 解碼器讀取 MQ 意見反應內容屬性，以判斷回應是否移動瀏覽或 NAN。 它會設定傳輸中立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]取景位置調整或 nan false _FRRTransportLevelAck 布林值的值為 true。  
  
  SWIFT 的 FRR CorrelationSet 解析管線元件會覆寫回應訊息的 FRRCorrelationToken 屬性，而 FRR 協調流程，MQMD 中的值。CorrelId 屬性。