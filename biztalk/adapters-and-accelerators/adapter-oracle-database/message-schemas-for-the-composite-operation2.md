---
title: 訊息結構描述的複合 Operation2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1014ea162e9fab33aa6630d0cdb4eb774f91031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214062"
---
# <a name="message-schemas-for-the-composite-operation"></a>複合作業的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓您執行複合操作的 Oracle 資料庫上。 複合作業可以包含多個作業，並依照任何順序。 有關哪些作業可以包含在複合作業的資訊，請參閱[Oracle 資料庫中執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)。  
  
 如需如何執行複合操作使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。  
  
## <a name="message-structure-for-the-composite-operation"></a>複合作業的訊息結構  
 因為複合作業包含多個個別作業;複合作業的訊息結構包含個別作業的訊息的結構。 複合作業訊息會遵循要求-回應訊息交換模式。  
  
 下表顯示包含一個插入作業的複合作業的要求和回應訊息的結構、 已封裝的預存程序不接受任何輸入參數和刪除作業。  
  
|作業|XML 訊息|  
|---------------|-----------------|  
|複合作業要求|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|複合作業回應|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 [版本] = 訊息版本字串。例如，http://Microsoft.LobServices.OracleDB/2007/03  
  
 [PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。  
  
 [COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述的名稱。  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [TABLE_NAME] = 表格的名稱例如，員工。  
  
 [FIELD1_NAME] = 表格欄位的名稱。例如，名稱。  
  
 [SP_NAME] = 封裝預存程序的執行。例如，ADD_EMP_DETAILS。  
  
 [PRM1_NAME] = Oracle 參數，預存程序的名稱。  
  
## <a name="message-action-for-the-composite-operation"></a>複合作業的訊息動作  
 複合作業的訊息動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation。 」  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)