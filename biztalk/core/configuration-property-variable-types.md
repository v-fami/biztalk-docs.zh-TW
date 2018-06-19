---
title: 組態屬性變數型別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, properties
- binding files, properties
- binding files, data types
- adapters, data types
ms.assetid: 703219ce-e275-4a07-a2ad-28010d8363e6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05b861100fb7843a95b250c233084c13924c28dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232806"
---
# <a name="configuration-property-variable-types"></a>組態屬性變數型別
繫結檔案之 TransportTypeData\CustomProps 節點中的配接器組態屬性符合 .NET Framework VarEnum 列舉中的可用資料型別。 下表列出相關資料型別。  
  
|成員名稱|說明|Value|  
|-----------------|-----------------|-----------|  
|VT_EMPTY|表示尚未指定值。|0|  
|VT_NULL|表示 null 值，和 SQL 中的 null 值類似。|1|  
|VT_I2|表示短整數。|2|  
|VT_I4|表示長整數。|3|  
|VT_R4|表示浮點值。|4|  
|VT_R8|表示雙精度浮點值。|5|  
|VT_CY|表示貨幣值。|6|  
|VT_DATE|表示 DATE 值。|7|  
|VT_BSTR|表示 BSTR 字串。|8|  
|VT_DISPATCH|表示 IDispatch 指標。|9|  
|VT_ERROR|表示 SCODE。|10|  
|VT_BOOL|表示布林值。|11|  
|VT_VARIANT|表示 VARIANT 遠程指標。|12|  
|VT_UNKNOWN|表示 IUnknown 指標。|13|  
|VT_DECIMAL|表示小數值。|14|  
|VT_I1|表示字元值。|16|  
|VT_UI1|表示位元組。|17|  
|VT_UI2|表示不帶正負號的短整數。|18|  
|VT_UI4|表示不帶正負號的長整數。|19|  
|VT_I8|表示 64 位元整數。|20|  
|VT_UI8|表示 64 位元不帶正負號的整數。|21|  
|VT_CLSID|表示類別識別碼。|72|  
|VT_ARRAY|表示 SAFEARRAY 指標。|8192|  
|VT_BYREF|表示數值為參考。|16384|