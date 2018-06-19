---
title: 使用單元測試功能的結構描述和對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29bcb159-ffdb-44b9-a3ff-565973d41797
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbc14621a1830f15da02336b7b82e9df475cfe9b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288990"
---
# <a name="using-the-unit-testing-feature-with-schemas-and-maps"></a><span data-ttu-id="2c02b-102">利用結構描述與對應來使用單元測試功能</span><span class="sxs-lookup"><span data-stu-id="2c02b-102">Using the Unit Testing Feature with Schemas and Maps</span></span>
<span data-ttu-id="2c02b-103">此主題示範如何使用單元測試功能，以在 HelloWorld 協調流程範例中新增結構描述與對應的單元測試。</span><span class="sxs-lookup"><span data-stu-id="2c02b-103">This topic demonstrates how to use the unit testing feature to add a unit test for the schemas and map in the HelloWorld orchestration example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c02b-104">對應的單元測試功能目前不支援多個輸入對應。</span><span class="sxs-lookup"><span data-stu-id="2c02b-104">The unit testing feature for maps currently does not support multiple input maps.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2c02b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="2c02b-105">Prerequisites</span></span>  
 <span data-ttu-id="2c02b-106">您必須先遵循建置 HelloWorld 範例的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="2c02b-106">You must first follow the steps for building the HelloWorld sample.</span></span> <span data-ttu-id="2c02b-107">這些步驟可以在這裡找到： [HelloWorld （BizTalk Server 範例）](../core/helloworld-biztalk-server-sample.md)</span><span class="sxs-lookup"><span data-stu-id="2c02b-107">Those steps can be found here: [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md)</span></span>  
  
### <a name="adding-a-unit-test-project-to-the-helloworld-sample"></a><span data-ttu-id="2c02b-108">將單元測試專案新增至 HelloWorld 範例</span><span class="sxs-lookup"><span data-stu-id="2c02b-108">Adding a Unit Test Project to the HelloWorld Sample</span></span>  
  
1.  <span data-ttu-id="2c02b-109">在 Visual Studio 中，開啟 HelloWorld.sln 解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="2c02b-109">In Visual Studio, open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2c02b-110">在 [方案總管] 中，以滑鼠右鍵按一下**HelloWorld**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-110">In Solution Explorer, right-click the **HelloWorld** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2c02b-111">在 專案設計工具中，按一下 **部署**屬性頁面 索引標籤和組**啟用單元測試**至`True`。</span><span class="sxs-lookup"><span data-stu-id="2c02b-111">In Project Designer, click the **Deployment** property page tab and set **Enable Unit Testing** to `True`.</span></span>  
  
4.  <span data-ttu-id="2c02b-112">儲存所做的變更，關閉專案屬性頁。</span><span class="sxs-lookup"><span data-stu-id="2c02b-112">Close the project properties page saving the changes.</span></span>  
  
5.  <span data-ttu-id="2c02b-113">在主功能表中，按一下**建置**，然後按一下 **重建方案**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-113">In main menu, click **Build**, and then click **Rebuild Solution**.</span></span>  
  
6.  <span data-ttu-id="2c02b-114">在主功能表中，按一下 **測試**，然後按一下 **新測試**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-114">On the main menu, click **Test**, and then click **New Test**.</span></span>  
  
7.  <span data-ttu-id="2c02b-115">在**加入新測試**對話方塊中，選取**建立新的 Visual C# 測試專案**如**測試專案中加入**欄位。</span><span class="sxs-lookup"><span data-stu-id="2c02b-115">In the **Add New Test** dialog box, select **Create a new Visual C# test project** for **Add to Test Project** field.</span></span> <span data-ttu-id="2c02b-116">選取**單元測試精靈**中**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-116">Select **Unit Test Wizard** in the **Templates** list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="2c02b-117">在**新的測試專案**對話方塊方塊中，保留相同的專案名稱**TestProject1**按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-117">In the **New Test Project** dialog box, leave the project name as **TestProject1** and click **Create**.</span></span>  
  
