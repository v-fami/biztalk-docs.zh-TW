---
title: "步驟 2： 設定的連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e804da96-26ae-482d-b6e1-67af24d639d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e31746fbbc34e24ab1638cb52c84f99e43a876b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-ports"></a><span data-ttu-id="6e5da-102">步驟 2： 設定的連接埠</span><span class="sxs-lookup"><span data-stu-id="6e5da-102">Step 2: Configure the Ports</span></span>
<span data-ttu-id="6e5da-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="6e5da-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="6e5da-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="6e5da-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="6e5da-105">**目標：**在此步驟中，您建立的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6e5da-105">**Objective:** In this step, you create the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="6e5da-106">您建立每個邏輯連接埠在協調流程中所建立的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="6e5da-106">You create a physical port for each logical port you created in the orchestration.</span></span> <span data-ttu-id="6e5da-107">您將建立下列連接埠：</span><span class="sxs-lookup"><span data-stu-id="6e5da-107">You will create the following ports:</span></span>  
  
-   <span data-ttu-id="6e5da-108">單向 WCF 自訂接收埠以接收通知訊息變更**員工**SQL Server 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="6e5da-108">A one-way WCF-Custom receive port to receive notification messages for changes to **Employee** table in a SQL Server database.</span></span>  
  
-   <span data-ttu-id="6e5da-109">要求-回應 WCF 自訂傳送埠以傳送要求訊息並接收回應叫用**UPDATE_EMPLOYEE**預存程序，在上執行插入作業的**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="6e5da-109">A request-response WCF-Custom send port to send request messages and receive response for invoking the **UPDATE_EMPLOYEE** stored procedure and for performing the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="6e5da-110">在協調流程中，您可以使用相同的傳送埠來執行這兩個作業。</span><span class="sxs-lookup"><span data-stu-id="6e5da-110">In the orchestration, you used the same send port to perform both the operations.</span></span> <span data-ttu-id="6e5da-111">同樣地，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您將這兩個作業使用單一傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6e5da-111">Similarly, in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you will use a single send port for both operations.</span></span>  
  
-   <span data-ttu-id="6e5da-112">單向傳送埠以傳送插入作業的回應。</span><span class="sxs-lookup"><span data-stu-id="6e5da-112">A one-way send port to send the response for the Insert operation.</span></span> <span data-ttu-id="6e5da-113">在本教學課程中，您必須通知採購部門，透過電子郵件，因為您建立此傳送埠做為 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="6e5da-113">In this tutorial, because you need to inform the Purchases department through an e-mail, you create this send port as an SMTP port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6e5da-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="6e5da-114">Prerequisites</span></span>  
 <span data-ttu-id="6e5da-115">您必須先完成[步驟 1： 部署的協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md))。</span><span class="sxs-lookup"><span data-stu-id="6e5da-115">You must have completed [Step 1: Deploy the Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md)).</span></span>  
  
### <a name="to-create-a-physical-one-way-receive-port"></a><span data-ttu-id="6e5da-116">若要建立單向的實體接收埠</span><span class="sxs-lookup"><span data-stu-id="6e5da-116">To create a physical one-way receive port</span></span>  
  
1.  <span data-ttu-id="6e5da-117">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6e5da-117">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="6e5da-118">在左邊主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-118">In the console tree on the left hand side, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="6e5da-119">展開**BizTalk 群組**，依序展開**應用程式**，然後展開**SampleApplication**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-119">Expand **BizTalk Group**, expand **Applications**, and expand **SampleApplication**.</span></span> <span data-ttu-id="6e5da-120">此教學課程中，您可以建立所有的連接埠和 SampleApplication 應用程式中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e5da-120">For this tutorial, you create all the ports and application within the SampleApplication application.</span></span>  
  
4.  <span data-ttu-id="6e5da-121">請遵循底下的 < 部署配接器的接收訊息從 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6e5da-121">Follow the instructions under the “Deploying Adapters for Receiving Messages from SQL Server” section of [Configure a port using the WCF-custom adapter and SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md).</span></span> <span data-ttu-id="6e5da-122">埠命名為**NotifyReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-122">Name the port as **NotifyReceivePort**.</span></span>  
  
