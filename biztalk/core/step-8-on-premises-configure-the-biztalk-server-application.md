---
title: 步驟 8 （內部部署）： 設定 BizTalk Server 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2015-12-08
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5109fb54-8453-444f-bc9c-070a65053397
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b3eafcc5e49bb6fa360f1db4b6e92d9393068a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996839"
---
# <a name="step-8-on-premises-configure-the-biztalk-server-application"></a><span data-ttu-id="cb611-102">步驟 8 （內部部署）： 設定 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="cb611-102">Step 8 (On Premises): Configure the BizTalk Server Application</span></span>
<span data-ttu-id="cb611-103">在上一個步驟中，您建立了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="cb611-103">In the previous step you created a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span> <span data-ttu-id="cb611-104">在此步驟中，您將建置、部署和設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb611-104">In this step, you’ll build, deploy, and configure the application.</span></span>  

## <a name="build-and-deploy-the-application"></a><span data-ttu-id="cb611-105">建置及部署應用程式</span><span class="sxs-lookup"><span data-stu-id="cb611-105">Build and deploy the application</span></span>  

1.  <span data-ttu-id="cb611-106">在 Visual Studio 中，以滑鼠右鍵按一下 方案總管 中的方案名稱，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="cb611-106">In Visual Studio, right-click the solution name in the Solution Explorer, and click **Build**.</span></span>  

2.  <span data-ttu-id="cb611-107">部署程序要求組件必須是以強式名稱簽署的。</span><span class="sxs-lookup"><span data-stu-id="cb611-107">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="cb611-108">您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。</span><span class="sxs-lookup"><span data-stu-id="cb611-108">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  

    1.  <span data-ttu-id="cb611-109">在 [方案總管] 中，以滑鼠右鍵按一下 **[orderprocessingdemo]** 專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cb611-109">In Solution Explorer, right-click the **OrderProcessingDemo** project, and then click **Properties**.</span></span>  

    2.  <span data-ttu-id="cb611-110">按一下  **Signing**索引標籤，然後選取**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cb611-110">Click the **Signing** tab, and select the **Sign the assembly** checkbox.</span></span>  

    3.  <span data-ttu-id="cb611-111">從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<新增...\>**.</span><span class="sxs-lookup"><span data-stu-id="cb611-111">From the drop-down list in the **Choose a strong name key file** box, select **\<New…\>**.</span></span>  

    4.  <span data-ttu-id="cb611-112">在 **建立強式名稱金鑰**對話方塊方塊中，輸入金鑰檔案名稱，例如`OrderProcessingDemo.snk`。</span><span class="sxs-lookup"><span data-stu-id="cb611-112">In the **Create Strong Name Key** dialog box, enter a name for the key file, for example `OrderProcessingDemo.snk`.</span></span> <span data-ttu-id="cb611-113">清除保護使用密碼，金鑰檔的核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cb611-113">Clear the checkbox for protecting the key file with a password, and then click **OK**.</span></span>  

3.  <span data-ttu-id="cb611-114">按一下 **部署**索引標籤上，在右邊的方塊**應用程式名稱**，型別`OrderProcessingDemo`。</span><span class="sxs-lookup"><span data-stu-id="cb611-114">Click the **Deployment** tab, in the box to the right of **Application Name**, type `OrderProcessingDemo`.</span></span>  

4.  <span data-ttu-id="cb611-115">從下拉式清單方塊的清單中的右邊**重新部署**，選取 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="cb611-115">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  

