---
title: 協調流程凍結效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ab92e0e-6a33-4aaa-ab14-0c82322b04d5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e81052f0061ff4ad802a084536c09d48cb6cb55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263782"
---
# <a name="orchestration-dehydration-performance-counters"></a><span data-ttu-id="adf82-102">協調流程凍結效能計數器</span><span class="sxs-lookup"><span data-stu-id="adf82-102">Orchestration Dehydration Performance Counters</span></span>
<span data-ttu-id="adf82-103">下表列出監視凍結行為專用之「協調流程引擎」效能計數器的名稱。</span><span class="sxs-lookup"><span data-stu-id="adf82-103">The following table lists the names of Orchestration Engine performance counters that are specific to monitoring the behavior of dehydration.</span></span> <span data-ttu-id="adf82-104">使用 [效能監視器] 即可在調整凍結參數時觀看這些計數器。</span><span class="sxs-lookup"><span data-stu-id="adf82-104">Use Performance Monitor to watch these counters while tuning your dehydration parameters.</span></span>  
  
|<span data-ttu-id="adf82-105">凍結效能計數器</span><span class="sxs-lookup"><span data-stu-id="adf82-105">Dehydration Performance Counter</span></span>|<span data-ttu-id="adf82-106">說明</span><span class="sxs-lookup"><span data-stu-id="adf82-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="adf82-107">可凍結的協調流程數</span><span class="sxs-lookup"><span data-stu-id="adf82-107">Dehydratable orchestrations</span></span>|<span data-ttu-id="adf82-108">目前由主控件執行個體裝載，而可凍結的協調流程執行個體數。</span><span class="sxs-lookup"><span data-stu-id="adf82-108">Number of orchestrations instances that can be dehydrated which are currently hosted by the host instance.</span></span>|  
|<span data-ttu-id="adf82-109">凍結中的協調流程數</span><span class="sxs-lookup"><span data-stu-id="adf82-109">Dehydrating orchestrations</span></span>|<span data-ttu-id="adf82-110">目前正在凍結的協調流程數。</span><span class="sxs-lookup"><span data-stu-id="adf82-110">Number of orchestrations that are in the process of dehydrating.</span></span>|  
|<span data-ttu-id="adf82-111">進行中凍結循環</span><span class="sxs-lookup"><span data-stu-id="adf82-111">Dehydration cycle in progress</span></span>|<span data-ttu-id="adf82-112">指示目前是否有凍結循環正在進行中。</span><span class="sxs-lookup"><span data-stu-id="adf82-112">Indicates whether there is a dehydration cycle currently in progress.</span></span>|  
|<span data-ttu-id="adf82-113">凍結循環數</span><span class="sxs-lookup"><span data-stu-id="adf82-113">Dehydration cycles</span></span>|<span data-ttu-id="adf82-114">完成的凍結循環數目。</span><span class="sxs-lookup"><span data-stu-id="adf82-114">Number of dehydration cycles completed.</span></span>|  
|<span data-ttu-id="adf82-115">凍結閾值</span><span class="sxs-lookup"><span data-stu-id="adf82-115">Dehydration threshold</span></span>|<span data-ttu-id="adf82-116">以毫秒為單位的數字，用來判斷協調流程是否適度凍結。</span><span class="sxs-lookup"><span data-stu-id="adf82-116">Number in milliseconds that determines how aggressively orchestrations are being dehydrated.</span></span> <span data-ttu-id="adf82-117">如果協調流程引擎預測某執行個體可凍結的時間長短超出此閾值，就會凍結該執行個體。</span><span class="sxs-lookup"><span data-stu-id="adf82-117">If the orchestration engine predicts that an instance will be dehydratable for an amount of time longer than this threshold, it will dehydrate the instance.</span></span>|  
|<span data-ttu-id="adf82-118">凍結的協調流程數</span><span class="sxs-lookup"><span data-stu-id="adf82-118">Orchestrations dehydrated</span></span>|<span data-ttu-id="adf82-119">自從主控件執行個體啟動之後，已凍結的協調流程執行個體數。</span><span class="sxs-lookup"><span data-stu-id="adf82-119">Number of orchestration instances dehydrated since the host instance started.</span></span>|  
|<span data-ttu-id="adf82-120">凍結的協調流程數/秒</span><span class="sxs-lookup"><span data-stu-id="adf82-120">Orchestrations dehydrated/sec</span></span>|<span data-ttu-id="adf82-121">平均每秒凍結的數目。</span><span class="sxs-lookup"><span data-stu-id="adf82-121">Average number dehydrated per second.</span></span>|  
|<span data-ttu-id="adf82-122">解除凍結的協調流程數</span><span class="sxs-lookup"><span data-stu-id="adf82-122">Orchestrations rehydrated</span></span>|<span data-ttu-id="adf82-123">自從主控件執行個體啟動之後，已解除凍結的協調流程執行個體數。</span><span class="sxs-lookup"><span data-stu-id="adf82-123">Number of orchestration instances rehydrated since the host instance started.</span></span>|  
|<span data-ttu-id="adf82-124">解除凍結的協調流程數/秒</span><span class="sxs-lookup"><span data-stu-id="adf82-124">Orchestrations rehydrated/sec</span></span>|<span data-ttu-id="adf82-125">平均每秒解除凍結的數目</span><span class="sxs-lookup"><span data-stu-id="adf82-125">Average number rehydrated per second</span></span>|  
|<span data-ttu-id="adf82-126">排程等候凍結的協調流程數</span><span class="sxs-lookup"><span data-stu-id="adf82-126">Orchestrations scheduled for dehydration</span></span>|<span data-ttu-id="adf82-127">具有擱置中凍結要求的可凍結協調流程數。</span><span class="sxs-lookup"><span data-stu-id="adf82-127">Number of dehydratable orchestrations for which there is a dehydration request pending.</span></span>|