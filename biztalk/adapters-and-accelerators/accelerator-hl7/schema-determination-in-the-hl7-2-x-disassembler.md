---
title: HL7 2.X 反組譯工具中的結構描述判斷 |Microsoft Docs
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
ms.openlocfilehash: 5fcdd3b0ba6565aff4d401c8e43ae2f86fc37384
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010255"
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a>HL7 2.X 反組譯工具中的結構描述判斷
HL7 2.X 訊息包含標頭區段 (MSH)，後面接著的主體區段的數目和選擇性的 Z 區段的數目。 MSH 包含 21 的欄位。  
  
 當訊息抵達時，2.X 引擎讀取來判斷要用來剖析訊息內文結構描述的標頭。 就會發生以下一連串事件：  
  
1. 解譯器會讀取 MSH3 的值 （來源合作對象） 可判斷下列的驗證選項：  
  
   1.  是否要執行 XML 驗證的主體  
  
   2.  是否要驗證自訂資料類型之主體資料的欄位  
  
   3.  是否允許尾端分隔符號，在主體中  
  
   4.  本文結構描述的目標命名空間的功能 (**Targetns-xdrt.xml**)  
  
2. 反組譯工具接著會讀取 MSH9 並 MSH12 判斷主體的根節點名稱。 此演算法如下所示：  
  
   ```  
   Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
   ```  
  
    Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 永遠可以在尾端加入訊息標頭中的分隔符號。 引擎會檢查每一行的第三個字元的區段識別碼。 它會保留產生 XML 內文結構描述所定義的所有區段。 發生未定義的區段，它會將該區段為 Z 區段。 從那時起，所有未定義的區段構成 Z 訊息的一部分。 下一步 的 MSH 標示此訊息的結束。 批次訊息的 BTS （批次結尾區段標記） 的下一步 的 MSH 結束標記訊息。 Z 區段只能包含結構描述中未宣告的區段。 就會遇到的宣告的區段中的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)