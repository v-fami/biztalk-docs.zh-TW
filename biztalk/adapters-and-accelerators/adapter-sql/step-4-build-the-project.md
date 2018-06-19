---
title: 步驟 4： 建置專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d88b1407-ecdd-4dbf-90da-02dc4781568c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f1d6fa03b4a686537ef04f0121c1ae168e525ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225662"
---
# <a name="step-4-build-the-project"></a><span data-ttu-id="62623-102">步驟 4： 建置專案</span><span class="sxs-lookup"><span data-stu-id="62623-102">Step 4: Build the Project</span></span>
<span data-ttu-id="62623-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="62623-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="62623-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="62623-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="62623-105">**目標：** 在此步驟中，您編譯 BizTalk 協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="62623-105">**Objective:** In this step, you compile the BizTalk orchestration project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="62623-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="62623-106">Prerequisites</span></span>  
 <span data-ttu-id="62623-107">您必須先完成[步驟 3： 將要求訊息傳送至插入記錄，並接收回應](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)。</span><span class="sxs-lookup"><span data-stu-id="62623-107">You must have completed [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span></span>  
  
### <a name="to-build-the-biztalk-orchestration-project"></a><span data-ttu-id="62623-108">若要建置 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="62623-108">To build the BizTalk orchestration project</span></span>  
  
1.  <span data-ttu-id="62623-109">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="62623-109">In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="62623-110">在 [屬性頁] 對話方塊中，在樹狀目錄窗格中，展開**通用屬性**，按一下 **組件**，然後在 [屬性] 清單中，按一下 **組件金鑰檔案**省略符號 **[…]**.</span><span class="sxs-lookup"><span data-stu-id="62623-110">In the property pages dialog box, in the tree pane, expand **Common Properties**, click **Assembly**, and then in the properties list, click the **Assembly Key File** ellipsis **[…]**.</span></span>  
  
3.  <span data-ttu-id="62623-111">指定的路徑中所述，您建立的組件金鑰檔案[來建立使用 SQL 配接器的 SQL 應用程式的必要條件](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md)，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="62623-111">Specify a path to the assembly key file you created as described in [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md), and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="62623-112">在 屬性頁 對話方塊中，在樹狀目錄窗格中，展開**組態屬性**，按一下 **部署**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="62623-112">In the property pages dialog box, in the tree pane, expand **Configuration Properties**, click **Deployment**, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="62623-113">如**應用程式名稱**屬性中，輸入`SampleApplication`。</span><span class="sxs-lookup"><span data-stu-id="62623-113">For the **Application Name** property, type `SampleApplication`.</span></span>  
  
    2.  <span data-ttu-id="62623-114">如**重新部署**屬性選取**True**。</span><span class="sxs-lookup"><span data-stu-id="62623-114">For the **Redeploy** property, select **True**.</span></span>  
  
     <span data-ttu-id="62623-115">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="62623-115">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="62623-116">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="62623-116">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="62623-117">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="62623-117">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
     <span data-ttu-id="62623-118">應該會在畫面底部的 [輸出] 窗格：**建置： 3 的成功或最新狀態、 0 失敗、 0 略過。**</span><span class="sxs-lookup"><span data-stu-id="62623-118">The Output pane at the bottom of the screen should read: **Build: 3 succeeded or up-to-date, 0 failed, 0 skipped.**</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="62623-119">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="62623-119">What did I just do?</span></span>  
 <span data-ttu-id="62623-120">在此步驟中，您可以編譯包含 BizTalk 專案和兩個類別庫專案的方案。</span><span class="sxs-lookup"><span data-stu-id="62623-120">In this step, you compiled the solution containing the BizTalk project and two class library projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="62623-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="62623-121">Next Steps</span></span>  
 <span data-ttu-id="62623-122">中所述，部署方案時，[第 5 課： 部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="62623-122">You deploy the solution, as described in [Lesson 5: Deploy the Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62623-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62623-123">See Also</span></span>  
 <span data-ttu-id="62623-124">[步驟 3： 傳送要插入的記錄，並接收回應的要求訊息](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md) </span><span class="sxs-lookup"><span data-stu-id="62623-124">[Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md) </span></span>  
 [<span data-ttu-id="62623-125">第 4 課： 執行插入作業的採購訂單資料表</span><span class="sxs-lookup"><span data-stu-id="62623-125">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)