5.  <span data-ttu-id="cb611-116">在 [方案總管] 中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="cb611-116">In Solution Explorer, right-click **OrderProcessingDemo**, and then click **Deploy**.</span></span>  <span data-ttu-id="cb611-117">此時，[輸出] 視窗應該會顯示：</span><span class="sxs-lookup"><span data-stu-id="cb611-117">The Output window should display:</span></span>  

    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  

    ```  

## <a name="configure-the-application"></a><span data-ttu-id="cb611-118">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="cb611-118">Configure the application</span></span>  

1. <span data-ttu-id="cb611-119">按一下 **開始**，指向**所有程式**，指向**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb611-119">Click **Start**, point to **All Programs**, point to **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  

2. <span data-ttu-id="cb611-120">在左窗格中的主控台樹狀目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="cb611-120">In the console tree on the left pane, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.</span></span>  

3. <span data-ttu-id="cb611-121">依序展開**BizTalk 群組**，展開**應用程式**，展開 **[orderprocessingdemo]**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="cb611-121">Expand **BizTalk Group**, expand **Applications**, expand **OrderProcessingDemo**, and then click **Orchestrations**.</span></span> <span data-ttu-id="cb611-122">您會看到**OrderProcessingDemo.OrderProcessing**部署協調流程。</span><span class="sxs-lookup"><span data-stu-id="cb611-122">You will see that the **OrderProcessingDemo.OrderProcessing** orchestration is deployed.</span></span>  

4. <span data-ttu-id="cb611-123">在協調流程中，您已建立了邏輯連接埠 (**ReceiveSO**) 以接收來自服務匯流排佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="cb611-123">In the orchestration, you created a logical port (**ReceiveSO**) to receive messages from the Service Bus Queue.</span></span> <span data-ttu-id="cb611-124">在此步驟中，您會建立實體接收埠以對應至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb611-124">In this step, you create a physical receive port to map to the logical port.</span></span>  

   1. <span data-ttu-id="cb611-125">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="cb611-125">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  

   2. <span data-ttu-id="cb611-126">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-126">On the **General** tab, do the following:</span></span>  


      |                <span data-ttu-id="cb611-127">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-127">Use this</span></span>                |     <span data-ttu-id="cb611-128">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-128">To do this</span></span>      |
      |----------------------------------------|---------------------|
      |                <span data-ttu-id="cb611-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-129">**Name**</span></span>                | <span data-ttu-id="cb611-130">型別**ReceiveSO**。</span><span class="sxs-lookup"><span data-stu-id="cb611-130">Type **ReceiveSO**.</span></span> |
      | <span data-ttu-id="cb611-131">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="cb611-131">**Enable routing for failed messages**</span></span> |       <span data-ttu-id="cb611-132">(清除)</span><span class="sxs-lookup"><span data-stu-id="cb611-132">(clear)</span></span>       |


   3. <span data-ttu-id="cb611-133">按一下 **接收位置**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="cb611-133">Click **Receive Locations**, and then click **New**.</span></span>  

   4. <span data-ttu-id="cb611-134">從 [Receive Location1 - 接收位置屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-134">From Receive Location1 – Receive Location Properties dialog box, do the following:</span></span>  


      |       <span data-ttu-id="cb611-135">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-135">Use this</span></span>       |              <span data-ttu-id="cb611-136">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-136">To do this</span></span>              |
      |----------------------|--------------------------------------|
      |       <span data-ttu-id="cb611-137">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-137">**Name**</span></span>       |      <span data-ttu-id="cb611-138">型別**ReceiveOrders_SO**。</span><span class="sxs-lookup"><span data-stu-id="cb611-138">Type **ReceiveOrders_SO**.</span></span>      |
      |       <span data-ttu-id="cb611-139">**型別**</span><span class="sxs-lookup"><span data-stu-id="cb611-139">**Type**</span></span>       |       <span data-ttu-id="cb611-140">選取  **SB Messaging**。</span><span class="sxs-lookup"><span data-stu-id="cb611-140">Select **SB-Messaging**.</span></span>       |
      | <span data-ttu-id="cb611-141">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="cb611-141">**Receive handler**</span></span>  | <span data-ttu-id="cb611-142">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="cb611-142">Select **BizTalkServerApplication**.</span></span> |
      | <span data-ttu-id="cb611-143">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="cb611-143">**Receive pipeline**</span></span> |        <span data-ttu-id="cb611-144">選取  **XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="cb611-144">Select **XMLReceive**.</span></span>        |


   5. <span data-ttu-id="cb611-145">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cb611-145">Click **Configure**.</span></span>  

   6. <span data-ttu-id="cb611-146">從 [Sb-messaging 傳輸屬性] 對話方塊中上,**一般**索引標籤上，如**佇列或訂用帳戶的 URL**，輸入**sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**.</span><span class="sxs-lookup"><span data-stu-id="cb611-146">From SB-Messaging Transport Properties dialog box, on the **General** tab, for **Queue or Subscription URL**, enter **sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**.</span></span> <span data-ttu-id="cb611-147">在這裡， *mynamespace*是服務匯流排命名空間並*queueordersedi*是您在建立服務匯流排佇列[(適用於 Azure) 的步驟 3： 建立服務匯流排佇列](../core/step-3-for-azure-create-a-service-bus-queue.md)。</span><span class="sxs-lookup"><span data-stu-id="cb611-147">Here, *mynamespace* is the Service Bus namespace and *queueordersedi* is the Service Bus Queue that you created in [Step 3 (For Azure): Create a Service Bus Queue](../core/step-3-for-azure-create-a-service-bus-queue.md).</span></span>  

   7. <span data-ttu-id="cb611-148">從 [Sb-messaging 傳輸屬性] 對話方塊中，在**驗證**索引標籤上，指定下列值：</span><span class="sxs-lookup"><span data-stu-id="cb611-148">From SB-Messaging Transport Properties dialog box, on the **Authentication** tab, specify the following values:</span></span>  

      |<span data-ttu-id="cb611-149">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-149">Use this</span></span>|<span data-ttu-id="cb611-150">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-150">To do this</span></span>|  
      |--------------|----------------|  
      |<span data-ttu-id="cb611-151">**存取控制服務 STS Uri**</span><span class="sxs-lookup"><span data-stu-id="cb611-151">**Access Control Service STS Uri**</span></span>|<span data-ttu-id="cb611-152">輸入 `https://mynamespace-sb.accesscontrol.appfabriclabs.com/`</span><span class="sxs-lookup"><span data-stu-id="cb611-152">Type `https://mynamespace-sb.accesscontrol.appfabriclabs.com/`</span></span>|  
      |<span data-ttu-id="cb611-153">**簽發者名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-153">**Issuer name**</span></span>|<span data-ttu-id="cb611-154">指定簽發者名稱。</span><span class="sxs-lookup"><span data-stu-id="cb611-154">Specify the issuer name.</span></span> <span data-ttu-id="cb611-155">通常這會設定為`owner`。</span><span class="sxs-lookup"><span data-stu-id="cb611-155">Typically this is set to `owner`.</span></span>|  
      |<span data-ttu-id="cb611-156">**簽發者金鑰**</span><span class="sxs-lookup"><span data-stu-id="cb611-156">**Issuer key**</span></span>|<span data-ttu-id="cb611-157">指定簽發者金鑰。</span><span class="sxs-lookup"><span data-stu-id="cb611-157">Specify the issuer key.</span></span>|  

      > [!NOTE]
      >  <span data-ttu-id="cb611-158">您可以取得的值佇列 URL、 ACS URL、 簽發者名稱和金鑰[Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886)。</span><span class="sxs-lookup"><span data-stu-id="cb611-158">You can get the values for the Queue URL, ACS URL, issuer name and key from the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886).</span></span>  

   8. <span data-ttu-id="cb611-159">按一下 **確定**直到結束所有對話方塊為止。</span><span class="sxs-lookup"><span data-stu-id="cb611-159">Click **OK** until you exit all the dialog boxes.</span></span>  

