---
title: "基本的 SAP 資料型別 mySAP 配接器在 BizTalk 中 |Microsoft 文件"
description: "MySAP 配接器在 BizTalk 配接器組件 (BAP) 的支援的 ABAP 和資料庫資料類型"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 296b4813-f175-4a02-8fd3-227ae301bc3d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40e7dc6f98e1de2ff0388a8e7e52fdabafc7681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="basic-sap-data-types"></a>基本的 SAP 資料類型
參數類型，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]都受到支援:  
  
-   SAP 支援的 ABAP 資料類型  
  
-   SAP 支援的資料庫資料類型  
  
 此章節提供的 ABAP 和資料庫資料類型，以及其對應的.NET 和 XML 結構描述型別之間的對應。  
  
> [!NOTE]
>  本節中的資訊適用於 Rfc、 tRFCs 和 Bapi。 SAP 資料型別一律會以在 Idoc 中的字串 (xsd: string) 表示。 這是為了支援 BizTalk Server 的一般檔案剖析器。  
  
## <a name="supported-abap-data-types"></a>支援的 ABAP 資料類型  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援 「 安全輸入某些 ABAP 資料類型。 啟用 「 安全輸入時，這些資料型別會表示為字串。 您可以設定 「 安全輸入藉由設定**EnableSafeTyping**繫結屬性。 輸入的安全預設會停用。 如需有關[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 下表顯示未啟用 「 安全輸入時，如何顯示 ABAP 資料型別。 (**EnableSafeTyping**為 false)。 啟用 「 安全輸入時以不同的方式呈現的資料類型會以星號 （*） 標示。  
  
|ABAP 資料類型|RFC 類型|XSD 類型|.NET 類型|格式字串|  
|--------------------|--------------|--------------|---------------|-------------------|  
|我 （整數）|RFC_INT|xsd:int|Int32|-|  
|內部 (RFC_INT1)|RFC_INT1|xsd:unsignedByte|Byte|-|  
|內部 (RFC_INT2)|RFC_INT2|xsd:short|Int16|-|  
|F (Float)|RFC_FLOAT|xsd:double|Double|-|  
|P （BCD 數字）|RFC_BCD|xsd:decimal 如果長度 < = 28<br />xsd: string 如果長度 > 28|Decimal<br />字串|十進位數字。 小數位數 0<br />十進位數字。 使用 > 0 的小數位數|  
|C （字元）|RFC_CHAR|xsd:string|字串|-|  
|D (Date: YYYYMMDD) *|RFC_DATE|xsd:dateTime|DateTime|就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後的日期部分 (**DateTime.Date**) 用來建立會傳送到 SAP 系統的值。 SAP 系統會將這個日期值視為本地時間。<br /><br /> 您應該為 UTC，若要避免轉換指定的日期值。<br /><br /> -若為 xsd:dateTime，建議使用下列模式:"(\d\d\d\d-\d\d-\d\d)T(00:00:00) (。\*)Z"。<br />-若為**DateTime**物件組**DateTime.Kind**至**DateTimeKind.Utc**。|  
|T (時間： HHMMSS) *|RFC_TIME|xsd:dateTime|DateTime|就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後階段元件 (**DateTime.Time**) 用來建立會傳送到 SAP 系統的值。 SAP 系統會將這個時間值視為本地時間。<br /><br /> 您應該指定時間值以 UTC 以避免轉換。<br /><br /> -若為 xsd:dateTime，建議使用下列模式:"(0001-01-01)T(\d\d:\d\d:\d\d) (。\*) 」。<br />-若為**DateTime**物件組**DateTime.Kind**至**DateTimeKind.Utc**。<br /><br /> 例如，如果您的當地時間上午 9:15，這項行為表示為"(001-01-01) T (09: 15:00) Z"|  
|N （數字的字串） *|RFC_NUM|xsd: int 如果 lenrth < = 9<br />xsd: long 如果長度 > 9 和 < = 19<br />xsd: string 如果長度 > 19|Int32<br />long<br />字串|-|  
|X （位元組）|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
|字串|RFC_STRING|xsd:string|字串|-|  
|XSTRING|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
  
 * 表示 「 安全輸入啟用時的資料類型會以不同的方式顯示。  
  
### <a name="safe-typing-enabled"></a>啟用 「 安全輸入  
 下表顯示時，會顯示以不同的方式啟用 「 安全輸入的 ABAP 資料型別 ( **EnableSafeTyping**繫結屬性為 true)。  
  
