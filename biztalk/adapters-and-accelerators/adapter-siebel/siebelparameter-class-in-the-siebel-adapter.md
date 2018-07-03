---
title: Siebel 配接器中的 SiebelParameter 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelParameter
- Data Provider for Siebel, SiebelParameter
- SiebelParameter, supported properties and methods
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff2f0f5324dfacd118bc59dccfa524819acaa75
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021948"
---
# <a name="siebelparameter-class-in-the-siebel-adapter"></a>Siebel 配接器中的 SiebelParameter 類別
[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供`DbParameter`實作，以啟用的 ADO.NET 用戶端，來指定特定命令的參數。 使用的執行個體`System.Data.Common.DbCommand`的類別[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，用戶端程式可以取得的執行個體`System.Data.Common.DbParameter`類別。  

```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  

 或者，您可以使用下列方法：  

```  

//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  

 `SiebelParameter`類別繼承自`DbParameter`。  命名空間中存在`Microsoft.Data.SiebelClient`。  

## <a name="supported-properties"></a>支援的屬性  
 `SiebelParameter`類別支援下列`DbParameter`*公用*屬性：  


|       [屬性]        |   取得或設定   |                                                                                                            描述                                                                                                            |
|-------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **DbType**     | 取得和設定 |                                               參數的資料型別。 請參閱[基本的 Siebel 資料類型](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。                                               |
|   **方向**   | 取得和設定 | 支援下列值：<br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput` |
|  **IsNullable**   | 取得和設定 |                                                                               屬性不支援，並將會擲回例外狀況，如果呼叫。                                                                               |
| **參數名稱** | 取得和設定 |                                  [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援這個屬性來指定參數名稱的 ADO.NET 用戶端。                                  |
|     **ReplTest1**     | 取得和設定 |                                                    [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]表示為字串的參數值。                                                    |

###  <a name="BKMK_Datatypes"></a> 支援的資料類型  
 下表摘要說明簡單 Siebel 欄位型別[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援。 如需詳細涵蓋範圍，請參閱[基本的 Siebel 資料型別](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。  

|Siebel 欄位類型|.NET 類型|XML 結構描述類型|  
|-----------------------|---------------|---------------------|  
|DTYPE_BOOL|布林|xsd:boolean|  
|DTYPE_CURRENCY|Decimal|xsd:decimal|  
|DTYPE_DATE|DateTime|xsd:dateTime|  
|DTYPE_DATETIME|DateTime|xsd:dateTime|  
|DTYPE_ UTCDATETIME|DateTime|xsd:dateTime|  
|DTYPE_ID|String|xsd:string|  
|DTYPE_INTEGER|Integer|xsd:int|  
|DTYPE_NOTE|String|xsd:string|  
|DTYPE_NUMBER|Decimal|xsd:decimal|  
|DTYPE_PHONE|String|xsd:string|  
|DTYPE_TEXT|String|xsd:string|  
|DTYPE_TIME|DateTime|xsd:dateTime|  

## <a name="supported-methods"></a>支援的方法  
 `SiebelParameter`類別不會覆寫中的任何特殊方法`DbParameter`。  

## <a name="see-also"></a>另請參閱  
 [使用 Siebel 配接器擴充 ADO.NET 介面](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)