---
title: "範例訊息簡報 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, SWIFT message block
- SWIFT messages, message block example
ms.assetid: 3136a7da-658d-4100-bbe5-2186ee8bafd1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8a3d03e35f6184e6aed6ba4af71e01a9b65e342
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sample-message-presentation"></a>範例訊息簡報
下表顯示的 SWIFT 訊息區塊配置的範例。  
  
|區塊|範例|  
|-----------|-------------|  
|**區塊 1**基本的標頭|{1:F01BCITITMMAXXX0012000123}|  
|**封鎖 2** (I) 應用程式標頭的輸入 （SWIFT)<br /><br /> 或<br /><br /> **封鎖 2** (O) 應用程式標頭輸出 （來自 SWIFT)|{2:I103VBOEATWWXXXXN}或者 {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3|  
|**區塊 3**使用者標頭|{3: {108:BCITITMMA950906}}|  
|**封鎖 4**文字|{4:\<CRLF\> : 20:1234567890\<CRLF\> : 23B:CRED\<CRLF\> : 32A:010605GBP45000，\<CRLF\> : 33B:GBP45000，\<CRLF\> : 50K:MASTERS 匯入\<CRLF\> RUE DES ARBRES 119\<CRLF\> CAMBRAI\<CRLF\> : 52A:BNPAFRPPCAM\<CRLF\> : 53A:POCIITMM680\<CRLF\> : 57A:BCITITMM680\<CRLF\> : 59: / P03452032022819 30\<CRLF\>總計匯入\<CRLF\> PESCARA\<CRLF\> : 70: RFB/INV 5591\<CRLF\> : 71A:SHA\<CRLF\> -}|  
|**封鎖 5**結尾|{5: {MAC: 12345678} {CHK:123456789ABC}}|  
  
## <a name="see-also"></a>請參閱  
 [SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/swift-schemas.md)