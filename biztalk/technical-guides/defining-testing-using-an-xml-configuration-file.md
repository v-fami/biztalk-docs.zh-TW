---
title: 定義使用 XML 組態檔進行測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8339bcf-26d7-4a43-b68e-c4220a7a851d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd869d69ca11a41daac459229d7b58684e43afe7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992943"
---
# <a name="defining-testing-using-an-xml-configuration-file"></a><span data-ttu-id="21574-102">定義使用 XML 組態檔進行測試</span><span class="sxs-lookup"><span data-stu-id="21574-102">Defining Testing Using an XML Configuration File</span></span>
<span data-ttu-id="21574-103">BizUnit 提供定義測試的兩種方式： 透過 XML 組態檔與透過 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="21574-103">BizUnit offers two ways to define tests: via an XML configuration file and via an Excel worksheet.</span></span> <span data-ttu-id="21574-104">本主題著重於使用 XML 組態檔定義測試;不過，您應該也查看 BizUnit SDK，因為它提供如何定義使用 Excel 的 BizUnit 測試案例的個有趣的範例。</span><span class="sxs-lookup"><span data-stu-id="21574-104">This topic focuses on using an XML configuration file to define tests; however, you should also look at the BizUnit SDK, since it provides an interesting example of how to define BizUnit test cases using Excel.</span></span> <span data-ttu-id="21574-105">此外，您可能想要調查 BizUnit Designer 工具，可提供的 GUI，能快速建立 BizUnit 測試案例。</span><span class="sxs-lookup"><span data-stu-id="21574-105">In addition, you may wish to investigate the BizUnit Designer tool, which provides a GUI that allows for rapid creation of BizUnit test cases.</span></span> <span data-ttu-id="21574-106">本主題提供如何定義使用 XML 組態使用非常簡化的案例的測試案例的概觀。</span><span class="sxs-lookup"><span data-stu-id="21574-106">This topic provides an overview of how to define test cases using XML configuration using a very simplified scenario.</span></span>  
  
## <a name="overview-of-defining-a-bizunit-test-case-using-xml-configuration"></a><span data-ttu-id="21574-107">定義使用 XML 組態 BizUnit 測試案例的概觀</span><span class="sxs-lookup"><span data-stu-id="21574-107">Overview of defining a BizUnit test case using XML configuration</span></span>  
 <span data-ttu-id="21574-108">為剛才所述，這種情況下，已經過簡化為了進行說明。</span><span class="sxs-lookup"><span data-stu-id="21574-108">As just stated, this scenario is simplified for purposes of illustration.</span></span> <span data-ttu-id="21574-109">請考慮訊息類似如下所示的應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="21574-109">Consider a sample messaging application such as the one illustrated below.</span></span> <span data-ttu-id="21574-110">讓我們假設正常功能的行為，此應用程式是 BizTalk 收到的 XML 檔案，透過檔案接收位置，它然後將它傳送至適當的訂閱者，根據訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="21574-110">Let’s assume that normal functional behavior for this application is that BizTalk receives an XML file via a file receive location, it then sends it to an appropriate subscriber based on a subscription.</span></span> <span data-ttu-id="21574-111">若要有效地驗證此案例中很重要我們在測試中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="21574-111">To validate this scenario effectively it is important that we perform the following steps in the test:</span></span>  
  
1. <span data-ttu-id="21574-112">設定環境，以確保它是處於一致的狀態和已準備好要執行測試：</span><span class="sxs-lookup"><span data-stu-id="21574-112">Set up the environment to ensure that it is in a consistent state and ready for the test to be run:</span></span>  
  
   -   <span data-ttu-id="21574-113">這是藉由刪除使用的兩個檔案位置中有任何檔案。</span><span class="sxs-lookup"><span data-stu-id="21574-113">This is done by deleting any files that are present in the two file locations used.</span></span>  
  
2. <span data-ttu-id="21574-114">執行測試以驗證功能：</span><span class="sxs-lookup"><span data-stu-id="21574-114">Run the test to verify functionality:</span></span>  
  
   -   <span data-ttu-id="21574-115">建立有效的 XML 訊息的資料夾中，檔案接收位置輪詢。</span><span class="sxs-lookup"><span data-stu-id="21574-115">Create a valid XML message in the folder that the file receive location polls.</span></span>  
  
   -   <span data-ttu-id="21574-116">驗證正確的 XML 訊息會放在輸出資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="21574-116">Validate that the correct XML message is placed in the outbound folder location.</span></span>  
  
   -   <span data-ttu-id="21574-117">驗證應涵蓋的結構描述和訊息的承載資訊。</span><span class="sxs-lookup"><span data-stu-id="21574-117">The validation should cover both the schema and the payload information for the message.</span></span> <span data-ttu-id="21574-118">（通常數個索引鍵的欄位應該進行檢查。）</span><span class="sxs-lookup"><span data-stu-id="21574-118">(Typically a couple of the key fields should be examined.)</span></span>  
  
