---
title: XML 解譯器管線元件中的字元編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], character encoding
- XMLNorm.SourceCharset property
ms.assetid: 37962bdc-cbcb-4559-9ae8-6c4be49b4822
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fee26bdab8566010981e72585358b060009785f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977575"
---
# <a name="character-encoding-in-xml-disassembler-pipeline-component"></a>XML 解譯器管線元件中的字元編碼
XML 解譯器使用以下演算法以判斷使用哪種編碼處理內送訊息：  
  
1. 若資料中有位元順序標記，則會依此標記判斷編碼資訊。  
  
2. 否則，如果**IBaseMessagePart.Charset**屬性設定時，會使用指定的編碼。  
  
3. 或者，若 XML 文件中具有 XML 宣告，且 XML 宣告為 ANSI，則會使用其中指定的編碼。  
  
4. 或者，使用 UTF-8 編碼。  
  
   上述情況 2、 3 和 4，XML 解譯器判定編碼之後，它將它儲存在訊息內容中**XMLNorm.SourceCharset**屬性。 XML 解譯器管線元件所產生的訊息永遠使用 UTF-8 編碼。 對於情況 1，依位元順序標記判斷的編碼不會保留。  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)