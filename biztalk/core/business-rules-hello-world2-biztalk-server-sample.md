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
# <a name="business-rules-hello-world2-biztalk-server-sample"></a>商務規則 Hello World2 （BizTalk Server 範例）
商務規則 Hello World2 範例擴充 「 商務規則 Hello world1 」 範例示範如何版本、 發佈和部署 XML 規則集至共用的 SQL 規則存放區，以及如何執行原則使用**原則**物件「 商務規則架構所提供。 這個範例還會示範動態原則更新的實際操作。  
  
> [!NOTE]
>  這個範例假設使用者在安裝產品期間一併安裝了「規則引擎更新服務」和「商務規則元件」(位於 [其他軟體] 節點下)。  
  
> [!NOTE]
>  您使用**原則**物件至規則引擎整合至任何獨立的應用程式。 **原則**物件是多個規則引擎執行個體所管理的抽象概念，規則集合是擷取，並且從共用 SQL 存放區中，具現化，以及原則更新已擷取並發佈裝載應用程式。  
  
 此範例中，所建構的事實如需詳細的規則集定義，且範例的基本資訊[商務規則 Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會建立可執行檔，用來執行下面的一系列步驟：  
  
1.  呼叫方法**CreateRuleset**建置的規則集所述的 < 備註 > 一節。  
  
2.  呼叫方法**SaveToFile**示範儲存規則集至檔案。  
  
3.  呼叫方法**LoadFromFile**示範載入設定檔中的規則。  
  
4.  將規則集部署至共用 SQL 規則存放區。  
  
5.  執行規則集利用**原則**物件，並使用同一組事實範例商務規則 Hello world1 」 範例。  
  
6.  暫停，讓您修改規則集檔案**SampleRuleStore.xml**以特定方式。  
  
7.  執行規則集使用再次**原則**物件，現在已修改的規則集，並再次使用同一組事實範例商務規則 Hello world1 」 範例。  
  
8.  透過刪除規則集檔案和部署的規則集記錄進行清除，準備接著執行範例。  
  
> [!NOTE]
>  如需此 SDK 中的所有範例的重要資訊，請參閱[範例](../core/samples-in-the-sdk.md)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Business Rules\Business 規則 Hello World2\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|描述|  
|---------------|-----------------|  
|App.ico、AssemblyInfo.cs、BusinessRulesHelloWorld2.csproj、BusinessRulesHelloWorld2.sln|這個範例所屬的專案、解決方案和相關檔案，可建立、儲存、載入、部署和執行規則集。|  
|HelloWorld2.cs|Visual C# 檔，其中包含方法，示範如何建立規則設定、 儲存規則集至檔案，載入規則集檔案，將規則集部署至共用的 Microsoft SQL Server 規則存放區，以及再執行規則集使用**原則**物件。|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|SampleDocumentInstance.xml|範例輸入檔，與 SampleSchema.xsd 檔中定義的結構描述相符。|  
|SampleSchema.xsd|結構描述檔，定義簡單的結構描述，其中某個元素會由 Visual C# 檔 Class1.cs 中的規則集參照。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 \HelloWorld2Library 資料夾中：<br /><br /> AssemblyInfo.cs、HelloWorld2Library.csproj、HelloWorld2Library.sln|這個範例所屬的專案、解決方案和相關檔案，其提供定義所建立規則集參照之物件的類別。|  
|在 \HelloWorld2Library 資料夾中：<br /><br /> HelloWorld2LibraryClass.cs|Visual C# 檔，其中包含在所參考之屬性**IF**一部分所建立的規則，並可能在呼叫的方法**然後**部分建立的規則。|  
  
### <a name="to-build-and-initialize-the-business-rules-hello-world2-sample"></a>建置和初始化商務規則 Hello World2 範例  
  
1. 在命令視窗中，瀏覽至下列資料夾：  
  
    *\<範例路徑\>* \Business Rules\Business 規則 Hello World2\  
  
2. 執行檔案 Setup.bat，這會執行下列動作：  
  
   - 為這個範例編譯和部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
   > [!NOTE]
   >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
   > 
   > [!NOTE]
   >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
   > 
   > [!NOTE]
   >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
### <a name="to-run-the-business-rules-hello-world2-sample"></a>執行商務規則 Hello World2 範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     *\<範例路徑\>* \Business Rules\Business 規則 Hello World2\bin\Debug\  
  
2.  在 [命令] 視窗中，輸入此範例的檔案名稱 (**BusinessRulesHelloWorld2.exe**)，然後按 ENTER 鍵。  
  
## <a name="hello-world2-output"></a>Hello World2 輸出  
 根據建立的規則集，註解區段中所述的本質[商務規則 Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md)，如果您使用提供的範例輸入檔 SampleDocumentInstance.xml，定義的值為一 (1) 執行此範例針對其**識別碼**項目，您會看到下列輸出：  
  
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
>  以粗體顯示的輸出是由範例商務物件，定義中的檔案所產生的輸出**HelloWorld2Library**規則集參照的資料夾。 此時，應用程式會進入這個狀態並等待。  
  
 執行範例的下一個部分包括使用 [商務規則編輯器] 變更商務規則。  
  
#### <a name="to-use-the-business-rules-composer-to-change-the-business-rules"></a>使用商務規則編輯器變更商務規則  
  
1. 若要開啟 商務規則編輯器，請按一下**開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則編輯器**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
2. 如果 SQL Server 對話方塊隨即出現在執行 SQL Server 的電腦上，按一下**確定**連接至規則存放區。  
  
3. 在**原則總管**下面的**sampleruleset**節點，以滑鼠右鍵按一下節點**1.0 版 – 已部署**，然後按一下**複製**。  
  
4. 以滑鼠右鍵按一下 **[sampleruleset]**，然後按一下**貼上 （原則版本）**。  
  
5. 您可以視需要變更規則條件和動作。 此程序中，按一下**rule1**中**版本 1.1 （未儲存）**。 在右窗格中，以滑鼠右鍵按一下**條件**，然後按一下**新增邏輯 NOT**。 新增**邏輯 NOT**欲**不等於**述詞，相當於使用**等於**述詞。  
  
6. 以滑鼠右鍵按一下節點**1.1 （未儲存） 版**，然後按一下**儲存**。 同樣地，按一下滑鼠右鍵，然後按一下**發佈**。 以滑鼠右鍵按一下第三次，然後按一下 **部署**。  
  
7. 暫停的命令視窗會要求您在更新原則後按任意鍵繼續執行，請按任意鍵。  
  
   從可執行檔 BusinessRulesHelloWorld2.exe 輸出 (假設您新增邏輯 Not 而變更規則) 的作業會繼續進行如下：  
  
```  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...         
Grabbing the policy ...         
Executing the policy...         
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5         
The major version of the policy was: 1         
The minor version of the policy was: 1         
Press ENTER to continue after updating the policy...         
```  
  
 請注意輸出如何變更：  
  
-   此方法中的輸出行**MySampleMethod**只會列印一次就立即執行個體**MySampleBusinessObject**類別**MyValue**屬性等於 1而不是上一個規則，以列印時**MyValue**屬性不等於 1。  
  
-   現在，原則的次要版本號碼為 1。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則 (BizTalk Server Samples 資料夾)](../core/business-rules-biztalk-server-samples-folder.md)