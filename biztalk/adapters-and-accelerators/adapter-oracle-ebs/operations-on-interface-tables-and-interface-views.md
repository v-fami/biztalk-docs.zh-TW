---
title: 介面資料表和介面檢視上的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c7f3453-848f-42df-b092-725d9ff466cf
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffcf9b26f745112b4748c0020fd761f233caedd8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992031"
---
# <a name="operations-on-interface-tables-and-interface-views"></a>在介面資料表和介面檢視上的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現一組標準的作業 （Select、 Insert、 Update 和 Delete 每個介面資料表） 和 Oracle E-business Suite 中的每個介面檢視的選取作業。 藉由使用這些作業，您可以執行 SELECT、 INSERT、 UPDATE，並刪除目標介面資料表上的 WHERE 子句所限定的陳述式和限定目標介面檢視上的 WHERE 子句的 SELECT 陳述式。 這些作業也稱為資料操作語言 (DML) 作業。  
  
> [!IMPORTANT]
>  您可以執行在介面資料表和介面檢視上的作業之前，您必須設定應用程式內容中的這些成品[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定和成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 如需有關應用程式內容，以及如何將它設定的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

## <a name="supported-dml-operations"></a>支援的 DML 作業  
 下表顯示 DML 作業，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援：  
  
|作業|描述|  
|---------------|-----------------|  
|Select|執行選取的運算目標介面資料表或介面檢視上提供的資料行名稱和指定 SQL WHERE 子句的篩選條件字串清單為基礎。<br /><br /> 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。|  
|Insert|執行插入作業的目標介面資料表上。 Insert 作業支援多個記錄插入至目標介面資料表，根據提供的記錄集。<br /><br /> 插入作業的傳回值會是插入資料列數目。<br /><br /> **InlineValue**<br /><br /> 插入作業中的所有簡單資料記錄，您可以選擇指定呼叫的選擇性屬性的值來覆寫記錄的值**InlineValue**。 InlineValue 屬性可用來插入介面資料表，例如 [日期] 資料行中填入的主索引鍵的資料行使用順序，或插入 （使用 SYSDATE） 的系統日期的計算的值。 例如，在下列的 INSERT 陳述式：<br /><br /> `<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR_ARCHIVE_PURGE_INTERIM">   <RECORDSET>     <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">       <TRNS_DATE InlineValue="sysdate">2008-06-21T15:52:19</TRNS_DATE>       <EMPNAME>John</EMPNAME>     </InsertRecord>   </RECORDSET>   </Insert>`<br /><br /> 即使 「 2008年-06-21T15:52:19"TRNS_DATE 的值指定為值**InlineValue**屬性，「 SYSDATE，"（系統日期） 就會插入到目標介面資料表。<br /><br /> 同時使用 InlineValue 屬性：<br /><br /> -請避免使用 InlineValue 屬性的常數值。 例如，在 INSERT 陳述式，如果您指定`<EMPNAME InlineValue="John"/>`則會導致錯誤。 這是因為 InlineValue 屬性的值會傳遞為-是 Oracle，並在此情況下*John*傳遞至 Oracle E-business Suite，不是預期的值 (預期的值是 *'John'*)。 您必須使用單引號括住員工名稱。 例如： `<EMPNAME InlineValue="’John’"/>`＞。<br /><br /> -如果您想要用於 InlineValue 屬性中的 select 查詢，您必須以括弧括住 SELECT 陳述式，並也請確定選取的查詢會擷取單一記錄。 例如： `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`＞。<br /><br /> **注意：** 如果元素標示為 NOT NULL Oracle E-business Suite 中，您就必須指定該元素的值，即使您已指定為內嵌值。 無法執行這項操作，將會導致結構描述驗證失敗。|  
|Update|執行目標介面資料表上的更新作業。 所指定 SQL WHERE 子句的篩選字串指定要更新的記錄。 在範本的記錄中指定的更新值。<br /><br /> 更新作業的傳回值已更新的資料列數目。|  
|DELETE|執行 SQL WHERE 子句中的篩選字串指定為基礎的介面目標資料表上的刪除作業。<br /><br /> 刪除作業的傳回值是已刪除的資料列數目。|  

## <a name="important-details"></a>重要的詳細資料  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現相同的一組標準的作業 （Select、 Insert、 Update 和 Delete 每個資料表） 和選取作業為基礎的 Oracle 資料庫中的每個檢視。 上述的 DML 作業也會適用於基礎的 Oracle 資料庫資料表和檢視。  

  - 您不需要設定應用程式內容，若要執行的 Oracle 資料庫中的資料表和檢視上的作業。 不過，對於自訂的 Oracle E-business Suite 應用程式，使用者可能會或可能無法登錄為介面資料表的基底資料庫資料表。 如果資料庫資料表不會註冊為介面資料表中，它位於底下**資料表**中的子節點**成品型檢視**節點或**結構描述基礎的檢視**節點在設計階段時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
    這些資料表是與 Oracle E-business 應用程式相關聯。 因此對於這些資料表上的任何作業，您必須設定應用程式內容。 請參閱設定應用程式內容[這裡輸入連結描述](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)