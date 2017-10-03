---
title: "一般檔案組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component]
ms.assetid: 3c851771-55b2-4d21-9291-d707dd66837c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385b1f8ea6c2ce707069cde522ea2f6712290be7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-assembler-pipeline-component"></a>一般檔案組合器管線元件
一般檔案組合器將個別文件組合成一批檔案，並可以選擇是否在上面加入標頭或結尾 (或兩者)。 如需一般檔案的詳細資訊，請參閱[具有分隔記錄的一般檔案訊息](../core/flat-file-messages-with-delimited-records.md)。 另請參閱[具有位置記錄的一般檔案訊息](../core/flat-file-messages-with-positional-records.md)。  
  
 一般檔案組合器管線元件不會驗證內送的 XML 訊息。 若要確認 XML 驗證，請在傳送管線的預先組合階段中包含 XML 驗證器元件。  
  
 一般檔案組合器管線元件僅支援 Microsoft .NET Framework 所支援的轉換。 寫入自訂文字撰寫程式可以進行任何其他的轉換。  
  
 設定一般檔案組合器管線元件的相關資訊，請參閱[如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)。  
  
> [!NOTE]
>  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您無法將訊息組合到單一交換中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [一般檔案組合器管線元件中的字元編碼](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [一般檔案組合器管線元件中的文件結構強化](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [保留一般檔案組合器管線元件中的分隔符號](../core/retaining-delimiters-in-the-flat-file-assembler-pipeline-component.md)