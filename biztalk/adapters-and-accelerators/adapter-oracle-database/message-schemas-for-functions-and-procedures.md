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
ms.openlocfilehash: a0d44d12bab47aba1335261970a11199b86803a2
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752878"
---
# <a name="message-schemas-for-functions-and-procedures"></a><span data-ttu-id="deaba-102">函式和程序的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="deaba-102">Message Schemas for Functions and Procedures</span></span>
<span data-ttu-id="deaba-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]表面 Oracle 資料庫函式和預存程序做為作業。</span><span class="sxs-lookup"><span data-stu-id="deaba-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces Oracle database functions and stored procedures as operations.</span></span> <span data-ttu-id="deaba-104">本章節描述的訊息結構及用來叫用函式和程序的動作。</span><span class="sxs-lookup"><span data-stu-id="deaba-104">This section describes the message structure and actions used to invoke functions and procedures.</span></span>  

## <a name="message-structure-of-functions-and-procedures"></a><span data-ttu-id="deaba-105">函式和程序的訊息結構</span><span class="sxs-lookup"><span data-stu-id="deaba-105">Message Structure of Functions and Procedures</span></span>  
 <span data-ttu-id="deaba-106">作業呈現函式和預存程序會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="deaba-106">The operations surfaced for functions and stored procedures follow a request-response message exchange pattern.</span></span> <span data-ttu-id="deaba-107">下表顯示這些要求和回應訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="deaba-107">The following table shows the structure of these request and response messages.</span></span>  

