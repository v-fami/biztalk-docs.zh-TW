---
title: XML 和一般檔案屬性結構描述和屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d917b82-62c6-489f-99a9-97e429b6f7c0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6de871dedff280604a48c7e2adcd47bb6bea5d41
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006143"
---
# <a name="xml-and-flat-file-property-schema-and-properties"></a>XML 和一般檔案屬性結構描述與屬性
**http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties** 命名空間包含可用來設定一般檔案組合器和一般檔案解譯器管線元件的屬性。 下表說明這些屬性。  

## <a name="properties-list"></a>屬性清單

|屬性|類型|描述|  
|--------------|----------|-----------------|  
|**FlatFileHeaderDocument**|xs:string|可利用此屬性儲存內送一般檔案文件的標頭。|  
|**AllowUnrecognizedMessage**|xs:Boolean|指定 XML 元件是否應處理無法辨識的訊息。|  
|**ProcessingInstruction**|xs:string|處理外寄文件的指示文字。|  
|**DocumentSpecName**|xs:string|用於剖析或序列化文件的 XML 元件之結構描述。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間 # 根目錄。 若任何結構描述擁有相同的命名空間 # 根目錄，則驗證文件執行個體可能無法如預期運作。 命名空間 # 根目錄必須為唯一的。  若結構描述必須擁有相同的命名空間 # 根目錄，則應該為每個結構描述建立不同的管線並為每個 XML 解譯器管線元件各指定一個結構描述，或者使用一個管線但不指定任何結構描述作為 XML 解譯器管線元件的參數。  若沒有目標命名空間，此方式也能運作。|  
|**EnvelopeSpecName**|xs:string|用於剖析或序列化文件的 XML 元件之信封規格。<br /><br /> 此屬性中指定的結構描述應該要有唯一的目標命名空間 # 根目錄。 若任何結構描述擁有相同的命名空間 # 根目錄，則驗證文件執行個體可能無法如預期運作。 命名空間 # 根目錄必須為唯一的。  若結構描述必須擁有相同的命名空間 # 根目錄，則應該為每個結構描述建立不同的管線並為每個 XML 解譯器管線元件各指定一個結構描述，或者使用一個管線但不指定任何結構描述作為 XML 解譯器管線元件的參數。  若沒有目標命名空間，此方式也能運作。|  
|**TargetCharset**|xs:string|用於編碼輸出訊息的 XML 元件之字元集。|  
|**SourceCharset**|xs:string|用以在 XML 解譯器處理文件之前編碼文件的字元集。|  
|**ProcessingInstructionOption**|xs:int|指定如何將處理指示新增至外寄文件。 如需 ProcessingInstructionOption 的詳細資訊，請參閱[XML 組合器管線元件中的處理指示](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)。|  
|**AddXMLDeclaration**|xs:boolean|指定是否應將 XML 宣告新增至外寄文件。|  
|**HeaderSpecName**|xs:string|指定一般檔案文件標頭。|  
|**TrailerSpecName**|xs:string|指定一般檔案文件結尾。|  
|**PromotePropertiesOnly**|xs:boolean|當設定為 **，則為 True**，XML 解譯器元件未移除訊息信封或加以解譯。 僅執行屬性升級。|  

## <a name="see-also"></a>另請參閱  
- [設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
- [設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
- [設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
- [設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
- [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
- **訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
