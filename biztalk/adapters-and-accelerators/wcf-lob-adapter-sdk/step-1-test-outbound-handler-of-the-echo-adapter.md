---
title: "步驟 1： 測試輸出回應配接器處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4a8164-a584-436f-b20b-4c884f6e2b37
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bf419a8ae3e6611f3d071cc94d274a5f2b0e00f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-test-outbound-handler-of-the-echo-adapter"></a>步驟 1： 測試輸出回應配接器處理常式
![步驟 2 之 1](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **完成時間：** 15 分鐘  
  
 在此步驟中，您將測試回應配接器所提供的三個輸出作業。 您會執行此作業使用[!INCLUDE[vs2010](../../includes/vs2010-md.md)]，加入配接器服務參考 Visual Studio 外掛程式和自訂程式碼。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此步驟中，您必須先完成[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。  
  
## <a name="create-a-visual-studio-project"></a>建立 Visual Studio 專案  
  
1.  啟動 Visual Studio。  
  
2.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
3.  在**新專案**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**專案類型**|按一下**Visual C#**。|  
    |**範本**|按一下**主控台應用程式**。|  
    |**名稱**|型別**ConsumeEchoAdapter_Outbound**。|  
    |**位置**|型別**C:\Tutorials**。|  
    |**方案名稱**|型別**ConsumeEchoAdapter_Outbound**。|  
  
4.  按一下 **[確定]**。  
  
5.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
## <a name="browse-search-and-generate-the-wcf-client"></a>瀏覽、 搜尋及產生 WCF 用戶端  
  
1.  在 Visual Studio 方案 窗格中，以滑鼠右鍵按一下**ConsumeEchoAdapter_Outbound**專案，然後選擇 **新增配接器服務參考**以啟動 新增配接器服務參考外掛程式。  
  
2.  在**新增配接器服務參考**畫面上，選擇繫結。 這是藉由選擇**echoAdapterBindingV2**。  
  
3.  接下來，按一下設定的配接器和 connection 屬性**設定...**.  這會顯示**設定配接器**螢幕。  
  
4.  在**設定配接器**畫面上，選取**URI 屬性**索引標籤以設定連接屬性。 請注意，會顯示自訂回應配接器類別目錄-**連接**和**格式**。 在下**格式**分類中，變更**EchoInUpperCase**至**True**。  
  
5.  在**設定配接器**畫面上，選取**繫結屬性**索引標籤以設定配接器屬性。 請注意，自訂回應配接器類別**輸入**和**其他**列示如下。 在下**其他**分類中，變更**計數**至**3**。  
  
6.  按一下**確定**關閉**設定配接器**畫面上，並返回**新增配接器服務參考**螢幕。  
  
7.  接下來，按一下**連接**連接到的回應配接器和 （假設它所支援的特定業務系統）。 在幾分鐘之後, 的連接狀態應變**已連接**和類別目錄樹狀結構 (下**選取類別目錄**) 來擴展。  
  
8.  在 類別目錄樹狀結構中，按一下 **主要類別**。 這將會填入可用的類別目錄的清單包含三個輸出作業的作業。 會有任何類別。  
  
    > [!NOTE]
    >  預設的合約型別是輸出。 分類結果將會符合這個合約型別。  
  
9. 在**可用的類別和作業**，選取所有三項作業。 大量作業時，您可能會使用搜尋來縮小選取範圍。在此情況下，是只有三個。 按一下**新增**讓產生的 WCF 介面中選取的作業的一部分。  
  
10. 按一下**確定**產生 WCF 介面。 這會將應用程式組態檔 (app.config) 和 WCF 用戶端 proxy (EchoAdapterBindingClient.cs) 加入專案。  
  
11. 按一下**檔案**Visual Studio 功能表上選擇 **全部儲存**。  
  
## <a name="configure-adapter-authentication"></a>設定配接器的驗證  
  
1.  在 Visual Studio 方案 窗格中，按兩下**app.config**。  
  
2.  尋找`address`屬性`endpoint`項目。 看起來應類似下列範例：  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=False&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
     變更**enableAuthentication**從**False**至**True**如下所示。 這將需要將認證傳遞給配接器呼叫的應用程式。  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=True&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
3.  按一下以儲存方案**檔案**在 Visual Studio 功能表，選擇**全部儲存**。  
  
## <a name="create-a-sample-xml-file"></a>建立範例 XML 檔案  
  
1.  啟動 [記事本] 的執行個體。 使用 開始 功能表中，按一下 **所有程式**&#124;**附屬應用程式**，然後選擇 **記事本**。  
  
2.  下列範例將資料複製到 [記事本] 編輯器。  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <ns0:greeting xmlns:ns0="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes">  
      <ns0:address>  
        <ns0:street1>123 Microsoft Way</ns0:street1>  
        <ns0:street2>Building # 4599</ns0:street2>  
        <ns0:city>Redmond</ns0:city>  
        <ns0:state>WA</ns0:state>  
        <ns0:zip>98052</ns0:zip>  
      </ns0:address>  
      <ns0:greetingText>Welcome to Redmond!</ns0:greetingText>  
    </ns0:greeting>              
    ```  
  
3.  在 記事本 功能表中，按一下 **檔案**，然後選擇 **另存新檔...**. 輸入"CustomGreetingInstance.xml 」 中的檔案名稱並選擇 Unicode 的編碼方式，然後將它儲存到專案目錄或另一個的適當位置。 請注意的完整路徑和檔名，供日後參考。  
  
4.  已成功儲存檔案時，請關閉 [文字編輯器]。  
  
## <a name="test-the-echo-adapter"></a>測試回應配接器  
  
1.  在 [方案總管] 中，按兩下**Program.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，內部**Main**方法，加入下列程式碼以便建立產生 WCF 用戶端的執行個體。  
  
    ```csharp  
    EchoOutboundContractClient client = new EchoOutboundContractClient();  
    ```  
  
3.  現在加入程式碼所建立的配接器的認證。 驗證回應配接器中啟用時，它會檢查使用者名稱存在，但將不會檢查此值。  
  
    ```csharp  
    // pass client credentials  
    client.ClientCredentials.UserName.UserName = "username";  
    ```  
  
4.  加入程式碼來叫用 EchoStrings 作業以繼續。  
  
    ```csharp  
    // Invoke EchoStrings()  
    Console.WriteLine("Invoking EchoStrings() method against the adapter...");  
    string[] response = client.EchoStrings("Bonjour!");  
    foreach (string data in response)  
    {  
        Console.WriteLine(data);  
    }  
    ```  
  
5.  加入程式碼來叫用 EchoGreetings 作業以繼續。  
  
    ```csharp  
    // Invoke EchoGreetings()  
    Console.WriteLine("\nInvoking EchoGreetings() method against the adapter...");  
    microsoft.adapters.samples.echov2.Types.Greeting greeting = new microsoft.adapters.samples.echov2.Types.Greeting();  
    greeting.id = Guid.NewGuid();  
    greeting.sentDateTime = DateTime.Now;  
    greeting.greetingText = "Hello World!";  
    greeting.name = new microsoft.adapters.samples.echov2.Types.Name();  
    greeting.name.salutation = microsoft.adapters.samples.echov2.Types.Salutation.Miss;  
    greeting.name.firstName = "Jane";  
    greeting.name.middleName = "Z.";  
    greeting.name.lastName = "Smith";  
    microsoft.adapters.samples.echov2.Types.Greeting[] greetingArray = client.EchoGreetings(greeting);  
    foreach (microsoft.adapters.samples.echov2.Types.Greeting data in greetingArray)  
    {  
        Console.WriteLine(data.id + " " + data.sentDateTime + " " + data.greetingText + " " + data.name.firstName );  
    }  
    ```  
  
6.  加入程式碼來叫用 EchoCustomGreetingsFromFile 作業以繼續。  
  
    ```csharp  
    // Invoke EchoCustomGreetingFromFile()  
    Console.WriteLine("\nInvoking EchoCustomGreetingFromFile() method against the adapter ...");  
    // Copy the sample data from CustomGreeting-instance.xml file and place in appropriate folder  
    // as specified in the operation parameter  
    microsoft.adapters.samples.echov2.PreDefinedTypes.CustomGreeting   
    // change the Uri to point to the greeting instance xml file you created  
    customGreeting = client.EchoCustomGreetingFromFile(new Uri(@"c:\CustomGreetingInstance.xml"));  
    Console.WriteLine(customGreeting.greetingText + " " + customGreeting.address.city);  
    client.Close();  
    Console.ReadLine();  
    ```  
  
7.  EchoCustomGreetingsFromFile 中測試的程式碼，請確定自訂問候語會使用您在上一個程序中建立的檔案。 變更以反映您的檔案位置的程式碼。  
  
8.  在[!INCLUDE[vs2010](../../includes/vs2010-md.md)]上**檔案**功能表上，按一下 **全部儲存**。  
  
9. 執行應用程式。 您應該會看到類似下面的輸出：  
  
     **叫用配接器針對 EchoStrings() 方法...**  
  
     **Bonjour ！**  
  
     **Bonjour ！**  
  
     **Bonjour ！**  
  
     **Bonjour ！**  
  
     **Bonjour ！**  
  
     **叫用配接器針對 EchoGreetings() 方法...**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 2007 年 9 月 13 日下午 3:18:07 Hello World ！Jane**  
  
     **叫用配接器針對 EchoCustomGreetingFromFile() 方法...**  
  
     **歡迎使用雷德蒙德 ！台北市**  
  
10. 按下 Enter 鍵停止程式。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此步驟中，您可以建立測試應用程式的回應配接器開發教學課程 1 中所公開的三個輸出作業。 若要這樣做，您可以建立 Visual Studio 專案、 產生 WCF 服務，以及提供裝載 WCF 服務的程式碼。 最後，您已執行測試應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 若要測試輸入的作業，繼續進行[步驟 2： 回應配接器的測試輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
  [教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [步驟 2： 測試輸入的回應配接器處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)