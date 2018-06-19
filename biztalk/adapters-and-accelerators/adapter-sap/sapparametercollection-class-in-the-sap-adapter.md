---
title: SAP 配接器在 SAPParameterCollection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPParameterCollection, supported methods and classes
ms.assetid: fd09355b-95f4-4d49-a643-b13058e63d74
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 924cb884c64f337cec0e628c804b5c5a8c6cf37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218038"
---
# <a name="sapparametercollection-class-in-the-sap-adapter"></a><span data-ttu-id="e1035-102">SAP 配接器在 SAPParameterCollection 類別</span><span class="sxs-lookup"><span data-stu-id="e1035-102">SAPParameterCollection class in the SAP adapter</span></span>
<span data-ttu-id="e1035-103">下節列出方法和屬性的**SAPParameterCollection**類別。</span><span class="sxs-lookup"><span data-stu-id="e1035-103">The following section lists the methods and properties for the **SAPParameterCollection** class.</span></span> <span data-ttu-id="e1035-104">這衍生自**System.Data.Common.DbParameterCollection**。</span><span class="sxs-lookup"><span data-stu-id="e1035-104">This is derived from **System.Data.Common.DbParameterCollection**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="e1035-105">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="e1035-105">Supported Properties</span></span>  
  
|<span data-ttu-id="e1035-106">名稱</span><span class="sxs-lookup"><span data-stu-id="e1035-106">Name</span></span>|<span data-ttu-id="e1035-107">Get/Set</span><span class="sxs-lookup"><span data-stu-id="e1035-107">Get/Set</span></span>|<span data-ttu-id="e1035-108">Description</span><span class="sxs-lookup"><span data-stu-id="e1035-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="e1035-109">**Count**</span><span class="sxs-lookup"><span data-stu-id="e1035-109">**Count**</span></span>|<span data-ttu-id="e1035-110">Get</span><span class="sxs-lookup"><span data-stu-id="e1035-110">Get</span></span>|<span data-ttu-id="e1035-111">集合中的參數數目。</span><span class="sxs-lookup"><span data-stu-id="e1035-111">Number of parameters in the collection.</span></span>|  
|<span data-ttu-id="e1035-112">**IsFixedSize**</span><span class="sxs-lookup"><span data-stu-id="e1035-112">**IsFixedSize**</span></span>|<span data-ttu-id="e1035-113">Get</span><span class="sxs-lookup"><span data-stu-id="e1035-113">Get</span></span>|<span data-ttu-id="e1035-114">不支援。</span><span class="sxs-lookup"><span data-stu-id="e1035-114">Not supported.</span></span> <span data-ttu-id="e1035-115">傳回 false。</span><span class="sxs-lookup"><span data-stu-id="e1035-115">Returns false.</span></span>|  
|<span data-ttu-id="e1035-116">**IsReadOnly**</span><span class="sxs-lookup"><span data-stu-id="e1035-116">**IsReadOnly**</span></span>|<span data-ttu-id="e1035-117">Get</span><span class="sxs-lookup"><span data-stu-id="e1035-117">Get</span></span>|<span data-ttu-id="e1035-118">不支援。</span><span class="sxs-lookup"><span data-stu-id="e1035-118">Not supported.</span></span> <span data-ttu-id="e1035-119">傳回 false。</span><span class="sxs-lookup"><span data-stu-id="e1035-119">Returns false.</span></span>|  
|<span data-ttu-id="e1035-120">**IsSynchronized**</span><span class="sxs-lookup"><span data-stu-id="e1035-120">**IsSynchronized**</span></span>|<span data-ttu-id="e1035-121">Get</span><span class="sxs-lookup"><span data-stu-id="e1035-121">Get</span></span>|<span data-ttu-id="e1035-122">不支援。</span><span class="sxs-lookup"><span data-stu-id="e1035-122">Not supported.</span></span> <span data-ttu-id="e1035-123">傳回 false。</span><span class="sxs-lookup"><span data-stu-id="e1035-123">Returns false.</span></span>|  
|<span data-ttu-id="e1035-124">**Syncroot 同步**</span><span class="sxs-lookup"><span data-stu-id="e1035-124">**SyncRoot**</span></span>|<span data-ttu-id="e1035-125">Get</span><span class="sxs-lookup"><span data-stu-id="e1035-125">Get</span></span>|<span data-ttu-id="e1035-126">傳回之鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="e1035-126">Returns the lock object.</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="e1035-127">支援的方法</span><span class="sxs-lookup"><span data-stu-id="e1035-127">Supported Methods</span></span>  
  
