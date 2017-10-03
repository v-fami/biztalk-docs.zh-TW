---
title: "定義時間間隔和時間配量屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- managing [BAM], real-time data
- Primary Import database [BAM], time properties
- aggregations [BAM], managing
- Primary Import database [BAM], real-time data
- BAMConfiguration.xml file
- aggregations [BAM], real-time data
ms.assetid: 7f07b179-da10-4702-baf7-69516c8f16a6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d846b03866196e0a31facbbff68db50ec6a00a5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-the-time-window-and-time-slice-properties"></a><span data-ttu-id="b0608-102">定義時間間隔和時間配量屬性</span><span class="sxs-lookup"><span data-stu-id="b0608-102">Defining the Time Window and Time Slice Properties</span></span>
<span data-ttu-id="b0608-103">系統管理員可以使用 BAMConfiguration.xml 檔案中的 TimeWindow 和 TimeSlice 屬性，定義 BAM 主要匯入資料庫之即時彙總資料表中資料的存留時間。</span><span class="sxs-lookup"><span data-stu-id="b0608-103">Administrators use the TimeWindow and the TimeSlice properties in the BAMConfiguration.xml file to define the life of the data in the real-time aggregation tables in the BAM primary import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0608-104">若要使系統管理員在 BAM 組態檔案中所做的變更生效，系統管理員必須解除部署目前的 BAM 組態，然後部署已更新的 BAMConfiguration.xml。</span><span class="sxs-lookup"><span data-stu-id="b0608-104">To enact the changes they make in the BAM configuration file, administrators must undeploy the current BAM configuration, and then deploy the updated BAMConfiguration.xml.</span></span>  
  
 <span data-ttu-id="b0608-105">如需解除部署 BAM 定義，請參閱[如何移除 BAM 定義](../core/how-to-remove-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="b0608-105">For information about undeploying a BAM definition, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md).</span></span> <span data-ttu-id="b0608-106">如需部署 BAM 定義的相關資訊，請參閱[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="b0608-106">For information about deploying a BAM definition, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
 <span data-ttu-id="b0608-107">如果您只要變更 TimeWindow 和 TimeSlice 值而不解除部署 BAM 基礎結構，則可修改 BAM 主要匯入資料庫的 BAM_Metadata_Activities 資料表中對應的資料行。</span><span class="sxs-lookup"><span data-stu-id="b0608-107">If you want to change the TimeWindow and TimeSlice values without undeploying the BAM infrastructure, you can modifying the columns in the BAM_Metadata_Activities table in the BAM primary import database.</span></span>  
  
## <a name="timeslice"></a><span data-ttu-id="b0608-108">TimeSlice</span><span class="sxs-lookup"><span data-stu-id="b0608-108">TimeSlice</span></span>  
 <span data-ttu-id="b0608-109">請使用 TimeSlice 屬性將已完成的 BAM 執行個體資料分組。</span><span class="sxs-lookup"><span data-stu-id="b0608-109">You use the TimeSlice property to group completed BAM instance data.</span></span> <span data-ttu-id="b0608-110">TimeSlice 屬性根據資料寫入 BAM 主要匯入資料庫的時間，將 BAM 執行個體資料分組。</span><span class="sxs-lookup"><span data-stu-id="b0608-110">The TimeSlice property uses time that the data is written to the BAM primary import database to group BAM instance data.</span></span>  
  
 <span data-ttu-id="b0608-111">例如，執行個體 A 是完成和 BAM 主要匯入資料庫中保存在 1/1/2000年 1:02 a.m</span><span class="sxs-lookup"><span data-stu-id="b0608-111">For example, instance A is completed and persisted in the BAM primary import database at 1/1/2000 1:02 a.m.</span></span> <span data-ttu-id="b0608-112">是完成的執行個體 B，並將其保存在 BAM 主要匯入資料庫，在 1/1/2000年 1:04 a.m.</span><span class="sxs-lookup"><span data-stu-id="b0608-112">Instance B is completed and persisted in the BAM primary import database at 1/1/2000 1:04 a.m.</span></span> <span data-ttu-id="b0608-113">如果您設定 TimeSlice 屬性的值為 5 分鐘，執行個體 A 和 B 會群組在一起。</span><span class="sxs-lookup"><span data-stu-id="b0608-113">If you set the value of the TimeSlice property to five minutes, instance A and instance B are grouped together.</span></span>  
  
#### <a name="to-change-the-timeslice-value-in-the-bam-configuration-file"></a><span data-ttu-id="b0608-114">在 BAM 組態檔中變更 TimeSlice 值</span><span class="sxs-lookup"><span data-stu-id="b0608-114">To change the TimeSlice value in the BAM Configuration file</span></span>  
  
-   <span data-ttu-id="b0608-115">請變更 BAM 組態檔中這一行的值：</span><span class="sxs-lookup"><span data-stu-id="b0608-115">Change the value in this line of the BAM Configuration file:</span></span>  
  
    ```  
    <Property Name="RTATimeSlice">5</Property>  
    ```  
  
#### <a name="to-change-the-timeslice-value-in-the-bammetadataactivities-table"></a><span data-ttu-id="b0608-116">在 BAM_Metadata_Activities 資料表中變更 TimeSlice 值</span><span class="sxs-lookup"><span data-stu-id="b0608-116">To change the TimeSlice value in the BAM_Metadata_Activities table</span></span>  
  
-   <span data-ttu-id="b0608-117">請修改位於 BAMPrimaryImport 資料庫之 bam_Metadata_Activities 資料表中的 RTATimeSlice 值。</span><span class="sxs-lookup"><span data-stu-id="b0608-117">Modify the RTATimeSlice values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database.</span></span> <span data-ttu-id="b0608-118">如果您針對一或多個活動部署多個即時彙總 (RTA)，便可選擇為每個 RTA 指定不同的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b0608-118">If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0608-119">RTAWindow 的值必須是整數，且時間單位永遠為分鐘。</span><span class="sxs-lookup"><span data-stu-id="b0608-119">The value of RTAWindow must be an integer and the time unit is always minutes.</span></span>  
  
## <a name="timewindow"></a><span data-ttu-id="b0608-120">TimeWindow</span><span class="sxs-lookup"><span data-stu-id="b0608-120">TimeWindow</span></span>  
 <span data-ttu-id="b0608-121">當您執行 CubeUpdate DTS 封裝時，封裝會將資料從 BAM 主要匯入資料庫移至 BAM Cube。</span><span class="sxs-lookup"><span data-stu-id="b0608-121">When you run the CubeUpdate DTS package, the package moves data from the BAM primary import database into the BAM cubes.</span></span> <span data-ttu-id="b0608-122">一旦歸為同一群組的所有 BAM 資料執行個體都已超過 RTA 視窗屬性所指定的存留時間，封裝就會移動整組即時彙總資料。</span><span class="sxs-lookup"><span data-stu-id="b0608-122">The package moves real-time aggregation data as grouped BAM data instances after all of the data in the group is older than the age specified in the RTA window property.</span></span>  
  
#### <a name="to-change-the-timewindow-value-in-the-bam-configuration-file"></a><span data-ttu-id="b0608-123">在 BAM 組態檔中變更 TimeWindow 值</span><span class="sxs-lookup"><span data-stu-id="b0608-123">To change the TimeWindow value in the BAM Configuration file</span></span>  
  
-   <span data-ttu-id="b0608-124">請變更 BAM 組態檔中這一行的值：</span><span class="sxs-lookup"><span data-stu-id="b0608-124">Change the value in this line of the BAM Configuration file:</span></span>  
  
    ```  
    <Property Name="RTAWindow">60</Property>  
    ```  
  
#### <a name="to-change-the-timewindow-value-in-the-bammetadataactivities-table"></a><span data-ttu-id="b0608-125">在 BAM_Metadata_Activities 資料表中變更 TimeWindow 值</span><span class="sxs-lookup"><span data-stu-id="b0608-125">To change the TimeWindow value in the BAM_Metadata_Activities table</span></span>  
  
-   <span data-ttu-id="b0608-126">請修改位於 BAMPrimaryImport 資料庫之 bam_Metadata_Activities 資料表中的 RTAWindow 值。</span><span class="sxs-lookup"><span data-stu-id="b0608-126">Modify the RTAWindow values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database.</span></span> <span data-ttu-id="b0608-127">如果您針對一或多個活動部署多個即時彙總 (RTA)，便可選擇為每個 RTA 指定不同的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b0608-127">If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0608-128">RTAWindow 的值必須是整數，且時間單位永遠為分鐘。</span><span class="sxs-lookup"><span data-stu-id="b0608-128">The value of RTAWindow must be an integer and the time unit is always minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0608-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0608-129">See Also</span></span>  
 <span data-ttu-id="b0608-130">[BAM 組態結構描述](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="b0608-130">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 [<span data-ttu-id="b0608-131">BAM 安全性建議</span><span class="sxs-lookup"><span data-stu-id="b0608-131">BAM Security Recommendations</span></span>](../core/bam-security-recommendations.md)