3. <span data-ttu-id="21574-119">清除環境，以確定環境處於相同的狀態之前先執行測試：</span><span class="sxs-lookup"><span data-stu-id="21574-119">Clean up the environment to ensure that the environment is in the same state as before the test executed:</span></span>  
  
   -   <span data-ttu-id="21574-120">刪除使用的兩個檔案位置中有任何檔案。</span><span class="sxs-lookup"><span data-stu-id="21574-120">Delete any files that are present in the two file locations used.</span></span>  
  
   <span data-ttu-id="21574-121">![範例 BizTalk 傳訊應用程式](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span><span class="sxs-lookup"><span data-stu-id="21574-121">![Sample BizTalk Messaging Application](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span></span>  
   <span data-ttu-id="21574-122">範例 BizTalk 傳訊應用程式</span><span class="sxs-lookup"><span data-stu-id="21574-122">Sample BizTalk Messaging application</span></span>  
  
   <span data-ttu-id="21574-123">每個測試案例開頭和結尾 TestCase XML 標記testName 參數會傳遞到這個，以下所示。</span><span class="sxs-lookup"><span data-stu-id="21574-123">Each test case begins and ends with the TestCase XML tag; the testName parameter is passed into this as indicated here.</span></span>  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
```  
  
 <span data-ttu-id="21574-124">然後，我們要輸入 TestSetup 階段中，在其中我們確定環境處於一致的狀態，以執行測試。</span><span class="sxs-lookup"><span data-stu-id="21574-124">Then we enter the TestSetup phase, in which we ensure that the environment is in a consistent state to run the test.</span></span> <span data-ttu-id="21574-125">在此範例中，我們會刪除任何所包含的 XML 訊息我們 TestData 目錄中。</span><span class="sxs-lookup"><span data-stu-id="21574-125">In this example, we delete any XML messages that are contained in our TestData directory.</span></span> <span data-ttu-id="21574-126">這是使用**FileDeleteMultipleStep**。</span><span class="sxs-lookup"><span data-stu-id="21574-126">This is done using the **FileDeleteMultipleStep**.</span></span>  
  
```  
<TestSetup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
</TestSetup>  
```  
  
 <span data-ttu-id="21574-127">然後就可以輸入的測試，測試執行階段的最重要區段是什麼。</span><span class="sxs-lookup"><span data-stu-id="21574-127">We then enter what is the most critical section of the test, the test execution stage.</span></span> <span data-ttu-id="21574-128">這個階段可以包含多個測試步驟。</span><span class="sxs-lookup"><span data-stu-id="21574-128">This stage can contain multiple test steps.</span></span> <span data-ttu-id="21574-129">在此範例中我們使用 FileCreateStep 複製文件 (可在看到 InDoc1.xml \<SourcePath\>標記) 供檔案拖放到我們接收位置。</span><span class="sxs-lookup"><span data-stu-id="21574-129">In this example we use the FileCreateStep to copy a document (InDoc1.xml which can be seen in the \<SourcePath\> tag) to a file drop which is used by our receive location.</span></span> <span data-ttu-id="21574-130">請務必注意 BizUnit，支援的檔案名稱，在此步驟中，使用唯一識別碼這可以使用 %creationpath 標記中的 Guid %參考。</span><span class="sxs-lookup"><span data-stu-id="21574-130">It’s important to note that BizUnit supports using unique identifiers for filenames in this step; this can be seen with the %Guid% reference in the CreationPath tag.</span></span>  
  
 <span data-ttu-id="21574-131">這已完成之後，我們需要使用**FileValidateStep**建立來驗證輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="21574-131">After this has been completed, we need to use the **FileValidateStep** to validate the outbound message has been created.</span></span> <span data-ttu-id="21574-132">您會發現這個步驟可讓您指定的逾時值 （這是以毫秒為單位）、 目錄和搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="21574-132">You will notice this step allows you to specify a timeout value (this is in milliseconds), the directory and the search pattern.</span></span> <span data-ttu-id="21574-133">此外， **DeleteFile**標記可讓您指定您是否想要經過驗證之後，移除的檔案。</span><span class="sxs-lookup"><span data-stu-id="21574-133">In addition to this, the **DeleteFile** tag enables you to specify whether you want the file to be removed after it has been validated.</span></span> <span data-ttu-id="21574-134">最後，您也應該注意驗證包含 XPath 查詢中，驗證 [PONumber] 節點，在 XML 訊息 （它檢查的值為 PONumber_0）。檢查與驗證的任何輸出訊息的承載會使用 BizUnit 時所應遵循的指導原則的另一個範例。</span><span class="sxs-lookup"><span data-stu-id="21574-134">Finally, you should also note the validation includes an XPath query, which validates the PONumber node within the XML message (it checks that the value is PONumber_0.) Examination and validation of the payload of any outbound messages is another example of a guiding principle that you should follow when using BizUnit.</span></span>  
  
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
  
 <span data-ttu-id="21574-135">測試案例的最後階段為清除作業。</span><span class="sxs-lookup"><span data-stu-id="21574-135">The final stage of the test case is the cleanup.</span></span> <span data-ttu-id="21574-136">可以在這裡，看出**FileDelete**測試步驟用來清除測試用的目錄。</span><span class="sxs-lookup"><span data-stu-id="21574-136">As can be seen here, the **FileDelete** test step is used to clean up the directories used by the test.</span></span>  
  
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
  
 <span data-ttu-id="21574-137">希望這個範例會說明定義 BizUnit 測試，是相當直接的方法和，藉由使用此測試架構，您將能夠快速開發提供您的應用程式的功能測試的測試案例。</span><span class="sxs-lookup"><span data-stu-id="21574-137">Hopefully this example illustrates that defining tests in BizUnit is relatively straightforward and that by using this test framework, you will be able to rapidly develop test cases to provide functional testing of your application.</span></span>  
  
### <a name="full-test-case-example"></a><span data-ttu-id="21574-138">完整的測試案例範例</span><span class="sxs-lookup"><span data-stu-id="21574-138">Full test case example</span></span>  
 <span data-ttu-id="21574-139">完整的測試案例的組態檔案內容會包含在此處您參考：</span><span class="sxs-lookup"><span data-stu-id="21574-139">The full test case configuration file contents are included here for your reference:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21574-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21574-140">See Also</span></span>  
 [<span data-ttu-id="21574-141">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="21574-141">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)