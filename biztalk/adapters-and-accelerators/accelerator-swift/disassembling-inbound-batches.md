---
title: 解譯輸入批次使用 SWIFT |Microsoft Docs
description: 解除批次處理輸入的訊息，並自訂結構描述的批次使用 BizTalk Server 中的 SWIFT 加速器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f234ca9c867d978216972f8359c77de88aeebfa8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976239"
---
# <a name="disassemble-inbound-batches"></a>解譯輸入批次

## <a name="debatch-inbound-message"></a>解除批次處理輸入的訊息
SWIFT 解譯器可輸入解除批次中的方法，它可以處理，或解譯輸入批次 （檔案或包含多個 SWIFT 訊息的訊息）。 您會讓使用 SWIFT 解譯器設定屬性，具有相同名稱的輸入解除批次處理。 啟用輸入解除批次處理後，SWIFT 解譯器會預期要包含多個 SWIFT 訊息的批次接收所有訊息。 批次可能會或可能不會包含批次的信封 （批次標頭和批次結尾），以及每個個別的 SWIFT 訊息批次中可能會或可能不會包含訊息信封 （訊息標頭和訊息結尾）。 您可以設定使用下列的 SWIFT 解譯器組態屬性這些批次屬性 （格式）：  
  
- 批次標頭結構描述  
  
- 批次結尾結構描述  
  
- 訊息標頭結構描述  
  
- 訊息結尾結構描述  
  
  > [!NOTE]
  >  設定任何這些屬性，以 「 無 」 表示輸入的批次不包含該特定的組件。  
  
  SWIFT 解譯器會預期要有下列結構的所有輸入批次：  
  
  **批次標頭**  
  
  **訊息標頭**  
  
  **SWIFT 的交換訊息 （SWIFT 區塊的 1 到 5）**  
  
  **訊息結尾**  
  
  **批次結尾**  
  
  在此結構中，您可以考慮 「 訊息區塊 」 要**訊息標頭 – SWIFT 交換 – 訊息結尾**組件。 一系列的多個 「 訊息區塊 」 是由批次中的多個 SWIFT 訊息所組成。 批次標頭，訊息標頭，訊息結尾和批次結尾是選擇性的但是重複項目之間必須一致。  
  
