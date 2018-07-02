---
title: 一般檔案解譯器管線元件中的字元編碼 |Microsoft Docs
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
ms.openlocfilehash: d2a7ef27ec23fb7470aff74df2915150f892e07a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988807"
---
# <a name="character-encoding-in-the-flat-file-disassembler-pipeline-component"></a>一般檔案解譯器管線元件中的字元編碼
一般檔案解譯器元件會使用下列演算法判斷處理內送訊息時要使用哪一種編碼：  
  
1. 若資料中有位元順序標記，則會依此標記判斷編碼資訊。 此編碼資訊不會保留反組譯工具 (也就是它不會儲存到**XMLNorm.SourceCharset**屬性)。  
  
2. 否則，如果**IBaseMessagePart.Charset**屬性設定時，會使用指定的編碼。  
  
3. 或者，若標頭或文件結構描述包含字碼頁資訊，則會使用它。  
  
4. 或者，使用 UTF-8 編碼。  
  
   上述情況 2、 3 和 4，解譯器會將編碼資訊儲存在訊息內容中**XMLNorm.SourceCharset**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
 [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)