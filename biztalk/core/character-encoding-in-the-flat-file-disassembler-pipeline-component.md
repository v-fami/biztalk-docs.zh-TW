---
title: 一般檔案解譯器管線元件中的字元編碼 |Microsoft 文件
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
- pipeline components, Flat File Disassembler
- Flat File Disassembler [pipeline component], character encoding
ms.assetid: 0dbe24fb-c431-4edf-8aa9-4c040d6a7b32
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 839a3377f27417757e394c946fe96acc83752355
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231638"
---
# <a name="character-encoding-in-the-flat-file-disassembler-pipeline-component"></a>一般檔案解譯器管線元件中的字元編碼
一般檔案解譯器元件會使用下列演算法判斷處理內送訊息時要使用哪一種編碼：  
  
1.  若資料中有位元順序標記，則會依此標記判斷編碼資訊。 此編碼資訊不會保留反組譯工具 (亦即，不會儲存至**XMLNorm.SourceCharset**屬性)。  
  
2.  否則，如果**IBaseMessagePart.Charset**屬性設定，會那里指定的編碼方式。  
  
3.  或者，若標頭或文件結構描述包含字碼頁資訊，則會使用它。  
  
4.  或者，使用 UTF-8 編碼。  
  
 上述情況 2、 3 和 4，解譯器會將編碼資訊儲存在訊息內容中**XMLNorm.SourceCharset**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
 [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)