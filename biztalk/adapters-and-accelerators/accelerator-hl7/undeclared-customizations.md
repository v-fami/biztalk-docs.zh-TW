---
title: "未宣告的自訂項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeclared customizations
- Z objects, undeclared customizations
- customizing, Z objects
- customizing, undeclared customizations
ms.assetid: f062dbb7-2c78-47ea-a927-99e1fba4854b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77f688e4cf6a4bbb55243d9f5f6f60e144bad862
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="undeclared-customizations"></a>未宣告的自訂項目
您可以新增至訊息的資料，但未定義的格式或資料的本質。 您使用未宣告的 Z 區段。 未宣告的 Z 區段是未預期的執行個體訊息結尾處。 XML 剖析器/驗證程式不會驗證區段。 未定義任何結構描述。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 視為二進位大型物件 (BLOB) 的區段。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將未宣告的 Z 區段資料，透過傳遞做為三部分訊息的第三個部分。 三個部分是標頭、 內文和未宣告的 Z 區段，也稱為 Z 組件。 區段識別碼開頭為字母"Z"，比方說，「 ZPD 「 自訂病患的人口統計資訊，識別 Z 組件。  
  
## <a name="see-also"></a>另請參閱  
 [宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)   
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)