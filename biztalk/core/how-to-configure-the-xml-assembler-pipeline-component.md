---
title: 如何設定 XML 組合器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], configuring
- messages, XML documents
- messages, envelopes
- configuring, pipeline components
- pipeline components, XML Assembler
ms.assetid: 6d883819-a1d4-4ad0-b08f-fcd7583134d6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cf69d5bd982571aefcf794d6ad32b0e69499470
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248830"
---
# <a name="how-to-configure-the-xml-assembler-pipeline-component"></a>如何設定 XML 組合器管線元件
XML 組合器管線元件用以在從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送訊息之前，將 XML 文件包裝為 XML 封套。  
  
### <a name="to-configure-the-properties-for-the-xml-assembler-pipeline-component"></a>設定 XML 組合器管線元件的屬性  
  
1.  將 XML 組合器管線元件拖曳至傳送管線的組合階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**新增處理指示**|**附加**： 的值**新增處理指示文字**應該附加到已存在訊息中的處理指示。<br /><br /> **建立新物件：** 值**新增處理指示文字**輸入中的欄位應該覆寫或取代任何已存在訊息中的處理指示。<br /><br /> 如果**新建**選取時，**新增處理指示文字**必須包含有效的處理指示。<br /><br /> **忽略**： 如果存在處理指示文字訊息中，將其移除。<br /><br /> 預設值：**附加**|  
    |**新增處理指示文字**|指定要新增到目標 XML 文件開頭的 XML 處理指示。 **注意：** 處理指示文字應該符合 W3C XML 處理指示標準。 <br /><br /> 預設值：無|  
    |**新增 XML 宣告**|當**True**，將類似下列的 XML 宣告加入至外寄文件： `<?xml version='1.0' encoding='UTF-8'>`。 決定編碼後組編碼在執行階段的目標文件。<br /><br /> 預設值： **，則為 True**|  
    |**文件結構描述**|指示要套用到文件之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。 **注意：** 如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**屬性。 <br /><br /> 預設值：空集合|  
    |**信封結構描述**|指示要套用到信封之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。 **注意：** 如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**信封結構描述**屬性。 <br /><br /> 預設值：空集合|  
    |**保留位元順序標記**|指定組合器元件所產生的文件是否要加上位元順序標記 (BOM)。<br /><br /> 預設值： **，則為 True**|  
    |**處理指示範圍**|指定在最外層信封或文件層級上定義處理指示。<br /><br /> 預設值：**文件**|  
    |**目標字元集**|指定用以編碼外寄訊息的字元集。<br /><br /> 預設值：無|  
  
## <a name="see-also"></a>另請參閱  
 [XML 組合器管線元件](../core/xml-assembler-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)