5. <span data-ttu-id="cb611-160">在協調流程中，您已建立了邏輯連接埠 (**SendToSQL**) 將訊息傳送至**SalesOrder**資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="cb611-160">In the orchestration, you created a logical port (**SendToSQL**) to send messages to the **SalesOrder** database table.</span></span> <span data-ttu-id="cb611-161">在此步驟中，您會建立實體傳送埠以對應至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb611-161">In this step, you create a physical send port to map to the logical port.</span></span>  

   1. <span data-ttu-id="cb611-162">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="cb611-162">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

   2. <span data-ttu-id="cb611-163">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-163">On the General tab, do the following:</span></span>  


      |     <span data-ttu-id="cb611-164">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-164">Use this</span></span>      |              <span data-ttu-id="cb611-165">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-165">To do this</span></span>              |
      |-------------------|--------------------------------------|
      |     <span data-ttu-id="cb611-166">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-166">**Name**</span></span>      |         <span data-ttu-id="cb611-167">型別**SendToSQL**。</span><span class="sxs-lookup"><span data-stu-id="cb611-167">Type **SendToSQL**.</span></span>          |
      |     <span data-ttu-id="cb611-168">**型別**</span><span class="sxs-lookup"><span data-stu-id="cb611-168">**Type**</span></span>      |         <span data-ttu-id="cb611-169">選取  **WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="cb611-169">Select **WCF-SQL**.</span></span>          |
      | <span data-ttu-id="cb611-170">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="cb611-170">**Send handler**</span></span>  | <span data-ttu-id="cb611-171">選取  **BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="cb611-171">Select **BizTAlkServerApplication**.</span></span> |
      | <span data-ttu-id="cb611-172">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="cb611-172">**Send pipeline**</span></span> |     <span data-ttu-id="cb611-173">選取  **PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="cb611-173">Select **PassThruTransmit**.</span></span>     |


   3. <span data-ttu-id="cb611-174">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cb611-174">Click **Configure**.</span></span>  

   4. <span data-ttu-id="cb611-175">從 [WCF-SQL 傳輸屬性] 上**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-175">From WCF-SQL Transport Properties, on the **General** tab, do the following:</span></span>  


      |     <span data-ttu-id="cb611-176">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-176">Use this</span></span>      |                                                                                                                                                                                    <span data-ttu-id="cb611-177">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-177">To do this</span></span>                                                                                                                                                                                    |
      |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | <span data-ttu-id="cb611-178">**位址 (URI)**</span><span class="sxs-lookup"><span data-stu-id="cb611-178">**Address (URI)**</span></span> | <span data-ttu-id="cb611-179">型別**mssql://computername/database_instance_name/databasename**。</span><span class="sxs-lookup"><span data-stu-id="cb611-179">Type **mssql://computername/database_instance_name/databasename**.</span></span> <span data-ttu-id="cb611-180">例如，若要連接到**DemoDB**預設資料庫執行個體之下執行的本機電腦上的資料庫中，輸入 `mssql://.//DemoDB`</span><span class="sxs-lookup"><span data-stu-id="cb611-180">For example, to connect to a **DemoDB** database on the local computer running under the default database instance, enter `mssql://.//DemoDB`</span></span><br /><br /> <span data-ttu-id="cb611-181">如需詳細資訊，請參閱 <<c0> [ 建立 SQL Server 連接 URI](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="cb611-181">For more information, see [Create the SQL Server connection URI](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span> |
      |    <span data-ttu-id="cb611-182">**動作**</span><span class="sxs-lookup"><span data-stu-id="cb611-182">**Action**</span></span>     |                                                                                                                                                                     <span data-ttu-id="cb611-183">型別**TableOp/Insert/dbo/SalesOrder**。</span><span class="sxs-lookup"><span data-stu-id="cb611-183">Type **TableOp/Insert/dbo/SalesOrder**.</span></span>                                                                                                                                                                      |


   5. <span data-ttu-id="cb611-184">從 [WCF-SQL 傳輸屬性] 上**認證**索引標籤上，選取**不會使用單一登入**，並指定 （區分大小寫） 的認證，以連接到 SQL Server 資料庫中所指定連接字串。</span><span class="sxs-lookup"><span data-stu-id="cb611-184">From WCF-SQL Transport Properties, on the **Credentials** tab, select **Do not use Single Sign-On**, and specify credentials (case-sensitive) to connect to the SQL Server database you specified in the connection string.</span></span> <span data-ttu-id="cb611-185">如果您想使用 [Windows 驗證] 進行連線，請將認證空白。</span><span class="sxs-lookup"><span data-stu-id="cb611-185">If you want to connect using Windows Authentication, leave the credentials blank.</span></span>  

   6. <span data-ttu-id="cb611-186">按一下 **確定**直到結束所有對話方塊為止。</span><span class="sxs-lookup"><span data-stu-id="cb611-186">Click **OK** until you exit all the dialog boxes.</span></span>  

