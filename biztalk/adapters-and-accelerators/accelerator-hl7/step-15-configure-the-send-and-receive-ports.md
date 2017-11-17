---
title: "步驟 15： 設定傳送埠和接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, ports
ms.assetid: d532b196-473e-4c8f-b4ed-acef674fc698
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 020d83db1db86f9ff9ce116578cf58f19ba08241
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-15-configure-the-send-and-receive-ports"></a><span data-ttu-id="a84c6-102">步驟 15： 設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="a84c6-102">Step 15: Configure the Send and Receive Ports</span></span>
<span data-ttu-id="a84c6-103">在上一個步驟中，您可以建立邏輯傳送和接收埠使用協調流程設計師並設定連接埠繫結到 「 稍後指定 」。</span><span class="sxs-lookup"><span data-stu-id="a84c6-103">In previous steps, you created a logical send and receive port using Orchestration Designer and set the port binding to "Specify Later".</span></span> <span data-ttu-id="a84c6-104">在此步驟中，您可以使用 BizTalk 總管 中定義實體的來源和目的地位置，並以您在協調流程中建立的邏輯連接埠繫結的實體連接埠完成連接埠設定。</span><span class="sxs-lookup"><span data-stu-id="a84c6-104">In this step, you use BizTalk Explorer to finalize the port configuration by defining the physical source and destination locations and binding the physical ports to the logical ports that you created in the orchestration.</span></span>  
  
## <a name="configure-the-send-and-receive-ports"></a><span data-ttu-id="a84c6-105">設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="a84c6-105">Configure the send and receive ports</span></span>  
  
1.  <span data-ttu-id="a84c6-106">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開  **BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
2.  <span data-ttu-id="a84c6-107">以滑鼠右鍵按一下**傳送埠**，指向 [新增]，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-107">Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="a84c6-108">在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MLLPSendPort**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-108">In the Send Port Properties dialog box, in the **Name** box, type **MLLPSendPort**.</span></span>  
  
4.  <span data-ttu-id="a84c6-109">如**類型**，選取**MLLP**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-109">For **Type**, select **MLLP**.</span></span>  
  
5.  <span data-ttu-id="a84c6-110">按一下**設定**按鈕右邊的**類型**欄位。</span><span class="sxs-lookup"><span data-stu-id="a84c6-110">Click the **Configure** button to the right of the **Type** field.</span></span>  
  
6.  <span data-ttu-id="a84c6-111">在 [MLLP 傳輸屬性] 對話方塊的**連接名稱**輸入**MLLPConnection**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-111">In the MLLP Transport Properties dialog box, for **Connection Name** enter **MLLPConnection**.</span></span> <span data-ttu-id="a84c6-112">如**主機**輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-112">For **Host** enter **localhost**.</span></span> <span data-ttu-id="a84c6-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-113">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a84c6-114">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-114">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="a84c6-115">在管理主控台中，以滑鼠右鍵按一下**MLLPSendPort**連接埠，，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-115">In the Administration Console, right-click **MLLPSendPort** port, and then click **Start**.</span></span>  
  
9. <span data-ttu-id="a84c6-116">展開**平台設定**，按一下 **主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-116">Expand **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**.</span></span> <span data-ttu-id="a84c6-117">如果主機已在執行中，按一下**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-117">If the host is already running, click **Restart**.</span></span>  
  
10. <span data-ttu-id="a84c6-118">按一下**協調流程**，以滑鼠右鍵按一下**BTAHL7_Project.Doorbell_Orchestration**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-118">Click **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="a84c6-119">在 [協調流程屬性] 對話方塊的主控台樹狀目錄中，按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-119">In the Orchestration Properties dialog box, in the console tree, click **Bindings**.</span></span>  
  
12. <span data-ttu-id="a84c6-120">在**繫結** 窗格中，針對**主機**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="a84c6-120">In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**.</span></span>  
  
13. <span data-ttu-id="a84c6-121">如**SOAPReceivePort**，選取**WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**中**接收埠**資料行。</span><span class="sxs-lookup"><span data-stu-id="a84c6-121">For **SOAPReceivePort**, select **WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** in the **Receive Ports** column.</span></span>  
  
14. <span data-ttu-id="a84c6-122">如**MLLPSendPort**，選取**MLLPSendPort**中**傳送埠/傳送埠群組**資料行。</span><span class="sxs-lookup"><span data-stu-id="a84c6-122">For **MLLPSendPort**, select **MLLPSendPort** in the **Send Ports/Send Port Groups** column.</span></span>  
  
15. <span data-ttu-id="a84c6-123">按一下**確定**儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="a84c6-123">Click **OK** to save the changes.</span></span>  
  
## <a name="msh-5-and-msh-6"></a><span data-ttu-id="a84c6-124">MSH 5 和 MSH 6</span><span class="sxs-lookup"><span data-stu-id="a84c6-124">MSH 5 and MSH 6</span></span>  
 <span data-ttu-id="a84c6-125">MSH 5 和 MSH 6 標頭欄位會分別包含的目的端應用程式和功能。</span><span class="sxs-lookup"><span data-stu-id="a84c6-125">The MSH 5 and MSH 6 header fields contain the destination application and facility, respectively.</span></span> <span data-ttu-id="a84c6-126">在組態總管 中，您可以 MSH 5 和 MSH 6 的情況下，當您想要變更訊息中的目的地資訊中的三個元件的每個指定的值。</span><span class="sxs-lookup"><span data-stu-id="a84c6-126">In Configuration Explorer, you can specify the values for each of the three components of MSH 5 and MSH 6, in cases when you want the destination information in the message to be changed.</span></span> <span data-ttu-id="a84c6-127">這是這種情況，當原始的訊息不包含合作對象特有的資訊。</span><span class="sxs-lookup"><span data-stu-id="a84c6-127">This is a likely scenario when the original message does not include party-specific information.</span></span> <span data-ttu-id="a84c6-128">這個步驟是適用於宣告式 （發行者/訂閱者） 模型。</span><span class="sxs-lookup"><span data-stu-id="a84c6-128">This step is applicable in the declarative (publisher/subscriber) model.</span></span> <span data-ttu-id="a84c6-129">如果適用的話，您的環境中，您可以執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="a84c6-129">You perform this step if it is applicable in your environment.</span></span> <span data-ttu-id="a84c6-130">如需有關如何設定這些值的詳細資訊，請參閱[合作對象-BTAHL7 Configuration 總管](parties-tab.md)。</span><span class="sxs-lookup"><span data-stu-id="a84c6-130">For more information about setting these values, see [Parties - BTAHL7 Configuration Explorer](parties-tab.md).</span></span>  
  
 <span data-ttu-id="a84c6-131">若要繼續[步驟 16： 啟動協調流程](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="a84c6-131">Proceed to [Step 16: Start the Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84c6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a84c6-132">See Also</span></span>  
 [<span data-ttu-id="a84c6-133">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="a84c6-133">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)