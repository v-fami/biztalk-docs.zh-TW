---
title: "建立追蹤設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, creating
- creating, tracking profiles
ms.assetid: 62598529-9763-4c73-acbe-06ce5650134a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ce1edcab724201dc03792a37b0b796625201351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-tracking-profiles"></a><span data-ttu-id="67e63-102">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="67e63-102">Creating Tracking Profiles</span></span>
<span data-ttu-id="67e63-103">您可以建立新的追蹤設定檔，也可以修改現有的設定檔，加強對組織特定商務程序的管理與監控。</span><span class="sxs-lookup"><span data-stu-id="67e63-103">You create a new tracking profile or modify an existing one to better manage and monitor a specific business process for your organization.</span></span> <span data-ttu-id="67e63-104">追蹤設定檔編輯器 (TPE) 可以讓您定義要收集的資料，以符合商務分析師的需求。</span><span class="sxs-lookup"><span data-stu-id="67e63-104">The Tracking Profile Editor (TPE) allows you to define the data to collect to meet the business analyst's requirement.</span></span> <span data-ttu-id="67e63-105">您建立或修改的設定檔可以很簡單，也可以很複雜，需視您的商務需求而定。</span><span class="sxs-lookup"><span data-stu-id="67e63-105">The profile you create or modify can be as simple or as complex as you like depending on your business requirements.</span></span>  
  
 <span data-ttu-id="67e63-106">身為開發人員，您可以根據 BAM 活動定義建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="67e63-106">As a developer, you create a new profile based on a BAM activity definition.</span></span> <span data-ttu-id="67e63-107">已部署的活動定義可能已經具有為它所定義的設定檔。</span><span class="sxs-lookup"><span data-stu-id="67e63-107">A deployed activity definition may already have a profile defined for it.</span></span> <span data-ttu-id="67e63-108">如果沒有，請執行下列工作以建立追蹤設定檔：</span><span class="sxs-lookup"><span data-stu-id="67e63-108">If not, you create a tracking profile by performing these tasks:</span></span>  
  
-   <span data-ttu-id="67e63-109">選取部署伺服器與資料庫</span><span class="sxs-lookup"><span data-stu-id="67e63-109">Selecting a deployment server and database</span></span>  
  
-   <span data-ttu-id="67e63-110">從 BizTalk 管理資料庫中選取已部署的 BAM 活動定義</span><span class="sxs-lookup"><span data-stu-id="67e63-110">Selecting a deployed BAM activity definition from the BizTalk Management database</span></span>  
  
-   <span data-ttu-id="67e63-111">定義要從協調流程擷取的資料</span><span class="sxs-lookup"><span data-stu-id="67e63-111">Defining the data to be extracted from the orchestration</span></span>  
  
-   <span data-ttu-id="67e63-112">連接活動 (如果商務程序的實際實作橫跨一個以上的協調流程)</span><span class="sxs-lookup"><span data-stu-id="67e63-112">Connecting activities, if the actual implementation of your business process spans more than one orchestration</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67e63-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="67e63-113">In This Section</span></span>  
  
-   [<span data-ttu-id="67e63-114">如何建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="67e63-114">How to Create a Tracking Profile</span></span>](../core/how-to-create-a-tracking-profile.md)  
  
-   [<span data-ttu-id="67e63-115">如何對應事件來源</span><span class="sxs-lookup"><span data-stu-id="67e63-115">How to Map Event Sources</span></span>](../core/how-to-map-event-sources.md)  
  
-   [<span data-ttu-id="67e63-116">如何對應項目資料</span><span class="sxs-lookup"><span data-stu-id="67e63-116">How to Map Item Data</span></span>](../core/how-to-map-item-data.md)  
  
-   [<span data-ttu-id="67e63-117">如何建立接續</span><span class="sxs-lookup"><span data-stu-id="67e63-117">How to Create a Continuation</span></span>](../core/how-to-create-a-continuation.md)  
  
-   [<span data-ttu-id="67e63-118">如何對應多個組件</span><span class="sxs-lookup"><span data-stu-id="67e63-118">How to Map Multiple Assemblies</span></span>](../core/how-to-map-multiple-assemblies.md)  
  
-   [<span data-ttu-id="67e63-119">如何套用和移除追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="67e63-119">How to Apply and Remove a Tracking Profile</span></span>](../core/how-to-apply-and-remove-a-tracking-profile.md)