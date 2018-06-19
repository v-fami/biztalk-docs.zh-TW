---
title: 資料流的 Oracle 資料庫中的 LOB 資料類型支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- streaming, node-value
- streaming
- LOB data
- streaming, node
ms.assetid: a4943cdf-8336-48ac-b592-52ec514e7300
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3f052b5051e511179ed0a3b371a619b315a16af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214646"
---
# <a name="streaming-support-for-lob-data-types-in-oracle-database"></a><span data-ttu-id="f38d8-102">Oracle 資料庫中的 LOB 資料類型的串流支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-102">Streaming Support for LOB Data Types in Oracle Database</span></span>
<span data-ttu-id="f38d8-103">Oracle 資料庫支援資料流處理大型物件 (LOB) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f38d8-103">The Oracle database supports streaming on large object (LOB) data types.</span></span> <span data-ttu-id="f38d8-104">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援訊息資料流處理，這樣就能 LOB 資料端對端 Oracle 資料庫與配接器用戶端之間傳送資料流。</span><span class="sxs-lookup"><span data-stu-id="f38d8-104">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]supports message streaming, which makes it possible to stream LOB data end-to-end between the Oracle database and an adapter client.</span></span> <span data-ttu-id="f38d8-105">不過，資料流不支援相同的方式跨所有的程式撰寫模型時使用配接器。</span><span class="sxs-lookup"><span data-stu-id="f38d8-105">However, streaming is not supported in the same manner across all programming models when you use the adapter.</span></span>  
  
 <span data-ttu-id="f38d8-106">下列示範如何端對端 LOB 資料類型的資料流配接器支援在不同的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="f38d8-106">The following shows how end-to-end streaming of LOB data types is supported by the adapter across different programming models.</span></span>  
  
|<span data-ttu-id="f38d8-107">作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-107">Operation</span></span>|<span data-ttu-id="f38d8-108">WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="f38d8-108">WCF Channel Model</span></span>|<span data-ttu-id="f38d8-109">WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="f38d8-109">WCF Service Model</span></span>|<span data-ttu-id="f38d8-110">BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f38d8-110">BizTalk Server</span></span>|  
|---------------|-----------------------|-----------------------|--------------------|  
|<span data-ttu-id="f38d8-111">資料表/檢視表的 Insert 作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-111">Table/View Insert operation</span></span>|<span data-ttu-id="f38d8-112">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-112">Not supported</span></span>|<span data-ttu-id="f38d8-113">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-113">Not supported</span></span>|<span data-ttu-id="f38d8-114">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-114">Not supported</span></span>|  
|<span data-ttu-id="f38d8-115">資料表/檢視表選取作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-115">Table/View Select operation</span></span>|<span data-ttu-id="f38d8-116">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-116">Supported</span></span>|<span data-ttu-id="f38d8-117">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-117">Not supported</span></span>|<span data-ttu-id="f38d8-118">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-118">Supported</span></span>|  
|<span data-ttu-id="f38d8-119">資料表/檢視表更新作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-119">Table/View Update operation</span></span>|<span data-ttu-id="f38d8-120">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-120">Not supported</span></span>|<span data-ttu-id="f38d8-121">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-121">Not supported</span></span>|<span data-ttu-id="f38d8-122">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-122">Not supported</span></span>|  
|<span data-ttu-id="f38d8-123">資料表/檢視表刪除作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-123">Table/View Delete operation</span></span>|<span data-ttu-id="f38d8-124">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-124">Not supported</span></span>|<span data-ttu-id="f38d8-125">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-125">Not supported</span></span>|<span data-ttu-id="f38d8-126">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-126">Not supported</span></span>|  
|<span data-ttu-id="f38d8-127">資料表/檢視表 ReadLOB 作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-127">Table/View ReadLOB operation</span></span>|<span data-ttu-id="f38d8-128">支援;不過，ReadLOB 作業會顯示主要是為了支援資料流 WCF 服務模型中，不建議以供 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="f38d8-128">Supported; however, the ReadLOB operations is surfaced primarily to support streaming in the WCF service model, it is not recommended for use in the WCF channel model.</span></span> <span data-ttu-id="f38d8-129">相反地，請使用選取的作業或 SQLEXECUTE 操作。</span><span class="sxs-lookup"><span data-stu-id="f38d8-129">Use a Select operation or the SQLEXECUTE operation instead.</span></span>|<span data-ttu-id="f38d8-130">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-130">Supported</span></span>|<span data-ttu-id="f38d8-131">BizTalk Server 不支援 ReadLOB 作業。</span><span class="sxs-lookup"><span data-stu-id="f38d8-131">The ReadLOB operation is not supported for BizTalk Server.</span></span> <span data-ttu-id="f38d8-132">請改用選取作業。</span><span class="sxs-lookup"><span data-stu-id="f38d8-132">Use a Select operation instead.</span></span>|  
|<span data-ttu-id="f38d8-133">資料表/檢視表 UpdateLOB 作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-133">Table/View UpdateLOB operation</span></span>|<span data-ttu-id="f38d8-134">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-134">Supported</span></span>|<span data-ttu-id="f38d8-135">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-135">Not Supported</span></span>|<span data-ttu-id="f38d8-136">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-136">Supported</span></span>|  
|<span data-ttu-id="f38d8-137">SQLEXECUTE 操作</span><span class="sxs-lookup"><span data-stu-id="f38d8-137">SQLEXECUTE operation</span></span>|<span data-ttu-id="f38d8-138">在回應中支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-138">Supported in the response</span></span>|<span data-ttu-id="f38d8-139">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-139">Not Supported</span></span>|<span data-ttu-id="f38d8-140">在回應中支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-140">Supported in the response</span></span>|  
|<span data-ttu-id="f38d8-141">預存程序和函式的作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-141">Stored procedure and function operation</span></span>|<span data-ttu-id="f38d8-142">在回應中支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-142">Supported in the response</span></span>|<span data-ttu-id="f38d8-143">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-143">Not Supported</span></span>|<span data-ttu-id="f38d8-144">在回應中支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-144">Supported in the response</span></span>|  
|<span data-ttu-id="f38d8-145">POLLINGSTMT 作業</span><span class="sxs-lookup"><span data-stu-id="f38d8-145">POLLINGSTMT operation</span></span>|<span data-ttu-id="f38d8-146">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-146">Supported</span></span>|<span data-ttu-id="f38d8-147">不支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-147">Not Supported</span></span>|<span data-ttu-id="f38d8-148">支援</span><span class="sxs-lookup"><span data-stu-id="f38d8-148">Supported</span></span>|  
  
 <span data-ttu-id="f38d8-149">更完整如何支援資料流的 LOB 資料類型的配接器和如何加以支援當您使用各種程式設計模型與配接器的詳細資訊，請參閱[串流處理大型物件資料類型](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f38d8-149">For more comprehensive information about how streaming of LOB data types is supported by the adapter and how it is supported when you use various programming models with the adapter, see [Streaming large object data types](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38d8-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38d8-150">See Also</span></span>  
 [<span data-ttu-id="f38d8-151">BizTalk Adapter for Oracle 資料庫的概觀</span><span class="sxs-lookup"><span data-stu-id="f38d8-151">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)