---
title: "FRR 接收訊息的位置來自 SWIFT |Microsoft 文件"
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
ms.assetid: d15989de-56f9-4d62-8394-f4fd6e971495
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d609cfc8c5177581f32ee0957a6a7ae7c1fe9a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-swift"></a>FRR 來自 SWIFT 接收訊息的位置
若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收管線元件從 SAA 接收訊息，並準備處理[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 接收管線包含下列元件：  
  
-   「 解譯 」 階段中的 SWIFT 解譯器  
  
-   SWIFT FRR 解碼器管線元件中的解碼器階段  
  
-   SWIFT FRR CorrelationSet 解決器管線元件中的合作對象解析階段  
  
 當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收取景位置調整/NAN、 SWIFT FRR 解碼器讀取 MQ 意見反應內容屬性來判斷回應是 PAN 或 NAN。 它會設定傳輸無從驗證[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRTransportLevelAck 布林值的移動瀏覽或 false 的 NAN 值為 true。  
  
 SWIFT FRR CorrelationSet 解決器管線元件會覆寫回應訊息的 FRRCorrelationToken 屬性 FRR 協調流程使用，MQMD 中的值。CorrelId 屬性。