|<span data-ttu-id="e1035-128">名稱</span><span class="sxs-lookup"><span data-stu-id="e1035-128">Name</span></span>|<span data-ttu-id="e1035-129">Description</span><span class="sxs-lookup"><span data-stu-id="e1035-129">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e1035-130">**Add(SAPParameter)**</span><span class="sxs-lookup"><span data-stu-id="e1035-130">**Add(SAPParameter)**</span></span>|<span data-ttu-id="e1035-131">參數不能屬於多個 ParameterCollection。</span><span class="sxs-lookup"><span data-stu-id="e1035-131">Parameter cannot belong to more than one ParameterCollection.</span></span>|  
|<span data-ttu-id="e1035-132">**Add （object)**</span><span class="sxs-lookup"><span data-stu-id="e1035-132">**Add(object)**</span></span>|<span data-ttu-id="e1035-133">物件應該是 SAPParameter 型別。</span><span class="sxs-lookup"><span data-stu-id="e1035-133">Object should be of SAPParameter type.</span></span>|  
|<span data-ttu-id="e1035-134">**AddRange(System.Array)**</span><span class="sxs-lookup"><span data-stu-id="e1035-134">**AddRange(System.Array)**</span></span>|<span data-ttu-id="e1035-135">將 SAPParameter 執行個體的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1035-135">Adds an array of SAPParameter instances.</span></span>|  
|<span data-ttu-id="e1035-136">**Clear （)**</span><span class="sxs-lookup"><span data-stu-id="e1035-136">**Clear()**</span></span>|<span data-ttu-id="e1035-137">清除集合中的參數。</span><span class="sxs-lookup"><span data-stu-id="e1035-137">Clears the parameters in the collection.</span></span>|  
|<span data-ttu-id="e1035-138">**Contains(object)**</span><span class="sxs-lookup"><span data-stu-id="e1035-138">**Contains(object)**</span></span>|<span data-ttu-id="e1035-139">檢查根據參數執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1035-139">Checks based on parameter instance.</span></span>|  
|<span data-ttu-id="e1035-140">**Contains(string)**</span><span class="sxs-lookup"><span data-stu-id="e1035-140">**Contains(string)**</span></span>|<span data-ttu-id="e1035-141">參數名稱為基礎的檢查。</span><span class="sxs-lookup"><span data-stu-id="e1035-141">Checks based on parameter name.</span></span>|  
|<span data-ttu-id="e1035-142">**CopyTo （SAPParameter []，int）**</span><span class="sxs-lookup"><span data-stu-id="e1035-142">**CopyTo(SAPParameter[], int)**</span></span>|<span data-ttu-id="e1035-143">複製 SAPParameter 型別的陣列以參數清單。</span><span class="sxs-lookup"><span data-stu-id="e1035-143">Copies parameter list to an array of SAPParameter types.</span></span>|  
|<span data-ttu-id="e1035-144">**CopyTo (System.Array，int)**</span><span class="sxs-lookup"><span data-stu-id="e1035-144">**CopyTo(System.Array, int)**</span></span>|<span data-ttu-id="e1035-145">複製到陣列的參數清單。</span><span class="sxs-lookup"><span data-stu-id="e1035-145">Copies parameter list to an array.</span></span>|  
|<span data-ttu-id="e1035-146">**GetEnumerator()**</span><span class="sxs-lookup"><span data-stu-id="e1035-146">**GetEnumerator()**</span></span>|<span data-ttu-id="e1035-147">集合中取得參數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e1035-147">Gets an enumerator for the parameters in the collection.</span></span>|  
|<span data-ttu-id="e1035-148">**IndexOf(object)**</span><span class="sxs-lookup"><span data-stu-id="e1035-148">**IndexOf(object)**</span></span>|<span data-ttu-id="e1035-149">依據 SAPParameter 執行個體的參數索引。</span><span class="sxs-lookup"><span data-stu-id="e1035-149">Index of parameter based on SAPParameter instance.</span></span>|  
|<span data-ttu-id="e1035-150">**IndexOf(string)**</span><span class="sxs-lookup"><span data-stu-id="e1035-150">**IndexOf(string)**</span></span>|<span data-ttu-id="e1035-151">參數以 SAPParameter 名稱為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="e1035-151">Index of parameter based on SAPParameter name.</span></span>|  
|<span data-ttu-id="e1035-152">**插入 （int，object）**</span><span class="sxs-lookup"><span data-stu-id="e1035-152">**Insert(int, object)**</span></span>|<span data-ttu-id="e1035-153">將 SAPParameter 插入至集合。</span><span class="sxs-lookup"><span data-stu-id="e1035-153">Inserts an SAPParameter into the collection.</span></span>|  
|<span data-ttu-id="e1035-154">**Remove(object)**</span><span class="sxs-lookup"><span data-stu-id="e1035-154">**Remove(object)**</span></span>|<span data-ttu-id="e1035-155">移除 SAPParameter 到根據執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="e1035-155">Removes an SAPParameter into the collection based on instance.</span></span>|  
|<span data-ttu-id="e1035-156">**RemoveAt(int)**</span><span class="sxs-lookup"><span data-stu-id="e1035-156">**RemoveAt(int)**</span></span>|<span data-ttu-id="e1035-157">集合中指定索引處移除 SAPParameter。</span><span class="sxs-lookup"><span data-stu-id="e1035-157">Removes an SAPParameter into the collection at a given index.</span></span>|  
|<span data-ttu-id="e1035-158">**RemoveAt(string)**</span><span class="sxs-lookup"><span data-stu-id="e1035-158">**RemoveAt(string)**</span></span>|<span data-ttu-id="e1035-159">移除 SAPParameter 至名稱為基礎的集合。</span><span class="sxs-lookup"><span data-stu-id="e1035-159">Removes an SAPParameter into the collection based on name.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1035-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1035-160">See Also</span></span>  
 [<span data-ttu-id="e1035-161">SAP 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="e1035-161">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)