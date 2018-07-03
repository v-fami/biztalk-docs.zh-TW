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
# <a name="defining-testing-using-an-xml-configuration-file"></a>定義使用 XML 組態檔進行測試
BizUnit 提供定義測試的兩種方式： 透過 XML 組態檔與透過 Excel 工作表。 本主題著重於使用 XML 組態檔定義測試;不過，您應該也查看 BizUnit SDK，因為它提供如何定義使用 Excel 的 BizUnit 測試案例的個有趣的範例。 此外，您可能想要調查 BizUnit Designer 工具，可提供的 GUI，能快速建立 BizUnit 測試案例。 本主題提供如何定義使用 XML 組態使用非常簡化的案例的測試案例的概觀。  
  
## <a name="overview-of-defining-a-bizunit-test-case-using-xml-configuration"></a>定義使用 XML 組態 BizUnit 測試案例的概觀  
 為剛才所述，這種情況下，已經過簡化為了進行說明。 請考慮訊息類似如下所示的應用程式的範例。 讓我們假設正常功能的行為，此應用程式是 BizTalk 收到的 XML 檔案，透過檔案接收位置，它然後將它傳送至適當的訂閱者，根據訂用帳戶。 若要有效地驗證此案例中很重要我們在測試中，執行下列步驟：  
  
1. 設定環境，以確保它是處於一致的狀態和已準備好要執行測試：  
  
   -   這是藉由刪除使用的兩個檔案位置中有任何檔案。  
  
2. 執行測試以驗證功能：  
  
   -   建立有效的 XML 訊息的資料夾中，檔案接收位置輪詢。  
  
   -   驗證正確的 XML 訊息會放在輸出資料夾位置。  
  
   -   驗證應涵蓋的結構描述和訊息的承載資訊。 （通常數個索引鍵的欄位應該進行檢查。）  
  
3. 清除環境，以確定環境處於相同的狀態之前先執行測試：  
  
   -   刪除使用的兩個檔案位置中有任何檔案。  
  
   ![範例 BizTalk 傳訊應用程式](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")  
   範例 BizTalk 傳訊應用程式  
  
   每個測試案例開頭和結尾 TestCase XML 標記testName 參數會傳遞到這個，以下所示。  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
```  
  
 然後，我們要輸入 TestSetup 階段中，在其中我們確定環境處於一致的狀態，以執行測試。 在此範例中，我們會刪除任何所包含的 XML 訊息我們 TestData 目錄中。 這是使用**FileDeleteMultipleStep**。  
  
```  
<TestSetup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
</TestSetup>  
```  
  
 然後就可以輸入的測試，測試執行階段的最重要區段是什麼。 這個階段可以包含多個測試步驟。 在此範例中我們使用 FileCreateStep 複製文件 (可在看到 InDoc1.xml \<SourcePath\>標記) 供檔案拖放到我們接收位置。 請務必注意 BizUnit，支援的檔案名稱，在此步驟中，使用唯一識別碼這可以使用 %creationpath 標記中的 Guid %參考。  
  
 這已完成之後，我們需要使用**FileValidateStep**建立來驗證輸出訊息。 您會發現這個步驟可讓您指定的逾時值 （這是以毫秒為單位）、 目錄和搜尋模式。 此外， **DeleteFile**標記可讓您指定您是否想要經過驗證之後，移除的檔案。 最後，您也應該注意驗證包含 XPath 查詢中，驗證 [PONumber] 節點，在 XML 訊息 （它檢查的值為 PONumber_0）。檢查與驗證的任何輸出訊息的承載會使用 BizUnit 時所應遵循的指導原則的另一個範例。  
  
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
  
 測試案例的最後階段為清除作業。 可以在這裡，看出**FileDelete**測試步驟用來清除測試用的目錄。  
  
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
  
 希望這個範例會說明定義 BizUnit 測試，是相當直接的方法和，藉由使用此測試架構，您將能夠快速開發提供您的應用程式的功能測試的測試案例。  
  
### <a name="full-test-case-example"></a>完整的測試案例範例  
 完整的測試案例的組態檔案內容會包含在此處您參考：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用 BizUnit 促進自動化測試](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)