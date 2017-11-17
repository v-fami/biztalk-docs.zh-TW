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
# <a name="segments-common-schemas"></a><span data-ttu-id="e0ae2-102">區段的一般結構描述</span><span class="sxs-lookup"><span data-stu-id="e0ae2-102">Segments Common Schemas</span></span>
<span data-ttu-id="e0ae2-103"> **Segments_\<*版本*>.xsd * * 檔案包含 datatypes_\<*版本*>.xsd 和包含的所有定義HL7 版本相關的區段。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-103">The **segments_\<*version*>.xsd** file includes datatypes_\<*version*>.xsd and contains the definition of all the segments related to the HL7 version.</span></span> <span data-ttu-id="e0ae2-104">每個訊息結構描述會使用 segments_\<*版本*>.xsd。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-104">Each message schema uses segments_\<*version*>.xsd.</span></span> <span data-ttu-id="e0ae2-105">HL7 訊息定義在每個子資料夾之下，而且包括 segments_\<*版本*>.xsd。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-105">HL7 message definitions are under each subfolder and include segments_\<*version*>.xsd.</span></span> <span data-ttu-id="e0ae2-106">SegmentDataElements 和 DataElements 存取資料庫資料表產生 segments_\<*版本*>.xsd 檔案，其中包含所有資料類型的 Fields.xsd 結構描述檔的指標。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-106">The SegmentDataElements and DataElements Access database tables generate the segments_\<*version*>.xsd file, which includes a pointer to the Fields.xsd schema file for all data types.</span></span> <span data-ttu-id="e0ae2-107">結構描述檔案名稱格式如下：</span><span class="sxs-lookup"><span data-stu-id="e0ae2-107">The schema file name format is:</span></span>  
  
```  
  
<xxx>_<nnn>_<vaa>_GLO_DEF.xsd  
```  
  
 <span data-ttu-id="e0ae2-108">其中*xxx*是訊息類型，  *nnn* 是觸發程序的事件， *vaa*是版本號碼，GLO 指出全球化，和 DEF 表示預設值。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-108">Where *xxx* is the message type, *nnn* is the trigger event, *vaa* is the version number, GLO indicates globalize, and DEF indicates default.</span></span> <span data-ttu-id="e0ae2-109">結構描述檔案 *\<xxx >*_*\<nnn>*\_*\<vaa >* \_ *\<glo >*\_*\<def >*.xsdis 產生從 EventMessageTypeSegments 和 SegmentDataElements 存取資料庫資料表和包含的指標區段\_\<*版本*>.xsd 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="e0ae2-109">The schema file *\<xxx>*_*\<nnn>*\_*\<vaa>*\_*\<glo>*\_*\<def>*.xsdis generated from the EventMessageTypeSegments and SegmentDataElements Access database tables and includes a pointer to the Segments\_\<*version*>.xsd schema file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ae2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ae2-110">See Also</span></span>  
 <span data-ttu-id="e0ae2-111">[HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="e0ae2-111">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="e0ae2-112">[資料類型的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="e0ae2-112">[Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span></span>  
 [<span data-ttu-id="e0ae2-113">資料表值的通用結構描述</span><span class="sxs-lookup"><span data-stu-id="e0ae2-113">Table Values Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)