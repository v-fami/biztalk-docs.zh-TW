---
title: 如何設定 BizTalk Framework 解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- disassembly stage, pipelines
- receive pipelines, disassembly stage
- BizTalk Framework Disassembler [pipeline component], configuring
ms.assetid: a5599bcb-dbee-46a5-a91d-3c54f901cd30
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07fefb577e5322fa303a1a1476a976b453adb083
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249190"
---
# <a name="how-to-configure-the-biztalk-framework-disassembler-pipeline-component"></a>如何設定 BizTalk Framework 解譯器管線元件
BizTalk Framework 解譯器管線元件應該在接收管線的「解譯」階段中使用。  
  
### <a name="to-configure-the-properties-for-the-biztalk-framework-disassembler-pipeline-component"></a>設定 BizTalk Framework 解譯器管線元件的屬性  
  
1.  將 BizTalk Framework 解譯器管線元件拖曳至接收管線的「解譯」階段中。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**允許無法辨識的訊息**|指出是否允許沒有可辨識結構描述的訊息通過解譯器。<br /><br /> 預設值： **False**|  
    |**文件結構描述**|指示要套用到文件之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間。 若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。 若結構描述必須擁有相同的命名空間，則您應該為各結構描述個別建立管線，然後為每一個 BizTalk Framework 解譯器管線元件指定一個結構描述，或者您也可以使用一個管線，但不將任何結構描述指定為 BizTalk Framework 解譯器管線元件的參數。<br /><br /> 預設值：空集合|  
    |**信封結構描述**|指示要套用到信封之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間。 若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。 若結構描述必須擁有相同的命名空間，則您應該為各結構描述個別建立管線，然後為每一個 BizTalk Framework 解譯器管線元件指定一個結構描述，或者您也可以使用一個管線，但不將任何結構描述指定為 BizTalk Framework 解譯器管線元件的參數。<br /><br /> 預設值：空集合|  
    |**驗證文件結構**|當**True**，執行驗證的組譯工具，包括信封內送訊息。 **注意：** 時**True**，如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**或**信封結構描述**屬性。 <br /><br /> 預設值： **False**|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Framework 解譯器管線元件](../core/biztalk-framework-disassembler-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)