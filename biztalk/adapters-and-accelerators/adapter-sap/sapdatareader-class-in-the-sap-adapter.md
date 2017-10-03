---
title: "SAP 配接器在 SAPDataReader 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPDataReader, supported methods and classes
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe658058b6d00b4a22b333ef5683a285b9cab3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapdatareader-class-in-the-sap-adapter"></a>SAP 配接器在 SAPDataReader 類別
下節列出方法和屬性的**SAPDataReader**類別。 這衍生自**System.Data.Common.DbDataReader**。  
  
## <a name="supported-properties"></a>支援的屬性  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**深度**|Get|不支援。 傳回 0。|  
|**FieldCount**|Get|目前的記錄組中的欄位數目|  
|**IsClosed**|Get|傳回資料讀取器的狀態|  
|**RecordsAffected**|Get|不支援。 會傳回-1|  
  
## <a name="supported-methods"></a>支援的方法  
  
|名稱|Description|  
|----------|-----------------|  
|**Close （)**|關閉 DataReader|  
|**取得 [方法]**<sup>*</sup><br /><br /> 在 [方法] 是預期的資料類型。 例如 GetInt32(int)|取得預期的資料類型為基礎的資料行值|  
|**IsDBNull(int)**|不支援。 傳回 false。|  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)