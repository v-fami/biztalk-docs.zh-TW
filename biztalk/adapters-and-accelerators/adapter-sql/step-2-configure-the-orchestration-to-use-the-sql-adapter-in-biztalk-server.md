---
title: 步驟 2： 設定協調流程中使用 SQL 配接器的 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6152560-5ff0-4bdc-818c-e906b9642f52
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6293758d9891d86e137d07e9735ce37162d6a96b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984023"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-using-the-sql-adapter"></a><span data-ttu-id="15616-102">步驟 2： 設定協調流程中使用 SQL 配接器的 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="15616-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console using the SQL adapter</span></span>
<span data-ttu-id="15616-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="15616-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="15616-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="15616-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="15616-105">**目標：** 在此步驟中，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="15616-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
- <span data-ttu-id="15616-106">建立 WCF 自訂傳送-接收埠以傳送和接收訊息，從 SQL Server 資料庫使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15616-106">Create a WCF-Custom send-receive port to send and receive messages from the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="15616-107">設定此連接埠使用您在上一個步驟中建立的對應。</span><span class="sxs-lookup"><span data-stu-id="15616-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
- <span data-ttu-id="15616-108">設定協調流程使用 WCF 自訂連接埠上一個步驟中部署。</span><span class="sxs-lookup"><span data-stu-id="15616-108">Configure the orchestration you deployed in the previous step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="15616-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="15616-109">Prerequisites</span></span>  
 <span data-ttu-id="15616-110">您應該已經部署新的 BizTalk 協調流程，您要設定 WCF 自訂連接埠，如中所述[步驟 1： 修改 vPrev BizTalk 專案使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="15616-110">You should have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port as described in [Step 1: Modify the vPrev BizTalk Project using the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md).</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="15616-111">若要建立一個 WCF 自訂連接埠</span><span class="sxs-lookup"><span data-stu-id="15616-111">To create a WCF-Custom port</span></span>  
  
1. <span data-ttu-id="15616-112">當您作業產生結構描述上的 SQL Server 資料庫使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="15616-112">When you generate schema for an operation on the SQL Server database using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="15616-113">您可以將此繫結檔案匯入到您的 BizTalk 應用程式來建立 WCF 自訂傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="15616-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="15616-114">如需匯入繫結檔案的指示，請參閱 <<c0> [ 匯入繫結](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53)。</span><span class="sxs-lookup"><span data-stu-id="15616-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53).</span></span>  
  
2. <span data-ttu-id="15616-115">匯入繫結檔案之後下, 建立傳送埠**傳送埠**資料夾中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="15616-115">After you import the binding file, a send port is created under the **Send Ports** folder in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
3. <span data-ttu-id="15616-116">以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="15616-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="15616-117">從傳送埠的 屬性 對話方塊的左窗格中，按一下**一般** 索引標籤。從右窗格中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="15616-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5. <span data-ttu-id="15616-118">在 [ **Wcf-custom 傳輸屬性**] 對話方塊中，按一下**認證**索引標籤上，指定的認證以連接到 SQL Server 資料庫，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15616-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, specify the credentials to connect to a SQL Server database, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="15616-119">從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="15616-119">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="15616-120">從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**ResponseMap**。</span><span class="sxs-lookup"><span data-stu-id="15616-120">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
    <span data-ttu-id="15616-121">![設定輸入的對應](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span><span class="sxs-lookup"><span data-stu-id="15616-121">![Configure inbound map](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span></span>  
  
7. <span data-ttu-id="15616-122">從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="15616-122">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="15616-123">從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**RequestMap**。</span><span class="sxs-lookup"><span data-stu-id="15616-123">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
    <span data-ttu-id="15616-124">![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span><span class="sxs-lookup"><span data-stu-id="15616-124">![Configure outbound map](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span></span>  
  
8. <span data-ttu-id="15616-125">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="15616-125">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="15616-126">若要設定的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="15616-126">To configure the BizTalk application</span></span>  
  
1. <span data-ttu-id="15616-127">在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**，然後展開 協調流程的部署位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="15616-127">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2. <span data-ttu-id="15616-128">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="15616-128">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3. <span data-ttu-id="15616-129">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="15616-129">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="15616-130">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="15616-130">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4. <span data-ttu-id="15616-131">底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至實體中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="15616-131">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
   1.  <span data-ttu-id="15616-132">選取您將會卸除要求訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="15616-132">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="15616-133">BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="15616-133">The BizTalk orchestration will consume the request message and send it to the SQL Server database.</span></span>  
  
   2.  <span data-ttu-id="15616-134">選取 BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="15616-134">Select the file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.</span></span>  
  
   3.  <span data-ttu-id="15616-135">選取您稍早在本主題中建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="15616-135">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
   4.  <span data-ttu-id="15616-136">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="15616-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="15616-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="15616-137">Next Steps</span></span>  
 <span data-ttu-id="15616-138">您現在已完成移轉至 BizTalk 專案，將訊息傳送到使用以 WCF 為基礎的 SQL Server 資料庫 vPrev BizTalk 專案的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15616-138">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SQL Server database using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="15616-139">您現在必須測試已移轉的 BizTalk 應用程式傳送要求訊息至執行 SQL Server 資料庫中，插入作業中所述[步驟 3： 測試移轉應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="15616-139">You must now test the migrated BizTalk application by sending a request message to perform an Insert operation on the SQL Server database, as described in [Step 3: Test the Migrated Application that uses the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15616-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15616-140">See Also</span></span>  
 [<span data-ttu-id="15616-141">教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="15616-141">Tutorial 1: Migrate BizTalk Projects to the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)