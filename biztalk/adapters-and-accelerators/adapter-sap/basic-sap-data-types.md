---
title: MySAP 配接器在 BizTalk 中的基本 SAP 資料型別 |Microsoft Docs
description: MySAP 配接器在 「 BizTalk 配接器組件 」 (BAP) 的支援的 ABAP 和資料庫資料類型
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 296b4813-f175-4a02-8fd3-227ae301bc3d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e878ff1830477bfb888415947cb50169394a9d46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015047"
---
# <a name="basic-sap-data-types"></a>基本 SAP 資料類型
參數型別[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]都受到支援:  

- ABAP SAP 支援的資料類型  

- SAP 支援的資料庫資料類型  

  此章節提供 ABAP 與資料庫的資料型別，以及其對應的.NET 和 XML 結構描述型別之間的對應。  

> [!NOTE]
>  在本節中的資訊適用於 Rfc、 Trfc 和 Bapi。 SAP 資料型別永遠會表示為在 Idoc 中的字串 (xsd: string) 中。 這是為了支援 BizTalk Server 的一般檔案剖析器。  

## <a name="supported-abap-data-types"></a>支援的 ABAP 資料類型  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援安全的輸入，針對某些 ABAP 資料類型。 啟用 「 安全輸入時，這些資料型別會表示為字串。 設定 藉由設定 「 安全輸入**EnableSafeTyping**繫結屬性。 預設會停用安全的輸入。 如需詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

 下表顯示 ABAP 資料型別安全輸入未啟用時的呈現方式。 (**EnableSafeTyping**為 false)。 啟用 「 安全輸入時以不同的方式呈現的資料類型會以星號 （*） 標示。  

|ABAP 資料類型|RFC 類型|XSD 類型|.NET 類型|格式字串|  
|--------------------|--------------|--------------|---------------|-------------------|  
|我 （整數）|RFC_INT|xsd:int|Int32|-|  
|內部 (RFC_INT1)|RFC_INT1|xsd:unsignedByte|Byte|-|  
|內部 (RFC_INT2)|RFC_INT2|xsd:short|Int16|-|  
|F （浮點數）|RFC_FLOAT|xsd:double|Double|-|  
|P （BCD 數字）|RFC_BCD|system.decimal 如果長度 < = 28<br />xsd: string 如果長度 > 28|Decimal<br />String|十進位數字。 具有 0 的小數位數<br />十進位數字。 使用 > 0 的小數位數|  
|C （字元）|RFC_CHAR|xsd:string|String|-|  
|D (Date: YYYYMMDD) *|RFC_DATE|xsd:dateTime|DateTime|就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後的日期元件 (**DateTime.Date**) 用來建立傳送至 SAP 系統的值。 SAP 系統會將這個日期值視為本地時間。<br /><br /> 您應該指定日期的值為 UTC，以避免轉換。<br /><br /> -對於 xsd:dateTime，建議使用下列模式:"(\d\d\d\d-\d\d-\d\d)T(00:00:00) (。\*)Z"。<br />-若是**DateTime**物件組**DateTime.Kind**來**DateTimeKind.Utc**。|  
|T (時間： HHMMSS) *|RFC_TIME|xsd:dateTime|DateTime|就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後階段元件 (**DateTime.Time**) 用來建立傳送至 SAP 系統的值。 SAP 系統會將此時間值視為本地時間。<br /><br /> 您應該指定時間值為 UTC，以避免轉換。<br /><br /> -對於 xsd:dateTime，建議使用下列模式:"(0001-01-01)T(\d\d:\d\d:\d\d) (。\*) 」。<br />-若是**DateTime**物件組**DateTime.Kind**來**DateTimeKind.Utc**。<br /><br /> 比方說，如果您的當地時間是上午 9:15，表示為"(001-01-01) T (09: 15:00) Z 」|  
|N （數字的字串） *|RFC_NUM|xsd: int 如果 lenrth < = 9<br />xsd:long、int64 如果 9 長度 > 和 < = 19<br />xsd: string 如果長度 > 19|Int32<br />long<br />String|-|  
|X （位元組）|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
|字串|RFC_STRING|xsd:string|String|-|  
|XSTRING|RFC_BYTE|xsd:base64Binary|Byte[]|-|  

 * 表示 「 安全輸入啟用時的資料類型以不同的方式呈現。  

### <a name="safe-typing-enabled"></a>啟用 「 安全輸入  
 下表顯示當啟用 「 安全輸入時以不同的方式呈現的 ABAP 資料類型 ( **EnableSafeTyping**繫結屬性為 true)。  

