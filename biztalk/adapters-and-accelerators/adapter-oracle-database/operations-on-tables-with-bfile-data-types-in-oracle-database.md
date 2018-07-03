---
title: 對具有 BFILE 資料類型，Oracle 資料庫中的資料表上的作業 |Microsoft Docs
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
ms.openlocfilehash: ab9885497468f91b309eb51ac0abbf4c0807ca76
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998255"
---
# <a name="operations-on-tables-with-bfile-data-types-in-oracle-database"></a><span data-ttu-id="bc65f-102">對具有 BFILE 資料類型，Oracle 資料庫中的資料表上的作業</span><span class="sxs-lookup"><span data-stu-id="bc65f-102">Operations on Tables With BFILE Data Types in Oracle Database</span></span>
<span data-ttu-id="bc65f-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和預存程序中支援 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="bc65f-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the BFILE data type in tables and stored procedures.</span></span> <span data-ttu-id="bc65f-104">下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料類型和存取 LOB 成品 （資料表/程序）：</span><span class="sxs-lookup"><span data-stu-id="bc65f-104">The following table summarizes the BFILE data type exposed by the adapter based on the operation performed and the LOB artifact (table/procedure) accessed:</span></span>  
  
|<span data-ttu-id="bc65f-105">成品</span><span class="sxs-lookup"><span data-stu-id="bc65f-105">Artifact</span></span>|<span data-ttu-id="bc65f-106">作業</span><span class="sxs-lookup"><span data-stu-id="bc65f-106">Operation</span></span>|<span data-ttu-id="bc65f-107">BFILE 資料行/參數為公開的資料類型</span><span class="sxs-lookup"><span data-stu-id="bc65f-107">Data type exposed for BFILE col/param</span></span>|<span data-ttu-id="bc65f-108">註解</span><span class="sxs-lookup"><span data-stu-id="bc65f-108">Comments</span></span>|  
|--------------|---------------|--------------------------------------------|--------------|  
|<span data-ttu-id="bc65f-109">TABLE</span><span class="sxs-lookup"><span data-stu-id="bc65f-109">TABLE</span></span>|<span data-ttu-id="bc65f-110">Insert</span><span class="sxs-lookup"><span data-stu-id="bc65f-110">INSERT</span></span>|<span data-ttu-id="bc65f-111">String</span><span class="sxs-lookup"><span data-stu-id="bc65f-111">String</span></span>|<span data-ttu-id="bc65f-112">表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="bc65f-112">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="bc65f-113">例如</span><span class="sxs-lookup"><span data-stu-id="bc65f-113">E.g.</span></span> <span data-ttu-id="bc65f-114">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="bc65f-114">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="bc65f-115">TABLE</span><span class="sxs-lookup"><span data-stu-id="bc65f-115">TABLE</span></span>|<span data-ttu-id="bc65f-116">UPDATE</span><span class="sxs-lookup"><span data-stu-id="bc65f-116">UPDATE</span></span>|<span data-ttu-id="bc65f-117">String</span><span class="sxs-lookup"><span data-stu-id="bc65f-117">String</span></span>|<span data-ttu-id="bc65f-118">至檔案，以更新到 BFILE 資料行代表邏輯的 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="bc65f-118">Represents the logical Oracle directory path to the file to be updated into the BFILE column</span></span>|  
|<span data-ttu-id="bc65f-119">TABLE</span><span class="sxs-lookup"><span data-stu-id="bc65f-119">TABLE</span></span>|<span data-ttu-id="bc65f-120">SELECT</span><span class="sxs-lookup"><span data-stu-id="bc65f-120">SELECT</span></span>|<span data-ttu-id="bc65f-121">byte[]</span><span class="sxs-lookup"><span data-stu-id="bc65f-121">byte[]</span></span>|<span data-ttu-id="bc65f-122">代表構成 BFILE 的二進位資料</span><span class="sxs-lookup"><span data-stu-id="bc65f-122">Represents the binary data constituting the BFILE</span></span>|  
|<span data-ttu-id="bc65f-123">預存程序</span><span class="sxs-lookup"><span data-stu-id="bc65f-123">STORED PROC</span></span>|<span data-ttu-id="bc65f-124">在 參數</span><span class="sxs-lookup"><span data-stu-id="bc65f-124">IN PARAM</span></span>|<span data-ttu-id="bc65f-125">String</span><span class="sxs-lookup"><span data-stu-id="bc65f-125">String</span></span>|<span data-ttu-id="bc65f-126">表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="bc65f-126">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="bc65f-127">例如</span><span class="sxs-lookup"><span data-stu-id="bc65f-127">E.g.</span></span> <span data-ttu-id="bc65f-128">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="bc65f-128">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="bc65f-129">預存程序</span><span class="sxs-lookup"><span data-stu-id="bc65f-129">STORED PROC</span></span>|<span data-ttu-id="bc65f-130">OUT 參數</span><span class="sxs-lookup"><span data-stu-id="bc65f-130">OUT PARAM</span></span>|<span data-ttu-id="bc65f-131">String</span><span class="sxs-lookup"><span data-stu-id="bc65f-131">String</span></span>|<span data-ttu-id="bc65f-132">表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="bc65f-132">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="bc65f-133">例如</span><span class="sxs-lookup"><span data-stu-id="bc65f-133">E.g.</span></span> <span data-ttu-id="bc65f-134">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="bc65f-134">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="bc65f-135">預存程序</span><span class="sxs-lookup"><span data-stu-id="bc65f-135">STORED PROC</span></span>|<span data-ttu-id="bc65f-136">INOUT 參數</span><span class="sxs-lookup"><span data-stu-id="bc65f-136">INOUT PARAM</span></span>|<span data-ttu-id="bc65f-137">不支援</span><span class="sxs-lookup"><span data-stu-id="bc65f-137">Not Supported</span></span>|-|  
  
 <span data-ttu-id="bc65f-138">BFILE 資料型別之資料表上也支援特殊作業 ReadLOB。</span><span class="sxs-lookup"><span data-stu-id="bc65f-138">The special operation ReadLOB is also supported on tables with BFILE data type.</span></span> <span data-ttu-id="bc65f-139">不支援 UpdateLOB 作業。</span><span class="sxs-lookup"><span data-stu-id="bc65f-139">The UpdateLOB operation is not supported.</span></span> <span data-ttu-id="bc65f-140">配接器用戶端，或者可以使用更新作業。</span><span class="sxs-lookup"><span data-stu-id="bc65f-140">Adapter clients can alternately use the UPDATE operation.</span></span>  
  
 <span data-ttu-id="bc65f-141">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="bc65f-141">For more information about:</span></span>  
  
- <span data-ttu-id="bc65f-142">使用包含 BFILE 資料類型的資料表上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 具有 BFILE 資料類型，使用 BizTalk Server 的 Oracle 資料庫中的資料表執行作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="bc65f-142">Performing operations on tables containing BFILE data types by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run operations on Tables with BFILE Data Types in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc65f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc65f-143">See Also</span></span>  
 <span data-ttu-id="bc65f-144">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="bc65f-144">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>