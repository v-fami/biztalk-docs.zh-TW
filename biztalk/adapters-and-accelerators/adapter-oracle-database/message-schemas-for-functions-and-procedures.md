---
title: 訊息函式和程序的結構描述 |Microsoft 文件
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
ms.openlocfilehash: 6fc8c09499914dd075fe6a46fbc230a4bed104e0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25964564"
---
# <a name="message-schemas-for-functions-and-procedures"></a>函數和程序的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面 Oracle 資料庫函式和預存程序做為作業。 本章節描述的訊息結構及用來叫用函數和程序的動作。  
  
## <a name="message-structure-of-functions-and-procedures"></a>函數和程序的訊息結構  
 作業中顯示函式和預存程序會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  
  
|運算|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|預存程序要求|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|訊息本文中支援 Oracle IN 和 OUT IN 參數|  
|預存程序的回應|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|支援訊息內文中的 Oracle 出和 IN OUT 參數|  
|函式要求|`<[FN_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|訊息本文中支援 Oracle IN 和 OUT IN 參數|  
|函式的回應|`<[FN_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|支援訊息內文中的 Oracle 出和 IN OUT 參數<br /><br /> -函式的傳回值會傳回在\<[FN_NAME] 結果\>項目。 這是在回應訊息中的第一個項目。 它前面的任何參數。|  
|封裝的程序或函式要求|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|函式或預存程序相同|  
|封裝的程序或函式的回應|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|函式或預存程序相同|  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [SP_NAME] = 預存程序的執行。例如，SP_INSERT。  
  
 [FN_NAME] = 要執行的函式例如，FN_GETID。  
  
 [PRM1_NAME] = Oracle 參數的名稱。 請參閱支援的參數方向的每個訊息的描述資料行。  
  
 [PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。  
  
 Oracle 資料庫支援預存程序和函式多載。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援這項功能將多載字串附加至每個多載的成品的目標命名空間。 這個字串的值為"overload1 」 的第一個多載中，「 overload2"第二個多載，依此類推。 下列範例顯示兩個多載的預存程序的訊息結構。  
  
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
  
## <a name="message-actions-of-functions-and-procedures"></a>函數和程序的訊息動作  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]預存程序和函式的作業會使用下列的訊息動作。  
  
|訊息|動作|範例|  
|-------------|------------|-------------|  
|預存程序要求|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT|  
|預存程序的回應|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/response|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/response|  
|函式要求|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID|  
|函式的回應|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]/response|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID/response|  
|封裝的預存程序要求|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT|  
|封裝預存程序的回應|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT/response|  
|包裝函式要求|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID|  
|回應封裝函式|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID/response|  
|多載的預存程序要求|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1|  
|預存程序回應的多載|http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response|http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1/response|  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [SP_NAME] = 預存程序的執行。例如，SP_INSERT。  
  
 [FN_NAME] = 要執行的函式例如，FN_GETID。  
  
 [PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。  
  
 [多載] = 多載的參數。 可能的值為 overload1、 overload2，等等。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)