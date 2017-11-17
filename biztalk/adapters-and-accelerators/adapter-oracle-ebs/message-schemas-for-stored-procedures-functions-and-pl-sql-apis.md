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
ms.openlocfilehash: 6364716793e3638d157e1441e369133dc79bda95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="c5288-102">訊息結構描述的預存程序、 函數和 PL/SQL 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="c5288-102">Message Schemas for Stored Procedures, Functions, and PL/SQL APIs</span></span>
<span data-ttu-id="c5288-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]介面為基礎的 Oracle 資料庫做為作業的預存程序、 函數和 PL/SQL Api （預存程序和函式，在封裝內）。</span><span class="sxs-lookup"><span data-stu-id="c5288-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces the underlying Oracle database stored procedures, functions, and PL/SQL APIs (stored procedures and functions within a package) as operations.</span></span> <span data-ttu-id="c5288-104">本章節描述的訊息結構及用來叫用預存程序、 函數和 PL/SQL Api 的動作。</span><span class="sxs-lookup"><span data-stu-id="c5288-104">This section describes the message structure and actions used to invoke stored procedures, functions, and PL/SQL APIs.</span></span>  
  
## <a name="message-structure-of-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="c5288-105">訊息結構的預存程序、 函數和 PL/SQL 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="c5288-105">Message Structure of Stored Procedures, Functions, and PL/SQL APIs</span></span>  
 <span data-ttu-id="c5288-106">作業中顯示函式和預存程序會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c5288-106">The operations surfaced for functions and stored procedures follow a request-response message exchange pattern.</span></span> <span data-ttu-id="c5288-107">下表顯示這些要求和回應訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="c5288-107">The following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5288-108">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="c5288-108">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="c5288-109">作業</span><span class="sxs-lookup"><span data-stu-id="c5288-109">Operation</span></span>|<span data-ttu-id="c5288-110">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="c5288-110">XML Message</span></span>|<span data-ttu-id="c5288-111">Description</span><span class="sxs-lookup"><span data-stu-id="c5288-111">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="c5288-112">預存程序要求</span><span class="sxs-lookup"><span data-stu-id="c5288-112">Stored Procedure Request</span></span>|`<[SP_NAME] xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="c5288-113">訊息本文中支援 Oracle IN 和 OUT IN 參數</span><span class="sxs-lookup"><span data-stu-id="c5288-113">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="c5288-114">預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-114">Stored Procedure Response</span></span>|`<[SP_NAME]Response xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="c5288-115">支援訊息內文中的 Oracle 出和 IN OUT 參數</span><span class="sxs-lookup"><span data-stu-id="c5288-115">Supports Oracle OUT and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="c5288-116">函式要求</span><span class="sxs-lookup"><span data-stu-id="c5288-116">Function Request</span></span>|`<[FN_NAME] xmlns="[VERSION]/Functions/[SCHEMA] ">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|<span data-ttu-id="c5288-117">訊息本文中支援 Oracle IN 和 OUT IN 參數</span><span class="sxs-lookup"><span data-stu-id="c5288-117">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="c5288-118">函式的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-118">Function Response</span></span>|`<[FN_NAME]Response xmlns="[VERSION]/Functions/[SCHEMA]">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|<span data-ttu-id="c5288-119">支援訊息內文中的 Oracle 出和 IN OUT 參數</span><span class="sxs-lookup"><span data-stu-id="c5288-119">Supports Oracle OUT and IN OUT parameters in the message body</span></span><br /><br /> <span data-ttu-id="c5288-120">函式傳回值會傳回在\<[FN_NAME] 結果 > 項目。</span><span class="sxs-lookup"><span data-stu-id="c5288-120">The function return value is returned in the \<[FN_NAME]Result> element.</span></span> <span data-ttu-id="c5288-121">這是在回應訊息中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="c5288-121">This is the first element in the response message.</span></span> <span data-ttu-id="c5288-122">它前面的任何參數。</span><span class="sxs-lookup"><span data-stu-id="c5288-122">It comes before any parameters.</span></span>|  