|<span data-ttu-id="deaba-108">作業</span><span class="sxs-lookup"><span data-stu-id="deaba-108">Operation</span></span>|<span data-ttu-id="deaba-109">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="deaba-109">XML Message</span></span>|<span data-ttu-id="deaba-110">描述</span><span class="sxs-lookup"><span data-stu-id="deaba-110">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="deaba-111">預存程序要求</span><span class="sxs-lookup"><span data-stu-id="deaba-111">Stored Procedure Request</span></span>|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="deaba-112">支援訊息內文中的 Oracle IN 和 OUT IN 參數</span><span class="sxs-lookup"><span data-stu-id="deaba-112">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="deaba-113">預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="deaba-113">Stored Procedure Response</span></span>|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="deaba-114">支援在訊息主體中的 Oracle 出] 及 [在 OUT 參數</span><span class="sxs-lookup"><span data-stu-id="deaba-114">Supports Oracle OUT and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="deaba-115">函式要求</span><span class="sxs-lookup"><span data-stu-id="deaba-115">Function Request</span></span>|`<[FN_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|<span data-ttu-id="deaba-116">支援訊息內文中的 Oracle IN 和 OUT IN 參數</span><span class="sxs-lookup"><span data-stu-id="deaba-116">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="deaba-117">函式回應</span><span class="sxs-lookup"><span data-stu-id="deaba-117">Function Response</span></span>|`<[FN_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|<span data-ttu-id="deaba-118">支援在訊息主體中的 Oracle 出] 及 [在 OUT 參數</span><span class="sxs-lookup"><span data-stu-id="deaba-118">Supports Oracle OUT and IN OUT parameters in the message body</span></span><br /><br /> <span data-ttu-id="deaba-119">-函式的傳回值會傳回在`<[FN_NAME]Result\>`項目。</span><span class="sxs-lookup"><span data-stu-id="deaba-119">- The function return value is returned in the `<[FN_NAME]Result\>` element.</span></span> <span data-ttu-id="deaba-120">這是回應訊息中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="deaba-120">This is the first element in the response message.</span></span> <span data-ttu-id="deaba-121">它前面的任何參數。</span><span class="sxs-lookup"><span data-stu-id="deaba-121">It comes before any parameters.</span></span>|  
|<span data-ttu-id="deaba-122">封裝的程序或函式要求</span><span class="sxs-lookup"><span data-stu-id="deaba-122">Packaged Procedure or Function Request</span></span>|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="deaba-123">函式或預存程序相同</span><span class="sxs-lookup"><span data-stu-id="deaba-123">Same as Function or Stored Procedure</span></span>|  
|<span data-ttu-id="deaba-124">封裝的程序或函式回應</span><span class="sxs-lookup"><span data-stu-id="deaba-124">Packaged Procedure or Function Response</span></span>|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="deaba-125">函式或預存程序相同</span><span class="sxs-lookup"><span data-stu-id="deaba-125">Same as Function or Stored Procedure</span></span>|  

 <span data-ttu-id="deaba-126">`[SCHEMA]` = Oracle 成品、 的集合比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="deaba-126">`[SCHEMA]` = Collection of Oracle artifacts; for example, SCOTT.</span></span>  

 <span data-ttu-id="deaba-127">`[SP_NAME]` = 若要執行預存程序比方說，SP_INSERT。</span><span class="sxs-lookup"><span data-stu-id="deaba-127">`[SP_NAME]` = The stored procedure to be executed; for example, SP_INSERT.</span></span>  

 <span data-ttu-id="deaba-128">`[FN_NAME]` = 要執行的函式比方說，FN_GETID。</span><span class="sxs-lookup"><span data-stu-id="deaba-128">`[FN_NAME]` = The function to be executed; for example, FN_GETID.</span></span>  

 <span data-ttu-id="deaba-129">`[PRM1_NAME]` = Oracle 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="deaba-129">`[PRM1_NAME]` = The name of the Oracle parameter.</span></span> <span data-ttu-id="deaba-130">請參閱 [描述] 欄位的每個訊息的支援的參數方向。</span><span class="sxs-lookup"><span data-stu-id="deaba-130">See the Description column for supported parameter directions for each message.</span></span>  

 <span data-ttu-id="deaba-131">`[PACKAGE_NAME]` = 封裝包含目標的程序或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="deaba-131">`[PACKAGE_NAME]` = The name of the package that contains the targeted procedure or function.</span></span>  

 <span data-ttu-id="deaba-132">Oracle 資料庫支援預存程序和函式多載。</span><span class="sxs-lookup"><span data-stu-id="deaba-132">The Oracle database supports overloading for stored procedures and functions.</span></span> <span data-ttu-id="deaba-133">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由將多載字串附加至每個多載的成品的目標命名空間支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="deaba-133">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports this capability by appending an overload string to the target namespace for each overloaded artifact.</span></span> <span data-ttu-id="deaba-134">這個字串的值會是第一個多載而言，「 overload2""overload1 」，第二個多載，依此類推。</span><span class="sxs-lookup"><span data-stu-id="deaba-134">The value of this string is "overload1" for the first overload, "overload2" for the second overload, and so on.</span></span> <span data-ttu-id="deaba-135">下列範例顯示兩個多載的預存程序的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="deaba-135">The following example shows the message structure for two overloaded stored procedures.</span></span>  

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

## <a name="message-actions-of-functions-and-procedures"></a><span data-ttu-id="deaba-136">函式和程序的訊息動作</span><span class="sxs-lookup"><span data-stu-id="deaba-136">Message Actions of Functions and Procedures</span></span>  
 <span data-ttu-id="deaba-137">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]預存程序和函式的作業會使用下列的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="deaba-137">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the following message actions for stored procedure and function operations.</span></span>  


|               <span data-ttu-id="deaba-138">訊息</span><span class="sxs-lookup"><span data-stu-id="deaba-138">Message</span></span>                |                                              <span data-ttu-id="deaba-139">動作</span><span class="sxs-lookup"><span data-stu-id="deaba-139">Action</span></span>                                              |                                          <span data-ttu-id="deaba-140">範例</span><span class="sxs-lookup"><span data-stu-id="deaba-140">Example</span></span>                                           |
|--------------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|       <span data-ttu-id="deaba-141">預存程序要求</span><span class="sxs-lookup"><span data-stu-id="deaba-141">Stored Procedure Request</span></span>       |            `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]`            |          `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT`           |
|      <span data-ttu-id="deaba-142">預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="deaba-142">Stored Procedure Response</span></span>       |       `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/response`        |      `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/response`      |
|           <span data-ttu-id="deaba-143">函式要求</span><span class="sxs-lookup"><span data-stu-id="deaba-143">Function Request</span></span>           |            `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]`             |           `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID`            |
|          <span data-ttu-id="deaba-144">函式回應</span><span class="sxs-lookup"><span data-stu-id="deaba-144">Function Response</span></span>           |        `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]/response`        |       `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID/response`       |
|  <span data-ttu-id="deaba-145">封裝的預存程序要求</span><span class="sxs-lookup"><span data-stu-id="deaba-145">Packaged Stored Procedure Request</span></span>   |     `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]`      |       `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT`       |
|  <span data-ttu-id="deaba-146">封裝的預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="deaba-146">Packaged Stored Procedure Response</span></span>  | `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response` |  `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT/response`   |
|      <span data-ttu-id="deaba-147">封裝函式要求</span><span class="sxs-lookup"><span data-stu-id="deaba-147">Packaged Function Request</span></span>       |     `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]`      |       `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID`        |
|      <span data-ttu-id="deaba-148">封裝函式回應</span><span class="sxs-lookup"><span data-stu-id="deaba-148">Packaged Function Response</span></span>      | `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response` |   `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID/response`   |
| <span data-ttu-id="deaba-149">多載的預存程序要求</span><span class="sxs-lookup"><span data-stu-id="deaba-149">Overloaded Stored Procedure Request</span></span>  |      `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]`       |     `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1`      |
| <span data-ttu-id="deaba-150">預存程序回應的多載</span><span class="sxs-lookup"><span data-stu-id="deaba-150">Overloaded Stored Procedure Response</span></span> |  `http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response`  | `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1/response` |

 <span data-ttu-id="deaba-151">`[SCHEMA]` = Oracle 成品、 的集合比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="deaba-151">`[SCHEMA]` = Collection of Oracle artifacts; for example, SCOTT.</span></span>  

 <span data-ttu-id="deaba-152">`[SP_NAME]` = 若要執行預存程序比方說，SP_INSERT。</span><span class="sxs-lookup"><span data-stu-id="deaba-152">`[SP_NAME]` = The stored procedure to be executed; for example, SP_INSERT.</span></span>  

 <span data-ttu-id="deaba-153">`[FN_NAME]` = 要執行的函式比方說，FN_GETID。</span><span class="sxs-lookup"><span data-stu-id="deaba-153">`[FN_NAME]` = The function to be executed; for example, FN_GETID.</span></span>  

 <span data-ttu-id="deaba-154">`[PACKAGE_NAME]` = 封裝包含目標的程序或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="deaba-154">`[PACKAGE_NAME]` = The name of the package that contains the targeted procedure or function.</span></span>  

 <span data-ttu-id="deaba-155">`[OVERLOAD]` = 多載的參數。</span><span class="sxs-lookup"><span data-stu-id="deaba-155">`[OVERLOAD]` = The Overload parameter.</span></span> <span data-ttu-id="deaba-156">可能的值為 overload1、 overload2，等等。</span><span class="sxs-lookup"><span data-stu-id="deaba-156">The possible values are overload1, overload2, and so on.</span></span>  

## <a name="see-also"></a><span data-ttu-id="deaba-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deaba-157">See Also</span></span>  
 [<span data-ttu-id="deaba-158">BizTalk Adapter for Oracle Database 的訊息和訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="deaba-158">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)
