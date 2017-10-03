---
title: "文件中的一般檔案解譯器管線元件的驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Validate Document Structure property
- FFDasm.ValidateDocumentStructure property
- Flat File Disassembler [pipeline component], validating documents
- pipeline components, Flat File Disassembler
ms.assetid: 8cd777e4-8aba-4c17-92e8-958e5dd57d09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 120d4664f922a653d0d532ca25213f3cb60a4e67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-validation-in-the-flat-file-disassembler-pipeline-component"></a>一般檔案解譯器管線元件中的文件驗證
依照預設，「一般檔案解譯器」元件不會驗證它所處理的文件。 不過，您可以將驗證設定**驗證文件結構**到元件上的屬性**True**，或藉由設定**FFDasm.ValidateDocumentStructure**訊息內容屬性來**True**。 當文件驗證設定為執行時，「一般檔案解譯器」會驗證文件結構以及標頭與結尾結構，以確定它們符合文件、標頭與結尾結構描述。  
  
 一般檔案解譯器 」 可以移除空白欄位，而且會記錄何時**suppress_empty_nodes ="True"**所指定**schemaInfo**一般檔案 XSD 結構描述中的註解。 如果您使用**schemaInfo**註釋，如此一來，一般檔案解譯器會移除空的欄位和記錄，無論是否為選擇性。 如果您使用 XML 驗證，這可能會造成驗證錯誤 (藉由設定一般檔案解譯器**驗證文件結構**屬性**True**或使用 XML 驗證器管線元件). 若發生驗證錯誤，將擱置訊息。 如需 suppress_empty_nodes 屬性的詳細資訊，請參閱[其他一般檔案屬性](../core/additional-flat-file-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
 [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)