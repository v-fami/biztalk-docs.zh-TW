---
title: Siebel 配接器中的 SiebelParameter 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelParameter
- Data Provider for Siebel, SiebelParameter
- SiebelParameter, supported properties and methods
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff2f0f5324dfacd118bc59dccfa524819acaa75
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021948"
---
# <a name="siebelparameter-class-in-the-siebel-adapter"></a><span data-ttu-id="1eaa6-102">Siebel 配接器中的 SiebelParameter 類別</span><span class="sxs-lookup"><span data-stu-id="1eaa6-102">SiebelParameter class in the Siebel adapter</span></span>
<span data-ttu-id="1eaa6-103">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供`DbParameter`實作，以啟用的 ADO.NET 用戶端，來指定特定命令的參數。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbParameter` implementation to enable an ADO.NET client to specify parameters for a particular command.</span></span> <span data-ttu-id="1eaa6-104">使用的執行個體`System.Data.Common.DbCommand`的類別[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，用戶端程式可以取得的執行個體`System.Data.Common.DbParameter`類別。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-104">Using an instance of the `System.Data.Common.DbCommand` class of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], a client program can obtain an instance of the `System.Data.Common.DbParameter` class.</span></span>  

```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  

 <span data-ttu-id="1eaa6-105">或者，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="1eaa6-105">Alternatively, the following approach can be used:</span></span>  

```  

//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  

 <span data-ttu-id="1eaa6-106">`SiebelParameter`類別繼承自`DbParameter`。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-106">The `SiebelParameter` class inherits from `DbParameter`.</span></span>  <span data-ttu-id="1eaa6-107">命名空間中存在`Microsoft.Data.SiebelClient`。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-107">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  

## <a name="supported-properties"></a><span data-ttu-id="1eaa6-108">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="1eaa6-108">Supported Properties</span></span>  
 <span data-ttu-id="1eaa6-109">`SiebelParameter`類別支援下列`DbParameter`*公用*屬性：</span><span class="sxs-lookup"><span data-stu-id="1eaa6-109">The `SiebelParameter` class supports the following `DbParameter`*public* properties:</span></span>  


|       <span data-ttu-id="1eaa6-110">[屬性]</span><span class="sxs-lookup"><span data-stu-id="1eaa6-110">Name</span></span>        |   <span data-ttu-id="1eaa6-111">取得或設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-111">Get/Set</span></span>   |                                                                                                            <span data-ttu-id="1eaa6-112">描述</span><span class="sxs-lookup"><span data-stu-id="1eaa6-112">Description</span></span>                                                                                                            |
|-------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <span data-ttu-id="1eaa6-113">**DbType**</span><span class="sxs-lookup"><span data-stu-id="1eaa6-113">**DbType**</span></span>     | <span data-ttu-id="1eaa6-114">取得和設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-114">Get and Set</span></span> |                                               <span data-ttu-id="1eaa6-115">參數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-115">Data type of the parameter.</span></span> <span data-ttu-id="1eaa6-116">請參閱[基本的 Siebel 資料類型](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-116">See [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>                                               |
|   <span data-ttu-id="1eaa6-117">**方向**</span><span class="sxs-lookup"><span data-stu-id="1eaa6-117">**Direction**</span></span>   | <span data-ttu-id="1eaa6-118">取得和設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-118">Get and Set</span></span> | <span data-ttu-id="1eaa6-119">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="1eaa6-119">The following values are supported:</span></span><br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput` |
|  <span data-ttu-id="1eaa6-120">**IsNullable**</span><span class="sxs-lookup"><span data-stu-id="1eaa6-120">**IsNullable**</span></span>   | <span data-ttu-id="1eaa6-121">取得和設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-121">Get and Set</span></span> |                                                                               <span data-ttu-id="1eaa6-122">屬性不支援，並將會擲回例外狀況，如果呼叫。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-122">The property is not supported, and will throw an exception if called.</span></span>                                                                               |
| <span data-ttu-id="1eaa6-123">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="1eaa6-123">**ParameterName**</span></span> | <span data-ttu-id="1eaa6-124">取得和設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-124">Get and Set</span></span> |                                  <span data-ttu-id="1eaa6-125">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援這個屬性來指定參數名稱的 ADO.NET 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-125">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports this property for an ADO.NET client to specify the parameter name.</span></span>                                  |
|     <span data-ttu-id="1eaa6-126">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="1eaa6-126">**Value**</span></span>     | <span data-ttu-id="1eaa6-127">取得和設定</span><span class="sxs-lookup"><span data-stu-id="1eaa6-127">Get and Set</span></span> |                                                    <span data-ttu-id="1eaa6-128">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]表示為字串的參數值。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-128">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] represents parameter values as strings.</span></span>                                                    |

