---
title: 反組譯 SWIFT 與輸入批次 |Microsoft 文件
description: Debatch 輸入的訊息，並自訂結構描述的批次在 BizTalk Server 中使用 SWIFT 加速器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f14a199e3422a45235727d2d16fc1464e2e4927
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="disassemble-inbound-batches"></a>反組譯輸入批次

## <a name="debatch-inbound-message"></a>Debatch 輸入的訊息
SWIFT 解譯器就能輸入解除批次處理即將它處理或反組譯輸入批次 （檔案或包含多個 SWIFT 訊息的訊息）。 您可以啟用輸入解除批次處理即將使用相同名稱的 SWIFT 解譯器組態屬性。 輸入解除批次處理即將啟用之後，SWIFT 解譯器會預期收到要包含多個 SWIFT 訊息的批次的所有訊息。 批次可能會或可能不會包含在批次的信封 （批次標頭和批次結尾），以及每個批次內的個別 SWIFT 訊息可能會或可能不會包含訊息信封 （訊息標頭和訊息結尾）。 您可以設定這些批次屬性 （格式） 使用下列 SWIFT 解譯器組態屬性：  
  
-   批次標頭結構描述  
  
-   批次結尾結構描述  
  
-   訊息標頭結構描述  
  
-   訊息結尾結構描述  
  
    > [!NOTE]
    >  設定任一這些屬性為"None"，表示輸入批次不包含該特定部分。  
  
 SWIFT 解譯器需要輸入的所有批次會有下列結構：  
  
 **批次標頭**  
  
 **訊息標頭**  
  
 **SWIFT 的交換訊息 （SWIFT 區塊的 1 到 5）**  
  
 **訊息結尾**  
  
 **批次結尾**  
  
 在此結構中，您可以考慮使用 「 訊息區塊 」 是**– SWIFT 交換 – 訊息標頭訊息結尾**組件。 一系列的多個 「 訊息區塊 」 是由批次中的多個 SWIFT 訊息所組成。 批次標頭、 訊息標頭、 訊息結尾和批次結尾是選擇性的但重複項目之間必須一致。  
  
