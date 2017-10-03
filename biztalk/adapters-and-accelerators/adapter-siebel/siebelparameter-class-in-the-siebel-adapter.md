---
title: "Siebel 配接器中的 SiebelParameter 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelParameter
- Data Provider for Siebel, SiebelParameter
- SiebelParameter, supported properties and methods
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27df4b207b23cd04f7d29a2a18ec4ab032836e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="siebelparameter-class-in-the-siebel-adapter"></a><span data-ttu-id="d5934-102">Siebel 配接器中 SiebelParameter 類別</span><span class="sxs-lookup"><span data-stu-id="d5934-102">SiebelParameter class in the Siebel adapter</span></span>
<span data-ttu-id="d5934-103">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供`DbParameter`實作，以啟用 ADO.NET 用戶端，以指定特定命令的參數。</span><span class="sxs-lookup"><span data-stu-id="d5934-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbParameter` implementation to enable an ADO.NET client to specify parameters for a particular command.</span></span> <span data-ttu-id="d5934-104">使用的執行個體`System.Data.Common.DbCommand`類別[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，用戶端程式可以取得的執行個體`System.Data.Common.DbParameter`類別。</span><span class="sxs-lookup"><span data-stu-id="d5934-104">Using an instance of the `System.Data.Common.DbCommand` class of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], a client program can obtain an instance of the `System.Data.Common.DbParameter` class.</span></span>  
  
```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  
  
 <span data-ttu-id="d5934-105">或者，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="d5934-105">Alternatively, the following approach can be used:</span></span>  
  
```  
  
//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  
  
 <span data-ttu-id="d5934-106">`SiebelParameter`類別繼承自`DbParameter`。</span><span class="sxs-lookup"><span data-stu-id="d5934-106">The `SiebelParameter` class inherits from `DbParameter`.</span></span>  <span data-ttu-id="d5934-107">命名空間中存在`Microsoft.Data.SiebelClient`。</span><span class="sxs-lookup"><span data-stu-id="d5934-107">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="d5934-108">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="d5934-108">Supported Properties</span></span>  
 <span data-ttu-id="d5934-109">`SiebelParameter`類別支援下列`DbParameter`*公用*屬性：</span><span class="sxs-lookup"><span data-stu-id="d5934-109">The `SiebelParameter` class supports the following `DbParameter`*public* properties:</span></span>  
  
