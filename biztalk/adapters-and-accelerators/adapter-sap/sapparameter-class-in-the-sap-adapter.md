---
title: "SAP 配接器在 SAPParameter 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPParameter, supported methods, classes, and constructors
ms.assetid: 60053393-ad22-4c99-abae-e538d43c8e18
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ff43c344cc14adb3deef226c270adc3ca94f2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapparameter-class-in-the-sap-adapter"></a><span data-ttu-id="04e81-102">SAP 配接器在 SAPParameter 類別</span><span class="sxs-lookup"><span data-stu-id="04e81-102">SAPParameter class in the SAP adapter</span></span>
<span data-ttu-id="04e81-103">下節列出方法和屬性的**SAPParameter**類別。</span><span class="sxs-lookup"><span data-stu-id="04e81-103">The following section lists the methods and properties for the **SAPParameter** class.</span></span> <span data-ttu-id="04e81-104">這衍生自**System.Data.Common.DbParameter**。</span><span class="sxs-lookup"><span data-stu-id="04e81-104">This is derived from **System.Data.Common.DbParameter**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="04e81-105">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="04e81-105">Supported Properties</span></span>  
  
|<span data-ttu-id="04e81-106">名稱</span><span class="sxs-lookup"><span data-stu-id="04e81-106">Name</span></span>|<span data-ttu-id="04e81-107">Get/Set</span><span class="sxs-lookup"><span data-stu-id="04e81-107">Get/Set</span></span>|<span data-ttu-id="04e81-108">Description</span><span class="sxs-lookup"><span data-stu-id="04e81-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="04e81-109">**DbType**</span><span class="sxs-lookup"><span data-stu-id="04e81-109">**DbType**</span></span>|<span data-ttu-id="04e81-110">Get</span><span class="sxs-lookup"><span data-stu-id="04e81-110">Get</span></span>|<span data-ttu-id="04e81-111">如果傳回參數的 DbType。</span><span class="sxs-lookup"><span data-stu-id="04e81-111">DbType if the parameter returned.</span></span> <span data-ttu-id="04e81-112">無法設定。</span><span class="sxs-lookup"><span data-stu-id="04e81-112">Cannot be set.</span></span>|  
|<span data-ttu-id="04e81-113">**方向**</span><span class="sxs-lookup"><span data-stu-id="04e81-113">**Direction**</span></span>|<span data-ttu-id="04e81-114">取得和設定</span><span class="sxs-lookup"><span data-stu-id="04e81-114">Get and Set</span></span>|<span data-ttu-id="04e81-115">不支援 ParameterDirection.ReturnValue。</span><span class="sxs-lookup"><span data-stu-id="04e81-115">ParameterDirection.ReturnValue not supported.</span></span>|  
|<span data-ttu-id="04e81-116">**IsNullable**</span><span class="sxs-lookup"><span data-stu-id="04e81-116">**IsNullable**</span></span>|-|<span data-ttu-id="04e81-117">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-117">Not supported.</span></span>|  
|<span data-ttu-id="04e81-118">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="04e81-118">**ParameterName**</span></span>|<span data-ttu-id="04e81-119">取得和設定</span><span class="sxs-lookup"><span data-stu-id="04e81-119">Get and Set</span></span>|<span data-ttu-id="04e81-120">參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="04e81-120">Name of the parameter.</span></span>|  
|<span data-ttu-id="04e81-121">**大小**</span><span class="sxs-lookup"><span data-stu-id="04e81-121">**Size**</span></span>|-|<span data-ttu-id="04e81-122">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-122">Not supported.</span></span>|  
|<span data-ttu-id="04e81-123">**SourceColumn**</span><span class="sxs-lookup"><span data-stu-id="04e81-123">**SourceColumn**</span></span>|-|<span data-ttu-id="04e81-124">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-124">Not supported.</span></span>|  
|<span data-ttu-id="04e81-125">**SourceColumnNullMapping**</span><span class="sxs-lookup"><span data-stu-id="04e81-125">**SourceColumnNullMapping**</span></span>|-|<span data-ttu-id="04e81-126">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-126">Not supported.</span></span>|  
|<span data-ttu-id="04e81-127">**SourceVersion**</span><span class="sxs-lookup"><span data-stu-id="04e81-127">**SourceVersion**</span></span>|-|<span data-ttu-id="04e81-128">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-128">Not supported.</span></span>|  
|<span data-ttu-id="04e81-129">**值**</span><span class="sxs-lookup"><span data-stu-id="04e81-129">**Value**</span></span>|<span data-ttu-id="04e81-130">取得和設定</span><span class="sxs-lookup"><span data-stu-id="04e81-130">Get and Set</span></span>|<span data-ttu-id="04e81-131">參數的值</span><span class="sxs-lookup"><span data-stu-id="04e81-131">Value of the parameter</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="04e81-132">支援的方法</span><span class="sxs-lookup"><span data-stu-id="04e81-132">Supported Methods</span></span>  
  
