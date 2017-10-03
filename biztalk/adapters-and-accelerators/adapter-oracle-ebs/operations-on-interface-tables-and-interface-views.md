---
title: "介面資料表和檢視介面上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c7f3453-848f-42df-b092-725d9ff466cf
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ec9b7c5f952b6be60a3c3463e6ea0682faa9d4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-interface-tables-and-interface-views"></a>介面在資料表和檢視介面上的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現一組標準的作業 （Select、 Insert、 Update 和 Delete 每個介面資料表） 和 Oracle E-business Suite 中的每個介面檢視的選取作業。 藉由使用這些作業，您可以執行 SELECT、 INSERT、 UPDATE，並刪除目標介面資料表上的 WHERE 子句所限定的陳述式和 SELECT 陳述式 WHERE 子句的目標介面檢視上所限定。 這些作業也稱為資料操作語言 (DML) 作業。  
  
> [!IMPORTANT]
>  您可以執行介面資料表和檢視介面上的作業之前，您必須設定在這些成品的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 如需應用程式內容和設定方式的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

## <a name="supported-dml-operations"></a>支援的 DML 作業  
 下表顯示對 DML 作業的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援：  
  
|作業|Description|  
|---------------|-----------------|  
|Select|選取上執行運算目標介面資料表或介面檢視根據提供的資料行名稱和指定 SQL WHERE 子句的篩選條件字串清單。<br /><br /> 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。|  
|Insert|執行插入作業的目標介面資料表上。 Insert 作業支援多個記錄插入至目標介面資料表根據提供的記錄組。<br /><br /> 插入作業的傳回值會是插入的資料列數目。<br /><br /> **InlineValue**<br /><br /> 在插入作業中的所有簡單資料記錄，您可以選擇指定呼叫的選擇性屬性的值來覆寫記錄的值**InlineValue**。 InlineValue 屬性可以用來計算的值插入介面資料表，例如擴展成日期資料行的主索引鍵的資料行使用順序，或插入 （使用 SYSDATE） 的系統日期。 例如，在下列的 INSERT 陳述式：<br /><br /> `<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR_ARCHIVE_PURGE_INTERIM">   <RECORDSET>     <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">       <TRNS_DATE InlineValue="sysdate">2008-06-21T15:52:19</TRNS_DATE>       <EMPNAME>John</EMPNAME>     </InsertRecord>   </RECORDSET>   </Insert>`<br /><br /> 即使"2008年-06-21T15:52:19"TRNS_DATE，值的指定值為**InlineValue**屬性，「 SYSDATE，"（系統日期） 將會插入至目標介面資料表。<br /><br /> 同時使用 InlineValue 屬性：<br /><br /> 為避免 InlineValue 屬性使用常數值。 例如，在 INSERT 陳述式，如果您指定`<EMPNAME InlineValue="John"/>`則會導致錯誤。 這是因為 InlineValue 屬性的值會傳遞做為的是 Oracle 中，並在此情況下*John*傳遞至 Oracle E-business Suite，不是預期的值 (預期的值是*'John'*)。 您必須使用單引號員工名稱。 例如： `<EMPNAME InlineValue="’John’"/>`。<br /><br /> -如果您想要用於 InlineValue 屬性中的 select 查詢，您必須以括號括住 SELECT 陳述式，並也請確定選取的查詢會擷取單一記錄。 例如： `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`。<br /><br /> **注意：**如果元素標示為 NOT NULL Oracle E-business Suite 中，您就必須指定該元素的值，即使您已指定內嵌值。 無法執行此動作將會導致結構描述驗證失敗。|  
|Update|執行目標介面資料表上的更新作業。 指定 SQL WHERE 子句的篩選字串會指定要更新的記錄。 更新的值會指定範本記錄。<br /><br /> 更新作業的傳回值是更新的資料列數目。|  
|DELETE|執行 SQL WHERE 子句的篩選條件字串中指定為基礎的介面目標資料表上的刪除作業。<br /><br /> 刪除作業的傳回值是刪除的資料列數目。|  

## <a name="important-details"></a>重要的詳細資料  
  -   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現相同的一組標準的作業 （Select、 Insert、 Update 和 Delete 每個資料表） 和為基礎的 Oracle 資料庫中的每個檢視選取的作業。 上述的 DML 作業也是有效的基礎 Oracle 資料庫資料表和檢視。  

 -   您不需要設定要在 Oracle 資料庫資料表和檢視表上執行作業的應用程式內容。 不過，對於自訂 Oracle E-business Suite 應用程式，使用者可能會或可能無法登錄為介面資料表的基底資料庫資料表。 如果尚未註冊資料庫資料表與介面的資料表，它位在**資料表**中的子節點**成品根據檢視**節點或**結構描述基礎檢視**節點在設計階段時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
    這些資料表是 Oracle E-business 應用程式相關聯。 因此對於這些資料表上的任何作業，您必須設定應用程式內容。 請參閱設定應用程式內容[輸入連結描述](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)