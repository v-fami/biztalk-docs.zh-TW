---
title: BAM API 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e181af5766231ed9a7d828b49e2d840a47f216c
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710449"
---
# <a name="bam-api-biztalk-server-sample"></a><span data-ttu-id="47830-102">BAM API (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="47830-102">BAM API (BizTalk Server Sample)</span></span>
<span data-ttu-id="47830-103">BAM API 範例示範如何將對 BAM API 的呼叫整合到應用程式，以儲存可供您監控的關鍵資訊。</span><span class="sxs-lookup"><span data-stu-id="47830-103">The BAM API sample illustrates how to incorporate calls to the BAM API into an application to save key information that you can monitor.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="47830-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="47830-104">What This Sample Does</span></span>  
 <span data-ttu-id="47830-105">此範例實作簡單的採購實例。</span><span class="sxs-lookup"><span data-stu-id="47830-105">This sample implements a simple purchasing scenario.</span></span> <span data-ttu-id="47830-106">它會產生訂單、處理每筆訂單、建立出貨、建立和處理發票。</span><span class="sxs-lookup"><span data-stu-id="47830-106">It generates purchase orders, processes each purchase order, creates shipments, and creates and processes invoices.</span></span> <span data-ttu-id="47830-107">隨著範例執行，它會建立與更新 BAM 活動，以反映訂單與發票的明細和處理狀況。</span><span class="sxs-lookup"><span data-stu-id="47830-107">As the sample runs, it creates and updates BAM activities to reflect the details and disposition of the purchase orders and invoices.</span></span>  
  
## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="47830-108">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="47830-108">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="47830-109">此範例旨在示範如何使用 BAM 來儲存來自非 BizTalk 協調流程之應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="47830-109">This sample was designed to illustrate how to use BAM to store information from an application that is not a BizTalk orchestration.</span></span> <span data-ttu-id="47830-110">雖然應用程式是簡易的應用程式，卻示範了在實際執行應用程式中可能會用到的 BAM 的數個層面。</span><span class="sxs-lookup"><span data-stu-id="47830-110">While the application is simple, it illustrates several aspects of BAM that you are likely to use in a production application.</span></span> <span data-ttu-id="47830-111">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="47830-111">These include the following:</span></span>  
  
-   <span data-ttu-id="47830-112">構成單一活動的多個執行緒</span><span class="sxs-lookup"><span data-stu-id="47830-112">Multiple threads that contribute to a single activity</span></span>  
  
-   <span data-ttu-id="47830-113">建立兩個活動之間的關係</span><span class="sxs-lookup"><span data-stu-id="47830-113">Creating a relationship between two activities</span></span>  
  
-   <span data-ttu-id="47830-114">使用接續以允許使用不同的 ID 存取相同的活動</span><span class="sxs-lookup"><span data-stu-id="47830-114">Using a continuation to allow the same activity to be accessed with different IDs</span></span>  
  
 <span data-ttu-id="47830-115">BAM API 範例包含三個主要類別︰ 一個用來處理採購訂單、 一個處理出貨，而另一個處理發票。</span><span class="sxs-lookup"><span data-stu-id="47830-115">The BAM API sample consists of three main classes: one to process purchase orders, one to process shipments, and one to process invoices.</span></span> <span data-ttu-id="47830-116">每個類別都 **RunOnce** 從佇列擷取訊息，然後再處理訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="47830-116">Each class has a **RunOnce** method that retrieves a message from a queue, and then processes the message.</span></span> <span data-ttu-id="47830-117">每個類別也有 **執行** 不斷呼叫的方法 **RunOnce** 方法。</span><span class="sxs-lookup"><span data-stu-id="47830-117">Each class also has a **Run** method that continually calls the **RunOnce** method.</span></span>  
  
 <span data-ttu-id="47830-118">**RunOnce** 方法 **PoApplication** 類別會進行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="47830-118">The **RunOnce** method of the **PoApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="47830-119">建立代表訂單的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="47830-119">Creates an XML message that represents a purchase order.</span></span>  
  
2.  <span data-ttu-id="47830-120">開始 BAMApiPo 活動，並將訂單和訂單收到時間相關資訊新增到活動。</span><span class="sxs-lookup"><span data-stu-id="47830-120">Begins a BAMApiPo activity and adds to the activity information about the purchase order and when it was received.</span></span>  
  
