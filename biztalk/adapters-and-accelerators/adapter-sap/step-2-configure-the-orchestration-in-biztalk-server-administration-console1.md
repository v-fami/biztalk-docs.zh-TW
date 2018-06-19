---
title: 步驟 2： 設定協調流程中 BizTalk Server 管理 Console1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration, configruing in BizTalk Server Administration console
- WCF-Custom port, creating
- migration
ms.assetid: fb057bce-5702-4ea0-8ed5-e299d3a78a11
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1783e56891ffd6d5d27058eab1df8a60663f481b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217710"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console"></a><span data-ttu-id="e206a-102">步驟 2： 在 BizTalk Server 管理主控台中設定協調流程</span><span class="sxs-lookup"><span data-stu-id="e206a-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console</span></span>
<span data-ttu-id="e206a-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="e206a-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="e206a-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="e206a-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="e206a-105">**目標：** 在此步驟中，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="e206a-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e206a-106">建立 WCF 自訂傳送-接收埠以傳送和接收訊息從 SAP 系統使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e206a-106">Create a WCF-Custom send-receive port to send and receive messages from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e206a-107">設定此連接埠使用您在上一個步驟中建立的對應。</span><span class="sxs-lookup"><span data-stu-id="e206a-107">Configure this port to use the maps that you created in the previous step.</span></span>  
  
-   <span data-ttu-id="e206a-108">設定協調流程使用 WCF 自訂連接埠的最後一個步驟中部署。</span><span class="sxs-lookup"><span data-stu-id="e206a-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="e206a-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="e206a-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="e206a-110">部署您要設定 WCF 自訂連接埠的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="e206a-110">Deploy the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="e206a-111">若要建立一個 WCF 自訂連接埠</span><span class="sxs-lookup"><span data-stu-id="e206a-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="e206a-112">當您產生結構描述使用 RFC [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e206a-112">When you generate schema for an RFC using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="e206a-113">您可以將此繫結檔案匯入到您的 BizTalk 應用程式建立 Wcf-custom 傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="e206a-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="e206a-114">如需匯入繫結檔案的指示，請參閱[匯入繫結](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf)。</span><span class="sxs-lookup"><span data-stu-id="e206a-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf).</span></span>  
  
2.  <span data-ttu-id="e206a-115">在您匯入繫結檔案之後，會建立傳送埠**傳送埠**BizTalk Server 管理主控台中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e206a-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3.  <span data-ttu-id="e206a-116">以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e206a-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e206a-117">從傳送埠屬性 對話方塊的左窗格中，按一下 **一般** 索引標籤。從右窗格中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e206a-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="e206a-118">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，並指定要連接到 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="e206a-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and specify the credentials to connect to an SAP system.</span></span>  
  
6.  <span data-ttu-id="e206a-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e206a-119">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="e206a-120">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="e206a-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="e206a-121">從右窗格中，按一下 下的欄位**對應**資料行，然後從下拉式清單中，選取**ResponseMap**。</span><span class="sxs-lookup"><span data-stu-id="e206a-121">From the right pane, click the field under the **Map** column, and from the drop-down, select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="e206a-122">![在 WCF 自訂連接埠上設定輸入的對應](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")</span><span class="sxs-lookup"><span data-stu-id="e206a-122">![Configure the inbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")</span></span>  
  
8.  <span data-ttu-id="e206a-123">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸出對應。**</span><span class="sxs-lookup"><span data-stu-id="e206a-123">From the left pane of the send port properties dialog box, click **Outbound Maps.**</span></span> <span data-ttu-id="e206a-124">從右窗格中，按一下 下的欄位**對應**資料行，然後從下拉式清單中，選取**RequestMap**。</span><span class="sxs-lookup"><span data-stu-id="e206a-124">From the right pane, click the field under the **Map** column, and from the drop-down, select **RequestMap**.</span></span>  
  
     <span data-ttu-id="e206a-125">![在 WCF 自訂連接埠上設定輸出對應](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")</span><span class="sxs-lookup"><span data-stu-id="e206a-125">![Configure the outbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")</span></span>  
  
9. <span data-ttu-id="e206a-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e206a-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="e206a-127">若要設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e206a-127">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="e206a-128">在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開 協調流程部署所在的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e206a-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="e206a-129">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="e206a-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="e206a-130">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="e206a-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="e206a-131">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e206a-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="e206a-132">在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到 BizTalk Server 管理主控台中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="e206a-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="e206a-133">選取您將在此置放要求訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="e206a-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="e206a-134">BizTalk 協調流程會使用要求訊息，並將它傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="e206a-134">The BizTalk orchestration will consume the request message and send it to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="e206a-135">選取 BizTalk 協調流程將會卸除包含 SAP 系統從回應的回應訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="e206a-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the SAP system.</span></span>  
  
    3.  <span data-ttu-id="e206a-136">選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="e206a-136">Select the WCF-custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="e206a-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e206a-137">Click **OK**.</span></span>  
  
     <span data-ttu-id="e206a-138">如需有關如何設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」 在[http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360)。</span><span class="sxs-lookup"><span data-stu-id="e206a-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e206a-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e206a-139">Next Steps</span></span>  
 <span data-ttu-id="e206a-140">您現在已完成的 vPrev BizTalk 專案，以將訊息傳送至使用 WCF 為基礎之 SAP 系統的 BizTalk 專案移轉[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e206a-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e206a-141">您現在必須測試已移轉的 BizTalk 應用程式中所述，傳送要求訊息，以叫用 SD_RFC_CUSTOMER_GET RFC，[步驟 3： 測試移轉應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md)。</span><span class="sxs-lookup"><span data-stu-id="e206a-141">You must now test the migrated BizTalk application by sending a request message to invoke the SD_RFC_CUSTOMER_GET RFC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e206a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e206a-142">See Also</span></span>  
 [<span data-ttu-id="e206a-143">教學課程 2： 移轉 SAP RFC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="e206a-143">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)