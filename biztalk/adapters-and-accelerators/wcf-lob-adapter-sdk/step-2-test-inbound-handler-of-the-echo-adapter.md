---
title: 步驟 2： 測試輸入處理常式回應配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86dede9b-6b7e-4901-9c79-b75bfee9155f
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e17bcc987949b9ca25ac25db9a1789ebe980eb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967036"
---
# <a name="step-2-test-inbound-handler-of-the-echo-adapter"></a>步驟 2： 測試輸入的回應配接器處理常式
![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **若要完成的時間：** 10 分鐘  
  
 在此步驟中，您會測試輸入的回應配接器所提供的服務。 您使用 Visual Studio 中，加入配接器服務參考 Visual Studio 外掛程式和自訂程式碼。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此步驟中，您必須先完成[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。 獨立於完成這個步驟[步驟 1： 測試輸出回應配接器處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md)。  
  
## <a name="create-a-visual-studio-project"></a>建立 Visual Studio 專案  
  
1.  啟動 Visual Studio。  
  
2.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
3.  在**新專案**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**專案類型**|按一下**Visual C#**。|  
    |**範本**|按一下**主控台應用程式**。|  
    |**名稱**|型別**ConsumeEchoAdapter_Inbound**。|  
    |**位置**|型別**C:\Tutorials**。|  
    |**方案名稱**|型別**ConsumeEchoAdapter_Inbound**。|  
  
4.  按一下 **[確定]**。  
  
5.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
## <a name="browse-search-and-generate-the-wcf-service"></a>瀏覽、 搜尋及產生 WCF 服務  
  
1.  在 Visual Studio 方案 窗格中，以滑鼠右鍵按一下**ConsumeEchoAdapter_Inbound**專案，然後選擇 **新增配接器服務參考**以啟動 新增配接器服務參考外掛程式。  
  
2.  在**新增配接器服務參考**畫面上，選擇繫結。 這是藉由選擇**echoAdapterBindingV2**。  
  
3.  接下來，按一下設定的配接器和 connection 屬性**設定**。  這會開啟**設定配接器**螢幕。  
  
4.  在**設定配接器**畫面上，選取**繫結屬性**索引標籤以設定配接器屬性。 請注意，自訂回應配接器類別**輸入**和**其他**列示如下。 在下**其他**分類中，按一下 [ **InboundFileSystemWatcherFolder** ]，然後輸入您想要監視的目錄。  
  
5.  按一下**確定**關閉**設定配接器**畫面上，並返回**新增配接器服務參考**螢幕。  
  
6.  接下來，按一下**連接**連接到的回應配接器和 （假設它所支援的特定業務系統）。 在幾分鐘之後, 的連接狀態應變**已連接**和類別目錄樹狀結構 (下**選取類別目錄**) 來擴展。  
  
7.  若要檢視可用的輸入的操作，請變更**服務合約型別**至**服務 （輸入操作）**。  
  
8.  在 類別目錄樹狀結構中，按一下 **主要類別**。 這會填入可用的類別和單一輸入作業的作業清單。 不有任何類別。  
  
9. 在**可用的類別和作業**，選取**OnReceiveEcho**作業。 按一下**新增**讓產生的 WCF 介面中選取的作業的一部分。  
  
10. 按一下**確定**產生 WCF 介面。 這會將應用程式組態檔 (app.config)、 WCF 介面 (EchoAdapterBindingInterface.cs) 和 WCF 服務 (EchoAdapterBindingService.cs) 加入專案。  
  
11. 按一下**檔案**上**Visual Studio**功能表，然後選擇 **全部儲存**。  
  
## <a name="test-the-echo-adapter"></a>測試回應配接器  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterBindingService.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，內部**OnReceiveEcho**方法，以下列取代現有的實作：  
  
    ```csharp  
    System.Console.WriteLine("path = " + path + ", len = " + length);  
    ```  
  
3.  在 [方案總管] 中，按兩下**Program.cs**檔案。  
  
4.  在 Visual Studio 編輯器中，在 Main 方法中，加入下列程式碼來裝載 WCF 服務。  
  
    ```csharp  
    try  
    {  
        // Create a ServiceHost for the EchoServiceImpl type  
        // and use the base address from app.config  
        System.ServiceModel.ServiceHost host = new System.ServiceModel.ServiceHost(typeof(EchoAdapterBindingNamespace.EchoAdapterBindingService));  
  
        // Open the ServiceHost to start listening for messages  
        host.Open();  
  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost  
        host.Close();  
    }  
    catch (TimeoutException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    catch (System.ServiceModel.CommunicationException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    ```  
  
5.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
6.  按 F5 啟動範例。  
  
7.  "Txt"副檔名的檔案放入稍早在本教學課程中所指定的目錄。 您應該會看到類似下面的程式的 [輸出] 視窗中的資訊：  
  
     **服務已就緒。**  
  
     **按\<ENTER\>終止服務。**  
  
     **路徑 = file:///C:/Tutorial/InboundTest/InboundTest.txt，len = 229179**  
  
8.  按下 Enter 鍵停止服務。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此步驟中，建立測試應用程式開發中的回應配接器所公開的輸入的操作[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。 若要這樣做，您可以建立 Visual Studio 專案、 產生 WCF 服務，以及提供裝載 WCF 服務的程式碼。 最後，您已執行測試應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 這是本教學課程的最後一個步驟。 如需輸入作業的詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IInboundHandler`。 若要查看範例示範如何裝載 WCF 服務需要驗證的 SDK，下載在回應配接器和測試程式碼[http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184)。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [教學課程 1：開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)