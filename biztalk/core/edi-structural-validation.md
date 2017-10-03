---
title: "EDI 結構驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87086614-5616-441d-915c-2979c63c6e2f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505b9ac55eff0b6adb249d11788308f03902f1d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-structural-validation"></a>EDI 結構驗證
X12 和 EDIFACT 編碼的 EDI 規格都針對 EDI 交換的結構定義了具體的規則和慣例。 EDIReceivePipeline 中的 EDI 解譯器會驗證每一則接收訊息的信封是否符合這些結構規則。 EDISendPipeline 也會遵照這些規則來建置要傳送的每一則訊息，並在傳送之前驗證信封。  
  
 結構驗證可確保必要的標頭和結尾確實存在。 結構完整性的檢查包括區段與迴圈排序與計數的檢查。 這些檢查一定會執行，以確保文件能夠正確剖析或序列化。 這項驗證執行即使**EDI 類型驗證**及/或**擴充驗證**選項已停用。 通過基本結構驗證的交換將遭擱置，即使**EDI 類型驗證**及/或**擴充驗證**選項已停用。  
  
 標頭和結尾內資料元素的值，以及標頭/結尾與資料元素分隔的方式，都是由協議決定。 這些部分需透過結構描述驗證來進行驗證。  
  
 如需信封和內容標頭和結尾的每一組的詳細資訊，請參閱[EDI 訊息結構](../core/edi-message-structure.md)。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息驗證](../core/edi-message-validation.md)