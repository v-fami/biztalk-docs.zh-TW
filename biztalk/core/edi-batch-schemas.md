---
title: "EDI 批次結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26da8036-8fe0-481e-b1e9-7f2e5b090768
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e159734c7d6028eb7f54354140c40757cb212b3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="edi-batch-schemas"></a>EDI 批次結構描述
BizTalk Server 處理保留的交換時，會使用結構描述至少三次：  
  
-   批次結構描述 (交換 XML 結構描述)，用來驗證保留的批次交換根節點 ( BaseArtifacts.dll 中部署的 X12_BatchSchema 或 Edifact_BatchSchema)  
  
-   信封服務結構描述，用來驗證交換、群組，以及交易集標頭和結尾 (BaseArtifacts.dll 中部署的 X12ServiceSchema 和 EdifactServiceSchema)。 如需詳細資訊，請參閱[EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。  
  
-   文件結構描述，用於批次交換中的每種文件類型 (部署在您的專案中)。 如需詳細資訊，請參閱[EDI 文件結構描述](../core/edi-document-schemas.md)。  
  
 批次結構描述是在執行階段用來驗證將保留的輸入和輸出批次交換。 批次結構描述也可在設計階段用來驗證和產生訊息執行個體。  
  
## <a name="batch-schemas-used-at-runtime"></a>執行階段使用的批次結構描述  
 批次結構描述的兩個標準版本存在： X12_BatchSchema.xsd for X12 編碼和 EDIFACT_BatchSchema.xsd 用於 EDIFACT 編碼。 這兩個結構描述是包含控制區段的範本， 並且擁有下列根名稱和命名空間：  
  
|結構描述|根節點|命名空間|  
|------------|---------------|---------------|  
|X12_BatchSchema|X12InterchangeXML|http://schemas.microsoft.com/Edi/X12_BatchSchema|  
|Edifact_BatchSchema|EdifactInterchangeXML|http://schemas.microsoft.com/Edi/Edifact|  
  
 接收管線所產生的 XML 執行個體上的文件類型會是常數 (\<編碼\>_BatchSchema.xml)，它會參考此標準結構描述。 您可以在協調流程的對應中使用此執行個體，不過必須先將文件類型和命名空間變更為對應至實際需要的結構描述，才能使用此執行個體。  
  
 您不需要在專案的設計階段指定批次結構描述，因為它會部署在 BaseArtifacts.dll 中。  
  
## <a name="batch-schemas-in-the-schema-store"></a>結構描述保存區中的批次結構描述  
 BizTalk Server 在執行階段用來處理保留批次的批次結構描述會部署至 BaseArtifacts.dll 組件中。 這些結構描述會自動供執行階段處理使用。 Edifact_BatchSchema 和 X12_BatchSchema 中還會提供在 BizTalk 結構描述保存區[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI。 這些結構描述只能在設計階段用來驗證或產生交換。 在執行階段，無論接收管線或傳送管線都不需要使用結構描述進行驗證。  
  
## <a name="see-also"></a>請參閱  
 [EDI 結構描述](../core/edi-schemas.md)   
 [處理內送批次](../core/processing-incoming-batches.md)