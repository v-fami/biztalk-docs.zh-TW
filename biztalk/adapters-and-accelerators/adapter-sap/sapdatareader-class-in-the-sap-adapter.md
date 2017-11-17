---
title: "SAP 配接器在 SAPDataReader 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPDataReader, supported methods and classes
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe658058b6d00b4a22b333ef5683a285b9cab3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapdatareader-class-in-the-sap-adapter"></a><span data-ttu-id="edf5f-102">SAP 配接器在 SAPDataReader 類別</span><span class="sxs-lookup"><span data-stu-id="edf5f-102">SAPDataReader class in the SAP adapter</span></span>
<span data-ttu-id="edf5f-103">下節列出方法和屬性的**SAPDataReader**類別。</span><span class="sxs-lookup"><span data-stu-id="edf5f-103">The following section lists the methods and properties for the **SAPDataReader** class.</span></span> <span data-ttu-id="edf5f-104">這衍生自**System.Data.Common.DbDataReader**。</span><span class="sxs-lookup"><span data-stu-id="edf5f-104">This is derived from **System.Data.Common.DbDataReader**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="edf5f-105">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="edf5f-105">Supported Properties</span></span>  
  
|<span data-ttu-id="edf5f-106">名稱</span><span class="sxs-lookup"><span data-stu-id="edf5f-106">Name</span></span>|<span data-ttu-id="edf5f-107">Get/Set</span><span class="sxs-lookup"><span data-stu-id="edf5f-107">Get/Set</span></span>|<span data-ttu-id="edf5f-108">Description</span><span class="sxs-lookup"><span data-stu-id="edf5f-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="edf5f-109">**深度**</span><span class="sxs-lookup"><span data-stu-id="edf5f-109">**Depth**</span></span>|<span data-ttu-id="edf5f-110">Get</span><span class="sxs-lookup"><span data-stu-id="edf5f-110">Get</span></span>|<span data-ttu-id="edf5f-111">不支援。</span><span class="sxs-lookup"><span data-stu-id="edf5f-111">Not supported.</span></span> <span data-ttu-id="edf5f-112">傳回 0。</span><span class="sxs-lookup"><span data-stu-id="edf5f-112">Returns 0.</span></span>|  
|<span data-ttu-id="edf5f-113">**FieldCount**</span><span class="sxs-lookup"><span data-stu-id="edf5f-113">**FieldCount**</span></span>|<span data-ttu-id="edf5f-114">Get</span><span class="sxs-lookup"><span data-stu-id="edf5f-114">Get</span></span>|<span data-ttu-id="edf5f-115">目前的記錄組中的欄位數目</span><span class="sxs-lookup"><span data-stu-id="edf5f-115">Number of fields in the current record set</span></span>|  
|<span data-ttu-id="edf5f-116">**IsClosed**</span><span class="sxs-lookup"><span data-stu-id="edf5f-116">**IsClosed**</span></span>|<span data-ttu-id="edf5f-117">Get</span><span class="sxs-lookup"><span data-stu-id="edf5f-117">Get</span></span>|<span data-ttu-id="edf5f-118">傳回資料讀取器的狀態</span><span class="sxs-lookup"><span data-stu-id="edf5f-118">Returns status of data reader</span></span>|  
|<span data-ttu-id="edf5f-119">**RecordsAffected**</span><span class="sxs-lookup"><span data-stu-id="edf5f-119">**RecordsAffected**</span></span>|<span data-ttu-id="edf5f-120">Get</span><span class="sxs-lookup"><span data-stu-id="edf5f-120">Get</span></span>|<span data-ttu-id="edf5f-121">不支援。</span><span class="sxs-lookup"><span data-stu-id="edf5f-121">Not supported.</span></span> <span data-ttu-id="edf5f-122">會傳回-1</span><span class="sxs-lookup"><span data-stu-id="edf5f-122">Returns -1</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="edf5f-123">支援的方法</span><span class="sxs-lookup"><span data-stu-id="edf5f-123">Supported Methods</span></span>  
  
|<span data-ttu-id="edf5f-124">名稱</span><span class="sxs-lookup"><span data-stu-id="edf5f-124">Name</span></span>|<span data-ttu-id="edf5f-125">Description</span><span class="sxs-lookup"><span data-stu-id="edf5f-125">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="edf5f-126">**Close （)**</span><span class="sxs-lookup"><span data-stu-id="edf5f-126">**Close()**</span></span>|<span data-ttu-id="edf5f-127">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="edf5f-127">Closes the DataReader</span></span>|  
|<span data-ttu-id="edf5f-128">**取得 [方法]**<sup>*</sup></span><span class="sxs-lookup"><span data-stu-id="edf5f-128">**Get [methods]** <sup>*</sup></span></span><br /><br /> <span data-ttu-id="edf5f-129">在 [方法] 是預期的資料類型。</span><span class="sxs-lookup"><span data-stu-id="edf5f-129">where [methods] is the expected data type.</span></span> <span data-ttu-id="edf5f-130">例如</span><span class="sxs-lookup"><span data-stu-id="edf5f-130">E.g.</span></span> <span data-ttu-id="edf5f-131">GetInt32(int)</span><span class="sxs-lookup"><span data-stu-id="edf5f-131">GetInt32(int)</span></span>|<span data-ttu-id="edf5f-132">取得預期的資料類型為基礎的資料行值</span><span class="sxs-lookup"><span data-stu-id="edf5f-132">Gets column value based on the data type expected</span></span>|  
|<span data-ttu-id="edf5f-133">**IsDBNull(int)**</span><span class="sxs-lookup"><span data-stu-id="edf5f-133">**IsDBNull(int)**</span></span>|<span data-ttu-id="edf5f-134">不支援。</span><span class="sxs-lookup"><span data-stu-id="edf5f-134">Not supported.</span></span> <span data-ttu-id="edf5f-135">傳回 false。</span><span class="sxs-lookup"><span data-stu-id="edf5f-135">Returns false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edf5f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edf5f-136">See Also</span></span>  
 [<span data-ttu-id="edf5f-137">SAP 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="edf5f-137">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)