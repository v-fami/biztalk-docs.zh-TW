---
title: 商務規則 Hello World2 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: 2a88a2a0-8cb6-4373-8441-0ab04345a477
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ccc78579c9febfa93b489d72c40ccb603bed92a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972807"
---
# <a name="business-rules-hello-world2-biztalk-server-sample"></a><span data-ttu-id="9151c-102">商務規則 Hello World2 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="9151c-102">Business Rules Hello World2 (BizTalk Server Sample)</span></span>
<span data-ttu-id="9151c-103">商務規則 Hello World2 範例擴充 「 商務規則 Hello world1 」 範例示範如何版本、 發佈和部署 XML 規則集至共用的 SQL 規則存放區，以及如何執行原則使用**原則**物件「 商務規則架構所提供。</span><span class="sxs-lookup"><span data-stu-id="9151c-103">The Business Rules Hello World2 sample extends the Business Rules Hello World1 sample by demonstrating how to version, publish, and deploy the XML rule set to the shared SQL rule store, and how to run the policy using the **Policy** object provided by the Business Rules Framework.</span></span> <span data-ttu-id="9151c-104">這個範例還會示範動態原則更新的實際操作。</span><span class="sxs-lookup"><span data-stu-id="9151c-104">The sample also demonstrates dynamic policy updates in action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9151c-105">這個範例假設使用者在安裝產品期間一併安裝了「規則引擎更新服務」和「商務規則元件」(位於 [其他軟體] 節點下)。</span><span class="sxs-lookup"><span data-stu-id="9151c-105">This sample assumes that the user has installed the Rule Engine Update Service and Business Rules Components (located under the "Additional Software" node) during installation of the product.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9151c-106">您使用**原則**物件至規則引擎整合至任何獨立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9151c-106">You use **Policy** objects to integrate the rule engine into any stand-alone application.</span></span> <span data-ttu-id="9151c-107">**原則**物件是多個規則引擎執行個體所管理的抽象概念，規則集合是擷取，並且從共用 SQL 存放區中，具現化，以及原則更新已擷取並發佈裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="9151c-107">The **Policy** object is the abstraction through which multiple rule engine instances are managed, rule sets are retrieved and instantiated from the shared SQL store, and updates to the policies are retrieved and published to the hosting application.</span></span>  
  
 <span data-ttu-id="9151c-108">此範例中，所建構的事實如需詳細的規則集定義，且範例的基本資訊[商務規則 Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="9151c-108">For basic information about the rule set defined, and sample facts constructed by this sample, see [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="9151c-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="9151c-109">What This Sample Does</span></span>  
 <span data-ttu-id="9151c-110">這個範例會建立可執行檔，用來執行下面的一系列步驟：</span><span class="sxs-lookup"><span data-stu-id="9151c-110">This sample creates an executable that performs the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="9151c-111">呼叫方法**CreateRuleset**建置的規則集所述的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="9151c-111">Calls the method **CreateRuleset** to build the rule set described in the Remarks section.</span></span>  
  
2.  <span data-ttu-id="9151c-112">呼叫方法**SaveToFile**示範儲存規則集至檔案。</span><span class="sxs-lookup"><span data-stu-id="9151c-112">Calls the method **SaveToFile** to demonstrate saving a rule set to a file.</span></span>  
  
3.  <span data-ttu-id="9151c-113">呼叫方法**LoadFromFile**示範載入設定檔中的規則。</span><span class="sxs-lookup"><span data-stu-id="9151c-113">Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.</span></span>  
  
4.  <span data-ttu-id="9151c-114">將規則集部署至共用 SQL 規則存放區。</span><span class="sxs-lookup"><span data-stu-id="9151c-114">Deploys the rule set to a shared SQL rule store.</span></span>  
  
5.  <span data-ttu-id="9151c-115">執行規則集利用**原則**物件，並使用同一組事實範例商務規則 Hello world1 」 範例。</span><span class="sxs-lookup"><span data-stu-id="9151c-115">Runs the rule set by using a **Policy** object, and by using the same set of sample facts used in the Business Rules Hello World1 sample.</span></span>  
  
6.  <span data-ttu-id="9151c-116">暫停，讓您修改規則集檔案**SampleRuleStore.xml**以特定方式。</span><span class="sxs-lookup"><span data-stu-id="9151c-116">Pauses, enabling you to modify the rule set file **SampleRuleStore.xml** in a specific way.</span></span>  
  
7.  <span data-ttu-id="9151c-117">執行規則集使用再次**原則**物件，現在已修改的規則集，並再次使用同一組事實範例商務規則 Hello world1 」 範例。</span><span class="sxs-lookup"><span data-stu-id="9151c-117">Runs the rule set again using a **Policy** object, the now modified rule set, and again with the same set of sample facts used in the Business Rules Hello World1 sample.</span></span>  
  
8.  <span data-ttu-id="9151c-118">透過刪除規則集檔案和部署的規則集記錄進行清除，準備接著執行範例。</span><span class="sxs-lookup"><span data-stu-id="9151c-118">Cleans up by deleting the rule set file and the deployed rule set records in preparation for subsequent running of the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9151c-119">如需此 SDK 中的所有範例的重要資訊，請參閱[範例](../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="9151c-119">For important information about all samples in this SDK, see [Samples](../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="9151c-120">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="9151c-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="9151c-121">*\<範例路徑\>* \Business Rules\Business 規則 Hello World2\\</span><span class="sxs-lookup"><span data-stu-id="9151c-121">*\<Samples Path\>* \Business Rules\Business Rules Hello World2\\</span></span>  
  
 <span data-ttu-id="9151c-122">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="9151c-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="9151c-123">檔案</span><span class="sxs-lookup"><span data-stu-id="9151c-123">File(s)</span></span>|<span data-ttu-id="9151c-124">描述</span><span class="sxs-lookup"><span data-stu-id="9151c-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9151c-125">App.ico、AssemblyInfo.cs、BusinessRulesHelloWorld2.csproj、BusinessRulesHelloWorld2.sln</span><span class="sxs-lookup"><span data-stu-id="9151c-125">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld2.csproj, BusinessRulesHelloWorld2.sln</span></span>|<span data-ttu-id="9151c-126">這個範例所屬的專案、解決方案和相關檔案，可建立、儲存、載入、部署和執行規則集。</span><span class="sxs-lookup"><span data-stu-id="9151c-126">Project, solution, and related files for the portion of this sample that creates, saves, loads, deploys, and executes a rule set.</span></span>|  
|<span data-ttu-id="9151c-127">HelloWorld2.cs</span><span class="sxs-lookup"><span data-stu-id="9151c-127">HelloWorld2.cs</span></span>|<span data-ttu-id="9151c-128">Visual C# 檔，其中包含方法，示範如何建立規則設定、 儲存規則集至檔案，載入規則集檔案，將規則集部署至共用的 Microsoft SQL Server 規則存放區，以及再執行規則集使用**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="9151c-128">Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, loading a rule set from a file, deploying the rule set to a shared Microsoft SQL Server rule store, and then running the rule set by using a **Policy** object.</span></span>|  
|<span data-ttu-id="9151c-129">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="9151c-129">Cleanup.bat</span></span>|<span data-ttu-id="9151c-130">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="9151c-130">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="9151c-131">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9151c-131">Removes send and receive ports.</span></span> <span data-ttu-id="9151c-132">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="9151c-132">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="9151c-133">SampleDocumentInstance.xml</span><span class="sxs-lookup"><span data-stu-id="9151c-133">SampleDocumentInstance.xml</span></span>|<span data-ttu-id="9151c-134">範例輸入檔，與 SampleSchema.xsd 檔中定義的結構描述相符。</span><span class="sxs-lookup"><span data-stu-id="9151c-134">Sample input file that conforms to the schema defined in the file SampleSchema.xsd.</span></span>|  
|<span data-ttu-id="9151c-135">SampleSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="9151c-135">SampleSchema.xsd</span></span>|<span data-ttu-id="9151c-136">結構描述檔，定義簡單的結構描述，其中某個元素會由 Visual C# 檔 Class1.cs 中的規則集參照。</span><span class="sxs-lookup"><span data-stu-id="9151c-136">Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file Class1.cs.</span></span>|  
|<span data-ttu-id="9151c-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="9151c-137">Setup.bat</span></span>|<span data-ttu-id="9151c-138">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="9151c-138">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="9151c-139">在 \HelloWorld2Library 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9151c-139">In the \HelloWorld2Library folder:</span></span><br /><br /> <span data-ttu-id="9151c-140">AssemblyInfo.cs、HelloWorld2Library.csproj、HelloWorld2Library.sln</span><span class="sxs-lookup"><span data-stu-id="9151c-140">AssemblyInfo.cs, HelloWorld2Library.csproj, HelloWorld2Library.sln</span></span>|<span data-ttu-id="9151c-141">這個範例所屬的專案、解決方案和相關檔案，其提供定義所建立規則集參照之物件的類別。</span><span class="sxs-lookup"><span data-stu-id="9151c-141">Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.</span></span>|  
|<span data-ttu-id="9151c-142">在 \HelloWorld2Library 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9151c-142">In the \HelloWorld2Library folder:</span></span><br /><br /> <span data-ttu-id="9151c-143">HelloWorld2LibraryClass.cs</span><span class="sxs-lookup"><span data-stu-id="9151c-143">HelloWorld2LibraryClass.cs</span></span>|<span data-ttu-id="9151c-144">Visual C# 檔，其中包含在所參考之屬性**IF**一部分所建立的規則，並可能在呼叫的方法**然後**部分建立的規則。</span><span class="sxs-lookup"><span data-stu-id="9151c-144">Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.</span></span>|  
  
### <a name="to-build-and-initialize-the-business-rules-hello-world2-sample"></a><span data-ttu-id="9151c-145">建置和初始化商務規則 Hello World2 範例</span><span class="sxs-lookup"><span data-stu-id="9151c-145">To build and initialize the Business Rules Hello World2 sample</span></span>  
  
1. <span data-ttu-id="9151c-146">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9151c-146">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="9151c-147">*\<範例路徑\>* \Business Rules\Business 規則 Hello World2\\</span><span class="sxs-lookup"><span data-stu-id="9151c-147">*\<Samples Path\>* \Business Rules\Business Rules Hello World2\\</span></span>  
  
2. <span data-ttu-id="9151c-148">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9151c-148">Run the file Setup.bat, which performs the following actions:</span></span>  
  
   - <span data-ttu-id="9151c-149">為這個範例編譯和部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="9151c-149">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9151c-150">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9151c-150">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="9151c-151">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9151c-151">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="9151c-152">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="9151c-152">Use this key pair to sign the resulting assemblies.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="9151c-153">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="9151c-153">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="9151c-154">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="9151c-154">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
### <a name="to-run-the-business-rules-hello-world2-sample"></a><span data-ttu-id="9151c-155">執行商務規則 Hello World2 範例</span><span class="sxs-lookup"><span data-stu-id="9151c-155">To run the Business Rules Hello World2 sample</span></span>  
  
1.  <span data-ttu-id="9151c-156">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9151c-156">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="9151c-157">*\<範例路徑\>* \Business Rules\Business 規則 Hello World2\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="9151c-157">*\<Samples Path\>* \Business Rules\Business Rules Hello World2\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="9151c-158">在 [命令] 視窗中，輸入此範例的檔案名稱 (**BusinessRulesHelloWorld2.exe**)，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9151c-158">In the command window, type the name of the file for this sample (**BusinessRulesHelloWorld2.exe**), and then press ENTER.</span></span>  
  
## <a name="hello-world2-output"></a><span data-ttu-id="9151c-159">Hello World2 輸出</span><span class="sxs-lookup"><span data-stu-id="9151c-159">Hello World2 Output</span></span>  
 <span data-ttu-id="9151c-160">根據建立的規則集，註解區段中所述的本質[商務規則 Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md)，如果您使用提供的範例輸入檔 SampleDocumentInstance.xml，定義的值為一 (1) 執行此範例針對其**識別碼**項目，您會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9151c-160">Based on the nature of the created rule set, described in the Comments section of [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md), if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Deploying the ruleset ...  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...  
Grabbing the policy ...  
Executing the policy...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
The major version of the policy was: 1  
The minor version of the policy was: 0  
Press the ENTER to continue after updating the policy...  
```  
  
> [!NOTE]
>  <span data-ttu-id="9151c-161">以粗體顯示的輸出是由範例商務物件，定義中的檔案所產生的輸出**HelloWorld2Library**規則集參照的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9151c-161">The output shown in bold is the output produced by the sample business object, defined by the files in the **HelloWorld2Library** folder that the rule set references.</span></span> <span data-ttu-id="9151c-162">此時，應用程式會進入這個狀態並等待。</span><span class="sxs-lookup"><span data-stu-id="9151c-162">At this point, the application is left waiting in this state.</span></span>  
  
 <span data-ttu-id="9151c-163">執行範例的下一個部分包括使用 [商務規則編輯器] 變更商務規則。</span><span class="sxs-lookup"><span data-stu-id="9151c-163">The next part of running the sample involves using the Business Rules Composer to change the business rules.</span></span>  
  
#### <a name="to-use-the-business-rules-composer-to-change-the-business-rules"></a><span data-ttu-id="9151c-164">使用商務規則編輯器變更商務規則</span><span class="sxs-lookup"><span data-stu-id="9151c-164">To use the Business Rules Composer to change the business rules</span></span>  
  
1. <span data-ttu-id="9151c-165">若要開啟 商務規則編輯器，請按一下**開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則編輯器**。</span><span class="sxs-lookup"><span data-stu-id="9151c-165">To open the Business Rules Composer, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Composer**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9151c-166">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="9151c-166">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="9151c-167">若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="9151c-167">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2. <span data-ttu-id="9151c-168">如果 SQL Server 對話方塊隨即出現在執行 SQL Server 的電腦上，按一下**確定**連接至規則存放區。</span><span class="sxs-lookup"><span data-stu-id="9151c-168">If a SQL Server dialog box appears on the computer running SQL Server, click **OK** to connect to the rule store.</span></span>  
  
3. <span data-ttu-id="9151c-169">在**原則總管**下面的**sampleruleset**節點，以滑鼠右鍵按一下節點**1.0 版 – 已部署**，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="9151c-169">In **Policy Explorer**, below the **SampleRuleSet** node, right-click the node **Version 1.0 – Deployed**, and then click **Copy**.</span></span>  
  
4. <span data-ttu-id="9151c-170">以滑鼠右鍵按一下 **[sampleruleset]**，然後按一下**貼上 （原則版本）**。</span><span class="sxs-lookup"><span data-stu-id="9151c-170">Right-click **SampleRuleSet**, and then click **Paste (Policy Version)**.</span></span>  
  
5. <span data-ttu-id="9151c-171">您可以視需要變更規則條件和動作。</span><span class="sxs-lookup"><span data-stu-id="9151c-171">You can change the rule condition and action to meet your needs.</span></span> <span data-ttu-id="9151c-172">此程序中，按一下**rule1**中**版本 1.1 （未儲存）**。</span><span class="sxs-lookup"><span data-stu-id="9151c-172">For this procedure, click **rule1** in **Version 1.1 (not saved)**.</span></span> <span data-ttu-id="9151c-173">在右窗格中，以滑鼠右鍵按一下**條件**，然後按一下**新增邏輯 NOT**。</span><span class="sxs-lookup"><span data-stu-id="9151c-173">In the right pane, right-click **Conditions**, and then click **Add Logical NOT**.</span></span> <span data-ttu-id="9151c-174">新增**邏輯 NOT**欲**不等於**述詞，相當於使用**等於**述詞。</span><span class="sxs-lookup"><span data-stu-id="9151c-174">Adding a **Logical NOT** operation to **Not Equal** to predicate is equivalent to using an **Equal** predicate.</span></span>  
  
6. <span data-ttu-id="9151c-175">以滑鼠右鍵按一下節點**1.1 （未儲存） 版**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="9151c-175">Right-click the node **Version 1.1(not saved)**, and then click **Save**.</span></span> <span data-ttu-id="9151c-176">同樣地，按一下滑鼠右鍵，然後按一下**發佈**。</span><span class="sxs-lookup"><span data-stu-id="9151c-176">Right-click again, and then click **Publish**.</span></span> <span data-ttu-id="9151c-177">以滑鼠右鍵按一下第三次，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="9151c-177">Right-click a third time and click **Deploy**.</span></span>  
  
7. <span data-ttu-id="9151c-178">暫停的命令視窗會要求您在更新原則後按任意鍵繼續執行，請按任意鍵。</span><span class="sxs-lookup"><span data-stu-id="9151c-178">In the paused command window asking you to press any key to continue after updating the policy, press any key.</span></span>  
  
   <span data-ttu-id="9151c-179">從可執行檔 BusinessRulesHelloWorld2.exe 輸出 (假設您新增邏輯 Not 而變更規則) 的作業會繼續進行如下：</span><span class="sxs-lookup"><span data-stu-id="9151c-179">Output (assuming you changed the rule by adding a logical Not) from the executable file BusinessRulesHelloWorld2.exe continues as follows:</span></span>  
  
```  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...         
Grabbing the policy ...         
Executing the policy...         
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5         
The major version of the policy was: 1         
The minor version of the policy was: 1         
Press ENTER to continue after updating the policy...         
```  
  
 <span data-ttu-id="9151c-180">請注意輸出如何變更：</span><span class="sxs-lookup"><span data-stu-id="9151c-180">Notice how the output has changed:</span></span>  
  
-   <span data-ttu-id="9151c-181">此方法中的輸出行**MySampleMethod**只會列印一次就立即執行個體**MySampleBusinessObject**類別**MyValue**屬性等於 1而不是上一個規則，以列印時**MyValue**屬性不等於 1。</span><span class="sxs-lookup"><span data-stu-id="9151c-181">The output line in the method **MySampleMethod** only prints once now, for the instance of the **MySampleBusinessObject** class for which the **MyValue** property is equal to 1, rather than the previous rule of printing when the **MyValue** property is not equal to 1.</span></span>  
  
-   <span data-ttu-id="9151c-182">現在，原則的次要版本號碼為 1。</span><span class="sxs-lookup"><span data-stu-id="9151c-182">The minor version number of the policy is now 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9151c-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9151c-183">See Also</span></span>  
 [<span data-ttu-id="9151c-184">商務規則 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="9151c-184">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)