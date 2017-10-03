---
title: "如何設定 XML 驗證器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Validator [pipeline component]
- send pipelines, validating
- pipeline components, XML Validator
- receive pipelines, validating
ms.assetid: 3b3becaf-703c-4399-a5ed-e7082e31e6e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 821ad6a1353c0aa29866fd36fe84a7ea6317690b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-xml-validator-pipeline-component"></a>如何設定 XML 驗證器管線元件
XML 驗證器管線元件可用於傳送或接收管線中的任何階段 (除了解譯或組合階段)。  
  
### <a name="to-configure-the-properties-for-the-xml-validator-pipeline-component"></a>設定 XML 驗證器管線元件的屬性  
  
1.  將 XML 驗證器管線元件拖曳至接收管線的驗證階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，進行下列設定。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**文件結構描述**|指示要套用到文件之結構描述的命名空間與類型名稱。 如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。 若未指定結構描述，則會使用訊息的目標命名空間和根項目名稱資訊，來進行執行階段結構描述探索。 **注意：**如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**屬性。 <br /><br /> 預設值：空集合|  
    |可復原交換處理|若為 "false" - 表示整個交換是將其視為一個單位加以驗證 (若任何包含的訊息失敗，就會擱置整個交換)。<br /><br /> 若為 "true" 時 - 表示交換中的訊息會由驗證器個別擷取，同時可能發生透過傳訊路徑或其他路徑的部分填入將會遭到擱置。<br /><br /> 如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 驗證器管線元件](../core/xml-validator-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)