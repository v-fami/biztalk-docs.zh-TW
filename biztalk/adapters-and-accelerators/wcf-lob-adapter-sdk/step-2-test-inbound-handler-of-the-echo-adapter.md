---
title: "步驟 2： 測試輸入處理常式回應配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dede9b-6b7e-4901-9c79-b75bfee9155f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e17bcc987949b9ca25ac25db9a1789ebe980eb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-test-inbound-handler-of-the-echo-adapter"></a><span data-ttu-id="13e4b-102">步驟 2： 測試輸入的回應配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="13e4b-102">Step 2: Test Inbound Handler of the Echo Adapter</span></span>
<span data-ttu-id="13e4b-103">![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="13e4b-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="13e4b-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="13e4b-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="13e4b-105">在此步驟中，您會測試輸入的回應配接器所提供的服務。</span><span class="sxs-lookup"><span data-stu-id="13e4b-105">In this step, you test the inbound service provided by the Echo Adapter.</span></span> <span data-ttu-id="13e4b-106">您使用 Visual Studio 中，加入配接器服務參考 Visual Studio 外掛程式和自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="13e4b-106">You do this using Visual Studio, the Add Adapter Service Reference Visual Studio Plug-In and custom code.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13e4b-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="13e4b-107">Prerequisites</span></span>  
 <span data-ttu-id="13e4b-108">若要完成此步驟中，您必須先完成[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13e4b-108">To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="13e4b-109">獨立於完成這個步驟[步驟 1： 測試輸出回應配接器處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13e4b-109">This step can be completed independent of [Step 1: Test Outbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md).</span></span>  
  
## <a name="create-a-visual-studio-project"></a><span data-ttu-id="13e4b-110">建立 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="13e4b-110">Create a Visual Studio project</span></span>  
  
1.  <span data-ttu-id="13e4b-111">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="13e4b-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="13e4b-112">在 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-112">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="13e4b-113">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="13e4b-113">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="13e4b-114">使用</span><span class="sxs-lookup"><span data-stu-id="13e4b-114">Use this</span></span>|<span data-ttu-id="13e4b-115">動作</span><span class="sxs-lookup"><span data-stu-id="13e4b-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="13e4b-116">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="13e4b-116">**Project types**</span></span>|<span data-ttu-id="13e4b-117">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-117">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="13e4b-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="13e4b-118">**Templates**</span></span>|<span data-ttu-id="13e4b-119">按一下**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-119">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="13e4b-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="13e4b-120">**Name**</span></span>|<span data-ttu-id="13e4b-121">型別**ConsumeEchoAdapter_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-121">Type **ConsumeEchoAdapter_Inbound**.</span></span>|  
    |<span data-ttu-id="13e4b-122">**位置**</span><span class="sxs-lookup"><span data-stu-id="13e4b-122">**Location**</span></span>|<span data-ttu-id="13e4b-123">型別**C:\Tutorials**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-123">Type **C:\Tutorials**.</span></span>|  
    |<span data-ttu-id="13e4b-124">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="13e4b-124">**Solution Name**</span></span>|<span data-ttu-id="13e4b-125">型別**ConsumeEchoAdapter_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-125">Type **ConsumeEchoAdapter_Inbound**.</span></span>|  
  
4.  <span data-ttu-id="13e4b-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-126">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="13e4b-127">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-127">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="browse-search-and-generate-the-wcf-service"></a><span data-ttu-id="13e4b-128">瀏覽、 搜尋及產生 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="13e4b-128">Browse, search, and generate the WCF service</span></span>  
  
1.  <span data-ttu-id="13e4b-129">在 Visual Studio 方案 窗格中，以滑鼠右鍵按一下**ConsumeEchoAdapter_Inbound**專案，然後選擇 **新增配接器服務參考**以啟動 新增配接器服務參考外掛程式。</span><span class="sxs-lookup"><span data-stu-id="13e4b-129">In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Inbound** project then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.</span></span>  
  
2.  <span data-ttu-id="13e4b-130">在**新增配接器服務參考**畫面上，選擇繫結。</span><span class="sxs-lookup"><span data-stu-id="13e4b-130">In the **Add Adapter Service Reference** screen, choose a binding.</span></span> <span data-ttu-id="13e4b-131">這是藉由選擇**echoAdapterBindingV2**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-131">This is done by choosing **echoAdapterBindingV2**.</span></span>  
  
3.  <span data-ttu-id="13e4b-132">接下來，按一下設定的配接器和 connection 屬性**設定**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-132">Next, configure the adapter and connection properties by clicking **Configure**.</span></span>  <span data-ttu-id="13e4b-133">這會開啟**設定配接器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="13e4b-133">This opens the **Configure Adapter** screen.</span></span>  
  
4.  <span data-ttu-id="13e4b-134">在**設定配接器**畫面上，選取**繫結屬性**索引標籤以設定配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="13e4b-134">In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties.</span></span> <span data-ttu-id="13e4b-135">請注意，自訂回應配接器類別**輸入**和**其他**列示如下。</span><span class="sxs-lookup"><span data-stu-id="13e4b-135">Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown.</span></span> <span data-ttu-id="13e4b-136">在下**其他**分類中，按一下 [ **InboundFileSystemWatcherFolder** ]，然後輸入您想要監視的目錄。</span><span class="sxs-lookup"><span data-stu-id="13e4b-136">Under the **Misc** category, click **InboundFileSystemWatcherFolder** and then enter the directory you want to monitor.</span></span>  
  
5.  <span data-ttu-id="13e4b-137">按一下**確定**關閉**設定配接器**畫面上，並返回**新增配接器服務參考**螢幕。</span><span class="sxs-lookup"><span data-stu-id="13e4b-137">Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.</span></span>  
  
6.  <span data-ttu-id="13e4b-138">接下來，按一下**連接**連接到的回應配接器和 （假設它所支援的特定業務系統）。</span><span class="sxs-lookup"><span data-stu-id="13e4b-138">Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports).</span></span> <span data-ttu-id="13e4b-139">在幾分鐘之後, 的連接狀態應變**已連接**和類別目錄樹狀結構 (下**選取類別目錄**) 來擴展。</span><span class="sxs-lookup"><span data-stu-id="13e4b-139">After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.</span></span>  
  
7.  <span data-ttu-id="13e4b-140">若要檢視可用的輸入的操作，請變更**服務合約型別**至**服務 （輸入操作）**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-140">To view available inbound operations, change the **Service contract type** to **Service (Inbound operations)**.</span></span>  
  
8.  <span data-ttu-id="13e4b-141">在 類別目錄樹狀結構中，按一下 **主要類別**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-141">In the Category Tree, click **Main Category**.</span></span> <span data-ttu-id="13e4b-142">這會填入可用的類別和單一輸入作業的作業清單。</span><span class="sxs-lookup"><span data-stu-id="13e4b-142">This populates the list of available categories and operations with a single inbound operation.</span></span> <span data-ttu-id="13e4b-143">不有任何類別。</span><span class="sxs-lookup"><span data-stu-id="13e4b-143">There are no categories.</span></span>  
  
9. <span data-ttu-id="13e4b-144">在**可用的類別和作業**，選取**OnReceiveEcho**作業。</span><span class="sxs-lookup"><span data-stu-id="13e4b-144">In the **Available Categories and Operations**, select the **OnReceiveEcho** operation.</span></span> <span data-ttu-id="13e4b-145">按一下**新增**讓產生的 WCF 介面中選取的作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="13e4b-145">Click **Add** to make the selected operations part of the generated WCF interface.</span></span>  
  
10. <span data-ttu-id="13e4b-146">按一下**確定**產生 WCF 介面。</span><span class="sxs-lookup"><span data-stu-id="13e4b-146">Click **OK** to generate the WCF interface.</span></span> <span data-ttu-id="13e4b-147">這會將應用程式組態檔 (app.config)、 WCF 介面 (EchoAdapterBindingInterface.cs) 和 WCF 服務 (EchoAdapterBindingService.cs) 加入專案。</span><span class="sxs-lookup"><span data-stu-id="13e4b-147">This adds an application configuration file (app.config), a WCF interface (EchoAdapterBindingInterface.cs) and a WCF service (EchoAdapterBindingService.cs) to the project.</span></span>  
  
11. <span data-ttu-id="13e4b-148">按一下**檔案**上**Visual Studio**功能表，然後選擇 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-148">Click **File** on the **Visual Studio** menu and choose **Save All**.</span></span>  
  
## <a name="test-the-echo-adapter"></a><span data-ttu-id="13e4b-149">測試回應配接器</span><span class="sxs-lookup"><span data-stu-id="13e4b-149">Test the Echo Adapter</span></span>  
  
1.  <span data-ttu-id="13e4b-150">在 [方案總管] 中，按兩下**EchoAdapterBindingService.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="13e4b-150">In Solution Explorer, double-click the **EchoAdapterBindingService.cs** file.</span></span>  
  
2.  <span data-ttu-id="13e4b-151">在 Visual Studio 編輯器中，內部**OnReceiveEcho**方法，以下列取代現有的實作：</span><span class="sxs-lookup"><span data-stu-id="13e4b-151">In the Visual Studio editor, inside the **OnReceiveEcho** method, replace the existing implementation with the following:</span></span>  
  
    ```csharp  
    System.Console.WriteLine("path = " + path + ", len = " + length);  
    ```  
  
3.  <span data-ttu-id="13e4b-152">在 [方案總管] 中，按兩下**Program.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="13e4b-152">In Solution Explorer, double-click the **Program.cs** file.</span></span>  
  
4.  <span data-ttu-id="13e4b-153">在 Visual Studio 編輯器中，在 Main 方法中，加入下列程式碼來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="13e4b-153">In the Visual Studio editor, inside the Main method, add the following code to host the WCF service.</span></span>  
  
    ```csharp  
    try  
    {  
        // Create a ServiceHost for the EchoServiceImpl type  
        // and use the base address from app.config  
        System.ServiceModel.ServiceHost host = new System.ServiceModel.ServiceHost(typeof(EchoAdapterBindingNamespace.EchoAdapterBindingService));  
  
        // Open the ServiceHost to start listening for messages  
        host.Open();  
  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost  
        host.Close();  
    }  
    catch (TimeoutException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    catch (System.ServiceModel.CommunicationException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    ```  
  
5.  <span data-ttu-id="13e4b-154">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="13e4b-154">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="13e4b-155">按 F5 啟動範例。</span><span class="sxs-lookup"><span data-stu-id="13e4b-155">Press F5 to start the sample.</span></span>  
  
7.  <span data-ttu-id="13e4b-156">"Txt"副檔名的檔案放入稍早在本教學課程中所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="13e4b-156">Drop a file with the "txt" extension into the directory specified earlier in this tutorial.</span></span> <span data-ttu-id="13e4b-157">您應該會看到類似下面的程式的 [輸出] 視窗中的資訊：</span><span class="sxs-lookup"><span data-stu-id="13e4b-157">You should see information similar to the following in the program output window:</span></span>  
  
     <span data-ttu-id="13e4b-158">**服務已就緒。**</span><span class="sxs-lookup"><span data-stu-id="13e4b-158">**The service is ready.**</span></span>  
  
     <span data-ttu-id="13e4b-159">**按\<ENTER\>終止服務。**</span><span class="sxs-lookup"><span data-stu-id="13e4b-159">**Press \<ENTER\> to terminate service.**</span></span>  
  
     <span data-ttu-id="13e4b-160">**路徑 = file:///C:/Tutorial/InboundTest/InboundTest.txt，len = 229179**</span><span class="sxs-lookup"><span data-stu-id="13e4b-160">**path = file:///C:/Tutorial/InboundTest/InboundTest.txt, len = 229179**</span></span>  
  
8.  <span data-ttu-id="13e4b-161">按下 Enter 鍵停止服務。</span><span class="sxs-lookup"><span data-stu-id="13e4b-161">Press the Enter key to stop the service.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="13e4b-162">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="13e4b-162">What Did I Just Do?</span></span>  
 <span data-ttu-id="13e4b-163">在此步驟中，建立測試應用程式開發中的回應配接器所公開的輸入的操作[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13e4b-163">In this step, you created a test application for the inbound operation exposed by the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="13e4b-164">若要這樣做，您可以建立 Visual Studio 專案、 產生 WCF 服務，以及提供裝載 WCF 服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="13e4b-164">To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service.</span></span> <span data-ttu-id="13e4b-165">最後，您已執行測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="13e4b-165">Finally, you ran the test application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="13e4b-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="13e4b-166">Next Steps</span></span>  
 <span data-ttu-id="13e4b-167">這是本教學課程的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="13e4b-167">This is the last step of the tutorial.</span></span> <span data-ttu-id="13e4b-168">如需輸入作業的詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IInboundHandler`。</span><span class="sxs-lookup"><span data-stu-id="13e4b-168">For more information about Inbound operations, see `Microsoft.ServiceModel.Channels.Common.IInboundHandler`.</span></span> <span data-ttu-id="13e4b-169">若要查看範例示範如何裝載 WCF 服務需要驗證的 SDK，下載在回應配接器和測試程式碼[http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184)。</span><span class="sxs-lookup"><span data-stu-id="13e4b-169">To see an example SDK that demonstrates how to host a WCF Service that requires authentication, download the echo adapter and test code at [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e4b-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="13e4b-170">See Also</span></span>  
 <span data-ttu-id="13e4b-171">[教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span><span class="sxs-lookup"><span data-stu-id="13e4b-171">[Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span></span>  
 [<span data-ttu-id="13e4b-172">教學課程 1：開發 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="13e4b-172">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)