---
title: "訊息的程序和函數的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4acfb29e-8774-4eb7-ba10-2dcb93d2b41a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 374b4d3365ec3aaac86fb5004969cd4cc189271d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-procedures-and-functions"></a>訊息結構描述的程序和函式
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]介面 SQL Server 資料庫預存程序和純量和資料表值函式做為作業。 本章節描述的訊息結構及用來叫用程序和函數的動作。  
  
## <a name="message-structure-of-procedures-and-functions"></a>訊息結構的程序和函數  
 作業中顯示程序和函式會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|預存程序要求|`<[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|-|  
|預存程序的回應|`<[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[SP_NAME]Result>      <DataSet>        <any>[Value]</any>       <any>[Value]</any>       …     </DataSet>   </[SP_NAME]Result>   <ReturnValue>[Value]</ReturnValue> </[SP_NAME]Response>`|預存程序的傳回值是資料集的陣列。|  
|強型別的預存程序要求|`<[STRNG_SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[STRNG_SP_NAME]>`|-|  
|強型別的預存程序的回應|`<[STRNG_SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">     <StoredProcedureResultSet0>          <StoredProcedureResultSet0 xmlns:ns1="http://schemas.microsoft.com/Sql/2008/05/ProcedureResultSets/[SCHEMA]/[STRNG_SP_NAME]">               <[PRM1_NAME]>value1<[PRM1_NAME]>               <[PRM2_NAME]>value2</[PRM2_NAME]>               …         </StoredProcedureResultSet0>     </StoredProcedureResultSet0>    <ReturnValue>[Value]</ReturnValue> </[STRNG_SP_NAME]Response>`|強類型的預存程序的傳回值是強型別資料的陣列。|  
|純量函式要求|`<[SCLR_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[PRM_NAME]>value</[PRM_NAME]> </[SCLR_FN_NAME]>`|-|  
|純量函數回應|`<[SCLR_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[SCLR_FN_NAME]Result>return_value</[SCLR_FN_NAME]Result>   <[PRM_NAME]>value</[PRM_NAME]>   </[SCLR_FN_NAME]Response>`|-|  
|資料表值函式要求|`<[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[TBL_FN_NAME]>`|-|  
|資料表值函式的回應|`<[TBL_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[TBL_FN_NAME]Result>      <[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">         <[PRM1_NAME]>value1</[PRM1_NAME]>         <[PRM2_NAME]>value2</[PRM2_NAME]>         ...      </[TBL_FN_NAME]">        ...      </[TBL_FN_NAME]Result> </[TBL_FN_NAME]Response>`||  
  
 [SCHEMA] = 集合 SQL Server 成品。例如，dbo。  
  
 [SP_NAME] = 預存程序的執行。例如，ADD_EMP_DETAILS。  
  
 [STRNG_SP_NAME] = 強型別的預存程序的執行。例如，GET_EMP_DETAILS。  
  
 [SCLR_FN_NAME] = 要執行的純量函式例如，GET_EMP_ID。  
  
 [TBL_FN_NAME] = 要執行; 資料表值函式例如，TVF_EMPLOYEE。  
  
 [PRM_NAME] = SQL Server 參數的名稱。  
  
## <a name="message-actions-of-functions-and-procedures"></a>函數和程序的訊息動作  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]預存程序和函式的作業會使用下列的訊息動作。  
  
|訊息|動作|範例|  
|-------------|------------|-------------|  
|預存程序要求|程序 / [SCHEMA] / [SP_NAME]|程序/dbo/ADD_EMP_DETAILS|  
|預存程序的回應|程序 / [SCHEMA] / [SP_NAME] / 回應|程序/dbo/ADD_EMP_DETAILS/回應|  
|強型別的預存程序要求|TypedProcedure / [SCHEMA] / [STRNG_SP_NAME]|TypedProcedure/dbo/GET_EMP_DETAILS|  
|強型別的預存程序的回應|TypedProcedure / [SCHEMA] / [STRNG_SP_NAME] / 回應|TypedProcedure/dbo/GET_EMP_DETAILS/回應|  
|XML 預存程序要求|XmlProcedure / [SCHEMA] / [SP_NAME]|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML|  
|XML 預存程序的回應|XmlProcedure / [SCHEMA] / [SP_NAME] / 回應|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML/回應|  
|純量函式要求|ScalarFunction / [SCHEMA] / [SCLR_FN_NAME]|ScalarFunction/dbo/GET_EMP_ID|  
|純量函數回應|ScalarFunction / [SCHEMA] / [SCLR_FN_NAME] / 回應|ScalarFunction/dbo/GET_EMP_ID/回應|  
|資料表值函式要求|Tablefunction 之 Argument / [SCHEMA] / [TBL_FN_NAME]|Tablefunction 之 Argument/dbo/TVF_EMPLOYEE|  
|資料表值函式的回應|Tablefunction 之 Argument / [SCHEMA] / [TBL_FN_NAME] / 回應|Tablefunction 之 Argument/dbo/TVF_EMPLOYEE/回應|  
  
 [SP_NAME] = 預存程序的執行。例如，ADD_EMP_DETAILS。  
  
 [STRNG_SP_NAME] = 強型別的預存程序的執行。例如，GET_EMP_DETAILS。  
  
 [SCLR_FN_NAME] = 要執行的純量函式例如，GET_EMP_ID。  
  
 [TBL_FN_NAME] = 要執行; 資料表值函式的名稱例如，TVF_EMPLOYEE。  
  
## <a name="see-also"></a>另請參閱  
 [訊息與 BizTalk adapter for SQL Server 的訊息結構描述](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)