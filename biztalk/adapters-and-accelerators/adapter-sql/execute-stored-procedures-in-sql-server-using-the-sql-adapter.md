---
title: 使用 SQL 配接器的 SQL Server 中執行預存程序 |Microsoft Docs
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
ms.openlocfilehash: c6515baa313fc6b68c62556ad5b5883500cfde8a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021551"
---
# <a name="execute-stored-procedures-in-sql-server-using-the-sql-adapter"></a>使用 SQL 配接器的 SQL Server 中執行預存程序
TRANSACT-SQL 和 SQL Server 中的 CLR 預存程序會顯示為中的作業[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]底下**程序**時使用的節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 所公開的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL Server 中的預存程序的名稱相同。 預存程序中的所有參數會都公開在對應的作業。 OUT 參數會包含預存程序的傳回值。 預存程序的結果集是資料集的陣列。 如需有關資料集的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=196853 ](http://go.microsoft.com/fwlink/?LinkId=196853)。 目標物件的結構描述資訊是在執行階段取得回應訊息的一部分。  

 不過，如果您想要取得在設計階段的目標物件的結構描述資訊時，您必須產生結構描述下的程序**Strongly-Typed 程序**中的節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請注意，相同的預存程序會在呈現**程序**並**Strongly-Typed 程序**節點。 預存程序傳回值為強型別，而不只是資料集的陣列。 因為在設計階段使用的結構描述資訊，您可以使用它的預存程序的結構描述對應到另一個結構描述不同的作業。 比方說，您可以對應至資料庫資料表上的插入作業所產生的結構描述的強型別 」 程序所產生的結構描述。  

> [!NOTE]
>  您無法檢視的強類型的預存程序在設計階段的結構描述資訊，如果：  
> 
> - 您正在使用資料指標，也就是另一個預存程序，傳回值做為輸入參數為強類型的預存程序。  
>   -   它是 CLR 預存程序，以在資料表上的某些作業。  

## <a name="support-for-stored-procedures-with-for-xml-clause"></a>搭配 FOR XML 子句的預存程序的支援  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也可讓您執行具有 FOR XML 子句的 SELECT 陳述式的預存程序。 FOR XML 子句用於 SELECT 陳述式中，以 XML 形式傳回結果，而不是資料列集。 如需有關 FOR XML 子句的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=131402 ](http://go.microsoft.com/fwlink/?LinkId=131402)。  

> [!NOTE]
>  「 原生 」[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]支援僅的預存程序傳回的 XML，也就是有 FOR XML 子句的 SELECT 陳述式中。 搭配 FOR XML 子句的預存程序的支援，您可以執行這些預存程序，使用以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]而不需要對預存程序定義中的任何變更。  

## <a name="support-for-stored-procedures-with-temporary-tables"></a>使用暫存資料表的預存程序的支援  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓您產生包含其定義中的暫存資料表的預存程序的中繼資料。 不過，這類預存程序則必須產生中繼資料選取預存程序，只能從**程序**節點，同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 配接器不支援從在這類預存程序產生的中繼資料**Strongly-Typed 程序**節點。  

## <a name="support-for-result-sets-containing-columns-without-names-or-with-same-names"></a>支援結果集包含資料行沒有名稱或相同的名稱  
 下表列出了[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]處理而不需要名稱和預存程序和強型別的預存程序之結果集內的相同名稱的資料行。  


|    結果集包含...     |                                                                                                                                                       預存程序                                                                                                                                                       |                                                                                                           強型別的預存程序                                                                                                            |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **沒有名稱的資料行**  | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以下列方式產生資料行的名稱： 沒有資料行產生唯一識別碼 (GUID)"-"（連字號），然後 GUID 字串前面加上"C"因為產生的 GUID 可能會以數字開頭，但 XML 標記名稱不能和。 |                                [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會產生下列資料行名稱:"UnNamedColumn [column_index] 」，從 '0' column_index 開始的位置。                                |
| **具有相同名稱的資料行** |                                                                                第一個以外的資料行的名稱再加上"*"（底線） 後面接著隨機的 GUID，而不"-"（連字號）。例如:"\\*[GUID]"。                                                                                | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]結果集中不支援具有相同名稱的資料行，而且會擲回例外狀況。 **重要事項：** 您必須確定在結果集中的資料行名稱有唯一的名稱。 |

> [!NOTE]
>  一般情況下，建議結果中的所有資料行設定預存程序和強型別的預存程序必須名稱，並且具有唯一的名稱。  

 如需詳細資訊：  

-   如何執行預存程序，請參閱[使用 BizTalk Server 的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)。  

-   執行具有 FOR XML 子句的預存程序，請參閱[執行具有 FOR XML 子句中使用 BizTalk Server 的 SQL Server 中的預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)。  

-   訊息的預存程序的結構描述，請參閱 <<c0> [ 程序和函式的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)。  

## <a name="see-also"></a>另請參閱  
 [連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)