9. <span data-ttu-id="2c02b-118">在**建立單元測試**對話方塊方塊中，展開型別，然後選取**POSchema()** 下的建構函式**Microsoft.Samples.BizTalk.HelloWorld.POSchema**節點。</span><span class="sxs-lookup"><span data-stu-id="2c02b-118">In the **Create Unit Tests** dialog box, expand the types and select the **POSchema()** constructor under the **Microsoft.Samples.BizTalk.HelloWorld.POSchema** node.</span></span> <span data-ttu-id="2c02b-119">也選取**potoinvoice ()** 下的建構函式**Microsoft.Samples.BizTalk.HelloWorld.POToInvoice**節點。</span><span class="sxs-lookup"><span data-stu-id="2c02b-119">Also select **POToInvoice()** constructor under the **Microsoft.Samples.BizTalk.HelloWorld.POToInvoice** node.</span></span> <span data-ttu-id="2c02b-120">下圖顯示應要選取的項目。</span><span class="sxs-lookup"><span data-stu-id="2c02b-120">The figure below shows the selections that should be made.</span></span> <span data-ttu-id="2c02b-121">如下所示的選取項目之後，請按**確定**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-121">After making the selections shown below, press **OK**.</span></span>  
  
     ![](../core/media/schemaandmapsunittestwizardselection.gif "SchemaAndMapsUnitTestWizardSelection")  
  
### <a name="adding-test-code-to-test-the-schemas-and-map"></a><span data-ttu-id="2c02b-122">新增測試程式碼以測試結構描述與對應</span><span class="sxs-lookup"><span data-stu-id="2c02b-122">Adding Test Code to Test the Schemas and Map</span></span>  
  
1.  <span data-ttu-id="2c02b-123">將下列參考加入**TestProject1**從專案 **.NET**  索引標籤中加入參考 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="2c02b-123">Add the following references to the **TestProject1** project from the **.NET** tab in the Add Reference dialog:</span></span>  
  
    -   <span data-ttu-id="2c02b-124">Microsoft.BizTalk.TestTools</span><span class="sxs-lookup"><span data-stu-id="2c02b-124">Microsoft.BizTalk.TestTools</span></span>  
  
    -   <span data-ttu-id="2c02b-125">Microsoft XLANG/s 基底型別</span><span class="sxs-lookup"><span data-stu-id="2c02b-125">Microsoft XLANG/s Base Types</span></span>  
  
2.  <span data-ttu-id="2c02b-126">在 [方案總管] 中，開啟 POSchemaTest.cs</span><span class="sxs-lookup"><span data-stu-id="2c02b-126">In Solution Explorer, open POSchemaTest.cs</span></span>  
  
3.  <span data-ttu-id="2c02b-127">捲動到檔案底部，取代**POSchemaConstructorTest**方法，以下列程式碼會驗證範例 PO 輸入訊息：</span><span class="sxs-lookup"><span data-stu-id="2c02b-127">Scroll to the bottom of the file and replace the **POSchemaConstructorTest** method with the following code which validates the sample PO input message:</span></span>  
  
    ```  
    [TestMethod()]  
    public void POSchemaInstanceValidationTest()  
    {  
        POSchema target = new POSchema();  
  
        //=== The SamplePOInput.xml file from <Samples Path>\Orchestrations\HelloWorld ===//  
        string strSourcePO_XML = testContextInstance.TestDir + "..\\..\\..\\SamplePOInput.xml";  
  
        //=== Validate the SamplePOInput message against the schema ===//  
        Assert.IsTrue(target.ValidateInstance(strSourcePO_XML, Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML));  
    }  
    ```  
  
4.  <span data-ttu-id="2c02b-128">在 [方案總管] 中，開啟 POToInvoiceTest.cs，然後在該檔案頂端新增下列指示詞：</span><span class="sxs-lookup"><span data-stu-id="2c02b-128">In Solution Explorer open POToInvoiceTest.cs and add the following directive to the top of that file:</span></span>  
  
    ```  
  
    using System.IO;   
    ```  
  
5.  <span data-ttu-id="2c02b-129">捲動到檔案底部，取代**POToInvoiceConstructorTest**方法，以下列程式碼測試對應的使用範例 PO 輸入訊息：</span><span class="sxs-lookup"><span data-stu-id="2c02b-129">Scroll to the bottom of the file and replace the **POToInvoiceConstructorTest** method with the following code which tests the map using the sample PO input message:</span></span>  
  
    ```  
  
    [TestMethod()]  
    public void POToInvoiceMapTest()  
    {  
        POToInvoice target = new POToInvoice();  
  
        //=== Use the HelloWorld sample directory path for the message files ===//  
  
        string strSourcePO_XML = testContextInstance.TestDir + "..\\..\\..\\SamplePOInput.xml";  
        string strDestInvoice_XML = testContextInstance.TestDir + "..\\..\\..\\SampleInvoiceOutput.xml";  
  
        //=== Test the map by using the TestMap method of the TestableMapBase class ===//  
  
        target.ValidateOutput = true;  
        target.TestMap(strSourcePO_XML,  
                       Microsoft.BizTalk.TestTools.Schema.InputInstanceType.Xml,  
                       strDestInvoice_XML,  
                       Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML);  
  
        //=== Output file should be created as a result of testing the map ===//  
  
        Assert.IsTrue(File.Exists(strDestInvoice_XML));   
    }  
    ```  
  
