---
title: 訊息驗證引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message validation engine
- errors, validating
- XML validation
- parsing validation
- BRE policies, validating
- errors, messages
- messages, errors
- validating, messages
- validating, BRE policies
- validating, XML
- messages, validating
- validating, errors
- validating, parsing
ms.assetid: 4ba0b75e-665b-4771-b04f-5bc3e90d83f0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbdcb375c04e4c9684b2a805c7a7a7315f46f83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209030"
---
# <a name="message-validation-engine"></a>訊息驗證引擎
所提供的最重要功能的其中一個[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是完整驗證 SWIFT 接收從後端系統的 SWIFT 網路，或從 SWIFT （交易夥伴所傳送） 的網路接收的訊息的能力。 驗證輸出 SWIFT 訊息保證的訊息符合 SWIFT 標準和 SWIFT 網路不會拒絕訊息。  
  
 驗證輸入 SWIFT 訊息可確保從其他金融機構接收的訊息會遵循特定協議 （商務規則） 特定的關聯性。 在這兩種情況下，有助於降低交易成本和總擁有成本 (TCO) 驗證，並且設陷錯誤，再認可訊息的能力。  
  
 下列清單說明組成 A4SWIFT 驗證引擎的四個部分：  
  
-   一般檔案剖析器所執行的結構化驗證  
  
-   XML 驗證讀取器所執行的資料驗證  
  
-   執行商務規則引擎 (BRE) 的 SWIFT 網路和使用方式規則驗證  
  
-   訊息標記與收集的 「 盡力 」 時發生錯誤  
  
## <a name="structural-validation-parsing"></a>（剖析） 的結構化驗證  
 A4SWIFT 剖析 SWIFT 標準根據每個 SWIFT 訊息類型所定義的 XSD 結構描述的 SWIFT 的一般檔案訊息。 將一般檔案剖析為 XML 可保證，一般檔案結構正確。 剖析時，也會產生更輕鬆地讀取、 操作或轉換成其他格式或訊息類型的 XML。 您也可以針對資料有效性的結構描述驗證 XML，並使用更複雜的評估商務規則引擎 (BRE)。  
  
 SWIFT 解譯器會叫用 BizTalk 一般檔案剖析器剖析 SWIFT 解譯器所叫用的 SWIFT 的一般檔案訊息。 SWIFT 的解譯器中的錯誤集合會記錄在剖析期間發生的任何錯誤的詳細資料，並一律會嘗試繼續剖析為了儘可能收集多結構的錯誤，在第一階段中的資料。 不過，大部分的剖析錯誤嚴重並停止在第一個錯誤的訊息處理。  
  
 如需結構化驗證的詳細資訊，請參閱[使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)。  
  
## <a name="data-validation-xml-validation"></a>資料驗證 （XML 驗證）  
 您可以定義符合定義 XSD 結構描述做為格式正確的 XML 傳遞結構化驗證的 SWIFT 訊息。 A4SWIFT 會在剖析階段期間產生的結構上有效的 SWIFT 訊息的 XML。 A4SWIFT 可以接著會驗證此 XML 資料的正確性，針對對應 XSD 結構描述中定義的條件約束。  
  
 這些條件約束包括資料輸入、 長度和標準 SWIFT 依據定義的值範圍。 SWIFT 解譯器會叫用驗證讀取器來執行資料驗證的 XML。  
  
 SWIFT 解譯器會記錄錯誤集合中的 XML 驗證期間發生的錯誤詳細資料，並繼續驗證要儘可能收集最多的 XML 驗證錯誤，在第一階段的剩餘資料。 （不同於剖析時，接續的 XML 驗證不會保證。）  
  
 如需詳細資料驗證的詳細資訊，請參閱[使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)。  
  
## <a name="swift-network-and-usage-rule-validation-bre-validation"></a>SWIFT 網路和使用方式規則驗證 （BRE 驗證）  
 A4SWIFT 驗證 XML 結構上有效的 SWIFT 訊息的商務層級，根據商務規則引擎 (BRE) 原則的正確性。 這些原則包括強制執行 SWIFT 網路和使用方式的規則和其他複雜的跨欄位規則，依據 SWIFT 的標準定義。 SWIFT 解譯器會叫用 BRE 執行商業層級驗證。  
  
 SWIFT 解譯器會記錄錯誤集合中的 BRE 驗證期間發生的錯誤詳細資料，並繼續驗證要儘可能收集最多的 BRE 驗證錯誤，在第一階段的剩餘資料。 （如同 XML 驗證，接續的 BRE 驗證保證。）  
  
 如需 SWIFT 網路和使用方式的規則驗證的詳細資訊，請參閱[使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)。  
  
## <a name="validation-failures-and-message-marking"></a>驗證失敗，訊息標記  
 A4SWIFT 收集驗證錯誤，以及透過訊息驗證的每個階段的詳細資料： 剖析結構化 XML 驗證，BRE 驗證。 A4SWIFT 收集來收集錯誤相關資訊訊息盡可能使用 「 盡力 」 啟發學習法這些錯誤。 這項功能可讓失敗的訊息，找出的所有錯誤，然後再回報一次，而不是需要的送出，多個反覆項目驗證、 失敗、 修正，再重新送出。  
  
 至少一個錯誤集合中的任何驗證階段期間發生的錯誤訊息會被視為無效，而且會失敗。 A4SWIFT 將這些訊息發佈到 MessageBox 資料庫，但它們就會標示，表示訊息已驗證失敗的升級屬性，報表的每個驗證階段的錯誤計數。  
  
 提升的屬性，除了 A4SWIFT 序列化成 XML 的錯誤集合，並將 「 錯誤 」 的一部分多部分訊息的集合附加。 最後的訊息包含失敗的訊息內文部分中和錯誤組件中的錯誤集合 XML 及增強 A4SWIFT 升級屬性，以指出失敗狀態。 SWIFT 解譯器會將此多部分訊息發佈到 MessageBox 資料庫。  
  
 BizTalk 傳送埠或協調流程可以擷取失敗的訊息從 MessageBox 資料庫訂閱特殊 A4SWIFT 升級屬性。 您可以將訂用帳戶來擷取特定的驗證階段的所有失敗的訊息或只使用特定數目的錯誤訊息。  
  
 擷取失敗的訊息之後，您可以將它傳送給報表的應用程式、 修復應用程式或處理序或失敗的儲存機制，或您可以將它捨棄。  
  
 這項功能訂閱失敗的訊息 （和區分其他部分類型的訂用帳戶中的失敗），搭配豐富資訊的錯誤集合附加至每個失敗的訊息的 XML 表單強大的架構來開發簡單的錯誤報告應用程式，例如提供訊息修復和新送出功能 A4SWIFT 安裝程式安裝。  
  
 如需驗證失敗並標示為訊息的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for SWIFT 的執行階段](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)