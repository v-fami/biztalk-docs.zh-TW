---
title: 建立動態訊息類型探索的自訂標頭結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, dynamic resolution
- schemas, message types
- schemas, custom headers
- header schemas
ms.assetid: 0c936c57-b533-47ca-9258-576b021fd016
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf73b5cf02d6fa25fdea1347e56573ff023d934a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009119"
---
# <a name="creating-custom-header-schemas-for-dynamic-message-type-discovery"></a>建立動態訊息類型探索的自訂標頭結構描述
在大部分情況下，您應該指定預設的 SWIFT 標頭結構描述 (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) SWIFT 解譯器的 SWIFT 標頭結構描述的組態屬性。 SWIFT 解譯器會使用預設的 SWIFT 標頭結構描述剖析訊息標頭符合 SWIFT 的標準規格，並具有所需之升級屬性，以便動態結構描述解析 （和 「 雙重類型 」 的子型別解析SWIFT 的訊息，例如 MT574_IRSLST 和 MT574_W8BENO）。 如需有關預設 SWIFT 標頭結構描述，以及了解 SWIFT 解譯器的結構描述解析的執行方式的詳細資訊，請參閱[動態訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。  
  
 其他案例中，其中的訊息包含非 SWIFT 標準標頭資料，您可以使用自訂標頭結構描述的標頭解析和動態訊息類型探索。 若要建立及使用動態結構描述解析的自訂標頭結構描述，執行下列作業：  
  
1. 建立自訂的結構描述的 SWIFT 解譯器可以使用結構剖析預期的標頭的資料格式。  
  
2. 識別結構描述中的哪些欄位將保留的值，指出訊息類型。  
  
3. A4SWIFT 屬性結構描述 (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) 加入屬性結構描述之 「 清單 」 的自訂標頭結構描述，並將適當的欄位，指出使用下列的訊息類型的升級[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]屬性：  
  
   -   **A4SWIFT_MessageType**  
  
   -   **A4SWIFT_MessageType2** (若**A4SWIFT_MessageTypes**用)  
  
   -   **A4SWIFT_SecondaryMessageType** （選擇性）  
  
4. 建置和部署自訂標頭結構描述。  
  
5. 設定 SWIFT 解譯器 （在接收管線專案） 的 SWIFT 標頭結構描述的組態屬性的自訂標頭結構描述。  
  
   如需有關這些和其他升級的屬性的詳細資訊，請參閱 < [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。 如需使用 BizTalk 編輯器來建立和編輯結構描述、 升級屬性使用屬性結構描述，以及建置和部署結構描述專案的詳細資訊，請參閱 BizTalk Server 說明。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)