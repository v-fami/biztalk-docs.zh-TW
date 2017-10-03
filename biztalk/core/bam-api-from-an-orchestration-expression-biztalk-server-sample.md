---
title: "BAM API，從協調流程運算式 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, BAM
- examples, orchestrations
- BAM, examples
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26b9cbc21eb93cad52a421b7df0912a37708978c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-api-from-an-orchestration-expression-biztalk-server-sample"></a><span data-ttu-id="1ff9a-102">BAM API，從協調流程運算式 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="1ff9a-102">BAM API from an Orchestration Expression (BizTalk Server Sample)</span></span>
<span data-ttu-id="1ff9a-103">這個範例會示範如何：</span><span class="sxs-lookup"><span data-stu-id="1ff9a-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="1ff9a-104">使用 BAM API 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程運算式。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-104">Use the BAM API from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration expression.</span></span>  
  
-   <span data-ttu-id="1ff9a-105">重複的訊息內的項目，例如個別活動執行個體的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-105">Track repeating items inside a message as separate activity instances.</span></span>  
  
-   <span data-ttu-id="1ff9a-106">建立追蹤使用追蹤設定檔的 BAM 資料之間的關聯性，並使用 BAM API 追蹤 BAM 資料。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-106">Create a relationship between BAM data that is tracked by using a tracking profile, and BAM data tracked by using the BAM API.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="1ff9a-107">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="1ff9a-107">Where to Find This Sample</span></span>  
 <span data-ttu-id="1ff9a-108">您可以找到此範例位於*\<範例路徑 >*\BAM\BamFromExpression。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-108">You can find this sample at *\<Samples Path>*\BAM\BamFromExpression.</span></span>  
  
 <span data-ttu-id="1ff9a-109">下表列出此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-109">The following table lists the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="1ff9a-110">檔案</span><span class="sxs-lookup"><span data-stu-id="1ff9a-110">File</span></span>|<span data-ttu-id="1ff9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="1ff9a-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1ff9a-112">BamDefinition.xls</span><span class="sxs-lookup"><span data-stu-id="1ff9a-112">BamDefinition.xls</span></span>|<span data-ttu-id="1ff9a-113">BAM 定義樣式表。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-113">BAM definition stylesheet.</span></span>|  
|<span data-ttu-id="1ff9a-114">BamDefinition.xml</span><span class="sxs-lookup"><span data-stu-id="1ff9a-114">BamDefinition.xml</span></span>|<span data-ttu-id="1ff9a-115">BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-115">BAM definition.</span></span>|  
|<span data-ttu-id="1ff9a-116">BamFromExpression.btproj</span><span class="sxs-lookup"><span data-stu-id="1ff9a-116">BamFromExpression.btproj</span></span>|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="1ff9a-117">追蹤檔案的專案。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-117"> tracking file project.</span></span>|  
|<span data-ttu-id="1ff9a-118">BamFromExpression.sln</span><span class="sxs-lookup"><span data-stu-id="1ff9a-118">BamFromExpression.sln</span></span>|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="1ff9a-119">方案。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-119"> solution.</span></span>|  
|<span data-ttu-id="1ff9a-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="1ff9a-120">Cleanup.bat</span></span>|<span data-ttu-id="1ff9a-121">用來解除部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-121">Batch file to undeploy the sample.</span></span>|  
|<span data-ttu-id="1ff9a-122">InputMessage.xml</span><span class="sxs-lookup"><span data-stu-id="1ff9a-122">InputMessage.xml</span></span>|<span data-ttu-id="1ff9a-123">輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-123">Input message.</span></span>|  
|<span data-ttu-id="1ff9a-124">Orchestration1.odx</span><span class="sxs-lookup"><span data-stu-id="1ff9a-124">Orchestration1.odx</span></span>|<span data-ttu-id="1ff9a-125">協調流程。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-125">Orchestration.</span></span>|  
|<span data-ttu-id="1ff9a-126">PoSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="1ff9a-126">PoSchema.xsd</span></span>|<span data-ttu-id="1ff9a-127">訂單結構描述。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-127">Purchase order schema.</span></span>|  
|<span data-ttu-id="1ff9a-128">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="1ff9a-128">PropertySchema.xsd</span></span>|<span data-ttu-id="1ff9a-129">屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-129">Property schema.</span></span>|  
|<span data-ttu-id="1ff9a-130">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="1ff9a-130">Setup.bat</span></span>|<span data-ttu-id="1ff9a-131">用來編譯和部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-131">Batch file to compile and deploy the sample.</span></span>|  
|<span data-ttu-id="1ff9a-132">QueryBam.sql</span><span class="sxs-lookup"><span data-stu-id="1ff9a-132">QueryBam.sql</span></span>|<span data-ttu-id="1ff9a-133">SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-133">SQL script.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="1ff9a-134">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="1ff9a-134">How to Use This Sample</span></span>  
 <span data-ttu-id="1ff9a-135">使用下列程序來建立追蹤設定檔、 執行範例，以及檢視結果。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-135">Use the following procedures to create the tracking profile, run the sample, and view the results.</span></span>  
  