|ABAP 資料類型|RFC 類型|XSD 類型|.NET 類型|格式字串|  
|--------------------|--------------|--------------|---------------|-------------------|  
|D (Date: YYYYMMDD)|RFC_DATE|xsd:string|String|SAP 日期格式： YYYYMMDD。<br /><br /> 值，所以基本上是八個字元字串日期的數字，允許字元|  
|T (時間： HHMMSS)|RFC_TIME|xsd:string|String|SAP 時間格式： HHMMSS。<br /><br /> 值，所以基本上是六個字元的字串時間的數字，允許字元|  
|N （數字的字串）|RFC_NUM|xsd:string|String|N 個字元字串;其中 n = numc 欄位的長度。|  

 未啟用安全的輸入時，會顯示為相同的方式 ABAP 不在此資料表中的資料類型。  

### <a name="support-for-date-and-time-fields"></a>支援日期和時間欄位  
 ABAP 日期 (D) 和時間 (T) 型別時未啟用安全的輸入，當成 xsd:dateTime;不過，呈現的日期和時間類型的模式 facet 都不同。  

-   日期的模式 facet 是： `(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)`  

     例如，2007 年 7 月 7 日 (2007年-07-07) 會表示為：  

     `(2007-07-07)T(00:00:00)`。  

-   時間的模式 facet 是： `(0001-01-01)T(\d\d:\d\d:\d\d)(.*)`  

     例如，18:30:30 （下午 6 點 30 和 30 秒） 會表示為：  

     `(0001-01-01)T(18:30:30)`。  

#### <a name="how-does-the-adapter-represent-minimum-and-maximum-time-values-on-inbound-messages-from-sap"></a>為何的配接器代表最小值和輸入訊息上的最大時間值 （從 SAP)？  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統接收時間值時，會使用下列指導方針：  

-   配接器會將值為 0 小時、 0 分鐘，以及 0 秒 000000 (hhmmss) 和 240000 (hhmmss)。  

## <a name="supported-database-data-types"></a>支援的資料庫資料類型  
 方式[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]表面資料庫資料類型也取決於是否啟用安全的輸入。 下表顯示當未啟用安全的輸入配接器介面如何資料庫資料類型 ( **EnableSafeTyping**繫結屬性為 false)。 啟用 「 安全輸入時以不同的方式呈現的資料類型會以星號 （*） 標示。  


|     資料庫資料類型      |  RFC 類型  |                                                                                                                                                                                                                                                                                                              XSD                                                                                                                                                                                                                                                                                                              |                                                     .NET 類型                                                      |
|-----------------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
|   ACCP （張貼句點）\*   |  RFC_NUM   |                                                                                                                                                                                                                                                                                                            xsd:int                                                                                                                                                                                                                                                                                                            |                                                       Int32                                                        |
|            CHAR             |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|        CLNT （用戶端）        |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|    目前範圍內 （貨幣欄位）    |  RFC_BCD   |                                                                                                                                                 system.decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入的十進位的參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會捨去至 4.00003。                                                                                                                                                  |                                                      Decimal                                                       |
|     CUKY （貨幣索引鍵）     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|     DATS （[日期] 欄位）\*     |  RFC_DATE  |                                                 xsd:dateTime<br /><br /> 就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後的日期元件 (**DateTime.Date**) 用來建立傳送至 SAP 系統的值。 SAP 系統會將這個日期值視為本地時間。<br /><br /> 您應該指定日期的值為 UTC，以避免轉換。 建議使用下列模式:"(\d\d\d\d-\d\d-\d\d)T(00:00:00) (。\*)Z"。                                                 | DateTime<br /><br /> 您應該指定為 UTC 的日期值 (DateTime.Kind = DateTimeKind.Utc) 若要避免轉換。 |
|        DEC （數量）         |  RFC_BCD   |                                                                                                                                                 system.decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入的十進位的參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會捨去至 4.00003。                                                                                                                                                  |                                                      Decimal                                                       |
|    FLTP （浮點數）    | RFC_FLOAT  |                                                                                                                                                                                                                                                                                                          xsd:double                                                                                                                                                                                                                                                                                                           |                                                       Double                                                       |
|            INT1             |  RFC_INT1  |                                                                                                                                                                                                                                                                                                       xsd:unsignedbyte                                                                                                                                                                                                                                                                                                        |                                                        Byte                                                        |
|            INT2             |  RFC_INT2  |                                                                                                                                                                                                                                                                                                           xsd:short                                                                                                                                                                                                                                                                                                           |                                                       Int16                                                        |
|            INT4             |  RFC_INT   |                                                                                                                                                                                                                                                                                                            xsd:int                                                                                                                                                                                                                                                                                                            |                                                       Int32                                                        |
|     LANG （語言機碼）     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|            LCHR             | RFC_STRING |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|    LRAW (長位元組 seq)     |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
|           NUMC\*            |  RFC_NUM   |                                                                                                                                                                                                                                                                                             xsd:int<br />xsd:long<br />xsd:string                                                                                                                                                                                                                                                                                             |                  Int32 如果長度 < = 9<br />Int64 如果長度 > 9 和 < = 19<br />如果字串長度 > 19                   |
|       PREC （正確性）       |  RFC_INT2  |                                                                                                                                                                                                                                                                                                           xsd:short                                                                                                                                                                                                                                                                                                           |                                                       Int16                                                        |
|       QUAN （數量）       |  RFC_BCD   |                                                                                                                                                 system.decimal**附註：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]四捨五入的十進位的參數定義為基礎的十進位值。 比方說，如果 DECIMAL 參數可以接受最多五個位數，小數點後面，例如 4.000028 值會捨去至 4.00003。                                                                                                                                                  |                                                      Decimal                                                       |
|     RAW （位元組序列）     |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
| RAWSTRING （可變長度） |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
|  字串 （可變長度）   | RFC_STRING |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|     TIMS （[時間] 欄位）\*     |  RFC_TIME  | xsd:datetime<br /><br /> 就內部而言，配接器還原序列化成值**DateTime**物件。 然後它叫用**DateTime.ToUniversalTime**方法，將此物件的值轉換為 UTC。 最後階段元件 (**DateTime.Time**) 用來建立傳送至 SAP 系統的值。 SAP 系統會將此時間值視為本地時間。<br /><br /> 您應該指定時間值為 UTC，以避免轉換。 建議使用下列模式:"(0001-01-01)T(\d\d:\d\d:\d\d) (。\*)Z"。<br /><br /> 比方說，如果您的當地時間是上午 9:15，表示為"(001-01-01) T (09: 15:00) Z 」 | DateTime<br /><br /> 您應該指定時間值為 UTC (DateTime.Kind = DateTimeKind.Utc) 若要避免轉換。 |
|     單位 （單位為 Qty）     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|        [不支援]        |     --     |                                                                                                                                                                                                                                                                                                              --                                                                                                                                                                                                                                                                                                               |                                                       String                                                       |

 * 表示，配接器會呈現的資料型別以不同的方式啟用 「 安全輸入時。  

