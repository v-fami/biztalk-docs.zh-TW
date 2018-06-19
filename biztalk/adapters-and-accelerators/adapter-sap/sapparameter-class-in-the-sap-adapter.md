---
title: SAP 配接器在 SAPParameter 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPParameter, supported methods, classes, and constructors
ms.assetid: 60053393-ad22-4c99-abae-e538d43c8e18
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ff43c344cc14adb3deef226c270adc3ca94f2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217998"
---
# <a name="sapparameter-class-in-the-sap-adapter"></a>SAP 配接器在 SAPParameter 類別
下節列出方法和屬性的**SAPParameter**類別。 這衍生自**System.Data.Common.DbParameter**。  
  
## <a name="supported-properties"></a>支援的屬性  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**DbType**|Get|如果傳回參數的 DbType。 無法設定。|  
|**方向**|取得和設定|不支援 ParameterDirection.ReturnValue。|  
|**IsNullable**|-|不支援。|  
|**參數名稱**|取得和設定|參數的名稱。|  
|**大小**|-|不支援。|  
|**SourceColumn**|-|不支援。|  
|**SourceColumnNullMapping**|-|不支援。|  
|**SourceVersion**|-|不支援。|  
|**值**|取得和設定|參數的值|  
  
## <a name="supported-methods"></a>支援的方法  
  
|名稱|Description|  
|----------|-----------------|  
|**ResetDbType()**|不支援。|  
  
## <a name="supported-constructors"></a>支援的建構函式  
  
|名稱|Description|  
|----------|-----------------|  
|**SAPParameter()**|SAP 參數執行個體。|  
|**SAPParameter(string)**|SAP 與 SAP 的參數名稱的參數。|  
|**SAPParameter （字串、 DbType）**|SAP DbType 與 SAP 參數名稱的參數。|  
|**SAPParameter （字串、 物件）**|SAP 與 SAP 參數名稱和值的參數。 複雜型別具有值的類型 DataTable 和 XML 字串。|  
|**SAPParameter （字串、 ParameterDirection）**|SAP 參數與 SAP 參數名稱和參數方向。|  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)