5.  <span data-ttu-id="6e5da-123">請確定您設定下列繫結屬性設定配接器接收的變更通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="6e5da-123">Make sure you set the following binding properties to configure the adapter to receive notifications for changes to the **Employee** table.</span></span>  
  
    |<span data-ttu-id="6e5da-124">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="6e5da-124">Binding property</span></span>|<span data-ttu-id="6e5da-125">值</span><span class="sxs-lookup"><span data-stu-id="6e5da-125">Value</span></span>|  
    |----------------------|-----------|  
    |<span data-ttu-id="6e5da-126">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="6e5da-126">**InboundOperationType**</span></span>|<span data-ttu-id="6e5da-127">將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-127">Set this to **Notification**.</span></span>|  
    |<span data-ttu-id="6e5da-128">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="6e5da-128">**NotificationStatement**</span></span>|<span data-ttu-id="6e5da-129">將此值設定為：</span><span class="sxs-lookup"><span data-stu-id="6e5da-129">Set this to:</span></span><br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> <span data-ttu-id="6e5da-130">**注意：**您必須明確指定資料行名稱的陳述式中這個 Select 陳述式中所示。</span><span class="sxs-lookup"><span data-stu-id="6e5da-130">**Note:** You must specifically specify the column names in the statement as shown in this Select statement.</span></span> <span data-ttu-id="6e5da-131">此外，您必須一律指定資料表名稱，以及結構描述名稱，例如`dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="6e5da-131">Also, you must always specify the table name along with the schema name, for example, `dbo.Employee`.</span></span>|  
    |<span data-ttu-id="6e5da-132">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="6e5da-132">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="6e5da-133">將此設**True**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-133">Set this to **True**.</span></span>|  
  
     <span data-ttu-id="6e5da-134">如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6e5da-134">For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
### <a name="to-create-a-request-response-send-port-for-two-operations"></a><span data-ttu-id="6e5da-135">建立要求-回應傳送埠的兩個作業</span><span class="sxs-lookup"><span data-stu-id="6e5da-135">To create a request-response send port for two operations</span></span>  
  
1.  <span data-ttu-id="6e5da-136">請遵循底下的 < 部署配接器的傳送訊息至 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6e5da-136">Follow the instructions under the “Deploying Adapters for Sending Messages to SQL Server” section of [Configure a port using the WCF-custom adapter and SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md).</span></span> <span data-ttu-id="6e5da-137">埠命名為**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-137">Name the port as **SQLOutboundPort**.</span></span>  
  
2.  <span data-ttu-id="6e5da-138">因為您正在執行兩項作業使用相同的傳送埠時，您必須使用動態動作對應來指定作業的動作。</span><span class="sxs-lookup"><span data-stu-id="6e5da-138">Because you are performing two operations using the same send port, you must use dynamic action mapping to specify the action for the operation.</span></span> <span data-ttu-id="6e5da-139">在設定連接埠時**動作**方塊中，以下列方式指定動作對應：</span><span class="sxs-lookup"><span data-stu-id="6e5da-139">While configuring the port, in the **Action** box, specify the action mapping in the following manner:</span></span>  
  
    ```  
    \<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
      <Operation Name="UpdateEmp" Action="TypedProcedure/dbo/UPDATE_EMPLOYEE" />  
      <Operation Name="InsertPO" Action="TableOp/Insert/dbo/Purchase_Order" />  
    </BtsActionMapping>  
    ```  
  
     <span data-ttu-id="6e5da-140">請注意，在協調流程，您建立要求-回應傳送埠的兩個作業： **UpdateEmp**和**InsertPO**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-140">Note that in the orchestration, you created two operations for the request-response send port: **UpdateEmp** and **InsertPO**.</span></span> <span data-ttu-id="6e5da-141">因此，實體連接埠組態中您會提供相同的作業名稱動態動作對應中。</span><span class="sxs-lookup"><span data-stu-id="6e5da-141">So, in the physical port configuration you provide the same operation names in the dynamic action mapping.</span></span> <span data-ttu-id="6e5da-142">在以上摘錄中，為動作**UpdateEmp**作業`TypedProcedure/dbo/UPDATE_EMPLOYEE`。</span><span class="sxs-lookup"><span data-stu-id="6e5da-142">In the above excerpt, the action for **UpdateEmp** operation is `TypedProcedure/dbo/UPDATE_EMPLOYEE`.</span></span> <span data-ttu-id="6e5da-143">同樣地，針對動作**InsertPO**作業`TableOp/Insert/dbo/Purchase_Order`。</span><span class="sxs-lookup"><span data-stu-id="6e5da-143">Similarly, the action for **InsertPO** operation is `TableOp/Insert/dbo/Purchase_Order`.</span></span>  
  
3.  <span data-ttu-id="6e5da-144">您也必須設定傳送埠，使用您在對應的回應訊息的協調流程中建立的對應工具**UPDATE_EMPLOYEE**預存程序來插入作業的要求訊息**Purchase_順序**資料表。</span><span class="sxs-lookup"><span data-stu-id="6e5da-144">You must also configure the send port to use the Mapper you created in the orchestration to map the response message of **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation on **Purchase_Order** table.</span></span> <span data-ttu-id="6e5da-145">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="6e5da-145">To do so:</span></span>  
  
    1.  <span data-ttu-id="6e5da-146">以滑鼠右鍵按一下在 SQLOutboundPort[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-146">Right-click the SQLOutboundPort in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="6e5da-147">從**SQLOutboundPort-傳送埠屬性**對話方塊中的，從左窗格中，按一下**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-147">From the **SQLOutboundPort – Send Port Properties** dialog box, from the left pane, click **Outbound Maps**.</span></span>  
  
    3.  <span data-ttu-id="6e5da-148">從右窗格中，在**輸出對應**方塊中，按一下下方的儲存格**對應**資料行，然後從下拉式清單中，選取**[transform_1]**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-148">From the right-pane, in the **Outbound Maps** box, click the cell under the **Map** column, and from the drop-down list, select **Transform_1**.</span></span> <span data-ttu-id="6e5da-149">這是您建立 BizTalk 協調流程中之對應的名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e5da-149">This is the name of the map you created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
         <span data-ttu-id="6e5da-150">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-150">Click **OK**.</span></span>  
  
         <span data-ttu-id="6e5da-151">![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")</span><span class="sxs-lookup"><span data-stu-id="6e5da-151">![Configure outbound map](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")</span></span>  
  
### <a name="to-create-an-smtp-send-port"></a><span data-ttu-id="6e5da-152">若要建立 SMTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="6e5da-152">To create an SMTP send port</span></span>  
  
1.  <span data-ttu-id="6e5da-153">依照 「 如何設定 SMTP 傳送埠與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 」 區段在[http://go.microsoft.com/fwlink/?LinkId=141549](http://go.microsoft.com/fwlink/?LinkId=141549)。</span><span class="sxs-lookup"><span data-stu-id="6e5da-153">Follow the instructions under the “How to Configure an SMTP Send Port with the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console” section at [http://go.microsoft.com/fwlink/?LinkId=141549](http://go.microsoft.com/fwlink/?LinkId=141549).</span></span> <span data-ttu-id="6e5da-154">埠命名為**EmailResponse**。</span><span class="sxs-lookup"><span data-stu-id="6e5da-154">Name the port as **EmailResponse**.</span></span>  
  
2.  <span data-ttu-id="6e5da-155">連接埠組態的一部分，指定 電子郵件地址，如採購部門**至**屬性。</span><span class="sxs-lookup"><span data-stu-id="6e5da-155">As part of the port configuration, specify the e-mail address for the Purchases department for the **To** property.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="6e5da-156">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="6e5da-156">What did I just do?</span></span>  
 <span data-ttu-id="6e5da-157">在此步驟中您建立 WCF 自訂接收 SQL Server 從接收通知的連接埠、 Wcf-custom 傳送埠執行 SQL Server 上的作業和採購部門為以電子郵件傳送回應從 SQL Server 的 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="6e5da-157">In this step you created a WCF-Custom receive port for receiving notifications from SQL Server, WCF-Custom send port for performing operations on SQL Server, and an SMTP port for sending the response from SQL Server as an e-mail to the Purchases department.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6e5da-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6e5da-158">Next Steps</span></span>  
 <span data-ttu-id="6e5da-159">您設定和啟動 BizTalk 應用程式中所述[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6e5da-159">You configure and start the BizTalk application, as described in [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5da-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e5da-160">See Also</span></span>  
 <span data-ttu-id="6e5da-161">[步驟 1： 部署的協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="6e5da-161">[Step 1: Deploy the Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md) </span></span>  
 <span data-ttu-id="6e5da-162">[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="6e5da-162">[Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span></span>  
 [<span data-ttu-id="6e5da-163">第 5 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="6e5da-163">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)