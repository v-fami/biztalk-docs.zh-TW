---
title: 如何設定 XML 解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, pipeline components
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], configuring
- disassembly stage, pipelines
- receive pipelines, disassembly stage
ms.assetid: 93dd9148-4ae4-4868-b85d-66eada354f58
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 376daf04abb9bb555e9190fc819c3a3360cbe3cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249110"
---
# <a name="how-to-configure-the-xml-disassembler-pipeline-component"></a>如何設定 XML 解譯器管線元件
XML 解譯器管線元件應該用於接收管線的「解譯」階段。  
  
### <a name="to-configure-the-properties-for-the-xml-disassembler-pipeline-component"></a>設定 XML 解譯器管線元件的屬性  
  
1.  將 XML 解譯器管線元件拖曳至接收管線的解譯階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**允許無法辨識的訊息**|指示是否允許沒有可辨識訊息類型的訊息通過解譯器。<br /><br /> 預設值： **False**|  
    |**文件結構描述**|指示要套用到文件之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間。 若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。 若結構描述必須擁有相同的命名空間，則應該為每個結構描述建立不同的管線並為每個 XML 解譯器管線元件各指定一個結構描述，或者使用一個管線但不指定任何結構描述做為 XML 解譯器管線元件的參數。<br /><br /> 預設值：空集合|  
    |**信封結構描述**|指示要套用到信封之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間。 若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。 若結構描述必須擁有相同的命名空間，則應該為每個結構描述建立不同的管線並為每個 XML 解譯器管線元件各指定一個結構描述，或者使用一個管線但不指定任何結構描述做為 XML 解譯器管線元件的參數。<br /><br /> 預設值：空集合|  
    |**可復原交換處理**|若為 "false" - 表示整個交換是解譯為一個單位 (若任何包含的訊息失敗，就會擱置整個交換)。<br /><br /> 若為 "true" 時 - 表示交換中的訊息會由解譯器個別擷取，同時可能發生透過傳訊路徑或其他路徑的部分填入將會遭到擱置。<br /><br /> 如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。|  
    |**驗證文件結構**|當**True**，會執行驗證，以針對文件及選擇性的信封結構描述的內送訊息。<br /><br /> 如果升級的屬性沒有預設或固定的值，這個屬性設定為**False**，不會升級此屬性。<br /><br /> 預設值： **False** **附註：** 時**True**，如果您指定兩個或多個結構描述，您可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤如**文件結構描述**或**信封結構描述**屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)