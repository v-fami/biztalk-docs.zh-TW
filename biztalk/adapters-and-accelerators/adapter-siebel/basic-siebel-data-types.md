---
title: 基本的 Siebel 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Siebel data types, supported
ms.assetid: bf86f639-6c45-49db-9e58-79c3ad2c9978
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d45a5c8b0caf16d38df7b368c6f0f63ba020d95
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971543"
---
# <a name="basic-siebel-data-types"></a>基本的 Siebel 資料類型
本章節描述如何支援 Siebel 資料類型上[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  

## <a name="supported-siebel-data-types"></a>支援的 Siebel 資料類型  
 下表顯示的 Siebel 資料類型，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援和它們如何呈現在配接器的 BizTalk （XSD 型別） 和 WCF 服務模型 （.NET 型別）。 將以星號標示的類型，請參閱表格後的注意事項。  


|     資料類型     |    XSD 類型    | .NET 類型 |                                                                                                                                                                                                                                                                                                                                                                             描述                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------|----------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    DTYPE_BOOL     |  xsd:boolean   |  布林  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|  DTYPE_CURRENCY   |  xsd:decimal   |  Decimal  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_DATE     | xsd:dateTime\* | DateTime  | 值不能為 Coordinated Universal Time (UTC)。<br /><br /> -對於 xsd:dateTime，值應該遵循這個模式:"(\d\d\d\d-\d\d-\d\d)T(00:00:00) (。\*) 」。<br />-若是**DateTime**物件，**DateTime.Kind**必須是**DateTimeKind.Unspecified**。<br /><br /> 配接器，將會忽略時間元件。<br /><br /> 對於輸出訊息，配接器會執行的執行階段驗證，以確保指定的值不是 UTC （z 或 UTC 時差）。 如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此型別會公開為 xsd: string （根據所述的規則）：<br /><br /> -格式取決於基礎資料庫。<br />-沒有執行階段上執行驗證的值。 |
|  DTYPE_DATETIME   | xsd:dateTime\* | DateTime  |                                                                                          值可以包含日期和時間元件，而且不得為 UTC。<br /><br /> -若是**DateTime**物件， **DateTime.Kind**必須是**DateTimeKind.Unspecified**。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證，以確保符合這些條件;如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此型別會公開為 xsd: string （根據所述的規則）：<br /><br /> -格式取決於基礎資料庫。<br />-沒有執行階段上執行驗證的值。                                                                                           |
|     DTYPE_ID      |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|   DTYPE_INTEGER   |    xsd:int     |   Int32   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_NOTE     |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|   DTYPE_NUMBER    |  xsd:decimal   |  Decimal  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_PHONE    |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_TEXT     |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_TIME     | xsd:dateTime\* | DateTime  |                                       值不能為 UTC。<br /><br /> -對於 xsd:dateTime，值應該遵循這個模式: (1753-01-01)T(\d\d:\d\d:\d\d) (。\*) 」。<br />-若是**DateTime**物件<strong>，DateTime.Kind</strong>必須是**DateTimeKind.Unspecified**。<br /><br /> 對於輸出訊息，配接器會執行的執行階段驗證，以確保指定的值不是 UTC （z 或 UTC 時差）。 如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此型別會公開為 xsd: string （根據所述的規則）：<br /><br /> -格式取決於基礎資料庫。<br />-沒有執行階段上執行驗證的值。                                       |
| DTYPE_UTCDATETIME | xsd:dateTime\* | DateTime  |                                                   值可以包含日期和時間元件，而且必須是 UTC。<br /><br /> -對於 xsd:dateTime，值必須以 UTC （'Z' 表示法或 UTC 時差） 來表示。<br />-若是**DateTime**物件**DateTime.Kind**必須是**DateTimeKind.Utc**。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證，以確保符合這些條件;如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此型別會公開為 xsd: string （根據所述的規則）：<br /><br /> -格式取決於基礎資料庫。<br />-沒有執行階段上執行驗證的值。                                                   |

 以下是商務服務方法引數型別：  

 date  
 與 DTYPE_DATE 相同。  

 Number  
 與 DTYPE_NUMBER 相同。  

 String  
 與 DTYPE_TEXT 相同。  

 階層  
 對應至 XSD 類型 xsd: string 和.Net 型別字串。  在 XML 訊息，這必須放在 CDATA 節點。  

 整合物件  
 與階層相同。  

 * 配接器會判斷是否要使用 以下列方式代表 DTYPE_DATE、 DTYPE_DATETIME、 DTYPE_TIME 和 DTYPE_UTCDATETIME 欄位商業元件中的 xsd:dateTime 或 xsd: string。  

1.  如果商務元件欄位之前的資料類型的其中一個，配接器會將它公開為 xsd:dateTime 型別 （在這會對應到 DateTime 類型的.Net)。  

