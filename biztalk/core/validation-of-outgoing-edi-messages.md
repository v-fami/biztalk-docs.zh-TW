---
title: 驗證外寄 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 491303c0-b585-409e-a289-a2f6f9f82469
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 946e90eb58c9b81e0cd7fa9bf2c02cc49af021ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287990"
---
# <a name="validation-of-outgoing-edi-messages"></a>驗證外寄 EDI 訊息
EDI 傳送管線處理外寄訊息時，會對信封和訊息資料執行一系列驗證。 有些驗證處理是固定會執行的，而有些需經啟用才會執行。 這些驗證包括下列項目：  
  
-   對交易集資料元素和訊息結構描述執行的結構描述驗證。 此項目固定會執行。  
  
-   交易集資料項目的欄位交互驗證 (僅限 X12 編碼訊息)。 需在訊息結構描述中啟用才會執行。  
  
-   對交易集資料項目執行的 EDI 驗證。 需在協議屬性中啟用才會執行。  
  
-   對交易集資料元素執行的擴充驗證。 需在協議屬性中啟用才會執行。  
  
-   依據 X12 標準，驗證單一群組 (以交易集 – 群組對應為基礎) 中的交易集。 這執行時，才**輸入批次處理選項**屬性設定為**保留交換-發生錯誤時暫停交換**或**保留交換-暫止交易設定錯誤**。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 結構驗證](../core/edi-structural-validation.md)   
 [協議屬性驗證](../core/agreement-properties-validation.md)   
 [EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md)   
 [擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md)   
 [結構描述驗證](../core/schema-validation2.md)   
 [交叉驗證欄位區段](../core/cross-field-segment-validation.md)