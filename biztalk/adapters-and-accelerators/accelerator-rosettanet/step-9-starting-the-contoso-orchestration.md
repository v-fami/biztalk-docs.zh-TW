---
title: "步驟 9： 啟動 Contoso 協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, starting orchestrations
ms.assetid: df3ff90b-5a9f-4ae7-819a-11cb36d64ccd
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d58d7f2f9d725fca94eb6cf3d2412b3c376fe015
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-starting-the-contoso-orchestration"></a><span data-ttu-id="a3947-102">步驟 9： 啟動 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="a3947-102">Step 9: Starting the Contoso Orchestration</span></span>
<span data-ttu-id="a3947-103">在此步驟中，您將定義實體來源和目的地位置，藉以完成連接埠設定程序。</span><span class="sxs-lookup"><span data-stu-id="a3947-103">In this step, you complete the port configuration process by defining the physical source and destination locations.</span></span> <span data-ttu-id="a3947-104">您將實體連接埠繫結至您在建立邏輯連接埠[步驟 7： 建立和設定的連接埠](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="a3947-104">You bind the physical ports to the logical ports you created in [Step 7: Creating and Configuring Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md).</span></span> <span data-ttu-id="a3947-105">然後，登錄服務，使您在協調流程與協調流程將執行中的實體環境中設計的商務程序。</span><span class="sxs-lookup"><span data-stu-id="a3947-105">You then enlist the service to associate the business process that you designed in the orchestration with the physical environment that the orchestration will run in.</span></span> <span data-ttu-id="a3947-106">最後，啟動協調流程，讓它可以參與商務交易與 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="a3947-106">Finally, you start the orchestration so that it can participate in business transactions with Fabrikam.</span></span>  
  
### <a name="to-bind-the-orchestration-ports"></a><span data-ttu-id="a3947-107">若要繫結協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="a3947-107">To bind the orchestration ports</span></span>  
  
1.  <span data-ttu-id="a3947-108">開啟**BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="a3947-108">Open **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="a3947-109">在 [BizTalk 總管] 中，展開**BizTalk 組態資料庫**，依序展開**協調流程**，以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**，然後按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="a3947-109">In BizTalk Explorer, expand **BizTalk Configuration Database**, expand **Orchestrations**, right-click **ContosoPriceAndAvailability.PrivateResponderProcess**, and then click **Bind**.</span></span>  
  
3.  <span data-ttu-id="a3947-110">在 [連接埠繫結屬性] 頁面上選取**LOB_To_PrivateResponder**中**FromLOB**屬性。</span><span class="sxs-lookup"><span data-stu-id="a3947-110">On the Port Bindings Properties page, select **LOB_To_PrivateResponder** in the **FromLOB** property.</span></span>  
  
4.  <span data-ttu-id="a3947-111">在**ContosoSQLReqResponsePort**方塊中，選取**3A2SQLReqResponseSendPort**。</span><span class="sxs-lookup"><span data-stu-id="a3947-111">In the **ContosoSQLReqResponsePort** box, select **3A2SQLReqResponseSendPort**.</span></span>  
  
5.  <span data-ttu-id="a3947-112">在**ToLOB**屬性中，展開 **傳送埠**選取**PrivateResponder_To_LOB**。</span><span class="sxs-lookup"><span data-stu-id="a3947-112">In the **ToLOB** property, expand **Send Ports** and select **PrivateResponder_To_LOB**.</span></span>  
  
6.  <span data-ttu-id="a3947-113">在 [設定] 視窗的左窗格中，選取**主機**。</span><span class="sxs-lookup"><span data-stu-id="a3947-113">In the Configuration window in the left pane, select **Host**.</span></span>  
  
7.  <span data-ttu-id="a3947-114">在**主機**屬性，請在**BizTalk 主控件**類別目錄中，選取**BizTalkServerApplication**從下拉式清單，然後按一下**確定**.</span><span class="sxs-lookup"><span data-stu-id="a3947-114">In the **Host** property, in the **BizTalk Host** category, select **BizTalkServerApplication** from the drop-down list, and then click **OK**.</span></span>  
  
### <a name="to-start-the-biztalk-runtime-process"></a><span data-ttu-id="a3947-115">啟動 BizTalk 執行階段程序</span><span class="sxs-lookup"><span data-stu-id="a3947-115">To start the BizTalk runtime process</span></span>  
  
1.  <span data-ttu-id="a3947-116">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] ，然後按一下 **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a3947-116">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a3947-117">在 BizTalk 管理主控台，在左窗格中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後按一下展開**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="a3947-117">In the BizTalk Administration Console, in the left pane, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="a3947-118">確認的狀態**BizTalkServerApplication**服務**執行**。</span><span class="sxs-lookup"><span data-stu-id="a3947-118">Verify that the status of the **BizTalkServerApplication** service is **Running**.</span></span>  
  
### <a name="to-enlist-and-start-the-orchestration"></a><span data-ttu-id="a3947-119">登錄並啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="a3947-119">To enlist and start the orchestration</span></span>  
  
1.  <span data-ttu-id="a3947-120">在 BizTalk 管理主控台的左窗格中，依序展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="a3947-120">In the left pane of the BizTalk Administration Console, expand **Applications**, expand **BizTalk Application 1**, and then click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="a3947-121">在右窗格中，以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**協調流程，然後再按一下**登錄**。</span><span class="sxs-lookup"><span data-stu-id="a3947-121">In the right pane, right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Enlist**.</span></span>  
  
3.  <span data-ttu-id="a3947-122">以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**協調流程，然後再按一下**啟動**啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="a3947-122">Right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Start** to start the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3947-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3947-123">See Also</span></span>  
 [<span data-ttu-id="a3947-124">建立 Fabrikam 解決方案</span><span class="sxs-lookup"><span data-stu-id="a3947-124">Creating the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)