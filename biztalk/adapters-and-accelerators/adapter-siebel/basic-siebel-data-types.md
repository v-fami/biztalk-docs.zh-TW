---
title: 基本的 Siebel 資料類型 |Microsoft 文件
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
ms.openlocfilehash: 0266f445c2fd8a7cba9a0e2089b9542813230580
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22218750"
---
# <a name="basic-siebel-data-types"></a>基本的 Siebel 資料型別
本章節描述如何在支援 Siebel 資料型別[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
## <a name="supported-siebel-data-types"></a>支援的 Siebel 資料類型  
 下表顯示的 Siebel 資料型別，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援和它們如何呈現配接器的 BizTalk （XSD 類型） 和 WCF 服務模型 （.NET 型別） 中。 將以星號標示的型別，請參閱表格後的注意事項。  
  
|資料類型|XSD 類型|.NET 類型|Description|  
|---------------|--------------|---------------|-----------------|  
|DTYPE_BOOL|xsd:boolean|布林|-|  
|DTYPE_CURRENCY|xsd:decimal|Decimal|-|  
|DTYPE_DATE|xsd:dateTime*|DateTime|值不能為 Coordinated Universal Time (UTC)。<br /><br /> -若為 xsd:dateTime，值應為遵循這個模式:"(\d\d\d\d-\d\d-\d\d)T(00:00:00) (。\*) 」。<br />-若為**DateTime**物件**DateTime.Kind**必須**DateTimeKind.Unspecified**。<br /><br /> 配接器會忽略時間元件。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證以確定指定的值不是 UTC （z 或 UTC 時差）。 如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此類型會公開為 xsd: string （根據規則，如下所述）：<br /><br /> -格式取決於基礎資料庫。<br />-不執行階段會執行驗證的值。|  
|DTYPE_DATETIME|xsd:dateTime*|DateTime|值可以包含日期和時間元件，而且不得為 UTC。<br /><br /> -若為**DateTime**物件**DateTime.Kind**必須**DateTimeKind.Unspecified**。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證，以確保符合這些條件。如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此類型會公開為 xsd: string （根據規則，如下所述）：<br /><br /> -格式取決於基礎資料庫。<br />-不執行階段會執行驗證的值。|  
|DTYPE_ID|xsd:string|字串|-|  
|DTYPE_INTEGER|xsd:int|Int32|-|  
|DTYPE_NOTE|xsd:string|字串|-|  
|DTYPE_NUMBER|xsd:decimal|Decimal|-|  
|DTYPE_PHONE|xsd:string|字串|-|  
|DTYPE_TEXT|xsd:string|字串|-|  
|DTYPE_TIME|xsd:dateTime*|DateTime|值不能為 UTC。<br /><br /> -若為 xsd:dateTime，值應為遵循這個模式: (1753-01-01)T(\d\d:\d\d:\d\d) (。\*) 」。<br />-若為**DateTime**物件 **，DateTime.Kind**必須**DateTimeKind.Unspecified**。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證以確定指定的值不是 UTC （z 或 UTC 時差）。 如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此類型會公開為 xsd: string （根據的規則如下所述）：<br /><br /> -格式取決於基礎資料庫。<br />-不執行階段會執行驗證的值。|  
|DTYPE_UTCDATETIME|xsd:dateTime*|DateTime|值可以包含日期和時間元件，而且必須是 UTC。<br /><br /> -若為 xsd:dateTime，此值必須以表示 utc 時區 （'Z' 標記法或 UTC 時差）。<br />-若為**DateTime**物件**DateTime.Kind**必須**DateTimeKind.Utc**。<br /><br /> 對於輸出訊息，配接器會執行執行階段驗證，以確保符合這些條件。如果驗證失敗，配接器會擲回例外狀況。<br /><br /> 當此類型會公開為 xsd: string （根據規則，如下所述）：<br /><br /> -格式取決於基礎資料庫。<br />-不執行階段會執行驗證的值。|  
  
 商務服務方法的引數類型如下：  
  
 日期  
 與 DTYPE_DATE 相同。  
  
 Number  
 與 DTYPE_NUMBER 相同。  
  
 字串  
 與 DTYPE_TEXT 相同。  
  
 階層  
 對應於 XSD 型別 xsd: string 和.Net 型別字串。  在 XML 訊息，這必須放在 CDATA 節點。  
  
 整合物件  
 階層相同。  
  
 * 配接器會決定是否要使用 xsd:dateTime 或 xsd: string 以下列方式代表 DTYPE_DATE、 DTYPE_DATETIME、 DTYPE_TIME 和 DTYPE_UTCDATETIME 商業元件中的欄位。  
  
1.  如果商務元件欄位前面的資料型別之一，配接器會將它公開為 xsd:dateTime （這會對應到 DateTime 類型的.Net) 中的型別。  
  
