---
title: XML 解譯器管線元件中的字元編碼 |Microsoft 文件
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
ms.openlocfilehash: 2b0e307f2f608cde266e7a566fb3005bde048c31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231662"
---
# <a name="character-encoding-in-xml-disassembler-pipeline-component"></a>XML 解譯器管線元件中的字元編碼
XML 解譯器使用以下演算法以判斷使用哪種編碼處理內送訊息：  
  
1.  若資料中有位元順序標記，則會依此標記判斷編碼資訊。  
  
2.  否則，如果**IBaseMessagePart.Charset**屬性設定，會那里指定的編碼方式。  
  
3.  或者，若 XML 文件中具有 XML 宣告，且 XML 宣告為 ANSI，則會使用其中指定的編碼。  
  
4.  或者，使用 UTF-8 編碼。  
  
 上述情況 2、 3 和 4，XML 解譯器判定編碼之後，它將它儲存在訊息內容中**XMLNorm.SourceCharset**屬性。 XML 解譯器管線元件所產生的訊息永遠使用 UTF-8 編碼。 對於情況 1，依位元順序標記判斷的編碼不會保留。  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)