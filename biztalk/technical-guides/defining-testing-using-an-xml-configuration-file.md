---
title: "定義使用 XML 組態檔進行測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8339bcf-26d7-4a43-b68e-c4220a7a851d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 761f8c0a4480c26240926240cd890c1c68419b58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-testing-using-an-xml-configuration-file"></a><span data-ttu-id="87d03-102">定義使用 XML 組態檔進行測試</span><span class="sxs-lookup"><span data-stu-id="87d03-102">Defining Testing Using an XML Configuration File</span></span>
<span data-ttu-id="87d03-103">BizUnit 提供以定義測試的兩種方法： 透過 XML 組態檔與透過 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="87d03-103">BizUnit offers two ways to define tests: via an XML configuration file and via an Excel worksheet.</span></span> <span data-ttu-id="87d03-104">本主題著重在使用 XML 組態檔來定義測試。不過，您應該也查看 BizUnit SDK，因為它提供有趣如何定義使用 Excel 的 BizUnit 測試案例的範例。</span><span class="sxs-lookup"><span data-stu-id="87d03-104">This topic focuses on using an XML configuration file to define tests; however, you should also look at the BizUnit SDK, since it provides an interesting example of how to define BizUnit test cases using Excel.</span></span> <span data-ttu-id="87d03-105">此外，您可能想要調查 [BizUnit 設計工具] 工具，提供可以快速建立 BizUnit 測試案例的 GUI。</span><span class="sxs-lookup"><span data-stu-id="87d03-105">In addition, you may wish to investigate the BizUnit Designer tool, which provides a GUI that allows for rapid creation of BizUnit test cases.</span></span> <span data-ttu-id="87d03-106">本主題提供如何定義使用 XML 組態使用非常簡化的案例的測試案例的概觀。</span><span class="sxs-lookup"><span data-stu-id="87d03-106">This topic provides an overview of how to define test cases using XML configuration using a very simplified scenario.</span></span>  
  
## <a name="overview-of-defining-a-bizunit-test-case-using-xml-configuration"></a><span data-ttu-id="87d03-107">定義使用 XML 組態 BizUnit 測試案例的概觀</span><span class="sxs-lookup"><span data-stu-id="87d03-107">Overview of defining a BizUnit test case using XML configuration</span></span>  
 <span data-ttu-id="87d03-108">為剛才所述，此案例已經過簡化供目的圖例。</span><span class="sxs-lookup"><span data-stu-id="87d03-108">As just stated, this scenario is simplified for purposes of illustration.</span></span> <span data-ttu-id="87d03-109">請考慮傳訊應用程式，例如以下的範例。</span><span class="sxs-lookup"><span data-stu-id="87d03-109">Consider a sample messaging application such as the one illustrated below.</span></span> <span data-ttu-id="87d03-110">讓我們假設正常功能的行為，這個應用程式是 BizTalk 收到的 XML 檔案，透過檔案接收位置，它然後將它傳送至適當的訂閱者，根據訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="87d03-110">Let’s assume that normal functional behavior for this application is that BizTalk receives an XML file via a file receive location, it then sends it to an appropriate subscriber based on a subscription.</span></span> <span data-ttu-id="87d03-111">若要有效地驗證此案例中非常重要我們在測試中執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="87d03-111">To validate this scenario effectively it is important that we perform the following steps in the test:</span></span>  
  
1.  <span data-ttu-id="87d03-112">設定環境，以確保它處於一致的狀態和已備妥要執行測試：</span><span class="sxs-lookup"><span data-stu-id="87d03-112">Set up the environment to ensure that it is in a consistent state and ready for the test to be run:</span></span>  
  
    -   <span data-ttu-id="87d03-113">這是刪除沒有使用的兩個檔案位置中的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="87d03-113">This is done by deleting any files that are present in the two file locations used.</span></span>  
  
2.  <span data-ttu-id="87d03-114">執行測試來驗證功能：</span><span class="sxs-lookup"><span data-stu-id="87d03-114">Run the test to verify functionality:</span></span>  
  
    -   <span data-ttu-id="87d03-115">建立有效的 XML 訊息的資料夾中，檔案接收位置的輪詢。</span><span class="sxs-lookup"><span data-stu-id="87d03-115">Create a valid XML message in the folder that the file receive location polls.</span></span>  
  
    -   <span data-ttu-id="87d03-116">驗證正確的 XML 訊息會放在輸出資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="87d03-116">Validate that the correct XML message is placed in the outbound folder location.</span></span>  
  
    -   <span data-ttu-id="87d03-117">驗證應涵蓋的結構描述和訊息的承載資訊。</span><span class="sxs-lookup"><span data-stu-id="87d03-117">The validation should cover both the schema and the payload information for the message.</span></span> <span data-ttu-id="87d03-118">（通常是幾個索引鍵欄位都應該經過檢查。）</span><span class="sxs-lookup"><span data-stu-id="87d03-118">(Typically a couple of the key fields should be examined.)</span></span>  
  
