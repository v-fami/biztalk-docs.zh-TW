---
title: "步驟 3： 設定並啟動應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4252470-805e-404f-80d5-df8d1ff3af63
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96f26035094ee6e39b672b480525747f8aaf4ede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-and-start-the-application"></a><span data-ttu-id="e1ab4-102">步驟 3： 設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="e1ab4-102">Step 3: Configure and Start the Application</span></span>
<span data-ttu-id="e1ab4-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="e1ab4-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="e1ab4-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="e1ab4-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="e1ab4-105">**目標：**在此步驟中，設定並啟動 SampleApplication 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-105">**Objective:** In this step, you configure and start the SampleApplication application.</span></span> <span data-ttu-id="e1ab4-106">當您設定 SampleApplication 應用程式時，您將建立關聯的邏輯成品，您在建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]與其實體對應項目。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-106">When you configure the SampleApplication application, you associate the logical artifacts you created in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] with their physical counterparts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e1ab4-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="e1ab4-107">Prerequisites</span></span>  
 <span data-ttu-id="e1ab4-108">您必須先完成[步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-108">You must have completed [Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span></span>  
  
### <a name="to-configure-and-start-the-application"></a><span data-ttu-id="e1ab4-109">若要設定並啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="e1ab4-109">To configure and start the application</span></span>  
  
1.  <span data-ttu-id="e1ab4-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="e1ab4-111">在左邊主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-111">In the console tree on the left hand side, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="e1ab4-112">展開**BizTalk 群組**，依序展開**應用程式**，以滑鼠右鍵按一下**SampleApplication**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-112">Expand **BizTalk Group**, expand **Applications**, right-click **SampleApplication**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="e1ab4-113">在**設定應用程式**對話方塊**EmployeeOrch**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e1ab4-113">In the **Configure Application** dialog box, on the **EmployeeOrch** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="e1ab4-114">如**主機**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-114">For **Host** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
    2.  <span data-ttu-id="e1ab4-115">按兩下儲存格之間**ReceiveNotification**選取**NotifyReceivePort**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-115">Double-click the cell across **ReceiveNotification** and select **NotifyReceivePort** from the drop-down list.</span></span>  
  
    3.  <span data-ttu-id="e1ab4-116">按兩下儲存格之間**SQLOutboundPort**選取**SQLOutboundPort**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-116">Double-click the cell across **SQLOutboundPort** and select **SQLOutboundPort** from the drop-down list.</span></span>  
  
    4.  <span data-ttu-id="e1ab4-117">按兩下儲存格之間**SaveResponsePort**選取**EmailResponse**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-117">Double-click the cell across **SaveResponsePort** and select **EmailResponse** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="e1ab4-118">下圖顯示設定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-118">The following figure shows a configured application.</span></span>  
  
     <span data-ttu-id="e1ab4-119">![設定應用程式](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")</span><span class="sxs-lookup"><span data-stu-id="e1ab4-119">![Configured application](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")</span></span>  
  
6.  <span data-ttu-id="e1ab4-120">在**設定應用程式**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-120">In the **Configure Application** dialog box, click **OK**.</span></span>  
  
7.  <span data-ttu-id="e1ab4-121">在主控台樹狀目錄中，以滑鼠右鍵按一下**SampleApplication**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-121">In the console tree, right-click **SampleApplication**, and then click **Start**.</span></span>  
  
8.  <span data-ttu-id="e1ab4-122">在主控台樹狀目錄中，按一下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-122">In the console tree, click **Applications**.</span></span>  
  
9. <span data-ttu-id="e1ab4-123">在 [應用程式詳細資料] 窗格中，檢查**狀態**的**SampleApplication**是**已啟動**。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-123">In the Applications details pane, check that the **Status** of **SampleApplication** is **Started**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="e1ab4-124">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="e1ab4-124">What did I just do?</span></span>  
 <span data-ttu-id="e1ab4-125">您設定並啟動 SampleApplication 應用程式</span><span class="sxs-lookup"><span data-stu-id="e1ab4-125">You configured and started the SampleApplication application</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e1ab4-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e1ab4-126">Next Steps</span></span>  
 <span data-ttu-id="e1ab4-127">插入新的員工中測試應用程式**員工**資料表中所述[步驟 4： 測試應用程式](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e1ab4-127">You test the application by inserting new employees in the **Employee** table, as described in [Step 4: Test the Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ab4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1ab4-128">See Also</span></span>  
 <span data-ttu-id="e1ab4-129">[步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span><span class="sxs-lookup"><span data-stu-id="e1ab4-129">[Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span></span>  
 <span data-ttu-id="e1ab4-130">[步驟 4： 測試應用程式](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="e1ab4-130">[Step 4: Test the Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md) </span></span>  
 [<span data-ttu-id="e1ab4-131">第 5 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="e1ab4-131">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)