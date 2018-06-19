---
title: BFILE 資料型別，Oracle 資料庫中之資料表上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, on tables with BFILE data types
- BFILE data type
- BFILE
ms.assetid: 7937564e-4423-459f-9824-6a27113ebfb3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c236651e6c44248ea8f6cf0f73f0c9bc17e46ac5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214310"
---
# <a name="operations-on-tables-with-bfile-data-types-in-oracle-database"></a><span data-ttu-id="9f7d7-102">BFILE 資料型別，Oracle 資料庫中之資料表上的作業</span><span class="sxs-lookup"><span data-stu-id="9f7d7-102">Operations on Tables With BFILE Data Types in Oracle Database</span></span>
<span data-ttu-id="9f7d7-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和預存程序中支援 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="9f7d7-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the BFILE data type in tables and stored procedures.</span></span> <span data-ttu-id="9f7d7-104">下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料型別和 LOB 成品 （資料表/程序） 存取：</span><span class="sxs-lookup"><span data-stu-id="9f7d7-104">The following table summarizes the BFILE data type exposed by the adapter based on the operation performed and the LOB artifact (table/procedure) accessed:</span></span>  
  
|<span data-ttu-id="9f7d7-105">成品</span><span class="sxs-lookup"><span data-stu-id="9f7d7-105">Artifact</span></span>|<span data-ttu-id="9f7d7-106">作業</span><span class="sxs-lookup"><span data-stu-id="9f7d7-106">Operation</span></span>|<span data-ttu-id="9f7d7-107">BFILE 資料行/參數為公開的資料類型</span><span class="sxs-lookup"><span data-stu-id="9f7d7-107">Data type exposed for BFILE col/param</span></span>|<span data-ttu-id="9f7d7-108">註解</span><span class="sxs-lookup"><span data-stu-id="9f7d7-108">Comments</span></span>|  
|--------------|---------------|--------------------------------------------|--------------|  
|<span data-ttu-id="9f7d7-109">TABLE</span><span class="sxs-lookup"><span data-stu-id="9f7d7-109">TABLE</span></span>|<span data-ttu-id="9f7d7-110">INSERT</span><span class="sxs-lookup"><span data-stu-id="9f7d7-110">INSERT</span></span>|<span data-ttu-id="9f7d7-111">字串</span><span class="sxs-lookup"><span data-stu-id="9f7d7-111">String</span></span>|<span data-ttu-id="9f7d7-112">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="9f7d7-112">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="9f7d7-113">例如</span><span class="sxs-lookup"><span data-stu-id="9f7d7-113">E.g.</span></span> <span data-ttu-id="9f7d7-114">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="9f7d7-114">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="9f7d7-115">TABLE</span><span class="sxs-lookup"><span data-stu-id="9f7d7-115">TABLE</span></span>|<span data-ttu-id="9f7d7-116">UPDATE</span><span class="sxs-lookup"><span data-stu-id="9f7d7-116">UPDATE</span></span>|<span data-ttu-id="9f7d7-117">字串</span><span class="sxs-lookup"><span data-stu-id="9f7d7-117">String</span></span>|<span data-ttu-id="9f7d7-118">表示更新成 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="9f7d7-118">Represents the logical Oracle directory path to the file to be updated into the BFILE column</span></span>|  
|<span data-ttu-id="9f7d7-119">TABLE</span><span class="sxs-lookup"><span data-stu-id="9f7d7-119">TABLE</span></span>|<span data-ttu-id="9f7d7-120">SELECT</span><span class="sxs-lookup"><span data-stu-id="9f7d7-120">SELECT</span></span>|<span data-ttu-id="9f7d7-121">byte[]</span><span class="sxs-lookup"><span data-stu-id="9f7d7-121">byte[]</span></span>|<span data-ttu-id="9f7d7-122">代表從屬 BFILE 的二進位資料</span><span class="sxs-lookup"><span data-stu-id="9f7d7-122">Represents the binary data constituting the BFILE</span></span>|  
|<span data-ttu-id="9f7d7-123">預存程序</span><span class="sxs-lookup"><span data-stu-id="9f7d7-123">STORED PROC</span></span>|<span data-ttu-id="9f7d7-124">PARAM 中</span><span class="sxs-lookup"><span data-stu-id="9f7d7-124">IN PARAM</span></span>|<span data-ttu-id="9f7d7-125">字串</span><span class="sxs-lookup"><span data-stu-id="9f7d7-125">String</span></span>|<span data-ttu-id="9f7d7-126">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="9f7d7-126">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="9f7d7-127">例如</span><span class="sxs-lookup"><span data-stu-id="9f7d7-127">E.g.</span></span> <span data-ttu-id="9f7d7-128">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="9f7d7-128">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="9f7d7-129">預存程序</span><span class="sxs-lookup"><span data-stu-id="9f7d7-129">STORED PROC</span></span>|<span data-ttu-id="9f7d7-130">OUT 參數</span><span class="sxs-lookup"><span data-stu-id="9f7d7-130">OUT PARAM</span></span>|<span data-ttu-id="9f7d7-131">字串</span><span class="sxs-lookup"><span data-stu-id="9f7d7-131">String</span></span>|<span data-ttu-id="9f7d7-132">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="9f7d7-132">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="9f7d7-133">例如</span><span class="sxs-lookup"><span data-stu-id="9f7d7-133">E.g.</span></span> <span data-ttu-id="9f7d7-134">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="9f7d7-134">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="9f7d7-135">預存程序</span><span class="sxs-lookup"><span data-stu-id="9f7d7-135">STORED PROC</span></span>|<span data-ttu-id="9f7d7-136">INOUT 參數</span><span class="sxs-lookup"><span data-stu-id="9f7d7-136">INOUT PARAM</span></span>|<span data-ttu-id="9f7d7-137">不支援</span><span class="sxs-lookup"><span data-stu-id="9f7d7-137">Not Supported</span></span>|-|  
  
 <span data-ttu-id="9f7d7-138">也支援特殊作業 ReadLOB BFILE 資料型別之資料表上。</span><span class="sxs-lookup"><span data-stu-id="9f7d7-138">The special operation ReadLOB is also supported on tables with BFILE data type.</span></span> <span data-ttu-id="9f7d7-139">不支援 UpdateLOB 作業。</span><span class="sxs-lookup"><span data-stu-id="9f7d7-139">The UpdateLOB operation is not supported.</span></span> <span data-ttu-id="9f7d7-140">或者，配接器用戶端可以使用更新作業。</span><span class="sxs-lookup"><span data-stu-id="9f7d7-140">Adapter clients can alternately use the UPDATE operation.</span></span>  
  
 <span data-ttu-id="9f7d7-141">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="9f7d7-141">For more information about:</span></span>  
  
-   <span data-ttu-id="9f7d7-142">使用包含 BFILE 資料型別資料表上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[以 BFILE 資料型別使用 BizTalk Server 的 Oracle 資料庫中執行的資料表作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7d7-142">Performing operations on tables containing BFILE data types by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run operations on Tables with BFILE Data Types in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f7d7-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f7d7-143">See Also</span></span>  
 <span data-ttu-id="9f7d7-144">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="9f7d7-144">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>