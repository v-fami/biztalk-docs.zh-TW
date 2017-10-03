---
title: "訂單處理階段中的處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 698005da-1ba8-4972-83db-f5ae45fd6a83
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a8eae6b814af36d0ea07065726ca66518984703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-order-processing-stages"></a><span data-ttu-id="5503d-102">訂單處理階段中的處理</span><span class="sxs-lookup"><span data-stu-id="5503d-102">Processing in the Order Processing Stages</span></span>
<span data-ttu-id="5503d-103">商務程序管理解決方案包含兩個階段， **CableOrder1**和**CableOrder2**協調流程會執行訂單處理動作。</span><span class="sxs-lookup"><span data-stu-id="5503d-103">The Business Process Management solution includes two stages, the **CableOrder1** and **CableOrder2** orchestrations, that perform the order processing actions.</span></span> <span data-ttu-id="5503d-104">如需如何訂單程序分成兩階段的詳細資訊，請參閱[的處理階段的數目](../core/number-of-processing-stages.md)。</span><span class="sxs-lookup"><span data-stu-id="5503d-104">For more information about how the order process was divided into stages, see [Number of Processing Stages](../core/number-of-processing-stages.md).</span></span>  
  
 <span data-ttu-id="5503d-105">兩個處理階段開始時收到訂單訊息，並同時回覆狀態訊息，以**OrderManager**在開始之後的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5503d-105">Both processing stages begin when they receive an order message and both reply with a status message to the **OrderManager** orchestration once they have started.</span></span> <span data-ttu-id="5503d-106">同樣地，這兩個將訊息傳回**OrderManager**指出階段是否已完成或終止並產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5503d-106">Similarly, both send a message back to the **OrderManager** to indicate whether the stage completed or terminated with an error.</span></span> <span data-ttu-id="5503d-107">如需詳細資訊之間的連線**OrderManager**協調流程和處理階段，請參閱[反向直接夥伴繫結](../core/inverse-direct-partner-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="5503d-107">For details about the connection between the **OrderManager** orchestration and the processing stages, see [Inverse Direct Partner Binding](../core/inverse-direct-partner-binding.md).</span></span>  
  
 <span data-ttu-id="5503d-108">這兩種處理階段使用自我相互關聯，動態連接埠，以將資訊傳送回**OrderManger**。</span><span class="sxs-lookup"><span data-stu-id="5503d-108">Both processing stages use self-correlating, dynamic ports to send information back to the **OrderManger**.</span></span> <span data-ttu-id="5503d-109">配合動態連接埠時，協調流程會將連接埠位址從訊息複製到傳送埠。</span><span class="sxs-lookup"><span data-stu-id="5503d-109">With dynamic ports, the orchestrations copy the port address from the message to send port.</span></span>  
  
 <span data-ttu-id="5503d-110">所有的處理階段所接收的訂單訊息都是正規化及標準訂單訊息中建立**OrderBroker**。</span><span class="sxs-lookup"><span data-stu-id="5503d-110">All of the order messages the processing stages receive are the normalized, canonical order messages created in the **OrderBroker**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5503d-111">因為**CableOrder1**和**CableOrder2**協調流程，您可以閱讀此節與 Microsoft Visual Studio 中開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="5503d-111">Because of the length of the **CableOrder1** and **CableOrder2** orchestrations, you may want to read this section with the orchestrations open in Microsoft Visual Studio.</span></span>  
  
## <a name="the-cableorder1-orchestration"></a><span data-ttu-id="5503d-112">CableOrder1 協調流程</span><span class="sxs-lookup"><span data-stu-id="5503d-112">The CableOrder1 Orchestration</span></span>  
 <span data-ttu-id="5503d-113">**CableOrder1**收到訂單訊息時，會啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="5503d-113">The **CableOrder1** orchestration starts when it receives an order message.</span></span> <span data-ttu-id="5503d-114">接著，它會將回覆位址從訊息複製到階段完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5503d-114">It then copies the reply address from the message to the stage completion port.</span></span> <span data-ttu-id="5503d-115">接下來，以建構應答訊息，然後將它做為回應傳送**BeginStagePort**連接埠，，然後將路由資訊儲存在區域變數中。</span><span class="sxs-lookup"><span data-stu-id="5503d-115">Next, it constructs an acknowledgement message and sends it as a response to the **BeginStagePort** port, and then saves the routing information in a local variable.</span></span>  
  
 <span data-ttu-id="5503d-116">這樣，此協調流程就會自 SSO 取得組態資訊。</span><span class="sxs-lookup"><span data-stu-id="5503d-116">The orchestration next gets the configuration information from SSO.</span></span> <span data-ttu-id="5503d-117">如需解決方案如何使用 SSO 的詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="5503d-117">For more information about how the solution uses SSO, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="5503d-118">協調流程接著會建立執行個體**OrderHandler**物件來與後端處理序通訊，會檢查訊息的有效性，分析訊息，判斷服務類型，並採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5503d-118">The orchestration then creates an instance of the **OrderHandler** object to communicate with the backend processes, checks the validity of the message, analyzes the message, determines the service type, and which action to take.</span></span> <span data-ttu-id="5503d-119">根據要採取的動作，它會呼叫其中一個訂單動作協調流程**Activate**，**變更**，或**取消**並傳遞**OrderHandler**協調流程的物件。</span><span class="sxs-lookup"><span data-stu-id="5503d-119">Depending on the action to take, it calls one of the order action orchestrations **Activate**, **Change**, or **Cancel** and passes the **OrderHandler** object to the orchestration.</span></span>  
  
 <span data-ttu-id="5503d-120">**CableOrder1**協調流程會接著檢查中斷，訊息聆聽設備群組並等待傳送回。</span><span class="sxs-lookup"><span data-stu-id="5503d-120">The **CableOrder1** orchestration then checks for an interrupt, sends a message to the facilities group and waits to hear back.</span></span> <span data-ttu-id="5503d-121">如果協調流程收到來自設備群組的回應訊息，它就會繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5503d-121">If the orchestration gets a message back from the facilities group, it continues processing.</span></span> <span data-ttu-id="5503d-122">否則，若有發生中斷，協調流程就會擲出中斷例外錯誤。</span><span class="sxs-lookup"><span data-stu-id="5503d-122">Otherwise, if there is an interrupt, the orchestration throws an interrupt exception.</span></span>  
  
 <span data-ttu-id="5503d-123">透過建構完成訊息，並將它透過傳送完成的協調流程**StageCompletion**連接埠。</span><span class="sxs-lookup"><span data-stu-id="5503d-123">The orchestration finishes by constructing a completion message and sending it through the **StageCompletion** port.</span></span>  
  
## <a name="the-cableorder2-orchestration"></a><span data-ttu-id="5503d-124">CableOrder2 協調流程</span><span class="sxs-lookup"><span data-stu-id="5503d-124">The CableOrder2 Orchestration</span></span>  
 <span data-ttu-id="5503d-125">CableOrder2 協調流程會執行相同步驟開始與 CableOrder1 協調流程來路由資訊 SSO 組態資訊，以及建立的執行個體**OrderHandler**物件。</span><span class="sxs-lookup"><span data-stu-id="5503d-125">The CableOrder2 orchestration performs the same starting steps as the CableOrder1 orchestration for the routing information, SSO configuration information, and creating an instance of the **OrderHandler** object.</span></span>  
  
 <span data-ttu-id="5503d-126">協調流程會接著檢查中斷，並傳遞**OrderHandler**物件的呼叫中**完成**協調流程。</span><span class="sxs-lookup"><span data-stu-id="5503d-126">The orchestration then checks for an interrupt and passes the **OrderHandler** object in a call to the **Complete** orchestration.</span></span> <span data-ttu-id="5503d-127">協調流程接下來，建立訂單狀態訊息、 更新訂單歷程記錄，以及傳送完成訊息透過**StageCompletion**連接埠。</span><span class="sxs-lookup"><span data-stu-id="5503d-127">Next, the orchestration creates an order status message, updates the order history, and sends a completion message through the **StageCompletion** port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5503d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5503d-128">See Also</span></span>  
 <span data-ttu-id="5503d-129">[版本控制商務程序管理解決方案](../core/versioning-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="5503d-129">[Versioning the Business Process Management Solution](../core/versioning-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="5503d-130">商務程序管理解決方案中的處理</span><span class="sxs-lookup"><span data-stu-id="5503d-130">Processing in the Business Process Management Solution</span></span>](../core/processing-in-the-business-process-management-solution.md)