---
title: "步驟 1： 測試輸出回應配接器處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4a8164-a584-436f-b20b-4c884f6e2b37
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bf419a8ae3e6611f3d071cc94d274a5f2b0e00f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-test-outbound-handler-of-the-echo-adapter"></a><span data-ttu-id="8a7e9-102">步驟 1： 測試輸出回應配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="8a7e9-102">Step 1: Test Outbound Handler of the Echo Adapter</span></span>
<span data-ttu-id="8a7e9-103">![步驟 2 之 1](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span><span class="sxs-lookup"><span data-stu-id="8a7e9-103">![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span></span>  
  
 <span data-ttu-id="8a7e9-104">**完成時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="8a7e9-104">**Time to Complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="8a7e9-105">在此步驟中，您將測試回應配接器所提供的三個輸出作業。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-105">In this step, you will test the three outbound operations provided by the Echo Adapter.</span></span> <span data-ttu-id="8a7e9-106">您會執行此作業使用[!INCLUDE[vs2010](../../includes/vs2010-md.md)]，加入配接器服務參考 Visual Studio 外掛程式和自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-106">You will do this using [!INCLUDE[vs2010](../../includes/vs2010-md.md)], the Add Adapter Service Reference Visual Studio Plug-In and custom code.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a7e9-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a7e9-107">Prerequisites</span></span>  
 <span data-ttu-id="8a7e9-108">若要完成此步驟中，您必須先完成[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-108">To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
## <a name="create-a-visual-studio-project"></a><span data-ttu-id="8a7e9-109">建立 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="8a7e9-109">Create a Visual Studio project</span></span>  
  
1.  <span data-ttu-id="8a7e9-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8a7e9-111">在 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-111">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="8a7e9-112">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8a7e9-112">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8a7e9-113">使用</span><span class="sxs-lookup"><span data-stu-id="8a7e9-113">Use this</span></span>|<span data-ttu-id="8a7e9-114">動作</span><span class="sxs-lookup"><span data-stu-id="8a7e9-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8a7e9-115">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-115">**Project types**</span></span>|<span data-ttu-id="8a7e9-116">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-116">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="8a7e9-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-117">**Templates**</span></span>|<span data-ttu-id="8a7e9-118">按一下**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-118">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="8a7e9-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-119">**Name**</span></span>|<span data-ttu-id="8a7e9-120">型別**ConsumeEchoAdapter_Outbound**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-120">Type **ConsumeEchoAdapter_Outbound**.</span></span>|  
    |<span data-ttu-id="8a7e9-121">**位置**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-121">**Location**</span></span>|<span data-ttu-id="8a7e9-122">型別**C:\Tutorials**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-122">Type **C:\Tutorials**.</span></span>|  
    |<span data-ttu-id="8a7e9-123">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-123">**Solution Name**</span></span>|<span data-ttu-id="8a7e9-124">型別**ConsumeEchoAdapter_Outbound**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-124">Type **ConsumeEchoAdapter_Outbound**.</span></span>|  
  
4.  <span data-ttu-id="8a7e9-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="8a7e9-126">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-126">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="browse-search-and-generate-the-wcf-client"></a><span data-ttu-id="8a7e9-127">瀏覽、 搜尋及產生 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="8a7e9-127">Browse, search, and generate the WCF client</span></span>  
  
1.  <span data-ttu-id="8a7e9-128">在 Visual Studio 方案 窗格中，以滑鼠右鍵按一下**ConsumeEchoAdapter_Outbound**專案，然後選擇 **新增配接器服務參考**以啟動 新增配接器服務參考外掛程式。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-128">In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Outbound** project, then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.</span></span>  
  
2.  <span data-ttu-id="8a7e9-129">在**新增配接器服務參考**畫面上，選擇繫結。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-129">In the **Add Adapter Service Reference** screen, choose a binding.</span></span> <span data-ttu-id="8a7e9-130">這是藉由選擇**echoAdapterBindingV2**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-130">This is done by choosing **echoAdapterBindingV2**.</span></span>  
  
3.  <span data-ttu-id="8a7e9-131">接下來，按一下設定的配接器和 connection 屬性**設定...**.</span><span class="sxs-lookup"><span data-stu-id="8a7e9-131">Next, configure the adapter and connection properties by clicking **Configure…**.</span></span>  <span data-ttu-id="8a7e9-132">這會顯示**設定配接器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-132">This will bring up the **Configure Adapter** screen.</span></span>  
  
4.  <span data-ttu-id="8a7e9-133">在**設定配接器**畫面上，選取**URI 屬性**索引標籤以設定連接屬性。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-133">In the **Configure Adapter** screen, select the **URI Properties** tab to configure connection properties.</span></span> <span data-ttu-id="8a7e9-134">請注意，會顯示自訂回應配接器類別目錄-**連接**和**格式**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-134">Notice that the custom Echo Adapter categories are shown — **Connection** and **Format**.</span></span> <span data-ttu-id="8a7e9-135">在下**格式**分類中，變更**EchoInUpperCase**至**True**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-135">Under the **Format** category, change **EchoInUpperCase** to **True**.</span></span>  
  
5.  <span data-ttu-id="8a7e9-136">在**設定配接器**畫面上，選取**繫結屬性**索引標籤以設定配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-136">In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties.</span></span> <span data-ttu-id="8a7e9-137">請注意，自訂回應配接器類別**輸入**和**其他**列示如下。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-137">Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown.</span></span> <span data-ttu-id="8a7e9-138">在下**其他**分類中，變更**計數**至**3**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-138">Under the **Misc** category, change **Count** to **3**.</span></span>  
  
6.  <span data-ttu-id="8a7e9-139">按一下**確定**關閉**設定配接器**畫面上，並返回**新增配接器服務參考**螢幕。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-139">Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.</span></span>  
  
7.  <span data-ttu-id="8a7e9-140">接下來，按一下**連接**連接到的回應配接器和 （假設它所支援的特定業務系統）。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-140">Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports).</span></span> <span data-ttu-id="8a7e9-141">在幾分鐘之後, 的連接狀態應變**已連接**和類別目錄樹狀結構 (下**選取類別目錄**) 來擴展。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-141">After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.</span></span>  
  
8.  <span data-ttu-id="8a7e9-142">在 類別目錄樹狀結構中，按一下 **主要類別**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-142">In the Category Tree, click **Main Category**.</span></span> <span data-ttu-id="8a7e9-143">這將會填入可用的類別目錄的清單包含三個輸出作業的作業。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-143">This will populate the list of available categories and operations with three outbound operations.</span></span> <span data-ttu-id="8a7e9-144">會有任何類別。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-144">There will be no categories.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a7e9-145">預設的合約型別是輸出。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-145">The default contract type is Outbound.</span></span> <span data-ttu-id="8a7e9-146">分類結果將會符合這個合約型別。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-146">Category results will match this contract type.</span></span>  
  
9. <span data-ttu-id="8a7e9-147">在**可用的類別和作業**，選取所有三項作業。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-147">In the **Available Categories and Operations**, select all three operations.</span></span> <span data-ttu-id="8a7e9-148">大量作業時，您可能會使用搜尋來縮小選取範圍。在此情況下，是只有三個。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-148">When there are a large number of operations, you might use search to narrow down the selection; in this case, there are only three.</span></span> <span data-ttu-id="8a7e9-149">按一下**新增**讓產生的 WCF 介面中選取的作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-149">Click **Add** to make the selected operations part of the generated WCF interface.</span></span>  
  
10. <span data-ttu-id="8a7e9-150">按一下**確定**產生 WCF 介面。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-150">Click **OK** to generate the WCF interface.</span></span> <span data-ttu-id="8a7e9-151">這會將應用程式組態檔 (app.config) 和 WCF 用戶端 proxy (EchoAdapterBindingClient.cs) 加入專案。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-151">This will add an application configuration file (app.config) and a WCF client proxy (EchoAdapterBindingClient.cs) to the project.</span></span>  
  
11. <span data-ttu-id="8a7e9-152">按一下**檔案**Visual Studio 功能表上選擇 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-152">Click **File** on the Visual Studio menu and choose **Save All**.</span></span>  
  
## <a name="configure-adapter-authentication"></a><span data-ttu-id="8a7e9-153">設定配接器的驗證</span><span class="sxs-lookup"><span data-stu-id="8a7e9-153">Configure adapter authentication</span></span>  
  
1.  <span data-ttu-id="8a7e9-154">在 Visual Studio 方案 窗格中，按兩下**app.config**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-154">In Visual Studio Solution pane, double-click **app.config**.</span></span>  
  
2.  <span data-ttu-id="8a7e9-155">尋找`address`屬性`endpoint`項目。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-155">Find the `address` attribute in the `endpoint` element.</span></span> <span data-ttu-id="8a7e9-156">看起來應類似下列範例：</span><span class="sxs-lookup"><span data-stu-id="8a7e9-156">It should look similar to the following:</span></span>  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=False&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
     <span data-ttu-id="8a7e9-157">變更**enableAuthentication**從**False**至**True**如下所示。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-157">Change **enableAuthentication** from **False** to **True** as shown below.</span></span> <span data-ttu-id="8a7e9-158">這將需要將認證傳遞給配接器呼叫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-158">This will require the calling application to pass credentials to the adapter.</span></span>  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=True&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
3.  <span data-ttu-id="8a7e9-159">按一下以儲存方案**檔案**在 Visual Studio 功能表，選擇**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-159">Save the solution by clicking **File** on the Visual Studio menu and choosing **Save All**.</span></span>  
  
## <a name="create-a-sample-xml-file"></a><span data-ttu-id="8a7e9-160">建立範例 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8a7e9-160">Create a sample XML file</span></span>  
  
1.  <span data-ttu-id="8a7e9-161">啟動 [記事本] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-161">Start an instance of Notepad.</span></span> <span data-ttu-id="8a7e9-162">使用 開始 功能表中，按一下 **所有程式**&#124;**附屬應用程式**，然後選擇 **記事本**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-162">Using the Start menu, click **All Programs** &#124; **Accessories** and then choose **Notepad**.</span></span>  
  
2.  <span data-ttu-id="8a7e9-163">下列範例將資料複製到 [記事本] 編輯器。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-163">Copy the following sample data into the Notepad editor.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <ns0:greeting xmlns:ns0="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes">  
      <ns0:address>  
        <ns0:street1>123 Microsoft Way</ns0:street1>  
        <ns0:street2>Building # 4599</ns0:street2>  
        <ns0:city>Redmond</ns0:city>  
        <ns0:state>WA</ns0:state>  
        <ns0:zip>98052</ns0:zip>  
      </ns0:address>  
      <ns0:greetingText>Welcome to Redmond!</ns0:greetingText>  
    </ns0:greeting>              
    ```  
  
3.  <span data-ttu-id="8a7e9-164">在 記事本 功能表中，按一下 **檔案**，然後選擇 **另存新檔...**.</span><span class="sxs-lookup"><span data-stu-id="8a7e9-164">On the Notepad menu, click **File** and then choose **Save As…**.</span></span> <span data-ttu-id="8a7e9-165">輸入"CustomGreetingInstance.xml 」 中的檔案名稱並選擇 Unicode 的編碼方式，然後將它儲存到專案目錄或另一個的適當位置。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-165">Type in "CustomGreetingInstance.xml" for the file name and choose Unicode for the encoding and then save it to the project directory or another suitable location.</span></span> <span data-ttu-id="8a7e9-166">請注意的完整路徑和檔名，供日後參考。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-166">Note the full path and filename for later reference.</span></span>  
  
4.  <span data-ttu-id="8a7e9-167">已成功儲存檔案時，請關閉 [文字編輯器]。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-167">Close the text editor when the file is successfully saved.</span></span>  
  
## <a name="test-the-echo-adapter"></a><span data-ttu-id="8a7e9-168">測試回應配接器</span><span class="sxs-lookup"><span data-stu-id="8a7e9-168">Test the Echo Adapter</span></span>  
  
1.  <span data-ttu-id="8a7e9-169">在 [方案總管] 中，按兩下**Program.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-169">In Solution Explorer, double-click the **Program.cs** file.</span></span>  
  
2.  <span data-ttu-id="8a7e9-170">在 Visual Studio 編輯器中，內部**Main**方法，加入下列程式碼以便建立產生 WCF 用戶端的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-170">In the Visual Studio editor, inside the **Main** method, add the following line of code to create an instance of the generated WCF client.</span></span>  
  
    ```csharp  
    EchoOutboundContractClient client = new EchoOutboundContractClient();  
    ```  
  
3.  <span data-ttu-id="8a7e9-171">現在加入程式碼所建立的配接器的認證。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-171">Now add code that establishes credentials for the adapter.</span></span> <span data-ttu-id="8a7e9-172">驗證回應配接器中啟用時，它會檢查使用者名稱存在，但將不會檢查此值。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-172">When authentication is enabled in the Echo Adapter, it will check for the existence of a user name but will not check the value.</span></span>  
  
    ```csharp  
    // pass client credentials  
    client.ClientCredentials.UserName.UserName = "username";  
    ```  
  
4.  <span data-ttu-id="8a7e9-173">加入程式碼來叫用 EchoStrings 作業以繼續。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-173">Continue by adding code to invoke the EchoStrings operation.</span></span>  
  
    ```csharp  
    // Invoke EchoStrings()  
    Console.WriteLine("Invoking EchoStrings() method against the adapter...");  
    string[] response = client.EchoStrings("Bonjour!");  
    foreach (string data in response)  
    {  
        Console.WriteLine(data);  
    }  
    ```  
  
5.  <span data-ttu-id="8a7e9-174">加入程式碼來叫用 EchoGreetings 作業以繼續。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-174">Continue by adding code to invoke the EchoGreetings operation.</span></span>  
  
    ```csharp  
    // Invoke EchoGreetings()  
    Console.WriteLine("\nInvoking EchoGreetings() method against the adapter...");  
    microsoft.adapters.samples.echov2.Types.Greeting greeting = new microsoft.adapters.samples.echov2.Types.Greeting();  
    greeting.id = Guid.NewGuid();  
    greeting.sentDateTime = DateTime.Now;  
    greeting.greetingText = "Hello World!";  
    greeting.name = new microsoft.adapters.samples.echov2.Types.Name();  
    greeting.name.salutation = microsoft.adapters.samples.echov2.Types.Salutation.Miss;  
    greeting.name.firstName = "Jane";  
    greeting.name.middleName = "Z.";  
    greeting.name.lastName = "Smith";  
    microsoft.adapters.samples.echov2.Types.Greeting[] greetingArray = client.EchoGreetings(greeting);  
    foreach (microsoft.adapters.samples.echov2.Types.Greeting data in greetingArray)  
    {  
        Console.WriteLine(data.id + " " + data.sentDateTime + " " + data.greetingText + " " + data.name.firstName );  
    }  
    ```  
  
6.  <span data-ttu-id="8a7e9-175">加入程式碼來叫用 EchoCustomGreetingsFromFile 作業以繼續。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-175">Continue by adding code to invoke the EchoCustomGreetingsFromFile operation.</span></span>  
  
    ```csharp  
    // Invoke EchoCustomGreetingFromFile()  
    Console.WriteLine("\nInvoking EchoCustomGreetingFromFile() method against the adapter ...");  
    // Copy the sample data from CustomGreeting-instance.xml file and place in appropriate folder  
    // as specified in the operation parameter  
    microsoft.adapters.samples.echov2.PreDefinedTypes.CustomGreeting   
    // change the Uri to point to the greeting instance xml file you created  
    customGreeting = client.EchoCustomGreetingFromFile(new Uri(@"c:\CustomGreetingInstance.xml"));  
    Console.WriteLine(customGreeting.greetingText + " " + customGreeting.address.city);  
    client.Close();  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="8a7e9-176">EchoCustomGreetingsFromFile 中測試的程式碼，請確定自訂問候語會使用您在上一個程序中建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-176">In the EchoCustomGreetingsFromFile test code, make sure the custom greeting uses the file you created in a previous procedure.</span></span> <span data-ttu-id="8a7e9-177">變更以反映您的檔案位置的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-177">Change the code to reflect the location of your file.</span></span>  
  
8.  <span data-ttu-id="8a7e9-178">在[!INCLUDE[vs2010](../../includes/vs2010-md.md)]上**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-178">In [!INCLUDE[vs2010](../../includes/vs2010-md.md)], on the **File** menu, click **Save All**.</span></span>  
  
9. <span data-ttu-id="8a7e9-179">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-179">Run the application.</span></span> <span data-ttu-id="8a7e9-180">您應該會看到類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="8a7e9-180">You should see output similar to the following:</span></span>  
  
     <span data-ttu-id="8a7e9-181">**叫用配接器針對 EchoStrings() 方法...**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-181">**Invoking EchoStrings() method against the adapter...**</span></span>  
  
     <span data-ttu-id="8a7e9-182">**Bonjour ！**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-182">**Bonjour!**</span></span>  
  
     <span data-ttu-id="8a7e9-183">**Bonjour ！**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-183">**Bonjour!**</span></span>  
  
     <span data-ttu-id="8a7e9-184">**Bonjour ！**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-184">**Bonjour!**</span></span>  
  
     <span data-ttu-id="8a7e9-185">**Bonjour ！**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-185">**Bonjour!**</span></span>  
  
     <span data-ttu-id="8a7e9-186">**Bonjour ！**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-186">**Bonjour!**</span></span>  
  
     <span data-ttu-id="8a7e9-187">**叫用配接器針對 EchoGreetings() 方法...**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-187">**Invoking EchoGreetings() method against the adapter...**</span></span>  
  
     <span data-ttu-id="8a7e9-188">**179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-188">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="8a7e9-189">**179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-189">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="8a7e9-190">**179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-190">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="8a7e9-191">**179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-191">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="8a7e9-192">**179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-192">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="8a7e9-193">**叫用配接器針對 EchoCustomGreetingFromFile() 方法...**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-193">**Invoking EchoCustomGreetingFromFile() method against the adapter ...**</span></span>  
  
     <span data-ttu-id="8a7e9-194">**歡迎使用雷德蒙德 ！台北市**</span><span class="sxs-lookup"><span data-stu-id="8a7e9-194">**Welcome to Redmond! Redmond**</span></span>  
  
10. <span data-ttu-id="8a7e9-195">按下 Enter 鍵停止程式。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-195">Press the Enter key to stop the program.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8a7e9-196">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="8a7e9-196">What Did I Just Do?</span></span>  
 <span data-ttu-id="8a7e9-197">在此步驟中，您可以建立測試應用程式的回應配接器開發教學課程 1 中所公開的三個輸出作業。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-197">In this step, you created a test application for the three outbound operations exposed by the Echo Adapter developed in Tutorial 1.</span></span> <span data-ttu-id="8a7e9-198">若要這樣做，您可以建立 Visual Studio 專案、 產生 WCF 服務，以及提供裝載 WCF 服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-198">To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service.</span></span> <span data-ttu-id="8a7e9-199">最後，您已執行測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-199">Finally, you ran the test application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8a7e9-200">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8a7e9-200">Next Steps</span></span>  
 <span data-ttu-id="8a7e9-201">若要測試輸入的作業，繼續進行[步驟 2： 回應配接器的測試輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8a7e9-201">To test the Inbound operation, proceed to [Step 2: Test Inbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7e9-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a7e9-202">See Also</span></span>  
  <span data-ttu-id="8a7e9-203">[教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span><span class="sxs-lookup"><span data-stu-id="8a7e9-203">[Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span></span>  
 [<span data-ttu-id="8a7e9-204">步驟 2： 測試輸入的回應配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="8a7e9-204">Step 2: Test Inbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)