3.  <span data-ttu-id="47830-121">核准或拒絕訂單。</span><span class="sxs-lookup"><span data-stu-id="47830-121">Arbitrarily approves or rejects the purchase order.</span></span>  
  
4.  <span data-ttu-id="47830-122">更新 BAMApiPo 活動以記錄訂單狀態 (已接受或已拒絕)。</span><span class="sxs-lookup"><span data-stu-id="47830-122">Updates the BAMApiPo activity to record the status of the purchase order (accepted or rejected).</span></span>  
  
5.  <span data-ttu-id="47830-123">如果已接受訂單， **RunOnce** 方法也會進行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="47830-123">If the purchase order was accepted, the **RunOnce** method also does the following:</span></span>  
  
    1.  <span data-ttu-id="47830-124">建立代表要出貨之包裝的 XML 訊息，並將該訊息新增到出貨佇列。</span><span class="sxs-lookup"><span data-stu-id="47830-124">Creates an XML message to represent a package to be shipped, and adds the message to the queue of shipments.</span></span>  
  
    2.  <span data-ttu-id="47830-125">將代表訂單的 XML 訊息新增到訂單佇列，以包含在發票中。</span><span class="sxs-lookup"><span data-stu-id="47830-125">Adds the XML message that represents the purchase order to the queue of purchase orders to be included in an invoice.</span></span>  
  
    3.  <span data-ttu-id="47830-126">為 BAMApiPo 活動啟用接續。</span><span class="sxs-lookup"><span data-stu-id="47830-126">Enables continuation for the BAMApiPo activity.</span></span>  
  
    4.  <span data-ttu-id="47830-127">結束 BAMApiPo 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-127">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="47830-128">**RunOnce** 方法 **ShipmentApplication** 類別會進行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="47830-128">The **RunOnce** method of the **ShipmentApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="47830-129">從其佇列中擷取代表要出貨之包裝的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="47830-129">Retrieves from its queue an XML message that represents a package to be shipped.</span></span>  
  
2.  <span data-ttu-id="47830-130">更新 BAMApiPo 活動以記錄包裝出貨的時間。</span><span class="sxs-lookup"><span data-stu-id="47830-130">Updates the BAMApiPo activity to record the time that the package was shipped.</span></span>  
  
3.  <span data-ttu-id="47830-131">結束 BAMApiPo 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-131">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="47830-132">**RunOnce** 方法 **InvoiceApplication** 類別會進行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="47830-132">The **RunOnce** method of the **InvoiceApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="47830-133">從其佇列中擷取代表要開發票之訂單的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="47830-133">Retrieves from its queue an XML message that represents a purchase order to be invoiced.</span></span>  
  
2.  <span data-ttu-id="47830-134">開始 BAMApiInvoice 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-134">Begins a BAMApiInvoice activity.</span></span>  
  
3.  <span data-ttu-id="47830-135">為正在開發票的訂單建立 BAMApiInvoice 活動與 BAMApiPo 活動間的 BAM 關係。</span><span class="sxs-lookup"><span data-stu-id="47830-135">Creates a BAM relationship between the BAMApiInvoice activity and the BAMApiPo activity for the purchase order that is being invoiced.</span></span>  
  
4.  <span data-ttu-id="47830-136">將發票和發票建立時間相關資訊新增到 BAMApiPo 活動資訊。</span><span class="sxs-lookup"><span data-stu-id="47830-136">Adds to the BAMApiPo activity information about the invoice and the time it was created.</span></span>  
  
5.  <span data-ttu-id="47830-137">在模擬等候支付發票款項的一段延遲時間後，將支付發票款項的時間新增到 BAMApiInvoice 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-137">After an arbitrary delay to simulate waiting for the invoice to be paid, adds to the BAMApiInvoice activity the time the invoice was paid.</span></span>  
  