> [!NOTE]
>  請勿混淆 SWIFT 的標頭和結尾區塊的訊息信封 （訊息標頭和訊息結尾）。 在批次內容中，您應該檢視 SWIFT 訊息 （交換），做為一個整體 (atomic) 的單位包括 SWIFT 標頭和結尾區塊。 在此情況下，訊息標頭和訊息結尾指信封包裝批次中的每個 SWIFT 的訊息。  
  
 若要更正式的說法 express 這個結構，其選項，其可重複性，請考慮如何[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義批次：  
  
- **批次標頭**由**BH**  
  
- **訊息標頭**由**MH**  
  
- **SWIFT 交換**由**SI**  
  
- **訊息結尾**由**MT**  
  
- **批次結尾**由**BT**。  
  
  運算式，表示預期的批次結構如下所示：  
  
  `[BH] ([MH] SI [MT])* [BT]  `
  
  在方括號 ( `[ ] ` ) 表示的部分是選擇性的。 星號 (**\\* * *) 表示的區塊是可重複。任何使用者建立的訊息批次，則必須使用訊息標頭 (*<em>MH</em>*) 和結尾 (*<em>MT</em>*) 中的每個重複以一致的方式 (`[MH] SI [MT]`)。  
  
  SWIFT 解譯器可處理任何遵守上述的結構的輸入批次，因為在結構中的每個組件符合一般檔案結構描述。 不過，如果您不使用訊息標頭/結尾與選擇性的批次標頭/結尾，訊息將會不符合這些結構描述。 如此一來，批次標頭結構描述、 批次結尾結構描述、 訊息標頭結構描述，並設定為 「 無 」 的訊息結尾結構描述屬性，會有包含連續的 SWIFT 訊息的批次。  

## <a name="customize-schemas-for-batching"></a>自訂批次結構的描述  
 您可以自訂訊息標頭/結尾與批次標頭/結尾的結構描述。 舉例來說，下列批次：  
  
```  
4  
SWIFT Message # 1  
$  
SWIFT Message # 2  
$  
SWIFT Message # 3  
$  
SWIFT Message # 4  
$  
```  
  
 若要處理這種類型的批次，您會設定批次結構描述屬性如下所示：  
  
- 您可以設定批次標頭結構描述屬性至剖析單一數字 （訊息計數） 以換行字元分隔的一般檔案結構描述。  
  
- 設定成剖析單一的 $ 符號和換行字元的一般檔案結構描述的訊息結尾結構描述。  
  
- 您可以設定剩餘信封結構描述 （批次結尾結構描述和訊息標頭結構描述） 為 None。  
  
  您可以設定 SWIFT 解譯器，它會處理任何 SWIFT 的訊息批次建立，並指定一般檔案信封結構描述的適當組合。 這項功能是非常大的彈性。  
  
  SWIFT 解譯器一律會嘗試完成處理整個批次，即使發生錯誤，在過程中。 這可讓它來收集和報告多個錯誤越好，全部一次。 若要執行這個 「 最大努力 」 啟發式，SWIFT 解譯器必須進行某些決策和假設選取在遇到新的組件 時使用的結構描述時，或會發生剖析錯誤。 選取正確的結構描述不一定能夠根據本質和剖析錯誤和模稜兩可/之間的相似度信封結構描述和 SWIFT 交換結構描述的位置。 在某些情況下，您可以減少可能會使用設計良好的信封結構描述，以選取錯誤的結構描述。 如果解譯器發生嚴重的剖析錯誤，或反組譯工具無法判斷正確的結構描述，解譯器將會失敗的批次，而不需處理剩餘的資料。  
  
  當**輸入解除批次處理**是**啟用**(設定為**True**)，SWIFT 解譯器剖析使用指定的批次的信封 （批次的標頭結構描述的結構描述的批次和批次結尾結構描述） 和訊息信封 （訊息標頭結構描述和訊息結尾結構描述），以及指定用於剖析批次中 SWIFT 的訊息 （交換） 的結構描述。 對於批次中 SWIFT 的訊息，訊息類型和結構描述可動態探索和載入單一的非批次訊息的相同方式 （藉由指定 SWIFT 標頭結構描述）。 如需 SWIFT 解譯器的結構描述解析的執行方式的詳細資訊，請參閱[動態訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。  
  
  SWIFT 解譯器會剖析，並個別驗證輸入的批次中每個 SWIFT 的訊息。 它會執行下列處理順序的批次：  
  
1. 如果您已經指定批次標頭結構描述，請剖析批次標頭。  
  
2. 如果您已指定訊息標頭結構描述，請剖析訊息信封標頭。  
  
3. 剖析 SWIFT 的交換 （訊息）。  
  
4. 如果您已啟用 XML 驗證，請驗證 XML 條件約束 SWIFT 訊息。  
  
5. 如果您已啟用 BRE 驗證，請驗證 BRE 原則 （SWIFT 網路和使用方式規則） SWIFT 訊息。  
  
6. 如果指定了訊息結尾結構描述，請剖析訊息信封結尾。  
  
7. 重複步驟 2 到 6，解譯器的批次中找不到任何訊息之前。  
  
8. 如果您已經指定批次結尾結構描述，請剖析批次的結尾。  
  
   您可以設定 SWIFT 解譯器，以執行批次資料，它會剖析並驗證使用下列的 SWIFT 解譯器設定屬性使用不同的動作：  
  
- **片段**屬性會決定是否 SWIFT 解譯器應該在批次至 MessageBox 資料庫中個別發佈每則訊息 (也就是為每個訊息之後每次出現的上述的步驟 6,)，則它應該完成所有步驟 1 到 8，然後將整個批次中，發行以原生格式 （的輸入的完全相同複本），當作單一訊息至 MessageBox 資料庫。 您設定**分散**要 **，則為 True**啟用片段，並個別發佈批次的訊息。 您設定**分散**要**False**停用片段，並將整個批次中，以原生格式，發佈當作單一訊息只有在處理整個批次之後。 一般而言，設定**片段**要**已停用**情況下，當您僅需要 BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) 來剖析及驗證輸入批次，然後失敗，或轉送，在同一個表單[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收它們。 通常設定**分散**要**已啟用**的情況下您想[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]來轉換或修改的批次內的訊息之後剖析和驗證，, 或您想要[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要重新排序順序不同於批次中的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]原來接收它們。 您也設定**片段**要**已啟用**包含有不同的最終目的地的訊息之輸入批次的案例。  
  
- **保留批次標頭 / 保留批次結尾**屬性會決定 SWIFT 解譯器應該捨棄或保留批次的信封 （標頭和結尾） 資料之後剖析它。 如果您設定**保留的批次標頭或保留批次結尾**要 **，則為 True**，解譯器個別的訊息將對應的批次組件 (剖析的 XML) 發佈到 MessageBox 資料庫。 解譯器會將資料發佈在多部分訊息內文部分。 解譯器會升級特殊的內容屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以將它們是在批次內這些訊息的批次，其來源而來的序數位置相互關聯 (批次結尾的最後一個位置中的 批次標頭的第一個位置）。 如果您設定**保留的批次標頭或保留批次結尾**要**False**，解譯器剖析之後捨棄對應的批次組件 （剖析的資料）。  
  
  > [!NOTE]
  >  這些組態屬性是有效的只有當啟用分割時 (**分散**設為 **，則為 True**)。 停用片段時，解譯器發佈的完全相同的複本，整個批次中，以原生格式，到 MessageBox 資料庫，因此保留設定無關 (*一切*保留)。  
  
- **保留的訊息標頭** / **保留訊息結尾**屬性會決定是否應該捨棄 SWIFT 解譯器，或者保留訊息信封 （訊息標頭和結尾）之後剖析它們。 如果您設定**保留的訊息標頭或保留訊息結尾**要 **，則為 True**，解譯器會將對應的批次組件 (剖析的 XML) 發佈到 MessageBox 資料庫*連同它所包裝的個別 SWIFT 訊息*。 解譯器將發佈中的訊息信封標頭**標頭**多部分訊息的一部分。 解譯器將發佈中的訊息信封結尾**結尾**多部分訊息的一部分。 解譯器會發佈在郵件信封中所包含的 SWIFT 訊息**主體**屬於相同的多部分訊息。 解譯器會升級特殊的內容屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以將這些訊息，其來源而批次，並已批次內的序數位置相互關聯。 如果您設定**保留的訊息標頭或保留訊息結尾**要**False**，解譯器剖析之後捨棄對應的批次組件 （剖析的資料）。  
  
  > [!NOTE]
  >  這些組態屬性是有效的只有當啟用分割時 (**分散**設為 **，則為 True**)。 停用片段時，解譯器發佈的完全相同的複本，整個批次中，以原生格式，到 MessageBox 資料庫，因此保留設定無關 (*一切*保留)。  
  
  如需每個組態屬性的詳細資訊，以及其他使用方式和組態資訊，請參閱 < [SWIFT 解譯器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。 如需 MessageBox 資料庫發行和多部分訊息的詳細資訊，請參閱 BizTalk Server 說明。  
  
## <a name="next-step"></a>下一步
  
[批次相關升級屬性](batch-related-promoted-properties.md)
