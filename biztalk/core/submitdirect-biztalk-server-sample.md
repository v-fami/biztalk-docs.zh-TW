---
title: "SubmitDirect （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- receive adapters, examples
- examples, receive adapters
ms.assetid: 3540368b-cf46-4c83-a87b-94aec9cd1b36
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4941cb95e180b7075b7e113fb89f7734a9abd82
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="submitdirect-biztalk-server-sample"></a>SubmitDirect （BizTalk Server 範例）
SubmitDirect 範例將示範如何從 .NET 架構的應用程式，以程式設計的方式將單向及要求/回應訊息提交至 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此範例將示範搭配配接器使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] API。 此外還提供名為 Submit 的接收配接器，可用來提交訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
 在執行此範例之前，請先確認您以屬於 [BizTalk 外掛式主控件使用者] 群組的使用者登入。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例將說明如何執行與 BizTalk 配接器相關的各種不同工作。 具體而言，此範例將說明如何：  
  
-   使用在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理程序外部執行的外掛式配接器。 Submit 配接器是外掛式配接器，因為它是由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理程序外部的處理程序所建立 (啟動方式與 .NET 應用程式相同)。  
  
-   提交訊息批次至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 Submit 配接器會使用批次訊息提交功能，一次提交數個訊息。  
  
-   使用要求/回應模式同步提交訊息，以及使用單向模式非同步地提交訊息。  
  
-   向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊配接器。 此範例會說明如何註冊配接器，並且提供註冊可執行檔來自動化配接器註冊。  
  
 此範例實際上包含兩個範例，如下所示：  
  
-   **提交單向訊息批次。** 主控台應用程式 SubmitMessages.exe 會從命令列字串，並提交當做個別訊息公佈到每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在接收位置挑選每一個提交的訊息，透過通過接收和傳送管線傳送，然後寫入文字檔中。  
  
-   **提交要求/回應訊息。** 主控台應用程式 SubmitRequest.exe 會採用其命令列上指定的.xml 檔，並將它提交給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此 .xml 檔的結構描述會定義包含兩個整數欄位的元素。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]挑選.xml 檔案，並處理以協調流程 （含有一個要求/回應連接埠）。 然後使用對應產生傳回整數的 XML 回應訊息，該整數為要求中兩個整數得出的結果。 當主控台應用程式收到回應時，便會顯示結果。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\AdaptersDevelopment\SubmitDirect\  
  
 下表列出此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|Setup.bat|建置並初始化此範例。|  
|SubmitDirect.sln|方案檔，其中 ProcessRequest 資料夾包含 BizTalk 專案，而 Microsoft Visual C# 專案則包含在其他資料夾中。|  
|SubmitMessagesBinding.xml，SubmitRequestBinding.xml|用於自動化設定，例如連接埠繫結。|  
|\ProcessRequest 資料夾中：<br /><br /> DocIn.xsd、DocOut.xsd、Multiplier.odx、Multiply.btm、ProcessRequest.btproj|提供 BizTalk 專案，將要求/回應實例中的整數相乘。|  
|在 \SubmitMessages 資料夾中：<br /><br /> AssemblyInfo.cs、SubmitMessages.cs、SubmitMessages.csproj|提供 Visual C# 專案給主控台應用程式，該應用程式會將命令列字串參數當做一批單獨訊息傳遞。|  
|在 \SubmitRequest 資料夾中：<br /><br /> AssemblyInfo.cs、DocInstance.xml、SubmitRequest.cs、SubmitRequest.csproj|提供 C# 專案給主控台應用程式，該應用程式會傳遞包含兩個要相乘之整數的 .xml 檔 (DocInstance.xml)。|  
|在 \TransportProxyUtils 資料夾中：<br /><br /> AssemblyInfo.cs、MessageHelper.cs、MessagingAPIInterface.cs、MessagingAPIs.cs、ResponseCallBack.cs、TpBatchAsyncCallback.cs、TpBatchAsyncResult.cs、TpBatchStatus.cs、TransportProxyUtils.csproj|提供 C# 專案給 Submit 配接器的執行階段部份，該配接器會實作同步和非同步提交訊息的方法，以及提交批次和單一要求訊息的方法。|  
|在 \TransportProxyUtilsReg 資料夾中：<br /><br /> AssemblyInfo.cs、RegisterAdapter.cs、TransportProxyUtilsReg.csproj|提供 Visual C# 專案，示範可用來向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊配接器的程式碼。|  
|在 \TransportProxyUtilsUI 資料夾中：<br /><br /> AssemblyInfo.cs、TransportProxyUtilsMgmt.cs、TransportProxyUtilsUI.csproj|提供 Visual C# 專案給 Submit 配接器的使用者介面部分。|  
  
## <a name="building-and-initializing-the-sample"></a>建置和初始化範例  
  
