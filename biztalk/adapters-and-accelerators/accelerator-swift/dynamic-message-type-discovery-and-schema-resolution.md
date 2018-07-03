---
title: 動態訊息類型探索和解析結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic schema resolution
- disassembler, code sample
- schemas, dynamic resolution
- assembler, message types
- disassembler, message types
- code samples, disassembler
ms.assetid: 5f71d3df-a37e-4ef2-9055-b614656203e9
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5bbc5f8afaa8c08da04e9eab1b476e5884b2e6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986407"
---
# <a name="dynamic-message-type-discovery-and-schema-resolution"></a>動態訊息類型探索和結構描述解析
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]實現動態訊息類型探索和結構描述解析 SWIFT 解譯器和組合器中的。  
  
## <a name="swift-disassembler"></a>SWIFT 解譯器  
 SWIFT 解譯器 (DASM) 具有動態探索接收訊息的訊息類型，並載入適當的結構描述來剖析訊息所需的能力。 這項功能的最大優點是，您可以設定單一管線來處理任何 SWIFT 的訊息類型的 SWIFT 訊息使用 SWIFT 解譯器。 不同於原生 BizTalk 一般檔案解譯器，SWIFT 解譯器不需要您建立個別的接收管線 A4SWIFT 可能會遇到每種訊息類型。  
  
 如果您假設，在大部分情況下，系統會接收的所有訊息的都開頭結構同質性的標頭資料，您可以使用動態訊息類型探索。 標頭內的資料會顯示訊息的訊息類型的欄位。 SWIFT 的訊息標頭資料包含 SWIFT 訊息區塊 1、 2 和 3，以包含在區塊 （稱為應用程式標頭） 的 2 的訊息型別資訊。  
  
 SWIFT DASM 元件可以處理所有 「 單一 」 （非批次） SWIFT 訊息根據預設，而不需要任何設定的屬性。 根據預設的 SWIFT 交換的結構描述和 SWIFT 標頭結構描述未設定;不過，SWIFT DASM 元件會使用存在於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll SWIFT 標頭結構描述，來動態偵測 SWIFT 訊息類型，並處理訊息。 此外，BRE 」 和 「 XML 驗證會預設啟用以便處理任何訊息將會完整驗證。 SWIFT 標頭結構描述屬性設定為指向 RuntimeSchemas.dll SWIFT 標頭也會與上述相同的行為。  
  
 當 SWIFT 解譯器的 SWIFT 標頭結構描述的組態屬性設定為"None"（預設值） 時，解譯器動態解析，並載入適當的結構描述，執行下列步驟：  
  
1. 您可以使用 （SWIFT 標頭結構描述的組態屬性所指定） 的使用者指定的標頭結構描述，剖析接收訊息的開頭 （標頭）。  
  
2. 會產生 「 標頭 XML 」 檢查 A4SWIFT_MessageType 升級的屬性欄位。 如果此欄位存在，它會使用的欄位值為 「 訊息類型 」，並繼續進行步驟 4。 如果欄位不存在，便會繼續進行步驟 3。  
  
3. 會檢查 A4SWIFT_MessageType2 升級的屬性欄位的標頭 XML （預期如果解譯器找不到 A4SWIFT_MessageType 欄位）。 使用 A4SWIFT_MessageType2 欄位值做為 「 訊息類型 」。  
  
4. 如果 「 574"的 「 訊息類型 」 在步驟 2 或 3 中識別，SWIFT 解譯器會檢查訊息類型"574 」 是否雙重類型的訊息清單組態屬性 （這是屬性的反組譯工具） 中指定的訊息類型的清單中。 如果是，它會繼續進行步驟 5。 若為否，則會繼續進行步驟 6。  
  
5. 會檢查 A4SWIFT_SecondaryMessageType 升級的屬性欄位的 XML 標頭。 如果此欄位存在時，解譯器會使用 「 訊息子類型為"的欄位值 (例如，"IRSLST 」)，並將其附加至 「 訊息類型 」，比方說，「 574_IRSLST"。  
  
   > [!IMPORTANT]
   >  步驟 5 所提供的說明是簡化的 SWIFT 解譯器實際用途來評估訊息的子類型。 實際上，SWIFT 解譯器會使用以下演算法以判斷訊息類型具有子類型，且如果是這樣，哪些的子類型，如下所示。  
  
   ```  
   Given MT type number nxx ...  
   if nxx is in the Dual-Type list {  
     if field 119 exists AND field 119 is NOT null/empty {  
       if n == 1 {  
         if field 119 == "STP" {  
           Use MTnxxPLUS schema  
         } else if field 119 == "REMIT" {  
           Use MTnxx schema  
         } else {  
           Use MTnxx_<field 119> schema  
         }   
       } else {  
         // n != 1  
         Use MTnxx_<field 119> schema  
       }  
     } else {  
       // field 119 does not exist or 119 does exist but is null/empty  
       Use MTnxx schema  
     }  
   } else {  
     // nxx is not a dual-type message  
     Use MTnxx schema  
   }  
   ```  
  
