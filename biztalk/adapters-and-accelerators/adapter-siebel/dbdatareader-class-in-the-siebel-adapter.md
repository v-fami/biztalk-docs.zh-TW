---
title: Siebel 配接器在 DbDataReader 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, DbDataReader
- DbDataReader
ms.assetid: 7673cd10-ec1e-4cb0-93c2-f11928d00ca2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ad584571f7ef746a43032935e42e377ceb6cd70
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012615"
---
# <a name="dbdatareader-class-in-the-siebel-adapter"></a>Siebel 配接器在 DbDataReader 類別
[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供`DbDataReader`運用 XML 資料讀取器。 這能夠取用者的 Siebel 資料來源讀取順向資料流的資料列。  

## <a name="supported-properties"></a>支援的屬性  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援下列`DbDataReader`屬性。  

|[屬性]|取得或設定|描述|  
|----------|--------------|-----------------|  
|**HasRows**|Get|這個屬性不支援，並將會擲回例外狀況，如果存取。|  
|**IsClosed**|Get|取得值，指出是否`DbDataReader`已關閉。|  
|**RecordsAffected**|Get|取得值，指出是否`DbDataReader`包含一或多個資料列。|  
|**Item(Int32)**|Get|取得物件的執行個體為指定的資料行的值。 叫用這個索引子時，請使用所需的資料行的序數數字。|  
|**Item(String)**|Get|取得物件的執行個體為指定的資料行的值。 叫用這個索引子時，請使用所需的資料行名稱。|  

## <a name="supported-methods"></a>支援的方法  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援下列`DbDataReader`方法。  


|        [屬性]        |                                                                                                                                                                                                                            描述                                                                                                                                                                                                                             |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **GetSchemaTable** | 傳回 `DataTable`，描述 `DbDataReader` 的資料行中繼資料。 所支援的結構描述資料行屬性[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]是：<br /><br /> -M<br />-ColumnOrdinal<br />.NET 資料類型<br />長度<br />有效位數 （如果有的話）<br />-調整 （如果有的話）<br />-AllowDBNull<br />-LocalName<br />擴充的 LocalName<br />命名空間 |
|   **GetString**    |                                                                                                                                                                                                 從指定的資料行取得 `String` 執行個體形式的值。                                                                                                                                                                                                 |
|    **GetValue**    |                                                                                                                                                                                                 從指定的資料行取得 `String` 執行個體形式的值。                                                                                                                                                                                                 |
|    **isDbNull**    |                                                                                                                                                                                       取得值，指出資料行是否包含不存在或遺漏的值。                                                                                                                                                                                       |
|   **NextResult**   |                                                                                                                                                           Siebel 資料提供者一律會傳回單一結果集;因此這個呼叫完全耗盡的目前結果集傳回前**false**。                                                                                                                                                           |
|      **讀取**      |                                                                                                                                                         讓讀取器前進到結果集中的下一個記錄。  它會傳回 **，則為 true**如果成功，並**false**如果讀取器左邊有沒有更多的記錄。                                                                                                                                                         |
|     **關閉**      |                                                                                                         關閉 `DbDataReader` 物件。 **注意：** 當您完成使用`DbDataReader`物件時，您必須先關閉，才能釋出 Siebel COM 程式庫物件。 否則，用戶端應用程式的記憶體和控制代碼使用上揚。                                                                                                          |

## <a name="see-also"></a>另請參閱  
 [使用 Siebel 配接器擴充 ADO.NET 介面](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)