#### <a name="to-create-the-tracking-profile"></a><span data-ttu-id="1ff9a-136">若要建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="1ff9a-136">To create the tracking profile</span></span>  
  
1.  <span data-ttu-id="1ff9a-137">開啟命令提示字元並執行*\<範例路徑 >*\BAM\BAMFromExpression\Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-137">Open a command prompt and run *\<Samples Path>*\BAM\BAMFromExpression\Setup.bat.</span></span> <span data-ttu-id="1ff9a-138">如果您使用[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，開啟命令提示字元，以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-138">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.</span></span> <span data-ttu-id="1ff9a-139">Setup.bat 會初始化此範例中，BAM 基礎結構，並將部署 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-139">Setup.bat initializes the BAM infrastructure for this sample, and deploys the BAM activity.</span></span>  
  
2.  <span data-ttu-id="1ff9a-140">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **追蹤設定檔編輯器**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-140">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span> <span data-ttu-id="1ff9a-141">如果您使用[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，以滑鼠右鍵按一下**追蹤設定檔編輯器**，然後按一下 **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-141">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], right-click **Tracking Profile Editor** and then click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="1ff9a-142">在左窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡匯入 BAM 活動定義**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-142">In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.</span></span>  
  
4.  <span data-ttu-id="1ff9a-143">在**BAM 活動定義名稱**區段**匯入 BAM 活動定義**對話方塊中，選取**FromExpressionPo**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="1ff9a-143">In the **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **FromExpressionPo**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="1ff9a-144">在右窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡選取事件來源**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-144">In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.</span></span>  
  
6.  <span data-ttu-id="1ff9a-145">在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamFromExpression**，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-145">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamFromExpression**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="1ff9a-146">在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamFromExpression.Orchestration1**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="1ff9a-146">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamFromExpression.Orchestration1**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="1ff9a-147">以滑鼠右鍵按一下**Receive_1**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-147">Right-click the **Receive_1** shape, and then click **Message Payload Schema**.</span></span>  
  
9. <span data-ttu-id="1ff9a-148">展開**\<結構描述 >**，依序展開**PurchaseOrder**，依序展開**從**，然後將拖曳**PoID** 右窗格中**ActivityID**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-148">Expand **\<Schema>**, expand **PurchaseOrder**, expand **From**, and then drag **PoID** in the right pane to **ActivityID** in the left pane.</span></span>  
  
