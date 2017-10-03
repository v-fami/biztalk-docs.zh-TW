---
title: "排程批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, scheduling
- scheduling batching
ms.assetid: 037626f1-1b3b-43e6-80eb-5fb900cdbd46
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08337171897a4a78e605054e9126e8c8238d5fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scheduling-batching"></a><span data-ttu-id="6cd2e-102">排程批次</span><span class="sxs-lookup"><span data-stu-id="6cd2e-102">Scheduling Batching</span></span>
<span data-ttu-id="6cd2e-103">您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]Configuration 總管來啟動、 要求或終止輸出批次。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to activate, request, or terminate an outbound batch.</span></span> <span data-ttu-id="6cd2e-104">啟用輸出批次包含兩個步驟： 設定以時間為基礎或訊息計數準則，然後啟動輸出批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-104">Activating an outbound batch consists of two steps: configuring time-based or message count criteria and then starting the outbound batching orchestration.</span></span>  
  
 <span data-ttu-id="6cd2e-105">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**批次排程** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Schedule** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")  
  
 <span data-ttu-id="6cd2e-106">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管和排程批次處理。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-106">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and schedule batching.</span></span>  
  
### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="6cd2e-107">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="6cd2e-107">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="6cd2e-108">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本 > Accelerator for HL7**，然後按一下  **BTAHL7組態總管**。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-108">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-schedule-message-batching"></a><span data-ttu-id="6cd2e-109">若要排程訊息批次處理</span><span class="sxs-lookup"><span data-stu-id="6cd2e-109">To schedule message batching</span></span>  
  
1.  <span data-ttu-id="6cd2e-110">開啟 BTAHL7 組態檔案總管。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-110">Open BTAHL7 Configuration Explorer.</span></span>  
  
2.  <span data-ttu-id="6cd2e-111">BTAHL7 組態總管 中，在中**BTAHL7 Configuration 總管**對話方塊**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**批次排程**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6cd2e-111">In BTAHL7 Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Schedule** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6cd2e-112">使用</span><span class="sxs-lookup"><span data-stu-id="6cd2e-112">Use this</span></span>|<span data-ttu-id="6cd2e-113">動作</span><span class="sxs-lookup"><span data-stu-id="6cd2e-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6cd2e-114">**第一次批次之前的小時**</span><span class="sxs-lookup"><span data-stu-id="6cd2e-114">**Hours before first batch**</span></span>|<span data-ttu-id="6cd2e-115">輸入第一個批次之前啟動的時數。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-115">Type the number of hours before the first batch is to start.</span></span>|  
    |<span data-ttu-id="6cd2e-116">**重複之後的批次**</span><span class="sxs-lookup"><span data-stu-id="6cd2e-116">**Repeat Batch After**</span></span>|<span data-ttu-id="6cd2e-117">選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="6cd2e-117">Select one of the following:</span></span><br /><br /> <span data-ttu-id="6cd2e-118">-   **小時**。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-118">-   **Hours**.</span></span> <span data-ttu-id="6cd2e-119">輸入重複執行批次程序的時數。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-119">Type the number of hours to repeat the batch process.</span></span><br /><span data-ttu-id="6cd2e-120">-   **訊息**。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-120">-   **Messages**.</span></span> <span data-ttu-id="6cd2e-121">型別要處理下一個批次程序之前的訊息數目開始。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-121">Type the number of messages you want to process before the next batch process begins.</span></span>|  
    |<span data-ttu-id="6cd2e-122">**批次控制項**</span><span class="sxs-lookup"><span data-stu-id="6cd2e-122">**Batch Control**</span></span>|<span data-ttu-id="6cd2e-123">選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="6cd2e-123">Select one of the following:</span></span><br /><br /> <span data-ttu-id="6cd2e-124">-   **啟動排程**： 選取批次排程的開始。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-124">-   **Start Schedule**: Select to start the batch schedule.</span></span><br /><span data-ttu-id="6cd2e-125">-   **立即傳送**： 選取来啟動批次立即處理。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-125">-   **Send Now**: Select to start the batch process immediately.</span></span><br /><span data-ttu-id="6cd2e-126">-   **停止排程**： 選取即可停止目前的批次排程。</span><span class="sxs-lookup"><span data-stu-id="6cd2e-126">-   **Stop Schedule**: Select to stop the current batch schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cd2e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cd2e-127">See Also</span></span>  
 [<span data-ttu-id="6cd2e-128">設定批次處理通知</span><span class="sxs-lookup"><span data-stu-id="6cd2e-128">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)