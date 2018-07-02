---
title: 步驟 2： 設定的連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e804da96-26ae-482d-b6e1-67af24d639d9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fe05185c625825c795ee89dff10d5be9ae6a68d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973727"
---
# <a name="step-2-configure-the-ports"></a><span data-ttu-id="eca28-102">步驟 2： 設定的連接埠</span><span class="sxs-lookup"><span data-stu-id="eca28-102">Step 2: Configure the Ports</span></span>
<span data-ttu-id="eca28-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="eca28-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="eca28-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="eca28-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="eca28-105">**目標：** 在此步驟中，您會建立中的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="eca28-105">**Objective:** In this step, you create the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="eca28-106">您建立每個邏輯連接埠在協調流程中所建立的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="eca28-106">You create a physical port for each logical port you created in the orchestration.</span></span> <span data-ttu-id="eca28-107">您將建立下列連接埠：</span><span class="sxs-lookup"><span data-stu-id="eca28-107">You will create the following ports:</span></span>  
  
- <span data-ttu-id="eca28-108">在單向的 WCF 自訂接收埠以接收通知訊息的變更**員工**SQL Server 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="eca28-108">A one-way WCF-Custom receive port to receive notification messages for changes to **Employee** table in a SQL Server database.</span></span>  
  
- <span data-ttu-id="eca28-109">要求-回應 Wcf-custom 傳送埠以傳送要求訊息並接收回應，來叫用**UPDATE_EMPLOYEE**預存程序，並用來執行插入作業上**為 Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="eca28-109">A request-response WCF-Custom send port to send request messages and receive response for invoking the **UPDATE_EMPLOYEE** stored procedure and for performing the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="eca28-110">在協調流程中，您可以使用相同的傳送埠來執行這兩項作業。</span><span class="sxs-lookup"><span data-stu-id="eca28-110">In the orchestration, you used the same send port to perform both the operations.</span></span> <span data-ttu-id="eca28-111">同樣地，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您將用於這兩項作業中的單一傳送埠。</span><span class="sxs-lookup"><span data-stu-id="eca28-111">Similarly, in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you will use a single send port for both operations.</span></span>  
  
- <span data-ttu-id="eca28-112">單向傳送埠以傳送插入作業的回應。</span><span class="sxs-lookup"><span data-stu-id="eca28-112">A one-way send port to send the response for the Insert operation.</span></span> <span data-ttu-id="eca28-113">在本教學課程中，您需要告知採購部門，透過電子郵件，因為您建立此傳送埠與 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="eca28-113">In this tutorial, because you need to inform the Purchases department through an e-mail, you create this send port as an SMTP port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eca28-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="eca28-114">Prerequisites</span></span>  
 <span data-ttu-id="eca28-115">您必須先完成[步驟 1： 部署協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md))。</span><span class="sxs-lookup"><span data-stu-id="eca28-115">You must have completed [Step 1: Deploy the Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md)).</span></span>  
  
### <a name="to-create-a-physical-one-way-receive-port"></a><span data-ttu-id="eca28-116">若要建立單向的實體接收埠</span><span class="sxs-lookup"><span data-stu-id="eca28-116">To create a physical one-way receive port</span></span>  
  
1. <span data-ttu-id="eca28-117">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="eca28-117">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="eca28-118">在左邊的主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="eca28-118">In the console tree on the left hand side, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3. <span data-ttu-id="eca28-119">依序展開**BizTalk 群組**，展開**應用程式**，然後展開**SampleApplication**。</span><span class="sxs-lookup"><span data-stu-id="eca28-119">Expand **BizTalk Group**, expand **Applications**, and expand **SampleApplication**.</span></span> <span data-ttu-id="eca28-120">本教學課程中，您可以建立所有連接埠和 SampleApplication 應用程式內的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eca28-120">For this tutorial, you create all the ports and application within the SampleApplication application.</span></span>  
  
4. <span data-ttu-id="eca28-121">請遵循 < 部署配接器的接收訊息從 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="eca28-121">Follow the instructions under the “Deploying Adapters for Receiving Messages from SQL Server” section of [Configure a port using the WCF-custom adapter and SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md).</span></span> <span data-ttu-id="eca28-122">為埠命名**NotifyReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="eca28-122">Name the port as **NotifyReceivePort**.</span></span>  
  