2.  如果商務元件欄位沒有資料型別，配接器會將它公開為 xsd: string （這會對應至字串類型的.Net) 中。  
  
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
  
 以下是一些規則會控制如何及何時會發佈 facet 和它們的值：  
  
 如果欄位的長度屬性設定為值小於或等於零且小於或等於 （在上表中的括號中指定） 的最大值：  
  
-   有效位數 facet 已發行，如下所示：  
  
    -   如果精確度屬性設定的欄位，就會發行相同的值，做為有效位數 facet。  
  
    -   如果精確度屬性未設定的欄位，長度值就會發行做為有效位數 facet。  
  
-   只有當這兩個，已發行的小數位數 facet:  
  
    -   已發行的有效位數屬性  
  
    -   標尺屬性設為欄位值小於或等於零且小於有效位數 facet 的一部分已發佈的值  
  
-   MaxLength facet 是指定 Length 屬性的值。 這被挑選從欄位定義儲存機制。 如果未指定長度的欄位定義儲存機制中，取得發行在上表中的括號中指定的值。  
  
### <a name="special-cases-related-to-siebel-data-types"></a>特殊情況下，相關的 Siebel 資料類型  
 下列規則會影響的作業中使用的內容為基礎的商務元件欄位 facet。 這些規則也適用於 INSERT 和 UPDATE 作業。 查詢作業會公開給使用者的商務元件的所有欄位。  
  
 **商務元件欄位標示為 REQUIRED Siebel 中**  
  
 即使商務元件欄位標示為 REQUIRED Siebel 系統中，但前的預設值或後續的預設值都會設為欄位，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]標示為選擇性欄位。 因此如果使用者提供要插入或更新的值，配接器處理該值。 如果未不提供任何值，Siebel 會使用 default 前/default 後的值。  
  
 **未標示為 Siebel 中 READ ONLY 商務元件欄位**  
  
 如果商務元件欄位未標示為 READ ONLY[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開為可寫入的欄位。 不過，有幾個這項規則的例外狀況。 它們是：  
  
-   如果商務元件欄位**計算**欄位 Siebel，它不會出現在 Insert 或 Update 作業因為 Siebel 會自動處理**計算**欄位。  
  
-   如果商務元件欄位已取得透過明確聯結 （資料表聯結在另一個資料表上），它是一般唯讀的。 不過 Siebel 可讓資料寫入至這個欄位，如果它是挑選清單的欄位。 因此，如果商務元件欄位是從明確聯結的欄位不挑選清單欄位，然後它不會出現在 Insert 或 Update 作業因為配接器用戶端無法寫入這類欄位的資料。  
  
 **商務元件中未指定欄位的資料類型**  
  
 如果未在商務元件中，指定欄位的資料型別[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開欄位中繼資料，使用下列啟發學習法。  
  
-   如果欄位是一個特殊的欄位 （也就是挑選清單或聯結）[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]目的地商務元件中的對應欄位將會查詢。 如果該欄位，與相關聯的類型為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開，做為欄位的類型。 不過，如果該型別是 DTYPE_DATE、 DTYPE_TIME、 DTYPE_DATETIME 或 DTYPE_UTCDATETIME，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開為 xsd: string 類型欄位。 如果對應的欄位沒有關聯的型別，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開 （expose) 的原始 xsd: string 類型欄位。  
  
-   如果沒有欄位的挑選清單或聯結欄位[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會將它公開為 xsd: string 類型。  
  
 **資料類型、 欄位長度或有效位數的上層業務元件不是使用**  
  
 如果資料類型，長度，或欄位的上層業務元件 （已根據挑選清單或 MVLs 下層業務元件商務元件），精確度[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]取得有關資料類型、 長度、 有效位數和小數位數的資訊挑選清單商務元件或 MVL 商務元件。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)