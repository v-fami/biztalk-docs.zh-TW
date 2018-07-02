---
title: 商務規則 Hello World1 （BizTalk Server 範例） |Microsoft Docs
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
ms.assetid: 0623ad20-96cc-430e-bb36-35431a5d17ee
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebf4afafeabeae8fa9dec0683bd344c40ce23da8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989999"
---
# <a name="business-rules-hello-world1-biztalk-server-sample"></a><span data-ttu-id="eaf4b-102">商務規則 Hello World1 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="eaf4b-102">Business Rules Hello World1 (BizTalk Server Sample)</span></span>
<span data-ttu-id="eaf4b-103">「商務規則 Hello World1」範例示範如何建立 BizTalk 規則集、將規則集儲存到檔案 (SampleRuleSet.xml)、載入規則集，以及依據一組事實範例執行該規則集。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-103">The Business Rules Hello World1 sample demonstrates how to create a BizTalk rule set, save it to a file (SampleRuleSet.xml), load it, and run it based on a sample set of facts.</span></span> <span data-ttu-id="eaf4b-104">範例規則集包含有關 XML 項目的簡單規則，以及做為規則定義內容的 .NET 物件 (屬性和成員)。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-104">The sample rule set contains a simple rule that involves an XML element, and .NET-based objects (properties and members) as terms in rule definition.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="eaf4b-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="eaf4b-105">What This Sample Does</span></span>  
 <span data-ttu-id="eaf4b-106">這個範例會建立可執行檔，用來執行下面的一系列步驟：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-106">This sample creates an executable that performs the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="eaf4b-107">呼叫方法**CreateRuleset**建置的規則集所述的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-107">Calls the method **CreateRuleset** to build the rule set described in the Remarks section.</span></span>  
  
2.  <span data-ttu-id="eaf4b-108">呼叫方法**SaveToFile**示範儲存規則集至檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-108">Calls the method **SaveToFile** to demonstrate saving a rule set to a file.</span></span>  
  
3.  <span data-ttu-id="eaf4b-109">呼叫方法**LoadFromFile**示範載入設定檔中的規則。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-109">Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.</span></span>  
  
4.  <span data-ttu-id="eaf4b-110">建構要執行規則集的範例事實。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-110">Constructs sample facts against which to run the rule set.</span></span>  
  
5.  <span data-ttu-id="eaf4b-111">針對範例事實執行規則集，產生螢幕輸出。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-111">Runs the rule set against the sample facts, producing screen output.</span></span>  
  
6.  <span data-ttu-id="eaf4b-112">暫停，讓您檢查規則集檔案 SampleRuleStore.xml。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-112">Pauses, enabling you to examine the rule set file SampleRuleStore.xml.</span></span>  
  
7.  <span data-ttu-id="eaf4b-113">透過刪除規則集檔案進行清除，準備接續的範例執行。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-113">Cleans up by deleting the rule set file in preparation for subsequent runs of the sample.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="eaf4b-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="eaf4b-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="eaf4b-115">\<*範例路徑*\>\Business Rules\Business 規則 Hello World1\\</span><span class="sxs-lookup"><span data-stu-id="eaf4b-115">\<*Samples Path*\>\Business Rules\Business Rules Hello World1\\</span></span>  
  
 <span data-ttu-id="eaf4b-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="eaf4b-117">檔案</span><span class="sxs-lookup"><span data-stu-id="eaf4b-117">File(s)</span></span>|<span data-ttu-id="eaf4b-118">描述</span><span class="sxs-lookup"><span data-stu-id="eaf4b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eaf4b-119">App.ico、AssemblyInfo.cs、BusinessRulesHelloWorld1.csproj、BusinessRulesHelloWorld1.sln</span><span class="sxs-lookup"><span data-stu-id="eaf4b-119">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld1.csproj, BusinessRulesHelloWorld1.sln</span></span>|<span data-ttu-id="eaf4b-120">這個範例所屬的專案、解決方案和相關檔案，可建立、儲存、載入和執行規則集。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-120">Project, solution, and related files for the portion of this sample that creates, saves, loads, and runs a rule set.</span></span>|  
