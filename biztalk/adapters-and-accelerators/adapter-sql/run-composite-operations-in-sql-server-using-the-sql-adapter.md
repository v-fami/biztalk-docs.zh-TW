---
title: 使用 SQL 配接器的 SQL Server 中執行複合作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 906c6352-44f3-4624-9e32-aea3fbb7510d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5acf0eca210bd163c0d74e7d8d873ec6009d40a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999279"
---
# <a name="run-composite-operations-in-sql-server--using-the-sql-adapter"></a>使用 SQL 配接器的 SQL Server 中執行複合作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓配接器用戶端執行複合作業上的 SQL Server 資料庫。 複合作業可以包含任意數目的下列作業，並依照任何順序：  
  
- 資料表和檢視表上插入、 更新和刪除作業。  
  
- 顯示為配接器中的作業的預存程序。  
  
  複合作業中的作業*必須*目標資料表和檢視表，只能在單一資料庫中的。  
  
  如需詳細資訊：  
  
- 如何執行中的複合作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[SQL Server 使用 BizTalk Server 上執行複合操作](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)。  
  
- 訊息複合作業的結構描述，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。  
  
> [!IMPORTANT]
>  有"n"中的作業數目的複合運算傳回的結果設定然後 「 n + 1"的連線次數需要執行複合作業。 因此，您必須確定指定的值**MaxConnectionPoolSize**屬性繫結為 n + 1 或更新版本。 如需詳細資訊**MaxConnectionPoolSize**繫結屬性，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)