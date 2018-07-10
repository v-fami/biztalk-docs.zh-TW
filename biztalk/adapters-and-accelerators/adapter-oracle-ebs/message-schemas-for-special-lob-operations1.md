---
title: 特殊 LOB Operations1 如訊息結構描述 |Microsoft Docs
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
ms.openlocfilehash: 651a4fe57d4b7ef7c85cc9c195c0ec96c67d0e8f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014551"
---
# <a name="message-schemas-for-special-lob-operations"></a>特殊 LOB 作業的訊息結構描述
Read_\<LOBColName\>和 Update_\<LOBColName\>作業會顯示資料表和檢視表包含 LOB 資料行，其中\<LOBColName\>是資料表中的 LOB 資料行或檢視表。 這些作業可讓您讀取或寫入為 base64Binary 編碼資料的資料流的 LOB 資料。 它們是單一資料列中的 LOB 資料的單一資料行上運作。  
  
 如需概觀 Read_\<LOBColName\>和 Update_\<LOBColName\>作業和 Oracle LOB 資料類型的支援，請參閱[介面資料表、 介面檢視、 資料表上的作業和包含 LOB 資料的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。  
  
## <a name="message-structure-of-lob-data-type-operations"></a>LOB 資料型別作業的訊息結構  
 下表顯示要求和回應訊息的結構如 Read_\<LOBColName\>和 Update_\<LOBColName\>作業。 作業的目標資料表中的訊息動作指定，也會出現在 目標命名空間。  
  
> [!NOTE]
>  表格後，請參閱實體描述。  
  
|           作業            |                                                                                  XML 訊息                                                                                  |                                                                                                                                                                                                                                                              描述                                                                                                                                                                                                                                                              |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Read_\<LOBColName\>       |                           `<Read_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</FILTER></Read_[LOBColName]>`                           |                                                                                                           LOB 資料在資料列符合 where 子句篩選項目中指定，會傳回。 Where 子句應該符合單一資料列。 如果有多個相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。                                                                                                            |
|  Read_\<LOBColName\>回應  | `<Read_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <Read_[LOBColName]Result>    [LOB_DATA]  </Read_[LOBColName]Result></Read_[LOBColName]Response>` |                                                                                                                                                                                                                                  LOB 資料會當成 base64Binary 編碼資料的資料流。                                                                                                                                                                                                                                   |
|     Update_\<LOBColName\>      |            `<Update_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</LOB_COLUMN>  <DATA>[Value]</DATA></Update_[LOBColName]>`            | LOB 資料中的資料列符合 where 子句篩選項目中指定更新中的資料\<資料\>項目。 Where 子句應該符合單一資料列。 如果有多個相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]擲回例外狀況。<br /><br /> **附註**更新 BLOB 的資料行時發生\<資料\>項目必須永遠包含 base64 編碼值。 CLOB 和 NCLOB，\<資料\>項目可以有字串值。 |
| Update_\<LOBColName\>回應 |                                 `<Update_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]"></Update_[LOBColName]Response>`                                  |                                                                                                                                                                                                                                                    會傳回空的回應。                                                                                                                                                                                                                                                     |
  
 實體描述：  
  
 [VERSION] = 訊息版本字串;例如，"<http://schemas.microsoft.com/OracleEBS/2008/05>」。  
  
 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  
  
 [TABLE_NAME] = 包含目標的 LOB 資料行; 的資料表例如，客戶。  
  
 [LOBCol_Name] = 是 LOB 資料行的名稱例如，相片。  
  
 [W] = [Oracle 資料庫的 SELECT 陳述式的單一資料列; 符合 WHERE 子句例如，識別碼 = 1。  
  
 [如果是 LOB_DATA] = base64Binary 型別中的 LOB 資料行資料。  
  
> [!IMPORTANT]
>  訊息的結構 Read_\<LOBColName\>和 Update_\<LOBColName\>檢視上的作業相同資料表上會有不同之處在於的命名空間作業指定的檢視，而不是資料表：`<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`.  
  
## <a name="message-actions-for-lob-data-type-operations"></a>LOB 資料型別作業的訊息動作  
 下表顯示所使用的訊息動作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]針對 Read_\<LOBColName\>和 Update_\<LOBColName\>資料表上的作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用資料表名稱和訊息動作中指定的 LOB 資料行名稱來判斷目標資料表與 LOB 作業的資料行。  
  
> [!NOTE]
>  表格後，請參閱實體描述。  
  
|作業|動作|範例|  
|---------------|------------|-------------|  
|Read_\<LOBColName\>|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo`|  
|Read_\<LOBColName\>回應|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo/response`|  
|Update_\<LOBColName\>|**Blob**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|**Blob**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/`|  
|Update_\<LOBColName\>回應|**Blob**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|**Blob**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/response`<br /><br /> **CLOB 和 NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/response`|  
  
 實體描述：  
  
 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  
  
 [TABLE_NAME] = 包含目標的 LOB 資料行; 的資料表例如，客戶。 (SCOTT。CUSTOMER 資料表中會安裝所包含的範例中的 SQL 指令碼）。  
  
 [LOBCol_Name] = 是 LOB 資料行的名稱例如，相片。  
  
> [!IMPORTANT]
>  Read_ 的訊息動作\<LOBColName\>和 Update_\<LOBColName\>檢視表上的作業是所使用的資料表，類似，不同之處在於動作作業指定的檢視，而不是資料表： `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`.  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle E-Business Suite 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)