10. <span data-ttu-id="1ff9a-149">從右窗格中，將下列項目，並將它們放置到左窗格中的具名節點：</span><span class="sxs-lookup"><span data-stu-id="1ff9a-149">Drag the following elements from the right pane, and drop them onto the named nodes in the left pane:</span></span>  
  
    |<span data-ttu-id="1ff9a-150">來源</span><span class="sxs-lookup"><span data-stu-id="1ff9a-150">From</span></span>|<span data-ttu-id="1ff9a-151">若要</span><span class="sxs-lookup"><span data-stu-id="1ff9a-151">To</span></span>|  
    |----------|--------|  
    |<span data-ttu-id="1ff9a-152">名稱</span><span class="sxs-lookup"><span data-stu-id="1ff9a-152">Name</span></span>|<span data-ttu-id="1ff9a-153">來源</span><span class="sxs-lookup"><span data-stu-id="1ff9a-153">From</span></span>|  
    |<span data-ttu-id="1ff9a-154">State</span><span class="sxs-lookup"><span data-stu-id="1ff9a-154">State</span></span>|<span data-ttu-id="1ff9a-155">State</span><span class="sxs-lookup"><span data-stu-id="1ff9a-155">State</span></span>|  
    |<span data-ttu-id="1ff9a-156">City</span><span class="sxs-lookup"><span data-stu-id="1ff9a-156">City</span></span>|<span data-ttu-id="1ff9a-157">City</span><span class="sxs-lookup"><span data-stu-id="1ff9a-157">City</span></span>|  
    |<span data-ttu-id="1ff9a-158">Phone</span><span class="sxs-lookup"><span data-stu-id="1ff9a-158">Phone</span></span>|<span data-ttu-id="1ff9a-159">Phone</span><span class="sxs-lookup"><span data-stu-id="1ff9a-159">Phone</span></span>|  
    |<span data-ttu-id="1ff9a-160">Total</span><span class="sxs-lookup"><span data-stu-id="1ff9a-160">Total</span></span>|<span data-ttu-id="1ff9a-161">PoTotal</span><span class="sxs-lookup"><span data-stu-id="1ff9a-161">PoTotal</span></span>|  
  