6.  <span data-ttu-id="47830-138">結束 BAMApiInvoice 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-138">Ends the BAMApiInvoice activity.</span></span>  
  
 <span data-ttu-id="47830-139">**Main** 方法 **MainApp** 類別初始化應用程式。</span><span class="sxs-lookup"><span data-stu-id="47830-139">The **Main** method of the **MainApp** class initializes the application.</span></span> <span data-ttu-id="47830-140">它會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="47830-140">It does the following:</span></span>  
  
1.  <span data-ttu-id="47830-141">建立 **DirectEventStream** 物件。</span><span class="sxs-lookup"><span data-stu-id="47830-141">Creates a **DirectEventStream** object.</span></span>  
  
2.  <span data-ttu-id="47830-142">啟動數個執行緒，並呼叫 **執行** 方法 **POApplication** 中每個執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="47830-142">Starts several threads, and calls the **Run** method of the **POApplication** object in each thread.</span></span>  
  
3.  <span data-ttu-id="47830-143">啟動數個執行緒，並呼叫 **執行** 方法 **ShipmentApplication** 中每個執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="47830-143">Starts several threads, and calls the **Run** method of the **ShipmentApplication** object in each thread.</span></span>  
  
4.  <span data-ttu-id="47830-144">啟動數個執行緒，並呼叫 **執行** 方法 **InvoiceApplication** 中每個執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="47830-144">Starts several threads, and calls the **Run** method of the **InvoiceApplication** object in each thread.</span></span>  
  
 <span data-ttu-id="47830-145">**Global** 類別會定義常數所使用的範例應用程式，例如要建立的執行緒數目和拒絕訂單的百分比。</span><span class="sxs-lookup"><span data-stu-id="47830-145">The **Global** class defines constants that are used by the sample application, such as the number of threads to create and the percentage of purchase orders to reject.</span></span>  
  
 <span data-ttu-id="47830-146">除了 Visual Studio 方案，此範例也包含定義活動的 Microsoft Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="47830-146">In addition to the Visual Studio solution, the sample also contains a Microsoft Excel file that defines the activities.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="47830-147">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="47830-147">Where to Find This Sample</span></span>  
 <span data-ttu-id="47830-148">您可以找到此範例位於*\<範例路徑\>* \BAM\BamApiSample。</span><span class="sxs-lookup"><span data-stu-id="47830-148">You can find this sample at *\<Samples Path\>* \BAM\BamApiSample.</span></span>  
  
 <span data-ttu-id="47830-149">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="47830-149">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="47830-150">檔案</span><span class="sxs-lookup"><span data-stu-id="47830-150">File</span></span>|<span data-ttu-id="47830-151">Description</span><span class="sxs-lookup"><span data-stu-id="47830-151">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="47830-152">BamApiSample.cs</span><span class="sxs-lookup"><span data-stu-id="47830-152">BamApiSample.cs</span></span>|<span data-ttu-id="47830-153">檢測的應用程式。</span><span class="sxs-lookup"><span data-stu-id="47830-153">Instrumented application.</span></span>|  