3.  <span data-ttu-id="87d03-119">清除環境，以確定環境處於相同狀態然後再執行測試：</span><span class="sxs-lookup"><span data-stu-id="87d03-119">Clean up the environment to ensure that the environment is in the same state as before the test executed:</span></span>  
  
    -   <span data-ttu-id="87d03-120">刪除使用的兩個檔案位置中出現的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="87d03-120">Delete any files that are present in the two file locations used.</span></span>  
  
 <span data-ttu-id="87d03-121">![範例 BizTalk 訊息應用程式](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span><span class="sxs-lookup"><span data-stu-id="87d03-121">![Sample BizTalk Messaging Application](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span></span>  
<span data-ttu-id="87d03-122">範例 BizTalk 傳訊應用程式</span><span class="sxs-lookup"><span data-stu-id="87d03-122">Sample BizTalk Messaging application</span></span>  
  
 <span data-ttu-id="87d03-123">每個測試案例開始，並以測試案例 XML 結束標記。testName 參數會傳遞到這個，此處所示。</span><span class="sxs-lookup"><span data-stu-id="87d03-123">Each test case begins and ends with the TestCase XML tag; the testName parameter is passed into this as indicated here.</span></span>  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
```  
  
 <span data-ttu-id="87d03-124">然後我們輸入 TestSetup 階段中，在其中我們確定環境處於一致的狀態，以執行測試。</span><span class="sxs-lookup"><span data-stu-id="87d03-124">Then we enter the TestSetup phase, in which we ensure that the environment is in a consistent state to run the test.</span></span> <span data-ttu-id="87d03-125">在此範例中，我們會刪除任何包含的 XML 訊息我們 TestData 目錄中。</span><span class="sxs-lookup"><span data-stu-id="87d03-125">In this example, we delete any XML messages that are contained in our TestData directory.</span></span> <span data-ttu-id="87d03-126">這是使用**FileDeleteMultipleStep**。</span><span class="sxs-lookup"><span data-stu-id="87d03-126">This is done using the **FileDeleteMultipleStep**.</span></span>  
  
```  
<TestSetup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
</TestSetup>  
```  
  
 <span data-ttu-id="87d03-127">我們再輸入什麼是最重要區段的測試，測試執行階段。</span><span class="sxs-lookup"><span data-stu-id="87d03-127">We then enter what is the most critical section of the test, the test execution stage.</span></span> <span data-ttu-id="87d03-128">這個階段可以包含多個測試步驟。</span><span class="sxs-lookup"><span data-stu-id="87d03-128">This stage can contain multiple test steps.</span></span> <span data-ttu-id="87d03-129">在此範例中我們使用 FileCreateStep 複製文件 (InDoc1.xml 中能看到\<SourcePath > 標記) 所使用的為檔案置放我們接收位置。</span><span class="sxs-lookup"><span data-stu-id="87d03-129">In this example we use the FileCreateStep to copy a document (InDoc1.xml which can be seen in the \<SourcePath> tag) to a file drop which is used by our receive location.</span></span> <span data-ttu-id="87d03-130">請務必注意 BizUnit 支援使用唯一的識別項的檔名，在此步驟。這可以看到 %creationpath 標記中的 Guid %參考。</span><span class="sxs-lookup"><span data-stu-id="87d03-130">It’s important to note that BizUnit supports using unique identifiers for filenames in this step; this can be seen with the %Guid% reference in the CreationPath tag.</span></span>  
  
 <span data-ttu-id="87d03-131">完成之後，我們需要使用**FileValidateStep**驗證外寄訊息已建立。</span><span class="sxs-lookup"><span data-stu-id="87d03-131">After this has been completed, we need to use the **FileValidateStep** to validate the outbound message has been created.</span></span> <span data-ttu-id="87d03-132">您會發現此步驟可讓您指定的逾時值 （這是以毫秒為單位）、 目錄和搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="87d03-132">You will notice this step allows you to specify a timeout value (this is in milliseconds), the directory and the search pattern.</span></span> <span data-ttu-id="87d03-133">此外， **DeleteFile**標記可讓您指定您是否想要經過驗證之後，會移除的檔案。</span><span class="sxs-lookup"><span data-stu-id="87d03-133">In addition to this, the **DeleteFile** tag enables you to specify whether you want the file to be removed after it has been validated.</span></span> <span data-ttu-id="87d03-134">最後，您也應注意驗證包含 XPath 查詢中，確認 [PONumber] 節點內 XML 訊息 （它檢查的值為 PONumber_0）。檢查與驗證的任何輸出訊息的裝載會使用 BizUnit 時應遵循的指導原則的另一個範例。</span><span class="sxs-lookup"><span data-stu-id="87d03-134">Finally, you should also note the validation includes an XPath query, which validates the PONumber node within the XML message (it checks that the value is PONumber_0.) Examination and validation of the payload of any outbound messages is another example of a guiding principle that you should follow when using BizUnit.</span></span>  
  
```  
<TestExecution>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileCreateStep">  
      <SourcePath>..\..\..\TestData\InDoc1.xml</SourcePath>  
      <CreationPath>..\..\..\Rec_03\TransactionId_%Guid%.xml</CreationPath>  
   </TestStep>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileValidateStep">  
      <Timeout>3000</Timeout>  
      <Directory>..\..\..\Rec_03\</Directory>  
      <SearchPattern>TransactionId_*.xml</SearchPattern>  
      <DeleteFile>true</DeleteFile>  
      <ValidationStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.XmlValidationStep">  
         <XmlSchemaPath>..\..\..\TestData\PurchaseOrder.xsd</XmlSchemaPath>  
         <XmlSchemaNameSpace>http://SendMail.PurchaseOrder</XmlSchemaNameSpace>  
         <XPathList>  
            <XPathValidation query="/*[local-name()='PurchaseOrder' and namespace-uri()='http://SendMail.PurchaseOrder']/*[local-name()='PONumber' and namespace-uri()='']">PONumber_0</XPathValidation>  
         </XPathList>  
      </ValidationStep>  
   </TestStep>  
</TestExecution>  
```  
  
 <span data-ttu-id="87d03-135">測試案例的最後階段為清除。</span><span class="sxs-lookup"><span data-stu-id="87d03-135">The final stage of the test case is the cleanup.</span></span> <span data-ttu-id="87d03-136">在這裡，可以看出**FileDelete**測試步驟用來清除測試所使用的目錄。</span><span class="sxs-lookup"><span data-stu-id="87d03-136">As can be seen here, the **FileDelete** test step is used to clean up the directories used by the test.</span></span>  
  
```  
<TestCleanup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
      <SearchPattern>*.xml</SearchPattern>   
   </TestStep>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\Rec_03\</Directory>  
      <SearchPattern>*.xml</SearchPattern>   
   </TestStep>  
</TestCleanup>  
```  
  
 <span data-ttu-id="87d03-137">希望這個範例會說明 BizUnit 中定義的測試，是相當直接的方法和，藉由使用此測試架構，您將能夠快速地開發測試案例來提供您的應用程式的功能測試。</span><span class="sxs-lookup"><span data-stu-id="87d03-137">Hopefully this example illustrates that defining tests in BizUnit is relatively straightforward and that by using this test framework, you will be able to rapidly develop test cases to provide functional testing of your application.</span></span>  
  
### <a name="full-test-case-example"></a><span data-ttu-id="87d03-138">完整的測試案例的範例</span><span class="sxs-lookup"><span data-stu-id="87d03-138">Full test case example</span></span>  
 <span data-ttu-id="87d03-139">完整的測試案例的組態檔內容會包含在此處提供您參考：</span><span class="sxs-lookup"><span data-stu-id="87d03-139">The full test case configuration file contents are included here for your reference:</span></span>  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
   <TestSetup>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\TestData\</Directory>  
            <SearchPattern>*.xml</SearchPattern>   
         </TestStep>  
   </TestSetup>  
   <TestExecution>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileCreateStep">  
         <SourcePath>..\..\..\TestData\InDoc1.xml</SourcePath>  
         <CreationPath>..\..\..\Rec_03\TransactionId_%Guid%.xml</CreationPath>  
      </TestStep>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileValidateStep">  
         <Timeout>3000</Timeout>  
         <Directory>..\..\..\Rec_03\</Directory>  
         <SearchPattern>TransactionId_*.xml</SearchPattern>  
         <DeleteFile>true</DeleteFile>  
         <ValidationStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.XmlValidationStep">  
            <XmlSchemaPath>..\..\..\TestData\PurchaseOrder.xsd</XmlSchemaPath>  
            <XmlSchemaNameSpace>http://SendMail.PurchaseOrder</XmlSchemaNameSpace>  
            <XPathList>  
               <XPathValidation query="/*[local-name()='PurchaseOrder' and namespace-uri()='http://SendMail.PurchaseOrder']/*[local-name()='PONumber' and namespace-uri()='']">PONumber_0</XPathValidation>  
            </XPathList>  
         </ValidationStep>  
      </TestStep>  
   </TestExecution>  
   <!-- Test cleanup: test cases should always leave the system in the state they found it -->  
   <TestCleanup>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\Rec_03\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87d03-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87d03-140">See Also</span></span>  
 [<span data-ttu-id="87d03-141">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="87d03-141">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)