|<span data-ttu-id="eaf4b-121">HelloWorld1.cs</span><span class="sxs-lookup"><span data-stu-id="eaf4b-121">HelloWorld1.cs</span></span>|<span data-ttu-id="eaf4b-122">Visual C# 檔案，其中包含的方法用於示範建立規則集、儲存規則集到檔案中，以及從檔案載入規則集。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-122">Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, and loading a rule set from a file.</span></span> <span data-ttu-id="eaf4b-123">另外也包含周圍程式碼，用於呼叫這些方法，然後再執行所建立的規則集。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-123">Also contains surrounding code that calls these methods and then runs the created rule set.</span></span>|  
|<span data-ttu-id="eaf4b-124">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="eaf4b-124">Cleanup.bat</span></span>|<span data-ttu-id="eaf4b-125">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-125">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="eaf4b-126">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-126">Removes send and receive ports.</span></span> <span data-ttu-id="eaf4b-127">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-127">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="eaf4b-128">SampleDocumentInstance.xml</span><span class="sxs-lookup"><span data-stu-id="eaf4b-128">SampleDocumentInstance.xml</span></span>|<span data-ttu-id="eaf4b-129">範例輸入檔，與 SampleSchema.xsd 檔中定義的結構描述相符。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-129">Sample input file that conforms to the schema defined in the file SampleSchema.xsd.</span></span>|  
|<span data-ttu-id="eaf4b-130">SampleSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="eaf4b-130">SampleSchema.xsd</span></span>|<span data-ttu-id="eaf4b-131">結構描述檔，定義簡單的結構描述，其中某個項目會由 Visual C# 檔 HelloWorld1.cs 中建立的規則集所參照。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-131">Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file HelloWorld1.cs.</span></span>|  
|<span data-ttu-id="eaf4b-132">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="eaf4b-132">Setup.bat</span></span>|<span data-ttu-id="eaf4b-133">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-133">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="eaf4b-134">在 \MySampleLibrary 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-134">In the \MySampleLibrary folder:</span></span><br /><br /> <span data-ttu-id="eaf4b-135">AssemblyInfo.cs、MySampleLibrary.csproj、MySampleLibrary.sln</span><span class="sxs-lookup"><span data-stu-id="eaf4b-135">AssemblyInfo.cs, MySampleLibrary.csproj, MySampleLibrary.sln</span></span>|<span data-ttu-id="eaf4b-136">這個範例所屬的專案、解決方案和相關檔案，其提供定義所建立規則集參照之物件的類別。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-136">Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.</span></span>|  
|<span data-ttu-id="eaf4b-137">在 \MySampleLibrary 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-137">In the \MySampleLibrary folder:</span></span><br /><br /> <span data-ttu-id="eaf4b-138">MySampleLibraryClass.cs</span><span class="sxs-lookup"><span data-stu-id="eaf4b-138">MySampleLibraryClass.cs</span></span>|<span data-ttu-id="eaf4b-139">Visual C# 檔，其中包含在所參考之屬性**IF**一部分所建立的規則，並可能在呼叫的方法**然後**部分建立的規則。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-139">Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="eaf4b-140">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="eaf4b-140">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="eaf4b-141">請使用下列程序，建置和初始化「商務規則 Hello World1」範例。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-141">Use the following procedure to build and initialize the Business Rules Hello World1 sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="eaf4b-142">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="eaf4b-142">To build and initialize this sample</span></span>  
  
1. <span data-ttu-id="eaf4b-143">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-143">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="eaf4b-144">\<*範例路徑*\>\Business Rules\Business 規則 Hello World1\\</span><span class="sxs-lookup"><span data-stu-id="eaf4b-144">\<*Samples Path*\>\Business Rules\Business Rules Hello World1\\</span></span>  
  
2. <span data-ttu-id="eaf4b-145">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-145">Run the file Setup.bat, which performs the following actions:</span></span>  
  
   - <span data-ttu-id="eaf4b-146">為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-146">Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="eaf4b-147">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-147">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="eaf4b-148">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-148">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="eaf4b-149">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-149">Use this key pair to sign the resulting assemblies.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="eaf4b-150">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-150">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="eaf4b-151">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-151">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="eaf4b-152">執行此範例</span><span class="sxs-lookup"><span data-stu-id="eaf4b-152">Running This Sample</span></span>  
 <span data-ttu-id="eaf4b-153">請使用下列程序，執行「商務規則 Hello World1」範例。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-153">Use the following procedure to run the Business Rules Hello World1 sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="eaf4b-154">執行此範例</span><span class="sxs-lookup"><span data-stu-id="eaf4b-154">To run this sample</span></span>  
  
1. <span data-ttu-id="eaf4b-155">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-155">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="eaf4b-156">\<*範例路徑*\>\Business Rules\Business 規則 Hello World1\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="eaf4b-156">\<*Samples Path*\>\Business Rules\Business Rules Hello World1\bin\Debug\\</span></span>  
  
2. <span data-ttu-id="eaf4b-157">在命令視窗中，輸入這個範例的可執行檔名稱 (BusinessRulesHelloWorld1.exe)，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-157">In the command window, type the name of the executable file for this sample (BusinessRulesHelloWorld1.exe), and then press ENTER.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="eaf4b-158">在執行時，規則集檔案 SampleRuleStore.xml 在此範例會產生**bin\Debug**資料夾。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-158">While running, this sample produces the rule set file SampleRuleStore.xml in the **bin\Debug** folder.</span></span> <span data-ttu-id="eaf4b-159">當可執行檔暫停時，是等候您按 ENTER 以完成作業，您可以檢查這個檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-159">When the executable pauses, waiting for you to press ENTER to finish, you can examine the contents of this file.</span></span> <span data-ttu-id="eaf4b-160">請記得先關閉檔案，再按下任何鍵完成作業。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-160">Remember to close it before pressing any key to finish.</span></span> <span data-ttu-id="eaf4b-161">否則，可執行檔可能無法刪除檔案，以準備接續的範例執行。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-161">Otherwise, the executable may not be able to delete it in preparation for subsequent runs of the sample.</span></span>  
  
   <span data-ttu-id="eaf4b-162">根據建立的規則集的本質，如果您執行這個範例使用提供的範例輸入檔 SampleDocumentInstance.xml，其值為一 (1) 定義其**識別碼**項目，您會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-162">Based on the nature of the created rule set, if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
