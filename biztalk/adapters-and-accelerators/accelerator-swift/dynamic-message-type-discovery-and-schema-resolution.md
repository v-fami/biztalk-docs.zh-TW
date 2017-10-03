---
title: "動態訊息類型探索和結構描述解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic schema resolution
- disassembler, code sample
- schemas, dynamic resolution
- assembler, message types
- disassembler, message types
- code samples, disassembler
ms.assetid: 5f71d3df-a37e-4ef2-9055-b614656203e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77e9a8949787fcd3c7e942c406c9f31470894a8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-message-type-discovery-and-schema-resolution"></a>動態訊息類型探索和結構描述解析
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]啟用動態訊息類型探索和結構描述解析 SWIFT 解譯器和組合器中的。  
  
## <a name="swift-disassembler"></a>SWIFT 反組譯工具  
 SWIFT 的解譯器 (DASM) 能夠以動態方式探索接收訊息的訊息類型和載入會剖析訊息所需的適當結構描述。 這項功能的最大優點是，您可以設定單一管線來處理任何 SWIFT 訊息類型的 SWIFT 訊息使用 SWIFT 解譯器。 與原生 BizTalk 一般檔案解譯器，不同的是 SWIFT 解譯器不需要您建立個別的接收管線 A4SWIFT 可能會遇到每種訊息類型。  
  
 如果您假設，在大部分情況下，系統接收的所有訊息的都開頭是同質性結構上的標頭資料，您可以使用動態訊息類型探索。 標頭中的資料會顯示訊息的訊息類型的欄位。 SWIFT 的訊息標頭資料組成 SWIFT 訊息區塊 1、 2 和 3，以包含在區塊 （稱為應用程式標頭） 的 2 的訊息類型資訊。  
  
 SWIFT DASM 元件可以處理所有 「 單一 」 （非批次） SWIFT 訊息立即可用的而不需要任何設定的屬性。 根據預設，SWIFT 交換的結構描述和 SWIFT 標頭結構描述未設定。不過，SWIFT DASM 元件會使用存在於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll SWIFT 標頭結構描述來動態偵測 SWIFT 訊息類型和處理訊息。 此外，BRE 」 和 「 XML 驗證會預設啟用以便處理任何訊息將會完整驗證。 設定為指向 SWIFT 中的標頭 RuntimeSchemas.dll SWIFT 標頭結構描述屬性也會與上述相同的行為。  
  
 當 SWIFT 解譯器的 SWIFT 標頭結構描述組態屬性設定為"None"（預設值） 時，解譯器會以動態方式解析並藉由執行下列步驟，載入適當的結構描述：  
  
1.  您可以使用使用者指定的標頭結構描述 （SWIFT 標頭結構描述組態屬性所指定），剖析接收訊息的開頭 （標頭）。  
  
2.  會產生 「 標頭 XML 」 檢查 A4SWIFT_MessageType 升級的屬性欄位。 如果此欄位存在時，它會使用 [訊息類型] 欄位值，並繼續進行步驟 4。 如果欄位不存在，它會繼續進行步驟 3。  
  
3.  會檢查 A4SWIFT_MessageType2 升級的屬性欄位標頭的 XML （預期如果解譯器找不到 A4SWIFT_MessageType 欄位）。 使用 「 訊息類型 」 A4SWIFT_MessageType2 欄位值。  
  
4.  如果 「 訊息類型 」 步驟 2 或 3 中識別"574"，SWIFT 解譯器會檢查訊息類型 」 574 」 是否雙重類型的訊息清單組態屬性 （這是屬性的反組譯工具） 中指定的訊息類型的清單中。 如果是，它會繼續進行步驟 5。 若為否，繼續進行步驟 6。  
  
5.  會檢查標頭 XML A4SWIFT_SecondaryMessageType 升級的屬性欄位。 如果此欄位存在時，解譯器會使用 「 訊息子類型為"的欄位值 (例如，"IRSLST")，並將它附加到 「 訊息類型 」，例如，"574_IRSLST"。  
  
    > [!IMPORTANT]
    >  步驟 5 指定說明是簡化 SWIFT 解譯器實際用途的評估訊息的子類型。 事實上，SWIFT 解譯器會使用下列演算法來判斷訊息類型是否為子類型，而且如果是，哪些的子類型，如下所示。  
  
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
  
