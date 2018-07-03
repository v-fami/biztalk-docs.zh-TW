---
title: 執行 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業使用 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fda0544-a028-4a95-aae6-1f6a90764c5d
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7374a0852c4f6689a0c092e5ddf0b11c038d6e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990319"
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a>執行 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業使用 SQL 配接器
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會公開下列作業的根層級：  
  
- **ExecuteNonQuery**： 使用此作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果您不想設定要傳回任何結果。 您可以使用這項作業建立資料庫物件，或變更資料庫中的資料執行 INSERT、 UPDATE 或 DELETE 陳述式。 這項作業的傳回值是 Int32 資料型別，以及：  
  
  -   UPDATE、 INSERT 和 DELETE 陳述式，傳回的值會是 SQL 陳述式所影響的資料列數目。  
  
  -   對於所有其他類型的陳述式，則傳回值是 **-1**。  
  
- **ExecuteReader**： 使用此作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果您想要的結果集傳回，如果有的話，為資料集的陣列。 資料集的相關資訊，請參閱 < 資料集類別 >，網址[ http://go.microsoft.com/fwlink/?LinkID=196853 ](http://go.microsoft.com/fwlink/?LinkID=196853)。  
  
- **ExecuteScalar**： 執行傳回單一值的 SQL Server 中的任何任意的 SQL 陳述式中使用這項作業。 這項作業只能在 SQL 陳述式所傳回的結果集第一個資料列的第一個資料行中傳回的值。  
  
  > [!NOTE]
  >  ExecuteScalar 優於 ExecuteReader 是小得多 ExecuteReader 作業所傳回比較 ExecuteScalar 作業的回應訊息承載。 因此，如果您需要只能有一個要傳回的值時，您應該使用 ExecuteScalar 代替 ExecuteReader。  
  
  您可以使用 ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar 作業執行多個 SQL 陳述式。  
  
  如需有關執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業所使用的 BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)