---
title: 批次排程 索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.batchschedule
helpviewer_keywords:
- batching, scheduling
- Batch Schedule tab [Configuration Explorer]
- scheduling batching
ms.assetid: 3792388b-6af2-41c2-8f41-bdfda7e17b2b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d870abad399dcca76c32a3a8d0e8c6637fc93284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-schedule-tab"></a><span data-ttu-id="b3eeb-102">批次排程 索引標籤</span><span class="sxs-lookup"><span data-stu-id="b3eeb-102">Batch Schedule Tab</span></span>
<span data-ttu-id="b3eeb-103">您使用**批次排程**索引標籤來啟動、 要求或終止輸出批次。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-103">You use the **Batch Schedule** tab to activate, request, or terminate an outbound batch.</span></span> <span data-ttu-id="b3eeb-104">啟用輸出批次包含兩個步驟： 設定以時間為基礎或訊息計數準則，然後啟動輸出批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-104">Activating an outbound batch consists of two steps: configuring time-based or message count criteria and then starting the outbound batching orchestration.</span></span>  
  
 <span data-ttu-id="b3eeb-105">您可以設定[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]建立輸出批次使用以時間為基礎或訊息計數的篩選條件或兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-105">You can configure [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to create an outbound batch using time-based or message count criteria or a combination of both.</span></span> <span data-ttu-id="b3eeb-106">設定批次啟動準則是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-106">Setting batch activation criteria is optional.</span></span> <span data-ttu-id="b3eeb-107">如果未指定，則您可以手動啟動批次。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-107">If not specified, you can activate a batch manually.</span></span> <span data-ttu-id="b3eeb-108">如果您想要啟用使用以時間為基礎的批次，或訊息計數準則，您必須指定這些準則，然後再啟動批次。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-108">If you want to activate a batch using time-based or message count criteria, you must specify these criteria before activating the batch.</span></span>  
  
 <span data-ttu-id="b3eeb-109">在**BTAHL7 Configuration 總管**對話方塊**批次排程**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b3eeb-109">In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Schedule** tab, do the following:</span></span>  
  
|<span data-ttu-id="b3eeb-110">使用</span><span class="sxs-lookup"><span data-stu-id="b3eeb-110">Use this</span></span>|<span data-ttu-id="b3eeb-111">動作</span><span class="sxs-lookup"><span data-stu-id="b3eeb-111">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="b3eeb-112">**第一次批次之前的小時**</span><span class="sxs-lookup"><span data-stu-id="b3eeb-112">**Hours before first batch**</span></span>|<span data-ttu-id="b3eeb-113">輸入再開始第一個批次的時數。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-113">Type the number of hours before starting the first batch.</span></span><br /><br /> <span data-ttu-id="b3eeb-114">此選項無法使用。 當您選取做為批次控制的訊息計數</span><span class="sxs-lookup"><span data-stu-id="b3eeb-114">This option is not available when you select message count as the batch control.</span></span>|  
|<span data-ttu-id="b3eeb-115">**重複之後的批次**</span><span class="sxs-lookup"><span data-stu-id="b3eeb-115">**Repeat Batch After**</span></span>|<span data-ttu-id="b3eeb-116">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="b3eeb-116">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="b3eeb-117">-                   **小時**。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-117">-                   **Hours**.</span></span> <span data-ttu-id="b3eeb-118">輸入重複執行的批次程序之前要等待時的數。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-118">Type the number of hours to wait before repeating the batch process.</span></span><br /><br /> <span data-ttu-id="b3eeb-119">-                   **訊息**。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-119">-                   **Messages**.</span></span> <span data-ttu-id="b3eeb-120">輸入您想要在啟動下一個批次之前處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-120">Type the number of messages that you want to process before initiating the next batch.</span></span>|  
|<span data-ttu-id="b3eeb-121">**批次控制項**</span><span class="sxs-lookup"><span data-stu-id="b3eeb-121">**Batch Control**</span></span>|<span data-ttu-id="b3eeb-122">使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="b3eeb-122">Use the following options:</span></span><br /><br /> <span data-ttu-id="b3eeb-123">-                   **啟動排程**： 選取此選項以啟動批次排程。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-123">-                   **Start Schedule**: Select this option to start your batch schedule.</span></span><br /><br /> <span data-ttu-id="b3eeb-124">-                   **立即傳送**： 選取此選項即可立即啟動批次程序。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-124">-                   **Send Now**: Select this option to start the batch process immediately.</span></span> <span data-ttu-id="b3eeb-125">這會覆寫**第一個批次之前的小時**和**重複批次之後**設定。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-125">This overrides the **Hours before first batch** and **Repeat Batch After** settings.</span></span><br /><br /> <span data-ttu-id="b3eeb-126">-                   **停止排程**： 選取此選項即可停止目前的批次排程。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-126">-                   **Stop Schedule**: Select this option to stop the current batch schedule.</span></span> <span data-ttu-id="b3eeb-127">這會完成目前的批次，然後停止 批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="b3eeb-127">This completes the current batch and then stops the batch orchestration.</span></span>|