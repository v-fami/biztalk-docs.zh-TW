---
title: 一般檔案組合器管線元件中的字元編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Flat File Assembler [pipeline component], character encoding
- IBaseMessagePart.Charset property
- pipeline components, Flat File Assembler
- Codepage property
- XMLNorm.SourceCharset property
- XMLNorm.TargetCharset property
- Target Charset property
ms.assetid: 0cf3c0fd-f036-4190-83ce-9064ef4e823c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47c1b85531a2efe13b91383a4bb5a8deb35b63e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986335"
---
# <a name="character-encoding-in-the-flat-file-assembler-pipeline-component"></a>一般檔案組合器管線元件中的字元編碼
一般檔案組合器可用使用者指定的字元編碼產生訊息。 您可以在數個層級中指定字元編碼：  
  
- **結構描述。** 設定**字碼頁**文件的一般檔案結構描述中的屬性。  
  
- **元件。** 設定**目標字元集**管線設計師 」 中的元件屬性。  
  
- **訊息。** 設定**XMLNorm.TargetCharset**訊息內容屬性。  
  
  在訊息內容中所設定的屬性值一律會覆寫在管線設計師中所設定的屬性值。 此外，一律在管線設計師中設定的值會覆寫值設為**字碼頁**一般檔案文件結構描述中的屬性。  
  
  一般檔案組合器使用以下演算法以判斷將哪一種編碼用於輸出訊息：  
  
- 如果**XMLNorm.TargetCharset**內容屬性設定，其值會用於編碼。  
  
- 否則，如果**目標字元集**管線設計師 」 中的屬性已指定，則會使用該值。  
  
- 否則，如果**字碼頁**一般檔案結構描述中的屬性已指定，則會使用該值。  
  
- 否則，如果**XMLNorm.SourceCharset**屬性已指定，則會使用該值。  
  
- 或者，使用 "UTF-8"。 請注意，使用 UTF-8 編碼時，一般檔案組合器管線元件不會在外寄訊息中加入位元順序標記。  
  
  一般檔案組合器會將儲存編碼 BizTalk 訊息物件中的內文部分的詳細資訊**IBaseMessagePart.Charset**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md)   
 [如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)