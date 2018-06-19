---
title: 宣告自訂 |Microsoft 文件
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
ms.openlocfilehash: 767fdd543b1cb5d87bf3ec1c1943ac81d91c6ea4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204782"
---
# <a name="declared-customizations"></a>宣告的自訂項目
宣告的自訂設定，您必須修改或加入 HL7 訊息的彈性。 您甚至可以定義新類型的訊息。 您可以下列方式：  
  
-   變更訊息的定義，藉由定義新的訊息類型或觸發程序事件  
  
-   將新的區段新增至現有的訊息類型  
  
-   變更 （區段、 欄位、 元件或子元件） 的現有訊息部分的資料類型  
  
-   您可以使用現有的訊息組件中的可能值的變更  
  
    > [!NOTE]
    >  您可以變更用於宣告的 Z 物件或標準 HL7 結構描述中的物件的列舉值。 若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。  
  
 您可以修改或加入 HL7 訊息由加入、 維護和關聯的目前定義的訊息類型的自訂物件。 HL7 標準呼叫這些自訂物件 「 Z 物件 」 以便區別 HL7 標準符合的現有物件。 您可以使用 BizTalk 編輯器來定義 Z 物件。 您也可以使用 BizTalk 編輯器 中使用 Z 物件的更新可直接傳播到所有的觸發程序事件的功能和包含它的抽象訊息。 如需建立 Z 物件的詳細資訊，請參閱[擴充 HL7 2.X 結構描述具有 Z 物件](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)。  
  
 您可以使用 Z 物件，讓您使用方式不 HL7 標準中所指定的區段的本機定義。 進行這些變更結構描述，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝精靈安裝在電腦上。 您接著可以共用這些修改過的結構描述與其他[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝與您交換訊息。  
  
## <a name="types-of-z-objects"></a>Z 物件類型  
 HL7 標準 (2.X) 目前支援下列形式的自訂：  
  
-   **自訂觸發程序事件。** 如果您在區域和需要新的訊息結構，或想要支援的觸發程序事件，就不會包含在標準中，您可以建立新的觸發程序事件使用 Z 的前置詞，例如 Z05。 在此情況下，您必須建立新的本機訊息結構描述，藉由定義抽象的訊息包含區段的模式。  
  
-   **自訂區段。** 如果您是在本機的區域中，在內容中，已經支援的觸發程序事件，並需要額外的資料，您可以建立新的區段，並包含區段內需要的資料元素。 您必須指定使用現有的 HL7 資料類型的區段內的項目。 您可以建立自訂 Z 區段中 [BizTalk 編輯器] 中，結構描述中建立新的記錄。 如需詳細資訊，請參閱[建立宣告 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)。 或者，您可以加入透過存取資料庫，然後再將該 Z 區段加入訊息結構的 Z 區段。 如需詳細資訊，請參閱[解決資料庫錯誤](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)。  
  
-   **自訂資料子型別。** HL7 提供一份支援的資料類型，例如，格式化的文字，掃描影像、 音訊資料。 不過，如果您想要定義其他資料類型，您可以執行前面加上"Z"搭配使用的助憶鍵，藉此建立 Z 資料輸入。  
  
    > [!NOTE]
    >  不允許標準，來建立新的資料類型，或將項目新增至現有區段的範圍內。 小於仍然是它允許來取得目前未使用的項目，並重新定義它以符合某些其他用途。 相反地，支援傳統介面的組織可能必須配合這種作法。  
  
-   **自訂資料表。** 在訊息中的許多現有物件具有有限的範圍內的特定值，HL7 常見的結構描述所定義的資料表中的列舉所定義。 您可以修改這些列舉型別來建立 Z 資料表，以啟用額外的值。  
  
## <a name="see-also"></a>另請參閱  
 [未宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)   
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)