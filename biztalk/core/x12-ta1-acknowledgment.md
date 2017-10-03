---
title: "X12 TA1 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68568a1a-3669-46f4-8edc-8d057b012544
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8547175461732e41248e1e94bf961f95e655890f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="x12-ta1-acknowledgment"></a>X12 TA1 通知
X12 TA1 技術通知會報告位址接收者對交換標頭和結尾的處理狀態。 包括 X12 編碼訊息的 ISA 和 IEA 何時有效，何時有傳出正的 TA1 ACK，以及任何的其他內容狀態。 若結果為否，就會傳送包含錯誤碼的 TA1 ACK。  
  
 X12 TA1 通知會與 x12_<\<版本號碼 > _TA1.xsd 結構描述。 此 TA1 ACK 會以 ISA/IEA 信封傳送。 其中的 ISA 和 IEA 與任何其他交換的 ISA 和 IEA 完全相同。  
  
 下表列出在 TA1 ACK 交換內的區段。  
  
|TA1 中的欄位|欄位的名稱|對應至內送交換|值|  
|------------------|-------------------|------------------------------------|-----------|  
|TA101|交換控制編號|ISA13 - 交換控制編號|-|  
|TA102|交換日期|ISA09 - 交換日期|-|  
|TA103|交換時間|ISA10 - 交換時間|-|  
|TA104|交換通知代碼*|不適用|引擎行為： A、 E 或 R<br /><br /> A = 接受<br /><br /> E = 交換已接受，發生錯誤<br /><br /> R = 交換已拒絕/已擱置|  
|TA105|交換說明碼|不適用|正在處理結果錯誤碼。 **注意：**中的，請參閱資料表[X12 TA1 通知錯誤碼](../core/x12-ta1-acknowledgment-error-codes.md)。|  
  
 \*引擎行為根據資料元素驗證;除了安全性和驗證資訊，會依據其組態資訊的字串比較。