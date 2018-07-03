---
title: 關於 Data Provider for Siebel |Microsoft Docs
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
ms.openlocfilehash: 97d7366ba227c16a5910a8000e57e92f992d3e1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989575"
---
# <a name="about-the-data-provider-for-siebel"></a><span data-ttu-id="12756-102">關於 Data Provider for Siebel</span><span class="sxs-lookup"><span data-stu-id="12756-102">About the Data Provider for Siebel</span></span>
## <a name="overview"></a><span data-ttu-id="12756-103">概觀</span><span class="sxs-lookup"><span data-stu-id="12756-103">Overview</span></span>
<span data-ttu-id="12756-104">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]之上的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12756-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is built on top of the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="12756-105">您可以使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]來：</span><span class="sxs-lookup"><span data-stu-id="12756-105">You can use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] to:</span></span>  
  
- <span data-ttu-id="12756-106">撰寫 ADO.NET 用戶端連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="12756-106">Write an ADO.NET client to connect to the Siebel system.</span></span> <span data-ttu-id="12756-107">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]公開特定類別，可讓您與提供者介面。</span><span class="sxs-lookup"><span data-stu-id="12756-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] exposes certain classes that enable you to interface with the provider.</span></span>  
  
- <span data-ttu-id="12756-108">Siebel 商務元件上執行 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="12756-108">Run a SELECT query on a Siebel business component</span></span>
  
- <span data-ttu-id="12756-109">Siebel 商務服務上執行的執行查詢</span><span class="sxs-lookup"><span data-stu-id="12756-109">Run an EXEC query on a Siebel business service</span></span>
  
- <span data-ttu-id="12756-110">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]搭配 SQL Server Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="12756-110">Use the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SQL Server Integration Services (SSIS)</span></span>
  
<span data-ttu-id="12756-111">[使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)位於資訊的絕佳資源：</span><span class="sxs-lookup"><span data-stu-id="12756-111">[Use  the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) is a great resource for information on:</span></span>  
  
- <span data-ttu-id="12756-112">擴充 ADO.NET 介面 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12756-112">The ADO.NET interfaces extended by the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]</span></span>  
  
- <span data-ttu-id="12756-113">連接字串以連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="12756-113">The connection string to connect to a Siebel system</span></span>  
  
- <span data-ttu-id="12756-114">SELECT 和 EXEC 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="12756-114">Syntax for the SELECT and EXEC statements</span></span>  
  
- <span data-ttu-id="12756-115">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用 SSIS</span><span class="sxs-lookup"><span data-stu-id="12756-115">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SSIS</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="12756-116">限制</span><span class="sxs-lookup"><span data-stu-id="12756-116">Limitations</span></span>
<span data-ttu-id="12756-117">下列已知的限制[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="12756-117">The following are known limitations of the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:</span></span>  
  
- <span data-ttu-id="12756-118">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援別名的資料表名稱在 SELECT 子句中，但不是會在 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="12756-118">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause, but not in the WHERE clause.</span></span>  
  
- <span data-ttu-id="12756-119">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法建立資料表的資料行名稱中有特殊字元，"]"。</span><span class="sxs-lookup"><span data-stu-id="12756-119">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to create a table with column names that have the special character, "]".</span></span> <span data-ttu-id="12756-120">您可以包括另一個右方括弧來逸出特殊字元。</span><span class="sxs-lookup"><span data-stu-id="12756-120">You can escape the special character by including another closing square bracket.</span></span> <span data-ttu-id="12756-121">因此，您應該包含"]]"而不是 「] 」。</span><span class="sxs-lookup"><span data-stu-id="12756-121">So, you should include"]]" instead of "]".</span></span>  
  
- <span data-ttu-id="12756-122">因為基礎 Siebel 用戶端 API，逾時處理的問題而[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="12756-122">Due to issues with timeout handling by the underlying Siebel client API, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support command and connection timeout.</span></span>  
  
- <span data-ttu-id="12756-123">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援非同步命令的行為。</span><span class="sxs-lookup"><span data-stu-id="12756-123">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
- <span data-ttu-id="12756-124">SQL Server Integration Services (SSIS) 專案中，搭配使用時[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法擷取資料行包含值超過 8000 個字元的資料。</span><span class="sxs-lookup"><span data-stu-id="12756-124">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="12756-125">這是因為，據此 SSIS 限制：</span><span class="sxs-lookup"><span data-stu-id="12756-125">This is due to an SSIS restriction according to which:</span></span>  
  
  -   <span data-ttu-id="12756-126">不支援大於 4000 個字元，SSIS 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="12756-126">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
  -   <span data-ttu-id="12756-127">不支援大於 4000 個寬字元的值。</span><span class="sxs-lookup"><span data-stu-id="12756-127">Values greater than 4000 wide characters are not supported.</span></span>  
  
  -   <span data-ttu-id="12756-128">不支援大於 8000 個單一位元組字元的值。</span><span class="sxs-lookup"><span data-stu-id="12756-128">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
- <span data-ttu-id="12756-129">EXEC 作業將無法正常運作時使用[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]與 SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="12756-129">The EXEC operation will not be functional while using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="12756-130">因此，比方說，配接器用戶端將無法再執行 Siebel 商務服務 (使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 時使用 SSIS 中使用的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="12756-130">So, for example, adapter clients will not be able to execute a business service in Siebel (using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) while using the data providers with SSIS.</span></span> 

## <a name="see-also"></a><span data-ttu-id="12756-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12756-131">See also</span></span>
[<span data-ttu-id="12756-132">Siebel 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="12756-132">Limitations of the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[<span data-ttu-id="12756-133">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="12756-133">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)