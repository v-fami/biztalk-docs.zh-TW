---
title: "定義資料庫的自動成長設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd86dd49-6505-4673-b413-d3af729dfca9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e39de58751615e0465ce543368f47c1acd42ebc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="defining-auto-growth-settings-for-databases"></a><span data-ttu-id="2eede-102">定義資料庫的自動成長設定</span><span class="sxs-lookup"><span data-stu-id="2eede-102">Defining Auto-Growth Settings for Databases</span></span>
<span data-ttu-id="2eede-103">您應該將資料庫自動成長設 mb，而不是百分比，特別是針對 MessageBox 和 「 BizTalk 追蹤資料庫的固定數。</span><span class="sxs-lookup"><span data-stu-id="2eede-103">You should set database auto-growth to a fixed number of megabytes instead of to a percentage, especially for the MessageBox and BizTalk Tracking databases.</span></span> <span data-ttu-id="2eede-104">根據您的 BizTalk 應用程式和輸送量，MessageBox 與追蹤資料庫可以變得很大。</span><span class="sxs-lookup"><span data-stu-id="2eede-104">Depending on your BizTalk application and throughput, the MessageBox and Tracking databases can get quite large.</span></span> <span data-ttu-id="2eede-105">如果您將設定自動成長百分比，然後自動成長也很嚴重。</span><span class="sxs-lookup"><span data-stu-id="2eede-105">If you set auto-growth to a percentage, then the auto-growth can be substantial as well.</span></span>  
  
## <a name="how-instant-file-initialization-works"></a><span data-ttu-id="2eede-106">如何立即檔案初始化的運作方式</span><span class="sxs-lookup"><span data-stu-id="2eede-106">How Instant File Initialization Works</span></span>  
 <span data-ttu-id="2eede-107">當 SQL Server 會增加檔案大小時，它必須先初始化新的空間，才能使用。</span><span class="sxs-lookup"><span data-stu-id="2eede-107">When SQL Server increases the size of a file, it must first initialize the new space before it can be used.</span></span> <span data-ttu-id="2eede-108">這是封鎖作業，包括新的空間中填入空白頁。</span><span class="sxs-lookup"><span data-stu-id="2eede-108">This is a blocking operation that involves filling the new space with empty pages.</span></span> <span data-ttu-id="2eede-109">在 Windows 上的 SQL Server 支援立即檔案初始化。 」</span><span class="sxs-lookup"><span data-stu-id="2eede-109">SQL Server on Windows supports “instant file initialization.”</span></span> <span data-ttu-id="2eede-110">這可大幅減少檔案成長作業的效能影響。</span><span class="sxs-lookup"><span data-stu-id="2eede-110">This can greatly reduce the performance impact of a file growth operation.</span></span> <span data-ttu-id="2eede-111">如需詳細資訊，請參閱[資料庫檔案初始化](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization)。</span><span class="sxs-lookup"><span data-stu-id="2eede-111">For more information, see [Database File Initialization](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization).</span></span> <span data-ttu-id="2eede-112">本主題概述必須採取以啟用立即檔案初始化的步驟。</span><span class="sxs-lookup"><span data-stu-id="2eede-112">This topic outlines the steps that must be taken to enable instant file initialization.</span></span>  
  
## <a name="enabling-instant-file-initialization"></a><span data-ttu-id="2eede-113">啟用立即檔案初始化</span><span class="sxs-lookup"><span data-stu-id="2eede-113">Enabling Instant File Initialization</span></span>  
 <span data-ttu-id="2eede-114">針對步驟啟用立即檔案初始化，請參閱[資料庫檔案初始化](https://docs.microsoft.com/en-us/sql/relational-databases/databases/database-instant-file-initialization)。</span><span class="sxs-lookup"><span data-stu-id="2eede-114">For steps on enabling instant file initialization, see [Database File Initialization](https://docs.microsoft.com/en-us/sql/relational-databases/databases/database-instant-file-initialization).</span></span> <span data-ttu-id="2eede-115">建立檔案群組，並將 BizTalk Server 資料庫資料表、 索引和記錄檔移到適當的檔案群組，請遵循 「 附錄 B-建議使用 BizTalk Server 資料庫組態 」 中的建議中[< BizTalk Server資料庫最佳化 」 白皮書](http://go.microsoft.com/fwlink/?LinkID=101578)。</span><span class="sxs-lookup"><span data-stu-id="2eede-115">For creating file groups and moving the BizTalk Server database tables, indexes, and log files into the appropriate file groups, follow the recommendations in "Appendix B - Recommended BizTalk Server Database Configuration" in the ["BizTalk Server Database Optimization" white paper](http://go.microsoft.com/fwlink/?LinkID=101578).</span></span> <span data-ttu-id="2eede-116">在理想情況下支援的檔案群組的檔案大小應該預先配置，並可能的話，請設定為靜態的大小。</span><span class="sxs-lookup"><span data-stu-id="2eede-116">Ideally the size of files supporting the file groups should be pre-allocated and if possible, set to a static size.</span></span>  
  
 <span data-ttu-id="2eede-117">如果是新系統，而且靜態的大小不已明確建立，然後設定檔案與**啟用自動成長**選項，並指定檔案的成長**以 mb 為單位**。</span><span class="sxs-lookup"><span data-stu-id="2eede-117">If the system is new and the static sizes have not been definitively established, then configure files with the **Enable Autogrowth** option and specify file growth **In Megabytes**.</span></span> <span data-ttu-id="2eede-118">成長遞增值通常是不能大於 100 MB （適用於大型的檔案）、 10 MB （適用於中小型檔案） 或 1 MB （適用於小型檔案）。</span><span class="sxs-lookup"><span data-stu-id="2eede-118">The growth increment should generally be no larger than 100 MB (for large files), 10 MB (for medium-sized files), or 1 MB (for small files).</span></span>