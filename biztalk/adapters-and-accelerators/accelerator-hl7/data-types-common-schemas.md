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
ms.openlocfilehash: 0e7d693cdf70f7d29a79aa8999dde49f408b8815
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="data-types-common-schemas"></a><span data-ttu-id="bd015-102">資料類型的通用結構描述</span><span class="sxs-lookup"><span data-stu-id="bd015-102">Data Types Common Schemas</span></span>
<span data-ttu-id="bd015-103"> **Datatypes_*\<版本\>*.xsd * * 結構描述檔案 (其中*\<版本\>*是 HL7 版本號碼) 包含對應的 HL7 版本的所有 HL7 基本及複合資料類型的定義。</span><span class="sxs-lookup"><span data-stu-id="bd015-103">The **datatypes_*\<version\>*.xsd** schema file (where *\<version\>* is the HL7 version number) contains the definition of all the HL7 elementary and composite data types for the corresponding HL7 version.</span></span> <span data-ttu-id="bd015-104">Segments_*\<版本\>*.xsd 檔案會使用此檔案，以符合對應 HL7 版本。</span><span class="sxs-lookup"><span data-stu-id="bd015-104">The segments_*\<version\>*.xsd file uses this file to match the corresponding HL7 version.</span></span> <span data-ttu-id="bd015-105">DataStructures 存取資料庫資料表產生 DataTypes_*\<版本\>*.xsd 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="bd015-105">The DataStructures Access database table generates the DataTypes_*\<version\>*.xsd schema file.</span></span> <span data-ttu-id="bd015-106">下列範例是 HL7 基本資料類型的項目**ST**:</span><span class="sxs-lookup"><span data-stu-id="bd015-106">The following example is an entry for the HL7 elementary data type **ST**:</span></span>  
  
```  
<xsd:simpleType name="ST">  
  <xsd:restriction base="xsd:string" />   
</xsd:simpleType>  
```  
  
 <span data-ttu-id="bd015-107">這個範例會定義**ST**為**字串**。</span><span class="sxs-lookup"><span data-stu-id="bd015-107">This example defines **ST** as a **string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd015-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd015-108">See Also</span></span>  
 <span data-ttu-id="bd015-109">[HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="bd015-109">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="bd015-110">[區段的一般結構描述](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="bd015-110">[Segments Common Schemas](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md) </span></span>  
 [<span data-ttu-id="bd015-111">資料表值的通用結構描述</span><span class="sxs-lookup"><span data-stu-id="bd015-111">Table Values Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)