---
title: 訊息結構描述的輪詢 Operations1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c572c4ec-0a3f-42b8-bebd-40eb584438ad
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61aa47a7f991c140e0c0659b67da658a11a7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216142"
---
# <a name="message-schemas-for-the-polling-operations"></a><span data-ttu-id="035da-102">輪詢作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="035da-102">Message Schemas for the Polling Operations</span></span>
<span data-ttu-id="035da-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現輪詢根據 Oracle E-business Suite 中的目標物件與相關的各種輸入的作業。</span><span class="sxs-lookup"><span data-stu-id="035da-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces various inbound operations related to polling depending on the target object in Oracle E-Business Suite.</span></span> <span data-ttu-id="035da-104">介面資料表、 介面檢視、 資料表和檢視表，而您可以有多個自訂輪詢作業 PL/SQL 應用程式開發介面、 函數和預存程序，會顯示單一的輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="035da-104">For interface tables, interface views, tables, and views, a single Poll operation is surfaced whereas you can have multiple custom polling operations for PL/SQL APIs, functions, and stored procedures.</span></span>  
  
 <span data-ttu-id="035da-105">設定繫結屬性設定輪詢作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="035da-105">You configure the polling operations by setting binding properties in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="035da-106">如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="035da-106">For more information about these binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="035da-107">您設定**PollingStatement**內容繫結至指定的 SQL 陳述式、 預存程序、 函式或在封裝中的輪詢查詢的程序。</span><span class="sxs-lookup"><span data-stu-id="035da-107">You set the **PollingStatement** binding property to specify a SQL statement, stored procedure, function or a procedure within a package for the polling query.</span></span> <span data-ttu-id="035da-108">此查詢的結果集傳回做為資料輪詢作業中的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="035da-108">The result set of this query is returned as data to your code in the polling operation.</span></span>  
  
## <a name="message-structure-for-the-polling-operations"></a><span data-ttu-id="035da-109">輪詢作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="035da-109">Message Structure for the Polling Operations</span></span>  
 <span data-ttu-id="035da-110">下表顯示各種輪詢作業的 XML 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="035da-110">The following table shows the XML message structure for the various polling operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="035da-111">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="035da-111">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="035da-112">作業</span><span class="sxs-lookup"><span data-stu-id="035da-112">Operation</span></span>|<span data-ttu-id="035da-113">目標物件</span><span class="sxs-lookup"><span data-stu-id="035da-113">Target Object</span></span>|<span data-ttu-id="035da-114">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="035da-114">XML Message</span></span>|<span data-ttu-id="035da-115">Description</span><span class="sxs-lookup"><span data-stu-id="035da-115">Description</span></span>|  
|---------------|-------------------|-----------------|-----------------|  
|<span data-ttu-id="035da-116">輪詢</span><span class="sxs-lookup"><span data-stu-id="035da-116">Poll</span></span>|<span data-ttu-id="035da-117">介面資料表</span><span class="sxs-lookup"><span data-stu-id="035da-117">- Interface Tables</span></span><br /><br /> <span data-ttu-id="035da-118">介面檢視</span><span class="sxs-lookup"><span data-stu-id="035da-118">- Interface Views</span></span><br /><br /> <span data-ttu-id="035da-119">-資料表</span><span class="sxs-lookup"><span data-stu-id="035da-119">- Tables</span></span><br /><br /> <span data-ttu-id="035da-120">對檢視</span><span class="sxs-lookup"><span data-stu-id="035da-120">- Views</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/[TargetObject]/[Schema]/[TargetObject_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|<span data-ttu-id="035da-121">例如，輪詢作業介面資料表上的 XML 訊息會，如下所示：</span><span class="sxs-lookup"><span data-stu-id="035da-121">For example, the XML message for the Poll operation on Interface Tables will be as follows:</span></span><br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/InterfaceTables/[Schema]/[InterfaceTable_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|  
|<span data-ttu-id="035da-122">[CustomPollingOperation]</span><span class="sxs-lookup"><span data-stu-id="035da-122">[CustomPollingOperation]</span></span>|<span data-ttu-id="035da-123">-PL/SQL 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="035da-123">- PL/SQL APIs</span></span><br /><br /> <span data-ttu-id="035da-124">-預存程序</span><span class="sxs-lookup"><span data-stu-id="035da-124">- Stored Procedures</span></span><br /><br /> <span data-ttu-id="035da-125">函式</span><span class="sxs-lookup"><span data-stu-id="035da-125">- Functions</span></span>|<span data-ttu-id="035da-126">**PL/SQL 應用程式開發介面**</span><span class="sxs-lookup"><span data-stu-id="035da-126">**PL/SQL APIs**</span></span><br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingPackageAPis/[Schema]/[PL/SQL API]">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> <span data-ttu-id="035da-127">**函數**</span><span class="sxs-lookup"><span data-stu-id="035da-127">**Functions**</span></span><br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> <span data-ttu-id="035da-128">**預存程序**</span><span class="sxs-lookup"><span data-stu-id="035da-128">**Stored Procedures**</span></span><br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`|<span data-ttu-id="035da-129">輪詢作業中的結果集的結構取決於目標物件中的項目中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="035da-129">The structure of the result set in the polling operation is determined by the data type of the elements in the target object.</span></span>|  
  
 <span data-ttu-id="035da-130">實體描述：</span><span class="sxs-lookup"><span data-stu-id="035da-130">Entity descriptions:</span></span>  
  
 <span data-ttu-id="035da-131">[版本] = http://schemas.microsoft.com/OracleEBS/2008/05。</span><span class="sxs-lookup"><span data-stu-id="035da-131">[Version] = http://schemas.microsoft.com/OracleEBS/2008/05.</span></span>  
  
 <span data-ttu-id="035da-132">[CustomPollingOperation] = 自訂輪詢作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="035da-132">[CustomPollingOperation] = Name of the custom polling operation.</span></span>  
  
 <span data-ttu-id="035da-133">[Schema] = Oracle 結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="035da-133">[Schema] = Name of the Oracle schema.</span></span> <span data-ttu-id="035da-134">例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="035da-134">For example, SCOTT.</span></span>  
  
 <span data-ttu-id="035da-135">[PL/SQL API] = 自訂輪詢作業執行所在的 PL/SQL api 的名稱。</span><span class="sxs-lookup"><span data-stu-id="035da-135">[PL/SQL API] = Name of the PL/SQL API on which a custom polling operation is performed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035da-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="035da-136">See Also</span></span>  
 [<span data-ttu-id="035da-137">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="035da-137">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)