---
title: 步驟 2： 使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台中設定協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 598b4ab0-ff22-4dfa-aa9c-774c60c90227
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b348a21a54ece0e5db736e18f60c9bed2b8d047d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215550"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-to-use-the-oracle-database-adapter"></a><span data-ttu-id="68e44-102">步驟 2： 使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台中設定協調流程</span><span class="sxs-lookup"><span data-stu-id="68e44-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console to use the Oracle Database adapter</span></span>
<span data-ttu-id="68e44-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="68e44-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="68e44-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="68e44-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="68e44-105">**目標：** 在此步驟中，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="68e44-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="68e44-106">建立 WCF 自訂傳送-接收埠以傳送和接收訊息，從 Oracle 資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="68e44-106">Create a WCF-Custom send-receive port to send and receive messages from the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="68e44-107">設定此連接埠使用您在上一個步驟中建立的對應。</span><span class="sxs-lookup"><span data-stu-id="68e44-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
-   <span data-ttu-id="68e44-108">設定協調流程使用 WCF 自訂連接埠的最後一個步驟中部署。</span><span class="sxs-lookup"><span data-stu-id="68e44-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="68e44-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="68e44-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="68e44-110">您必須部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-110">You must have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="68e44-111">若要建立一個 WCF 自訂連接埠</span><span class="sxs-lookup"><span data-stu-id="68e44-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="68e44-112">當您產生結構描述作業的 Oracle 資料庫使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="68e44-112">When you generate schema for an operation on the Oracle database using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="68e44-113">您可以將此繫結檔案匯入到您的 BizTalk 應用程式建立 Wcf-custom 傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="68e44-114">如需匯入繫結檔案的指示，請參閱[匯入繫結](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f)。</span><span class="sxs-lookup"><span data-stu-id="68e44-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f).</span></span>  
  
2.  <span data-ttu-id="68e44-115">在您匯入繫結檔案之後，會建立傳送埠**傳送埠**BizTalk Server 管理主控台中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="68e44-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3.  <span data-ttu-id="68e44-116">以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="68e44-116">Right-click the WCF-Custom port and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="68e44-117">從傳送埠屬性 對話方塊的左窗格中，按一下 **一般** 索引標籤。從右窗格中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="68e44-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="68e44-118">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，並指定要連接到 Oracle 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="68e44-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and specify the credentials to connect to an Oracle database.</span></span>  
  
6.  <span data-ttu-id="68e44-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68e44-119">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="68e44-120">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="68e44-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="68e44-121">從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**ResponseMap**。</span><span class="sxs-lookup"><span data-stu-id="68e44-121">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="68e44-122">![設定輸入的對應](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")</span><span class="sxs-lookup"><span data-stu-id="68e44-122">![Configure inbound map](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")</span></span>  
  
8.  <span data-ttu-id="68e44-123">從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="68e44-123">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="68e44-124">從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**RequestMap**。</span><span class="sxs-lookup"><span data-stu-id="68e44-124">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
     <span data-ttu-id="68e44-125">![設定輸出對應](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")</span><span class="sxs-lookup"><span data-stu-id="68e44-125">![Configure outbound map](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")</span></span>  
  
9. <span data-ttu-id="68e44-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68e44-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="68e44-127">若要設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="68e44-127">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="68e44-128">在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**、 展開協調流程部署所在的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="68e44-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="68e44-129">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="68e44-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="68e44-130">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="68e44-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="68e44-131">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="68e44-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="68e44-132">在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到 BizTalk Server 管理主控台中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="68e44-133">選取您將在此置放要求訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="68e44-134">BizTalk 協調流程會使用要求訊息，並將它傳送到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="68e44-134">The BizTalk orchestration will consume the request message and send it to the Oracle database.</span></span>  
  
    2.  <span data-ttu-id="68e44-135">選取 BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the Oracle database.</span></span>  
  
    3.  <span data-ttu-id="68e44-136">選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="68e44-136">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="68e44-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68e44-137">Click **OK**.</span></span>  
  
     <span data-ttu-id="68e44-138">如需有關如何設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」 在[http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961)。</span><span class="sxs-lookup"><span data-stu-id="68e44-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="68e44-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="68e44-139">Next Steps</span></span>  
 <span data-ttu-id="68e44-140">您現在已完成的 vPrev BizTalk 專案，以將訊息傳送至使用 WCF 型 Oracle 資料庫的 BizTalk 專案移轉[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="68e44-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="68e44-141">您現在必須測試已移轉的 BizTalk 應用程式中所述，傳送要求訊息，以執行 Oracle 資料庫時，插入作業[步驟 3： 測試已移轉的應用程式至 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="68e44-141">You must now test the migrated BizTalk application by sending a request message to perform an Insert operation on the Oracle database, as described in [Step 3: Test the migrated application to Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e44-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e44-142">See Also</span></span>  
 <span data-ttu-id="68e44-143">[教學課程： 移轉 BizTalk 專案](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span><span class="sxs-lookup"><span data-stu-id="68e44-143">[Tutorial: Migrating BizTalk Projects](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span></span>