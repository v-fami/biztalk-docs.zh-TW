---
title: "步驟 1： 部署的協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8988fced-b2d5-4ee7-a851-20fc7c3dd087
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47565daf53f66fc5fc898e7c023ca09a34c78113
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-orchestration"></a><span data-ttu-id="1211b-102">步驟 1： 部署的協調流程</span><span class="sxs-lookup"><span data-stu-id="1211b-102">Step 1: Deploy the Orchestration</span></span>
<span data-ttu-id="1211b-103">![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="1211b-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="1211b-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="1211b-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="1211b-105">**目標：**此步驟中，在部署協調流程方案。</span><span class="sxs-lookup"><span data-stu-id="1211b-105">**Objective:** In this step, deploy the orchestration solution.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1211b-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="1211b-106">Prerequisites</span></span>  
 <span data-ttu-id="1211b-107">您必須先完成中的步驟[第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)。</span><span class="sxs-lookup"><span data-stu-id="1211b-107">You must have completed the steps in [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span></span>  
  
### <a name="to-deploy-the-solution"></a><span data-ttu-id="1211b-108">若要部署解決方案</span><span class="sxs-lookup"><span data-stu-id="1211b-108">To deploy the solution</span></span>  
  
1.  <span data-ttu-id="1211b-109">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1211b-109">In Solution Explorer, right-click the solution name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1211b-110">在 [屬性頁] 對話方塊中，在樹狀結構控制項中，展開**組態屬性**，然後按一下 [**組態**。</span><span class="sxs-lookup"><span data-stu-id="1211b-110">In the properties pages dialog box, in the tree control, expand **Configuration Properties**, and then click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="1211b-111">在**組態**頁面上，於**部署**資料行中，選取 BizTalk 專案中，針對核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1211b-111">On the **Configuration** page, in the **Deploy** column, select the check box against the BizTalk project, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="1211b-112">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="1211b-112">In Solution Explorer, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
     <span data-ttu-id="1211b-113">應該會在畫面底部的 [輸出] 窗格：**部署： 1 成功、 0 失敗、 0 略過**。</span><span class="sxs-lookup"><span data-stu-id="1211b-113">The Output pane at the bottom of the screen should read: **Deploy: 1 succeeded, 0 failed, 0 skipped**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="1211b-114">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="1211b-114">What did I just do?</span></span>  
 <span data-ttu-id="1211b-115">在此步驟中，您部署到 BizTalk 協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1211b-115">In this step, you deployed the BizTalk orchestration to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1211b-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1211b-116">Next Steps</span></span>  
 <span data-ttu-id="1211b-117">您建立的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述[步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="1211b-117">You create the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, as described in [Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1211b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1211b-118">See Also</span></span>  
 <span data-ttu-id="1211b-119">[步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span><span class="sxs-lookup"><span data-stu-id="1211b-119">[Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span></span>  
 [<span data-ttu-id="1211b-120">第 5 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="1211b-120">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)