|<span data-ttu-id="04e81-133">名稱</span><span class="sxs-lookup"><span data-stu-id="04e81-133">Name</span></span>|<span data-ttu-id="04e81-134">Description</span><span class="sxs-lookup"><span data-stu-id="04e81-134">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="04e81-135">**ResetDbType()**</span><span class="sxs-lookup"><span data-stu-id="04e81-135">**ResetDbType()**</span></span>|<span data-ttu-id="04e81-136">不支援。</span><span class="sxs-lookup"><span data-stu-id="04e81-136">Not supported.</span></span>|  
  
## <a name="supported-constructors"></a><span data-ttu-id="04e81-137">支援的建構函式</span><span class="sxs-lookup"><span data-stu-id="04e81-137">Supported Constructors</span></span>  
  
|<span data-ttu-id="04e81-138">名稱</span><span class="sxs-lookup"><span data-stu-id="04e81-138">Name</span></span>|<span data-ttu-id="04e81-139">Description</span><span class="sxs-lookup"><span data-stu-id="04e81-139">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="04e81-140">**SAPParameter()**</span><span class="sxs-lookup"><span data-stu-id="04e81-140">**SAPParameter()**</span></span>|<span data-ttu-id="04e81-141">SAP 參數執行個體。</span><span class="sxs-lookup"><span data-stu-id="04e81-141">SAP parameter instance.</span></span>|  
|<span data-ttu-id="04e81-142">**SAPParameter(string)**</span><span class="sxs-lookup"><span data-stu-id="04e81-142">**SAPParameter(string)**</span></span>|<span data-ttu-id="04e81-143">SAP 與 SAP 的參數名稱的參數。</span><span class="sxs-lookup"><span data-stu-id="04e81-143">SAP parameter with SAP parameter name.</span></span>|  
|<span data-ttu-id="04e81-144">**SAPParameter （字串、 DbType）**</span><span class="sxs-lookup"><span data-stu-id="04e81-144">**SAPParameter(string, DbType)**</span></span>|<span data-ttu-id="04e81-145">SAP DbType 與 SAP 參數名稱的參數。</span><span class="sxs-lookup"><span data-stu-id="04e81-145">SAP parameter with SAP parameter name and DbType.</span></span>|  
|<span data-ttu-id="04e81-146">**SAPParameter （字串、 物件）**</span><span class="sxs-lookup"><span data-stu-id="04e81-146">**SAPParameter(string, object)**</span></span>|<span data-ttu-id="04e81-147">SAP 與 SAP 參數名稱和值的參數。</span><span class="sxs-lookup"><span data-stu-id="04e81-147">SAP parameter with SAP parameter name and value.</span></span> <span data-ttu-id="04e81-148">複雜型別具有值的類型 DataTable 和 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="04e81-148">Complex types have value of type DataTable and XML string.</span></span>|  
|<span data-ttu-id="04e81-149">**SAPParameter （字串、 ParameterDirection）**</span><span class="sxs-lookup"><span data-stu-id="04e81-149">**SAPParameter(string, ParameterDirection)**</span></span>|<span data-ttu-id="04e81-150">SAP 參數與 SAP 參數名稱和參數方向。</span><span class="sxs-lookup"><span data-stu-id="04e81-150">SAP parameter with SAP parameter name and parameter direction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04e81-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04e81-151">See Also</span></span>  
 [<span data-ttu-id="04e81-152">SAP 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="04e81-152">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)