---
title: ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar Operations2 如訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f8cb98-8da8-40c1-bf87-4aad5a24bba2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ede2d471ce935d11286c49cc7cfb53c0e7ea9d92
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001423"
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開根層級的 SQL Server 中執行任何任意的 SQL 陳述式的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 輸出作業。  
  
 如需詳細資訊：  
  
- 這些作業，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
- 執行這些作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構  
 在這些作業訊息會遵循要求-回應訊息交換模式，以及下表顯示這些要求和回應訊息的結構。  
  
|作業|XML 訊息|描述|  
|---------------|-----------------|-----------------|  
|ExecuteNonQuery 要求|`<ExecuteNonQuery xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">    <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query>  </ExecuteNonQuery>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteNonQuery 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult> </ExecuteNonQueryResponse>`|UPDATE、 INSERT 和 DELETE 陳述式中，`[value]`代表受 PL/SQL 陳述式中的資料列的數目*ExecuteNonQuery 要求*訊息。 對於所有其他類型的陳述式，`[value]`為-1。|  
|ExecuteReader 要求|`<ExecuteReader xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteReader>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteReader 回應|`<?xml version="1.0" encoding="utf-8" ?>  <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteReaderResult>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </ExecuteReaderResult> </ExecuteReaderResponse>`|結果集是回應訊息的執行中的 PL/SQL 陳述式*ExecuteReader 要求*訊息，而且會當做資料集的陣列傳回。 資料集的相關資訊，請參閱 < 資料集類別 >，網址[ http://go.microsoft.com/fwlink/?LinkID=196853 ](http://go.microsoft.com/fwlink/?LinkID=196853)。|  
|ExecuteScalar 要求|`<ExecuteScalar xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteScalar>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteScalar 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|`[value]`代表 PL/SQL 陳述式中所傳回的結果集中的第一個資料列的第一個資料行中的值*ExecuteScalar 要求*訊息。|  
  
 [PL/SQL 陳述式] = 整個要執行的 PL/SQL 陳述式。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)