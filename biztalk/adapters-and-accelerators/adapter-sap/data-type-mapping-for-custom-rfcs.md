---
title: 資料型別對應自訂 Rfc |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom RFCs, data type mapping
ms.assetid: 33539a5a-bdfc-423f-8026-436f69a20c70
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cac254734a35658e3aa635b086f765e8f06494a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-custom-rfcs"></a>自訂 Rfc 的資料類型對應
下表提供有關 SAP 資料類型和其如何對應至.NET 資料型別 Z_EXTRACT_DATA_OO RFC 的資訊。 使用這個自訂 RFC [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
> [!NOTE]
>  如 Z_EXECUTE_SAP_QUERY，這由[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]執行 EXECQUERY 命令，所有的 SAP 資料類型會轉換為.NET 字串類型。  
  
|SAP 資料類型|.NET 資料類型|  
|-------------------|--------------------|  
|ACCP|-Int32<br />的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。|  
|CHAR|字串|  
|CLNT|字串|  
|CUKY|字串|  
|目前|Decimal、 有效位數小於或等於 28 時<br /><br /> 字串，如果有效位數大於 28|  
|DATS|日期時間<br />的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。|  
|DEC|Decimal|  
|FLTP|Double|  
|INT1|Byte|  
|INT2|Int16|  
|INT4|Int32|  
|LANG|字串|  
|NUMC|-Int32，如果欄位長度小於或等於到 9<br />-Int64，如果欄位長度大於 9 且小於或等於 19<br />字串，如果大於 19<br />的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。|  
|PREC|Int16|  
|QUAN|Decimal|  
|RAW|Byte]|  
|RSTR|Byte]|  
|SSTR|字串|  
|STRG|字串|  
|TIMS|-TimeSpan<br />的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。|  
|單位|字串|  
|LCHR|字串|  
|LRAW|Byte]|  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)