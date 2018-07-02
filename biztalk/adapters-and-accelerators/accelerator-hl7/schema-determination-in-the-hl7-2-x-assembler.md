---
title: HL7 2.X 組譯工具中的結構描述判斷 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, assembler
- MSH5
- assembler, schemas
ms.assetid: 464c006e-4fae-4e2a-99ea-157301c0179e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 962f9576032ec8b42542111502c2b6d6698f98d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983647"
---
# <a name="schema-determination-in-the-hl7-2x-assembler"></a>HL7 2.X 組譯工具中的結構描述判斷
訊息的序列化程式的流程時，Microsoft BizTalk Accelerator for HL7 中的序列化程式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用 MSH5 （目的合作對象） 的訊息，以判斷要在訊息上執行的作業。 這類的作業包括：  
  
- 是否要執行 XML 驗證的主體區段  
  
- 是否要驗證的主體區段的自訂資料類型  
  
- 是否允許尾端分隔符號，在主體中  
  
- 序列化程式將使用哪一個結構描述目標命名空間  
  
- 序列化程式是否需要對應的標頭  
  
  若要判斷結構描述，序列化程式會執行下列作業：  
  
- 設定目標命名空間 (**Targetns-xdrt.xml**) 來設定目的合作對象的命名空間相同的值  
  
- 會擷取**Rootnode**從**BTS。MessageType**升級屬性  
  
  **Doctype**會變成**Targetns-xdrt.xml"#"+ Rootnode**。  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)