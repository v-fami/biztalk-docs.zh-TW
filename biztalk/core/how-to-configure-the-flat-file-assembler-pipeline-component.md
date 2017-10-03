---
title: "如何設定一般檔案組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component], configuring
- messages, flat files
ms.assetid: 5af61bba-4eb2-4bb9-a655-394a76d08d3b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fe9c7a0720db68d8e629410dd3f0a443a99d7a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-flat-file-assembler-pipeline-component"></a>如何設定一般檔案組合器管線元件
一般檔案組合器管線元件用以在 XML 文件從伺服器傳送出去前，先將 XML 文件序列化成分隔式或序數一般檔案格式。  
  
### <a name="to-configure-the-properties-for-the-flat-file-assembler-pipeline-component"></a>設定一般檔案組合器管線元件的屬性  
  
1.  將一般檔案組合器管線元件拖曳至傳送管線的組合階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**文件結構描述**|選取將訊息從 XML 格式序列化成一般檔案文件格式的一般檔案文件結構描述。 若未指定結構描述，則會使用執行階段結構描述探索。 在 BizTalk 編輯器中可以建立一般檔案文件結構描述。<br /><br /> 預設值：無|  
    |**標頭結構描述**|選取做為一般檔案訊息標頭部分的結構描述。 標頭結構描述也可以在名為訊息內容屬性中指定**HeaderSpecName** xmlnorm 命名空間之下。 在此狀況下，它將覆寫管線設計師中指定的標頭結構描述。<br /><br /> 使用 BizTalk 編輯器可以建立一般檔案訊息標頭部分的結構描述。<br /><br /> 預設值：無|  
    |**保留位元順序標記**|指定組合器元件所產生的文件是否要加上位元順序標記 (BOM)。<br /><br /> 預設值： **False**|  
    |**目標字元集**|指定將用來為外寄訊息編碼的目標字元集。<br /><br /> 預設值：無|  
    |**結尾結構描述**|選取作為一般檔案訊息結尾部分的結構描述。 使用 BizTalk 編輯器可以建立一般檔案訊息結尾部分的結構描述。<br /><br /> 預設值：無|  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)