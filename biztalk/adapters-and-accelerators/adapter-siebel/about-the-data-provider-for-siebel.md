---
title: Siebel 的資料提供者相關 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, overview
ms.assetid: 461fe4d8-75f2-49d5-9fc2-3baab4ccf13f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cac425bf1671166b4f40cecae3e1a3aca1c8e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217758"
---
# <a name="about-the-data-provider-for-siebel"></a><span data-ttu-id="fbb51-102">有關 Siebel 的資料提供者</span><span class="sxs-lookup"><span data-stu-id="fbb51-102">About the Data Provider for Siebel</span></span>
## <a name="overview"></a><span data-ttu-id="fbb51-103">概觀</span><span class="sxs-lookup"><span data-stu-id="fbb51-103">Overview</span></span>
<span data-ttu-id="fbb51-104">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]建置最上層的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fbb51-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is built on top of the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="fbb51-105">您可以使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]至：</span><span class="sxs-lookup"><span data-stu-id="fbb51-105">You can use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] to:</span></span>  
  
-   <span data-ttu-id="fbb51-106">撰寫 ADO.NET 用戶端連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="fbb51-106">Write an ADO.NET client to connect to the Siebel system.</span></span> <span data-ttu-id="fbb51-107">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]會公開特定類別，可讓您與提供者介面。</span><span class="sxs-lookup"><span data-stu-id="fbb51-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] exposes certain classes that enable you to interface with the provider.</span></span>  
  
-   <span data-ttu-id="fbb51-108">Siebel 商務元件上執行 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="fbb51-108">Run a SELECT query on a Siebel business component</span></span>
  
-   <span data-ttu-id="fbb51-109">Siebel 商務服務上執行 EXEC 查詢</span><span class="sxs-lookup"><span data-stu-id="fbb51-109">Run an EXEC query on a Siebel business service</span></span>
  
-   <span data-ttu-id="fbb51-110">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]搭配 SQL Server Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="fbb51-110">Use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SQL Server Integration Services (SSIS)</span></span>
  
<span data-ttu-id="fbb51-111">[使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)位於資訊的絕佳資源：</span><span class="sxs-lookup"><span data-stu-id="fbb51-111">[Use  the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) is a great resource for information on:</span></span>  
  
-   <span data-ttu-id="fbb51-112">藉由擴充的 ADO.NET 介面[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb51-112">The ADO.NET interfaces extended by the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span></span>  
  
-   <span data-ttu-id="fbb51-113">要連接至 Siebel 系統的連接字串</span><span class="sxs-lookup"><span data-stu-id="fbb51-113">The connection string to connect to a Siebel system</span></span>  
  
-   <span data-ttu-id="fbb51-114">SELECT 和 EXEC 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="fbb51-114">Syntax for the SELECT and EXEC statements</span></span>  
  
-   <span data-ttu-id="fbb51-115">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 SSIS</span><span class="sxs-lookup"><span data-stu-id="fbb51-115">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SSIS</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="fbb51-116">限制</span><span class="sxs-lookup"><span data-stu-id="fbb51-116">Limitations</span></span>
<span data-ttu-id="fbb51-117">下列已知的限制[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="fbb51-117">The following are known limitations of the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span></span>  
  
-   <span data-ttu-id="fbb51-118">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援別名的資料表名稱在 SELECT 子句中，但不是在 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="fbb51-118">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause, but not in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="fbb51-119">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法建立資料表的資料行名稱中有特殊字元，"]"。</span><span class="sxs-lookup"><span data-stu-id="fbb51-119">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to create a table with column names that have the special character, "]".</span></span> <span data-ttu-id="fbb51-120">您可以藉由另一個右方括弧逸出特殊字元。</span><span class="sxs-lookup"><span data-stu-id="fbb51-120">You can escape the special character by including another closing square bracket.</span></span> <span data-ttu-id="fbb51-121">因此，您應該包括 「]]"而不是"]"。</span><span class="sxs-lookup"><span data-stu-id="fbb51-121">So, you should include"]]" instead of "]".</span></span>  
  
-   <span data-ttu-id="fbb51-122">因為具有基礎 Siebel 用戶端應用程式開發介面，逾時處理的問題而[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="fbb51-122">Due to issues with timeout handling by the underlying Siebel client API, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="fbb51-123">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援非同步命令的行為。</span><span class="sxs-lookup"><span data-stu-id="fbb51-123">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
-   <span data-ttu-id="fbb51-124">使用 SQL Server Integration Services (SSIS) 專案，使用時[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法擷取資料行包含的值超過 8000 個字元的資料。</span><span class="sxs-lookup"><span data-stu-id="fbb51-124">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="fbb51-125">這是因為，據此 SSIS 限制：</span><span class="sxs-lookup"><span data-stu-id="fbb51-125">This is due to an SSIS restriction according to which:</span></span>  
  
    -   <span data-ttu-id="fbb51-126">不支援大於 4000 個字元，SSIS 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="fbb51-126">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
    -   <span data-ttu-id="fbb51-127">不支援大於 4000 個寬字元的值。</span><span class="sxs-lookup"><span data-stu-id="fbb51-127">Values greater than 4000 wide characters are not supported.</span></span>  
  
    -   <span data-ttu-id="fbb51-128">不支援大於 8000 個單一位元組字元的值。</span><span class="sxs-lookup"><span data-stu-id="fbb51-128">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
-   <span data-ttu-id="fbb51-129">EXEC 作業將無法正常運作時使用[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]與 SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="fbb51-129">The EXEC operation will not be functional while using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="fbb51-130">因此，比方說，配接器用戶端將無法執行 Siebel 商務服務 (使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 時使用 SSIS 中使用的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="fbb51-130">So, for example, adapter clients will not be able to execute a business service in Siebel (using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) while using the data providers with SSIS.</span></span> 

## <a name="see-also"></a><span data-ttu-id="fbb51-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb51-131">See also</span></span>
[<span data-ttu-id="fbb51-132">Siebel 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="fbb51-132">Limitations of the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[<span data-ttu-id="fbb51-133">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="fbb51-133">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)