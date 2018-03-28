---
title: 基本的 Oracle 資料型別 Oracle EBS 配接器在 BizTalk 中 |Microsoft 文件
description: 資料和 XSD 類型、 安全的輸入，與 Oracle E-business Suite 中 BizTalk 配接器組件 (BAP) 中的驗證
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 008bf621-8b4e-450d-b354-ee26b91592f2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9012e2ef6adaf94f55b87bbccfc24b7fb889fbf3
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="basic-oracle-data-types"></a>基本的 Oracle 資料類型
本主題描述如何[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現基本的 Oracle 資料型別。  
  
## <a name="supported-oracle-data-types"></a>支援的 Oracle 資料類型  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援某些 Oracle 資料類型的 「 安全輸入。 啟用 「 安全輸入時，這些資料型別會表示為字串。 您可以設定啟用 「 安全輸入**EnableSafeTyping**繫結屬性 （預設為停用）。 如需有關[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
> [!NOTE]
>  不支援安全的輸入，如果資料類型是在使用者定義型別 (Udt) 內部。  
  
 下表顯示如何停用安全輸入提出的 Oracle 資料型別 (**EnableSafeTyping**是**false**)。 Oracle 資料類型受到**EnableSafeTyping**繫結屬性標示星號 （*）。  
  
|Oracle 資料類型|XSD 類型|.NET 類型|註解|  
|----------------------|--------------|---------------|--------------|  
|BFile|輸入： xsd: string<br /><br /> 輸出： xsd:base64Binary|字串<br /><br /> Byte[]|BFile 資料型別不支援複雜型別 （例如 RecordType TableType、 UDT 和 VArray） 內。|  
|Blob|xsd:base64Binary|Byte[]|-|  
|Char|xsd:string|字串|-|  
|Clob|xsd:string|字串|-|  
|日期 *<br /><br /> （沒有安全輸入如果 UDT 內）|xsd:dateTime|DateTime|日期值不能包含時區資訊 （UTC 或 UTC 位移）：<br /><br /> -xsd:dateTime 值不能包含 UTC 或 UTC 位移<br />-   **DateTime.Kind**必須**DateTimeKind.Unspecified**<br /><br /> 如果指定的時區資訊時，配接器會擲回**XmlReaderParsingException**例外狀況，並指出欄位的訊息。 **注意：** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開為 xsd:dateTime 而不是 xsd: date 的 Oracle Date 資料類型，因為： <ul><li>Oracle 的日期資料類型也可以包含時間值。</li><li>不沒有對等的 xsd: date 的任何.NET。</li></ul>|  
|Float * *|xsd:float 如果 prec < = 7<br /><br /> xsd:double 如果 prec > 7 和 < = 15<br /><br /> xsd: string 如果 prec > 15|Float<br /><br /> Double<br /><br /> 字串|您必須指定值為十進位字元和群組分隔符號，在指定的格式一致**NumericCharacters**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**NumericCharacters**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
|IntervalDS|xsd:string<br /><br /> 如果在 UDT xsd:duration|字串<br /><br /> 如果在 UDT Timespan|配接器使用 OracleIntervalDS.ToString 方法以字串形式傳回 IntervalDS 資料。<br /><br /> 此值應以 Oracle 原生格式表示： 天 HH:MI:SSxFF (例如"5 15:30:12.99")。|  
|IntervalYM|xsd:string<br /><br /> 如果在 UDT 的 xsd: long|字串<br /><br /> 若長 UDT|配接器使用 OracleIntervalYM.ToString 方法以字串形式傳回 IntervalYM 資料。<br /><br /> 此值應以 Oracle 原生格式表示： 年-月;例如，"1-2"（1 年和 2 個月）。|  
|長整數|xsd:string|字串|從 Oracle 資料庫 9i 版開始，LONG 資料類型已被取代。 Oracle 建議改用大型物件 (LOB) 資料類型。 因此，執行的作業上的 Oracle 資料庫時使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，我們建議使用 Oracle 資料庫成品操作的 LOB 資料類型和 LONG 資料類型。|  
|LongRaw|xsd:base64Binary|Byte[]|-|  
|NChar|xsd:string|字串|-|  
|NClob|xsd:string|字串||  
|數字 * *|xsd:decimal 如果 prec < = 28<br /><br /> xsd: string 如果 prec > 28|Decimal<br />字串|-|  
|NVarchar2|xsd:string|字串|-|  
|未經處理|xsd:base64Binary|Byte[]||  
|RowID|xsd:string|字串|-|  
|TimeStamp*<br /><br /> （沒有安全輸入如果 UDT 內）|xsd:dateTime if prec <= 7<br /><br /> xsd: string 如果 prec > 7|DateTime<br /><br /> 字串|當公開為字串 (prec > 7)，此值應該表示 Oracle NLS_TIMESTAMP_FORMAT 中。 您可以指定時間戳記資料類型中的字串格式**TimeStampFormat**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**TimeStampFormat**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。<br /><br /> 時間戳記值不能包含時區資訊 （UTC 或 UTC 位移）：<br /><br /> -xsd:dateTime 值不能包含 UTC 或 UTC 位移<br />-   **DateTime.Kind**必須**DateTimeKind.Unspecified**<br /><br /> 如果指定的時區資訊時，配接器會擲回**XmlReaderParsingException**例外狀況，並指出欄位的訊息。|  
|TimeStampLTZ|xsd:string|字串|TimeStampLTZ Udt 內不支援。<br /><br /> **外部 UDT**： 此值應在 Oracle NLS_TIMESTAMP_TZ_FORMAT 表示。 您可以指定 TimeStampLTZ 中之資料類型的字串格式**TimeStampTZFormat**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**TimeStampTZFormat**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
|TimeStampTZ|xsd:string<br /><br /> 如果在 UDT xsd:dateTime|字串<br /><br /> 如果在 UDT 的日期時間|**外部 UDT**： 此值應在 Oracle NLS_TIMESTAMP_TZ_FORMAT 表示。 您可以指定 TimeStampTZ 中之資料類型的字串格式**TimeStampTZFormat**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**TimeStampTZFormat**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
|Decimal**|xsd:decimal 如果 prec < = 28<br /><br /> xsd: string 如果 prec > 28|Decimal<br /><br /> 字串|-|  
|varchar2|xsd:string|字串|-|  
|二進位 Float * *|xsd:float 如果 prec < = 7<br /><br /> xsd: string 如果 prec > 7|Float<br /><br /> 字串|您必須指定值為十進位字元和群組分隔符號，在指定的格式一致**NumericCharacters**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**NumericCharacters**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
|二進位雙 * *|xsd:double 如果 prec < = 15<br /><br /> xsd: string 如果 prec > 15|Double<br /><br /> 字串|-|  
|二進位整數 * *|xsd:integer|Int32||  
|布林|xsd:boolean|可為 null 的布林值||  
|XMLTYPE|xsd:string|字串|支援最上層的層級程序參數。<br /><br /> 保留的 XML 字元，例如 '**\<**'、'**\>**' 必須使用其實體表示法取代**(&lt;， &gt;)**開發 biztalk 應用程式時，並使用 WCF 通道模型。 這不需要在 WCF 服務模型的情況下。|  
  
 \*形式出現這些 Oracle 資料類型的方式會受到**EnableSafeTyping**繫結屬性。  
  
 \*\*中的這些 Oracle 內資料集和弱式類型的 REF CURSOR 的數值資料類型便會顯示受影響的方式**EnableSafeTyping**繫結屬性。  
  
> [!IMPORTANT]
>  -   在 Oracle 資料類型中的值的最大長度[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]受限於 ODP.NET 所支援的 Oracle 資料類型的值的最大長度。  
> -   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會將內部 Oracle 數值資料類型，在 Udt 當做.NET 十進位。 不過，在一般 （亦即外部 Udt）、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]在內部視為 OracleDecimal 的 Oracle 數值資料類型。  
  
