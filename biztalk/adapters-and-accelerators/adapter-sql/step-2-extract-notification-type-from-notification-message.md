---
title: 步驟 2： 擷取通知訊息的通知類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72f3e805-0f5f-42fa-8fe3-78ccbb375f74
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a4fd5e96c3593d3f47ed3c7dfc1875efca7c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224158"
---
# <a name="step-2-extract-notification-type-from-notification-message"></a><span data-ttu-id="4e95f-102">步驟 2： 擷取通知訊息的通知類型</span><span class="sxs-lookup"><span data-stu-id="4e95f-102">Step 2: Extract Notification Type from Notification Message</span></span>
<span data-ttu-id="4e95f-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="4e95f-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="4e95f-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="4e95f-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="4e95f-105">**目標：** 在此步驟中，您可以新增 「 運算式 」 圖形，以擷取從 SQL Server 資料庫接收的通知類型。</span><span class="sxs-lookup"><span data-stu-id="4e95f-105">**Objective:** In this step, you add an expression shape to extract the type of notification received from the SQL Server database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e95f-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="4e95f-106">Prerequisites</span></span>  
 <span data-ttu-id="4e95f-107">您必須先完成[步驟 1： 新增至接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="4e95f-107">You must have completed [Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span></span>  
  
### <a name="to-extract-the-notification-type-from-the-notification-message"></a><span data-ttu-id="4e95f-108">擷取通知訊息的通知類型</span><span class="sxs-lookup"><span data-stu-id="4e95f-108">To extract the notification type from the notification message</span></span>  
  
1.  <span data-ttu-id="4e95f-109">將變數加入至您在建立 BizTalk 協調流程[步驟 1： 新增至接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="4e95f-109">Add a variable to the BizTalk orchestration you created in [Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span></span>  
  
    1.  <span data-ttu-id="4e95f-110">從協調流程] 檢視中，以滑鼠右鍵按一下**變數**，然後按一下 [**新變數**。</span><span class="sxs-lookup"><span data-stu-id="4e95f-110">From the Orchestration View, right-click **Variables**, and then click **New Variable**.</span></span>  
  
    2.  <span data-ttu-id="4e95f-111">以滑鼠右鍵按一下新的變數， **Variable_1**，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="4e95f-111">Right-click the new variable, **Variable_1**, and click **Properties Window**.</span></span> <span data-ttu-id="4e95f-112">設定變數的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="4e95f-112">Set the following properties for the variable.</span></span>  
  
        |<span data-ttu-id="4e95f-113">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="4e95f-113">Set this property</span></span>|<span data-ttu-id="4e95f-114">此值</span><span class="sxs-lookup"><span data-stu-id="4e95f-114">To this value</span></span>|  
        |-----------------------|-------------------|  
        |<span data-ttu-id="4e95f-115">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="4e95f-115">**Identifier**</span></span>|<span data-ttu-id="4e95f-116">Notificationtype 而</span><span class="sxs-lookup"><span data-stu-id="4e95f-116">NotificationType</span></span>|  
        |<span data-ttu-id="4e95f-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="4e95f-117">**Type**</span></span>|<span data-ttu-id="4e95f-118">System.String</span><span class="sxs-lookup"><span data-stu-id="4e95f-118">System.String</span></span>|  
  
2.  <span data-ttu-id="4e95f-119">新增**運算式**BizTalk 協調流程的圖形。</span><span class="sxs-lookup"><span data-stu-id="4e95f-119">Add an **Expression** shape to the BizTalk orchestration.</span></span> <span data-ttu-id="4e95f-120">從協調流程 [工具箱] 中，拖曳**運算式**圖形至協調流程設計介面，和卸除它後**接收**圖形</span><span class="sxs-lookup"><span data-stu-id="4e95f-120">From the orchestration Toolbox, drag the **Expression** shape to the orchestration design surface, and drop it after the **Receive** shape</span></span>  
  
     <span data-ttu-id="4e95f-121">內**運算式**圖形，將 xpath 查詢來擷取從 SQL Server 所接收的通知訊息類型。</span><span class="sxs-lookup"><span data-stu-id="4e95f-121">Within the **Expression** shape, you will add an xpath query to extract the type of notification message received from SQL Server.</span></span> <span data-ttu-id="4e95f-122">在之前建立 xpath 查詢，讓我們看看通知訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="4e95f-122">Before creating an xpath query, let us look at the format of a notification message.</span></span> <span data-ttu-id="4e95f-123">典型的通知訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e95f-123">A typical notification message resembles the following:</span></span>  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
3.  <span data-ttu-id="4e95f-124">您看到的通知類型的相關資訊可內`<info>`標記，在父系`<Notification>`標記。</span><span class="sxs-lookup"><span data-stu-id="4e95f-124">As you see, the information about the type of the notification is available within the `<info>` tag, within the parent `<Notification>` tag.</span></span> <span data-ttu-id="4e95f-125">因此，加入下列 xpath 查詢內**運算式**圖形：</span><span class="sxs-lookup"><span data-stu-id="4e95f-125">So, add the following xpath query within the **Expression** shape:</span></span>  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     <span data-ttu-id="4e95f-126">在這裡， **notificationtype 而**是您建立來儲存值的 xpath 查詢所擷取的變數。</span><span class="sxs-lookup"><span data-stu-id="4e95f-126">Here, **NotificationType** is the variable you created to store the value extracted by the xpath query.</span></span> <span data-ttu-id="4e95f-127">**NotifyReceive**是您在建立的訊息[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="4e95f-127">**NotifyReceive** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) to receive notification messages.</span></span>  
  
4.  <span data-ttu-id="4e95f-128">下圖顯示進行中協調流程**運算式**包含圖形。</span><span class="sxs-lookup"><span data-stu-id="4e95f-128">The following figure shows the in-progress orchestration with the **Expression** shape included.</span></span>  
  
     <span data-ttu-id="4e95f-129">![新增 「 運算式 」 圖形至協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")</span><span class="sxs-lookup"><span data-stu-id="4e95f-129">![Add an Expression shape to the orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="4e95f-130">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="4e95f-130">What did I just do?</span></span>  
 <span data-ttu-id="4e95f-131">在此步驟中，您已新增**運算式**圖形以解壓縮 SQL Server 資料庫從收到的通知類型。</span><span class="sxs-lookup"><span data-stu-id="4e95f-131">In this step, you added an **Expression** shape to extract the kind of notification received from the SQL Server database.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4e95f-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4e95f-132">Next Steps</span></span>  
 <span data-ttu-id="4e95f-133">中所述，新增決定圖形插入通知篩選[步驟 3： 將篩選加入插入通知](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)。</span><span class="sxs-lookup"><span data-stu-id="4e95f-133">You add a Decide shape to filter for Insert notifications, as described in [Step 3: Add a Filter for Insert Notifications](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e95f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e95f-134">See Also</span></span>  
 <span data-ttu-id="4e95f-135">[步驟 1： 加入以接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md) </span><span class="sxs-lookup"><span data-stu-id="4e95f-135">[Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md) </span></span>  
 <span data-ttu-id="4e95f-136">[步驟 3： 將篩選加入 Insert 通知](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="4e95f-136">[Step 3: Add a Filter for Insert Notifications](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md) </span></span>  
 [<span data-ttu-id="4e95f-137">第 2 課： 接收和篩選器通知</span><span class="sxs-lookup"><span data-stu-id="4e95f-137">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)