---
title: 步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程 |Microsoft 文件
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
ms.openlocfilehash: 9b090ae83f0ca36bb4ae95795480d5f0d1661f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223790"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-using-the-sql-adapter"></a><span data-ttu-id="f46c3-102">步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程</span><span class="sxs-lookup"><span data-stu-id="f46c3-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console using the SQL adapter</span></span>
<span data-ttu-id="f46c3-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="f46c3-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="f46c3-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="f46c3-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="f46c3-105">**目標：** 在此步驟中，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f46c3-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f46c3-106">建立 WCF 自訂傳送-接收埠以傳送和接收訊息，從 SQL Server 資料庫使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f46c3-106">Create a WCF-Custom send-receive port to send and receive messages from the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="f46c3-107">設定此連接埠使用您在上一個步驟中建立的對應。</span><span class="sxs-lookup"><span data-stu-id="f46c3-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
-   <span data-ttu-id="f46c3-108">設定協調流程使用 WCF 自訂連接埠上一個步驟中部署。</span><span class="sxs-lookup"><span data-stu-id="f46c3-108">Configure the orchestration you deployed in the previous step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f46c3-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="f46c3-109">Prerequisites</span></span>  
 <span data-ttu-id="f46c3-110">您應該部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠中所述[步驟 1： 修改 vPrev 使用 SQL 配接器的 BizTalk 專案](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f46c3-110">You should have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port as described in [Step 1: Modify the vPrev BizTalk Project using the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md).</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="f46c3-111">若要建立一個 WCF 自訂連接埠</span><span class="sxs-lookup"><span data-stu-id="f46c3-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="f46c3-112">當您產生結構描述作業的 SQL Server 資料庫使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f46c3-112">When you generate schema for an operation on the SQL Server database using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="f46c3-113">您可以將此繫結檔案匯入到您的 BizTalk 應用程式建立 Wcf-custom 傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="f46c3-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="f46c3-114">如需匯入繫結檔案的指示，請參閱[匯入繫結](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53)。</span><span class="sxs-lookup"><span data-stu-id="f46c3-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53).</span></span>  
  
2.  <span data-ttu-id="f46c3-115">在您匯入繫結檔案之後，會建立傳送埠**傳送埠**資料夾中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f46c3-115">After you import the binding file, a send port is created under the **Send Ports** folder in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
3.  <span data-ttu-id="f46c3-116">以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f46c3-117">從傳送埠屬性 對話方塊的左窗格中，按一下 **一般** 索引標籤。從右窗格中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f46c3-118">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤上，指定的認證來連接到 SQL Server 資料庫，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, specify the credentials to connect to a SQL Server database, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="f46c3-119">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-119">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="f46c3-120">從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**ResponseMap**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-120">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="f46c3-121">![設定輸入的對應](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span><span class="sxs-lookup"><span data-stu-id="f46c3-121">![Configure inbound map](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span></span>  
  
7.  <span data-ttu-id="f46c3-122">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-122">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="f46c3-123">從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**RequestMap**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-123">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
     <span data-ttu-id="f46c3-124">![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span><span class="sxs-lookup"><span data-stu-id="f46c3-124">![Configure outbound map](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span></span>  
  
8.  <span data-ttu-id="f46c3-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-125">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="f46c3-126">若要設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="f46c3-126">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="f46c3-127">在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開 協調流程部署所在的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f46c3-127">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="f46c3-128">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-128">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="f46c3-129">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="f46c3-129">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="f46c3-130">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="f46c3-130">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="f46c3-131">在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到實體連接埠中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f46c3-131">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    1.  <span data-ttu-id="f46c3-132">選取您將在此置放要求訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="f46c3-132">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="f46c3-133">BizTalk 協調流程會使用要求訊息，並將它傳送給 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f46c3-133">The BizTalk orchestration will consume the request message and send it to the SQL Server database.</span></span>  
  
    2.  <span data-ttu-id="f46c3-134">選取 BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="f46c3-134">Select the file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.</span></span>  
  
    3.  <span data-ttu-id="f46c3-135">選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="f46c3-135">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="f46c3-136">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f46c3-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f46c3-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f46c3-137">Next Steps</span></span>  
 <span data-ttu-id="f46c3-138">您現在已完成的 vPrev BizTalk 專案，以將訊息傳送至使用 WCF 為基礎的 SQL Server 資料庫的 BizTalk 專案移轉[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f46c3-138">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SQL Server database using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="f46c3-139">您現在必須測試已移轉的 BizTalk 應用程式傳送至執行 SQL Server 資料庫中，插入作業的要求訊息中所述[步驟 3： 測試移轉應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f46c3-139">You must now test the migrated BizTalk application by sending a request message to perform an Insert operation on the SQL Server database, as described in [Step 3: Test the Migrated Application that uses the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46c3-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f46c3-140">See Also</span></span>  
 [<span data-ttu-id="f46c3-141">教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="f46c3-141">Tutorial 1: Migrate BizTalk Projects to the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)