---
title: SAP 配接器在 SAPParameterCollection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPParameterCollection, supported methods and classes
ms.assetid: fd09355b-95f4-4d49-a643-b13058e63d74
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 924cb884c64f337cec0e628c804b5c5a8c6cf37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapparametercollection-class-in-the-sap-adapter"></a>SAP 配接器在 SAPParameterCollection 類別
下節列出方法和屬性的**SAPParameterCollection**類別。 這衍生自**System.Data.Common.DbParameterCollection**。  
  
## <a name="supported-properties"></a>支援的屬性  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**Count**|Get|集合中的參數數目。|  
|**IsFixedSize**|Get|不支援。 傳回 false。|  
|**IsReadOnly**|Get|不支援。 傳回 false。|  
|**IsSynchronized**|Get|不支援。 傳回 false。|  
|**Syncroot 同步**|Get|傳回之鎖定物件。|  
  
## <a name="supported-methods"></a>支援的方法  
  
|名稱|Description|  
|----------|-----------------|  
|**Add(SAPParameter)**|參數不能屬於多個 ParameterCollection。|  
|**Add （object)**|物件應該是 SAPParameter 型別。|  
|**AddRange(System.Array)**|將 SAPParameter 執行個體的陣列。|  
|**Clear （)**|清除集合中的參數。|  
|**Contains(object)**|檢查根據參數執行個體。|  
|**Contains(string)**|參數名稱為基礎的檢查。|  
|**CopyTo （SAPParameter []，int）**|複製 SAPParameter 型別的陣列以參數清單。|  
|**CopyTo (System.Array，int)**|複製到陣列的參數清單。|  
|**GetEnumerator()**|集合中取得參數的列舉值。|  
|**IndexOf(object)**|依據 SAPParameter 執行個體的參數索引。|  
|**IndexOf(string)**|參數以 SAPParameter 名稱為基礎的索引。|  
|**插入 （int，object）**|將 SAPParameter 插入至集合。|  
|**Remove(object)**|移除 SAPParameter 到根據執行個體的集合。|  
|**RemoveAt(int)**|集合中指定索引處移除 SAPParameter。|  
|**RemoveAt(string)**|移除 SAPParameter 至名稱為基礎的集合。|  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)