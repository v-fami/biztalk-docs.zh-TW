---
title: 訊息結構描述的特殊 LOB Operations1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e418a6-8bc7-42d9-9672-a9c149f32778
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b57e329d1de4740cac230cbb1e8151697d293dc7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962580"
---
# <a name="message-schemas-for-special-lob-operations"></a>特殊 LOB 作業的訊息結構描述
Read_\<LOBColName\>和 Update_\<LOBColName\>作業便會顯示資料表和檢視表包含 LOB 資料行，其中\<LOBColName\>是資料表中的 LOB 資料行或檢視表。 這些作業可讓您讀取或寫入 base64Binary 編碼資料的資料流的形式的 LOB 資料。 它們是在單一資料列的 LOB 資料的單一資料行上運作。  
  
 如需 Read_ 的概觀\<LOBColName\>和 Update_\<LOBColName\>作業和 Oracle LOB 資料類型的支援，請參閱[介面資料表、 介面檢視、 資料表上的作業和包含 LOB 資料的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。  
  
## <a name="message-structure-of-lob-data-type-operations"></a>LOB 資料型別作業的訊息結構  
 下表顯示的要求和回應訊息結構 Read_\<LOBColName\>和 Update_\<LOBColName\>作業。 作業的目標資料表中的訊息動作指定，而且也會出現在 目標命名空間。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|Read_\<LOBColName\>|`<Read_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</FILTER></Read_[LOBColName]>`|LOB 資料在資料列符合 where 子句篩選條件的項目中指定會傳回。 Where 子句應符合的單一資料列。 如果有一個以上相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。|  
|Read_\<LOBColName\>回應|`<Read_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <Read_[LOBColName]Result>    [LOB_DATA]  </Read_[LOBColName]Result></Read_[LOBColName]Response>`|LOB 資料是 base64Binary 編碼資料的資料流的形式傳回。|  
|Update_\<LOBColName\>|`<Update_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</LOB_COLUMN>  <DATA>[Value]</DATA></Update_[LOBColName]>`|LOB 資料中的資料列符合 where 子句篩選條件的項目中指定更新中的資料\<資料\>項目。 Where 子句應符合的單一資料列。 如果有一個以上相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]擲回例外狀況。<br /><br /> **請注意**更新 BLOB 的資料行時\<資料\>項目必須永遠包含 base64 編碼值。 CLOB 和 NCLOB，\<資料\>元素可以有字串值。|  
|Update_\<LOBColName\>回應|`<Update_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]"></Update_[LOBColName]Response>`|會傳回空白回應。|  
  
 實體描述：  
  
 [版本] = 訊息版本字串。例如，"http://schemas.microsoft.com/OracleEBS/2008/05。 」  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，客戶。  
  
 [LOBCol_Name] = 的 LOB 資料行名稱例如，相片。  
  
 [WHERE_clause] = Oracle 資料庫的 SELECT 陳述式 WHERE 子句，比對單一資料列。例如，識別碼 = 1。  
  
 [LOB_DATA] = base64Binary 類型中的 LOB 資料行資料。  
  
> [!IMPORTANT]
>  Read_ 的訊息結構\<LOBColName\>和 Update_\<LOBColName\>檢視上的作業相同資料表上會有不同之處在於此作業的命名空間指定的檢視，而不是資料表：`<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`.  
  
## <a name="message-actions-for-lob-data-type-operations"></a>LOB 資料型別作業的訊息動作  
 下表顯示所使用的訊息動作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]如 Read_\<LOBColName\>和 Update_\<LOBColName\>資料表上的作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用資料表名稱和訊息動作中指定的 LOB 資料行名稱來判斷目標資料表和 LOB 資料行的作業。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|動作|範例|  
|---------------|------------|-------------|  
|Read_\<LOBColName\>|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo`|  
|Read_\<LOBColName\>回應|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo/response`|  
|Update_\<LOBColName\>|**Blob**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|**Blob**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/`|  
|Update_\<LOBColName\>回應|**Blob**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|**Blob**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/response`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/response`|  
  
 實體描述：  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，客戶。 (SCOTT。CUSTOMER 資料表中會安裝所包含的範例中的 SQL 指令碼）。  
  
 [LOBCol_Name] = 的 LOB 資料行名稱例如，相片。  
  
> [!IMPORTANT]
>  Read_ 的訊息動作\<LOBColName\>和 Update_\<LOBColName\>檢視上的作業是所使用的資料表，類似，不同之處在於動作的作業指定的檢視，而不是資料表： `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`.  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Adapter for Oracle E-Business Suite 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)