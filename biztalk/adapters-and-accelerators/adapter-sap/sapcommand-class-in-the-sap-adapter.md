---
title: SAP 配接器在 SAPCommand 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPCommand, supported methods, classes, and constructors
ms.assetid: 55ad334e-1cc3-47c1-8764-be0f4e93f8b5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee083ed5afea06a5d350e9d73a9103adf157d8b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapcommand-class-in-the-sap-adapter"></a>SAP 配接器在 SAPCommand 類別
此命令會表示 SQL 查詢，以在 SAP 後端上執行。 [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]目前支援 SELECT 和 EXEC 陳述式只。 SELECT 陳述式啟用從單一的 SAP 資料表擷取資料和 EXEC 陳述式可讓使用者在 SAP 伺服器上執行 Rfc。  
  
 這衍生自**System.Data.Common.DbCommand**。  
  
## <a name="supported-properties"></a>支援的屬性  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**CommandText**|取得和設定|支援 SELECT 和 EXEC 陳述式。 如需 SELECT 陳述式的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。 如需在 EXEC 陳述式的詳細資訊，請參閱[sap EXEC 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md)。|  
|**CommandTimeout**|取得和設定|不支援。|  
|**CommandType**|取得和設定|支援 CommandType.Text。|  
|**連接**|取得和設定|此命令將執行基礎 SAP 連接。|  
|**DesignTimeVisible**|Get|不支援。 傳回 false。|  
|**參數**|Get|此命令使用的參數集合。|  
|**UpdatedRowSource**|-|不支援。|  
  
## <a name="supported-methods"></a>支援的方法  
  
|名稱|Description|  
|----------|-----------------|  
|**Cancel （)**|擷取批次中的資料時，取消命令。 擷取批次後，會發生取消。|  
|**Executenonquery （)**|不會輸出所有的 DataReader。 不過，值將可透過繫結參數。|  
|**Executereader （)**|輸出與所有匯出的複雜型別和參數資料表的 DataReader 為結果集。 您也可以透過繫結參數取得的值。|  
|**ExecuteReader(CommandBehavior)**|CommandBehaviors 支援如下：<br /><br /> 預設<br />-SingleResult<br />-SingleRow<br />-SchemaOnly|  
|**Executescalar （)**|對應至：<br /><br /> -CommandBehaviour.SingleRow SELECT 陳述式。<br />-CommandBehaviour.SingleResult EXEC 陳述式。|  
|**Prepare()**|-EXEC 支援繫結參數。<br />-選取支援繫結參數。|  
  
## <a name="supported-constructors"></a>支援的建構函式  
  
|名稱|Description|  
|----------|-----------------|  
|**SAPCommand()**|建立 SAPCommand 的新執行個體。|  
|**SAPCommand(string)**|SAPCommand 與命令文字。|  
|**SAPCommand （字串、 SAPConnection）**|此命令將執行的命令文字與 SAPConnection 物件使用 SAPCommand|  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)