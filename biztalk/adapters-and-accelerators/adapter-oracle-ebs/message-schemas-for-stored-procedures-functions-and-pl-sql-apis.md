---
title: "預存程序、 函數和 PL-SQL Api 訊息結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d707f10-470d-4390-bb5b-0301c326f375
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029c48c1e6066d09d43da51b2bb1f6786a516f54
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-stored-procedures-functions-and-plsql-apis"></a>訊息結構描述的預存程序、 函數和 PL/SQL 應用程式開發介面
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]介面為基礎的 Oracle 資料庫做為作業的預存程序、 函數和 PL/SQL Api （預存程序和函式，在封裝內）。 本章節描述的訊息結構及用來叫用預存程序、 函數和 PL/SQL Api 的動作。  
  
## <a name="message-structure-of-stored-procedures-functions-and-plsql-apis"></a>訊息結構的預存程序、 函數和 PL/SQL 應用程式開發介面  
 作業中顯示函式和預存程序會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|預存程序要求|`<[SP_NAME] xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|訊息本文中支援 Oracle IN 和 OUT IN 參數|  
|預存程序的回應|`<[SP_NAME]Response xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|支援訊息內文中的 Oracle 出和 IN OUT 參數|  
|函式要求|`<[FN_NAME] xmlns="[VERSION]/Functions/[SCHEMA] ">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|訊息本文中支援 Oracle IN 和 OUT IN 參數|  
|函式的回應|`<[FN_NAME]Response xmlns="[VERSION]/Functions/[SCHEMA]">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|支援訊息內文中的 Oracle 出和 IN OUT 參數<br /><br /> 函式傳回值會傳回在\<[FN_NAME] 結果\>項目。 這是在回應訊息中的第一個項目。 它前面的任何參數。|  
|PL/SQL API 要求|`<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|函式或預存程序相同|  
|封裝的程序或函式的回應|`<[SP_NAME]Response xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|函式或預存程序相同|  
  
 實體描述：  
  
 [版本] = http://schemas.microsoft.com/OracleEBS/2008/05。  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [SP_NAME] = 預存程序的執行。例如，SP_INSERT。  
  
 [FN_NAME] = 要執行的函式例如，FN_GETID。  
  
 [PRM1_NAME] = Oracle 參數的名稱。 請參閱支援的參數方向的每個訊息的描述資料行。  
  
 [PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。  
  
 Oracle 資料庫支援預存程序和函式多載。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援這項功能將多載字串附加至每個多載的成品的目標命名空間。 這個字串的值為"overload1 」 的第一個多載中，「 overload2"第二個多載，依此類推。 下列範例顯示兩個多載的預存程序的訊息結構。  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
## <a name="message-actions-of-stored-procedures-functions-and-plsql-apis"></a>訊息的預存程序、 函數和 PL/SQL Api 的動作  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]的預存程序、 函數和 PL/SQL API 作業會使用下列的訊息動作。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|訊息|動作|範例|  
|-------------|------------|-------------|  
|預存程序要求|程序 / [SCHEMA] / [SP_NAME]|程序/SCOTT/SP_INSERT|  
|預存程序的回應|程序 / [SCHEMA] / [SP_NAME] / 回應|程序/SCOTT/SP_INSERT/回應|  
|函式要求|函式 / [SCHEMA] / [FN_NAME]|函式/SCOTT/FN_GETID|  
|函式的回應|函式 / [SCHEMA] / [FN_NAME] / 回應|函式/SCOTT/FN_GETID/回應|  
|PL/SQL API 要求|[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME]|SCOTT/封裝/客戶/SP_INSERT|  
|封裝預存程序的回應|[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME] / 回應|SCOTT/封裝/客戶/SP_INSERT/回應|  
|包裝函式要求|[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME]|SCOTT/封裝/客戶/FN_GETID|  
|回應封裝函式|[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME] / 回應|SCOTT/封裝/客戶/FN_GETID/回應|  
|多載的預存程序要求|[SCHEMA] /Procedure/ [SP_NAME] / [多載]|SCOTT/程序/SP_INSERT/overload1|  
|預存程序回應的多載|[SCHEMA] /Procedure/ [SP_NAME] / [多載] / 回應|SCOTT/程序/SP_INSERT/overload1/回應|  
  
 實體描述：  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [SP_NAME] = 預存程序的執行。例如，SP_INSERT。  
  
 [FN_NAME] = 要執行的函式例如，FN_GETID。  
  
 [PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。  
  
 [多載] = 多載的參數。 可能的值為 overload1、 overload2，等等。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Adapter for Oracle E-Business Suite 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)