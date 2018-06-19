---
title: SAP 配接器在 SAPDataReader 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPDataReader, supported methods and classes
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe658058b6d00b4a22b333ef5683a285b9cab3
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22217310"
---
# <a name="sapdatareader-class-in-the-sap-adapter"></a><span data-ttu-id="55cbd-102">SAP 配接器在 SAPDataReader 類別</span><span class="sxs-lookup"><span data-stu-id="55cbd-102">SAPDataReader class in the SAP adapter</span></span>
<span data-ttu-id="55cbd-103">下節列出方法和屬性的**SAPDataReader**類別。</span><span class="sxs-lookup"><span data-stu-id="55cbd-103">The following section lists the methods and properties for the **SAPDataReader** class.</span></span> <span data-ttu-id="55cbd-104">這衍生自**System.Data.Common.DbDataReader**。</span><span class="sxs-lookup"><span data-stu-id="55cbd-104">This is derived from **System.Data.Common.DbDataReader**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="55cbd-105">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="55cbd-105">Supported Properties</span></span>  
  
|<span data-ttu-id="55cbd-106">名稱</span><span class="sxs-lookup"><span data-stu-id="55cbd-106">Name</span></span>|<span data-ttu-id="55cbd-107">Get/Set</span><span class="sxs-lookup"><span data-stu-id="55cbd-107">Get/Set</span></span>|<span data-ttu-id="55cbd-108">Description</span><span class="sxs-lookup"><span data-stu-id="55cbd-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="55cbd-109">**深度**</span><span class="sxs-lookup"><span data-stu-id="55cbd-109">**Depth**</span></span>|<span data-ttu-id="55cbd-110">Get</span><span class="sxs-lookup"><span data-stu-id="55cbd-110">Get</span></span>|<span data-ttu-id="55cbd-111">不支援。</span><span class="sxs-lookup"><span data-stu-id="55cbd-111">Not supported.</span></span> <span data-ttu-id="55cbd-112">傳回 0。</span><span class="sxs-lookup"><span data-stu-id="55cbd-112">Returns 0.</span></span>|  
|<span data-ttu-id="55cbd-113">**FieldCount**</span><span class="sxs-lookup"><span data-stu-id="55cbd-113">**FieldCount**</span></span>|<span data-ttu-id="55cbd-114">Get</span><span class="sxs-lookup"><span data-stu-id="55cbd-114">Get</span></span>|<span data-ttu-id="55cbd-115">目前的記錄組中的欄位數目</span><span class="sxs-lookup"><span data-stu-id="55cbd-115">Number of fields in the current record set</span></span>|  
|<span data-ttu-id="55cbd-116">**IsClosed**</span><span class="sxs-lookup"><span data-stu-id="55cbd-116">**IsClosed**</span></span>|<span data-ttu-id="55cbd-117">Get</span><span class="sxs-lookup"><span data-stu-id="55cbd-117">Get</span></span>|<span data-ttu-id="55cbd-118">傳回資料讀取器的狀態</span><span class="sxs-lookup"><span data-stu-id="55cbd-118">Returns status of data reader</span></span>|  
|<span data-ttu-id="55cbd-119">**RecordsAffected**</span><span class="sxs-lookup"><span data-stu-id="55cbd-119">**RecordsAffected**</span></span>|<span data-ttu-id="55cbd-120">Get</span><span class="sxs-lookup"><span data-stu-id="55cbd-120">Get</span></span>|<span data-ttu-id="55cbd-121">不支援。</span><span class="sxs-lookup"><span data-stu-id="55cbd-121">Not supported.</span></span> <span data-ttu-id="55cbd-122">會傳回-1</span><span class="sxs-lookup"><span data-stu-id="55cbd-122">Returns -1</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="55cbd-123">支援的方法</span><span class="sxs-lookup"><span data-stu-id="55cbd-123">Supported Methods</span></span>  
  
|<span data-ttu-id="55cbd-124">名稱</span><span class="sxs-lookup"><span data-stu-id="55cbd-124">Name</span></span>|<span data-ttu-id="55cbd-125">Description</span><span class="sxs-lookup"><span data-stu-id="55cbd-125">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="55cbd-126">**Close()**</span><span class="sxs-lookup"><span data-stu-id="55cbd-126">**Close()**</span></span>|<span data-ttu-id="55cbd-127">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="55cbd-127">Closes the DataReader</span></span>|  
|<span data-ttu-id="55cbd-128">**取得 [方法]** <sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="55cbd-128">**Get [methods]** <sup>\*</sup></span></span><br /><br /> <span data-ttu-id="55cbd-129">在 [方法] 是預期的資料類型。</span><span class="sxs-lookup"><span data-stu-id="55cbd-129">where [methods] is the expected data type.</span></span> <span data-ttu-id="55cbd-130">例如</span><span class="sxs-lookup"><span data-stu-id="55cbd-130">E.g.</span></span> <span data-ttu-id="55cbd-131">GetInt32(int)</span><span class="sxs-lookup"><span data-stu-id="55cbd-131">GetInt32(int)</span></span>|<span data-ttu-id="55cbd-132">取得預期的資料類型為基礎的資料行值</span><span class="sxs-lookup"><span data-stu-id="55cbd-132">Gets column value based on the data type expected</span></span>|  
|<span data-ttu-id="55cbd-133">**IsDBNull(int)**</span><span class="sxs-lookup"><span data-stu-id="55cbd-133">**IsDBNull(int)**</span></span>|<span data-ttu-id="55cbd-134">不支援。</span><span class="sxs-lookup"><span data-stu-id="55cbd-134">Not supported.</span></span> <span data-ttu-id="55cbd-135">傳回 false。</span><span class="sxs-lookup"><span data-stu-id="55cbd-135">Returns false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55cbd-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55cbd-136">See Also</span></span>  
 [<span data-ttu-id="55cbd-137">SAP 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="55cbd-137">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)