|<span data-ttu-id="47830-154">BamApiSample.csproj</span><span class="sxs-lookup"><span data-stu-id="47830-154">BamApiSample.csproj</span></span>|<span data-ttu-id="47830-155">檢測的應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="47830-155">Instrumented application project.</span></span>|  
|<span data-ttu-id="47830-156">BamApiSample.sln</span><span class="sxs-lookup"><span data-stu-id="47830-156">BamApiSample.sln</span></span>|<span data-ttu-id="47830-157">檢測的應用程式方案。</span><span class="sxs-lookup"><span data-stu-id="47830-157">Instrumented application solution.</span></span>|  
|<span data-ttu-id="47830-158">BamApiSample.xls</span><span class="sxs-lookup"><span data-stu-id="47830-158">BamApiSample.xls</span></span>|<span data-ttu-id="47830-159">BAM 定義樣式表。</span><span class="sxs-lookup"><span data-stu-id="47830-159">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="47830-160">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="47830-160">Cleanup.bat</span></span>|<span data-ttu-id="47830-161">移除所部署範例檔的批次檔。</span><span class="sxs-lookup"><span data-stu-id="47830-161">Batch file to remove deployed sample files.</span></span>|  
|<span data-ttu-id="47830-162">Input.txt</span><span class="sxs-lookup"><span data-stu-id="47830-162">Input.txt</span></span>|<span data-ttu-id="47830-163">範例攔截器組態輸入。</span><span class="sxs-lookup"><span data-stu-id="47830-163">Sample interceptor configuration input.</span></span>|  
|<span data-ttu-id="47830-164">InterceptorConfig.cs</span><span class="sxs-lookup"><span data-stu-id="47830-164">InterceptorConfig.cs</span></span>|<span data-ttu-id="47830-165">API 範例的攔截器組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="47830-165">Interceptor configuration code for API sample.</span></span>|  
|<span data-ttu-id="47830-166">InterceptorConfig.csproj</span><span class="sxs-lookup"><span data-stu-id="47830-166">InterceptorConfig.csproj</span></span>|<span data-ttu-id="47830-167">攔截器組態專案。</span><span class="sxs-lookup"><span data-stu-id="47830-167">Interceptor configuration project.</span></span>|  
|<span data-ttu-id="47830-168">Invoice_config.xml</span><span class="sxs-lookup"><span data-stu-id="47830-168">Invoice_config.xml</span></span>|<span data-ttu-id="47830-169">發票攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="47830-169">Invoice interceptor configuration.</span></span>|  
|<span data-ttu-id="47830-170">Invoice_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="47830-170">Invoice_interceptor.bin</span></span>|<span data-ttu-id="47830-171">序列化發票攔截器。</span><span class="sxs-lookup"><span data-stu-id="47830-171">Serialized invoice interceptor.</span></span>|  
|<span data-ttu-id="47830-172">PurchaseOrder_config.xml</span><span class="sxs-lookup"><span data-stu-id="47830-172">PurchaseOrder_config.xml</span></span>|<span data-ttu-id="47830-173">訂單攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="47830-173">PurchaseOrder interceptor configuration.</span></span>|  
|<span data-ttu-id="47830-174">PurchaseOrder_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="47830-174">PurchaseOrder_interceptor.bin</span></span>|<span data-ttu-id="47830-175">序列化訂單攔截器。</span><span class="sxs-lookup"><span data-stu-id="47830-175">Serialized PurchaseOrder interceptor.</span></span>|  
|<span data-ttu-id="47830-176">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="47830-176">Setup.bat</span></span>|<span data-ttu-id="47830-177">用來部署和登錄範例檔的批次檔。</span><span class="sxs-lookup"><span data-stu-id="47830-177">Batch file to deploy and enlist sample files.</span></span>|  
|<span data-ttu-id="47830-178">Shipment_config.xml</span><span class="sxs-lookup"><span data-stu-id="47830-178">Shipment_config.xml</span></span>|<span data-ttu-id="47830-179">出貨攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="47830-179">Shipment interceptor configuration.</span></span>|  
|<span data-ttu-id="47830-180">Shipment_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="47830-180">Shipment_interceptor.bin</span></span>|<span data-ttu-id="47830-181">已序列化的出貨攔截器。</span><span class="sxs-lookup"><span data-stu-id="47830-181">Serialized shipment interceptor.</span></span>|  
  
## <a name="run-the-bam-api-sample"></a><span data-ttu-id="47830-182">執行 BAM API 範例</span><span class="sxs-lookup"><span data-stu-id="47830-182">Run the BAM API sample</span></span>  
  
1.  <span data-ttu-id="47830-183">開啟命令提示字元，以系統管理員身分，並執行*\<範例路徑\>* \BAM\ BamApiSample\setup.bat。</span><span class="sxs-lookup"><span data-stu-id="47830-183">Open a command prompt as Administrator, and run *\<Samples Path\>* \BAM\ BamApiSample\setup.bat.</span></span>  
  
2.  <span data-ttu-id="47830-184">系統管理員身分啟動 Visual Studio，並開啟*\<範例路徑\>* BAMAPISAMPLE\BAMAPISAMPLE.SLN 方案。</span><span class="sxs-lookup"><span data-stu-id="47830-184">Start Visual Studio as Administrator, and open the *\<Samples Path\>* \BAM\ BamApiSample\BamApiSample.sln solution.</span></span> 
  
    > [!IMPORTANT]
    >  <span data-ttu-id="47830-185">必須在 BamApiSample.cs 檔案的 `//#define Interceptor` 該行前加上註解符號。請勿移除此行中的 “//”。</span><span class="sxs-lookup"><span data-stu-id="47830-185">The line `//#define Interceptor` in the BamApiSample.cs file must be commented out. Do not remove the “//” from this line.</span></span> <span data-ttu-id="47830-186">BAM API 範例僅使用不在 `#if Interceptor` 前置處理器指示詞內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47830-186">The BAM API sample uses only the code that is not inside an `#if Interceptor` preprocessor directive.</span></span>  
  
