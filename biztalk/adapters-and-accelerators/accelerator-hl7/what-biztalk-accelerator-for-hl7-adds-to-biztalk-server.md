---
title: BizTalk Accelerator for HL7 新增至 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ab7cd2d5abe126cc246be678c192c037ee48c90
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980055"
---
# <a name="what-biztalk-accelerator-for-hl7-adds-to-biztalk-server"></a>BizTalk Accelerator for HL7 新增至 BizTalk Server
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 建置[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]醫療保健整合系統的整合系統。 它會新增醫療保健組織所要求的功能。  
  
 在您安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]頂端的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將功能加入至核心[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]引擎。 它的新增功能、 工具和公用程式，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供。 它也會增加應用程式發展介面 (Api) 什麼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]SDK 提供。  
  
## <a name="btahl72x-message-processing"></a>BTAHL72X 訊息處理  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 加入功能和工具，可讓系統以原生，而不需要自訂處理 HL7 訊息的數。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 包含所有文件規格、 應用程式和元件，您需要開發及部署適用於處理完整範圍的 HL7 特定交易。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 支援[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2x 一般檔案結構描述。 下列[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件會執行[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2 X 訊息處理：  
  
- HL7 反組譯工具，可讓系統以剖析和序列化 HL7 訊息的原生組譯工具。 解譯器和組合器屬於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管線，它會執行一系列處理步驟對於訊息，包括 XML 轉換解碼或編碼，而訊息驗證。  
  
- 最小的較低層通訊協定 (MLLP) 配接器，可讓系統接收或傳送 HL7 訊息中，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通常會將使用 MLLP 通訊協定傳輸。 MLLP 配接器可確保[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 型傳訊應用程式互通。  
  
- HL7 訊息結構描述，讓系統接收 HL7 編碼的訊息。  
  
## <a name="btahl72xml-message-processing"></a>BTAHL72XML 訊息處理  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 新增許多功能和工具，可讓系統在處理 XML 訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將 HL7 訊息轉換成 XML 格式中，若要讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，它會使用 XML 就內部而言，在訊息上執行作業。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 只執行 HL7 V2 的轉換成 XML。X 的訊息，因為它們是以原生方式在一般檔案格式。 它不會執行 2.XML 訊息，以 XML 格式轉換。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 剖析，並驗證這些訊息，而無需轉換。  
  
 支援的 XML 訊息結構描述是[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML HL7 v2 HL7 組織所產生的結構描述。XML 版本、 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 V2 所使用的 2 X 結構描述。或更新版本的訊息 （以一般檔案格式）。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 包含文件規格、 應用程式，以及您需要開發及部署適用於處理的完整範圍的元件[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML 交易。 下列[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件會執行[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML 訊息處理：  
  
- XML 解譯器和組合器可讓系統以剖析和序列化 HL7 訊息相對應的 XML 訊息。 XML 解譯器和組合器包含的功能之外的增強功能[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]XML 解譯器和組合器，包括自動通知和訊息驗證。  
  
- HL7 相容 XML 結構描述，可讓系統接收 HL7 訊息 (這兩種 V2。X 和 V2。XML 訊息）。 系統會將轉換 V2。訊息為 XML 訊息 (V2。XML 訊息已在 XML 中），然後將它們傳送至 XML 功能的另一個系統。 同樣地，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以接收 XML 訊息，並將其轉換成 HL7 傳送。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 使用以 XML 為基礎的文件規格，以及 HL7 剖析器、 對應和其他轉換 HL7 特定資料或另一種格式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]呼叫結構描述和對應的工具。 比方說，您可能會收到的交換標準 HL7 V2.0 格式或 V2.5 格式，並將該資料轉換成可以使用現有的醫療應用程式的另一種格式。  
  
## <a name="validation"></a>驗證  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會執行驗證 HL7 V2。X 訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]無法執行。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會自動執行 HL7 訊息、 標頭的語法與圖解驗證，並會自動執行一些結構驗證的 HL7 訊息的本文。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 執行圖解 HL7 訊息本文，驗證，如果您啟用該功能 (請參閱[驗證設定](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md))。  
  
 驗證 HL7 編碼訊息的本文包含的結構描述、 資料格式，某些標頭和主體欄位，以及列舉值。 2.XML 訊息的驗證，包括其結構描述，也就是標準的 XML 驗證的驗證。 如需詳細資訊，請參閱 < [BTAHL72X 一般的檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)並[BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)。  
  
## <a name="auto-acknowledgment"></a>自動通知  
 若要確保傳訊系統的可靠性，建議您需要通知 (ACK) 到 HL7 訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生自動根據組態設定。  
  
 原始模式下認可確認的訊息標頭和主體的驗證。 增強的模式，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生兩種類型的通知： 的接受在驗證標頭，它會傳送的通知和應用程式在驗證完整的訊息傳送的通知。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 產生延遲的通知的特定業務應用程式所接收的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 幫助您支援雙向訊息傳輸的通知處理。  
  
## <a name="batching"></a>批次處理  
 您可以處理文件在批次模式中，進而省下的處理負擔。 您也可以批次處理這些批次回應。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 可讓三種類型的批次處理 HL7 2.X 訊息：  
  
- 輸入批次處理系統接收的訊息視為一個批次，並再將它片段成個別的訊息。  
  
- 在批次/所在系統同時接收和傳送訊息以批次，批次。  
  
- 建立批次，系統會傳送個別的訊息接收的訊息批次。  
  
  > [!NOTE]
  >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 不提供 V2 的批次處理功能。XML 訊息。  
  
## <a name="logging"></a>記錄  
 若要增強的疑難排解，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可報告的錯誤或系統元件收到的警告。 您可以篩選這類事件，將它們儲存在任何三個記錄檔存放區 ([!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件記錄檔，WMI，或有[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]記錄存放區)，或使用自訂它們[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]SDK。  
  
## <a name="configuration-explorer"></a>組態總管  
 您可以設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]合作對象、 批次、 通知和記錄檔儲存在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，加入至工具的系統管理工具，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供。 這項工具也可讓您起始在合作對象層級的批次處理。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] SDK 可讓您自訂這些設定以程式設計的方式。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)