2.  如果商務元件欄位沒有資料類型，配接器會將它公開為 xsd: string （在.Net 中這會對應至字串類型)。  

## <a name="supported-facets-for-the-xml-schema-types"></a>支援的 XML 結構描述型別 Facet  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援下列 facet 的 XML 結構描述型別。  

|Siebel 類型|Facet|  
|-----------------|-----------|  
|DTYPE_BOOL|無|  
|DTYPE_CURRENCY|有效位數 (22)，小數位數|  
|DTYPE_DATE|(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)|  
|DTYPE_DATETIME|無|  
|DTYPE_ID|MaxLength (15)|  
|DTYPE_INTEGER|有效位數 (22)|  
|DTYPE_NOTE|MaxLength (16384)|  
|DTYPE_NUMBER|有效位數 (22)，小數位數|  
|DTYPE_PHONE|MaxLength (40)|  
|DTYPE_TEXT|MaxLength (2048)|  
|DTYPE_TIME|(1753-01-01)T(\d\d:\d\d:\d\d)(.*)|  
|DTYPE_UTCDATETIME|無|  

 以下是一些規則會控制如何及何時 facet 和其值，都會被發行：  

 如果欄位的長度屬性設定為值小於或等於零且小於或等於 （在上表中的括號中指定） 的最大值：  

-   發佈有效位數 facet，如下所示：  

    -   如果有效位數屬性設定的欄位，就會發行相同的值，做為有效位數 facet。  

    -   如果欄位未設定有效位數屬性，就會做為有效位數 facet 發行的長度值。  

-   只有當這兩個，已發行的小數位數 facet:  

    -   已發行的有效位數屬性  

    -   [比例] 屬性設為欄位值小於或等於零且小於發佈為一部分的有效位數 facet 值  

-   MaxLength facet 是指定長度屬性的值。 這是從挑選欄位定義儲存機制。 如果未指定長度的欄位定義儲存機制中，取得發行在上表中的括號中指定的值。  

### <a name="special-cases-related-to-siebel-data-types"></a>相關的 Siebel 資料類型的特殊案例  
 下列規則會影響使用中作業的內容為基礎的商務元件欄位 facet。 這些規則是適用於 INSERT 和 UPDATE 作業。 針對查詢作業，所有的商務元件欄位會公開給使用者。  

 **商務元件欄位標示為必要 Siebel 中**  

 即使在 Siebel 系統中商務元件欄位標示為必要，但前的預設值或後續的預設值設定於欄位中，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]標示為選擇性欄位。 因此如果使用者提供的值來插入或更新，配接器會處理該值。 如果未不提供任何值，Siebel 會使用 default 預先/default 後值。  

 **未標示為唯讀在 Siebel 商務元件欄位**  

 如果商務元件欄位未標示為 READ ONLY[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開為可寫入的欄位。 不過，有幾個例外狀況，此規則。 它們是：  

- 如果商務元件欄位**Calculated**欄位中的 Siebel，它不會出現在 Insert 或 Update 作業因為 Siebel 會自動處理**Calculated**欄位。  

- 如果商務元件欄位透過明確聯結 （另一個資料表上的資料表聯結） 取得，它是一般唯讀的。 不過 Siebel 可讓資料寫入至這個欄位，如果它是挑選清單欄位。 因此，如果商務元件欄位是從明確聯結欄位不是挑選清單欄位，則它不會出現在 Insert 或 Update 作業因為配接器用戶端無法寫入這類欄位的資料。  

  **商務元件中未指定欄位的資料類型**  

  如果未在商務元件中，指定欄位的資料型別[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開 （expose) 使用下列啟發學習法的欄位中繼資料。  

- 如果欄位是一個特殊的欄位 （也就是挑選清單或聯結），[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]目的地商務元件中對應的欄位將會查閱。 如果該欄位，相關聯的類型為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開 （expose)，做為欄位的類型。 不過，如果該型別是 DTYPE_DATE、 DTYPE_TIME、 DTYPE_DATETIME，還是 DTYPE_UTCDATETIME，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開為 xsd: string 類型欄位。 如果對應的欄位沒有關聯的型別，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開 （expose) 的原始欄位做為 xsd: string 類型。  

- 如果欄位不是挑選清單或聯結欄位[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會將它公開為 xsd: string 類型。  

  **不提供資料類型、 欄位長度或上層業務元件的有效位數**  

  如果資料類型，長度，或欄位的上層業務元件 （已根據挑選清單或 MVLs 下層業務元件的商務元件），有效位數[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]取得有關資料類型、 長度、 有效位數和小數位數，從資訊挑選清單商務元件或 MVL 商務元件。  

## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)