---
title: 如何設定一般檔案解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], configuring
- pipeline components, Flat File Disassembler
- messages, flat files
ms.assetid: c09996f6-6035-42a3-a75f-4def4ac39a95
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 403262bc18115923cdc5552a3b5e9e68d52f013e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249046"
---
# <a name="how-to-configure-the-flat-file-disassembler-pipeline-component"></a>如何設定一般檔案解譯器管線元件
一般檔案解譯器管線元件是用來解譯一般檔案格式的文件，並將這些文件轉換為 XML 格式。  
  
### <a name="to-configure-the-properties-for-the-flat-file-disassembler-pipeline-component"></a>設定一般檔案解譯器管線元件的屬性  
  
1.  將一般檔案解譯器管線元件拖曳至接收管線的解譯階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**文件結構描述**|選取將訊息從一般檔案剖析為 XML 格式的一般檔案文件結構描述。 一般檔案文件的剖析結構描述可以在 BizTalk 編輯器中建立。<br /><br /> 預設值： None**附註：** 您必須指定為此屬性，結構描述，或將會發生編譯時期錯誤。|  
    |**標頭結構描述**|選取做為一般檔案訊息標頭部分的結構描述。 一般檔案訊息標頭部分的結構描述可以在 BizTalk 編輯器中建立。<br /><br /> 預設值：無|  
    |**保留標頭**|將此屬性設定為**True**如果您需要儲存在訊息內容的一般檔案訊息標頭。 保留一般檔案訊息的標頭可以讓標題結構與內容和訊息一起透過 BizTalk Server 傳送。 在一般檔案組合器管線元件中將訊息序列化回一般檔案格式時，可以使用這個標頭。<br /><br /> 在一般檔案組合器序列化保留的標頭時，由於可在執行階段動態取得標頭結構描述名稱，因此標頭文件設計階段屬性可能會缺少該項資訊。 這可以使用保留標頭的訊息類型來完成。<br /><br /> 預設值： **False**|  
    |**結尾結構描述**|選取作為一般檔案訊息結尾部分的結構描述。 一般檔案訊息結尾部分的結構描述可以在 BizTalk 編輯器中建立。<br /><br /> 預設值：無|  
    |**可復原交換處理**|若為 "false" - 表示整個交換是解譯為一個單位 (若任何包含的訊息失敗，就會擱置整個交換)。<br /><br /> 若為 "true" 時 - 表示交換中的訊息會由解譯器個別擷取，同時可能發生透過傳訊路徑或其他路徑的部分填入將會遭到擱置。<br /><br /> 如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。|  
    |**驗證文件結構**|將此屬性設定為**True**如果您要驗證的一般檔案訊息 （標頭、 內文和結尾） 以確保它們符合其結構描述的所有部分。 此選項會降低效能的一般檔案解譯器中，所以它會設定**False**預設。<br /><br /> 預設值： **False**|  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)