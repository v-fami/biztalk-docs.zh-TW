---
title: "最佳化效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bafa119b-187e-4595-a673-358dc0a109b7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e79c318d7cd12d799459535914046da98819561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-performance"></a><span data-ttu-id="42979-102">最佳化效能</span><span class="sxs-lookup"><span data-stu-id="42979-102">Optimizing Performance</span></span>
<span data-ttu-id="42979-103">預設安裝的 Windows 作業系統，SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並提供用於生產環境的最佳效能可大幅最佳化 IIS[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="42979-103">A default installation of the Windows operating system, SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and IIS can be significantly optimized to provide optimal performance for a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="42979-104">WCF 組態參數也可以從預設設定，以大幅提升效能微調。</span><span class="sxs-lookup"><span data-stu-id="42979-104">WCF configuration parameters can also be tuned from the default settings to provide significantly improved performance.</span></span> <span data-ttu-id="42979-105">本節提供部署生產時應該遵循特定的效能最佳化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="42979-105">This section provides specific performance optimizations that should be followed when deploying a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42979-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="42979-106">In This Section</span></span>  
  
-   [<span data-ttu-id="42979-107">作業系統效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-107">Optimizing Operating System Performance</span></span>](../technical-guides/optimizing-operating-system-performance.md)  
  
-   [<span data-ttu-id="42979-108">網路效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-108">Optimizing Network Performance</span></span>](../technical-guides/optimizing-network-performance.md)  
  
-   [<span data-ttu-id="42979-109">IIS 效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-109">Optimizing IIS Performance</span></span>](../technical-guides/optimizing-iis-performance.md)  
  
-   [<span data-ttu-id="42979-110">最佳化資料庫效能</span><span class="sxs-lookup"><span data-stu-id="42979-110">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)  
  
-   [<span data-ttu-id="42979-111">BizTalk Server 效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-111">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)  
  
-   [<span data-ttu-id="42979-112">協調流程效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-112">Optimizing Orchestration Performance</span></span>](../technical-guides/optimizing-orchestration-performance.md)  
  
-   [<span data-ttu-id="42979-113">WCF Web 服務效能最佳化</span><span class="sxs-lookup"><span data-stu-id="42979-113">Optimizing WCF Web Service Performance</span></span>](../technical-guides/optimizing-wcf-web-service-performance.md)  
  
-   [<span data-ttu-id="42979-114">最佳化 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="42979-114">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)  
  
-   [<span data-ttu-id="42979-115">Windows PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="42979-115">Windows PowerShell Scripts</span></span>](../technical-guides/windows-powershell-scripts.md)