5. <span data-ttu-id="eca28-123">請確定您設定下列的繫結屬性，以設定配接器接收的變更通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="eca28-123">Make sure you set the following binding properties to configure the adapter to receive notifications for changes to the **Employee** table.</span></span>  
  
   |<span data-ttu-id="eca28-124">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="eca28-124">Binding property</span></span>|<span data-ttu-id="eca28-125">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="eca28-125">Value</span></span>|  
   |----------------------|-----------|  
   |<span data-ttu-id="eca28-126">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="eca28-126">**InboundOperationType**</span></span>|<span data-ttu-id="eca28-127">將此設為**通知**。</span><span class="sxs-lookup"><span data-stu-id="eca28-127">Set this to **Notification**.</span></span>|  
   |<span data-ttu-id="eca28-128">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="eca28-128">**NotificationStatement**</span></span>|<span data-ttu-id="eca28-129">將此設為：</span><span class="sxs-lookup"><span data-stu-id="eca28-129">Set this to:</span></span><br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> <span data-ttu-id="eca28-130">**注意：** 您必須特別指定的資料行名稱的陳述式中，這個 Select 陳述式中所示。</span><span class="sxs-lookup"><span data-stu-id="eca28-130">**Note:** You must specifically specify the column names in the statement as shown in this Select statement.</span></span> <span data-ttu-id="eca28-131">此外，您必須一律指定資料表名稱，以及結構描述名稱，例如`dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="eca28-131">Also, you must always specify the table name along with the schema name, for example, `dbo.Employee`.</span></span>|  
   |<span data-ttu-id="eca28-132">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="eca28-132">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="eca28-133">將此設為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="eca28-133">Set this to **True**.</span></span>|  
  
    <span data-ttu-id="eca28-134">如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="eca28-134">For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
### <a name="to-create-a-request-response-send-port-for-two-operations"></a><span data-ttu-id="eca28-135">建立要求-回應傳送埠的兩個作業</span><span class="sxs-lookup"><span data-stu-id="eca28-135">To create a request-response send port for two operations</span></span>  
  
1. <span data-ttu-id="eca28-136">請遵循 < 部署配接器的傳送訊息至 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="eca28-136">Follow the instructions under the “Deploying Adapters for Sending Messages to SQL Server” section of [Configure a port using the WCF-custom adapter and SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md).</span></span> <span data-ttu-id="eca28-137">為埠命名**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="eca28-137">Name the port as **SQLOutboundPort**.</span></span>  
  
2. <span data-ttu-id="eca28-138">因為您正在執行兩項作業使用同一個傳送埠時，您必須使用動態動作對應，以指定作業的動作。</span><span class="sxs-lookup"><span data-stu-id="eca28-138">Because you are performing two operations using the same send port, you must use dynamic action mapping to specify the action for the operation.</span></span> <span data-ttu-id="eca28-139">在中設定連接埠時**動作**方塊中，以下列方式指定動作對應：</span><span class="sxs-lookup"><span data-stu-id="eca28-139">While configuring the port, in the **Action** box, specify the action mapping in the following manner:</span></span>  
  
   ```  
   <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
     <Operation Name="UpdateEmp" Action="TypedProcedure/dbo/UPDATE_EMPLOYEE" />  
     <Operation Name="InsertPO" Action="TableOp/Insert/dbo/Purchase_Order" />  
   </BtsActionMapping>  
   ```  
  
    <span data-ttu-id="eca28-140">請注意，在協調流程中，您已建立要求-回應傳送埠的兩個作業： **UpdateEmp**並**InsertPO**。</span><span class="sxs-lookup"><span data-stu-id="eca28-140">Note that in the orchestration, you created two operations for the request-response send port: **UpdateEmp** and **InsertPO**.</span></span> <span data-ttu-id="eca28-141">因此，實體連接埠組態中您會提供相同的作業名稱中的動態動作對應。</span><span class="sxs-lookup"><span data-stu-id="eca28-141">So, in the physical port configuration you provide the same operation names in the dynamic action mapping.</span></span> <span data-ttu-id="eca28-142">在以上摘錄中，動作**UpdateEmp**作業`TypedProcedure/dbo/UPDATE_EMPLOYEE`。</span><span class="sxs-lookup"><span data-stu-id="eca28-142">In the above excerpt, the action for **UpdateEmp** operation is `TypedProcedure/dbo/UPDATE_EMPLOYEE`.</span></span> <span data-ttu-id="eca28-143">同樣地，針對動作**InsertPO**作業`TableOp/Insert/dbo/Purchase_Order`。</span><span class="sxs-lookup"><span data-stu-id="eca28-143">Similarly, the action for **InsertPO** operation is `TableOp/Insert/dbo/Purchase_Order`.</span></span>  
  
3. <span data-ttu-id="eca28-144">您也必須設定傳送埠，使用您在要對應的回應訊息的協調流程中建立對應工具**UPDATE_EMPLOYEE**預存程序來插入作業的要求訊息**Purchase_順序**資料表。</span><span class="sxs-lookup"><span data-stu-id="eca28-144">You must also configure the send port to use the Mapper you created in the orchestration to map the response message of **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation on **Purchase_Order** table.</span></span> <span data-ttu-id="eca28-145">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="eca28-145">To do so:</span></span>  
  
   1. <span data-ttu-id="eca28-146">以滑鼠右鍵按一下 在 SQLOutboundPort[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="eca28-146">Right-click the SQLOutboundPort in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and then click **Properties**.</span></span>  
  
   2. <span data-ttu-id="eca28-147">從**SQLOutboundPort-傳送埠屬性**對話方塊中，從左窗格中，按一下**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="eca28-147">From the **SQLOutboundPort – Send Port Properties** dialog box, from the left pane, click **Outbound Maps**.</span></span>  
  
   3. <span data-ttu-id="eca28-148">從右窗格中，在**輸出對應**方塊中，按一下下方的儲存格**地圖**資料行，然後從下拉式清單中，選取 **[transform_1]**。</span><span class="sxs-lookup"><span data-stu-id="eca28-148">From the right-pane, in the **Outbound Maps** box, click the cell under the **Map** column, and from the drop-down list, select **Transform_1**.</span></span> <span data-ttu-id="eca28-149">這是 BizTalk 協調流程中建立的對應名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eca28-149">This is the name of the map you created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
       <span data-ttu-id="eca28-150">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="eca28-150">Click **OK**.</span></span>  
  
       <span data-ttu-id="eca28-151">![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")</span><span class="sxs-lookup"><span data-stu-id="eca28-151">![Configure outbound map](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")</span></span>  
  
### <a name="to-create-an-smtp-send-port"></a><span data-ttu-id="eca28-152">若要建立 SMTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="eca28-152">To create an SMTP send port</span></span>  
  
1. <span data-ttu-id="eca28-153">請依照下列指示 「 如何設定 SMTP 傳送埠與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 」 一節[ http://go.microsoft.com/fwlink/?LinkId=141549 ](http://go.microsoft.com/fwlink/?LinkId=141549)。</span><span class="sxs-lookup"><span data-stu-id="eca28-153">Follow the instructions under the “How to Configure an SMTP Send Port with the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console” section at [http://go.microsoft.com/fwlink/?LinkId=141549](http://go.microsoft.com/fwlink/?LinkId=141549).</span></span> <span data-ttu-id="eca28-154">為埠命名**EmailResponse**。</span><span class="sxs-lookup"><span data-stu-id="eca28-154">Name the port as **EmailResponse**.</span></span>  
  
2. <span data-ttu-id="eca28-155">指定連接埠組態的一部分，採購部門電子郵件地址**至**屬性。</span><span class="sxs-lookup"><span data-stu-id="eca28-155">As part of the port configuration, specify the e-mail address for the Purchases department for the **To** property.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="eca28-156">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="eca28-156">What did I just do?</span></span>  
 <span data-ttu-id="eca28-157">在此步驟中您建立 WCF 自訂接收從 SQL Server 中接收通知的連接埠、 Wcf-custom 傳送埠執行 SQL Server 上的作業和採購部門電子郵件形式傳送回應從 SQL Server 的 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="eca28-157">In this step you created a WCF-Custom receive port for receiving notifications from SQL Server, WCF-Custom send port for performing operations on SQL Server, and an SMTP port for sending the response from SQL Server as an e-mail to the Purchases department.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eca28-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eca28-158">Next Steps</span></span>  
 <span data-ttu-id="eca28-159">您設定和啟動 BizTalk 應用程式中所述[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)。</span><span class="sxs-lookup"><span data-stu-id="eca28-159">You configure and start the BizTalk application, as described in [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca28-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eca28-160">See Also</span></span>  
 <span data-ttu-id="eca28-161">[步驟 1： 部署協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="eca28-161">[Step 1: Deploy the Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md) </span></span>  
 <span data-ttu-id="eca28-162">[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="eca28-162">[Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span></span>  
 [<span data-ttu-id="eca28-163">第 5 課：部署方案</span><span class="sxs-lookup"><span data-stu-id="eca28-163">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)