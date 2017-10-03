---
title: "步驟 3： 將篩選加入 Insert 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a1e9ef-a179-42a7-b4ae-b1170181053b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fc32fe7dd657bb45edca91fda0eddaa537b32a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-a-filter-for-insert-notifications"></a><span data-ttu-id="a6bbc-102">步驟 3： 將篩選加入 Insert 通知</span><span class="sxs-lookup"><span data-stu-id="a6bbc-102">Step 3: Add a Filter for Insert Notifications</span></span>
<span data-ttu-id="a6bbc-103">![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="a6bbc-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="a6bbc-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="a6bbc-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="a6bbc-105">**目標：**此步驟中，在您加入至篩選的插入作業的通知訊息的協調流程 「 決定 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-105">**Objective:** In this step, you add a Decide shape to the orchestration to filter for notification messages for Insert operation.</span></span> <span data-ttu-id="a6bbc-106">協調流程中的後續作業會執行才收到通知的插入類型。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-106">Subsequent operations in the orchestration are performed only if the notification received is of Insert type.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6bbc-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="a6bbc-107">Prerequisites</span></span>  
 <span data-ttu-id="a6bbc-108">您必須先完成[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-108">You must have completed [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span></span>  
  
### <a name="to-filter-for-notification-messages"></a><span data-ttu-id="a6bbc-109">若要篩選的通知訊息</span><span class="sxs-lookup"><span data-stu-id="a6bbc-109">To filter for notification messages</span></span>  
  
1.  <span data-ttu-id="a6bbc-110">新增**決定**圖形至協調流程之後,**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-110">Add a **Decide** shape to the orchestration, after the **Expression** shape.</span></span> <span data-ttu-id="a6bbc-111">從 [工具箱] 拖曳**決定**圖形正下方的連接線到**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-111">From the Toolbox, drag the **Decide** shape onto the connecting line directly below the **Expression** shape.</span></span>  
  
     <span data-ttu-id="a6bbc-112">**決定**圖形展開會顯示分支**如果**陳述式**([rule_1])**和分支**Else**陳述式。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-112">The **Decide** shape expands to show a branch for the **If** statement **(Rule_1)** and a branch for the **Else** statement.</span></span>  
  
2.  <span data-ttu-id="a6bbc-113">設計介面上，以滑鼠右鍵按一下**決定**圖形，，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-113">On the design surface, right-click the **Decide** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="a6bbc-114">在**屬性**窗格**決定**圖形，在**名稱**屬性中，輸入`CheckNotification`。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-114">In the **Properties** pane for the **Decide** shape, in the **Name** property, type `CheckNotification`.</span></span>  
  
4.  <span data-ttu-id="a6bbc-115">設計介面上，以滑鼠右鍵按一下**Rule_1**圖形 (內**決定**圖形)，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-115">On the design surface, right-click the **Rule_1** shape (inside of the **Decide** shape), and then click **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="a6bbc-116">在**屬性**窗格**Rule_1**，請在**名稱**屬性中，輸入**插入**。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-116">In the **Properties** pane for **Rule_1**, in the **Name** property, type **Insert**.</span></span>  
  
6.  <span data-ttu-id="a6bbc-117">以滑鼠右鍵按一下**插入**圖形，，然後按一下**編輯布林值運算式**。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-117">Right-click the **Insert** shape, and then click **Edit Boolean Expression**.</span></span>  
  
7.  <span data-ttu-id="a6bbc-118">在 BizTalk 運算式編輯器 」 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="a6bbc-118">In the BizTalk Expression Editor, type the following:</span></span>  
  
    ```  
    NotificationType.Equals("Insert")  
    ```  
  
     <span data-ttu-id="a6bbc-119">這種狀況會告訴執行後續的作業，只有當協調流程中的值**notificationtype 而**變數是**插入**。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-119">This condition tells the orchestration to perform subsequent operations only if the value in the **NotificationType** variable is **Insert**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6bbc-120">加入這個變數中的[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)擷取 SQL Server 資料庫從收到的通知訊息的通知類型。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-120">You added this variable in [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) to extract the type of notification from the notification message received from the SQL Server database.</span></span>  
  
8.  <span data-ttu-id="a6bbc-121">下圖顯示進行中協調流程**決定**包含圖形。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-121">The following figure shows the in-progress orchestration with the **Decide** shape included.</span></span>  
  
     <span data-ttu-id="a6bbc-122">![新增 「 決定 」 圖形至協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")</span><span class="sxs-lookup"><span data-stu-id="a6bbc-122">![Add a Decide shape to the orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="a6bbc-123">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="a6bbc-123">What did I just do?</span></span>  
 <span data-ttu-id="a6bbc-124">在此步驟中，您已新增**決定**圖形以篩選來通知收到是用於插入作業時，才執行後續作業的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-124">In this step, you added a **Decide** shape to filter the notification messages to perform subsequent operations only if the notification received is for Insert operations.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a6bbc-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a6bbc-125">Next Steps</span></span>  
 <span data-ttu-id="a6bbc-126">在下一個步驟中，您將協調流程圖形來叫用 UPDATE_EMPLOYE 在員工資料表、 預存程序中所述[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)。</span><span class="sxs-lookup"><span data-stu-id="a6bbc-126">In the next step, you add orchestration shapes to invoke the UPDATE_EMPLOYE stored procedure on the Employee table, as described in [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bbc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6bbc-127">See Also</span></span>  
 <span data-ttu-id="a6bbc-128">[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span><span class="sxs-lookup"><span data-stu-id="a6bbc-128">[Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span></span>  
 [<span data-ttu-id="a6bbc-129">第 2 課： 接收和篩選器通知</span><span class="sxs-lookup"><span data-stu-id="a6bbc-129">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)