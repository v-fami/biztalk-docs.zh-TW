---
title: "資料類型的通用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, data types
- 2.X schemas, common schemas
- common schemas
ms.assetid: 6fd30cd3-9c4f-4391-9c79-a4dff11f2a46
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19ff35b515e70c21e2349ae54847ba312d7ce0f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-types-common-schemas"></a>資料類型的通用結構描述
 **Datatypes_*\<版本 >*.xsd * * 結構描述檔案 (其中*\<版本 >*是 HL7 版本號碼) 包含的定義所有 HL7 基本和複合資料類型對應 HL7 版本。 Segments_*\<版本 >*.xsd 檔案會使用此檔案，以符合對應 HL7 版本。 DataStructures 存取資料庫資料表產生 DataTypes_*\<版本 >*.xsd 結構描述檔案。 下列範例是 HL7 基本資料類型的項目**ST**:  
  
```  
<xsd:simpleType name="ST">  
  <xsd:restriction base="xsd:string" />   
</xsd:simpleType>  
```  
  
 這個範例會定義**ST**為**字串**。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [區段的一般結構描述](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)   
 [資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)