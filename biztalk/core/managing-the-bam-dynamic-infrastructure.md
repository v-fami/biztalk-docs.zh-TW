---
title: 管理 BAM 動態基礎結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- infrastructure, managing [BAM]
- managing [BAM], infrastructure
ms.assetid: af8a76b5-407a-484d-aff4-0d911f88313e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 861390d71c7cd16815ae7f3d446e956f0ae3bb74
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004703"
---
# <a name="managing-the-bam-dynamic-infrastructure"></a><span data-ttu-id="52324-102">管理 BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="52324-102">Managing the BAM Dynamic Infrastructure</span></span>
<span data-ttu-id="52324-103">商務活動監控 (BAM) 功能會使用動態產生的 SQL 和線上分析處理 (OLAP) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="52324-103">Business Activity Monitoring (BAM) features use a dynamically generated SQL and online analytical processing (OLAP) infrastructure.</span></span> <span data-ttu-id="52324-104">系統管理員可以使用 BAM 管理公用程式，以部署商務分析師所開發的 BAM 定義活頁簿或 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="52324-104">Administrators use the BAM Management utility to deploy the BAM definition workbook or XML file, which the business analyst develops.</span></span>  
  
 <span data-ttu-id="52324-105">BAM 動態基礎結構是由 BAM 活頁簿檢視、BAM 部署、BAM Data Transformation Services (DTS) 封裝以及 BAM 資料庫所組成。</span><span class="sxs-lookup"><span data-stu-id="52324-105">The BAM dynamic infrastructure consists of the BAM workbook views, BAM deployments, the BAM Data Transformation Services (DTS) packages, and the BAM databases.</span></span> <span data-ttu-id="52324-106">如需有關 BAM 動態基礎結構的詳細資訊，請參閱 < [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)。</span><span class="sxs-lookup"><span data-stu-id="52324-106">For more information about the BAM dynamic infrastructure, see [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md).</span></span>  
  
 <span data-ttu-id="52324-107">當您設定 BizTalk Server 時，BizTalk Server 就會建立下列 BAM 資料庫：</span><span class="sxs-lookup"><span data-stu-id="52324-107">BizTalk Server creates the following BAM databases when you configure BizTalk Server:</span></span>  
  
- <span data-ttu-id="52324-108">BAM 主要匯入 (BAMPrimaryImport) 資料庫</span><span class="sxs-lookup"><span data-stu-id="52324-108">BAM Primary Import (BAMPrimaryImport) database</span></span>  
  
- <span data-ttu-id="52324-109">BAM 星狀結構描述 (BAMStarSchema) 資料庫 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="52324-109">BAM Star Schema (BAMStarSchema) database (optional)</span></span>  
  
- <span data-ttu-id="52324-110">BAM 分析 (BAMAnalysis) 資料庫 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="52324-110">BAM Analysis (BAMAnalysis) database (optional)</span></span>  
  
- <span data-ttu-id="52324-111">BAM 封存 (BAMArchive) 資料庫</span><span class="sxs-lookup"><span data-stu-id="52324-111">BAM Archive (BAMArchive) database</span></span>  
  
  <span data-ttu-id="52324-112">BAM 資料庫的詳細資訊，請參閱[管理 BAM 資料庫](../core/managing-bam-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="52324-112">For information about the BAM databases, see [Managing BAM Databases](../core/managing-bam-databases.md).</span></span>  
  
  <span data-ttu-id="52324-113">系統管理員負責執行下列 BAM 基礎結構的管理工作，本節將詳細說明這些工作：</span><span class="sxs-lookup"><span data-stu-id="52324-113">Administrators perform the following management tasks for the BAM infrastructure, which are described in this section:</span></span>  
  
- <span data-ttu-id="52324-114">部署與解除部署 BAM 定義和檢視</span><span class="sxs-lookup"><span data-stu-id="52324-114">Deploy and undeploy BAM definitions and views</span></span>  
  
- <span data-ttu-id="52324-115">管理使用者對 BAM 檢視的存取</span><span class="sxs-lookup"><span data-stu-id="52324-115">Manage user access to BAM views</span></span>  
  
- <span data-ttu-id="52324-116">執行 BAM DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="52324-116">Run the BAM DTS packages</span></span>  
  
- <span data-ttu-id="52324-117">備份 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="52324-117">Back up the BAM databases</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52324-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="52324-118">In This Section</span></span>  
  
-   [<span data-ttu-id="52324-119">管理 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="52324-119">Managing BAM Definitions</span></span>](../core/managing-bam-definitions.md)
  
-   [<span data-ttu-id="52324-120">管理 BAM 安全性</span><span class="sxs-lookup"><span data-stu-id="52324-120">Managing BAM Security</span></span>](../core/managing-bam-security.md)  
  
-   [<span data-ttu-id="52324-121">管理彙總</span><span class="sxs-lookup"><span data-stu-id="52324-121">Managing Aggregations</span></span>](../core/managing-aggregations.md) 
  
-   [<span data-ttu-id="52324-122">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="52324-122">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)
  
## <a name="see-also"></a><span data-ttu-id="52324-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52324-123">See Also</span></span>  
 [<span data-ttu-id="52324-124">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="52324-124">Managing BAM</span></span>](../core/managing-bam.md)