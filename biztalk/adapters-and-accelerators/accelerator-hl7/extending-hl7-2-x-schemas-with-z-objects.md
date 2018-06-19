---
title: 擴充 HL7 2.X Z 物件結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.X schemas, Z objects
- Z objects, extending 2.X schemas
ms.assetid: 0980d919-eb81-4c65-b0f7-f17f7cfef6b3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27ef2bea3e13904f04449a5b77d05672c2b2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204654"
---
# <a name="extending-hl7-2x-schemas-with-z-objects"></a>擴充 HL7 2.X Z 物件結構描述
HL7 組織定義 HL7 2.X 結構描述，並預期所有寄件者和接收者辨識並使用這些結構描述，因為組織定義它們。 互通性可確保符合結構描述。 不過，HL7 標準可讓您自訂現有 HL7 2.X 特定的本機目的結構描述。 您也可以定義完全新的結構描述和物件。 您可以使用哪些 HL7 標準呼叫 Z 物件。  
  
 標準 HL7 並未定義 Z 物件的值。 已發行的 HL7 結構描述不包含它們。 在本機，定義它們，並與所有本機的合作對象的協議來使用它們。 HL7 組織會保留所有訊息類型、 觸發程序事件、 區段、 資料類型，以及這個在本機使用開頭為"Z"的資料表名稱。 前置詞，因為 HL7 標準呼叫這些站台定義物件 Z 物件。  
  
> [!NOTE]
>  當您將 Z 物件加入至現有的自訂 HL7 結構描述時，最後可能使用該結構描述的多個版本。 若要處理這些多個版本，最好是使用中的命名空間功能[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。 您可以在找到這項功能**驗證**索引標籤中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 （在合作對象層級）。 您也必須變更您部署該專案的結構描述中的命名空間屬性。  
  
 在建立或處理 Z 物件中，您應該遵循 HL7 組織已建立 Z 物件的規則...  
  
 當您將 Z 物件加入至現有的結構描述，或建立新的 Z 訊息結構描述，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會使用具有 Z 物件的結構描述來處理 HL7 編碼訊息。 這種類型的 Z 物件是宣告的 Z 物件。 您也可以使用整合引擎不會處理依據訊息結構描述宣告的 Z 區段。 如需這種類型的 Z 區段的詳細資訊，請參閱[處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)  
  
-   [在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)  
  
-   [在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)  
  
-   [擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)  
  
-   [自訂訊息透過 Z 物件](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)