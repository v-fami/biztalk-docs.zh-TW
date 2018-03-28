---
title: 使用單元測試功能搭配管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d58bfa4-322b-455f-a062-5bd44d368f57
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca19a58410014b9ea7c0c49df7420b439a544581
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="using-the-unit-testing-feature-with-pipelines"></a><span data-ttu-id="a2ddd-102">使用單元測試功能搭配管線</span><span class="sxs-lookup"><span data-stu-id="a2ddd-102">Using the Unit Testing Feature with Pipelines</span></span>
<span data-ttu-id="a2ddd-103">此主題示範如何使用單元測試功能，以在 FlatFileReceive 管線範例中新增管線的單元測試。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-103">This topic demonstrates how to use the unit testing feature to add a unit test for the pipeline in the FlatFileReceive pipeline example.</span></span> <span data-ttu-id="a2ddd-104">管線單元測試會記載於此處的 Pipeline.exe 工具相似：[管線工具](../core/pipeline-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-104">Pipeline unit testing is similar to the Pipeline.exe tool that is documented here: [Pipeline Tools](../core/pipeline-tools.md).</span></span> <span data-ttu-id="a2ddd-105">當您啟用單元測試上 **部署** ] 索引標籤的 [專案屬性中，您的專案中的管線類別衍生自 **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-105">When you enable unit testing on the **Deployment** tab of the project properties, the pipeline class in your project is derived from **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**.</span></span>  <span data-ttu-id="a2ddd-106">此類別可做為 Pipeline.exe 工具所公開之一些相同功能的模型。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-106">This class models some of the same functionality exposed by the Pipeline.exe tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a2ddd-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="a2ddd-107">Prerequisites</span></span>  
 <span data-ttu-id="a2ddd-108">您必須先遵循建置 FlatFileReceive 範例的步驟進行，然後便可熟悉該範例。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-108">You must first follow the steps for building the FlatFileReceive sample and become familiar with that sample.</span></span> <span data-ttu-id="a2ddd-109">包含的步驟，用於建置 FlatFileReceive 範例可以在這裡找到的文件： [FlatFileReceive （BizTalk Server 範例）](../core/flatfilereceive-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-109">The documentation that includes the steps for building the FlatFileReceive sample can be found here: [FlatFileReceive (BizTalk Server Sample)](../core/flatfilereceive-biztalk-server-sample.md).</span></span>  
  
## <a name="adding-a-unit-test-project-to-the-flatfilereceive-sample"></a><span data-ttu-id="a2ddd-110">將單元測試專案新增至 FlatFileReceive 範例</span><span class="sxs-lookup"><span data-stu-id="a2ddd-110">Adding a Unit Test Project to the FlatFileReceive Sample</span></span>  
  
#### <a name="to-add-a-unit-test-project-to-the-flatfilereceive-sample"></a><span data-ttu-id="a2ddd-111">將單元測試專案新增至 FlatFileReceive 範例</span><span class="sxs-lookup"><span data-stu-id="a2ddd-111">To add a unit test project to the FlatFileReceive sample</span></span>  
  
1.  <span data-ttu-id="a2ddd-112">在 Visual Studio 中，開啟 FlatFileReceive.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-112">In Visual Studio, open the FlatFileReceive.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a2ddd-113">在 [方案總管] 中，以滑鼠右鍵按一下 **FlatFileReceive** 專案，然後再按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-113">In Solution Explorer, right-click the **FlatFileReceive** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a2ddd-114">在 專案設計工具中，按一下  **部署** 屬性頁面 索引標籤和組 **啟用單元測試** 到 `True`。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-114">In Project Designer, click the **Deployment** property page tab and set **Enable Unit Testing** to `True`.</span></span>  
  
4.  <span data-ttu-id="a2ddd-115">儲存所做的變更，關閉專案屬性頁。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-115">Close the project properties page saving the changes.</span></span>  
  
5.  <span data-ttu-id="a2ddd-116">在主功能表中，按一下  **建置**, ，然後按一下  **重建方案**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-116">On the main menu, click **Build**, and then click **Rebuild Solution**.</span></span>  
  
6.  <span data-ttu-id="a2ddd-117">在主功能表中，按一下  **測試**, ，然後按一下  **新測試**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-117">On the main menu, click **Test**, and then click **New Test**.</span></span>  
  
7.  <span data-ttu-id="a2ddd-118">在 **Add New Test** 對話方塊中，選取 **建立新的 Visual C# 測試專案** 的 **加入至測試專案** 欄位。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-118">In the **Add New Test** dialog box, select **Create a new Visual C# test project** for the **Add to Test Project** field.</span></span> <span data-ttu-id="a2ddd-119">選取 **Unit Test Wizard** 中 **範本** 清單，然後再按 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-119">Select **Unit Test Wizard** in the **Templates** list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="a2ddd-120">在 **新的測試專案** 對話方塊方塊中，保留專案名稱，做為 **TestProject1** 按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-120">In the **New Test Project** dialog box, leave the project name as **TestProject1** and click **Create**.</span></span>  
  
9. <span data-ttu-id="a2ddd-121">在 **建立單元測試**  對話方塊中，展開型別，然後選取 **FFReceivePipeline()** 建構函式在 **Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline** 節點。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-121">In the **Create Unit Tests** dialog box, expand the types and select the **FFReceivePipeline()** constructor under the **Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline** node.</span></span> <span data-ttu-id="a2ddd-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-122">Click **OK**.</span></span>  
  
## <a name="adding-test-code-to-test-the-pipeline"></a><span data-ttu-id="a2ddd-123">新增測試程式碼以測試管線</span><span class="sxs-lookup"><span data-stu-id="a2ddd-123">Adding Test Code to Test the Pipeline</span></span>  
  
#### <a name="to-add-test-code-to-test-the-pipeline"></a><span data-ttu-id="a2ddd-124">新增測試程式碼以測試管線</span><span class="sxs-lookup"><span data-stu-id="a2ddd-124">To add test code to test the pipeline</span></span>  
  
1.  <span data-ttu-id="a2ddd-125">將下列參考加入 **TestProject1** 專案︰</span><span class="sxs-lookup"><span data-stu-id="a2ddd-125">Add the following references to the **TestProject1** project:</span></span>  
  
    -   <span data-ttu-id="a2ddd-126">BizTalk 管線 Interop</span><span class="sxs-lookup"><span data-stu-id="a2ddd-126">BizTalk Pipeline Interop</span></span>  
  
    -   <span data-ttu-id="a2ddd-127">Microsoft.BizTalk.TestTools</span><span class="sxs-lookup"><span data-stu-id="a2ddd-127">Microsoft.BizTalk.TestTools</span></span>  
  
    -   <span data-ttu-id="a2ddd-128">Microsoft XLANG/s 基底型別</span><span class="sxs-lookup"><span data-stu-id="a2ddd-128">Microsoft XLANG/s Base Types</span></span>  
  
2.  <span data-ttu-id="a2ddd-129">在 [方案總管] 中，開啟 FFReceivePipelineTest.cs，然後在該檔案頂端新增下列指示詞：</span><span class="sxs-lookup"><span data-stu-id="a2ddd-129">In Solution Explorer, open FFReceivePipelineTest.cs and add the following directives to the top of that file:</span></span>  
  
    ```  
    using System.IO;  
    using System.Collections.Specialized;  
    using System.Collections.Generic;  
    ```  
  
3.  <span data-ttu-id="a2ddd-130">捲動到檔案底部，並取代 **FFReceivePipelineConstructorTest** 為下列程式碼，用來驗證管線輸入存在測試管線之前的方法。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-130">Scroll to the bottom of the file and replace the **FFReceivePipelineConstructorTest** method with the following code, which verifies that the pipeline inputs exist before testing the pipeline.</span></span> <span data-ttu-id="a2ddd-131">此程式碼也確保會產生符合一般檔案結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-131">This code also verifies that a message conforming to the flat file schema is generated.</span></span>  
  
    ```  
    [TestMethod()]  
    public void FFReceivePipelineUnitTest()  
    {  
        //=== Pipeline class derived from TestableReceivePipeline ===//  
        FFReceivePipeline target = new FFReceivePipeline();  
  
        //=== Collection of messages to test the flat file pipeline ===//  
        StringCollection documents = new StringCollection();  
        string strSourcePO_XML = @".\..\..\..\FlatFileReceive_in.txt";  
        Assert.IsTrue(File.Exists(strSourcePO_XML));  
        documents.Add(strSourcePO_XML);  
  
        //=== Only a body part for this test message so an empty ===//  
        //=== collection will be passed.                         ===//  
        StringCollection parts = new StringCollection();  
  
        //=== Dictionary mapping the schema to the namespace and type ===//  
        //=== as displayed in the properties window for the *.xsd     ===//  
        Dictionary<string, string> schemas = new Dictionary<string, string>();  
        string SchemaFile = @".\..\..\..\PO.xsd";  
        Assert.IsTrue(File.Exists(SchemaFile));  
        schemas.Add("Microsoft.Samples.BizTalk.FlatFileReceive.PO", SchemaFile);  
  
        //=== Test the execution of the pipeline using the inputs ===//  
        target.TestPipeline(documents, parts, schemas);  
  
        //=== Validate that the pipeline test produced the message ===//  
        //=== which conforms to the schema.                        ===//  
        string[] strMessages = Directory.GetFiles(testContextInstance.TestDir + "\\out","Message*.out");              
        Assert.IsTrue(strMessages.Length > 0);                          
        PO PO_target = new PO();  
        foreach(string outFile in strMessages)  
        {  
          Assert.IsTrue(PO_target.ValidateInstance(outFile,Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML));  
        }                       
    }  
    ```  
  
## <a name="building-and-running-the-unit-test"></a><span data-ttu-id="a2ddd-132">建置和執行單元測試</span><span class="sxs-lookup"><span data-stu-id="a2ddd-132">Building and Running the Unit Test</span></span>  
  
#### <a name="to-build-and-run-the-unit-test"></a><span data-ttu-id="a2ddd-133">建置和執行單元測試</span><span class="sxs-lookup"><span data-stu-id="a2ddd-133">To build and run the unit test</span></span>  
  
1.  <span data-ttu-id="a2ddd-134">在 方案總管 中，以滑鼠右鍵按一下 **TestProject1**, ，然後按一下  **建置**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-134">In Solution Explorer, right-click **TestProject1**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="a2ddd-135">在主功能表中，按一下  **測試**, ，然後在 **Windows** 清單中，按一下 **測試檢視**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-135">On the main menu, click **Test**, and then in the **Windows** list, click **Test View**.</span></span>  
  
3.  <span data-ttu-id="a2ddd-136">在 測試檢視 視窗中，以滑鼠右鍵按一下 **FFReceivePipelineUnitTest**, ，然後按一下  **執行選取範圍**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-136">In the Test View window, right-click **FFReceivePipelineUnitTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="a2ddd-137">確認您看到 **成功** 測試結果 視窗中。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-137">Verify that you see **Passed** in the Test Results window.</span></span>  
  
4.  <span data-ttu-id="a2ddd-138">在 TestResults 目錄中檢查 \*.out 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-138">In the TestResults directory examine the \*.out file.</span></span> <span data-ttu-id="a2ddd-139">此檔案應包含由管線處理的新訊息。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-139">This file should contain the new message processed by the pipeline.</span></span>  <span data-ttu-id="a2ddd-140">位置所在的目錄看起來應和下面相似：</span><span class="sxs-lookup"><span data-stu-id="a2ddd-140">It should be located in a directory similar to the following:</span></span>  
  
     <span data-ttu-id="a2ddd-141">C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009-02-04 09_01_04\Out</span><span class="sxs-lookup"><span data-stu-id="a2ddd-141">C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009-02-04 09_01_04\Out</span></span>  
  
     <span data-ttu-id="a2ddd-142">所處理的訊息看起來應和下面相似：</span><span class="sxs-lookup"><span data-stu-id="a2ddd-142">The processed message should look similar to the following:</span></span>  
  
    ```  
    <purchaseOrder orderDate="1999-10-20" xmlns="http://FlatFileRecieve.PO">  
  
      <shipTo country="US" xmlns="">  
        <name>Alice Smith</name>  
        <street>123 Maple Street</street>  
        <city>Mill Valley</city>  
        <state>CA</state>  
        <zip>90952</zip>  
      </shipTo>  
  
      <billTo country="US" xmlns="">  
        <name>Robert Smith</name>  
        <street>8 Oak Avenue</street>  
        <city>Old Town</city>  
        <state>PA</state>  
        <zip>95819</zip>  
      </billTo>  
  
      <comment>Hurry, my lawn is going wild!</comment>  
  
      <items xmlns="">  
  
        <item partNum="872-AA">  
          <productName>Lawnmower</productName>  
          <quantity>1</quantity>  
          <USPrice>148.95</USPrice>  
          <comment xmlns="http://FlatFileRecieve.PO">Confirm this is electric</comment>  
        </item>  
  
        <item partNum="926-AA">  
          <productName>Baby Monitor</productName>  
          <quantity>1</quantity>  
          <USPrice>39.98</USPrice>  
          <comment xmlns="http://FlatFileRecieve.PO">Confirm this is electric</comment>  
          <shipDate>1999-05-21</shipDate>  
        </item>  
  
      </items>  
  
    </purchaseOrder>  
    ```  
  
5.  <span data-ttu-id="a2ddd-143">如果任何測試失敗，您可以在 [測試結果] 視窗中，按兩下該測試，查看導致該測試失敗的判斷提示或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-143">If any test fails you can double-click the test in the Test Results window to see the assert or exception that caused that test failure.</span></span>  
  
## <a name="test-code-summary"></a><span data-ttu-id="a2ddd-144">測試程式碼摘要</span><span class="sxs-lookup"><span data-stu-id="a2ddd-144">Test Code Summary</span></span>  
 <span data-ttu-id="a2ddd-145">當已啟用單元測試 **FlatFileReceive** 專案中， **FFReceivePipeline** C# 類別相關聯 **FFReceivePipeline.btp** 衍生自 **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline** 類別。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-145">When unit testing was enabled for the **FlatFileReceive** project, the **FFReceivePipeline** C# class associated with **FFReceivePipeline.btp** was derived from the **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline** class.</span></span> <span data-ttu-id="a2ddd-146">**FFReceivePipelineUnitTest** 方法中的 **TestProject1** 用 **TestPipeline** 方法， **FFReceivePipeline** 繼承來測試一般檔案接收管線。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-146">The **FFReceivePipelineUnitTest** method in **TestProject1** used the **TestPipeline** method that **FFReceivePipeline** inherited to test the flat file receive pipeline.</span></span> <span data-ttu-id="a2ddd-147">在管線處理訊息之後，就會針對一般檔案結構描述來驗證輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-147">After the pipeline processed the message, the output message was validated against the flat file schema.</span></span> <span data-ttu-id="a2ddd-148">參數 **TestPipeline** 方法如下︰</span><span class="sxs-lookup"><span data-stu-id="a2ddd-148">The parameters for the **TestPipeline** method are as follows:</span></span>  
  
|<span data-ttu-id="a2ddd-149">參數名稱</span><span class="sxs-lookup"><span data-stu-id="a2ddd-149">Parameter Name</span></span>|<span data-ttu-id="a2ddd-150">Description</span><span class="sxs-lookup"><span data-stu-id="a2ddd-150">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a2ddd-151">文件</span><span class="sxs-lookup"><span data-stu-id="a2ddd-151">Documents</span></span>|<span data-ttu-id="a2ddd-152">StringCollection 包含要由管線處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-152">StringCollection containing messages to be processed by the pipeline.</span></span>|  
|<span data-ttu-id="a2ddd-153">組件</span><span class="sxs-lookup"><span data-stu-id="a2ddd-153">Parts</span></span>|<span data-ttu-id="a2ddd-154">StringCollection 包含訊息的數個部分。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-154">StringCollection containing the parts for the messages.</span></span>|  
|<span data-ttu-id="a2ddd-155">結構描述</span><span class="sxs-lookup"><span data-stu-id="a2ddd-155">Schemas</span></span>|<span data-ttu-id="a2ddd-156">用來將每個訊息類型對應至其相對應的字典對應 \*.xsd 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-156">Dictionary mapping used to map each message type to its corresponding \*.xsd schema file.</span></span> <span data-ttu-id="a2ddd-157">索引鍵必須是格式 **Namespace.Type**。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-157">The key must be in the format **Namespace.Type**.</span></span> <span data-ttu-id="a2ddd-158">從 [屬性] 視窗，則應該注意的命名空間和型別使用\*Visual Studio 中的.xsd 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-158">The namespace and type used should be noted from the properties window for the \*.xsd file in Visual Studio.</span></span> <span data-ttu-id="a2ddd-159">請參閱下面的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="a2ddd-159">See the screenshot below.</span></span><br /><br /> <span data-ttu-id="a2ddd-160">![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")</span><span class="sxs-lookup"><span data-stu-id="a2ddd-160">![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")</span></span><br /><br /> <span data-ttu-id="a2ddd-161">**命名空間和型別公開從 XSD 檔案的 [屬性] 視窗。**</span><span class="sxs-lookup"><span data-stu-id="a2ddd-161">**Namespace and type exposed from the properties window of an XSD file.**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2ddd-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ddd-162">See Also</span></span>  
 <span data-ttu-id="a2ddd-163">[使用單元測試的結構描述和對應的功能](../core/using-the-unit-testing-feature-with-schemas-and-maps.md) </span><span class="sxs-lookup"><span data-stu-id="a2ddd-163">[Using the Unit Testing Feature with Schemas and Maps](../core/using-the-unit-testing-feature-with-schemas-and-maps.md) </span></span>  
 [<span data-ttu-id="a2ddd-164">使用單元測試 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a2ddd-164">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)