6. 反組譯工具現在知道訊息類型，並以形成交換結構描述名稱串連一些固定的結構描述命名前置詞和尾碼 （例如"MT"前置詞中讓 「 MT574_IRSLST")。  
  
7. 載入交換結構描述 （依名稱），並剖析整個訊息，**從頭開始**，使用載入的結構描述 (這表示解譯器剖析的標頭資料兩次： 一次使用標頭的結構描述，並再次使用交換結構描述的開頭）。 交換結構描述必須是能夠剖析整個訊息，包括標頭。  
  
   > [!NOTE]
   >  反組譯工具可以使用所有 A4SWIFT SWIFT 訊息結構描述來剖析整個 SWIFT 交換 （1、 2、 3、 4 和 5 SWIFT 區塊）。 解譯器會剖析區塊 1、 2 和 3 只使用預設 SWIFT 標頭結構描述。 如需詳細資訊，請參閱後文。  
  
   上面所述的結構描述解析演算法表示，為了讓動態訊息類型探索才能運作，SWIFT 標頭結構描述必須包含解譯器已升級使用下列的升級的屬性 （在 A4SWIFT 中定義的欄位屬性結構描述，Microsoft.Solutions.A4SWIFT.Property.PropertySchema）：  
  
- **A4SWIFT_MessageType**  
  
- **A4SWIFT_MessageType2** (若**A4SWIFT_MessageTypes**用)  
  
- **A4SWIFT_SecondaryMessageType** （選擇性）  
  
  如需有關這些和其他升級的屬性的詳細資訊，請參閱 < [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
> [!NOTE]
>  如果您將設定 SWIFT 標頭結構描述**無**，您應該指定完整的交換結構描述**SWIFT 交換結構描述**屬性。 在此情況下，解譯器會使用指定的交換結構描述來剖析 A4SWIFT 接收的所有訊息。 也就是您要停用動態結構描述解析，並設定管線來接收其類型符合指定的交換結構描述的訊息。  
  
 A4SWIFT 安裝的預設 SWIFT 標頭結構描述 (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema)，可以剖析 SWIFT 的標準標頭資料，並具備必要的升級的屬性，以便動態結構描述解析。  
  
 預設的 SWIFT 標頭結構描述有下列的升級的欄位：  
  
- **SWIFTHeader/ApplicationHeaderBlock_Input/MessageType**。 解譯器將其升級使用**A4SWIFT_MessageType**屬性。  
  
- **SWIFTHeader/ApplicationHeaderBlock_Output/MessageType**。 解譯器將其升級使用**A4SWIFT_MessageType2**屬性。  
  
- **SWIFTHeader/UserHeaderBlock/ValidationFlag_119**。 解譯器將其升級使用**A4SWIFT_MessageType**屬性。  
  
  解譯器會使用**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**標頭結構描述，如果您將 SWIFT 標頭結構描述和 SWIFT 交換的結構描述組態屬性設為預設 「None"。  
  
## <a name="swift-assembler"></a>SWIFT 組合器  
 SWIFT 解譯器，例如 SWIFT 組合器能夠動態探索輸出訊息的訊息類型，並載入序列化訊息所需的適當結構描述。 這項功能可讓您設定單一管線來處理任何 SWIFT 的訊息類型的 SWIFT 訊息使用 SWIFT 組合器。 不同於原生的 BizTalk 一般檔案組合器 SWIFT 組合器不需要您建立個別的傳送管線 A4SWIFT 可能會遇到每種訊息類型。  
  
 SWIFT 組合器中的動態結構描述解析會比 SWIFT 解譯器中更簡單，因為 「 組合器 」 會將 XML 序列化回至 SWIFT 的一般檔案格式的工作。 XML 的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]讓 SWIFT 組合器序列化包含訊息類型和結構描述資訊，其中 SWIFT 組合器可以直接使用來載入適當的結構描述進行序列化。 因此，SWIFT 組合器並沒有任何可設定性的標頭和交換的結構描述： 一律會使用指定的結構描述的 XML 中，它會序列化。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)