---
title: Siebel 配接器中的 SiebelCommand 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelCommand
- Data Provider for Siebel, SiebelCommand
- SiebelCommand, supported methods and properties
ms.assetid: 7cba0e47-634b-4878-b480-80fbcbbf5c90
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d268e9a1d5954d703d392070a53c84bd9cee0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222358"
---
# <a name="siebelcommand-class-in-the-siebel-adapter"></a>Siebel 配接器中 SiebelCommand 類別
建立與 Siebel 系統的連線後[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]剖析 Siebel 命令字串和 ADO.NET 用戶端所提供的命令參數，並將命令對應到 WCF 要求訊息。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]然後會傳送要求給[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]並取得回應 XML 以及從配接器的本文內容。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]接著會使用`XMLDataReader`來擷取關聯式資料的 XML 主體。  
  
 使用的執行個體`Microsoft.Data.SiebelClient.SiebelClientFactory`，用戶端程式可以取得的執行個體`System.Data.Common.DbCommand`類別以建構 Siebel 命令。  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbCommand command = factory.CreateCommand();  
```  
  
 或者，可以使用下列方法，來建立命令：  
  
```  
//Here connection is an instance of SiebelConnection  
SiebelCommand cmd = (SiebelCommand) connection.CreateCommand();  
cmd.CommandText = "SELECT [Name] as MyName, [City], [Country]  from Account.Account WHERE Name LIKE '3Com*' OPTION 'ViewMode 1'";  
```  
  
 `SiebelCommand`類別繼承自`DbCommand`。  命名空間中存在`Microsoft.Data.SiebelClient`。  
  
## <a name="supported-properties"></a>支援的屬性  
 **SiebelCommand**類別支援下列`DbCommand`*保護*屬性：  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**DbConnection**|取得和設定|這會包含基礎`DbConnection`從這個執行個體`DbCommand`取得執行個體。|  
|**DbParameterCollection**|Get|取得集合`DbParameter`物件。|  
  
 `SiebelCommand`也支援下列`DbCommand`*公用*屬性：  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**CommandText**|取得和設定|這包含 ADO.NET 用戶端想要執行的 SQL 陳述式。|  
|**CommandType**|取得和設定|只有`CommandType.Text`支援。|  
|**連接**|取得和設定|這會使用`DbConnection`成員。|  
|**參數**|Get|這會使用`DbParameterCollection`成員。|  
  
> [!IMPORTANT]
>  `SiebelCommand`類別會忽略`CommandTimeout`， `DesignTimeVisible`，和`DbTransaction`屬性。  
  
## <a name="supported-methods"></a>支援的方法  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援下列`DbCommand`*保護*方法：  
  
|名稱|Description|  
|----------|-----------------|  
|**CreateDbParameter**|建立新`DbParameter`執行個體。|  
|**ExecuteDbDataReader**|這會執行 SELECT 和 EXEC 命令並傳回`DbDataReader`。|  
  
 `SiebelCommand`也支援下列`DbCommand`*公用*方法：  
  
|名稱|Description|  
|----------|-----------------|  
|**CreateParameter**|建立新`DbParameter`透過執行個體`CreateDbParameter().`|  
|**ExecuteReader**|執行`CommandText`針對`Connection`並傳回`DbDataReader`透過`ExecuteDbDataReader()`。|  
|**準備**|這會剖析`CommandText`並建立 SQL 命令剖析樹狀目錄。|  
  
## <a name="see-also"></a>另請參閱  
 [Siebel 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)