---
title: "使用單元測試功能搭配管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d58bfa4-322b-455f-a062-5bd44d368f57
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5aca6e7be3c4fbeff2484f1d59454b09a4777cff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-unit-testing-feature-with-pipelines"></a>使用單元測試功能搭配管線
此主題示範如何使用單元測試功能，以在 FlatFileReceive 管線範例中新增管線的單元測試。 管線單元測試會記載於此處的 Pipeline.exe 工具相似：[管線工具](../core/pipeline-tools.md)。 當您啟用單元測試上**部署**] 索引標籤的 [專案屬性中，您的專案中的管線類別衍生自**Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**。  此類別可做為 Pipeline.exe 工具所公開之一些相同功能的模型。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先遵循建置 FlatFileReceive 範例的步驟進行，然後便可熟悉該範例。 包含的步驟，用於建置 FlatFileReceive 範例可以在這裡找到的文件： [FlatFileReceive （BizTalk Server 範例）](../core/flatfilereceive-biztalk-server-sample.md)。  
  
## <a name="adding-a-unit-test-project-to-the-flatfilereceive-sample"></a>將單元測試專案新增至 FlatFileReceive 範例  
  
#### <a name="to-add-a-unit-test-project-to-the-flatfilereceive-sample"></a>將單元測試專案新增至 FlatFileReceive 範例  
  
1.  在 Visual Studio 中，開啟 FlatFileReceive.sln 方案檔。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**FlatFileReceive**專案，然後再按一下**屬性**。  
  
3.  在 專案設計工具中，按一下 **部署**屬性頁面 索引標籤和組**啟用單元測試**至`True`。  
  
4.  儲存所做的變更，關閉專案屬性頁。  
  
5.  在主功能表中，按一下 **建置**，然後按一下 **重建方案**。  
  
6.  在主功能表中，按一下 **測試**，然後按一下 **新測試**。  
  
7.  在**加入新測試**對話方塊中，選取**建立新的 Visual C# 測試專案**如**測試專案中加入**欄位。 選取**單元測試精靈**中**範本**清單，然後再按**確定**。  
  
8.  在**新的測試專案**對話方塊方塊中，保留相同的專案名稱**TestProject1**按一下**建立**。  
  
9. 在**建立單元測試**對話方塊方塊中，展開型別，然後選取**FFReceivePipeline()**下的建構函式**Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline**節點。 按一下 **[確定]**。  
  
## <a name="adding-test-code-to-test-the-pipeline"></a>新增測試程式碼以測試管線  
  
#### <a name="to-add-test-code-to-test-the-pipeline"></a>新增測試程式碼以測試管線  
  
1.  將下列參考加入**TestProject1**專案：  
  
    -   BizTalk 管線 Interop  
  
    -   Microsoft.BizTalk.TestTools  
  
    -   Microsoft XLANG/s 基底型別  
  
2.  在 [方案總管] 中，開啟 FFReceivePipelineTest.cs，然後在該檔案頂端新增下列指示詞：  
  
    ```  
    using System.IO;  
    using System.Collections.Specialized;  
    using System.Collections.Generic;  
    ```  
  
3.  捲動到檔案底部，取代**FFReceivePipelineConstructorTest**驗證管線輸入存在測試管線之前為下列程式碼的方法。 此程式碼也確保會產生符合一般檔案結構描述的訊息。  
  
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
  
## <a name="building-and-running-the-unit-test"></a>建置和執行單元測試  
  
#### <a name="to-build-and-run-the-unit-test"></a>建置和執行單元測試  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**TestProject1**，然後按一下 **建置**。  
  
2.  在主功能表中，按一下 **測試**，然後在**Windows**清單中，按一下**測試檢視**。  
  
3.  在 測試檢視 視窗中，以滑鼠右鍵按一下**Testproject1**，然後按一下 **執行選取項目**。 確認您看到**成功**測試結果 視窗中。  
  
4.  在 TestResults 目錄中檢查 *.out 檔案。 此檔案應包含由管線處理的新訊息。  位置所在的目錄看起來應和下面相似：  
  
     C:\Program Files\Microsoft BizTalk Server\<版本 > \SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009年-02-04 09_01_04\Out  
  
     所處理的訊息看起來應和下面相似：  
  
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
  
5.  如果任何測試失敗，您可以在 [測試結果] 視窗中，按兩下該測試，查看導致該測試失敗的判斷提示或例外狀況。  
  
## <a name="test-code-summary"></a>測試程式碼摘要  
 當已啟用單元測試**FlatFileReceive**專案， **FFReceivePipeline**與相關聯的 C# 類別**FFReceivePipeline.btp**衍生自**Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**類別。 **Testproject1**方法中的**TestProject1**用**TestPipeline**方法， **FFReceivePipeline**繼承若要測試一般檔案接收管線。 在管線處理訊息之後，就會針對一般檔案結構描述來驗證輸出訊息。 參數**TestPipeline**方法如下：  
  
|參數名稱|Description|  
|--------------------|-----------------|  
|文件|StringCollection 包含要由管線處理的訊息。|  
|組件|StringCollection 包含訊息的數個部分。|  
|結構描述|用來將每個訊息類型對應至其相對應的字典對應\*.xsd 結構描述檔案。 此金鑰必須是格式**Namespace.Type**。 從 [屬性] 視窗，則應該注意的命名空間和型別使用\*.xsd 檔案中的[!INCLUDE[vs2010](../includes/vs2010-md.md)]。 請參閱下面的螢幕擷取畫面。<br /><br /> ![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")<br /><br /> **命名空間和類型從 XSD 檔案的 [屬性] 視窗中公開。**|  
  
## <a name="see-also"></a>另請參閱  
 [使用單元測試的結構描述和對應的功能](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)   
 [使用單元測試 (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)