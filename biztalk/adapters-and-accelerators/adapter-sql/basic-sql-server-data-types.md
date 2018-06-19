---
title: 基本的 SQL Server 資料類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f744fe14-4134-486d-b060-9ac2d5f21c56
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8e60816dc362fc4630e263397048bcdee8d774b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222614"
---
# <a name="basic-sql-server-data-types"></a>基本的 SQL Server 資料類型
本主題描述如何[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現基本的 SQL Server 資料類型。  
  
## <a name="supported-sql-server-data-types"></a>支援的 SQL Server 資料類型  
 下表顯示由 SQL Server 資料類型會顯示如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
|SQL Server 資料類型|XSD 類型|.NET 類型|註解|  
|--------------------------|--------------|---------------|--------------|  
|Bigint|長整數|長整數|-|  
|二進位|Base64Binary|Byte[]|-|  
|bit|布林|Bool|-|  
|Char|字串|字串|-|  
|日期|DateTime|DateTime|-|  
|Datetime|DateTime|DateTime|嘗試寫入的日期時間欄位的資料，配接器永遠都會以 GMT 儲存時間。 如果您指定的時區資訊時，配接器會將值轉換為有效的 GMT 值，使用該，並將它寫入至資料庫資料表。 例如，12/31/2008T23:59:59 + 5:30 會寫入至資料表作為 2008 年 12 月 31 日下午 6:29:59。<br /><br /> 不過，如果您未指定時區資訊，配接器會將這個值為 gmt，和相同的值寫入至資料表。 例如，12/31/2008T23:59:59 會寫入至資料表作為 2008 年 12 月 31 日 11:59:59 PM。|  
|Datetime2|DateTime|DateTime|-|  
|Datetimeoffset|DateTime|DateTime|-|  
|Decimal|如果精確度 xsd:decimal < = 28<br /><br /> 如果精確度 xsd: string > 28|如果有效位數十進位 < = 28<br /><br /> 如果有效位數的字串 > 28|-|  
|檔案資料流|Base64Binary|Byte[]|-|  
|Float|Double|Double|-|  
|Geography|字串|字串|-|  
|幾何|字串|字串|-|  
|Hierarchyid|字串|字串|-|  
|映像|Base64Binary|Byte[]|-|  
|int|int|int|-|  
|Money|Decimal|Decimal|-|  
|Nchar|字串|字串|-|  
|Ntext|字串|字串|-|  
|數值|Decimal|Decimal|-|  
|nvarchar|字串|字串|-|  
|Nvarchar （max)|字串|字串|-|  
|Real|Float|Float|-|  
|Smalldatetime|DateTime|DateTime|-|  
|Smallint|Short|Short|-|  
|Smallmoney|Decimal|Decimal|-|  
|SQLVariant|字串|字串|-|  
|Text|字串|字串|-|  
|Time|有效期間|Timespan|-|  
|時間戳記|Base64Binary|Byte[]|-|  
|Tinyint|UnsignedByte|Byte|-|  
|Uniqueidentifier|{http://schemas.microsoft.com/2003/10/Serialization/}: guid|Guid|-|  
|Varbinary|Base64Binary|Byte[]|-|  
|Varbinary （max)|Base64Binary|Byte[]|-|  
|Varchar|字串|字串|-|  
|Varchar （max)|字串|String|-|  
|XML|String|字串|-|  
  
## <a name="see-also"></a>另請參閱  
 [訊息與 BizTalk adapter for SQL Server 的訊息結構描述](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)