#### <a name="to-build-and-initialize-the-submitdirect-sample"></a>建置及初始化 SubmitDirect 範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\AdaptersDevelopment\SubmitDirect  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   針對本範例的批次提交部份建立下列輸出資料夾。  
  
         \<*範例路徑*\>\AdaptersDevelopment\SubmitDirect\Out  
  
    -   針對此範例編譯各種 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊 Submit 配接器。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
        > [!NOTE]
        >  此範例會在建立和繫結連接埠時顯示下列警告：  
        >   
        >  `Warning: Receive handler not specified for receive location "SubmitDirectRL"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.ProcessRequest.Multiplier"; updating with first available host.`  
        >   
        >  您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置，並啟動傳送埠和協調流程。  
  
        > [!NOTE]
        >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
        > [!NOTE]
        >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
  
        > [!NOTE]
        >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-the-sample"></a>執行範例  
 由於此範例使用 File 配接器，因此 BizTalk 主控件 (BizTalkServerApplication) 必須為執行中。 請使用下列程序來執行 SubmitDirect 範例。  
  
#### <a name="to-run-the-batch-submission-portion-of-the-submitdirect-sample"></a>執行 SubmitDirect 範例的批次提交部份  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\AdaptersDevelopment\SubmitDirect\SubmitMessages\bin\Debug  
  
2.  執行 SubmitMessages.exe 檔，在命令列上傳遞多個字串。  
  
     範例： SubmitMessages msg1 msg2 msg3  
  
3.  注意在 Out 輸出資料夾中建立的多個文字檔。這些檔案包含命令列上傳遞的字串，每個檔案包含一個字串。  
  
#### <a name="to-run-the-requestresponse-portion-of-the-submitdirect-sample"></a>執行 SubmitDirect 範例的要求/回應部份  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\AdaptersDevelopment\SubmitDirect\SubmitRequest\bin\Debug  
  
2.  執行 SubmitRequest.exe 檔，在命令列上傳遞適當的 .xml 檔案名稱。  
  
     範例： SubmitRequest...\\..\DocInstance.xml  
  
3.  觀察包含乘法運算中，顯示在主控台的結果的回應 XML 訊息。  
  
## <a name="comments"></a>註解  
 您可以在其他應用程式中使用 Submit 配接器。 您可以從任何 .NET 架構的程式碼使用該配接器，以程式設計的方式傳遞訊息至您的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 若要搭配您的程式碼使用此配接器，請執行下列程序。  
  
#### <a name="to-use-the-sample-adapter-with-your-code"></a>搭配您的程式碼使用範例配接器  
  
1.  向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊 Submit 配接器。 如果您已執行此範例提供的 Setup.bat 檔，則配接器應該已註冊且可立即使用。 否則，您可以建置 TransportProxyUtils.csproj、TransportProxyUtilsUI.csproj 和 TransportProxyUtilsReg.csproj 專案，然後執行第三個專案產生的可執行檔 RegisterAdapter.exe，藉此註冊配接器。  
  
    > [!IMPORTANT]
    >  如果您在 64 位元電腦上安裝 BizTalk，所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體中都變更為 HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ **RegisterAdapter.cs**檔案。  
  
2.  建立接收位置使用 Submit 配接器的接收埠。 指定接收位置的位址。 此位址可以是使用此配接器的接收位置內，任何未使用過的唯一字串。  
  
3.  參考您 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案中的組件 Microsoft.BizTalk.SDKSamples.AdaptersDevelopment.TransportProxyUtils.dll。  
  
4.  使用此組件提供的下列一或多個方法提交訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    |方法|Description|  
    |-----------------|-----------------|  
    |**Submitmessage**<br /><br /> **BeginSubmitMessage()**<br /><br /> **EndSubmitMessage()**|提交單向訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同步和非同步方法。 訊息內容中必須設定訊息將提交至其中的接收位置位址。<br /><br /> 表示已傳回提交狀態 (成功/失敗) 的布林值。|  
    |**SubmitMessages()**<br /><br /> **BeginSubmitMessages()**<br /><br /> **EndSubmitMessages()**|提交單向訊息陣列至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同步和非同步方法。 訊息內容中應設定訊息將提交至其中的接收位置位址。<br /><br /> 表示已傳回提交狀態 (成功/失敗) 的布林值。|  
    |**SubmitSyncMessage()**<br /><br /> **BeginSubmitSyncMessage()**<br /><br /> **EndSubmitSyncMessage()**|提交要求訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同步和非同步方法。 訊息內容中應設定訊息將提交至其中的接收位置位址。<br /><br /> 傳回回應訊息。|  
    |**CreateMessageFromString()**|從字串建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息物件，並且在訊息內容中設定接收位置位址屬性。<br /><br /> 傳回 BizTalk 訊息物件。|  
    |**CreateMessageFromStream()**|從資料流建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息物件，並在訊息內容中設定接收位置位址屬性。<br /><br /> 傳回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息物件。|  
  
     如需這些方法的參數和傳回類型的詳細資訊，請參閱 TransportProxyUtils 資料夾中的 MessagingAPIInterface.cs 檔。  
  
## <a name="see-also"></a>請參閱  
 [配接器範例-開發](../core/adapter-samples-development.md)   
 [註冊配接器](../core/registering-an-adapter.md)