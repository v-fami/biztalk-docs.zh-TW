---
title: 執行預存程序中使用 SQL 配接器的 SQL Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 245626a7-f546-4aca-90df-c0579139a872
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65a475d8de1fc30df2e06923ad14bcba0897159e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224054"
---
# <a name="execute-stored-procedures-in-sql-server-using-the-sql-adapter"></a>使用 SQL 配接器的 SQL Server 中執行預存程序
TRANSACT-SQL 和 SQL Server 中的 CLR 預存程序當成作業[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]下**程序**時使用的節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 所公開的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]SQL Server 中的預存程序的名稱相同。 預存程序中的所有參數會都公開在對應的作業。 OUT 參數會包含預存程序的傳回值。 預存程序的結果集是資料集的陣列。 如需有關資料集的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=196853](http://go.microsoft.com/fwlink/?LinkId=196853)。 目標物件的結構描述資訊會在執行階段取得做為回應訊息的一部分。  
  
 不過，如果您想要取得在設計階段目標物件的結構描述資訊，您必須產生結構描述底下的程序**Strongly-Typed 程序**節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請注意，相同的預存程序便會顯示在**程序**和**Strongly-Typed 程序**節點。 預存程序的傳回值是強型別，並不只是資料集的陣列。 因為在設計階段使用的結構描述資訊，您可以使用它的預存程序的結構描述對應到另一個結構描述的不同作業。 比方說，您可以對應至資料庫資料表的插入作業所產生的結構描述的強型別程序產生的結構描述。  
  
> [!NOTE]
>  您無法檢視的強類型的預存程序在設計階段的結構描述資訊：  
>   
>  -   您正在使用資料指標，也就是另一個預存程序，傳回值做為強型別的預存程序的輸入參數。  
> -   它是 CLR 預存程序，以執行某些作業在資料表上。  
  
## <a name="support-for-stored-procedures-with-for-xml-clause"></a>搭配 FOR XML 子句的預存程序支援  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也可讓您執行具有 FOR XML 子句的 SELECT 陳述式的預存程序。 FOR XML 子句用於 SELECT 陳述式中傳回結果為 XML，而不是資料列集。 如需 FOR XML 子句的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=131402](http://go.microsoft.com/fwlink/?LinkId=131402)。  
  
> [!NOTE]
>  「 原生 」[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]支援僅的預存程序會傳回 XML，亦即，具有 FOR XML 子句 SELECT 陳述式中。 搭配 FOR XML 子句的預存程序的支援，您可以執行這些預存程序，使用 WCF 型[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不到預存程序定義中進行任何變更。  
  
## <a name="support-for-stored-procedures-with-temporary-tables"></a>與暫存資料表的預存程序支援  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓您產生包含其定義中的暫存資料表的預存程序的中繼資料。 不過，這類預存程序則必須產生中繼資料選取預存程序，只能從**程序**節點，同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 配接器不支援從下這類預存程序產生的中繼資料**Strongly-Typed 程序**節點。  
  
## <a name="support-for-result-sets-containing-columns-without-names-or-with-same-names"></a>支援結果集包含資料行沒有名稱或相同的名稱  
 下表列出如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]處理沒有名稱和預存程序和強型別的預存程序之結果集內的相同名稱的資料行。  
  
|結果集包含...|預存程序|強型別的預存程序|  
|--------------------------|----------------------|--------------------------------------|  
|**沒有名稱的資料行**|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會以下列方式產生資料行的名稱： 沒有資料行產生唯一識別碼 (GUID)"-"（連字號），然後 GUID 字串前面加上"C"，因為產生的 GUID 可能會以數字開頭，但 XML 標記名稱不能和。|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會產生下列資料行名稱:"UnNamedColumn [column_index]"，從 '0' column_index 開始的位置。|  
|**具有相同名稱的資料行**|第一個以外的資料行名稱會附加"_"（底線） 後面跟著隨機 GUID 不含"-"（連字號）。 例如:"\_[GUID]"。|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援具有相同名稱的資料行中的結果集，並擲回例外狀況。 **重要事項：** 您必須確定結果集中的資料行名稱有唯一的名稱。|  
  
> [!NOTE]
>  一般情況下，建議在結果中的所有資料行設定預存程序和強型別的預存程序必須命名，並具有唯一的名稱。  
  
 如需詳細資訊：  
  
-   如何執行預存程序，請參閱[使用 BizTalk Server 的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)。  
  
-   執行具有 FOR XML 子句的預存程序，請參閱[執行預存程序在使用 BizTalk Server 的 SQL Server 中具有 FOR XML 子句](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)。  
  
-   訊息結構描述的預存程序，請參閱[訊息結構描述的程序和函式](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接至 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)