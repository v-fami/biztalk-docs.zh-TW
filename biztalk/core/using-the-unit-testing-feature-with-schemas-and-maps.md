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
# <a name="using-the-unit-testing-feature-with-schemas-and-maps"></a>利用結構描述與對應來使用單元測試功能
此主題示範如何使用單元測試功能，以在 HelloWorld 協調流程範例中新增結構描述與對應的單元測試。  
  
> [!NOTE]
>  對應的單元測試功能目前不支援多個輸入對應。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先遵循建置 HelloWorld 範例的步驟進行。 這些步驟可以在這裡找到： [HelloWorld （BizTalk Server 範例）](../core/helloworld-biztalk-server-sample.md)  
  
### <a name="adding-a-unit-test-project-to-the-helloworld-sample"></a>將單元測試專案新增至 HelloWorld 範例  
  
1.  在 Visual Studio 中，開啟 HelloWorld.sln 解決方案檔案。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**HelloWorld**專案，然後再按一下**屬性**。  
  
3.  在 專案設計工具中，按一下 **部署**屬性頁面 索引標籤和組**啟用單元測試**至`True`。  
  
4.  儲存所做的變更，關閉專案屬性頁。  
  
5.  在主功能表中，按一下**建置**，然後按一下 **重建方案**。  
  
6.  在主功能表中，按一下 **測試**，然後按一下 **新測試**。  
  
7.  在**加入新測試**對話方塊中，選取**建立新的 Visual C# 測試專案**如**測試專案中加入**欄位。 選取**單元測試精靈**中**範本**清單，然後再按**確定**。  
  
8.  在**新的測試專案**對話方塊方塊中，保留相同的專案名稱**TestProject1**按一下**建立**。  
  
9. 在**建立單元測試**對話方塊方塊中，展開型別，然後選取**POSchema()** 下的建構函式**Microsoft.Samples.BizTalk.HelloWorld.POSchema**節點。 也選取**potoinvoice ()** 下的建構函式**Microsoft.Samples.BizTalk.HelloWorld.POToInvoice**節點。 下圖顯示應要選取的項目。 如下所示的選取項目之後，請按**確定**。  
  
     ![](../core/media/schemaandmapsunittestwizardselection.gif "SchemaAndMapsUnitTestWizardSelection")  
  
### <a name="adding-test-code-to-test-the-schemas-and-map"></a>新增測試程式碼以測試結構描述與對應  
  
1.  將下列參考加入**TestProject1**從專案 **.NET**  索引標籤中加入參考 對話方塊：  
  
    -   Microsoft.BizTalk.TestTools  
  
    -   Microsoft XLANG/s 基底型別  
  
2.  在 [方案總管] 中，開啟 POSchemaTest.cs  
  
3.  捲動到檔案底部，取代**POSchemaConstructorTest**方法，以下列程式碼會驗證範例 PO 輸入訊息：  
  
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
  
4.  在 [方案總管] 中，開啟 POToInvoiceTest.cs，然後在該檔案頂端新增下列指示詞：  
  
    ```  
  
    using System.IO;   
    ```  
  
5.  捲動到檔案底部，取代**POToInvoiceConstructorTest**方法，以下列程式碼測試對應的使用範例 PO 輸入訊息：  
  
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
  
### <a name="building-and-running-the-unit-test"></a>建置和執行單元測試  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**TestProject1**，然後按一下 **建置**。  
  
2.  在主功能表中，按一下 **測試**，然後在**Windows**清單中，按一下**測試檢視**。  
  
3.  在 測試檢視 視窗中，以滑鼠右鍵按一下**Testproject1**，然後按一下 **執行選取項目**。 確認您看到**成功**測試結果 視窗中。  
  
4.  在 測試檢視 視窗中，以滑鼠右鍵按一下**POToInvoiceMapTest**，然後按一下 **執行選取項目**。 確認您看到**成功**測試結果 視窗中。  
  
5.  如果任何測試失敗，您可以在 [測試結果] 視窗中，按兩下該測試，查看導致該測試失敗的判斷提示或例外狀況。  
  
## <a name="test-code-summary"></a>測試程式碼摘要  
 當已啟用單元測試**HelloWorld**專案，與關聯的 C# 類別**POSchema.xsd**衍生自**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**類別。 **Testproject1**方法中的**TestProject1**用**ValidateInstance**方法**Validateinstance**類別PO 結構描述來驗證 SamplePOInput.xml。  
  
 同樣地，當您啟用的單元測試之後，才**HelloWorld**專案，與關聯的 C# 類別**POToInvoice.btm**對應衍生自**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**類別。 **POToInvoiceMaptest**方法使用**TestMap**方法**Testmap**來測試使用相同的 SamplePOInput.xml 訊息對應的類別。 這會導致在 HelloWorld 目錄中建立 SampleInvoiceOutput.xml。  
  
## <a name="see-also"></a>另請參閱  
 [使用單元測試功能搭配管線](../core/using-the-unit-testing-feature-with-pipelines.md)   
 [使用單元測試 (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)