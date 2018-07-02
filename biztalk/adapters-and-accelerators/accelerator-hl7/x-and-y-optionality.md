---
title: '&#39;X&#39;和&#39;Y&#39;選擇性 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, Y optionality
- segments, SegmentDataElements table
- SegmentDataElements table
- segments, X optionality
ms.assetid: 8a59b407-95a2-45ba-a8d6-db4154c91d7b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed5b87216bd2d8e127ff032e3773b3f740835c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981519"
---
# <a name="39x39-and-39y39-optionality"></a>&#39;X&#39;和&#39;Y&#39;選用性
HL7 Access 資料庫中的 SegmentDataElements 資料表包含數個資料的項目 （欄位） 已設為**Req/Opt = X**，這表示 HL7 標準不會將這個欄位關聯與此觸發程序事件，如中所示下表。  
  
|區段|版本|章節|資料項目|必要 /<br /><br /> 選擇性|報表|Number|HTML 標準|  
|-------------|-------------|-------------|---------------|-----------------------------|------------|------------|-------------------|  
|OBX|2.4|7.4.2.9|00577|X|Y|5|ch07.htm#Heading113|  
|OBX|2.4|7.4.2.8|00576|X||0|ch07.htm#Heading112|  
|OBX|2.4|7.4.2.6|00574|X||0|ch07.htm#Heading107|  
|OBX|2.4|7.4.2.17|00936|X|Y|0|ch07.htm#Heading121|  
  
 由於 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]不會指定觸發程序事件，您決定哪些必要/選用的規則，或應該是選用性。 根據本機站台的條件，您可能決定強制執行選擇性的規則。 根據預設，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供 23 欄位列為"X"做為選擇性欄位。  
  
> [!NOTE]
>  值"Y"是中的錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Access 資料庫。 [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] 假設所有的值**Y**並**空白**是選擇性的。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)