|ABAP 資料類型|RFC 類型|XSD 類型|.NET 類型|格式字串|  
|--------------------|--------------|--------------|---------------|-------------------|  
|D (Date: YYYYMMDD)|RFC_DATE|xsd:string|字串|SAP 日期格式： YYYYMMDD。<br /><br /> 字元允許日期的數字，因此值會基本上是八個字元的字串|  
|T (時間： HHMMSS)|RFC_TIME|xsd:string|字串|SAP 時間格式： HHMMSS。<br /><br /> 字元可時間數字，因此值會基本上六個字元字串|  
|N （數字的字串）|RFC_NUM|xsd:string|字串|N 個字元字串;其中 n = numc 欄位的長度。|  
  
 未啟用 「 安全輸入時便會顯示為相同的方式 ABAP 不在此資料表中的資料類型。  
  
### <a name="support-for-date-and-time-fields"></a>日期和時間欄位的支援  
 ABAP 日期 (D) 和時間 (T) 型別時未啟用 「 安全輸入，當成 xsd:dateTime;不過，日期和時間類型中顯示模式 facet 都不同。  
  
-   模式 facet，日期是：`(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)`  
  
     例如，2007 年 7 月 7 日 (2007年-07-07) 會表示如下：  
  
     `(2007-07-07)T(00:00:00)`。  
  
-   模式 facet，時間是：`(0001-01-01)T(\d\d:\d\d:\d\d)(.*)`  
  
     例如，18:30:30 （下午 6:30 和 30 秒） 會表示如下：  
  
     `(0001-01-01)T(18:30:30)`。  
  
#### <a name="how-does-the-adapter-represent-minimum-and-maximum-time-values-on-inbound-messages-from-sap"></a>如何執行配接器代表最小值和最大輸入訊息上的時間值 （從 SAP)？  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]收到來自 SAP 系統的時間值時，會使用下列指導方針：  
  
-   配接器會 000000 (hhmmss) 和 240000 (hhmmss) 視為 0 小時，0 分鐘為單位，0 秒。  
  
## <a name="supported-database-data-types"></a>支援的資料庫資料類型  
 方式[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]介面資料庫資料類型也取決於是否啟用 「 安全輸入。 下表顯示當未啟用 「 安全輸入配接器介面資料庫資料類型的方式 ( **EnableSafeTyping**繫結屬性為 false)。 啟用 「 安全輸入時以不同的方式呈現的資料類型會以星號 （*） 標示。  
  
|資料庫資料類型|RFC 類型|XSD|.NET 型別|  
|------------------------|--------------|---------|---------------|  
|ACCP （張貼期間） *|RFC_NUM|xsd:int|Int32|  
|CHAR|RFC_CHAR|xsd:string|字串|  
|CLNT （用戶端）|RFC_CHAR|xsd:string|字串|  
|目前 （貨幣欄位）|RFC_BCD|xsd:decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入小數參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會四捨五入至 4.00003。|Decimal|  
|CUKY （貨幣索引鍵）|RFC_CHAR|xsd:string|字串|  
|DATS （日期） *|RFC_DATE|xsd:dateTime<br /><br /> 就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後的日期部分 (**DateTime.Date**) 用來建立會傳送到 SAP 系統的值。 SAP 系統會將這個日期值視為本地時間。<br /><br /> 您應該為 UTC，若要避免轉換指定的日期值。 建議使用下列模式:"(\d\d\d\d-\d\d-\d\d) T (00: 00:00)(.*) Z"。|DateTime<br /><br /> 您應該將日期值指定為 UTC (DateTime.Kind = DateTimeKind.Utc) 若要避免轉換。|  
|DEC （容量）|RFC_BCD|xsd:decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入小數參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會四捨五入至 4.00003。|Decimal|  
|FLTP （浮點）|RFC_FLOAT|xsd:double|Double|  
|INT1|RFC_INT1|xsd:unsignedbyte|Byte|  
|INT2|RFC_INT2|xsd:short|Int16|  
|INT4|RFC_INT|xsd:int|Int32|  
|LANG （語言機碼）|RFC_CHAR|xsd:string|字串|  
|LCHR|RFC_STRING|xsd:string|字串|  
|LRAW (長位元組 seq)|RFC_BYTE|xsd:base64binary|Byte[]|  
|NUMC *|RFC_NUM|xsd:int<br />xsd:long<br />xsd:string|Int32 如果長度 < = 9<br />Int64 如果長度 > 9 和 < = 19<br />如果字串長度 > 19|  
|PREC （精確度）|RFC_INT2|xsd:short|Int16|  
|QUAN (Quantity)|RFC_BCD|xsd:decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入小數參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會四捨五入至 4.00003。|Decimal|  
|RAW （位元組序列）|RFC_BYTE|xsd:base64binary|Byte[]|  
|RAWSTRING （可變長度）|RFC_BYTE|xsd:base64binary|Byte[]|  
|字串 （可變長度）|RFC_STRING|xsd:string|字串|  
|TIMS （時間欄位） *|RFC_TIME|xsd:datetime<br /><br /> 就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後階段元件 (**DateTime.Time**) 用來建立會傳送到 SAP 系統的值。 SAP 系統會將這個時間值視為本地時間。<br /><br /> 您應該指定時間值以 UTC 以避免轉換。 建議使用下列模式:"(0001-01-01) T (\d\d:\d\d:\d\d)(.*) Z"。<br /><br /> 例如，如果您的當地時間上午 9:15，這項行為表示為"(001-01-01) T (09: 15:00) Z"|DateTime<br /><br /> 您應該指定時間值以 UTC (DateTime.Kind = DateTimeKind.Utc) 若要避免轉換。|  
|單位 （單位為 Qty）|RFC_CHAR|xsd:string|字串|  
|[不支援]|--|--|字串|  
  
 * 表示，配接器介面上的資料類型以不同的方式啟用 「 安全輸入時。  
  
