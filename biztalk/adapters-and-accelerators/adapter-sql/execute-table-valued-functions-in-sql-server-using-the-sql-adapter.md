---
title: "執行 SQL Server 使用 SQL 配接器中的資料表值函式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fb8c81c-9384-4eba-b0a0-baed1782245b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69877f214a2a4b700de22ec043094510707114d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="execute-table-valued-functions-in-sql-server-using-the-sql-adapter"></a>執行 SQL Server 使用 SQL 配接器中的資料表值函式
SQL Server 中的 TRANSACT-SQL 和 CLR 資料表值函式中的作業當成[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。 中的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]值在 SQL Server 中的函式的資料表名稱一樣。  
  
 資料表值函式中的所有參數會都公開在對應的作業。 如果您沒有指定之輸入的參數的資料表值函式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]內部叫用函數的 DEFAULT 關鍵字。 這表示使用預設值，指定定義函式時執行資料表值函式。  
  
 如需詳細資訊：  
  
-   使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 BizTalk Server 叫用 SQL Server 中的資料表值函式，請參閱[Invoking Table-Valued 函式中使用 BizTalk server 的 SQL Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)。  
  
-   訊息結構和資料表值函式的 SOAP 動作，請參閱[訊息結構描述的程序和函式](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)