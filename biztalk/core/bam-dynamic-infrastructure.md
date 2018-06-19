---
title: BAM 動態基礎結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- infrastructure, BAM
- BAM, infrastructure
ms.assetid: 88f39438-3213-4f0d-8b8d-e6426c266138
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3660eeb6f85fb21ff78b7b833b21adbb3af87385
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230446"
---
# <a name="bam-dynamic-infrastructure"></a><span data-ttu-id="e4348-102">BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="e4348-102">BAM Dynamic Infrastructure</span></span>
<span data-ttu-id="e4348-103">BAM 基礎結構包含 SQL Server 資料表、 BAM 檢視、 預存程序和 Data Transformation Services (DTS) 封裝所設定和管理透過累加在 BAM 資料庫 （主要匯入、 封存、 星狀結構描述和分析）部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="e4348-103">The BAM infrastructure consists of SQL Server tables, BAM views, stored procedures, and Data Transformation Services (DTS) packages in the BAM databases (Primary Import, Archive, Star Schema, and Analysis) as configured and managed through incremental deployments of BAM definitions.</span></span> <span data-ttu-id="e4348-104">基礎結構是 where、 在執行階段，事件會相互關聯、 彙總，且可供使用者查詢。</span><span class="sxs-lookup"><span data-stu-id="e4348-104">The infrastructure is where, at run time, events are correlated, aggregated, and then made available for querying by users.</span></span>  
  
 <span data-ttu-id="e4348-105">本節說明這些基礎結構程序中的一些程序。</span><span class="sxs-lookup"><span data-stu-id="e4348-105">This section describes some of these infrastructure processes.</span></span> <span data-ttu-id="e4348-106">例如，當您從應用程式 (BAM 定義) 擷取所需的資料之後，您就可以儲存它以便查詢。</span><span class="sxs-lookup"><span data-stu-id="e4348-106">For example, once you extract the data of interest from your applications (the BAM definition), you can store it so that it is available for queries.</span></span> <span data-ttu-id="e4348-107">此外，您還可以維護某些預先建立的資料彙總，以進行更快速的彙總查詢。</span><span class="sxs-lookup"><span data-stu-id="e4348-107">Additionally, you can maintain certain pre-created aggregations of the data for faster aggregated queries.</span></span>  
  
 <span data-ttu-id="e4348-108">一般而言，您必須耗費許多開發精力來實作資料倉儲，才能達成這個功能。</span><span class="sxs-lookup"><span data-stu-id="e4348-108">Typically, you achieve such functionality by an extensive development effort to implement a data warehouse.</span></span> <span data-ttu-id="e4348-109">但是，Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 BAM 卻可根據您的活動和檢視定義，自動產生 SQL 和 OLAP 基礎結構，而大幅簡化了這個程序。</span><span class="sxs-lookup"><span data-stu-id="e4348-109">BAM in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] greatly simplifies this process, however, by automatically generating the SQL and OLAP infrastructure based on your activity and view definitions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4348-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="e4348-110">In This Section</span></span>  
  
-   [<span data-ttu-id="e4348-111">何謂 BAM 定義？</span><span class="sxs-lookup"><span data-stu-id="e4348-111">What Is a BAM Definition?</span></span>](../core/what-is-a-bam-definition.md)  
  
-   [<span data-ttu-id="e4348-112">何謂 BAM 定義結構描述</span><span class="sxs-lookup"><span data-stu-id="e4348-112">What Is a BAM Definition Schema?</span></span>](../core/what-is-a-bam-definition-schema.md)  
  
-   [<span data-ttu-id="e4348-113">活動資料儲存區</span><span class="sxs-lookup"><span data-stu-id="e4348-113">Activity Data Storage</span></span>](../core/activity-data-storage.md)  
  
-   [<span data-ttu-id="e4348-114">什麼是彙總？</span><span class="sxs-lookup"><span data-stu-id="e4348-114">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)  
  
-   [<span data-ttu-id="e4348-115">查詢 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="e4348-115">Querying BAM Data</span></span>](../core/querying-bam-data.md)  
  
-   [<span data-ttu-id="e4348-116">BAM 基礎結構限制</span><span class="sxs-lookup"><span data-stu-id="e4348-116">BAM Infrastructure Limitations</span></span>](../core/bam-infrastructure-limitations.md)  
  
-   [<span data-ttu-id="e4348-117">如何在非英文的安裝中定義超出範圍的數字維度警示</span><span class="sxs-lookup"><span data-stu-id="e4348-117">How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations</span></span>](../core/define-out-of-range-numeric-dimension-alerts-in-non-english-installations--bam.md)