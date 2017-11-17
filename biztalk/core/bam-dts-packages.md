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
ms.openlocfilehash: 105d1b42848b73505d9a82df07693111708ce802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dts-packages"></a><span data-ttu-id="44712-102">BAM DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="44712-102">BAM DTS Packages</span></span>
<span data-ttu-id="44712-103">系統管理員可以更新下列 BAM DTS 封裝的參數：</span><span class="sxs-lookup"><span data-stu-id="44712-103">An administrator can update parameters for the following BAM DTS packages:</span></span>  
  
-   <span data-ttu-id="44712-104">**CubeUpdate** Data Transformation Services (DTS) 封裝永遠位於與星狀結構描述資料庫相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="44712-104">The **CubeUpdate** Data Transformation Services (DTS) package is always located on the same server as the Star Schema database.</span></span>  
  
-   <span data-ttu-id="44712-105">**DataMaintenance** DTS 封裝永遠位於主要匯入資料庫與相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="44712-105">The **DataMaintenance** DTS package is always located on the same server as the Primary Import database.</span></span>  
  
 <span data-ttu-id="44712-106">DTS 封裝在 BAMConfiguration.xml 檔案中使用下列參數。</span><span class="sxs-lookup"><span data-stu-id="44712-106">The DTS packages use the following parameters in the BAMConfiguration.xml file.</span></span>  
  
|<span data-ttu-id="44712-107">參數</span><span class="sxs-lookup"><span data-stu-id="44712-107">Parameter</span></span>|<span data-ttu-id="44712-108">Description</span><span class="sxs-lookup"><span data-stu-id="44712-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44712-109">ConnectionTimeOut</span><span class="sxs-lookup"><span data-stu-id="44712-109">ConnectionTimeOut</span></span>|<span data-ttu-id="44712-110">DTS 連線逾時值 (以秒為單位) 是整數。</span><span class="sxs-lookup"><span data-stu-id="44712-110">The DTS connection time out value (in seconds) is an integer.</span></span> <span data-ttu-id="44712-111">如果省略 ConnectionTimeOut 參數，組態檔案就會使用 60 秒 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="44712-111">If you omit the ConnectionTimeOut parameter, the configuration file uses 60 seconds, the default value.</span></span>|  
|<span data-ttu-id="44712-112">加密</span><span class="sxs-lookup"><span data-stu-id="44712-112">Encryption</span></span>|<span data-ttu-id="44712-113">DTS 封裝轉換資料時，預設不會加密資料 (Encryption 值為 0)。</span><span class="sxs-lookup"><span data-stu-id="44712-113">By default, the DTS packages do not encrypt data while they transform the data (Encryption value is 0).</span></span> <span data-ttu-id="44712-114">將 Encryption 設定為 1，即可在轉換期間加密資料。</span><span class="sxs-lookup"><span data-stu-id="44712-114">Set Encryption to 1 to encrypt the data during transformation.</span></span>|  
|<span data-ttu-id="44712-115">OwnerPassword</span><span class="sxs-lookup"><span data-stu-id="44712-115">OwnerPassword</span></span>|<span data-ttu-id="44712-116">DTS 封裝擁有者的密碼。</span><span class="sxs-lookup"><span data-stu-id="44712-116">The password for the DTS package owner.</span></span> <span data-ttu-id="44712-117">DTS 封裝擁有者可以開啟和修改 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="44712-117">DTS package owners can open and modify DTS packages.</span></span> <span data-ttu-id="44712-118">如需 DTS 封裝擁有者的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="44712-118">For information about DTS package owners, see SQL Server Books Online.</span></span>|  
|<span data-ttu-id="44712-119">UserPassword</span><span class="sxs-lookup"><span data-stu-id="44712-119">UserPassword</span></span>|<span data-ttu-id="44712-120">DTS 使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="44712-120">The password for the DTS user.</span></span> <span data-ttu-id="44712-121">DTS 封裝使用者可以執行 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="44712-121">DTS package users can run DTS packages.</span></span> <span data-ttu-id="44712-122">如需 DTS 封裝使用者的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="44712-122">For information about DTS package users, see SQL Server Books Online.</span></span>|  
  
 <span data-ttu-id="44712-123">DTS 封裝在 BAMConfiguration.xml 檔案中使用下列命名慣例：</span><span class="sxs-lookup"><span data-stu-id="44712-123">The DTS packages use the following naming conventions in the BAMConfiguration.xml file:</span></span>  
  
-   <span data-ttu-id="44712-124">**CubeUpdate** DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="44712-124">**CubeUpdate** DTS package</span></span>  
  
     <span data-ttu-id="44712-125">**bam_AN_\<** </span><span class="sxs-lookup"><span data-stu-id="44712-125">**bam_AN_\<** </span></span>  
     <span data-ttu-id="44712-126">***CubeName* >**，其中 CubeName 是 cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="44712-126">***CubeName* >**, where CubeName is the name of the cube.</span></span> <span data-ttu-id="44712-127">BAM 活頁簿會從檢視名稱產生 Cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="44712-127">The BAM workbook generates the cube name from the view name.</span></span> <span data-ttu-id="44712-128">如果您修改 BAM 組態 XML 文件中的 Cube 名稱，DTS 封裝名稱就會使用新的 Cube 名稱。</span><span class="sxs-lookup"><span data-stu-id="44712-128">If you modify the cube name in the BAM configuration XML document, the new cube name is used in the DTS package name.</span></span>  
  
-   <span data-ttu-id="44712-129">**DataMaintenance** DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="44712-129">**DataMaintenance** DTS package</span></span>  
  
     <span data-ttu-id="44712-130">**bam_DM_\<** </span><span class="sxs-lookup"><span data-stu-id="44712-130">**bam_DM_\<** </span></span>  
     <span data-ttu-id="44712-131">***ActivityName* >**，其中 ActivityName 是活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="44712-131">***ActivityName* >**, where ActivityName is the name of the activity.</span></span>  
  
 <span data-ttu-id="44712-132">執行 CubeUpdate DTS 封裝，可以彙總已排程的彙總。</span><span class="sxs-lookup"><span data-stu-id="44712-132">You run the CubeUpdate DTS package to aggregate the scheduled aggregation.</span></span> <span data-ttu-id="44712-133">在下一節中，您將會指定即時資料彙總的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="44712-133">In the next section, you can specify the time window for real-time data aggregation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44712-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44712-134">See Also</span></span>  
 <span data-ttu-id="44712-135">[BAM 組態結構描述](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="44712-135">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 <span data-ttu-id="44712-136">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="44712-136">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="44712-137">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="44712-137">Managing BAM</span></span>](../core/managing-bam.md)