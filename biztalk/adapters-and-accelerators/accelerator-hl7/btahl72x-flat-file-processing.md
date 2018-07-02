---
title: BTAHL72X 一般檔案處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a0220d44386eed94efbddc1a5a22fe6704a7780
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975551"
---
# <a name="btahl72x-flat-file-processing"></a>BTAHL72X 一般檔案處理
在 Microsoft BizTalk Accelerator for HL7 的下列元件 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理 HL7 2.X （HL7 編碼） 訊息：  
  
- 管線和核心程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineCommon.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineMessageCore.dll  
  
- 組合器和解譯器程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fAsm.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fDAsm.dll  
  
- 通知 (ACK) 的驗證程式庫用於雙向 MLLP 傳送配接器： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL7ACKHelper.dll  
  
## <a name="hl7-message-modes"></a>HL7 訊息模式  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X 訊息支援下列的訊息模式：  
  
- 發行者-訂閱 (pub sub) 模式  
  
   發行者會廣播至合作對象的 「 訂閱者 」 為宣告式或來路不明的更新。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供彈性，此模式中，因為您可以在設計階段之後管理訂用帳戶和合作對象。  
  
- 要求-回應模式  
  
   來自特定實體的特定要求回應訊息中產生 interrogative 或查詢訊息交換。  
  
## <a name="flat-file-parsing"></a>一般檔案剖析  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 剖析 HL7 2.X 多部分的訊息分成三個部分：  
  
-   標頭 MSH 組件  
  
-   內文部分  
  
-   Z 組件  
  
## <a name="hl7-header-validation"></a>HL7 標頭驗證  
 HL7 反組譯工具和組譯工具執行 2.X 訊息，以確認它可以處理訊息的標頭的結構化與圖解驗證。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 基底上常見的標頭結構描述，MSH_25_GLO_DEF 圖解的驗證。  
  
 比方說，剖析器會判斷 MSH1 和 MSH2 欄位有正確的格式。 MSH1 必須只有一個字元。 MSH2 必須是介於兩個到四個字元，而且沒有字元可以重複。  
  
## <a name="hl7-body-validation"></a>HL7 主體驗證  
 HL7 反組譯工具和組譯工具執行的 2.X 訊息內文的基本結構驗證和圖解的驗證，如果您啟用它。  
  
 基本結構驗證的主體中，其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]一律會執行，包括確認下列：  
  
- 區段中有三個字元  
  
- 區段分隔符號是\<CR\>或是\<CR\>\<LF\> （選擇性的最後一個區段）  
  
- 欄位分隔符號是適當  
  
- 未宣告的 Z 區段中有任何宣告的區段 （具有已定義的三個字元區段標記）  
  
  更多的結構描述驗證的主體包含下列項目：  
  
- 尾端欄位分隔符號  
  
   在標頭 MSH 區段及本文區段  
  
- Z 區段  
  
- XSD 支援與自訂資料類型  
  
   支援的 XSD 和非 XSD 型別 （TS （時間戳記）、 DT （日期）、 TM （時間） 和 TN （電話號碼）  
  
- 列舉型別  
  
   識別碼 （HL7 定義的資料表） 和 IS （使用者定義的資料表）  
  
- 選用性  
  
   必要和選擇性  
  
- 重複  
  
   區段和欄位  
  
- 逸出序列  
  
   字元編碼、 格式和字元集  
  
  您可以啟用或停用圖解驗證接收自或傳送至特定合作對象 （來源合作對象的解譯器，組合器的目的合作對象） 的所有訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 使用 HL7 2.X 結構描述，針對這項處理，由 MSH9.3 訊息結構標頭欄位、 MSH12 版本識別碼欄位 （2.3.1、 2.4、 2.5） 和在中設定的命名空間的直接[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
## <a name="hl7-disassembler-processing"></a>HL7 反組譯工具處理  
 HL7 反組譯工具會將連入 HL7 訊息剖析為 XML 區段進行處理。 剖析訊息，解譯器會執行下列工作：  
  
-   控制代碼逸出序列  
  
-   處理必要/選用屬性的檢查  
  
-   控制代碼定義區段和未定義或非預期的 Z 區段 (如需 Z 區段的說明，請參閱 <<c0> [ 透過 Z 物件自訂的訊息](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md))。  
  
-   會忽略未預期的執行個體結尾的區段 （這會成為未宣告的 Z 區段）  
  
## <a name="error-reporting"></a>錯誤報告  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 報告的大部分錯誤標準 HL7 錯誤格式，其中包括的區段、 序列、 欄位和錯誤的程式碼。 不過，錯誤狀況可能是，並非所有版本都可用，比方說，若沒有結構描述，則。 若要處理這種情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以報告在替代錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]錯誤格式。 在訊息中的錯誤區段包含兩個部分： 一個用於 HL7 錯誤，一個針對替代[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]時發生錯誤。  
  
## <a name="ack-generation"></a>通知的產生  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X 訊息支援下列類型的通知 (Ack)。 HL7 錯誤類型和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]（替代） 的錯誤類型使用：  
  
-   對應原始訊息和通知  
  
-   HL7 原始通知  
  
-   HL7 增強 Ack  
  
     認可接受並接受應用程式  
  
-   靜態 proxy 通知  
  
     ACK 或 NAK  
  
## <a name="property-promotion"></a>升級屬性  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 支援升級下列 2.X 屬性：  
  
-   屬性結構描述  
  
-   MSH 標頭結構描述  
  
## <a name="in-this-section"></a>本節內容  
  
-   [HL7 2.X 反組譯工具中的結構描述判斷](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [HL7 2.X 組譯工具中的結構描述判斷](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)