---
title: 函式和程序訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functions and procedures, message structure of
- functions and procedures, message actions of
ms.assetid: 90b77b15-a4c6-487d-a09e-a078ceddfd1e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a821de5ac4a05165f33fa7035880d239bd6892b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008575"
---
# <a name="message-schemas-for-functions-and-procedures"></a>函式和程序的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]表面 Oracle 資料庫函式和預存程序做為作業。 本章節描述的訊息結構及用來叫用函式和程序的動作。  

## <a name="message-structure-of-functions-and-procedures"></a>函式和程序的訊息結構  
 作業呈現函式和預存程序會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  

|作業|XML 訊息|描述|  
|---------------|-----------------|-----------------|  
|預存程序要求|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|支援訊息內文中的 Oracle IN 和 OUT IN 參數|  
|預存程序的回應|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|支援在訊息主體中的 Oracle 出] 及 [在 OUT 參數|  
|函式要求|`<[FN_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|支援訊息內文中的 Oracle IN 和 OUT IN 參數|  
|函式回應|`<[FN_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|支援在訊息主體中的 Oracle 出] 及 [在 OUT 參數<br /><br /> -函式的傳回值都會傳入\<[FN_NAME] 結果\>項目。 這是回應訊息中的第一個項目。 它前面的任何參數。|  
|封裝的程序或函式要求|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|函式或預存程序相同|  
|封裝的程序或函式回應|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|函式或預存程序相同|  

 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  

 [SP_NAME] = 預存程序的執行;比方說，SP_INSERT。  

 [FN_NAME] = 要執行的函式比方說，FN_GETID。  

 [PRM1_NAME] = Oracle 參數的名稱。 請參閱 [描述] 欄位的每個訊息的支援的參數方向。  

 [PACKAGE_NAME] = 封裝包含目標的程序或函式的名稱。  

 Oracle 資料庫支援預存程序和函式多載。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由將多載字串附加至每個多載的成品的目標命名空間支援這項功能。 這個字串的值會是第一個多載而言，「 overload2""overload1 」，第二個多載，依此類推。 下列範例顯示兩個多載的預存程序的訊息結構。  

```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  

Stored Procedure Overload 2:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  

## <a name="message-actions-of-functions-and-procedures"></a>函式和程序的訊息動作  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]預存程序和函式的作業會使用下列的訊息動作。  


|               訊息                |                                              動作                                              |                                          範例                                           |
|--------------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|       預存程序要求       |            http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Procedure/ [SP_NAME]            |          http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT           |
|      預存程序的回應       |       http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Procedure/ [SP_NAME] / 回應        |      http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/response      |
|           函式要求           |            http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Function/ [FN_NAME]             |           http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID            |
|          函式回應           |        http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Function/ [FN_NAME] / 回應        |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID/response       |
|  封裝的預存程序要求   |     http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME]      |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT       |
|  封裝的預存程序的回應  | http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME] / 回應 |  http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT/response   |
|      封裝函式要求       |     http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME]      |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID        |
|      封裝函式回應      | http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME] / 回應 |   http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID/response   |
| 多載的預存程序要求  |      http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Procedure/ [SP_NAME] / [多載]       |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1      |
| 預存程序回應的多載 |  http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA] /Procedure/ [SP_NAME] / [多載] / 回應  | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1/response |

 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  

 [SP_NAME] = 預存程序的執行;比方說，SP_INSERT。  

 [FN_NAME] = 要執行的函式比方說，FN_GETID。  

 [PACKAGE_NAME] = 封裝包含目標的程序或函式的名稱。  

 [多載] = 多載的參數。 可能的值為 overload1、 overload2，等等。  

## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)