> [!NOTE]
>  <span data-ttu-id="eaf4b-163">粗體，在上述程式碼和程式碼所示，輸出所產生的檔案中所定義的範例商務物件中所顯示的輸出**MySampleLibrary**規則集所參考的資料夾。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-163">The output shown in bold, both in the preceding code and in the code that follows, is the output produced by the sample business object, defined by the files in the **MySampleLibrary** folder, which is referenced by the rule set.</span></span>  
  
 <span data-ttu-id="eaf4b-164">如果您變更與相關聯的值**識別碼**範例輸入檔中的項目**SampleDocumentInstance.xml**從一 （1） 到二 （2），輸出會變更，如下所示：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-164">If you change the value associated with the **ID** element in the sample input file **SampleDocumentInstance.xml** from one (1) to two (2), the output would change as follows:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
 <span data-ttu-id="eaf4b-165">您不會收到輸出行的任何物件的**MySampleBusinessObject**類別具有其**MyValue**屬性設定為符合相關聯的值（建構期間）的值**識別碼**範例輸入檔 SampleDocumentInstance.xml 中的項目。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-165">You will not get an output line for any objects of the **MySampleBusinessObject** class that have their **MyValue** property set to a value (during construction) that matches the value associated with the **ID** element in the sample input file SampleDocumentInstance.xml.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="eaf4b-166">註解</span><span class="sxs-lookup"><span data-stu-id="eaf4b-166">Comments</span></span>  
 <span data-ttu-id="eaf4b-167">內以程式設計方式建立的規則**createruleset （)** 方法所示：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-167">The rule created programmatically within the **CreateRuleset()** method shows:</span></span>  
  
 <span data-ttu-id="eaf4b-168">**IF**</span><span class="sxs-lookup"><span data-stu-id="eaf4b-168">**IF**</span></span>  
  
 <span data-ttu-id="eaf4b-169">**MySampleBusinessObject.MyValue**不相等的值**識別碼**XML 文件中的項目。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-169">**MySampleBusinessObject.MyValue** is not equal to the value of the **ID** element in the XML document.</span></span>  
  
 <span data-ttu-id="eaf4b-170">**THEN**</span><span class="sxs-lookup"><span data-stu-id="eaf4b-170">**THEN**</span></span>  
  
 <span data-ttu-id="eaf4b-171">**Mysamplebusinessobject.mysamplemethod**整數參數，硬式編碼於常數五 （5） 在此情況下使用。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-171">**MySampleBusinessObject.MySampleMethod(int)** with an integer parameter, hard coded to the constant five (5) in this case.</span></span> <span data-ttu-id="eaf4b-172">這個方法會產生輸出行開頭**MySampleBusinessObject Class –-**。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-172">This method produces the output lines that begin **MySampleBusinessObject Class –-**.</span></span>  
  
 <span data-ttu-id="eaf4b-173">這個規則取決於下列項目：</span><span class="sxs-lookup"><span data-stu-id="eaf4b-173">This rule depends on the following:</span></span>  
  
- <span data-ttu-id="eaf4b-174">A **MySampleBusinessObject**類別的公用屬性，稱為**MyValue**和呼叫的公用方法**MySampleMethod** （會採用整數參數）。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-174">A **MySampleBusinessObject** class with a public property called **MyValue** and a public method called **MySampleMethod** (that takes in an integer parameter).</span></span>  
  
- <span data-ttu-id="eaf4b-175">XML 結構描述定義語言 (XSD) 結構描述定義 XML 文件，其中包含**識別碼**項目。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-175">An XML schema definition language (XSD) schema that defines an XML document that contains an **ID** element.</span></span>  
  
  <span data-ttu-id="eaf4b-176">您依據類別和結構描述定義規則，但在執行期間需要有相關類別的物件執行個體，以及相關結構描述的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-176">You define rules in terms of classes and schemas, but during execution, object instances of the relevant classes and document instances of the relevant schemas are required.</span></span> <span data-ttu-id="eaf4b-177">您要針對這些執行階段執行個體 (稱為事實) 評估規則。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-177">You evaluate the rules against these run-time instances (known as facts).</span></span> <span data-ttu-id="eaf4b-178">在此範例中，事實是多個執行個體**MySampleBusinessObject**包含不同的值所建構的物件及其**MyValue**屬性，而定義的結構描述的單一 XML 執行個體其中包含的值**識別碼**項目。</span><span class="sxs-lookup"><span data-stu-id="eaf4b-178">In this sample, the facts are multiple instances of the **MySampleBusinessObject** object, constructed with different values for their **MyValue** property, and a single XML instance of the defined schema that contains a value for the **ID** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf4b-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaf4b-179">See Also</span></span>  
 [<span data-ttu-id="eaf4b-180">商務規則 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="eaf4b-180">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)