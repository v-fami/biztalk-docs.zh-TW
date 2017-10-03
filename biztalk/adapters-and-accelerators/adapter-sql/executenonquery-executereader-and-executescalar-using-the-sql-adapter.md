---
title: "執行 ExecuteNonQuery、 ExecuteReader 和使用 SQL 配接器的 ExecuteScalar 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fda0544-a028-4a95-aae6-1f6a90764c5d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f68f4378a4d89d2a997f5a78a524e4f6bfca2c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a>執行 ExecuteNonQuery、 ExecuteReader 和使用 SQL 配接器的 ExecuteScalar 作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開根層級的下列作業：  
  
-   **ExecuteNonQuery**： 使用這個作業來執行 SQL Server 中的任何任意的 SQL 陳述式，如果不想讓任何結果集傳回。 您可以使用這項作業來建立資料庫物件或變更資料庫中的資料，藉由執行更新、 插入或刪除陳述式。 這項作業的傳回值屬於 Int32 資料型別，以及：  
  
    -   對於 INSERT、 UPDATE 和 DELETE 陳述式，傳回值會是 SQL 陳述式所影響的資料列數目。  
  
    -   對於所有其他陳述式類型，則傳回值是**-1**。  
  
-   **ExecuteReader**： 使用 SQL Server 中執行任何任意的 SQL 陳述式，如果您想將結果集傳回，如果有的話，做為陣列的資料集的這項作業。 資料集的相關資訊，請參閱 < 資料集類別 >，網址[http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853)。  
  
-   **ExecuteScalar**： 執行傳回單一值的 SQL Server 中的任何任意的 SQL 陳述式中使用這項作業。 這項作業只能在 SQL 陳述式所傳回的結果集第一個資料列的第一個資料行中傳回的值。  
  
    > [!NOTE]
    >  ExecuteScalar 優於 ExecuteReader 是較小 ExecuteReader 作業所傳回比較 ExecuteScalar 作業的回應訊息裝載。 因此，如果您需要傳回只有一個值，您應該使用 ExecuteScalar 而不是 ExecuteReader。  
  
 您可以使用 ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar 作業來執行多個 SQL 陳述式。  
  
 如需有關執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk server 的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)