---
title: 資料表包含 BFILE 資料型別上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d7ebeb9-c2d6-4024-a169-263b947eeeb1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5096539b86512e51756d3a872ff566872ff520f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960996"
---
# <a name="operations-on-tables-that-contain-bfile-data-types"></a><span data-ttu-id="2da6f-102">資料表包含 BFILE 資料型別上的作業</span><span class="sxs-lookup"><span data-stu-id="2da6f-102">Operations on Tables That Contain BFILE Data Types</span></span>
<span data-ttu-id="2da6f-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]資料表和預存程序中支援 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="2da6f-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports the BFILE data type in tables and stored procedures.</span></span> 

## <a name="bfile-data-types"></a><span data-ttu-id="2da6f-104">BFILE 資料型別</span><span class="sxs-lookup"><span data-stu-id="2da6f-104">BFILE data types</span></span>
<span data-ttu-id="2da6f-105">下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料型別和 LOB 成品 （資料表/程序） 存取：</span><span class="sxs-lookup"><span data-stu-id="2da6f-105">The following table summarizes the BFILE data type exposed by the adapter based on the operation performed and the LOB artifact (table/procedure) accessed:</span></span>  
  
|<span data-ttu-id="2da6f-106">成品</span><span class="sxs-lookup"><span data-stu-id="2da6f-106">Artifact</span></span>|<span data-ttu-id="2da6f-107">作業</span><span class="sxs-lookup"><span data-stu-id="2da6f-107">Operation</span></span>|<span data-ttu-id="2da6f-108">BFILE 資料行/參數為公開的資料類型</span><span class="sxs-lookup"><span data-stu-id="2da6f-108">Data type exposed for BFILE col/param</span></span>|<span data-ttu-id="2da6f-109">註解</span><span class="sxs-lookup"><span data-stu-id="2da6f-109">Comments</span></span>|  
|--------------|---------------|--------------------------------------------|--------------|  
|<span data-ttu-id="2da6f-110">TABLE</span><span class="sxs-lookup"><span data-stu-id="2da6f-110">TABLE</span></span>|<span data-ttu-id="2da6f-111">INSERT</span><span class="sxs-lookup"><span data-stu-id="2da6f-111">INSERT</span></span>|<span data-ttu-id="2da6f-112">字串</span><span class="sxs-lookup"><span data-stu-id="2da6f-112">String</span></span>|<span data-ttu-id="2da6f-113">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="2da6f-113">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="2da6f-114">例如</span><span class="sxs-lookup"><span data-stu-id="2da6f-114">E.g.</span></span> <span data-ttu-id="2da6f-115">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="2da6f-115">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="2da6f-116">TABLE</span><span class="sxs-lookup"><span data-stu-id="2da6f-116">TABLE</span></span>|<span data-ttu-id="2da6f-117">UPDATE</span><span class="sxs-lookup"><span data-stu-id="2da6f-117">UPDATE</span></span>|<span data-ttu-id="2da6f-118">字串</span><span class="sxs-lookup"><span data-stu-id="2da6f-118">String</span></span>|<span data-ttu-id="2da6f-119">表示更新成 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="2da6f-119">Represents the logical Oracle directory path to the file to be updated into the BFILE column</span></span>|  
|<span data-ttu-id="2da6f-120">TABLE</span><span class="sxs-lookup"><span data-stu-id="2da6f-120">TABLE</span></span>|<span data-ttu-id="2da6f-121">SELECT</span><span class="sxs-lookup"><span data-stu-id="2da6f-121">SELECT</span></span>|<span data-ttu-id="2da6f-122">byte[]</span><span class="sxs-lookup"><span data-stu-id="2da6f-122">byte[]</span></span>|<span data-ttu-id="2da6f-123">代表從屬 BFILE 的二進位資料</span><span class="sxs-lookup"><span data-stu-id="2da6f-123">Represents the binary data constituting the BFILE</span></span>|  
|<span data-ttu-id="2da6f-124">預存程序</span><span class="sxs-lookup"><span data-stu-id="2da6f-124">STORED PROC</span></span>|<span data-ttu-id="2da6f-125">PARAM 中</span><span class="sxs-lookup"><span data-stu-id="2da6f-125">IN PARAM</span></span>|<span data-ttu-id="2da6f-126">字串</span><span class="sxs-lookup"><span data-stu-id="2da6f-126">String</span></span>|<span data-ttu-id="2da6f-127">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="2da6f-127">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="2da6f-128">例如</span><span class="sxs-lookup"><span data-stu-id="2da6f-128">E.g.</span></span> <span data-ttu-id="2da6f-129">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="2da6f-129">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="2da6f-130">預存程序</span><span class="sxs-lookup"><span data-stu-id="2da6f-130">STORED PROC</span></span>|<span data-ttu-id="2da6f-131">OUT 參數</span><span class="sxs-lookup"><span data-stu-id="2da6f-131">OUT PARAM</span></span>|<span data-ttu-id="2da6f-132">字串</span><span class="sxs-lookup"><span data-stu-id="2da6f-132">String</span></span>|<span data-ttu-id="2da6f-133">表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑</span><span class="sxs-lookup"><span data-stu-id="2da6f-133">Represents the logical Oracle directory path to the file to be inserted into the BFILE column</span></span><br /><br /> <span data-ttu-id="2da6f-134">例如</span><span class="sxs-lookup"><span data-stu-id="2da6f-134">E.g.</span></span> <span data-ttu-id="2da6f-135">MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄</span><span class="sxs-lookup"><span data-stu-id="2da6f-135">MYDIR/screen.jpg where MYDIR is a logical directory in Oracle</span></span>|  
|<span data-ttu-id="2da6f-136">預存程序</span><span class="sxs-lookup"><span data-stu-id="2da6f-136">STORED PROC</span></span>|<span data-ttu-id="2da6f-137">INOUT 參數</span><span class="sxs-lookup"><span data-stu-id="2da6f-137">INOUT PARAM</span></span>|<span data-ttu-id="2da6f-138">不支援</span><span class="sxs-lookup"><span data-stu-id="2da6f-138">Not Supported</span></span>|-|  
  
 <span data-ttu-id="2da6f-139">特殊作業`Read_<LOBColName>`BFILE 資料型別，與資料表上也支援其中\<LOBColName\>是資料表中的 LOB 資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="2da6f-139">The special operation `Read_<LOBColName>` is also supported on tables with BFILE data type, where \<LOBColName\> is the LOB column name in the table.</span></span> <span data-ttu-id="2da6f-140">`Update_<LOBColName>` BFILE 資料型別不支援作業。</span><span class="sxs-lookup"><span data-stu-id="2da6f-140">The `Update_<LOBColName>` operation is not supported for BFILE data type.</span></span> <span data-ttu-id="2da6f-141">或者，配接器用戶端可以使用更新作業。</span><span class="sxs-lookup"><span data-stu-id="2da6f-141">Adapter clients can alternately use the Update operation.</span></span>  
  
## <a name="more-good-info"></a><span data-ttu-id="2da6f-142">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2da6f-142">More good info</span></span>  
  
-   <span data-ttu-id="2da6f-143">`Read_<LOBColName>`和`Update_<LOBColName>`作業，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2da6f-143">The `Read_<LOBColName>` and `Update_<LOBColName>` operations, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da6f-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="2da6f-144">See Also</span></span>  
 <span data-ttu-id="2da6f-145">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2da6f-145">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>