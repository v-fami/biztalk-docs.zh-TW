---
title: "BAM DTS 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DTS packages, BAM
- BAM, DTS packages
ms.assetid: bba70d81-6ddf-4f1f-a1f7-d5a5bf453bae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a71431ee800c80c6972747f09b0e2420f961e33e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bam-dts-packages"></a><span data-ttu-id="59a58-102">BAM DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="59a58-102">BAM DTS Packages</span></span>
<span data-ttu-id="59a58-103">系統管理員可以更新下列 BAM DTS 封裝的參數：</span><span class="sxs-lookup"><span data-stu-id="59a58-103">An administrator can update parameters for the following BAM DTS packages:</span></span>  
  
-   <span data-ttu-id="59a58-104">**CubeUpdate** Data Transformation Services (DTS) 封裝永遠位於與星狀結構描述資料庫相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="59a58-104">The **CubeUpdate** Data Transformation Services (DTS) package is always located on the same server as the Star Schema database.</span></span>  
  
-   <span data-ttu-id="59a58-105">**DataMaintenance** DTS 封裝永遠位於主要匯入資料庫與相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="59a58-105">The **DataMaintenance** DTS package is always located on the same server as the Primary Import database.</span></span>  
  
 <span data-ttu-id="59a58-106">DTS 封裝在 BAMConfiguration.xml 檔案中使用下列參數。</span><span class="sxs-lookup"><span data-stu-id="59a58-106">The DTS packages use the following parameters in the BAMConfiguration.xml file.</span></span>  
  
|<span data-ttu-id="59a58-107">參數</span><span class="sxs-lookup"><span data-stu-id="59a58-107">Parameter</span></span>|<span data-ttu-id="59a58-108">Description</span><span class="sxs-lookup"><span data-stu-id="59a58-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59a58-109">ConnectionTimeOut</span><span class="sxs-lookup"><span data-stu-id="59a58-109">ConnectionTimeOut</span></span>|<span data-ttu-id="59a58-110">DTS 連線逾時值 (以秒為單位) 是整數。</span><span class="sxs-lookup"><span data-stu-id="59a58-110">The DTS connection time out value (in seconds) is an integer.</span></span> <span data-ttu-id="59a58-111">如果省略 ConnectionTimeOut 參數，組態檔案就會使用 60 秒 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="59a58-111">If you omit the ConnectionTimeOut parameter, the configuration file uses 60 seconds, the default value.</span></span>|  
|<span data-ttu-id="59a58-112">加密</span><span class="sxs-lookup"><span data-stu-id="59a58-112">Encryption</span></span>|<span data-ttu-id="59a58-113">DTS 封裝轉換資料時，預設不會加密資料 (Encryption 值為 0)。</span><span class="sxs-lookup"><span data-stu-id="59a58-113">By default, the DTS packages do not encrypt data while they transform the data (Encryption value is 0).</span></span> <span data-ttu-id="59a58-114">將 Encryption 設定為 1，即可在轉換期間加密資料。</span><span class="sxs-lookup"><span data-stu-id="59a58-114">Set Encryption to 1 to encrypt the data during transformation.</span></span>|  
|<span data-ttu-id="59a58-115">OwnerPassword</span><span class="sxs-lookup"><span data-stu-id="59a58-115">OwnerPassword</span></span>|<span data-ttu-id="59a58-116">DTS 封裝擁有者的密碼。</span><span class="sxs-lookup"><span data-stu-id="59a58-116">The password for the DTS package owner.</span></span> <span data-ttu-id="59a58-117">DTS 封裝擁有者可以開啟和修改 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="59a58-117">DTS package owners can open and modify DTS packages.</span></span> <span data-ttu-id="59a58-118">如需 DTS 封裝擁有者的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="59a58-118">For information about DTS package owners, see SQL Server Books Online.</span></span>|  
|<span data-ttu-id="59a58-119">UserPassword</span><span class="sxs-lookup"><span data-stu-id="59a58-119">UserPassword</span></span>|<span data-ttu-id="59a58-120">DTS 使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="59a58-120">The password for the DTS user.</span></span> <span data-ttu-id="59a58-121">DTS 封裝使用者可以執行 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="59a58-121">DTS package users can run DTS packages.</span></span> <span data-ttu-id="59a58-122">如需 DTS 封裝使用者的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="59a58-122">For information about DTS package users, see SQL Server Books Online.</span></span>|  
  
 <span data-ttu-id="59a58-123">DTS 封裝在 BAMConfiguration.xml 檔案中使用下列命名慣例：</span><span class="sxs-lookup"><span data-stu-id="59a58-123">The DTS packages use the following naming conventions in the BAMConfiguration.xml file:</span></span>  
  
-   <span data-ttu-id="59a58-124">**CubeUpdate** DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="59a58-124">**CubeUpdate** DTS package</span></span>  
  
     <span data-ttu-id="59a58-125">**bam_AN_\<**   ***CubeName* \>** ，其中 CubeName 是 cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="59a58-125">**bam_AN_\<** ***CubeName* \>**, where CubeName is the name of the cube.</span></span> <span data-ttu-id="59a58-126">BAM 活頁簿會從檢視名稱產生 Cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="59a58-126">The BAM workbook generates the cube name from the view name.</span></span> <span data-ttu-id="59a58-127">如果您修改 BAM 組態 XML 文件中的 Cube 名稱，DTS 封裝名稱就會使用新的 Cube 名稱。</span><span class="sxs-lookup"><span data-stu-id="59a58-127">If you modify the cube name in the BAM configuration XML document, the new cube name is used in the DTS package name.</span></span>  
  
-   <span data-ttu-id="59a58-128">**DataMaintenance** DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="59a58-128">**DataMaintenance** DTS package</span></span>  
  
     <span data-ttu-id="59a58-129">**bam_DM_\<**   ***ActivityName* \>** ，其中 ActivityName 是活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="59a58-129">**bam_DM_\<** ***ActivityName* \>**, where ActivityName is the name of the activity.</span></span>  
  
 <span data-ttu-id="59a58-130">執行 CubeUpdate DTS 封裝，可以彙總已排程的彙總。</span><span class="sxs-lookup"><span data-stu-id="59a58-130">You run the CubeUpdate DTS package to aggregate the scheduled aggregation.</span></span> <span data-ttu-id="59a58-131">在下一節中，您將會指定即時資料彙總的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="59a58-131">In the next section, you can specify the time window for real-time data aggregation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a58-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="59a58-132">See Also</span></span>  
 <span data-ttu-id="59a58-133">[BAM 組態結構描述](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="59a58-133">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 <span data-ttu-id="59a58-134">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="59a58-134">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="59a58-135">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="59a58-135">Managing BAM</span></span>](../core/managing-bam.md)