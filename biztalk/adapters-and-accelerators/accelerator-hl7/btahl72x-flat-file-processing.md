---
title: "BTAHL72X 一般檔案處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- 2.X messages, disassembler
- property promotion, MSH-header schemas
- disassembler, validating messages
- HL7, errors
- 2.X messages, validating headers
- acknowledgements, generating
- assembler, validating messages
- messages, multi-part messages
- property promotion, property schemas
- generating aknowledgements
- messages, 2.X messages
- schemas, MSH-header schemas
- 2.X messages, validating message bodies
- 2.X messages
- schemas, property schemas
- message modes, 2.X messages
- errors, HL7 error format
- flat files
- validating, messages
- schemas, property promotion
- headers, validating
- 2.X messages, message modes
- 2.X messages, header validation
- 2.X messages, parsing flat files
ms.assetid: c92e2f70-0bfa-4bc8-8044-4a6e62cabee3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15d21653b9f0d6109487677484506c7a5d6bcc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btahl72x-flat-file-processing"></a>BTAHL72X 一般檔案處理
中的下列元件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理序 HL7 2.X （HL7 編碼） 訊息：  
  
-   管線與核心程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineCommon.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineMessageCore.dll  
  
-   組合器和解譯器程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fAsm.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fDAsm.dll  
  
-   通知 (ACK) 的驗證程式庫用於雙向 MLLP 傳送配接器： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL7ACKHelper.dll  
  
## <a name="hl7-message-modes"></a>HL7 訊息模式  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.X 訊息支援下列的訊息模式：  
  
-   發行者訂閱 (pub sub) 模式  
  
     「 發行者 」 端廣播給合作對象的 「 訂閱者 」 為宣告式或未經同意的更新。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可提供彈性，此模式中，因為您可以在設計階段之後管理訂用帳戶和合作對象。  
  
-   要求-回應模式  
  
     來自特定實體的特定要求回應訊息中產生 interrogative 或查詢訊息交換。  
  
## <a name="flat-file-parsing"></a>一般檔案剖析  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析 HL7 2.X 多部分的訊息分成三個部分：  
  
-   標頭 MSH 組件  
  
-   內文部分  
  
-   Z 組件  
  
## <a name="hl7-header-validation"></a>HL7 標頭驗證  
 HL7 解譯器和組合器執行 2.X 訊息，以確認它可以處理訊息的標頭的結構與圖解驗證。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]基底上常見的標頭結構描述，MSH_25_GLO_DEF 的圖解驗證。  
  
 比方說，剖析器會判斷 MSH1 和 MSH2 欄位有正確的格式。 MSH1 必須只有一個字元。 MSH2 必須是兩個和第四個字元之間，且沒有字元會重複。  
  
## <a name="hl7-body-validation"></a>HL7 主體驗證  
 HL7 解譯器和組合器執行 2.X 訊息主體的基本結構驗證與圖解的驗證，如果您啟用它。  
  
 基本結構驗證的主體，其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]一律會執行，包括確認下列：  
  
-   區段中有三個字元  
  
-   區段分隔符號是\<CR > 或\<CR >\<LF > （選擇性的最後一個區段）  
  
-   欄位分隔符號是適當  
  
-   未宣告的 Z 區段中沒有宣告的區段 （具有已定義的三個字元區段標記）  
  
 更多的結構描述驗證的主體包含下列內容：  
  
-   欄位尾端分隔符號  
  
     標頭 MSH 區段和主體區段中  
  
-   Z 區段  
  
-   XSD 支援和自訂資料類型  
  
     支援的 XSD 和非 XSD 型別 （TS （時間戳記）、 DT （日期）、 TM （時間） 和 TN （電話號碼）  
  
-   列舉型別  
  
     識別碼 （HL7 定義的資料表） 和 IS （使用者定義資料表）  
  
-   選用性  
  
     必要和選擇性  
  
-   重複  
  
     區段和欄位  
  
-   逸出序列  
  
     字元編碼、 格式和字元集  
  
 您可以啟用或停用的所有訊息從接收或傳送至特定合作對象 （來源合作對象的解譯器，組合器的目的合作對象） 的圖解驗證。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]直接針對這項處理，由 MSH9.3 訊息結構標頭欄位、 MSH12 版本識別碼欄位 （2.3.1、 2.4，2.5），以及命名空間設定中使用 HL7 2.X 結構描述[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
## <a name="hl7-disassembler-processing"></a>HL7 解譯器處理  
 HL7 解譯器會將傳入 HL7 訊息剖析為 XML 區段進行處理。 因為它會剖析訊息，解譯器會執行下列工作：  
  
-   控制代碼逸出序列  
  
-   處理必要/選用的屬性的檢查  
  
-   控制代碼定義區段和未定義或非預期的 Z 區段 (如需 Z 區段的說明，請參閱[Z 物件的自訂訊息](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md))。  
  
-   會忽略未預期的執行個體結尾的區段 （這會成為未宣告的 Z 區段）  
  
## <a name="error-reporting"></a>錯誤報告  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]標準 HL7 錯誤格式，其中包括的區段、 時序、 欄位和錯誤的程式碼的大部分錯誤報告。 不過，錯誤狀況可能並非所有版本都有可用的比方說，如果有任何結構描述。 若要處理這種情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以報告的替代錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]錯誤格式。 在訊息中的錯誤區段包含兩個部分： HL7 錯誤，另一個替代方案的其中一個[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]錯誤。  
  
## <a name="ack-generation"></a>通知的產生  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]支援下列類型的通知 (Ack) 的 2.X 訊息。 HL7 錯誤類型和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可用 （替代） 的錯誤類型：  
  
-   對應原始訊息和通知  
  
-   HL7 原始 Ack  
  
-   HL7 增強 Ack  
  
     認可接受和應用程式接受  
  
-   靜態 proxy 通知  
  
     ACK 或 NAK  
  
## <a name="property-promotion"></a>升級屬性  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]支援升級下列 2.X 屬性：  
  
-   屬性結構描述  
  
-   MSH 標頭結構描述  
  
## <a name="in-this-section"></a>本節內容  
  
-   [HL7 2.X 解譯器中的結構描述判斷](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [HL7 2.X 組合器中的結構描述判斷](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)