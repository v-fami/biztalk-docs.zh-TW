---
title: HL7 2.X 解譯器中的結構描述判斷 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- header segments [2.X]
- 2.X messages, header segments
- messages, parsing messages
- MSH
- disassembler, parsing messages
- 2.X messages, MSH
ms.assetid: afd45c4c-2feb-44eb-b3bd-49fe114eb893
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6314f9651d09dbb041d2e8851565e904366c9efe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206086"
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a>HL7 2.X 解譯器中的結構描述判斷
HL7 2.X 訊息包含標頭區段 (MSH)，後面接著的主體區段的數目和選擇性的 Z 區段數目。 MSH 包含 21 的欄位。  
  
 當訊息抵達時，2.X 引擎會讀取標頭來判斷要用來剖析訊息內文結構描述。 就會發生以下一連串事件：  
  
1.  解譯器會讀取 MSH3 值 （來源合作對象） 可判斷下列的驗證選項：  
  
    1.  是否要為主體執行 XML 驗證  
  
    2.  是否要驗證自訂資料欄位在本文資料  
  
    3.  是否允許尾端分隔符號，在主體中  
  
    4.  內文結構描述的目標命名空間是什麼 (**Targetns-xdrt.xml**)  
  
2.  解譯器接著會讀取 MSH9 和 MSH12 判斷主體的根節點名稱。 此演算法如下所示：  
  
    ```  
    Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
    ```  
  
     [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 永遠可以在尾端加入訊息標頭中的分隔符號。 引擎會檢查每一行的第一次三個字元的區段識別項。 它會保存產生 XML 的內文結構描述定義的所有區段。 當它遇到未定義的區段時，它會將該區段為 Z 區段。 從該點上，所有未定義的區段會構成 Z 訊息的一部分。 下一步的 MSH 標記本訊息結尾。 對於批次的訊息下, 一步的 MSH 或 BTS （批次結尾區段已標記） 結束標記的訊息。 Z 區段只能包含結構描述中未宣告的區段。 就會發生宣告的區段的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)