6.  解譯器現在會知道訊息類型，而且它可以形成交換的結構描述名稱串連某些固定的結構描述命名首碼及尾碼 （例如"MT"前置詞中讓 「 MT574_IRSLST")。  
  
7.  載入交換的結構描述 （依名稱），並將整個訊息，剖析**從頭開始**，使用載入的結構描述 (這表示解譯器剖析的標頭資料兩次： 一次使用的標頭結構描述，以及一次使用交換的結構描述的開頭）。 交換的結構描述必須是可以剖析整個訊息，包括標頭。  
  
    > [!NOTE]
    >  反組譯工具可以用來剖析整個 SWIFT 交換的所有 A4SWIFT SWIFT 訊息結構描述 （1、 2、 3、 4 和 5 SWIFT 區塊）。 解譯器會剖析區塊 1、 2 和 3 只使用預設 SWIFT 的標頭結構描述。 如需詳細資訊，請參閱後文。  
  
 上面所述的結構描述解析演算法表示，為了讓訊息動態類型探索才能運作，SWIFT 標頭結構描述必須包含反組譯工具有升級使用下列的升級的屬性 （在 A4SWIFT 中定義的欄位屬性結構描述，Microsoft.Solutions.A4SWIFT.Property.PropertySchema）：  
  
-   **A4SWIFT_MessageType**  
  
-   **A4SWIFT_MessageType2** (選擇性若**A4SWIFT_MessageTypes**用)  
  
-   **A4SWIFT_SecondaryMessageType** （選擇性）  
  
 如需有關這些和其他升級的屬性的詳細資訊，請參閱[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
> [!NOTE]
>  如果您將 SWIFT 標頭結構描述設**無**，您應該指定完整的交換結構描述**SWIFT 交換的結構描述**屬性。 在此情況下，解譯器會使用指定的交換的結構描述剖析 A4SWIFT 接收的所有訊息。 也就是您要停用動態結構描述解析，和設定管線來接收的訊息的類型符合指定的交換的結構描述。  
  
 A4SWIFT 安裝的預設 SWIFT 標頭結構描述 (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) 可以剖析 SWIFT 標準標頭資料，並具有必要的升級的屬性，以便動態結構描述解析。  
  
 預設 SWIFT 的標頭結構描述有下列的升級的欄位：  
  
-   **訊息類型 SWIFTHeader/ApplicationHeaderBlock_Input**。 解譯器將其升級使用**A4SWIFT_MessageType**屬性。  
  
-   **訊息類型 SWIFTHeader/ApplicationHeaderBlock_Output**。 解譯器將其升級使用**A4SWIFT_MessageType2**屬性。  
  
-   **SWIFTHeader/UserHeaderBlock/ValidationFlag_119**。 解譯器將其升級使用**A4SWIFT_MessageType**屬性。  
  
 解譯器會使用**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**標頭結構描述，如果您將 SWIFT 標頭結構描述和 SWIFT 交換的結構描述組態屬性設為預設 「None"。  
  
## <a name="swift-assembler"></a>SWIFT 組譯工具  
 SWIFT 的組譯工具，例如 SWIFT 組譯工具能夠以動態方式探索輸出訊息的訊息類型及載入序列化訊息所需的適當結構描述。 這項功能可讓您設定單一管線來處理任何 SWIFT 訊息類型的 SWIFT 訊息使用 SWIFT 組譯工具。 與原生 BizTalk 一般檔案組合器，不同的是 SWIFT 組合器不需要您建立個別的傳送管線 A4SWIFT 可能會遇到每種訊息類型。  
  
 動態結構描述解析的 SWIFT 組合器會比 SWIFT 解譯器中更簡單，因為組譯工具執行的 XML 序列化回一般檔案格式，SWIFT 工作。 XML 的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供 SWIFT 組譯工具，序列化包含訊息類型和結構描述資訊，其中 SWIFT 組譯工具可以使用直接載入適當的結構描述進行序列化。 因此，SWIFT 組譯工具沒有任何可設定性的標頭和交換的結構描述： 一律會使用指定的結構描述中的 XML，它會序列化。  
  
## <a name="see-also"></a>另請參閱  
 [SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)