###  <a name="BKMK_Datatypes"></a> <span data-ttu-id="1eaa6-129">支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="1eaa6-129">Supported Data Types</span></span>  
 <span data-ttu-id="1eaa6-130">下表摘要說明簡單 Siebel 欄位型別[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-130">The following table summarizes the simple Siebel field types that [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports.</span></span> <span data-ttu-id="1eaa6-131">如需詳細涵蓋範圍，請參閱[基本的 Siebel 資料型別](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-131">For more detailed coverage, see [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>  

|<span data-ttu-id="1eaa6-132">Siebel 欄位類型</span><span class="sxs-lookup"><span data-stu-id="1eaa6-132">Siebel Field Type</span></span>|<span data-ttu-id="1eaa6-133">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="1eaa6-133">.NET Type</span></span>|<span data-ttu-id="1eaa6-134">XML 結構描述類型</span><span class="sxs-lookup"><span data-stu-id="1eaa6-134">XML Schema Type</span></span>|  
|-----------------------|---------------|---------------------|  
|<span data-ttu-id="1eaa6-135">DTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="1eaa6-135">DTYPE_BOOL</span></span>|<span data-ttu-id="1eaa6-136">布林</span><span class="sxs-lookup"><span data-stu-id="1eaa6-136">Boolean</span></span>|<span data-ttu-id="1eaa6-137">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="1eaa6-137">xsd:boolean</span></span>|  
|<span data-ttu-id="1eaa6-138">DTYPE_CURRENCY</span><span class="sxs-lookup"><span data-stu-id="1eaa6-138">DTYPE_CURRENCY</span></span>|<span data-ttu-id="1eaa6-139">Decimal</span><span class="sxs-lookup"><span data-stu-id="1eaa6-139">Decimal</span></span>|<span data-ttu-id="1eaa6-140">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="1eaa6-140">xsd:decimal</span></span>|  
|<span data-ttu-id="1eaa6-141">DTYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="1eaa6-141">DTYPE_DATE</span></span>|<span data-ttu-id="1eaa6-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-142">DateTime</span></span>|<span data-ttu-id="1eaa6-143">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-143">xsd:dateTime</span></span>|  
|<span data-ttu-id="1eaa6-144">DTYPE_DATETIME</span><span class="sxs-lookup"><span data-stu-id="1eaa6-144">DTYPE_DATETIME</span></span>|<span data-ttu-id="1eaa6-145">DateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-145">DateTime</span></span>|<span data-ttu-id="1eaa6-146">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-146">xsd:dateTime</span></span>|  
|<span data-ttu-id="1eaa6-147">DTYPE_ UTCDATETIME</span><span class="sxs-lookup"><span data-stu-id="1eaa6-147">DTYPE_ UTCDATETIME</span></span>|<span data-ttu-id="1eaa6-148">DateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-148">DateTime</span></span>|<span data-ttu-id="1eaa6-149">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-149">xsd:dateTime</span></span>|  
|<span data-ttu-id="1eaa6-150">DTYPE_ID</span><span class="sxs-lookup"><span data-stu-id="1eaa6-150">DTYPE_ID</span></span>|<span data-ttu-id="1eaa6-151">String</span><span class="sxs-lookup"><span data-stu-id="1eaa6-151">String</span></span>|<span data-ttu-id="1eaa6-152">xsd:string</span><span class="sxs-lookup"><span data-stu-id="1eaa6-152">xsd:string</span></span>|  
|<span data-ttu-id="1eaa6-153">DTYPE_INTEGER</span><span class="sxs-lookup"><span data-stu-id="1eaa6-153">DTYPE_INTEGER</span></span>|<span data-ttu-id="1eaa6-154">Integer</span><span class="sxs-lookup"><span data-stu-id="1eaa6-154">Integer</span></span>|<span data-ttu-id="1eaa6-155">xsd:int</span><span class="sxs-lookup"><span data-stu-id="1eaa6-155">xsd:int</span></span>|  
|<span data-ttu-id="1eaa6-156">DTYPE_NOTE</span><span class="sxs-lookup"><span data-stu-id="1eaa6-156">DTYPE_NOTE</span></span>|<span data-ttu-id="1eaa6-157">String</span><span class="sxs-lookup"><span data-stu-id="1eaa6-157">String</span></span>|<span data-ttu-id="1eaa6-158">xsd:string</span><span class="sxs-lookup"><span data-stu-id="1eaa6-158">xsd:string</span></span>|  
|<span data-ttu-id="1eaa6-159">DTYPE_NUMBER</span><span class="sxs-lookup"><span data-stu-id="1eaa6-159">DTYPE_NUMBER</span></span>|<span data-ttu-id="1eaa6-160">Decimal</span><span class="sxs-lookup"><span data-stu-id="1eaa6-160">Decimal</span></span>|<span data-ttu-id="1eaa6-161">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="1eaa6-161">xsd:decimal</span></span>|  
|<span data-ttu-id="1eaa6-162">DTYPE_PHONE</span><span class="sxs-lookup"><span data-stu-id="1eaa6-162">DTYPE_PHONE</span></span>|<span data-ttu-id="1eaa6-163">String</span><span class="sxs-lookup"><span data-stu-id="1eaa6-163">String</span></span>|<span data-ttu-id="1eaa6-164">xsd:string</span><span class="sxs-lookup"><span data-stu-id="1eaa6-164">xsd:string</span></span>|  
|<span data-ttu-id="1eaa6-165">DTYPE_TEXT</span><span class="sxs-lookup"><span data-stu-id="1eaa6-165">DTYPE_TEXT</span></span>|<span data-ttu-id="1eaa6-166">String</span><span class="sxs-lookup"><span data-stu-id="1eaa6-166">String</span></span>|<span data-ttu-id="1eaa6-167">xsd:string</span><span class="sxs-lookup"><span data-stu-id="1eaa6-167">xsd:string</span></span>|  
|<span data-ttu-id="1eaa6-168">DTYPE_TIME</span><span class="sxs-lookup"><span data-stu-id="1eaa6-168">DTYPE_TIME</span></span>|<span data-ttu-id="1eaa6-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-169">DateTime</span></span>|<span data-ttu-id="1eaa6-170">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="1eaa6-170">xsd:dateTime</span></span>|  

## <a name="supported-methods"></a><span data-ttu-id="1eaa6-171">支援的方法</span><span class="sxs-lookup"><span data-stu-id="1eaa6-171">Supported Methods</span></span>  
 <span data-ttu-id="1eaa6-172">`SiebelParameter`類別不會覆寫中的任何特殊方法`DbParameter`。</span><span class="sxs-lookup"><span data-stu-id="1eaa6-172">The `SiebelParameter` class does not override any special methods in `DbParameter`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1eaa6-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1eaa6-173">See Also</span></span>  
 [<span data-ttu-id="1eaa6-174">使用 Siebel 配接器擴充 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="1eaa6-174">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)