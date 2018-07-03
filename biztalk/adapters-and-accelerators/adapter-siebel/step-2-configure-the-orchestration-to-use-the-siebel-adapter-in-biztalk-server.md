---
title: 步驟 2： 使用 Siebel 配接器在 BizTalk Server 管理主控台設定協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41338723-055d-46b4-acee-6969ea79fac0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f779c9b347c43fb9bd2a6dcdbdb3c33ac8ad09c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009127"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-with-the-siebel-adapter"></a><span data-ttu-id="ade4f-102">步驟 2： 使用 Siebel 配接器在 BizTalk Server 管理主控台設定協調流程</span><span class="sxs-lookup"><span data-stu-id="ade4f-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console with the Siebel adapter</span></span>
<span data-ttu-id="ade4f-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="ade4f-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="ade4f-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="ade4f-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="ade4f-105">**目標：** 在此步驟中，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="ade4f-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
- <span data-ttu-id="ade4f-106">建立 WCF 自訂傳送-接收埠以傳送和接收來自 Siebel 系統使用的訊息[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ade4f-106">Create a WCF-Custom send-receive port to send and receive messages from the Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="ade4f-107">設定此連接埠使用您在上一個步驟中建立的對應。</span><span class="sxs-lookup"><span data-stu-id="ade4f-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
- <span data-ttu-id="ade4f-108">設定協調流程使用 WCF 自訂連接埠的最後一個步驟中部署。</span><span class="sxs-lookup"><span data-stu-id="ade4f-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="ade4f-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ade4f-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="ade4f-110">您必須部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-110">You must have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="ade4f-111">若要建立一個 WCF 自訂連接埠</span><span class="sxs-lookup"><span data-stu-id="ade4f-111">To create a WCF-Custom port</span></span>  
  
1. <span data-ttu-id="ade4f-112">當您作業產生結構描述上 Siebel 系統使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ade4f-112">When you generate schema for an operation on the Siebel system using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="ade4f-113">您可以將此繫結檔案匯入到您的 BizTalk 應用程式來建立 WCF 自訂傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="ade4f-114">如需匯入繫結檔案的指示，請參閱 <<c0> [ 匯入繫結](http://msdn.microsoft.com/library/908ab90c-2ba2-4c65-9f74-10579f06e372)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/908ab90c-2ba2-4c65-9f74-10579f06e372).</span></span>  
  
2. <span data-ttu-id="ade4f-115">匯入繫結檔案之後下, 建立傳送埠**傳送埠**在 BizTalk Server 管理主控台中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ade4f-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3. <span data-ttu-id="ade4f-116">以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="ade4f-117">從傳送埠的 屬性 對話方塊的左窗格中，按一下**一般** 索引標籤。從右窗格中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5. <span data-ttu-id="ade4f-118">在 [ **Wcf-custom 傳輸屬性**] 對話方塊中，按一下**認證**索引標籤，然後指定要連接至 Siebel 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="ade4f-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and specify the credentials to connect to a Siebel system.</span></span>  
  
6. <span data-ttu-id="ade4f-119">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="ade4f-119">Click **OK**.</span></span>  
  
7. <span data-ttu-id="ade4f-120">從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="ade4f-121">從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**ResponseMap**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-121">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
    <span data-ttu-id="ade4f-122">![設定輸入的對應](../../adapters-and-accelerators/adapter-siebel/media/e1ceee98-9f10-40f1-a611-88d3a2c102a9.gif "e1ceee98-9f10-40f1-a611-88d3a2c102a9")</span><span class="sxs-lookup"><span data-stu-id="ade4f-122">![Configure inbound map](../../adapters-and-accelerators/adapter-siebel/media/e1ceee98-9f10-40f1-a611-88d3a2c102a9.gif "e1ceee98-9f10-40f1-a611-88d3a2c102a9")</span></span>  
  
8. <span data-ttu-id="ade4f-123">從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-123">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="ade4f-124">從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**RequestMap**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-124">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
    <span data-ttu-id="ade4f-125">![設定輸出對應](../../adapters-and-accelerators/adapter-siebel/media/8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9.gif "8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9")</span><span class="sxs-lookup"><span data-stu-id="ade4f-125">![Configure outbound map](../../adapters-and-accelerators/adapter-siebel/media/8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9.gif "8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9")</span></span>  
  
9. <span data-ttu-id="ade4f-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="ade4f-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="ade4f-127">若要設定的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="ade4f-127">To configure the BizTalk application</span></span>  
  
1. <span data-ttu-id="ade4f-128">在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**、 展開協調流程的部署位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ade4f-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2. <span data-ttu-id="ade4f-129">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="ade4f-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3. <span data-ttu-id="ade4f-130">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="ade4f-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="ade4f-131">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ade4f-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4. <span data-ttu-id="ade4f-132">底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
   1. <span data-ttu-id="ade4f-133">選取您將會卸除要求訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="ade4f-134">BizTalk 協調流程將會取用的要求訊息，並將它傳送至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="ade4f-134">The BizTalk orchestration will consume the request message and send it to the Siebel system.</span></span>  
  
   2. <span data-ttu-id="ade4f-135">選取 BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the Siebel system.</span></span>  
  
   3. <span data-ttu-id="ade4f-136">選取您稍早在本主題中建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ade4f-136">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
   4. <span data-ttu-id="ade4f-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="ade4f-137">Click **OK**.</span></span>  
  
      <span data-ttu-id="ade4f-138">設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」，網址[ http://go.microsoft.com/fwlink/?LinkId=102360 ](http://go.microsoft.com/fwlink/?LinkId=102360)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ade4f-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ade4f-139">Next Steps</span></span>  
 <span data-ttu-id="ade4f-140">您現在已完成移轉至 BizTalk 專案，將訊息傳送至使用 WCF 型 Siebel 系統 vPrev BizTalk 專案的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ade4f-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the Siebel system using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="ade4f-141">您現在必須測試已移轉的 BizTalk 應用程式傳送到叫用的帳戶商務元件的 Insert 作業的要求訊息中所述[步驟 3： 測試移轉應用程式與 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-141">You must now test the migrated BizTalk application by sending a request message to invoke the Insert operation on the Account business component, as described in [Step 3: Test the Migrated Application with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade4f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade4f-142">See Also</span></span>  
 [<span data-ttu-id="ade4f-143">教學課程 2： 移轉 BizTalk 專案中 Siebel</span><span class="sxs-lookup"><span data-stu-id="ade4f-143">Tutorial 2: Migrating BizTalk Projects in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)