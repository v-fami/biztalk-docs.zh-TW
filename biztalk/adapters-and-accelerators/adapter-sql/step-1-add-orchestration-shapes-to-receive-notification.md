---
title: "步驟 1： 加入以接收通知的協調流程圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e4c6fa5-81b7-4928-84d5-39533535f862
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a33693a09d89acc5d1ad9e4514c7907b789cc75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-orchestration-shapes-to-receive-notification"></a><span data-ttu-id="f8593-102">步驟 1： 加入以接收通知的協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="f8593-102">Step 1: Add Orchestration Shapes to Receive Notification</span></span>
<span data-ttu-id="f8593-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="f8593-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="f8593-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="f8593-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="f8593-105">**目標：**在此步驟中，您將收到變更通知的協調流程圖形**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="f8593-105">**Objective:** In this step, you add orchestration shapes to receive notification for changes to the **Employee** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8593-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="f8593-106">Prerequisites</span></span>  
 <span data-ttu-id="f8593-107">您必須先完成中的步驟[第 1 課： 產生的結構描述和建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="f8593-107">You must have completed the steps in [Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md).</span></span>  
  
### <a name="to-receive-notification-messages"></a><span data-ttu-id="f8593-108">若要接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="f8593-108">To receive notification messages</span></span>  
  
1.  <span data-ttu-id="f8593-109">開啟 BizTalk 協調流程**EmployeeOrch.odx**，您在加入[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="f8593-109">Open the BizTalk orchestration, **EmployeeOrch.odx**, you added in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).</span></span>  
  
2.  <span data-ttu-id="f8593-110">新增**接收**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8593-110">Add a **Receive** shape to the orchestration.</span></span> <span data-ttu-id="f8593-111">從協調流程 [工具箱] 中，拖曳**接收**圖形至協調流程設計介面，並將它放置到指示之間的空間**開始**（綠色圓形） 和**結束**（紅色八角形） 圖形。</span><span class="sxs-lookup"><span data-stu-id="f8593-111">From the orchestration Toolbox, drag the **Receive** shape to the orchestration design surface, and drop it into the space indicated between the **Begin** (green circle) and **End** (red octagon) shapes.</span></span>  
  
    |<span data-ttu-id="f8593-112">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="f8593-112">Set this property</span></span>|<span data-ttu-id="f8593-113">此值</span><span class="sxs-lookup"><span data-stu-id="f8593-113">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="f8593-114">**Activate**</span><span class="sxs-lookup"><span data-stu-id="f8593-114">**Activate**</span></span>|<span data-ttu-id="f8593-115">True</span><span class="sxs-lookup"><span data-stu-id="f8593-115">True</span></span>|  
    |<span data-ttu-id="f8593-116">**訊息**</span><span class="sxs-lookup"><span data-stu-id="f8593-116">**Message**</span></span>|<span data-ttu-id="f8593-117">NotifyReceive</span><span class="sxs-lookup"><span data-stu-id="f8593-117">NotifyReceive</span></span>|  
    |<span data-ttu-id="f8593-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f8593-118">**Name**</span></span>|<span data-ttu-id="f8593-119">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="f8593-119">ReceiveNotification</span></span>|  
  
3.  <span data-ttu-id="f8593-120">新增單向接收埠到協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8593-120">Add a one-way receive port to the orchestration.</span></span> <span data-ttu-id="f8593-121">您將使用此連接埠來接收通知訊息從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f8593-121">You will use this port to receive notification messages from the SQL Server database.</span></span> <span data-ttu-id="f8593-122">設定下列屬性的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f8593-122">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="f8593-123">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="f8593-123">Set this property</span></span>|<span data-ttu-id="f8593-124">此值</span><span class="sxs-lookup"><span data-stu-id="f8593-124">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="f8593-125">**通訊方向**</span><span class="sxs-lookup"><span data-stu-id="f8593-125">**Communication Direction**</span></span>|<span data-ttu-id="f8593-126">Receive</span><span class="sxs-lookup"><span data-stu-id="f8593-126">Receive</span></span>|  
    |<span data-ttu-id="f8593-127">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="f8593-127">**Communication Pattern**</span></span>|<span data-ttu-id="f8593-128">單向</span><span class="sxs-lookup"><span data-stu-id="f8593-128">One-Way</span></span>|  
    |<span data-ttu-id="f8593-129">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="f8593-129">**Identifier**</span></span>|<span data-ttu-id="f8593-130">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="f8593-130">ReceiveNotification</span></span>|  
  
     <span data-ttu-id="f8593-131">此外，從 Operation_1，若要變更的作業名稱**通知**。</span><span class="sxs-lookup"><span data-stu-id="f8593-131">Also, change the operation name from Operation_1 to **Notification**.</span></span>  
  
4.  <span data-ttu-id="f8593-132">連接**ReceiveNotification**埠連接到**ReceiveNotification**動作圖形。</span><span class="sxs-lookup"><span data-stu-id="f8593-132">Connect the **ReceiveNotification** port to the **ReceiveNotification** action shape.</span></span> <span data-ttu-id="f8593-133">在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。</span><span class="sxs-lookup"><span data-stu-id="f8593-133">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8593-134">在此步驟中，您使用拖放方法將連接埠連接到動作圖形。</span><span class="sxs-lookup"><span data-stu-id="f8593-134">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="f8593-135">代替使用動作圖形的作業屬性將動作圖形連接到連接埠。</span><span class="sxs-lookup"><span data-stu-id="f8593-135">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
5.  <span data-ttu-id="f8593-136">下圖顯示進行中協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8593-136">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="f8593-137">![若要接收通知訊息的協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")</span><span class="sxs-lookup"><span data-stu-id="f8593-137">![Orchestration to receive notification messages](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="f8593-138">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="f8593-138">What did I just do?</span></span>  
 <span data-ttu-id="f8593-139">在此步驟中，您可以加入協調流程圖形，並接收埠以接收通知，從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f8593-139">In this step, you added orchestration shapes and receive port to receive notification from the SQL Server database.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f8593-140">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f8593-140">Next Steps</span></span>  
 <span data-ttu-id="f8593-141">您新增 「 運算式 」 圖形至協調流程以擷取從 SQL Server 資料庫中，接收通知的類型中所述[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)。</span><span class="sxs-lookup"><span data-stu-id="f8593-141">You add an expression shape to the orchestration to extract the type of notification received from the SQL Server database, as described in [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8593-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8593-142">See Also</span></span>  
 <span data-ttu-id="f8593-143">[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span><span class="sxs-lookup"><span data-stu-id="f8593-143">[Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span></span>  
 [<span data-ttu-id="f8593-144">第 2 課： 接收和篩選器通知</span><span class="sxs-lookup"><span data-stu-id="f8593-144">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)