### <a name="safe-typing-enabled"></a>啟用 「 安全輸入  
 下表顯示的資料庫啟用 「 安全輸入時以不同的方式呈現的資料類型 ( **EnableSafeTyping**繫結屬性為 true)。  

|資料庫資料類型|RFC 類型|XSD|.NET 類型|字串值格式|  
|------------------------|--------------|---------|---------------|-------------------------|  
|ACCP （張貼句點）|RFC_NUM|xsd:string|String|字元字串|  
|NUMC|RFC_NUM|xsd:string|String|字元字串|  
|DATS （[日期] 欄位）|RFC_DATE|xsd:string|String|YYYYMMDD|  
|TIMS （[時間] 欄位）|RFC_TIME|xsd:string|String|HHMMSS|  

 未啟用安全的輸入時，不在此資料表中的資料類型會顯示為相同的方式。  

## <a name="supported-xsd-facets"></a>支援的 XSD Facet  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列 XSD facet。  

|RFC 類型|XSD Facet (**EnableSafeTyping** = false)|XSD Facet (**EnableSafeTyping** = true)|  
|--------------|-------------------------------------------------|------------------------------------------------|  
|RFC_BCD|**XSD 模式 facet**<br /><br /> **零個小數位數：** `"([\\-]{0,1})(([0-9]{1,"`  `+ digitsBeforeDecimal +`  `"}))"`<br /><br /> **一或多個小數位數：** `"([\\-]{0,1})(([0-9]{0,"` + `digitsBeforeDecimal +``"}\\.[0-9]{0,"``+ digitsAfterDecimal +``"})&#124;([0-9]{1,"``+ digitsBeforeDecimal +``"}))"`|相同|  
|RFC_NUM|**XSD totalDigits facet**如果長度 < = 19<br /><br /> **XSD 模式 facet**如果長度 > 19|**XSD maxLength facet （取決於 SAP 上值的長度）**|  
|RFC_DATE|**XSD 模式 facet**<br /><br /> `"(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)"`<br /><br /> 模式包含時間 00:00:00，才能與相容 `xsd:datetime`|**XSD maxLength facet = 8**|  
|RFC_TIME|**XSD 模式 facet**<br /><br /> `"(0001-01-01)T(\d\d:\d\d:\d\d)(.*)"`<br /><br /> 模式包含相容的日期以 0001-01-01 `xsd:datetime`|**XSD maxLength facet = 6**|  
|RFC_CHAR|**XSD maxLength facet**|相同|  

## <a name="unsupported-data-types"></a>不支援的資料類型  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援下列資料類型：  

-   ITAB II （階層式） 的資料表類型  

