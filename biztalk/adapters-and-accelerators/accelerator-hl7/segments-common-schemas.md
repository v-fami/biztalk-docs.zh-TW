---
title: "區段通用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, common schemas
- 2.X schemas, segments
- common schemas
ms.assetid: 6f66bce9-ead8-46c1-a66c-830750adc73b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff61c73b51eb08d1e6f845980686b49b3440d88c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="segments-common-schemas"></a>區段的一般結構描述
 **Segments_\<*版本*>.xsd * * 檔案包含 datatypes_\<*版本*>.xsd 和包含的所有定義HL7 版本相關的區段。 每個訊息結構描述會使用 segments_\<*版本*>.xsd。 HL7 訊息定義在每個子資料夾之下，而且包括 segments_\<*版本*>.xsd。 SegmentDataElements 和 DataElements 存取資料庫資料表產生 segments_\<*版本*>.xsd 檔案，其中包含所有資料類型的 Fields.xsd 結構描述檔的指標。 結構描述檔案名稱格式如下：  
  
```  
  
<xxx>_<nnn>_<vaa>_GLO_DEF.xsd  
```  
  
 其中*xxx*是訊息類型，  *nnn* 是觸發程序的事件， *vaa*是版本號碼，GLO 指出全球化，和 DEF 表示預設值。 結構描述檔案 *\<xxx >*_*\<nnn>*\_*\<vaa >* \_ *\<glo >*\_*\<def >*.xsdis 產生從 EventMessageTypeSegments 和 SegmentDataElements 存取資料庫資料表和包含的指標區段\_\<*版本*>.xsd 結構描述檔案。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [資料類型的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)