## <a name="safe-typing-enabled"></a>啟用 「 安全輸入  
 下表顯示 「 安全輸入受影響的 Oracle 資料型別會變更當**EnableSafeTyping**繫結屬性是**true**。  
  
> [!NOTE]
>  啟用或停用安全輸入不在此資料表中的 oracle 資料型別便會顯示相同的方式。  
  
|Oracle 資料類型|XSD 類型|.NET 類型|註解|  
|----------------------|--------------|---------------|-------------|  
|日期|xsd:string|字串|此值應在 Oracle NLS_DATE_FORMAT 表示。 您可以指定日期中之資料類型格式**DateFormat**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**DateFormat**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
|TimeStamp|xsd:string|字串|此值應在 Oracle NLS_TIMESTAMP_FORMAT 表示。 您可以指定時間戳記資料類型中的字串格式**TimeStampFormat**繫結屬性下的**MlsSettings**繫結屬性。 如果未不指定任何值，如**TimeStampFormat**繫結屬性，配接器使用 MLS 設定 ODP.NET 用戶端在同一部電腦上安裝配接器。|  
  
> [!IMPORTANT]
>  如果已啟用 「 安全輸入，Oracle 數值資料類型內的資料集和弱型別 REF 資料指標一律公開為字串。  
  
## <a name="validation"></a>驗證  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]對您指定的 Oracle 資料類型的值執行任何明確的驗證。 不過，根據 Oracle 資料型別和安全的輸入是啟用還是停用，可能會執行隱含的驗證：  
  
-   在還原序列化之間的 XML 傳遞訊息和配接器會在內部使用的.NET 類型中。  
  
-   由 ODP.NET 某些資料類型。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle E-Business Suite 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)