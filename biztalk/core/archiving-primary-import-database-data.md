---
title: 封存主要匯入資料庫資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Primary Import database [BAM], archiving data
- archived data, BAM
- managing [BAM], archiving data
- data, archiving [BAM]
ms.assetid: 4a014a59-0578-41fa-9441-8b582f54bbe8
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0fdfd55681fabd1b6cfc72f68b7e33150a121f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230414"
---
# <a name="archiving-primary-import-database-data"></a><span data-ttu-id="ce6e5-102">封存主要匯入資料庫資料</span><span class="sxs-lookup"><span data-stu-id="ce6e5-102">Archiving Primary Import Database Data</span></span>
<span data-ttu-id="ce6e5-103">系統管理員可以指定主要匯入資料庫中，活動執行個體資料的封存時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-103">An administrator can specify the time window for archiving activity instance data in the primary import database.</span></span> <span data-ttu-id="ce6e5-104">請使用 BAMPrimaryImport 資料庫 BAM_Metadata_Activities 資料表中的 OnlineWindowTimeUnit 和 OnlineWindowTimeLength 屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-104">You use the OnlineWindowTimeUnit and OnlineWindowTimeLength properties in the BAM_Metadata_Activities table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="ce6e5-105">若商務使用者已部署多個活動，您可以針對每個活動指定不同的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-105">If business users have deployed multiple activities, you can specify a different time window for each activity.</span></span> <span data-ttu-id="ce6e5-106">如需部署活動的相關資訊，請參閱 「 定義商務活動 」*資訊工作者使用者手冊 》*。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-106">For information about deploying activities, see "Defining a Business Activity" in *Information Workers Users Guide*.</span></span>  
  
 <span data-ttu-id="ce6e5-107">下表說明 OnlineWindowTimeUnit 和 OnlineWindowTimeLength 可用的值。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-107">The following table describes the values you can use for OnlineWindowTimeUnit and OnlineWindowTimeLength.</span></span>  
  
|<span data-ttu-id="ce6e5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ce6e5-108">Property</span></span>|<span data-ttu-id="ce6e5-109">值</span><span class="sxs-lookup"><span data-stu-id="ce6e5-109">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="ce6e5-110">OnlineWindowTimeUnit</span><span class="sxs-lookup"><span data-stu-id="ce6e5-110">OnlineWindowTimeUnit</span></span>|<span data-ttu-id="ce6e5-111">這個屬性可以是： 月、 日、 小時或分鐘。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-111">This property can be: month, day, hour, or minute.</span></span> <span data-ttu-id="ce6e5-112">此屬性的預設值是月。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-112">The default value of this property is month.</span></span>|  
|<span data-ttu-id="ce6e5-113">OnlineWindowTimeLength</span><span class="sxs-lookup"><span data-stu-id="ce6e5-113">OnlineWindowTimeLength</span></span>|<span data-ttu-id="ce6e5-114">此屬性必須是整數。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-114">This property must be an integer.</span></span> <span data-ttu-id="ce6e5-115">這個屬性的預設值為 6。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-115">The default value of this property is 6.</span></span>|  
  
 <span data-ttu-id="ce6e5-116">當分割比線上視窗還要舊時 (目前時間 - OnlineWindowTimeLength 個 OnlineWindowTimeUnit)，BAM 會將分割所代表的資料移出 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-116">BAM moves data out of the BAM primary import database by partition, when the partition is older than the online window (current time - OnlineWindowTimeLength of OnlineWindowTimeUnit).</span></span> <span data-ttu-id="ce6e5-117">例如，假設 OnlineWindowTimeLength = 5 且 OnlineWindowTimeUnit = 日，便會移除 5 天前的分割。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-117">For example, for OnlineWindowTimeLength = 5 and OnlineWindowTimeUnit = day, partitions older than 5 days are removed.</span></span>  
  
 <span data-ttu-id="ce6e5-118">BAM 會將封存的活動執行個體資料移至 BAM 封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-118">BAM moves archived activity instance data into the BAM archiving database.</span></span> <span data-ttu-id="ce6e5-119">BAM 封存資料庫是在設定 BizTalk BAM 組態期間指定的。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-119">You specify the BAM archiving database during BizTalk BAM Configuration.</span></span> <span data-ttu-id="ce6e5-120">如需 BizTalk BAM 組態資訊，請參閱[BAM 組態結構描述](../core/bam-configuration-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-120">For information about BizTalk BAM configuration, see [BAM Configuration Schema](../core/bam-configuration-schema.md).</span></span>  
  
 <span data-ttu-id="ce6e5-121">若您並未執行將執行個體資料處理至活動 Cube 中的 BAM Cube 更新「資料轉換服務」(DTS) 封裝，則 BAM 不會封存活動執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-121">BAM will not archive activity instance data if you have not run the BAM cube update Data Transformation Services (DTS) package, which processes the instance data into the activity cube.</span></span>  
  
 <span data-ttu-id="ce6e5-122">如需執行 BAM 資料維護 DTS 封裝的詳細資訊，請參閱[BAM DTS 封裝](../core/bam-dts-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-122">For information about running the BAM data maintenance DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).</span></span>  
  
 <span data-ttu-id="ce6e5-123">經過一段時間 BAMArchive 資料庫會成長的大小增加活動執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-123">Over time the BAMArchive database will grow in size as activity instance data is added.</span></span> <span data-ttu-id="ce6e5-124">雖然沒有直接的方式截斷整個資料庫，您可以定期截斷資料庫交易記錄，以減少儲存需求，並定期備份和封存整個 BAMArchive 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-124">Although there is no straightforward way to truncate an entire database, you can periodically truncate the database transaction log to reduce the storage requirements, and you can periodically back up and archive the entire BAMArchive database.</span></span> <span data-ttu-id="ce6e5-125">「 截斷交易記錄檔 」，請參閱 SQL Server 線上叢書 》 中的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6e5-125">See “Truncating the transaction log” in SQL Server Books Online for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6e5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6e5-126">See Also</span></span>  
 <span data-ttu-id="ce6e5-127">[定義時間間隔和時間配量屬性](../core/defining-the-time-window-and-time-slice-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ce6e5-127">[Defining the Time Window and Time Slice Properties](../core/defining-the-time-window-and-time-slice-properties.md) </span></span>  
 [<span data-ttu-id="ce6e5-128">管理 BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="ce6e5-128">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)