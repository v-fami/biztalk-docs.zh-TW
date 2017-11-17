---
title: "步驟 3B: FileAct 存放與轉寄 （提取） 案例的動態傳送埠與協調流程繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb973066-8797-4f51-a89e-3845f2811605
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10111de1080aacd532be96f501be1d20acda1dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-bind-the-orchestration-with-dynamic-send-port-for-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="05723-102">步驟 3B: FileAct 存放與轉寄 （提取） 案例的動態傳送埠與協調流程繫結</span><span class="sxs-lookup"><span data-stu-id="05723-102">Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="05723-103">在開始此步驟之前，必須先完成[步驟 3A： 建立 FileAct 存放與轉寄 （提取） 案例的動態傳送埠的協調流程](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)。</span><span class="sxs-lookup"><span data-stu-id="05723-103">Before you begin this step, you must complete [Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="05723-104">若要新增 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="05723-104">To add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="05723-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="05723-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="05723-106">在 BizTalk Server 管理主控台的左窗格中，展開 BizTalk Server 管理 中，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **主控件執行個體**.</span><span class="sxs-lookup"><span data-stu-id="05723-106">In the BizTalk Server Administration Console, in the left pane, expand BizTalk Server Administration, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="05723-107">確認的狀態**BizTalkServerApplication**裝載執行個體和 FileActhost 是**執行**。</span><span class="sxs-lookup"><span data-stu-id="05723-107">Verify that the status for the **BizTalkServerApplication** host instance and FileActhost instance is **running**.</span></span> <span data-ttu-id="05723-108">如果沒有，請以滑鼠右鍵按一下主控件執行個體，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="05723-108">If not, right-click the host instances, and click **Start**.</span></span>  
  
3.  <span data-ttu-id="05723-109">在左窗格中，展開 應用程式，然後再展開 BizTalk Application 1。</span><span class="sxs-lookup"><span data-stu-id="05723-109">In the left pane, expand Applications, and then expand BizTalk Application 1.</span></span> <span data-ttu-id="05723-110">按一下 協調流程。</span><span class="sxs-lookup"><span data-stu-id="05723-110">Click Orchestrations.</span></span>  
  
4.  <span data-ttu-id="05723-111">以滑鼠右鍵按一下**DynamicSendOrchestration**按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="05723-111">Right-click **DynamicSendOrchestration** and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="05723-112">在**協調流程屬性**] 對話方塊的左窗格中，按一下 [**繫結**並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="05723-112">In the **Orchestration Properties** dialog box, in the left pane, click **Bindings** and do the following:</span></span>  
  
    |<span data-ttu-id="05723-113">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="05723-113">**Use this**</span></span>|<span data-ttu-id="05723-114">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="05723-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="05723-115">**Host**</span><span class="sxs-lookup"><span data-stu-id="05723-115">**Host**</span></span>|<span data-ttu-id="05723-116">從下拉式清單選取**BizTalkServer 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="05723-116">From the drop-down list, select **BizTalkServer Application**.</span></span>|  
    |<span data-ttu-id="05723-117">**動態提取**</span><span class="sxs-lookup"><span data-stu-id="05723-117">**Dynamic Pull**</span></span>|<span data-ttu-id="05723-118">從下拉式清單選取**Tutorial_FA_DynamicSendPort**。</span><span class="sxs-lookup"><span data-stu-id="05723-118">From the drop-down list, select **Tutorial_FA_DynamicSendPort**.</span></span>|  
    |<span data-ttu-id="05723-119">**SendPullResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="05723-119">**SendPullResponseToSender**</span></span>|<span data-ttu-id="05723-120">從下拉式清單選取**Tutorial_FA_SendPullResponsetoReceiver**。</span><span class="sxs-lookup"><span data-stu-id="05723-120">From the drop-down list, select **Tutorial_FA_SendPullResponsetoReceiver**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05723-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05723-121">See Also</span></span>  
 [<span data-ttu-id="05723-122">步驟 3A： 建立 FileAct 存放與轉寄 （提取） 案例的動態傳送埠的協調流程</span><span class="sxs-lookup"><span data-stu-id="05723-122">Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)