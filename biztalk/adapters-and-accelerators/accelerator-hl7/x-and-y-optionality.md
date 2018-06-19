---
title: '&#39;X&#39;和&#39;Y&#39; Optionality |Microsoft 文件'
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
ms.openlocfilehash: 320e0188a0987601daf65c011cc24aabc49b14cb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22207214"
---
# <a name="39x39-and-39y39-optionality"></a>&#39;X&#39;和&#39;Y&#39;選用性
HL7 Access 資料庫中的 SegmentDataElements 資料表包含數個資料的項目 （欄位） 將設為**Req/Opt = X**，這表示 HL7 標準不將這個欄位關聯與此觸發程序事件，如中所示下表。  
  
|區段|版本|章節|資料項目|需要 /<br /><br /> 選擇性|報表|Number|HTML 標準|  
|-------------|-------------|-------------|---------------|-----------------------------|------------|------------|-------------------|  
|OBX|2.4|7.4.2.9|00577|X|Y|5|ch07.htm#Heading113|  
|OBX|2.4|7.4.2.8|00576|X||0|ch07.htm#Heading112|  
|OBX|2.4|7.4.2.6|00574|X||0|ch07.htm#Heading107|  
|OBX|2.4|7.4.2.17|00936|X|Y|0|ch07.htm#Heading121|  
  
 因為[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]不會指定觸發程序事件，您決定哪些必要/選用的規則，或應該是選用性。 根據本機站台的條件，您可能決定強制執行選用性的規則。 根據預設，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供 23 欄位列為"X"做為選擇性欄位。  
  
> [!NOTE]
>  值"Y"是在錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Access 資料庫。 [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] 假設所有的值**Y**和**空白**是選擇性的。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)