### <a name="building-and-running-the-unit-test"></a><span data-ttu-id="2c02b-130">建置和執行單元測試</span><span class="sxs-lookup"><span data-stu-id="2c02b-130">Building and Running the Unit Test</span></span>  
  
1.  <span data-ttu-id="2c02b-131">在 方案總管 中，以滑鼠右鍵按一下**TestProject1**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-131">In Solution Explorer, right-click **TestProject1**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="2c02b-132">在主功能表中，按一下 **測試**，然後在**Windows**清單中，按一下**測試檢視**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-132">On the main menu, click **Test**, and then in the **Windows** list, click **Test View**.</span></span>  
  
3.  <span data-ttu-id="2c02b-133">在 測試檢視 視窗中，以滑鼠右鍵按一下**Testproject1**，然後按一下 **執行選取項目**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-133">In the Test View window, right-click **POSchemaInstanceValidationTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="2c02b-134">確認您看到**成功**測試結果 視窗中。</span><span class="sxs-lookup"><span data-stu-id="2c02b-134">Verify that you see **Passed** in the Test Results window.</span></span>  
  
4.  <span data-ttu-id="2c02b-135">在 測試檢視 視窗中，以滑鼠右鍵按一下**POToInvoiceMapTest**，然後按一下 **執行選取項目**。</span><span class="sxs-lookup"><span data-stu-id="2c02b-135">In the Test View window, right-click **POToInvoiceMapTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="2c02b-136">確認您看到**成功**測試結果 視窗中。</span><span class="sxs-lookup"><span data-stu-id="2c02b-136">Verify that you see **Passed** in the Test Results window.</span></span>  
  
5.  <span data-ttu-id="2c02b-137">如果任何測試失敗，您可以在 [測試結果] 視窗中，按兩下該測試，查看導致該測試失敗的判斷提示或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2c02b-137">If any test fails you can double-click the test in the Test Results window to see the assert or exception that caused that test failure.</span></span>  
  
## <a name="test-code-summary"></a><span data-ttu-id="2c02b-138">測試程式碼摘要</span><span class="sxs-lookup"><span data-stu-id="2c02b-138">Test Code Summary</span></span>  
 <span data-ttu-id="2c02b-139">當已啟用單元測試**HelloWorld**專案，與關聯的 C# 類別**POSchema.xsd**衍生自**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**類別。</span><span class="sxs-lookup"><span data-stu-id="2c02b-139">When unit testing was enabled for the **HelloWorld** project, the C# class associated with **POSchema.xsd** was derived from the **Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase** class.</span></span> <span data-ttu-id="2c02b-140">**Testproject1**方法中的**TestProject1**用**ValidateInstance**方法**Validateinstance**類別PO 結構描述來驗證 SamplePOInput.xml。</span><span class="sxs-lookup"><span data-stu-id="2c02b-140">The **POSchemaInstanceValidationTest** method in **TestProject1** used the **ValidateInstance** method of the **POSchema** class to validate SamplePOInput.xml against the PO schema.</span></span>  
  
 <span data-ttu-id="2c02b-141">同樣地，當您啟用的單元測試之後，才**HelloWorld**專案，與關聯的 C# 類別**POToInvoice.btm**對應衍生自**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**類別。</span><span class="sxs-lookup"><span data-stu-id="2c02b-141">Similarly, when unit testing was enabled for the **HelloWorld** project, the C# class associated with the **POToInvoice.btm** map was derived from the **Microsoft.BizTalk.TestTools.Mapper.TestableMapBase** class.</span></span> <span data-ttu-id="2c02b-142">**POToInvoiceMaptest**方法使用**TestMap**方法**Testmap**來測試使用相同的 SamplePOInput.xml 訊息對應的類別。</span><span class="sxs-lookup"><span data-stu-id="2c02b-142">The **POToInvoiceMaptest** method used the **TestMap** method of the **POToInvoice** class to test the map using the same SamplePOInput.xml message.</span></span> <span data-ttu-id="2c02b-143">這會導致在 HelloWorld 目錄中建立 SampleInvoiceOutput.xml。</span><span class="sxs-lookup"><span data-stu-id="2c02b-143">This resulted in SampleInvoiceOutput.xml being created in the HelloWorld directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c02b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c02b-144">See Also</span></span>  
 <span data-ttu-id="2c02b-145">[使用單元測試功能搭配管線](../core/using-the-unit-testing-feature-with-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="2c02b-145">[Using the Unit Testing Feature with Pipelines](../core/using-the-unit-testing-feature-with-pipelines.md) </span></span>  
 [<span data-ttu-id="2c02b-146">使用單元測試 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2c02b-146">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)