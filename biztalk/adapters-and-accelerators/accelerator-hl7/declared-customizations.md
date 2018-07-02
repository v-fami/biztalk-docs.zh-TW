---
title: 宣告自訂項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declared customizations
- Z objects, declared customizations
- customizing, Z objects
- customizing, declared customizations
ms.assetid: 484655e9-8bfa-4643-bbe6-4ef69cbd83ad
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 091612d1ad15f7ea841b5936beba1fcf7fc26ddf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988263"
---
# <a name="declared-customizations"></a>宣告的自訂項目
宣告的自訂設定，您可以修改或加入 HL7 訊息的彈性。 您甚至可以定義新類型的訊息。 您可以在下列任一方式來這麼做：  
  
- 變更訊息的定義，藉由定義新的訊息類型或觸發程序事件  
  
- 將新的區段新增至現有的訊息類型  
  
- 變更現有的訊息部分 （區段、 欄位、 元件或子元件） 的資料類型  
  
- 變更可能的值，您可以使用現有的訊息組件中  
  
  > [!NOTE]
  >  您可以變更用於宣告的 Z 物件或標準 HL7 結構描述中的物件的列舉值。 若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。  
  
  您可以修改或加入 HL7 訊息，藉由新增、 維護及建立自訂的物件，在目前定義的訊息類型的關聯。 HL7 標準呼叫這些自訂物件 「 Z 物件 」 以便區別 HL7 標準符合的現有物件。 您可以使用 BizTalk 編輯器來定義 Z 物件。 您也可以使用 BizTalk 編輯器來處理將更新傳播到 Z 物件在所有觸發程序事件的功能和包含它的抽象訊息。 如需建立 Z 物件的詳細資訊，請參閱 <<c0> [ 使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)。  
  
  您可以使用 Z 物件提供給本機的定義，以您使用方式不 HL7 標準中所指定的區段。 您進行這些變更的結構描述，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝精靈安裝在您的電腦上。 您接著可以共用這些修改過的結構描述與其他[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝與您交換訊息。  
  
## <a name="types-of-z-objects"></a>Z 物件的類型  
 HL7 標準 (2.X) 目前支援下列形式進行自訂：  
  
-   **自訂觸發程序事件。** 如果您在本機區域和需要新的訊息結構，或想要支援不包含在標準的觸發程序事件，您可以建立新的觸發程序事件使用 Z 的前置詞，例如 Z05。 在此情況下，您必須建立新的本機訊息結構描述定義的抽象訊息和包含區段的模式。  
  
-   **自訂的使用者分佈。** 如果您是在本機的區域中，在內容中，已經支援的觸發程序事件，以及需要額外的資料，您可以建立新的區段，並包含需的資料區段中項目。 您必須指定使用現有的 HL7 資料型別區段中的項目。 您可以建立自訂的 Z 區段在 「 BizTalk 編輯器 」 中，結構描述中建立新的記錄。 如需詳細資訊，請參閱 <<c0> [ 建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)。 或者，您可以新增透過存取資料庫，然後再將該 Z 區段加入訊息結構的 Z 區段。 如需詳細資訊，請參閱 <<c0> [ 解決資料庫錯誤](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)。  
  
-   **自訂資料子型別。** HL7 提供一份支援的資料類型，例如，格式化文字時，掃描影像、 音訊資料。 不過，如果您想要定義其他資料類型，您可以執行前面加上"Z"搭配使用的助憶鍵，藉此建立 Z 資料輸入。  
  
    > [!NOTE]
    >  不允許的標準，以建立新的資料類型，或將項目新增至現有的區段範圍內。 仍少就是它允許接受目前未使用的項目，並重新定義它以符合某些其他用途。 相反地，支援舊版介面的組織可能需要配合這種做法。  
  
-   **自訂的資料表。** 在訊息中的許多現有物件具有有限的特定值，列舉 HL7 通用結構描述所定義的資料表中所定義。 您可以修改這些列舉，可透過建立 Z 資料表的其他值。  
  
## <a name="see-also"></a>另請參閱  
 [未宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)   
 [使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)