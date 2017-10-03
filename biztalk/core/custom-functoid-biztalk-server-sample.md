---
title: "自訂運算質 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, customizing
- examples, functoids
- functoids, examples
- XML tools
- examples, XML tools
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5117bed6ea1116047052359eadcd11754e9f85d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-functoid-biztalk-server-sample"></a><span data-ttu-id="eb39a-102">自訂運算質 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="eb39a-102">Custom Functoid (BizTalk Server Sample)</span></span>
<span data-ttu-id="eb39a-103">「自訂運算質」範例示範如何為 BizTalk 對應工具撰寫自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="eb39a-103">The Custom Functoid sample demonstrates how to write a custom functoid for BizTalk Mapper.</span></span> <span data-ttu-id="eb39a-104">您可以新增至運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。</span><span class="sxs-lookup"><span data-stu-id="eb39a-104">You can add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span> <span data-ttu-id="eb39a-105">BizTalk 對應工具在焦點時，[工具箱] 中會顯示運算質。</span><span class="sxs-lookup"><span data-stu-id="eb39a-105">The functoid will be displayed in the Toolbox when BizTalk Mapper is in focus.</span></span>  
  
 <span data-ttu-id="eb39a-106">自訂運算質應該存在於 BizTalk 對應工具組件才能辨識它。</span><span class="sxs-lookup"><span data-stu-id="eb39a-106">A custom functoid should reside in a BizTalk Mapper assembly to recognize it.</span></span> <span data-ttu-id="eb39a-107">您可以用任何 .NET 相容的語言來撰寫自訂運算質，例如 C# 或 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="eb39a-107">It can be written in any .NET-compliant language, such as C# or Visual Basic.</span></span>  
  
 <span data-ttu-id="eb39a-108">另外，自訂運算質必須衍生自 `Microsoft.BizTalk.BaseFunctoids` 類別，而且它必須藉由覆寫某些方法來提供該些方法的實作</span><span class="sxs-lookup"><span data-stu-id="eb39a-108">Also, a custom functoid must derive from the `Microsoft.BizTalk.BaseFunctoids` class, and it must provide implementation for some methods by overriding them.</span></span> <span data-ttu-id="eb39a-109">(`BaseFunctoid` 類別定義於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所隨附的 Microsoft.BizTalk.BaseFunctoids.dll 組件中)。</span><span class="sxs-lookup"><span data-stu-id="eb39a-109">(The `BaseFunctoid` class is defined in the Microsoft.BizTalk.BaseFunctoids.dll assembly included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="eb39a-110">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="eb39a-110">What This Sample Does</span></span>  
 <span data-ttu-id="eb39a-111">「自訂運算質」範例實作數個運算質，每個都是衍生自 `BaseFunctoid` 類別而且覆寫數個方法。</span><span class="sxs-lookup"><span data-stu-id="eb39a-111">The Custom Functoid sample implements several functoids, each deriving from the `BaseFunctoid` class and overriding several methods.</span></span>  
  
 <span data-ttu-id="eb39a-112">實作自訂運算質時，您可以公開其內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb39a-112">When implementing a custom functoid, you can expose its code inline.</span></span> <span data-ttu-id="eb39a-113">內嵌程式碼會執行運算質的計算。</span><span class="sxs-lookup"><span data-stu-id="eb39a-113">The inline code is what performs the computation for the functoid.</span></span> <span data-ttu-id="eb39a-114">BizTalk 對應工具編譯器會從運算質擷取內嵌程式碼，再於建置專案時將它內嵌於編譯的 XSLT。</span><span class="sxs-lookup"><span data-stu-id="eb39a-114">The BizTalk Mapper compiler extracts inline code from a functoid and embeds it in the compiled XSLT when you build the project.</span></span>  
  
 <span data-ttu-id="eb39a-115">若自訂運算質未公開任何內嵌程式碼，BizTalk 對應工具會產生 XSLT (用來呼叫自訂運算質所在之組件)。</span><span class="sxs-lookup"><span data-stu-id="eb39a-115">If your custom functoid does not expose any inline code, BizTalk Mapper generates XSLT that calls into the assembly where the custom functoid resides.</span></span> <span data-ttu-id="eb39a-116">因此，您必須確定自訂運算質組件可在全域組件快取 (GAC) 中使用，這樣 XSLT 引擎才找得到它。</span><span class="sxs-lookup"><span data-stu-id="eb39a-116">In this case, you must be sure your custom functoid assembly is available in the global assembly cache (GAC) so the XSLT engine can find it.</span></span> <span data-ttu-id="eb39a-117">自訂運算質也必須具備唯一的 GUID 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb39a-117">A custom functoid must also have a unique GUID attribute.</span></span> <span data-ttu-id="eb39a-118">BizTalk 對應工具會使用 GUID 識別要載入的組件。</span><span class="sxs-lookup"><span data-stu-id="eb39a-118">BizTalk Mapper uses the GUID to identify which assembly to load.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb39a-119">若您重複使用「自訂運算質」範例程式碼實作自己的運算質，務必將 GUID 屬性變更為唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb39a-119">If you reuse the Custom Functoid sample code to implement your own functoid(s), you must be sure to change the GUID attribute to one that is unique.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="eb39a-120">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="eb39a-121">*\<範例路徑 >*\XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="eb39a-121">*\<Samples Path>*\XmlTools\CustomFunctoid</span></span>  
  
 <span data-ttu-id="eb39a-122">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="eb39a-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="eb39a-123">檔案</span><span class="sxs-lookup"><span data-stu-id="eb39a-123">File(s)</span></span>|<span data-ttu-id="eb39a-124">Description</span><span class="sxs-lookup"><span data-stu-id="eb39a-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb39a-125">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="eb39a-125">AssemblyInfo.cs</span></span>|<span data-ttu-id="eb39a-126">組件資訊 C# 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb39a-126">Assembly information C# source code.</span></span>|  
|<span data-ttu-id="eb39a-127">CBuildArray.bmp</span><span class="sxs-lookup"><span data-stu-id="eb39a-127">CBuildArray.bmp</span></span>|<span data-ttu-id="eb39a-128">工具箱點陣圖。</span><span class="sxs-lookup"><span data-stu-id="eb39a-128">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="eb39a-129">CConcat.bmp</span><span class="sxs-lookup"><span data-stu-id="eb39a-129">CConcat.bmp</span></span>|<span data-ttu-id="eb39a-130">工具箱點陣圖。</span><span class="sxs-lookup"><span data-stu-id="eb39a-130">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="eb39a-131">CExtractArray.bmp</span><span class="sxs-lookup"><span data-stu-id="eb39a-131">CExtractArray.bmp</span></span>|<span data-ttu-id="eb39a-132">工具箱點陣圖。</span><span class="sxs-lookup"><span data-stu-id="eb39a-132">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="eb39a-133">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="eb39a-133">Cleanup.bat</span></span>|<span data-ttu-id="eb39a-134">用來解除部署組件，將這些組件從全域組件快取 (GAC) 移除，並刪除 CustomFunctoid.dll。</span><span class="sxs-lookup"><span data-stu-id="eb39a-134">Used to undeploy assemblies and remove them from the global assembly cache (GAC) and to delete CustomFunctoid.dll.</span></span>|  
|<span data-ttu-id="eb39a-135">CLongestString.bmp</span><span class="sxs-lookup"><span data-stu-id="eb39a-135">CLongestString.bmp</span></span>|<span data-ttu-id="eb39a-136">工具箱點陣圖。</span><span class="sxs-lookup"><span data-stu-id="eb39a-136">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="eb39a-137">CMultiply.bmp</span><span class="sxs-lookup"><span data-stu-id="eb39a-137">CMultiply.bmp</span></span>|<span data-ttu-id="eb39a-138">工具箱點陣圖。</span><span class="sxs-lookup"><span data-stu-id="eb39a-138">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="eb39a-139">CustomFunctoid.cs</span><span class="sxs-lookup"><span data-stu-id="eb39a-139">CustomFunctoid.cs</span></span>|<span data-ttu-id="eb39a-140">自訂運算質 C# 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb39a-140">Custom functoid C# source code.</span></span>|  
|<span data-ttu-id="eb39a-141">CustomFunctoid.csproj</span><span class="sxs-lookup"><span data-stu-id="eb39a-141">CustomFunctoid.csproj</span></span>|<span data-ttu-id="eb39a-142">自訂運算質 C# 專案。</span><span class="sxs-lookup"><span data-stu-id="eb39a-142">Custom functoid C# project.</span></span>|  
|<span data-ttu-id="eb39a-143">CustomFunctoid.sln</span><span class="sxs-lookup"><span data-stu-id="eb39a-143">CustomFunctoid.sln</span></span>|<span data-ttu-id="eb39a-144">自訂運算質解決方案。</span><span class="sxs-lookup"><span data-stu-id="eb39a-144">Custom functoid solution.</span></span>|  
|<span data-ttu-id="eb39a-145">CustomFunctoidResources.resx</span><span class="sxs-lookup"><span data-stu-id="eb39a-145">CustomFunctoidResources.resx</span></span>|<span data-ttu-id="eb39a-146">自訂運算質資源。</span><span class="sxs-lookup"><span data-stu-id="eb39a-146">Custom functoid resources.</span></span>|  
|<span data-ttu-id="eb39a-147">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="eb39a-147">Setup.bat</span></span>|<span data-ttu-id="eb39a-148">用來建置、部署及啟動範例。</span><span class="sxs-lookup"><span data-stu-id="eb39a-148">Used to build, deploy, and start the sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="eb39a-149">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-149">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="eb39a-150">請使用下列程序來建置和初始化「自訂運算質」範例。</span><span class="sxs-lookup"><span data-stu-id="eb39a-150">Use the following procedure to build and initialize the Custom Functoid sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="eb39a-151">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-151">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="eb39a-152">在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="eb39a-152">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="eb39a-153">\<*範例路徑*> \XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="eb39a-153">\<*Samples Path*>\XmlTools\CustomFunctoid</span></span>  
  
2.  <span data-ttu-id="eb39a-154">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="eb39a-154">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="eb39a-155">建置範例專案。</span><span class="sxs-lookup"><span data-stu-id="eb39a-155">Builds the sample project.</span></span>  
  
    -   <span data-ttu-id="eb39a-156">將產生的組件複製至 Developer Tools\Mapper Extensions 目錄。</span><span class="sxs-lookup"><span data-stu-id="eb39a-156">Copies the generated assembly to the Developer Tools\Mapper Extensions directory.</span></span>  
  
    -   <span data-ttu-id="eb39a-157">將產生的組件加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="eb39a-157">Adds the generated assembly to the GAC.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eb39a-158">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="eb39a-158">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="eb39a-159">執行此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-159">Running This Sample</span></span>  
 <span data-ttu-id="eb39a-160">使用下列程序執行「自訂運算質」範例。</span><span class="sxs-lookup"><span data-stu-id="eb39a-160">Use the following procedure to run the Custom Functoid sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="eb39a-161">執行此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-161">To run this sample</span></span>  
  
1.  <span data-ttu-id="eb39a-162">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 **工具**功能表，然後選取**選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-162">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.</span></span>  
  
2.  <span data-ttu-id="eb39a-163">在**[選擇工具箱項目**對話方塊中，選取**BizTalk 對應工具運算質**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eb39a-163">In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.</span></span>  
  
3.  <span data-ttu-id="eb39a-164">按一下**重設**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-164">Click **Reset**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb39a-165">如果您的自訂運算質未公開任何內嵌程式碼，請確定可以在 GAC 中使用它的組件。</span><span class="sxs-lookup"><span data-stu-id="eb39a-165">If your custom functoid does not expose any inline code, make sure its assembly is made available in the GAC.</span></span>  
  
4.  <span data-ttu-id="eb39a-166">從**檔案**功能表上，選取**結束**關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb39a-166">From the **File** menu, select **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="eb39a-167">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-167">Start **Visual Studio Command Prompt**.</span></span>  
  
6.  <span data-ttu-id="eb39a-168">在命令提示字元中，輸入**devenv /setup**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-168">At the command prompt, type **devenv /setup**.</span></span>  
  
7.  <span data-ttu-id="eb39a-169">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-169">Start **Microsoft Visual Studio**.</span></span>  
  
     <span data-ttu-id="eb39a-170">自訂運算質 （自訂串連運算質，最長字串、 組建陣列運算質，並擷取陣列運算質） 會出現在**字串運算質**工具箱和 「 累計乘法 」 運算質索引標籤會出現在**累計運算質** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eb39a-170">The custom functoids (Custom concatenate functoid, Longest String, Build array functoid, and Extract array functoid) appear on the **String Functoids** tab of the Toolbox, and the Cumulative Multiply functoid appears on the **Cumulative Functoids** tab.</span></span>  
  
## <a name="removing-this-sample"></a><span data-ttu-id="eb39a-171">移除此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-171">Removing This Sample</span></span>  
 <span data-ttu-id="eb39a-172">使用下列程序移除「自訂運算質」範例。</span><span class="sxs-lookup"><span data-stu-id="eb39a-172">Use the following procedure to remove the Custom Functoid sample.</span></span>  
  
#### <a name="to-remove-this-sample"></a><span data-ttu-id="eb39a-173">若要移除此範例</span><span class="sxs-lookup"><span data-stu-id="eb39a-173">To remove this sample</span></span>  
  
1.  <span data-ttu-id="eb39a-174">移除從運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。</span><span class="sxs-lookup"><span data-stu-id="eb39a-174">Remove the functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="eb39a-175">在執行 Cleanup.bat 之後，如果您仍然在工具箱中看到過時的自訂運算質 (可能是因為 Visual Studio 在內部進行快取)，請遵循下列程序：</span><span class="sxs-lookup"><span data-stu-id="eb39a-175">If after running Cleanup.bat, you still see the stale custom functoids in the toolbox (probably due to internal caching by Visual Studio), then follow the procedures below:</span></span>  
  
    1.  <span data-ttu-id="eb39a-176">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 **工具**功能表，然後選取**選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-176">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="eb39a-177">在**[選擇工具箱項目**對話方塊中，選取**BizTalk 對應工具運算質**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eb39a-177">In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.</span></span>  
  
    3.  <span data-ttu-id="eb39a-178">在清單中尋找自訂運算質 （自訂串連運算質、 最長字串、 組建陣列運算質、 擷取陣列 」 運算質和累計乘法）。</span><span class="sxs-lookup"><span data-stu-id="eb39a-178">Find the custom functoids (Custom concatenate functoid, Longest String, Build array functoid, Extract array functoid, and Cumulative Multiply) in the list.</span></span> <span data-ttu-id="eb39a-179">按一下對應**核取方塊**以移除運算質，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-179">Click the respective **check box** to remove the functoids, and then click **OK**.</span></span>  
  
     <span data-ttu-id="eb39a-180">如果上述程序無法解決問題，請遵循下列程序。</span><span class="sxs-lookup"><span data-stu-id="eb39a-180">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="eb39a-181">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [**工具箱**時編輯對應以顯示工具箱工具板] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eb39a-181">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab while editing a map to bring up the Toolbox Palette.</span></span>  
  
    2.  <span data-ttu-id="eb39a-182">以滑鼠右鍵按一下工具箱中，選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-182">Right-click the tool box and select **Choose Items**.</span></span>  
  
    3.  <span data-ttu-id="eb39a-183">在 選擇項目 對話方塊中，按一下 **重設**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-183">In the Choose Items dialog box, click **Reset**, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="eb39a-184">關閉所有執行個體[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb39a-184">Close all instances of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
     <span data-ttu-id="eb39a-185">如果上述程序無法解決問題，請遵循下列程序。</span><span class="sxs-lookup"><span data-stu-id="eb39a-185">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="eb39a-186">啟動**Visual Studio 命令提示字元**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="eb39a-186">Start **Visual Studio Command Prompt** as an administrator.</span></span>  
  
    2.  <span data-ttu-id="eb39a-187">關閉所有執行中的 Visual Studio 執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb39a-187">Close all the running instances of Visual Studio.</span></span>  
  
    3.  <span data-ttu-id="eb39a-188">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="eb39a-188">Give the following commands:</span></span>  
  
         `devenv /resetsettings`  
  
         `devenv /setup`  
  
    4.  <span data-ttu-id="eb39a-189">您可以從工具箱中手動選取不想要的運算質。</span><span class="sxs-lookup"><span data-stu-id="eb39a-189">You can manually select the unwanted functoids from the toolbox.</span></span> <span data-ttu-id="eb39a-190">以滑鼠右鍵按一下運算質，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="eb39a-190">Then, right click the functoid, and click **Delete**.</span></span>  
  
     <span data-ttu-id="eb39a-191">如果上述程序無法解決問題，請遵循下列程序。</span><span class="sxs-lookup"><span data-stu-id="eb39a-191">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="eb39a-192">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [工具箱] 索引標籤編輯對應以顯示工具箱工具板時。</span><span class="sxs-lookup"><span data-stu-id="eb39a-192">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the Toolbox tab while editing a map to bring up the Toolbox Palette.</span></span>  
  
    2.  <span data-ttu-id="eb39a-193">按一下**累計運算質**群組。</span><span class="sxs-lookup"><span data-stu-id="eb39a-193">Click the **Cumulative Functoids** group.</span></span>  
  
    3.  <span data-ttu-id="eb39a-194">以滑鼠右鍵按一下您想要移除，然後選擇 運算的質**刪除**或按下 delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="eb39a-194">Right click the functoid you want to remove and then choose **Delete** or press the delete key.</span></span>  
  
    4.  <span data-ttu-id="eb39a-195">按一下**字串運算質**群組。</span><span class="sxs-lookup"><span data-stu-id="eb39a-195">Click the **String Functoids** group.</span></span>  
  
    5.  <span data-ttu-id="eb39a-196">以滑鼠右鍵按一下您想要移除，然後選擇 運算的質**刪除**或按下 delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="eb39a-196">Right click the functoid you want to remove and then choose **Delete** or press the delete key.</span></span>  
  
2.  <span data-ttu-id="eb39a-197">在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="eb39a-197">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="eb39a-198">\<*範例路徑*> \XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="eb39a-198">\<*Samples Path*>\XmlTools\CustomFunctoid</span></span>  
  
3.  <span data-ttu-id="eb39a-199">執行 Cleanup.bat 檔案，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="eb39a-199">Run the file Cleanup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="eb39a-200">從 Developer Tools\Mapper Extensions 目錄刪除組件。</span><span class="sxs-lookup"><span data-stu-id="eb39a-200">Deletes the assembly from the Developer Tools\Mapper Extensions directory.</span></span>  
  
    -   <span data-ttu-id="eb39a-201">從 GAC 移除組件。</span><span class="sxs-lookup"><span data-stu-id="eb39a-201">Removes the assembly from the GAC.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="eb39a-202">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="eb39a-202">Classes or Methods Used in This Sample</span></span>  
 [<span data-ttu-id="eb39a-203">Microsoft.BizTalk.BaseFunctoids.BaseFunctoid</span><span class="sxs-lookup"><span data-stu-id="eb39a-203">Microsoft.BizTalk.BaseFunctoids.BaseFunctoid</span></span>](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="eb39a-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb39a-204">See Also</span></span>  
 <span data-ttu-id="eb39a-205">[使用 BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="eb39a-205">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 [<span data-ttu-id="eb39a-206">XML 工具 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="eb39a-206">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)