3.  <span data-ttu-id="47830-187">建置方案。</span><span class="sxs-lookup"><span data-stu-id="47830-187">Build the solution.</span></span>  
  
4.  <span data-ttu-id="47830-188">執行*\<範例路徑\>* \BAM\BamApiSample\bin\debug\BamApiSample.exe。</span><span class="sxs-lookup"><span data-stu-id="47830-188">Run *\<Samples Path\>* \BAM\BamApiSample\bin\debug\BamApiSample.exe.</span></span>  
  
     <span data-ttu-id="47830-189">輸出看起來會向下面這樣：</span><span class="sxs-lookup"><span data-stu-id="47830-189">The output will resemble the following:</span></span>  
  
    ```  
    ...  
    New Purchase Order #17 Received  
    8 was shipped as pkg#87  
    New Purchase Order #18 Received.  
    Shipping package pkg#87 via DHL  
    13 was Approved.  
    18 was Rejected.  
    17 was Rejected.  
    11 was shipped as pkg#114  
    16 wsas Rejected.  
    Shipping package pkg#114 via DHL  
    Invoice #5 send for {2 5 1 9 4 8 11 }  
    Package pkg#49 was delivered  
    New Purchase Order #19 Received.  
    ...  
    ```  
  
5.  <span data-ttu-id="47830-190">約 1 分鐘後，按下 CTRL+C 或關閉命令提示字元視窗以停止 BamApiSample 程式。</span><span class="sxs-lookup"><span data-stu-id="47830-190">After a minute or so, press CTRL+C or close the Command Prompt window to stop the BamApiSample program.</span></span>  
  
## <a name="view-the-results"></a><span data-ttu-id="47830-191">檢視結果</span><span class="sxs-lookup"><span data-stu-id="47830-191">View the results</span></span>
  
1.  <span data-ttu-id="47830-192">開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="47830-192">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="47830-193">在 SQL Server Management Studio 中，展開伺服器，展開 **資料庫**, ，依序展開 **BAMPrimaryImport**, ，然後展開 **資料表**。</span><span class="sxs-lookup"><span data-stu-id="47830-193">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="47830-194">以滑鼠右鍵按一下 **dbo.bam_BAMApiInvoice_Active** 然後按一下  **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="47830-194">Right-click **dbo.bam_BAMApiInvoice_Active** and then click **Open Table**.</span></span> <span data-ttu-id="47830-195">如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="47830-195">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="47830-196">bam_BAMApiInvoice_Active 資料表的內容會顯示於右窗格。</span><span class="sxs-lookup"><span data-stu-id="47830-196">The contents of the bam_BAMApiInvoice_Active table are displayed in the right pane.</span></span> <span data-ttu-id="47830-197">資料表中的每個資料列各代表一個已啟動但尚未完成的 BAMApiInvoice 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-197">Each row in the table represents a BAMApiInvoice activity that has been started, but  has not been completed.</span></span>  
  
4.  <span data-ttu-id="47830-198">以滑鼠右鍵按一下 **dbo.bam_BAMApiPo_Completed** 然後按一下  **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="47830-198">Right-click **dbo.bam_BAMApiPo_Completed** and then click **Open Table**.</span></span> <span data-ttu-id="47830-199">如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="47830-199">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="47830-200">bam_BAMApiPo_Completed 資料表的內容會顯示於右窗格。</span><span class="sxs-lookup"><span data-stu-id="47830-200">The contents of the bam_BAMApiPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="47830-201">資料表中的每個資料列各代表一個已完成的 BAMApiPo 活動。</span><span class="sxs-lookup"><span data-stu-id="47830-201">Each row in the table represents a BAMApiPo activity that has been completed.</span></span>