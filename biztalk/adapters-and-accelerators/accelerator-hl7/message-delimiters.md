---
title: 訊息分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, events
- messages, XML messages
- events
- delimiters
- messages, delimiters
- flat files
- XML messages
- messages, flat files
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3339ded8edf46f7c5b96317cdf7a3ec822ec808b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001495"
---
# <a name="message-delimiters"></a>訊息分隔符號
HL7 標準所定義的訊息事件的形式如下：  
  
- **一般檔案**。 HL7 2.4 及更早版本的版本所定義的訊息事件的一般檔案形式。  
  
- **XML**。 HL7 版本 2.XML 和第 3 版所定義的訊息事件的 XML 檔案形式。  
  
  標準 HL7 未遵循位置的格式，因為它會使用分隔符號來定義區段、 欄位、 元件和子元件層級的一般檔案。 下表列出由 HL7 一般檔案的預設分隔符號。  
  
|分隔符號|ReplTest1|使用方式|  
|---------------|-----------|-----------|  
|區段結束字元|\<cr\>|歸位字元結束區段的記錄。 您無法變更此值。|  
|欄位分隔符號|&#124;|縱線字元分隔的區段中的兩個相鄰的資料欄位。 此字元，也會將每個區段的第一個資料欄位的區段識別碼。|  
|元件分隔符號|^|Hat 字元會分隔相鄰的元件的資料欄位允許的 HL7 標準位置。|  
|子元件分隔符號|&|連字號字元會分隔相鄰的子元件的資料欄位允許的 HL7 標準位置。 如果不有任何子元件，您就可以省略此字元。|  
|重複分隔符號|~|波狀符號字元分隔的欄位中的子元件或元件的多個項目允許 HL7 標準的位置。|  
|逸出字元|\|使用符合 ST、 TX 或 全文檢索資料類型的任何欄位或 ED 資料類型的資料 （第四個） 元件，您可以使用逸出字元。 如果沒有逸出字元存在訊息中，您可以省略此字元。 不過，您必須將它包含如果您使用訊息中的子元件。|  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)