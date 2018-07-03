---
title: 複合作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d80c023b-1912-43d4-be29-eb9e1b323593
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 716e87dd2973572d473f6637e12c5a80ac6cf847
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015290"
---
# <a name="message-schemas-for-composite-operations"></a>複合作業的訊息結構描述
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓您執行 SQL Server 資料庫上的複合作業。 複合作業可以包含多項作業包括 Insert、 Update 和刪除作業的資料表和檢視表和預存程序的作業。 複合作業可以依任何順序來包含這些作業。  
  
 如需詳細資訊：  
  
- 複合作業，請參閱[支援複合作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)。  
  
- 如何執行複合作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 使用 SQL 配接器的 SQL Server 中執行複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。  
  
## <a name="message-structure-for-the-composite-operation"></a>複合作業的訊息結構  
 由於複合作業包含多個個別的作業;複合作業的訊息結構包含的個別作業的訊息結構。 複合作業包含資料表、 檢視和預存程序上的作業，因為複合作業訊息會遵循要求-回應訊息交換模式。  
  
 下表顯示包含插入作業的複合作業的要求和回應訊息的結構，不接受任何預存程序輸入參數和刪除作業。  
  
|作業|XML 訊息|  
|---------------|-----------------|  
|複合作業要求|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[Value1]</[FIELD2_NAME]>         …       </[TABLE_NAME]>     </Rows>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]" />   <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>       </[TABLE_NAME]>     </Rows>   </Delete> </Request>`|  
|複合作業回應|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <InsertResult>       <long>[value]</long>      </InsertResult>   </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">     <[SP_NAME]Result>       <DataSet>         <any>[Value]</any>          <any>[Value]</any>          …       </DataSet>     </[SP_NAME]Result>     <ReturnValue>[value]</ReturnValue>    </[SP_NAME]Response>   <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 [PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。  
  
 [COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述名稱。  
  
 [SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  
  
 [TABLE_NAME] = 資料表的名稱例如，員工。  
  
 [FIELD1_NAME] = 資料表的欄位名稱;例如，名稱。  
  
 [SP_NAME] = 預存程序的執行;比方說，ADD_EMP_DETAILS。  
  
## <a name="message-action-for-the-composite-operation"></a>複合作業的訊息動作  
 複合作業的訊息動作是 「 CompositeOperation。 」  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)