6. <span data-ttu-id="cb611-187">在協調流程中，您已建立了邏輯連接埠 (**SendToFile**) 將訊息傳送至共用的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="cb611-187">In the orchestration, you created a logical port (**SendToFile**) to send messages to a shared file location.</span></span> <span data-ttu-id="cb611-188">在此步驟中，您會建立實體傳送埠以對應至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb611-188">In this step, you create a physical send port to map to the logical port.</span></span>  

   1. <span data-ttu-id="cb611-189">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="cb611-189">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

   2. <span data-ttu-id="cb611-190">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-190">On the General tab, do the following:</span></span>  


      |     <span data-ttu-id="cb611-191">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-191">Use this</span></span>      |              <span data-ttu-id="cb611-192">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-192">To do this</span></span>              |
      |-------------------|--------------------------------------|
      |     <span data-ttu-id="cb611-193">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-193">**Name**</span></span>      |         <span data-ttu-id="cb611-194">型別**SendToFile**。</span><span class="sxs-lookup"><span data-stu-id="cb611-194">Type **SendToFile**.</span></span>         |
      |     <span data-ttu-id="cb611-195">**型別**</span><span class="sxs-lookup"><span data-stu-id="cb611-195">**Type**</span></span>      |           <span data-ttu-id="cb611-196">選取 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="cb611-196">Select **File**.</span></span>           |
      | <span data-ttu-id="cb611-197">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="cb611-197">**Send handler**</span></span>  | <span data-ttu-id="cb611-198">選取  **BizTAlkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="cb611-198">Select **BizTAlkServerApplication**.</span></span> |
      | <span data-ttu-id="cb611-199">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="cb611-199">**Send pipeline**</span></span> |       <span data-ttu-id="cb611-200">選取  **XML 傳輸**。</span><span class="sxs-lookup"><span data-stu-id="cb611-200">Select **XML Transmit**.</span></span>       |


   3. <span data-ttu-id="cb611-201">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cb611-201">Click **Configure**.</span></span>  

   4. <span data-ttu-id="cb611-202">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cb611-202">From File Transport Properties, do the following:</span></span>  


      |      <span data-ttu-id="cb611-203">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-203">Use this</span></span>      |                        <span data-ttu-id="cb611-204">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-204">To do this</span></span>                        |
      |--------------------|----------------------------------------------------------|
      | <span data-ttu-id="cb611-205">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="cb611-205">**Receive folder**</span></span> | <span data-ttu-id="cb611-206">指定您想要傳送訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="cb611-206">Specify the location where you want to send the message.</span></span> |
      |   <span data-ttu-id="cb611-207">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="cb611-207">**File name**</span></span>    |               <span data-ttu-id="cb611-208">保留 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="cb611-208">Retain **%MessageID%.xml**.</span></span>                |


   5. <span data-ttu-id="cb611-209">按一下 **確定**直到結束所有對話方塊為止。</span><span class="sxs-lookup"><span data-stu-id="cb611-209">Click **OK** until you exit all the dialog boxes.</span></span>  

