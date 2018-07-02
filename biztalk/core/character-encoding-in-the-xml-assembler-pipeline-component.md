---
title: XML 組合器管線元件中的字元編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- XMLNorm.SourceCharset property
- pipeline components, XML Assembler
- XMLNorm.TargetCharset property
- Target Charset property
- XML Assembler [pipeline component], character encoding
ms.assetid: c031fbbf-f00f-41ba-8ac9-cec7d625cef6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5d06842eab0def7846ab31419ce2feb0aeb2cd1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000871"
---
# <a name="character-encoding-in-the-xml-assembler-pipeline-component"></a>XML 組合器管線元件中的字元編碼
XML 組合器管線元件可以根據使用者指定的字元編碼來產生訊息，下表顯示這兩種方式：  
  
|編碼層級|編碼方法|  
|--------------------|---------------------|  
|元件|設定**目標字元集**管線設計師 」 中的元件屬性。|  
|訊息|設定**XMLNorm.TargetCharset**訊息內容屬性。 **注意：** 的訊息內容屬性永遠會覆寫在管線設計師中設定任何內容屬性。|  
  
 XML 組合器會使用下列演算法來判斷輸出訊息的編碼：  
  
1. 如果**XMLNorm.TargetCharset**內容屬性設定，則會使用該值。  
  
2. 否則，如果**目標字元集**屬性會指定在管線設計師中，則會使用該值。  
  
3. 否則，如果**XMLNorm.SourceCharset**屬性已指定，則會使用該值。  
  
4. 若未指定上述屬性，則會使用 UTF-8 編碼。  
  
   XML 組合器會將 BizTalk 訊息物件中編碼資訊儲存`IBaseMessagePart.Charset`屬性。 當使用 Unicode 或 UTF-8 編碼時，XML 組合器永遠會將位元順序標記 (byte order mark, BOM) 新增到外寄訊息。  
  
   請注意，當使用的預設的 XML 傳送管線，其中包含 XML 組合器元件，產生的文件的編碼提交到伺服器，或它們可能已建立的文件使用 utf-8 編碼時，使用做為相同的字元集在伺服器和**XMLNorm.TargetCharset**未指定。  
  
## <a name="see-also"></a>另請參閱  
 [XML 組合器管線元件](../core/xml-assembler-pipeline-component.md)   
 [如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)