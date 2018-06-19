---
title: 商務規則 Hello World1 （BizTalk Server 範例） |Microsoft 文件
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
ms.openlocfilehash: ebe9f04fc8dac06676d7f29bf5dd2ecd01e7a06c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967668"
---
# <a name="business-rules-hello-world1-biztalk-server-sample"></a>商務規則 Hello World1 （BizTalk Server 範例）
「商務規則 Hello World1」範例示範如何建立 BizTalk 規則集、將規則集儲存到檔案 (SampleRuleSet.xml)、載入規則集，以及依據一組事實範例執行該規則集。 範例規則集包含有關 XML 項目的簡單規則，以及做為規則定義內容的 .NET 物件 (屬性和成員)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會建立可執行檔，用來執行下面的一系列步驟：  
  
1.  呼叫方法**CreateRuleset**來建立規則集的 < 備註 > 一節所述。  
  
2.  呼叫方法**SaveToFile**示範儲存規則集至檔案。  
  
3.  呼叫方法**LoadFromFile**示範載入規則集檔案。  
  
4.  建構要執行規則集的範例事實。  
  
5.  針對範例事實執行規則集，產生螢幕輸出。  
  
6.  暫停，讓您檢查規則集檔案 SampleRuleStore.xml。  
  
7.  透過刪除規則集檔案進行清除，準備接續的範例執行。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Business Rules\Business 規則 Hello World1\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|App.ico、AssemblyInfo.cs、BusinessRulesHelloWorld1.csproj、BusinessRulesHelloWorld1.sln|這個範例所屬的專案、解決方案和相關檔案，可建立、儲存、載入和執行規則集。|  
|HelloWorld1.cs|Visual C# 檔案，其中包含的方法用於示範建立規則集、儲存規則集到檔案中，以及從檔案載入規則集。 另外也包含周圍程式碼，用於呼叫這些方法，然後再執行所建立的規則集。|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|SampleDocumentInstance.xml|範例輸入檔，與 SampleSchema.xsd 檔中定義的結構描述相符。|  
|SampleSchema.xsd|結構描述檔，定義簡單的結構描述，其中某個項目會由 Visual C# 檔 HelloWorld1.cs 中建立的規則集所參照。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 \MySampleLibrary 資料夾中：<br /><br /> AssemblyInfo.cs、MySampleLibrary.csproj、MySampleLibrary.sln|這個範例所屬的專案、解決方案和相關檔案，其提供定義所建立規則集參照之物件的類別。|  
|在 \MySampleLibrary 資料夾中：<br /><br /> MySampleLibraryClass.cs|Visual C# 檔，其中包含在所參考之屬性**如果**部分建立的規則，並可能在呼叫的方法**然後**部分建立的規則。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化「商務規則 Hello World1」範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Business Rules\Business 規則 Hello World1\  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
    > [!NOTE]
    >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序，執行「商務規則 Hello World1」範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Business Rules\Business 規則 Hello World1\bin\Debug\  
  
2.  在命令視窗中，輸入這個範例的可執行檔名稱 (BusinessRulesHelloWorld1.exe)，然後按 ENTER。  
  
    > [!NOTE]
    >  在執行時，規則集檔案 SampleRuleStore.xml 在此範例會產生**bin\Debug**資料夾。 當可執行檔暫停時，是等候您按 ENTER 以完成作業，您可以檢查這個檔案的內容。 請記得先關閉檔案，再按下任何鍵完成作業。 否則，可執行檔可能無法刪除檔案，以準備接續的範例執行。  
  
 如果您使用提供的範例輸入檔 SampleDocumentInstance.xml，定義的值為一 (1) 執行此範例為基礎建立的規則集的本質，其**識別碼**項目，您會看到下列輸出：  
  
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
>  粗體，在上述程式碼和程式碼所示，輸出所產生的檔案中所定義的範例商務物件中所顯示的輸出**MySampleLibrary**規則集所參考的資料夾。  
  
 如果您變更與相關聯的值**識別碼**範例輸入檔中的項目**SampleDocumentInstance.xml**從一 （1） 至二 （2），輸出會變更，如下所示：  
  
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
  
 您不會收到任何物件的輸出行**MySampleBusinessObject**類別具有其**MyValue**屬性設定為符合相關聯的值（建構期間）的值**識別碼**範例輸入檔 SampleDocumentInstance.xml 中的項目。  
  
## <a name="comments"></a>註解  
 內以程式設計方式建立的規則**createruleset （)** 方法顯示：  
  
 **如果**  
  
 **MySampleBusinessObject.MyValue**不等於值**識別碼**XML 文件中的項目。  
  
 **然後**  
  
 **Mysamplebusinessobject.mysamplemethod**具有整數參數，硬式編碼為常數五 （5） 在此情況下。 這個方法會產生輸出行開頭的**MySampleBusinessObject Class –-**。  
  
 這個規則取決於下列項目：  
  
-   A **MySampleBusinessObject**類別的公用屬性，稱為**MyValue**和公用的方法呼叫**MySampleMethod** （會採用整數參數）。  
  
-   XML 結構描述定義語言 (XSD) 結構描述定義 XML 文件，其中包含**識別碼**項目。  
  
 您依據類別和結構描述定義規則，但在執行期間需要有相關類別的物件執行個體，以及相關結構描述的文件執行個體。 您要針對這些執行階段執行個體 (稱為事實) 評估規則。 在本範例中的事實是多個執行個體**MySampleBusinessObject**包含不同的值所建構的物件及其**MyValue**屬性，並定義的結構描述的單一 XML 執行個體其中包含的值**識別碼**項目。  
  
## <a name="see-also"></a>請參閱  
 [商務規則 (BizTalk Server Samples 資料夾)](../core/business-rules-biztalk-server-samples-folder.md)