|<span data-ttu-id="c5288-123">PL/SQL API 要求</span><span class="sxs-lookup"><span data-stu-id="c5288-123">PL/SQL API Request</span></span>|`<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="c5288-124">函式或預存程序相同</span><span class="sxs-lookup"><span data-stu-id="c5288-124">Same as Function or Stored Procedure</span></span>|  
|<span data-ttu-id="c5288-125">封裝的程序或函式的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-125">Packaged Procedure or Function Response</span></span>|`<[SP_NAME]Response xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="c5288-126">函式或預存程序相同</span><span class="sxs-lookup"><span data-stu-id="c5288-126">Same as Function or Stored Procedure</span></span>|  
  
 <span data-ttu-id="c5288-127">實體描述：</span><span class="sxs-lookup"><span data-stu-id="c5288-127">Entity descriptions:</span></span>  
  
 <span data-ttu-id="c5288-128">[版本] = http://schemas.microsoft.com/OracleEBS/2008/05。</span><span class="sxs-lookup"><span data-stu-id="c5288-128">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05.</span></span>  
  
 <span data-ttu-id="c5288-129">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="c5288-129">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="c5288-130">[SP_NAME] = 預存程序的執行。例如，SP_INSERT。</span><span class="sxs-lookup"><span data-stu-id="c5288-130">[SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.</span></span>  
  
 <span data-ttu-id="c5288-131">[FN_NAME] = 要執行的函式例如，FN_GETID。</span><span class="sxs-lookup"><span data-stu-id="c5288-131">[FN_NAME] = The function to be executed; for example, FN_GETID.</span></span>  
  
 <span data-ttu-id="c5288-132">[PRM1_NAME] = Oracle 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5288-132">[PRM1_NAME] = The name of the Oracle parameter.</span></span> <span data-ttu-id="c5288-133">請參閱支援的參數方向的每個訊息的描述資料行。</span><span class="sxs-lookup"><span data-stu-id="c5288-133">See the Description column for supported parameter directions for each message.</span></span>  
  
 <span data-ttu-id="c5288-134">[PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5288-134">[PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.</span></span>  
  
 <span data-ttu-id="c5288-135">Oracle 資料庫支援預存程序和函式多載。</span><span class="sxs-lookup"><span data-stu-id="c5288-135">The Oracle database supports overloading for stored procedures and functions.</span></span> <span data-ttu-id="c5288-136">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援這項功能將多載字串附加至每個多載的成品的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="c5288-136">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports this capability by appending an overload string to the target namespace for each overloaded artifact.</span></span> <span data-ttu-id="c5288-137">這個字串的值為"overload1 」 的第一個多載中，「 overload2"第二個多載，依此類推。</span><span class="sxs-lookup"><span data-stu-id="c5288-137">The value of this string is "overload1" for the first overload, "overload2" for the second overload, and so on.</span></span> <span data-ttu-id="c5288-138">下列範例顯示兩個多載的預存程序的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="c5288-138">The following example shows the message structure for two overloaded stored procedures.</span></span>  
  
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
  
## <a name="message-actions-of-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="c5288-139">訊息的預存程序、 函數和 PL/SQL Api 的動作</span><span class="sxs-lookup"><span data-stu-id="c5288-139">Message Actions of Stored Procedures, Functions, and PL/SQL APIs</span></span>  
 <span data-ttu-id="c5288-140">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]的預存程序、 函數和 PL/SQL API 作業會使用下列的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="c5288-140">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for stored procedure, function, and PL/SQL API operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5288-141">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="c5288-141">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="c5288-142">訊息</span><span class="sxs-lookup"><span data-stu-id="c5288-142">Message</span></span>|<span data-ttu-id="c5288-143">動作</span><span class="sxs-lookup"><span data-stu-id="c5288-143">Action</span></span>|<span data-ttu-id="c5288-144">範例</span><span class="sxs-lookup"><span data-stu-id="c5288-144">Example</span></span>|  
|-------------|------------|-------------|  
|<span data-ttu-id="c5288-145">預存程序要求</span><span class="sxs-lookup"><span data-stu-id="c5288-145">Stored Procedure Request</span></span>|<span data-ttu-id="c5288-146">程序 / [SCHEMA] / [SP_NAME]</span><span class="sxs-lookup"><span data-stu-id="c5288-146">Procedures/[SCHEMA]/[SP_NAME]</span></span>|<span data-ttu-id="c5288-147">程序/SCOTT/SP_INSERT</span><span class="sxs-lookup"><span data-stu-id="c5288-147">Procedures/SCOTT/SP_INSERT</span></span>|  
|<span data-ttu-id="c5288-148">預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-148">Stored Procedure Response</span></span>|<span data-ttu-id="c5288-149">程序 / [SCHEMA] / [SP_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="c5288-149">Procedures/[SCHEMA]/[SP_NAME]/response</span></span>|<span data-ttu-id="c5288-150">程序/SCOTT/SP_INSERT/回應</span><span class="sxs-lookup"><span data-stu-id="c5288-150">Procedures/SCOTT/SP_INSERT/response</span></span>|  
|<span data-ttu-id="c5288-151">函式要求</span><span class="sxs-lookup"><span data-stu-id="c5288-151">Function Request</span></span>|<span data-ttu-id="c5288-152">函式 / [SCHEMA] / [FN_NAME]</span><span class="sxs-lookup"><span data-stu-id="c5288-152">Functions/[SCHEMA]/[FN_NAME]</span></span>|<span data-ttu-id="c5288-153">函式/SCOTT/FN_GETID</span><span class="sxs-lookup"><span data-stu-id="c5288-153">Functions/SCOTT/FN_GETID</span></span>|  
|<span data-ttu-id="c5288-154">函式的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-154">Function Response</span></span>|<span data-ttu-id="c5288-155">函式 / [SCHEMA] / [FN_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="c5288-155">Functions/[SCHEMA]/[FN_NAME]/response</span></span>|<span data-ttu-id="c5288-156">函式/SCOTT/FN_GETID/回應</span><span class="sxs-lookup"><span data-stu-id="c5288-156">Functions/SCOTT/FN_GETID/response</span></span>|  
|<span data-ttu-id="c5288-157">PL/SQL API 要求</span><span class="sxs-lookup"><span data-stu-id="c5288-157">PL/SQL API Request</span></span>|<span data-ttu-id="c5288-158">[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME]</span><span class="sxs-lookup"><span data-stu-id="c5288-158">[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]</span></span>|<span data-ttu-id="c5288-159">SCOTT/封裝/客戶/SP_INSERT</span><span class="sxs-lookup"><span data-stu-id="c5288-159">SCOTT/Package/CUSTOMER/SP_INSERT</span></span>|  
|<span data-ttu-id="c5288-160">封裝預存程序的回應</span><span class="sxs-lookup"><span data-stu-id="c5288-160">Packaged Stored Procedure Response</span></span>|<span data-ttu-id="c5288-161">[SCHEMA] /Package/ [PACKAGE_NAME] / [SP_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="c5288-161">[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response</span></span>|<span data-ttu-id="c5288-162">SCOTT/封裝/客戶/SP_INSERT/回應</span><span class="sxs-lookup"><span data-stu-id="c5288-162">SCOTT/Package/CUSTOMER/SP_INSERT/response</span></span>|  
|<span data-ttu-id="c5288-163">包裝函式要求</span><span class="sxs-lookup"><span data-stu-id="c5288-163">Packaged Function Request</span></span>|<span data-ttu-id="c5288-164">[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME]</span><span class="sxs-lookup"><span data-stu-id="c5288-164">[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]</span></span>|<span data-ttu-id="c5288-165">SCOTT/封裝/客戶/FN_GETID</span><span class="sxs-lookup"><span data-stu-id="c5288-165">SCOTT/Package/CUSTOMER/FN_GETID</span></span>|  
|<span data-ttu-id="c5288-166">回應封裝函式</span><span class="sxs-lookup"><span data-stu-id="c5288-166">Packaged Function Response</span></span>|<span data-ttu-id="c5288-167">[SCHEMA] /Package/ [PACKAGE_NAME] / [FN_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="c5288-167">[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response</span></span>|<span data-ttu-id="c5288-168">SCOTT/封裝/客戶/FN_GETID/回應</span><span class="sxs-lookup"><span data-stu-id="c5288-168">SCOTT/Package/CUSTOMER/FN_GETID/response</span></span>|  
|<span data-ttu-id="c5288-169">多載的預存程序要求</span><span class="sxs-lookup"><span data-stu-id="c5288-169">Overloaded Stored Procedure Request</span></span>|<span data-ttu-id="c5288-170">[SCHEMA] /Procedure/ [SP_NAME] / [多載]</span><span class="sxs-lookup"><span data-stu-id="c5288-170">[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]</span></span>|<span data-ttu-id="c5288-171">SCOTT/程序/SP_INSERT/overload1</span><span class="sxs-lookup"><span data-stu-id="c5288-171">SCOTT/Procedure/SP_INSERT/overload1</span></span>|  
|<span data-ttu-id="c5288-172">預存程序回應的多載</span><span class="sxs-lookup"><span data-stu-id="c5288-172">Overloaded Stored Procedure Response</span></span>|<span data-ttu-id="c5288-173">[SCHEMA] /Procedure/ [SP_NAME] / [多載] / 回應</span><span class="sxs-lookup"><span data-stu-id="c5288-173">[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response</span></span>|<span data-ttu-id="c5288-174">SCOTT/程序/SP_INSERT/overload1/回應</span><span class="sxs-lookup"><span data-stu-id="c5288-174">SCOTT/Procedure/SP_INSERT/overload1/response</span></span>|  
  
 <span data-ttu-id="c5288-175">實體描述：</span><span class="sxs-lookup"><span data-stu-id="c5288-175">Entity descriptions:</span></span>  
  
 <span data-ttu-id="c5288-176">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="c5288-176">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="c5288-177">[SP_NAME] = 預存程序的執行。例如，SP_INSERT。</span><span class="sxs-lookup"><span data-stu-id="c5288-177">[SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.</span></span>  
  
 <span data-ttu-id="c5288-178">[FN_NAME] = 要執行的函式例如，FN_GETID。</span><span class="sxs-lookup"><span data-stu-id="c5288-178">[FN_NAME] = The function to be executed; for example, FN_GETID.</span></span>  
  
 <span data-ttu-id="c5288-179">[PACKAGE_NAME] = 套件，其中包含目標的程序或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5288-179">[PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.</span></span>  
  
 <span data-ttu-id="c5288-180">[多載] = 多載的參數。</span><span class="sxs-lookup"><span data-stu-id="c5288-180">[OVERLOAD] = The Overload parameter.</span></span> <span data-ttu-id="c5288-181">可能的值為 overload1、 overload2，等等。</span><span class="sxs-lookup"><span data-stu-id="c5288-181">The possible values are overload1, overload2, and so on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5288-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5288-182">See Also</span></span>  
 [<span data-ttu-id="c5288-183">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="c5288-183">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)