### <a name="safe-typing-enabled"></a>啟用 「 安全輸入  
 下表顯示資料庫時，會顯示以不同的方式啟用 「 安全輸入的資料類型 ( **EnableSafeTyping**繫結屬性為 true)。  
  
|資料庫資料類型|RFC 類型|XSD|.NET 類型|字串值格式|  
|------------------------|--------------|---------|---------------|-------------------------|  
|ACCP （張貼週期）|RFC_NUM|xsd:string|字串|字元字串|  
|NUMC|RFC_NUM|xsd:string|字串|字元字串|  
|DATS （[日期] 欄位）|RFC_DATE|xsd:string|字串|YYYYMMDD|  
|TIMS （時間欄位）|RFC_TIME|xsd:string|字串|HHMMSS|  
  
 未啟用 「 安全輸入時便會顯示為相同的方式不在此資料表中的資料類型。  
  
## <a name="supported-xsd-facets"></a>支援的 XSD Facet  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列 XSD facet。  
  
|RFC 類型|XSD Facet (**EnableSafeTyping** = false)|XSD Facet (**EnableSafeTyping** = true)|  
|--------------|-------------------------------------------------|------------------------------------------------|  
|RFC_BCD|**XSD 模式 facet**<br /><br /> **零小數位數：**`"([\\-]{0,1})(([0-9]{1,"`  `+ digitsBeforeDecimal +`  `"}))"`<br /><br /> **一或多個小數位數：**`"([\\-]{0,1})(([0-9]{0,"` + `digitsBeforeDecimal +``"}\\.[0-9]{0,"``+ digitsAfterDecimal +``"})&#124;([0-9]{1,"``+ digitsBeforeDecimal +``"}))"`|相同|  
|RFC_NUM|**XSD totalDigits facet**如果長度 < = 19<br /><br /> **XSD 模式 facet**如果長度 > 19|**XSD maxLength facet （取決於 SAP 上值的長度）**|  
|RFC_DATE|**XSD 模式 facet**<br /><br /> `"(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)"`<br /><br /> 模式包含時間 00:00:00 與相容性`xsd:datetime`|**XSD maxLength facet = 8**|  
|RFC_TIME|**XSD 模式 facet**<br /><br /> `"(0001-01-01)T(\d\d:\d\d:\d\d)(.*)"`<br /><br /> 模式包含可與相容的日期以 0001-01-01`xsd:datetime`|**XSD maxLength facet = 6**|  
|RFC_CHAR|**XSD maxLength facet**|相同|  
  
## <a name="unsupported-data-types"></a>不支援的資料類型  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援下列資料類型：  
  
-   ITAB II （階層式） 的資料表類型  
  
