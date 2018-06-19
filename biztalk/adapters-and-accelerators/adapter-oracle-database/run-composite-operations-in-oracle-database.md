---
title: Oracle 資料庫中執行複合操作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b877d8e3-2016-40e8-888f-6b768021d6b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5595823fab4f25948e3d88db759ae525f62130
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215118"
---
# <a name="run-composite-operations-in-oracle-database"></a>Oracle 資料庫中執行複合操作
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行複合操作，可包含任意數目的下列作業，並以任何順序：  
  
-   Select、 Insert、 Update 和 Delete 資料表和檢視表上的作業。  
  
-   預存程序、 函數和程序或當成配接器中的作業之封裝內的函式。  
  
 資料表和檢視表中的相同資料庫或不同的資料庫，可鎖定目標的複合運算中的作業。 不過，資料無法共用，或重複用在不同的作業，在複合作業。 比方說，在複合作業中，選取作業的結果集不能做為輸入參數的預存程序。  
  
 執行複合作業中的每個作業使用個別的連接。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目和取得執行的作業，然後釋出連線。 不過，複合作業中的作業會傳回結果集，如果連接是之後才釋放使用訊息。  
  
> [!IMPORTANT]
>  如果您執行複合操作時遇到逾時問題然後可能是因為連線的數目小於的複合運算涉及作業數目：  
>   
>  -   預存程序包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 做為 OUT 或 IN OUT 參數。  
> -   選取作業。  
>   
>  若要解決此問題，您必須確定是否有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。 如需有關**MinPoolSize**繫結屬性，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
 如需詳細資訊：  
  
-   如何執行複合操作中的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。  
  
-   訊息結構描述的複合作業，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)