11. <span data-ttu-id="1ff9a-162">按一下資料夾圖示的箭號 (![資料夾和向上按鈕 &#45; 箭號](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 以顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-162">Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) to display the orchestration.</span></span>  
  
12. <span data-ttu-id="1ff9a-163">拖曳**Receive_1**右窗格中的圖形**Received**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-163">Drag the **Receive_1** shape in the right pane to **Received** in the left pane.</span></span>  
  
13. <span data-ttu-id="1ff9a-164">拖曳**[send_1]**右窗格中的圖形**傳送**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-164">Drag the **Send_1** shape in the right pane to **Send** in the left pane.</span></span>  
  
14. <span data-ttu-id="1ff9a-165">儲存追蹤設定檔來*\<範例路徑 >*\BAM\BamFromExpression\ BamFromExpression.btt。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-165">Save the tracking profile to *\<Samples Path>*\BAM\BamFromExpression\ BamFromExpression.btt.</span></span>  
  
15. <span data-ttu-id="1ff9a-166">在**工具**功能表上，按一下 **套用追蹤設定檔**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-166">On the **Tools** menu, click **Apply Tracking Profile**.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="1ff9a-167">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="1ff9a-167">To build and initialize this sample</span></span>  
  
-   <span data-ttu-id="1ff9a-168">部署追蹤設定檔 BamFromExpression.btt。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-168">Deploy the BamFromExpression.btt tracking profile.</span></span> <span data-ttu-id="1ff9a-169">如需詳細資訊，請參閱[如何使用 「 追蹤設定檔管理公用程式部署追蹤設定檔](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-169">For more information, see [How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="1ff9a-170">執行此範例</span><span class="sxs-lookup"><span data-stu-id="1ff9a-170">To run this sample</span></span>  
  
-   <span data-ttu-id="1ff9a-171">將檔案複製*\<範例路徑 >*至 \BamFromExpression\InputMessage.xml *\<範例路徑 >*\BamFromExpression\Input。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-171">Copy the file *\<Samples Path>*\BamFromExpression\InputMessage.xml to *\<Samples Path>*\BamFromExpression\Input.</span></span>  
  
     <span data-ttu-id="1ff9a-172">在 10 秒內的輸出訊息會出現在*\<範例路徑 >*\BamFromExpression\Output。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-172">In about 10 seconds the output message will appear in *\<Samples Path>*\BamFromExpression\Output.</span></span>  
  
#### <a name="to-view-the-bam-data"></a><span data-ttu-id="1ff9a-173">若要檢視 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="1ff9a-173">To view the BAM data</span></span>  
  
1.  <span data-ttu-id="1ff9a-174">開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-174">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="1ff9a-175">在 SQL Server Management Studio，展開伺服器，展開 **資料庫**，依序展開**BAMPrimaryImport**，然後展開**資料表**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-175">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="1ff9a-176">以滑鼠右鍵按一下**dbo.bam_fromexpressionpo_completed**，然後按一下 **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-176">Right-click **dbo.bam_FromExpressionPo_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="1ff9a-177">如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，按一下 **選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-177">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="1ff9a-178">bam_FromExpressionPo_Completed 資料表的內容會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-178">The contents of the bam_FromExpressionPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="1ff9a-179">有一個資料列 (活動識別碼為 123) 代表輸入訊息中所含價值 $345 的訂單。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-179">The one row, which has an activity ID of 123, represents the purchase order for $345 that was contained in the input message.</span></span>  
  
4.  <span data-ttu-id="1ff9a-180">以滑鼠右鍵按一下**dbo.bam_FromExpressionPoItem_Completed**，然後按一下 **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-180">Right-click **dbo.bam_FromExpressionPoItem_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="1ff9a-181">如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，按一下 **選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-181">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="1ff9a-182">Bam_FromExpressionPoItem_Completed 資料表的內容會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-182">The contents of the bam_FromExpressionPoItem_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="1ff9a-183">兩個資料列有活動識別碼 123_0 和 123_1，代表訂單中的項目： Flash MC 和紅外線解碼器。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-183">The two rows, which have activity IDs 123_0 and 123_1, represent the items in the purchase order: Flash MC and Infrared Decoder.</span></span>  
  
5.  <span data-ttu-id="1ff9a-184">以滑鼠右鍵按一下**dbo.bam_FromExpressionPoItem_CompletedRelationships**，然後按一下 **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-184">Right-click **dbo.bam_FromExpressionPoItem_CompletedRelationships**, and then click **Open Table**.</span></span> <span data-ttu-id="1ff9a-185">如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，按一下 **選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-185">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="1ff9a-186">Bam_FromExpressionPoItem_CompletedRelationships 資料表的內容會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-186">The contents of the bam_FromExpressionPoItem_CompletedRelationships table are displayed in the right pane.</span></span> <span data-ttu-id="1ff9a-187">資料表中的每個資料列都代表 FromExpressionPoItem 活動 FromExpressionPo 活動之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-187">Each row in the table represents a relationship between a FromExpressionPoItem activity and a FromExpressionPo activity.</span></span> <span data-ttu-id="1ff9a-188">中的值**ActivityID** FromExpressionPoItem 活動的活動識別碼的參考資料行。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-188">The value in the **ActivityID** column refers to the activity ID of the FromExpressionPoItem activity.</span></span> <span data-ttu-id="1ff9a-189">中的值**ReferenceData** FromExpressionPo 活動的活動識別碼的參考資料行。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-189">The value in the **ReferenceData** column refers to the activity ID of the FromExpressionPo activity.</span></span> <span data-ttu-id="1ff9a-190">在此情況下，兩個記錄會指出快閃 MC 和紅外線解碼器的項目相關聯價值 $345 的訂單。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-190">In this case, the two records indicate that the Flash MC and Infrared Decoder items are associated with the purchase order for $345.</span></span>  
  
#### <a name="to-re-run-the-sample"></a><span data-ttu-id="1ff9a-191">若要重新執行範例</span><span class="sxs-lookup"><span data-stu-id="1ff9a-191">To re-run the sample</span></span>  
  
1.  <span data-ttu-id="1ff9a-192">開啟命令提示字元並執行*\<範例路徑 >*\BAM\BamFromExpression\Cleanup.bat 移除追蹤設定檔和其他 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-192">Open a command prompt and run *\<Samples Path>*\BAM\BamFromExpression\Cleanup.bat to remove the tracking profile and other BAM infrastructure.</span></span> <span data-ttu-id="1ff9a-193">如果您使用[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，開啟命令提示字元，以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-193">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.</span></span>  
  
2.  <span data-ttu-id="1ff9a-194">執行*\<範例路徑 >*\BAM\BamFromExpression\Setup.bat 編譯範例，並將它部署。</span><span class="sxs-lookup"><span data-stu-id="1ff9a-194">Run *\<Samples Path>*\BAM\BamFromExpression\Setup.bat to compile the sample and deploy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff9a-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff9a-195">See Also</span></span>  
 <span data-ttu-id="1ff9a-196">[商務活動監控 （BizTalk Server 範例資料夾）](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="1ff9a-196">[Business Activity Monitoring (BizTalk Server Samples Folder)](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="1ff9a-197">活動關係</span><span class="sxs-lookup"><span data-stu-id="1ff9a-197">Activity Relationships</span></span>](../core/activity-relationships.md)