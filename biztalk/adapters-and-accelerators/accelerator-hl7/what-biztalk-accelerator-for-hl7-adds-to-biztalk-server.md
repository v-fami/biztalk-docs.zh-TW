---
title: "BizTalk Accelerator for HL7 新增至 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, documents
- BTAHL7, batching
- messages, acknowledgements
- messages, auditing
- Configuration Explorer
- BTAHL7, message validation
- BTAHL7, Configuration Explorer
- messages, processing
- BTAHL7, BizTalk Server
- BTAHL7, message processing
- auditing, messages
- BTAHL7, auditing
- validating, messages
- acknowledgements, messages
- BTAHL7, logging
- BizTalk Server, BTAHL7
- messages, validating
- logging
- BTAHL7, acknowledgements
- errors, logging
ms.assetid: 862e9f26-588a-4e91-8ebc-f53aab6f46c2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9e9d1277c5d037a42fd85ca48ec13c8f1893a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-biztalk-accelerator-for-hl7-adds-to-biztalk-server"></a>BizTalk Accelerator for HL7 新增至 BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 建置[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]醫療保健整合系統的整合系統。 它會加入醫療保健組織需要的功能。  
  
 您安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]最上層的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將功能加入至核心[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]引擎。 它的新增功能、 工具和公用程式，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供。 它也會增加應用程式發展介面 (Api) 什麼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]SDK 提供。  
  
## <a name="btahl72x-message-processing"></a>BTAHL72X 訊息處理  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]加入功能與工具，讓系統將原生，而不需要自訂處理 HL7 訊息的數。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]包含所有文件規格、 應用程式，以及您需要開發和部署處理完整範圍的 HL7 特定交易的元件。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]支援[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2x 一般檔案結構描述。 下列[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件會執行[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2 X 訊息處理：  
  
-   HL7 解譯器和組合器，讓系統將剖析和原生序列化 HL7 訊息。 解譯器和組合器屬於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管線，其會執行一系列或處理步驟對於訊息，包括 XML 之間來回轉換解碼的編碼方式和訊息驗證。  
  
-   可以讓系統接收或傳送 HL7 訊息的最小的較低層通訊協定 (MLLP) 介面卡的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通常使用 MLLP 通訊協定來傳輸。 MLLP 配接器可確保[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 訊息應用程式與交互作用。  
  
-   可讓系統接收 HL7 編碼訊息 HL7 訊息結構描述。  
  
## <a name="btahl72xml-message-processing"></a>BTAHL72XML 訊息處理  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]新增許多功能和工具，可讓系統來處理 XML 訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]若要讓將 HL7 訊息轉換成 XML 格式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，其中 XML 會在內部使用，在訊息上執行作業。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]只會針對 HL7 V2 執行轉換成 XML。X 的訊息，因為它是以原生的一般檔案格式。 2.XML 訊息，也就是以 XML 格式不會執行這項轉換。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析，並驗證這些訊息不需要轉換。  
  
 支援的 XML 訊息結構描述是[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML HL7 v2 HL7 組織所產生的結構描述。XML 版本和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 V2 所使用的 2 X 結構描述。X 版本訊息 （以一般檔案格式）。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]包含文件規格、 應用程式和元件，您需要開發和部署處理的完整範圍[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML 交易。 下列[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件會執行[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML 訊息處理：  
  
-   XML 解譯器和組合器，讓系統將剖析和序列化 HL7 訊息對應的 XML 訊息。 XML 解譯器和組合器 」 包含的功能之外的增強功能[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]XML 解譯器和組合器，包括自動認可和訊息驗證。  
  
-   HL7 相容 XML 結構描述可讓系統接收 HL7 訊息 (這兩個 V2。X 和 V2。XML 訊息）。 系統會將轉換 V2。X 訊息為 XML 訊息 (V2。XML 訊息已在 XML 中），然後將它們傳送至 XML 功能的另一個系統。 同樣地，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以接收 XML 訊息，並將其轉換成 HL7 傳送。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]使用 XML 文件規格，以及 HL7 剖析器、 對應和其他來轉換 HL7 特有資料從或另一種格式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]呼叫結構描述和對應的工具。 例如，您可能會接收交換標準 HL7 V2.0 格式或 2.5 版格式，並將該資料轉換成可以使用現有的醫療應用程式的另一種格式。  
  
## <a name="validation"></a>驗證  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會執行 HL7 V2 驗證。X 訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]無法執行。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會自動執行的訊息標頭 HL7，語法與圖解驗證，並會自動執行某些結構驗證的 HL7 訊息的本文。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]如果您啟用該功能，對執行圖解驗證 HL7 訊息本文，(請參閱[驗證設定](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md))。  
  
 HL7 編碼訊息的本文的驗證，包括結構描述、 資料格式、 某些標頭和本文欄位，以及列舉值。 2.XML 訊息的驗證，包括其結構描述，這是標準的 XML 驗證的驗證。 如需詳細資訊，請參閱[BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)和[BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)。  
  
## <a name="auto-acknowledgment"></a>自動通知  
 若要確保傳訊系統的可靠性，您可能要要求 HL7 的通知 (ACK) 訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會根據組態設定自動產生。  
  
 原始模式認可確認的訊息標頭和主體的驗證。 增強的模式，在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生兩種類型的通知： 的接受通知，它會傳送驗證標頭，和應用程式在驗證完成訊息傳送的通知。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收來自訊息的特定業務應用程式，以產生延後的 ACK [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]有助於支援雙向訊息傳輸的通知處理。  
  
## <a name="batching"></a>批次處理  
 您可以處理文件在批次模式中，以節省處理負擔。 您也可以批次處理這些批次回應。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可讓 for HL7 批次處理的三種 2.X 訊息：  
  
-   輸入批次處理，系統會以批次，接收訊息並再它分割成個別的訊息。  
  
-   在批次/所在系統同時接收和傳送訊息以批次時，批次。  
  
-   建立批次，系統會傳送個別的訊息接收的訊息批次。  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未提供批次處理功能 v2。XML 訊息。  
  
## <a name="logging"></a>記錄  
 若要增強疑難排解，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]能夠報告的錯誤或警告信號系統元件。 您可以篩選這類事件、 將它們儲存在任何三個記錄檔存放區 ([!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件記錄檔、 WMI、 或[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]記錄存放區)，或使用來自訂[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]SDK。  
  
## <a name="configuration-explorer"></a>組態總管  
 您可以設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]合作對象、 批次、 通知和記錄檔儲存在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，加入至工具的系統管理工具，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供。 此工具也可讓您起始處理合作對象層級的批次。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] SDK 可讓您自訂這些設定以程式設計的方式。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)