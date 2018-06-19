---
title: ExecuteNonQuery、 ExecuteReader，和 ExecuteScalar Operations2 訊息結構描述 |Microsoft 文件
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
ms.openlocfilehash: 0aaef682ad0528e8d22e043da94dc31e4f723f24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222470"
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開根層級執行 SQL Server 中的任何任意的 SQL 陳述式的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 輸出作業。  
  
 如需詳細資訊：  
  
-   這些作業，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
-   執行這些作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk Server 的 SQL 中的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader，和 ExecuteScalar 作業的訊息結構  
 這些作業中的訊息會遵循要求-回應訊息交換模式，以及下表顯示這些要求和回應訊息的結構。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|ExecuteNonQuery 要求|`<ExecuteNonQuery xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">    <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query>  </ExecuteNonQuery>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteNonQuery 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult> </ExecuteNonQueryResponse>`|對於 INSERT、 UPDATE 和 DELETE 陳述式，`[value]`代表受 PL/SQL 陳述式中的資料列數目*ExecuteNonQuery 要求*訊息。 對於所有其他類型的陳述式，`[value]`為-1。|  
|ExecuteReader 要求|`<ExecuteReader xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteReader>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteReader 回應|`<?xml version="1.0" encoding="utf-8" ?>  <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteReaderResult>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </ExecuteReaderResult> </ExecuteReaderResponse>`|結果集是在執行的 PL/SQL 陳述式的回應訊息*ExecuteReader 要求*訊息，而且會當做資料集的陣列傳回。 資料集的相關資訊，請參閱 < 資料集類別 >，網址[http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853)。|  
|ExecuteScalar 要求|`<ExecuteScalar xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteScalar>`|內`<Query>`標記，您可以指定多個以分號分隔的 PL/SQL 陳述式。|  
|ExecuteScalar 回應|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|`[value]`表示中的 PL/SQL 陳述式所傳回的結果集第一個資料列的第一個資料行中值*ExecuteScalar 要求*訊息。|  
  
 [PL/SQL 陳述式] = 整個執行的 PL/SQL 陳述式。  
  
## <a name="message-action-for-the-executenonquery-executereader-and-executescalar-operations"></a>ExecuteNonQuery、 ExecuteReader，和 ExecuteScalar 作業的訊息動作  
 下表顯示 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業所使用的訊息動作。  
  
|作業|動作|  
|---------------|------------|  
|ExecuteNonQuery 要求|GenericOp/ExecuteNonQuery|  
|ExecuteNonQuery 回應|GenericOp/ExecuteNonQuery 回應|  
|ExecuteReader 要求|GenericOp/ExecuteReader|  
|ExecuteReader 回應|GenericOp/ExecuteReader 回應|  
|ExecuteScalar 要求|GenericOp/ExecuteScalar|  
|ExecuteScalar 回應|GenericOp/ExecuteScalar 回應|  
  
## <a name="see-also"></a>另請參閱  
 [訊息與 BizTalk adapter for SQL Server 的訊息結構描述](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)