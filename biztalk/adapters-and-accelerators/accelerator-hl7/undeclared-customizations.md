---
title: 未宣告的自訂設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- undeclared customizations
- Z objects, undeclared customizations
- customizing, Z objects
- customizing, undeclared customizations
ms.assetid: f062dbb7-2c78-47ea-a927-99e1fba4854b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05a33abb76d49cfa5db640b1d15d9fde420f19c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974223"
---
# <a name="undeclared-customizations"></a>未宣告的自訂項目
您可以將資料加入一則訊息，而不需定義的格式或資料的本質。 您這麼做，使用未宣告的 Z 區段。 未宣告的 Z 區段都是未預期的執行個體訊息結尾處。 剖析器/XML 驗證器不會驗證該區段。 未定義任何結構描述。 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 視為二進位大型物件 (BLOB) 中的區段。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會透過未宣告的 Z 區段資料傳遞為三部分訊息的第三個部分。 三個部分是標頭、 內文和未宣告的 Z 區段，也稱為 Z 組件。 區段識別碼開頭為字母"Z"，比方說，「 ZPD"的自訂病患的人口統計資料的詳細資訊，識別 Z 組件。  
  
## <a name="see-also"></a>另請參閱  
 [宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)   
 [使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)