|<span data-ttu-id="d5934-110">名稱</span><span class="sxs-lookup"><span data-stu-id="d5934-110">Name</span></span>|<span data-ttu-id="d5934-111">Get/Set</span><span class="sxs-lookup"><span data-stu-id="d5934-111">Get/Set</span></span>|<span data-ttu-id="d5934-112">Description</span><span class="sxs-lookup"><span data-stu-id="d5934-112">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="d5934-113">**DbType**</span><span class="sxs-lookup"><span data-stu-id="d5934-113">**DbType**</span></span>|<span data-ttu-id="d5934-114">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d5934-114">Get and Set</span></span>|<span data-ttu-id="d5934-115">資料型別參數。</span><span class="sxs-lookup"><span data-stu-id="d5934-115">Data type of the parameter.</span></span> <span data-ttu-id="d5934-116">請參閱[基本的 Siebel 資料型別](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d5934-116">See [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>|  
|<span data-ttu-id="d5934-117">**方向**</span><span class="sxs-lookup"><span data-stu-id="d5934-117">**Direction**</span></span>|<span data-ttu-id="d5934-118">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d5934-118">Get and Set</span></span>|<span data-ttu-id="d5934-119">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="d5934-119">The following values are supported:</span></span><br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput`|  
|<span data-ttu-id="d5934-120">**IsNullable**</span><span class="sxs-lookup"><span data-stu-id="d5934-120">**IsNullable**</span></span>|<span data-ttu-id="d5934-121">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d5934-121">Get and Set</span></span>|<span data-ttu-id="d5934-122">屬性不支援，如果呼叫將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d5934-122">The property is not supported, and will throw an exception if called.</span></span>|  
|<span data-ttu-id="d5934-123">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="d5934-123">**ParameterName**</span></span>|<span data-ttu-id="d5934-124">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d5934-124">Get and Set</span></span>|<span data-ttu-id="d5934-125">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援指定的參數名稱的 ADO.NET 用戶端的這個屬性。</span><span class="sxs-lookup"><span data-stu-id="d5934-125">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports this property for an ADO.NET client to specify the parameter name.</span></span>|  
|<span data-ttu-id="d5934-126">**值**</span><span class="sxs-lookup"><span data-stu-id="d5934-126">**Value**</span></span>|<span data-ttu-id="d5934-127">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d5934-127">Get and Set</span></span>|<span data-ttu-id="d5934-128">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]表示為字串的參數值。</span><span class="sxs-lookup"><span data-stu-id="d5934-128">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] represents parameter values as strings.</span></span>|  
  
###  <span data-ttu-id="d5934-129"><a name="BKMK_Datatypes"></a>支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="d5934-129"><a name="BKMK_Datatypes"></a> Supported Data Types</span></span>  
 <span data-ttu-id="d5934-130">下表摘要說明簡單的 Siebel 欄位類型[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援。</span><span class="sxs-lookup"><span data-stu-id="d5934-130">The following table summarizes the simple Siebel field types that [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports.</span></span> <span data-ttu-id="d5934-131">如需詳細涵蓋範圍，請參閱[基本的 Siebel 資料型別](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d5934-131">For more detailed coverage, see [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>  
  
|<span data-ttu-id="d5934-132">Siebel 欄位類型</span><span class="sxs-lookup"><span data-stu-id="d5934-132">Siebel Field Type</span></span>|<span data-ttu-id="d5934-133">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="d5934-133">.NET Type</span></span>|<span data-ttu-id="d5934-134">XML 結構描述類型</span><span class="sxs-lookup"><span data-stu-id="d5934-134">XML Schema Type</span></span>|  
|-----------------------|---------------|---------------------|  
|<span data-ttu-id="d5934-135">DTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="d5934-135">DTYPE_BOOL</span></span>|<span data-ttu-id="d5934-136">布林</span><span class="sxs-lookup"><span data-stu-id="d5934-136">Boolean</span></span>|<span data-ttu-id="d5934-137">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="d5934-137">xsd:boolean</span></span>|  
|<span data-ttu-id="d5934-138">DTYPE_CURRENCY</span><span class="sxs-lookup"><span data-stu-id="d5934-138">DTYPE_CURRENCY</span></span>|<span data-ttu-id="d5934-139">Decimal</span><span class="sxs-lookup"><span data-stu-id="d5934-139">Decimal</span></span>|<span data-ttu-id="d5934-140">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="d5934-140">xsd:decimal</span></span>|  
|<span data-ttu-id="d5934-141">DTYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="d5934-141">DTYPE_DATE</span></span>|<span data-ttu-id="d5934-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-142">DateTime</span></span>|<span data-ttu-id="d5934-143">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-143">xsd:dateTime</span></span>|  
|<span data-ttu-id="d5934-144">DTYPE_DATETIME</span><span class="sxs-lookup"><span data-stu-id="d5934-144">DTYPE_DATETIME</span></span>|<span data-ttu-id="d5934-145">DateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-145">DateTime</span></span>|<span data-ttu-id="d5934-146">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-146">xsd:dateTime</span></span>|  
|<span data-ttu-id="d5934-147">DTYPE_ UTCDATETIME</span><span class="sxs-lookup"><span data-stu-id="d5934-147">DTYPE_ UTCDATETIME</span></span>|<span data-ttu-id="d5934-148">DateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-148">DateTime</span></span>|<span data-ttu-id="d5934-149">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-149">xsd:dateTime</span></span>|  
|<span data-ttu-id="d5934-150">DTYPE_ID</span><span class="sxs-lookup"><span data-stu-id="d5934-150">DTYPE_ID</span></span>|<span data-ttu-id="d5934-151">字串</span><span class="sxs-lookup"><span data-stu-id="d5934-151">String</span></span>|<span data-ttu-id="d5934-152">xsd:string</span><span class="sxs-lookup"><span data-stu-id="d5934-152">xsd:string</span></span>|  
|<span data-ttu-id="d5934-153">DTYPE_INTEGER</span><span class="sxs-lookup"><span data-stu-id="d5934-153">DTYPE_INTEGER</span></span>|<span data-ttu-id="d5934-154">Integer</span><span class="sxs-lookup"><span data-stu-id="d5934-154">Integer</span></span>|<span data-ttu-id="d5934-155">xsd:int</span><span class="sxs-lookup"><span data-stu-id="d5934-155">xsd:int</span></span>|  
|<span data-ttu-id="d5934-156">DTYPE_NOTE</span><span class="sxs-lookup"><span data-stu-id="d5934-156">DTYPE_NOTE</span></span>|<span data-ttu-id="d5934-157">字串</span><span class="sxs-lookup"><span data-stu-id="d5934-157">String</span></span>|<span data-ttu-id="d5934-158">xsd:string</span><span class="sxs-lookup"><span data-stu-id="d5934-158">xsd:string</span></span>|  
|<span data-ttu-id="d5934-159">DTYPE_NUMBER</span><span class="sxs-lookup"><span data-stu-id="d5934-159">DTYPE_NUMBER</span></span>|<span data-ttu-id="d5934-160">Decimal</span><span class="sxs-lookup"><span data-stu-id="d5934-160">Decimal</span></span>|<span data-ttu-id="d5934-161">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="d5934-161">xsd:decimal</span></span>|  
|<span data-ttu-id="d5934-162">DTYPE_PHONE</span><span class="sxs-lookup"><span data-stu-id="d5934-162">DTYPE_PHONE</span></span>|<span data-ttu-id="d5934-163">字串</span><span class="sxs-lookup"><span data-stu-id="d5934-163">String</span></span>|<span data-ttu-id="d5934-164">xsd:string</span><span class="sxs-lookup"><span data-stu-id="d5934-164">xsd:string</span></span>|  
|<span data-ttu-id="d5934-165">DTYPE_TEXT</span><span class="sxs-lookup"><span data-stu-id="d5934-165">DTYPE_TEXT</span></span>|<span data-ttu-id="d5934-166">字串</span><span class="sxs-lookup"><span data-stu-id="d5934-166">String</span></span>|<span data-ttu-id="d5934-167">xsd:string</span><span class="sxs-lookup"><span data-stu-id="d5934-167">xsd:string</span></span>|  
|<span data-ttu-id="d5934-168">DTYPE_TIME</span><span class="sxs-lookup"><span data-stu-id="d5934-168">DTYPE_TIME</span></span>|<span data-ttu-id="d5934-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-169">DateTime</span></span>|<span data-ttu-id="d5934-170">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="d5934-170">xsd:dateTime</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="d5934-171">支援的方法</span><span class="sxs-lookup"><span data-stu-id="d5934-171">Supported Methods</span></span>  
 <span data-ttu-id="d5934-172">`SiebelParameter`類別不會覆寫中的任何特殊方法`DbParameter`。</span><span class="sxs-lookup"><span data-stu-id="d5934-172">The `SiebelParameter` class does not override any special methods in `DbParameter`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5934-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5934-173">See Also</span></span>  
 [<span data-ttu-id="d5934-174">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="d5934-174">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)