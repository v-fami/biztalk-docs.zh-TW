---
title: 排程批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, scheduling
- scheduling batching
ms.assetid: 037626f1-1b3b-43e6-80eb-5fb900cdbd46
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 790cf5cb853da211d5e8928f398ecc1a2b3fe0ba
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961532"
---
# <a name="scheduling-batching"></a><span data-ttu-id="aa19a-102">排程批次</span><span class="sxs-lookup"><span data-stu-id="aa19a-102">Scheduling Batching</span></span>
<span data-ttu-id="aa19a-103">您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]Configuration 總管來啟動、 要求或終止輸出批次。</span><span class="sxs-lookup"><span data-stu-id="aa19a-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to activate, request, or terminate an outbound batch.</span></span> <span data-ttu-id="aa19a-104">啟用輸出批次包含兩個步驟： 設定以時間為基礎或訊息計數準則，然後啟動輸出批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="aa19a-104">Activating an outbound batch consists of two steps: configuring time-based or message count criteria and then starting the outbound batching orchestration.</span></span>  
  
 <span data-ttu-id="aa19a-105">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**批次排程** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="aa19a-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Schedule** tab.</span></span>  
  
 <span data-ttu-id="aa19a-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")</span><span class="sxs-lookup"><span data-stu-id="aa19a-106">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")</span></span>  
  
 <span data-ttu-id="aa19a-107">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管和排程批次處理。</span><span class="sxs-lookup"><span data-stu-id="aa19a-107">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and schedule batching.</span></span>  
  
### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="aa19a-108">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="aa19a-108">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="aa19a-109">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="aa19a-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-schedule-message-batching"></a><span data-ttu-id="aa19a-110">若要排程訊息批次處理</span><span class="sxs-lookup"><span data-stu-id="aa19a-110">To schedule message batching</span></span>  
  
1.  <span data-ttu-id="aa19a-111">開啟 BTAHL7 組態檔案總管。</span><span class="sxs-lookup"><span data-stu-id="aa19a-111">Open BTAHL7 Configuration Explorer.</span></span>  
  
2.  <span data-ttu-id="aa19a-112">BTAHL7 組態總管 中，在中**BTAHL7 Configuration 總管**對話方塊**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**批次排程**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aa19a-112">In BTAHL7 Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Schedule** tab, do the following:</span></span>  
  
    |<span data-ttu-id="aa19a-113">使用</span><span class="sxs-lookup"><span data-stu-id="aa19a-113">Use this</span></span>|<span data-ttu-id="aa19a-114">動作</span><span class="sxs-lookup"><span data-stu-id="aa19a-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aa19a-115">**第一次批次之前的小時**</span><span class="sxs-lookup"><span data-stu-id="aa19a-115">**Hours before first batch**</span></span>|<span data-ttu-id="aa19a-116">輸入第一個批次之前啟動的時數。</span><span class="sxs-lookup"><span data-stu-id="aa19a-116">Type the number of hours before the first batch is to start.</span></span>|  
    |<span data-ttu-id="aa19a-117">**重複之後的批次**</span><span class="sxs-lookup"><span data-stu-id="aa19a-117">**Repeat Batch After**</span></span>|<span data-ttu-id="aa19a-118">選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="aa19a-118">Select one of the following:</span></span><br /><br /> <span data-ttu-id="aa19a-119">-   **小時**。</span><span class="sxs-lookup"><span data-stu-id="aa19a-119">-   **Hours**.</span></span> <span data-ttu-id="aa19a-120">輸入重複執行批次程序的時數。</span><span class="sxs-lookup"><span data-stu-id="aa19a-120">Type the number of hours to repeat the batch process.</span></span><br /><span data-ttu-id="aa19a-121">-   **訊息**。</span><span class="sxs-lookup"><span data-stu-id="aa19a-121">-   **Messages**.</span></span> <span data-ttu-id="aa19a-122">型別要處理下一個批次程序之前的訊息數目開始。</span><span class="sxs-lookup"><span data-stu-id="aa19a-122">Type the number of messages you want to process before the next batch process begins.</span></span>|  
    |<span data-ttu-id="aa19a-123">**批次控制項**</span><span class="sxs-lookup"><span data-stu-id="aa19a-123">**Batch Control**</span></span>|<span data-ttu-id="aa19a-124">選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="aa19a-124">Select one of the following:</span></span><br /><br /> <span data-ttu-id="aa19a-125">-   **啟動排程**： 選取批次排程的開始。</span><span class="sxs-lookup"><span data-stu-id="aa19a-125">-   **Start Schedule**: Select to start the batch schedule.</span></span><br /><span data-ttu-id="aa19a-126">-   **立即傳送**： 選取来啟動批次立即處理。</span><span class="sxs-lookup"><span data-stu-id="aa19a-126">-   **Send Now**: Select to start the batch process immediately.</span></span><br /><span data-ttu-id="aa19a-127">-   **停止排程**： 選取即可停止目前的批次排程。</span><span class="sxs-lookup"><span data-stu-id="aa19a-127">-   **Stop Schedule**: Select to stop the current batch schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa19a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa19a-128">See Also</span></span>  
 [<span data-ttu-id="aa19a-129">設定批次處理通知</span><span class="sxs-lookup"><span data-stu-id="aa19a-129">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)