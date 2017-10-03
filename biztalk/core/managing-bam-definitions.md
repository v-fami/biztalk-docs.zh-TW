---
title: "管理 BAM 定義 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions]
- definitions [BAM], managing
- definition files [BAM], managing
- managing [BAM], definitions
- managing [BAM definitions], about managing BAM definitions
ms.assetid: 7aba0e40-b8d3-4afc-9e4c-92392f1f6269
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93cf3d280d0e615442a4141b7fa41f6ee3566490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-definitions"></a><span data-ttu-id="fd2ff-102">管理 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="fd2ff-102">Managing BAM Definitions</span></span>
<span data-ttu-id="fd2ff-103">BAM 定義是 BAM 基礎結構的一部分。</span><span class="sxs-lookup"><span data-stu-id="fd2ff-103">A BAM definition is part of the BAM infrastructure.</span></span> <span data-ttu-id="fd2ff-104">其內容定義所要追蹤和彙總的資料，以及追蹤資料的商務使用者檢視。</span><span class="sxs-lookup"><span data-stu-id="fd2ff-104">It defines the data to track and aggregate, as well as the business end user's view on the tracking data.</span></span> <span data-ttu-id="fd2ff-105">本節主題說明用以管理 BAM 定義之要素的各項程序，這些要素包括活動、檢視、成品和警示。</span><span class="sxs-lookup"><span data-stu-id="fd2ff-105">The topics in this section give procedures for managing the elements of BAM definitions, which include activities, views, artifacts, and alerts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd2ff-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="fd2ff-106">In This Section</span></span>  
  
-   [<span data-ttu-id="fd2ff-107">管理 BAM 定義檔案所需的使用者權限</span><span class="sxs-lookup"><span data-stu-id="fd2ff-107">Required User Rights for Managing BAM Definition Files</span></span>](../core/required-user-rights-for-managing-bam-definition-files.md)  
  
-   [<span data-ttu-id="fd2ff-108">如何部署 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="fd2ff-108">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)  
  
-   [<span data-ttu-id="fd2ff-109">如何移除 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="fd2ff-109">How to Remove BAM Definitions</span></span>](../core/how-to-remove-bam-activities.md)  
  
-   [<span data-ttu-id="fd2ff-110">如何列出 BAM 基礎結構的變更</span><span class="sxs-lookup"><span data-stu-id="fd2ff-110">How to List Changes to the BAM Infrastructure</span></span>](../core/how-to-list-changes-to-the-bam-infrastructure.md)  
  
-   [<span data-ttu-id="fd2ff-111">如何列出 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="fd2ff-111">How to List BAM Activities</span></span>](../core/how-to-list-bam-activities.md)  
  
-   [<span data-ttu-id="fd2ff-112">如何移除 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="fd2ff-112">How to Remove BAM Activities</span></span>](../core/how-to-remove-bam-activities.md)  
  
-   [<span data-ttu-id="fd2ff-113">如何列出 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="fd2ff-113">How to List BAM Views</span></span>](../core/how-to-list-bam-views.md)  
  
-   [<span data-ttu-id="fd2ff-114">如何移除 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="fd2ff-114">How to Remove BAM Views</span></span>](../core/how-to-remove-bam-views.md)  
  
-   [<span data-ttu-id="fd2ff-115">如何啟用警示</span><span class="sxs-lookup"><span data-stu-id="fd2ff-115">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md)  
  
-   [<span data-ttu-id="fd2ff-116">如何停用警示</span><span class="sxs-lookup"><span data-stu-id="fd2ff-116">How to Disable Alerts</span></span>](../core/how-to-disable-alerts.md)  
  
-   [<span data-ttu-id="fd2ff-117">如何移除 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="fd2ff-117">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)  
  
-   [<span data-ttu-id="fd2ff-118">如何更新 BAM 成品</span><span class="sxs-lookup"><span data-stu-id="fd2ff-118">How to Update BAM Artifacts</span></span>](../core/how-to-update-bam-artifacts.md)  
  
-   [<span data-ttu-id="fd2ff-119">如何移除已部署的成品</span><span class="sxs-lookup"><span data-stu-id="fd2ff-119">How to Remove Deployed Artifacts</span></span>](../core/how-to-remove-deployed-artifacts.md)  
  
-   [<span data-ttu-id="fd2ff-120">設定 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="fd2ff-120">Configuring BAM Alerts</span></span>](../core/configuring-bam-alerts.md)  
  
-   [<span data-ttu-id="fd2ff-121">管理 BAM 警示的執行</span><span class="sxs-lookup"><span data-stu-id="fd2ff-121">Managing BAM Alert Execution</span></span>](../core/managing-bam-alert-execution.md)  
  
-   [<span data-ttu-id="fd2ff-122">如何變更評估警示的頻率</span><span class="sxs-lookup"><span data-stu-id="fd2ff-122">How to Change the Frequency With Which Alerts Are Evaluated</span></span>](../core/how-to-change-the-frequency-with-which-alerts-are-evaluated.md)