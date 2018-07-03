---
title: 訊息至 SWIFT 的 FRR 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- send ports, FRR
ms.assetid: 905c69a3-dff3-4a60-803d-dd617ffb6896
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1732e5e41cd60f6c98f435197e2e9c6284e4dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991735"
---
# <a name="frr-send-port-for-messages-to-swift"></a>訊息至 SWIFT 的 FRR 傳送埠
若要啟用 FIN 回應對帳 (FRR)，您必須設定將 SAA 透過 BizTalk Adapter for MQSeries 訊息的 FRR 傳送埠。 此傳送連接埠路由訊息，以透過自訂的 FRR 傳送管線元件，您必須建立下列管線元件：  
  
- 中 「 組合 」 階段的 SWIFT 組合器  
  
- SWIFTAsmFrrMQSeriesHelper 管線元件中的編碼階段  
  
  SWIFTAsmFrrMQSeriesHelper 管線元件會將外寄訊息的 MQMD_MsgID 屬性設定為 FRRCorrelationToken 屬性的值。 它也會指派，並會在管線設計階段設定的值開頭為"MQ"的任何其他所需的內容屬性升級。 傳送管線包含針對 MQSeries 作為可設定的屬性定義每個屬性。 每個值預設為 「 使用 」。  
  
  傳送埠處理之訊息的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。 傳輸機制為 BizTalk Adapter for MQSeries。 如需詳細資訊的傳輸屬性 的分散大小，例如 MQSeries 文件。