---
title: ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar Operations1 如訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8aa5fdb2-1e7f-4a34-a1e5-c16d8fb477d5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7078fed7a007eca4dfb3eb5608eb6e688bb74a45
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011967"
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開執行 Oracle E-business Suite 中的 任何任意的 SQL 陳述式或 PL/SQL 封鎖根層級的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 輸出作業。  
  
 如需詳細資訊：  
  
- 這些作業，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
- 執行這些作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構  
 在這些作業訊息會遵循要求-回應訊息交換模式，以及下表顯示這些要求和回應訊息的結構。  
  
> [!NOTE]
>  表格後，請參閱實體描述。  
  
|作業|XML 訊息|  
|---------------|-----------------|  
|ExecuteNonQuery 要求|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQuery xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query>   <OutputRefCursorNames>     <string>[stringvalue1]</string>     <string>[stringvalue2]</string>     …   </OutputRefCursorNames> </ExecuteNonQuery>`|  
|ExecuteNonQuery 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult>   <OutputRefCursors>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </OutputRefCursors> </ExecuteNonQueryResponse>`|  
|ExecuteReader 要求|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteReader>`|  
|ExecuteReader 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteReaderResult>     <Any>[value]</Any>     <Any>[value]</Any>       …   </ExecuteReaderResult> </ExecuteReaderResponse>`|  
|ExecuteScalar 要求|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalar xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteScalar>`|  
|ExecuteScalar 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|  
  
 實體描述：  
  
 [PL/SQL 區塊] = 整個 PL/SQL 區塊執行。  
  
 [stringvalue1] = 的字串陣列中的值。  
  
## <a name="message-action-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息動作  
 下表顯示使用 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息動作。  
  
|作業|動作|  
|---------------|------------|  
|ExecuteNonQuery 要求|GenericOp/ExecuteNonQuery|  
|ExecuteNonQuery 回應|GenericOp/ExecuteNonQuery/回應|  
|ExecuteReader 要求|GenericOp/ExecuteReader|  
|ExecuteReader 回應|GenericOp/ExecuteReader/回應|  
|ExecuteScalar 要求|GenericOp/ExecuteScalar|  
|ExecuteScalar 回應|GenericOp/ExecuteScalar/回應|