7. <span data-ttu-id="cb611-210">您現在必須繫結在一起，以設定應用程式的實體和邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb611-210">You must now bind the physical and logical ports together to configure the application.</span></span>  

   1. <span data-ttu-id="cb611-211">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="cb611-211">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Configure**.</span></span>  

   2. <span data-ttu-id="cb611-212">從 設定應用程式，在左窗格中，按一下**OrderProcessing**。</span><span class="sxs-lookup"><span data-stu-id="cb611-212">From Configure Application, in the left pane, click **OrderProcessing**.</span></span>  

   3. <span data-ttu-id="cb611-213">使用下表中的值來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb611-213">Use the values in the following table to configure the application.</span></span>  


      |            <span data-ttu-id="cb611-214">使用</span><span class="sxs-lookup"><span data-stu-id="cb611-214">Use this</span></span>             |             <span data-ttu-id="cb611-215">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cb611-215">To do this</span></span>              |
      |---------------------------------|-------------------------------------|
      |          <span data-ttu-id="cb611-216">針對**主應用程式**</span><span class="sxs-lookup"><span data-stu-id="cb611-216">For **Host**</span></span>           | <span data-ttu-id="cb611-217">選取**BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="cb611-217">Select **BizTalkServerApplication**</span></span> |
      | <span data-ttu-id="cb611-218">對於邏輯連接埠**ReceiveSO**</span><span class="sxs-lookup"><span data-stu-id="cb611-218">For logical port **ReceiveSO**</span></span>  | <span data-ttu-id="cb611-219">選取實體連接埠**ReceiveSO**</span><span class="sxs-lookup"><span data-stu-id="cb611-219">Select physical port **ReceiveSO**</span></span>  |
      | <span data-ttu-id="cb611-220">對於邏輯連接埠**SendToSQL**</span><span class="sxs-lookup"><span data-stu-id="cb611-220">For logical port **SendToSQL**</span></span>  | <span data-ttu-id="cb611-221">選取實體連接埠**SendToSQL**</span><span class="sxs-lookup"><span data-stu-id="cb611-221">Select physical port **SendToSQL**</span></span>  |
      | <span data-ttu-id="cb611-222">對於邏輯連接埠 **[sendtofile]**</span><span class="sxs-lookup"><span data-stu-id="cb611-222">For logical port **SendToFile**</span></span> | <span data-ttu-id="cb611-223">選取實體連接埠 **[sendtofile]**</span><span class="sxs-lookup"><span data-stu-id="cb611-223">Select physical port **SendToFile**</span></span> |


   4. <span data-ttu-id="cb611-224">按一下 **確定**儲存設定。</span><span class="sxs-lookup"><span data-stu-id="cb611-224">Click **OK** to save the configuration.</span></span>  

## <a name="start-the-application"></a><span data-ttu-id="cb611-225">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="cb611-225">Start the application</span></span>  

1. <span data-ttu-id="cb611-226">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="cb611-226">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Start**.</span></span>  

2. <span data-ttu-id="cb611-227">在對話方塊中，按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="cb611-227">From the dialog, click **Start**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="cb611-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb611-228">See Also</span></span>  
 [<span data-ttu-id="cb611-229">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="cb611-229">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)