> [!NOTE]
>  請勿混淆 SWIFT 的標頭和結尾區塊的訊息信封 （訊息標頭和訊息結尾）。 在批次內容中，您應該檢視 SWIFT 訊息 （交換），做為一個整體 (atomic) 的單位包括 SWIFT 標頭和結尾區塊。 在此情況下，訊息標頭和訊息結尾指包裝批次中的每個 SWIFT 訊息的信封。  
  
 若要多正式表示此結構，其選項，以及其重複性，請考慮如何[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義批次：  
  
-   **批次標頭**由**BH**  
  
-   **訊息標頭**由**MH**  
  
-   **SWIFT 交換**由**SI**  
  
-   **訊息結尾**由**MT**  
  
-   **批次結尾**由**BT**。  
  
 表示預期的批次結構的運算式如下所示：  
  
 `[BH] ([MH] SI [MT])* [BT]  `
  
 在方括號 ( `[ ] ` ) 表示部分是選擇性的。 星號 (**\***) 表示區塊是可重複。 誰會建立訊息批次，則必須使用訊息標頭 (**MH**) 和結尾 (**MT**) 一致的方式中的每個重複 (`[MH] SI [MT]`)。  
  
 SWIFT 解譯器就能夠處理遵守上述的結構，任何輸入批次，因為在結構中的每個組件符合一般檔案結構描述。 不過，如果您未使用的選擇性批次標頭/結尾與訊息標頭/結尾，訊息將不符合這些結構描述。 如此一來，包含連續的 SWIFT 訊息的批次都有批次標頭結構描述、 批次結尾結構描述、 訊息標頭結構描述，以及訊息結尾結構描述屬性設定為"None"。  

## <a name="customize-schemas-for-batching"></a>自訂批次結構的描述  
 您可以自訂訊息標頭/結尾與批次標頭/結尾的結構描述。 下列批次是範例：  
  
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
  
 若要處理這種類型的批次，您應該設定為批次結構描述屬性，如下所示：  
  
-   您設定批次標頭結構描述屬性為一般檔案結構描述剖析歸位字元分隔的單一數字 （郵件計數）。  
  
-   設定成單一的 $ 符號和歸位字元-剖析一般檔案結構描述的訊息結尾結構描述。  
  
-   您可以設定剩餘信封結構描述 （批次結尾結構描述和訊息標頭結構描述） 為 None。  
  
 您可以設定 SWIFT 解譯器，會處理幾乎任何 SWIFT 訊息批次建立並指定一般檔案信封結構描述的適當組合。 這項功能相當富彈性。  
  
 SWIFT 解譯器一律會嘗試完成處理整個批次，即使遇到在過程中的錯誤。 這可讓它來收集和報告所有錯誤越好，一次。 若要執行此 「 盡力 」 啟發式，SWIFT 解譯器必須進行某些決策和假設選取在遇到新的組件 時使用的結構描述時，或剖析錯誤，就會發生。 選取正確的結構描述不一定能的本質和剖析錯誤和模稜兩可/之間的相似度信封結構描述和 SWIFT 交換結構描述的位置而定。 在某些情況下，您可以最小化，可能會使用設計良好的信封結構描述，以選取錯誤的結構描述。 如果解譯器發生嚴重的剖析錯誤，或反組譯工具無法判斷正確的結構描述，解譯器將會失敗批次，而不需處理其餘的資料。  
  
 當**輸入解除批次處理即將**是**啟用**(設定為**True**)，SWIFT 的解譯器剖析批次使用指定的批次的信封 （批次的標頭結構描述的結構描述和批次結尾結構描述） 和訊息信封 （訊息標頭結構描述和訊息結尾結構描述），以及指定用於剖析批次中的 SWIFT 訊息 （交換） 的結構描述。 對於批次中 SWIFT 的訊息，訊息類型和結構描述可動態探索和載入為單一的非批次訊息相同的方式 （藉由指定 SWIFT 標頭結構描述）。 如需如何 SWIFT 的解譯器會執行結構描述解析的詳細資訊，請參閱[動態的訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。  
  
 SWIFT 解譯器會剖析並個別驗證傳入的批次中每個 SWIFT 訊息。 它會執行下列處理順序的批次：  
  
1.  如果您已經指定批次標頭結構描述，剖析批次標頭。  
  
2.  如果您已經指定訊息標頭結構描述，請剖析訊息信封標頭。  
  
3.  剖析 SWIFT 的交換 （訊息）。  
  
4.  如果您已啟用 XML 驗證，請驗證 XML 條件約束 SWIFT 訊息。  
  
5.  如果您已啟用 BRE 驗證，請驗證 BRE 原則 （SWIFT 網路與使用規則） SWIFT 訊息。  
  
6.  如果訊息結尾結構描述指定，會剖析訊息信封結尾。  
  
7.  重複步驟 2 到 6，直到解譯器在批次中找不到任何其他訊息。  
  
8.  如果您已經指定批次結尾結構描述，剖析批次結尾。  
  
 您可以設定 SWIFT 的解譯器，以執行不同的動作與批次資料，它會剖析並驗證使用的下列 SWIFT 解譯器組態屬性：  
  
-   **片段**屬性會決定是否 SWIFT 解譯器應該在批次至 MessageBox 資料庫中個別發行每個訊息 (也就是針對每個訊息之後每次發生上述的步驟 6,)，或是否應該完成所有步驟 1 到 8，然後發行整個批次中，以原生格式 （的輸入的完全相同複本），當做單一訊息至 MessageBox 資料庫。 您設定**片段**至**True**啟用片段和個別發行從批次的訊息。 您設定**片段**至**False**停用片段並將整個批次中，以原生格式，發行為處理整個批次之後，只有單一訊息。 一般而言，設定**片段**至**已停用**案例，當您僅需要 BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) 剖析及驗證輸入批次和失敗，或轉送，在同一個表單[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收它們。 通常設定**片段**至**啟用**情況下您想在其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]轉換或修改訊息的批次內之後剖析和驗證，, 或您想要[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要重新排序批次中的訊息順序不同什麼[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]原來接收它們。 也設定**片段**至**啟用**包含具有不同的最終目的地的訊息之輸入批次的案例。  
  
-   **保留批次標頭 / 保留批次結尾**屬性會決定 SWIFT 解譯器應該捨棄或剖析它之後保留批次的信封 （標頭和結尾） 資料。 如果您設定**保留批次標頭或保留批次結尾**至**True**，解譯器將對應的批次部分 (剖析的 XML) 發佈到 MessageBox 資料庫當做個別訊息。 解譯器會將資料發行中多部分訊息的內文部分。 解譯器將特殊的內容屬性升級，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以相互關聯的批次內已這些訊息的批次，它們的來源和序數位置 （批次標頭的第一個位置，最後一個位置的批次結尾）。 如果您設定**保留批次標頭或保留批次結尾**至**False**，解譯器會在之後剖析捨棄對應的批次部分 （剖析的資料）。  
  
    > [!NOTE]
    >  只有在啟用片段時，這些組態屬性是有效 (**片段**設**True**)。 停用片段時，解譯器發行整個批次，完全相同複本中的原生格式，到 MessageBox 資料庫，以便保留設定無關 (*一切*保留)。  
  
-   **保留訊息標頭** / **保留訊息結尾**屬性會決定 SWIFT 解譯器應該捨棄或保留訊息信封 （訊息標頭和結尾）之後剖析它們。 如果您設定**保留訊息標頭或保留訊息結尾**至**True**，解譯器會將對應的批次部分 (剖析的 XML) 發佈到 MessageBox 資料庫*連同它所包裝的個別 SWIFT 訊息*。 解譯器將發佈中的訊息信封標頭**標頭**多部分訊息的一部分。 解譯器將發佈中的訊息信封結尾**結尾**多部分訊息的一部分。 解譯器將發佈中的訊息信封中包含的 SWIFT 訊息**主體**屬於相同的多部分訊息。 解譯器將特殊的內容屬性升級，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以相互關聯的這些訊息，它們來自批次，並將它們批次中的序數位置。 如果您設定**保留訊息標頭或保留訊息結尾**至**False**，解譯器會在之後剖析捨棄對應的批次部分 （剖析的資料）。  
  
    > [!NOTE]
    >  只有在啟用片段時，這些組態屬性是有效 (**片段**設**True**)。 停用片段時，解譯器發行整個批次，完全相同複本中的原生格式，到 MessageBox 資料庫，以便保留設定無關 (*一切*保留)。  
  
 如需有關每個組態屬性，以及其他使用方式和組態資訊，請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。 如需 MessageBox 資料庫發行和多部分訊息的詳細資訊，請參閱 BizTalk Server 說明。  
  
## <a name="next-step"></a>下一步
  
[批次相關升級屬性](batch-related-promoted-properties.md)
